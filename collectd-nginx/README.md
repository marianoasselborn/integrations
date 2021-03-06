# ![](https://github.com/signalfx/integrations/blob/master/collectd-nginx/img/integrations_nginx.png) NGINX

_This is a directory that consolidates all the metadata associated with the NGINX collectd plugin. The relevant code for the plugin can be found [here](https://github.com/signalfx/collectd/blob/master/src/nginx.c)_

- [Description](#description)
- [Requirements and Dependencies](#requirements-and-dependencies)
- [Installation](#installation)
- [Configuration](#configuration)
- [Usage](#usage)
- [Metrics](#metrics)
- [License](#license)

### DESCRIPTION

Use the NGINX plugin for collectd to monitor NGINX webserver performance.

#### FEATURES

##### Built-in dashboards

- **NGINX Servers**: Overview of data from all NGINX servers.

  [<img src='./img/dashboard_nginx_servers.png' width=200px>](./img/dashboard_nginx_servers.png)

- **NGINX Server**: Focus on a single NGINX server.

  [<img src='./img/dashboard_nginx_server.png' width=200px>](./img/dashboard_nginx_server.png)  

### REQUIREMENTS AND DEPENDENCIES

This plugin requires:

| Software          | Version        |
|-------------------|----------------|
| collectd |  4.2+  |

### INSTALLATION

1. On RHEL/CentOS and Amazon Linux systems, run the following command to install this plugin:

         yum install collectd-nginx
         
   On Ubuntu and Debian systems, this plugin is included by default with the [SignalFx collectd agent](https://github.com/signalfx/integrations/tree/master/collectd)[](sfx_link:sfxcollectd). 
         
1. Enable the `stub_status` module in your NGINX server as described [below](#configuration).

1. Download SignalFx’s [sample configuration file](https://github.com/signalfx/integrations/blob/master/collectd-nginx/10-nginx.conf) to `/etc/collectd/managed_config`.

1. Modify the sample configuration file to provide values that make sense for your environment, as described in [Configuration](#configuration), below.

1. Restart collectd.

### CONFIGURATION

Using the example configuration file [10-nginx.conf](https://github.com/signalfx/integrations/blob/master/collectd-nginx/10-nginx.conf) as a guide, provide values for the configuration options listed below that make sense for your environment and allow you to connect to the NGINX instance to be monitored.

| configuration option | definition | default value |
| ---------------------|------------|---------------|
| URL | URL at which collectd can access the output of the NGINX status module.  | "http://localhost:80/nginx_status" |

#### NGINX service configuration

Please see [nginx docs](http://nginx.org/en/docs/http/ngx_http_stub_status_module.html) for a guide to configuring the NGINX stats module `ngx_http_stub_status_module`.

### USAGE

Sample of pre-built dashboard in SignalFx:

![](././img/dashboard_nginx.png)

### METRICS

The following status information is provided:

| Metric | definition |
| -------|-------------|
|Active connections| The current number of active client connections including Waiting connections.|
|accepts|The total number of accepted client connections.|
|handled|The total number of handled connections. Generally, the parameter value is the same as accepts unless some resource limits have been reached (for example, the worker_connections limit).|
|requests|The total number of client requests.|
|Reading|The current number of connections where nginx is reading the request header.|
|Writing|The current number of connections where nginx is writing the response back to the client.|
|Waiting|The current number of idle client connections waiting for a request.|


For metrics and dimensions emitted by this plugin, [click here](././docs).

### LICENSE

This integration is released under the Apache 2.0 license. See [LICENSE](./LICENSE) for more details.
