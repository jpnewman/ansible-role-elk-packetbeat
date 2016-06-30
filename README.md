# jpnewman.elk-packetbeat

[![Ansible Role](https://img.shields.io/ansible/role/9592.svg?maxAge=2592000)](https://galaxy.ansible.com/jpnewman/elk-packetbeat/)
[![Build Status](https://travis-ci.org/jpnewman/ansible-role-elk-packetbeat.svg?branch=master)](https://travis-ci.org/jpnewman/ansible-role-elk-packetbeat)

This is a Ansible role to installs [packetbeat](https://www.elastic.co/products/beats/packetbeat)

## Requirements

Ansible 2.x

## Role Variables

|Variable|Description|Default|
|---|---|---|
|```packetbeat_version```||1.2.1|
|```packetbeat_version_check```||1.2.1|
|```packetbeat_platform```||amd64|
|```packetbeat_logstash_output```||true|
|```packetbeat_logstash_host```||'localhost:5044'|
|```packetbeat_elasticsearch_host```||'localhost:9200'|
|```packetbeat_protocols_ports```||Array of ```protocol_ports``` objects|
|```packetbeat_redis_host```||'localhost'|
|```packetbeat_enable_icmp```||true|
|```packetbeat_shipper_tags```||[]|
|```packetbeat_ignore_outgoing```||true|
|```packetbeat_refresh_topology_freq```||10|
|```packetbeat_topology_expire```||15|
|```ssl_cert_local_directory```||files/certs|
|```ssl_cert_directory```||/etc/pki/tls/certs|
|```ssl_cert```||logstash-forwarder.crt|
|```certificate_authorities```||'["/etc/pki/tls/certs/logstash-forwarder.crt"]'|
|```apt_cache_valid_time```||600|
|```geoip_database_url_path```||http://geolite.maxmind.com/download/geoip/database|
|```geoip_database_url_filename```||GeoLiteCity.dat.gz|
|```geoip_database_extracted_filename```||GeoLiteCity.dat|
|```geoip_database_paths```||```/usr/share/GeoIP/{{ geoip_database_extracted_filename }}```
|||```/usr/local/var/GeoIP/{{ geoip_database_extracted_filename }}```|


#### ```protocol_ports``` Objects
|Variable|Description|
|---|---|
|```protocol```|Name of protocol|
|```ports```|Array of port numbers|

The default ```protocol_ports``` objects settings are: -

~~~
packetbeat_protocols_ports:
  - protocol: dns
    ports: [53]
  - protocol: http
    ports: [80, 8080, 8000, 5000, 8002]
  - protocol: memcache
    ports: [11211]
  - protocol: mysql
    ports: [3306]
  - protocol: redis
    ports: [6379]
  - protocol: pgsql
    ports: [5432]
  - protocol: thrift
    ports: [9090]
~~~

## Dependencies

none

## Example Playbook

    - hosts: servers
      roles:
         - { role: jpnewman.elk-packetbeat, tags: ["packetbeat"] }

## License

MIT / BSD

## Author Information

John Paul Newman
