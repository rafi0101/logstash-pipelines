# Logstash-pipelines (WIP)
Some logstash pipelines and patterns I'm using

Content
-----------
* [Features](#Features)
* [Usage](#Usage)
    * [Prepare](#Prepare)
    * [fail2ban](#fail2ban)
    * [Grafana](#Grafana)
    * [Rspamd](#rspamd)
    * [UFW](#ufw-uncomplicated-firewall--iptables)
    * [Monit](#monit-website)
    * [openvpn-as](#openvpn-as)
* [Reference](#Reference)
* [License](#License)

Usage
----------

## Prepare

### Filebeat

Put the Filebeat config in your filebeat inputs directory --> `/etc/filebeat/inputs.d/` or add the content of the Filebeat config below `filebeat.inputs:` in your `/etc/filebeat/filebeat.yml`

If you prefere the first option, you need to create the `inputs.d` directory, and tell filebeat to use this:

```yml
# ============================== Filebeat inputs ===============================

filebeat.config.inputs:
  enabled: true
  path: ${path.config}/inputs.d/*.yml

```

### Logstash

Put the Logstash config in the config directory `/etc/logstash/conf.d`,  
and the grok patterns into the patterns directory `/etc/logstash/patterns.d`  

**Don't forget to restart Filebeat and Logstash after editing configs**  

## fail2ban
Filebeat: [fail2ban.yml](filebeat/inputs.d/fail2ban.yml)  
Logstash config: [fail2ban.conf](logstash/conf.d/20-fail2ban.conf)  
Logstash pattern: [fail2ban.grok](logstash/patterns.d/fail2ban.grok)  

## Grafana
Filebeat: [grafana.yml](filebeat/inputs.d/grafana.yml)  
Logstash config: [grafana.conf](logstash/conf.d/40-grafana.conf)  
Logstash pattern: [grafana.grok](logstash/patterns.d/grafana.grok)  

## Rspamd
Filebeat: [rspamd.yml](filebeat/inputs.d/rspamd.yml)  
Logstash config: [rspamd.conf](logstash/conf.d/30-rspamd.conf)  
Logstash pattern: [rspamd.grok](logstash/patterns.d/rspamd.grok)  

## UFW (uncomplicated firewall) / IPTABLES
Filebeat: [ufw.yml](filebeat/inputs.d/ufw.yml)  
Logstash config: [ufw.conf](logstash/conf.d/25-ufw.conf)  
Logstash pattern: [ufw.grok](logstash/patterns.d/ufw.grok)  

## Monit [Website](https://mmonit.com/monit/#download)
Filebeat: [monit.yml](filebeat/inputs.d/monit.yml)  
Logstash config: [monit.conf](logstash/conf.d/15-monit.conf)  
Logstash pattern: [monit.grok](logstash/patterns.d/monit.grok)  

## openvpn-as

Filebeat: [openvpnas.yml](filebeat/inputs.d/openvpnas.yml)  
Logstash config: [openvpnas.conf](logstash/conf.d/35-openvpnas.conf)  
Logstash pattern: [openvpnas.grok](logstash/patterns.d/openvpnas.grok)  


Reference
----------
fail2ban:
* https://github.com/nxhack/logstash

ufw:
* https://github.com/splitice/iptables-log-grok/blob/master/iptables.patterns

License
----------
    MIT License

    Copyright (c) 2021 Raphael Ebner

    Permission is hereby granted, free of charge, to any person obtaining a copy
    of this software and associated documentation files (the "Software"), to deal
    in the Software without restriction, including without limitation the rights
    to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
    copies of the Software, and to permit persons to whom the Software is
    furnished to do so, subject to the following conditions:

    The above copyright notice and this permission notice shall be included in all
    copies or substantial portions of the Software.

    THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
    IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
    FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
    AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
    LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
    OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
    SOFTWARE.
