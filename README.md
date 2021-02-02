dnsmasq_exporter Ansible role
=========
This role will install and configure Google's [dnsmasq_exporter](https://github.com/google/dnsmasq_exporter).

## Usage

Use it in a playbook as follows:
```yaml
- hosts: all
  roles:
    - stuart.dnsmasq_exporter
```

All variables which can be overridden are stored in [defaults/main.yml](defaults/main.yml) file as well as in table below.

| Name           | Default Value | Description                        |
| -------------- | ------------- | -----------------------------------|
|`dnsmasq_exporter_pkg_location`|none|URL where the executable can be downloaded from. PLEASE SPECIFY!|
|`dnsmasq_exporter_install_dir`|"/usr/local/bin"|Base dir where the exporter will be placed|
|`dnsmasq_exporter_svc_enabled`|true|Enable systemd service for the exporter at boot|
|`dnsmasq_exporter_listen`|"localhost:9153"|`IP:PORT` to bind|
|`dnsmasq_exporter_system_user`|"prometheus"|User that will run the exporter|
|`dnsmasq_exporter_system_group`|"prometheus"|Group that will run the exporter|
|`dnsmasq_exporter_consul_discovery_enabled`|true|If true, it will enable service discovery through Consul|
|`dnsmasq_exporter_leases_path`|"/var/lib/misc/dnsmasq.leases"|Path to dnsmasq DHCP lease file|

All the metrics are exported `http://{{dnsmasq_exporter_listen}}/metrics`

## Limitations

It currently supports only a binary served from S3 as the mean of installation

