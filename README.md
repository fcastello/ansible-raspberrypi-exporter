Role Name
=========

Ansible role to install prometheus exporter for raspberry pi metrics using prometheus node exporter textfile collector. This exporter is based on the work from https://github.com/fahlke/raspberrypi_exporter with a couple of modifications to make it work in ubuntu and with options to change default configuration for the text file and where commands are installed.

Requirements
------------

- systemd installed
- vcgencmd (for ubuntu systems it will install the package, raspbian should have it already)


Role Variables
--------------

```yaml
# Path where to install the exporter script
raspberrypi_exporter_script_path: /usr/local/bin
# Path the textfile collector file will be written
raspberrypi_exporter_textcollector_path: /var/lib/node_exporter/textfile_collector/
# Filename the textfile collector file will be written
raspberrypi_exporter_textcollector_file: raspberrypi-metrics.prom
# Systemd default directory
raspberrypi_exporter_systemd_dir: /etc/systemd/system

# Prefix for the metrics
raspberrypi_exporter_metrics_prefix: rpi_

# How ofter to collect metrics
# this is in systemd timer format
# By default it collects every 15 seconds
raspberrypi_exporter_metrics_timer: "*:*:0,15,30,45"
```

Example Playbook
----------------

```yaml
- hosts: all
 - name: Raspberry pi exporter
    import_role:
      name: fcastello.raspberrypi_exporter
```

Limitations
-----------

- Tested with Ubuntu 18.04 only

License
-------

MIT
