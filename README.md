# consul-template role

Ansible role to install, configure and run consul-template as a service.  The role also installs user specified consul-template templates.

## Requirements

* consul-template version 0.18+

## Example

### Copy templates and install and start consul-template as a service

```yaml
- hosts: myhost

  vars:
    consul_template_version: 0.18.5
    consul_template_consul_address: "<consulhost:consulport>"

  roles:
    - role: wunzeco.consul-template
      consul_template_template:
        source: "/data/nginx/templates/jenkins-8080-include.conf.ctmpl"
        destination: "/data/nginx/includes/common/jenkins-8080.conf"

    - role: wunzeco.consul-template
      consul_template_template:
        source: "/data/nginx/templates/jenkins-8080-upstream.conf.ctmpl"
        destination: "/data/nginx/upstream/jenkins-8080.conf"
```

## Testing

To run this role's integration tests

```bash
kitchen test
```

## Dependencies

none

## Outstanding

* redirect consul-template logs to file for service started by systemd
