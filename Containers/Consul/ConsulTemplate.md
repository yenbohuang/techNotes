# References

* <https://github.com/hashicorp/consul-template>
* <https://jlordiales.me/2015/04/01/consul-template/>
* <https://dimitrialexiou.com/tag/consul-template/>
* <http://agiletesting.blogspot.tw/2014/11/service-discovery-with-consul-and.html>

# Run consul-template

## Command

Continuously:

    # consul-template -consul=<Consul server IP>:8500 -config=consul-template.cfg

Run only once:

    # consul-template -once -consul=<Consul server IP>:8500 -config=consul-template.cfg

## Config

    {
      retry = "10s"
      max_stale = "10m"
      log_level = "info"
      pid_file = "/home/yenbo.huang/tmp/consul-template.pid"
      template {
         source = "/home/yenbo.huang/consul-demo/config/demo.ctmpl"
         destination = "/home/yenbo.huang/tmp/demo.config.json"
         command_timeout = "30s"
         perms = 0644
         backup = true
    }

## Template

Although [toJSONPretty](https://github.com/hashicorp/consul-template#tojsonpretty) should be considered final according to consul-template, it is very convenient for JSON format. We can fall back to the hard way (a complex template file) if it doesn't fulfill out requirements.

    {{ tree "some/key-value/path" | explode | toJSONPretty }}
