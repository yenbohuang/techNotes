# Blog posts

* <https://www.mauras.ch/securing-consul.html>
* <http://jovandeginste.github.io/2016/05/04/turning-on-acl-s-in-our-consul-cluster.html>

# Disable Support for Remote Execution

The default value of [disable_remote_exec](https://www.consul.io/docs/agent/options.html#disable_remote_exec) is *false* which allows any Consul nodes [issuing commands](https://www.consul.io/docs/commands/exec.html) (such as shutdown) to any node in the Consul cluster. This is dangerous especially when Consul agent is ran by root.

Add *disable_remote_exec* in Consul server/client config:

    {
      ...
      "disable_remote_exec": true,
      ...
    }

# Encrypt Consul Gossip Traffic

Consul is default to not encypt traffic using Gossip protocol. Adding encryption provides another layer of security.

First, generate encryption key by [keygen](https://www.consul.io/docs/commands/keygen.html). Please note that both servers and clients share the same encryption key.

    # consul keygen

Add [encrypt](https://www.consul.io/docs/agent/options.html#encrypt) in Consul server/client config:

    {
      ...
      "encrypt": <generated encryption key>,
      ...
    }

# Enabling ACL System

Consul provides an optional Access Control List (ACL) system which can be used to control access to data and APIs.

## Generating ACL Tokens

Use *uuidgen* and generate UUID as ACL tokens.

    # uuidgen 

## Enable ACL in Consul Server and Client

First, generate a UUID as ACL master token. This is only added in Consul server config:

    {
      ...
      "acl_datacenter": <Datacenter>,
      "acl_master_token": <ACL master token>,
      "acl_default_policy": "deny",
      "acl_down_policy": "extend-cache",
      ...
    }

For other nodes (Consul client), add the following config:

    {
      ...
      "acl_datacenter": <Datacenter>,
      ...
    }

See <https://www.consul.io/docs/agent/options.html> for details.

### Define ACL Policy

Refer to [Rule Specification](https://www.consul.io/docs/internals/acl.html) and [ACL HTTP Endpoint](https://www.consul.io/docs/agent/http/acl.html) about the syntax of ACL policy/rule.

    {
      "ID": <ACL token>,
      "Name": <Policy name>,
      "Type": "client",
      "Rules": "
        service \"\" { policy = \"read\" }
        key \"config/read-only/\" { policy = \"read\" }
        key \"config/read-write/\" { policy = \"write\" }
        "
    }

After ACL policies are defined, we can save them into files and put them into consul server by [ACL update API](https://www.consul.io/docs/agent/http/acl.html#acl_update) and ACL master token.

    #!/bin/sh
    
    CONSUL_IP=<server IP>
    ACL_MASTER_TOKEN=<ACL master token>
    
    for i in `ls -1 acl/*.acl.json`
    do
      curl -X PUT -d @$i http://$CONSUL_IP:8500/v1/acl/update?token=$ACL_MASTER_TOKEN
    done

## Accessing Consul with ACL

### Using ACL by Consul HTTP APIs

Consul provides [HTTP APIs](https://www.consul.io/docs/agent/http.html) for interacting with Consul agents. After we enabled [ACLs](https://www.consul.io/docs/agent/http.html) on Consul servers/clients, we need to add *"X-Consul-Token"* HTTP Header (More Secure) or append *"token"* Query String Parameter (Less Secure) when we call HTTP APIs.

#### By "X-Consul-Token" HTTP Header (More Secure)

This approach is more secure because tokens are not logged as part of the URL string (e.g., Apache access logs.)

    # curl -H "X-Consul-Token: <ACL token>" ... http://<server IP>:8500/...

#### By "token" Query String Parameter (Less Secure)

    # curl ... http://<server IP>:8500/...?token=<ACL master token>&...

### Setting Environment Variables by "docker run" Command

Some third-party tools support the undocumented ["CONSUL_HTTP_TOKEN" environment variable](https://github.com/hashicorp/consul/blob/master/api/api.go) for providing ACL tokens. This section documents the approach about how to add it by [docker run](https://docs.docker.com/engine/reference/commandline/run/) command.

#### By "--env-file" Option (More Secure)

This approach is more secure and you cannot see ACL token by `ps aux | grep docker`.

Prepare an environment file with ACL token.

    CONSUL_HTTP_TOKEN=<ACL token>

Use *"--env-file"* option of "docker run" command:

    # docker run ... --env-file=<environment file> ... consul://<Consul server IP>:8500

#### By "-e" Option (Less Secure)

We can also use *"-e"* option of "docker run" command:

    # docker run ... -e CONSUL_HTTP_TOKEN=<ACL token> ... consul://<Consul server IP>:8500

### Using ACL in Docker Daemon

By defining *"CONSUL_HTTP_TOKEN"* environment variable, Docker daemon uses this ACL token when communicating with Consul server. This technique is not documented in Docker daemon documents but can be found [here](https://github.com/docker/libkv/issues/98).

#### Running by systemd

Add *CONSUL_HTTP_TOKEN* environment variable in configuration file under `/etc/systemd/system/docker.service.d/` folder.

     [Service]
     Environment="CONSUL_HTTP_TOKEN=<ACL token>"
     ExecStart=
     ExecStart=/usr/bin/docker daemon .... --cluster-store=consul://<Consul server IP>:8500 ....

Reload docker service after changes:

    # sudo systemctl daemon-reload
    # sudo systemctl enable docker
    # sudo systemctl start docker

#### Running by Command-Line

    # sudo CONSUL_HTTP_TOKEN=<ACL token for docker daemon> \
     docker daemon -H tcp://0.0.0.0:2375 -H unix:///var/run/docker.sock \
     --cluster-advertise=<host IP>:2375 --cluster-store=consul://<Consul server IP>:8500

TODO: How to hide ACL token from "ps aux"?

### Using ACL by Consul-Template

Set *"CONSUL_TOKEN"* environment variable with ACL token for services which use [consul-template](https://github.com/hashicorp/consul-template).

### Putting Values into Consul KV Store

    # curl -v -X PUT -H "X-Consul-Token: <ACL token>" -d "<value>" http://<server IP>:8500/v1/kv/<key>

### Using ACL in Swarm

By defining *"CONSUL_HTTP_TOKEN"* environment variable, Swarm uses this ACL token when communicating with Consul server. This technique is not documented in Swarm documents but can be found [here](https://github.com/docker/swarm/issues/1643).

For Swarm manager:

    # docker run -d -p 4000:4000 --name=swarm-manager --env-file=<environment file> \
      swarm manage -H :4000 --replication --advertise <Swarm manager IP>:4000 consul://<Consul server IP>:8500

For Swarm agent:

    # docker run -d --name=swarm-agent --env-file=<environment file> \
      swarm join --advertise=<Swarm agent IP>:2375 consul://<Consul server IP>:8500

### Using ACL in Registrator

By defining *"CONSUL_HTTP_TOKEN"* environment variable, Registrator uses this ACL token when communicating with Consul server. This technique is not documented in Registrator documents but can be found [here](https://github.com/gliderlabs/registrator/issues/135).

    # docker run -d --name=registrator --env-file=<environment file> \
     --net=host --volume=/var/run/docker.sock:/tmp/docker.sock \
     gliderlabs/registrator:latest consul://<Consul server IP>:8500

