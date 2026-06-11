# ansible-role-jenkins-enterprise

An Ansible role that installs and configures Jenkins using the official Jenkins repository.

## Features

* Installs OpenJDK 21
* Adds the official Jenkins APT repository
* Installs Jenkins
* Configures Jenkins HTTP port
* Enables and starts the Jenkins service
* Uses systemd overrides for configuration
* Idempotent execution

## Requirements

* Ubuntu 22.04 (Jammy) or later
* Ansible 2.17+

## Role Variables

Default values are defined in `defaults/main.yml`.

| Variable             | Default        |
| -------------------- | -------------- |
| jenkins_java_package | openjdk-21-jdk |
| jenkins_http_port    | 8080           |
| jenkins_package_name | jenkins        |
| jenkins_service_name | jenkins        |

## Example Playbook

```yaml
- hosts: jenkins
  become: true

  roles:
    - role: binaryvikash.ansible_role_jenkins_enterprise
      vars:
        jenkins_http_port: 9090
```

## Testing

```bash
ansible-playbook -i tests/inventory tests/test.yml --become -K
```

## Roadmap

* Plugin management
* Security configuration
* Admin user creation
* Job provisioning

## License

MIT

## Author

Vikash Kumar Baitha
