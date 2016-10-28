# References

* <https://www.consul.io/>
* <https://cloud.google.com/solutions/autoscaled-load-balancing-using-haproxy-and-consul-on-compute-engine>
* <http://www.mammatustech.com/consul-service-discovery-and-health-for-microservices-architecture-tutorial>
* <https://www.digitalocean.com/community/tutorial_series/getting-started-with-consul>

# Running Consul Server

## Command

    # consul agent -advertise=<host IP> -config-file=consul.server.config.json

## Config

    {
      "bootstrap": true,
      "bind_addr": "0.0.0.0",
      "client_addr": "0.0.0.0",
      "datacenter": "dc-yenbo",
      "data_dir": "/home/yenbo.huang/tmp/consul/data",
      "dns_config": {
        "allow_stale": true,
        "max_stale": "5s",
        "enable_truncate": true
      },
      "domain": "domain-yenbo",
      "node_name": "server-yenbo",
      "reap": true,
      "server": true,
      "skip_leave_on_interrupt": true,
      "ui": true,
      
      "disable_remote_exec": true,
      "encrypt": <encryption key>,
      "acl_datacenter": "dc-yenbo",
      "acl_master_token": <Master ACL token>,
      "acl_default_policy": "deny",
      "acl_down_policy": "extend-cache"
    }

# Running Consul Client

## Command

    # consul agent -join=<Consul server IP> -config-file=consul.client.config.json -advertise=<Host IP>

## Config

    {
      "bind_addr": "0.0.0.0",
      "client_addr": "0.0.0.0",
      "datacenter": "dc-yenbo",
      "data_dir": "/home/yenbo.huang/tmp/consul/data",
      "dns_config": {
        "allow_stale": true,
        "max_stale": "5s",
        "enable_truncate": true
      },
      "domain": "domain-yenbo",
      "node_name": "client-yenbo-1",
      "reap": true,
      "server": false,
      "skip_leave_on_interrupt": true,
      "ui": false,
      
      "disable_remote_exec": true,
      "encrypt": <encryption key>,
      "acl_datacenter": "dc-yenbo",
      
      "services": [
        {
          "name": "test-service-1",
          "token": <ACL token>
        },
        ...
      ]
    }

# Run Consul Server by Docker

    # docker run -d -p 8500:8500 --name=consul progrium/consul -server -bootstrap

# Troubleshooting

## Invalid Recursor Address in Consul Server Logs

When you see this error:

    ==> Starting Consul agent...
    ==> Starting Consul agent RPC...
    ==> Error starting dns server: Invalid recursor address: lookup NOTE on ....:53: server misbehaving
    ==> WARNING: Bootstrap mode enabled! Do not enable unless necessary

Delete comments contains *nameserver* in */etc/resolv.conf* before running Consul:

    # Generated by NetworkManager
    ...
    # NOTE: the libc resolver may not support more than 3 nameservers.
    # The nameservers listed below may not be recognized.
    ...

This is the similar bug to Cloudbreak: <https://community.hortonworks.com/questions/14137/cloudbreak-deploy-fails-due-to-unsuccessful-addres.html>