# Ansible Role: wmi_exporter

[![Build Status](https://img.shields.io/travis/sbaerlocher/ansible.wmi_exporter.svg?branch=master&style=popout-square)](https://travis-ci.org/sbaerlocher/ansible.wmi_exporter) [![license](https://img.shields.io/github/license/mashape/apistatus.svg?style=popout-square)](https://sbaerlo.ch/licence) [![Ansible Galaxy](http://img.shields.io/badge/ansible--galaxy-wmi_exporter-blue.svg?style=popout-square)](https://galaxy.ansible.com/sbaerlocher/wmi_exporter) [![Ansible Role](https://img.shields.io/ansible/role/d/41724.svg?style=popout-square)](https://galaxy.ansible.com/sbaerlocher/wmi_exporter)

## Description

Ansible roles that installs wmi_exporter on a Windows system. Optionally with choco or as package.

## Installation

```bash
ansible-galaxy install sbaerlocher.wmi_exporter
```

## Requirements

## Role Variables

### Version and Architecture

Version and architecture of the wmi exporter to be installed.

```yml
wmi_exporter_version: 0.7.0
wmi_exporter_architecture: amd64
```

### install Parameters

Windows installation parameters for the wmi_exporter. [Link](https://github.com/martinlindhe/wmi_exporter#installation)

As the `--collectors.enabled` flag, provide a comma-separated list of enabled collectors

```yml
wmi_exporter_enabled_collectors:
```

The IP address to bind to. Defaults to 0.0.0.0

```yml
wmi_exporter_listen_addr:
```

The port to bind to. Defaults to 9182.

```yml
wmi_exporter_listen_port:
```

The path at which to serve metrics. Defaults to `/metrics`

```yml
wmi_exporter_metrics_path:
```

As the `--collector.textfile.directory` flag, provide a directory to read text files with metrics from

```yml
wmi_exporter_textfile_dir:
```

Allows passing full CLI flags. Defaults to an empty string.

```yml
wmi_exporter_extra_flags:
```

Whether to ignore existing choco installation and force 'package' type installation. Defaults to `false`.

```yml
wmi_exporter_force_package: false
```

### Global Variable

#### Proxy

If a proxy is in use this information can be used. By default, proxy settings are taken from the default\_\* variables, if they are not defined they are ignored.

```yml
wmi_exporter_proxy: '{{ default_proxy | default(omit) }}'
wmi_exporter_proxy_password: '{{ default_proxy_password | default(omit) }}'
wmi_exporter_proxy_username: '{{ default_proxy_username | default(omit) }}'
wmi_exporter_validate_certs: '{{ default_validate_certs | default(true) }}'
```

### Package

Download directory for the wmi export installations files.

```yml
wmi_exporter_download_directory: "{{ ansible_env.TEMP }}\\wmi_exporter"
```

## Dependencies

## Example Playbook

```yml
- hosts: all
  roles:
    - sbaerlocher.wmi_exporter
```

## Author

- [Simon Bärlocher](https://sbaerlocher.ch)

## License

This project is under the MIT License. See the [LICENSE](https://sbaerlo.ch/licence) file for the full license text.

## Copyright

(c) 2019, Simon Bärlocher
