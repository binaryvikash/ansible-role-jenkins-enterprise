# ansible-role-jenkins-enterprise

An Ansible role that installs and configures Jenkins on Ubuntu using the official Jenkins repository.

## Features

* Installs OpenJDK 21
* Adds the official Jenkins APT repository
* Installs Jenkins
* Configures Jenkins HTTP port
* Creates a systemd override for Jenkins configuration
* Enables and starts the Jenkins service
* Idempotent execution

## Supported Platforms

* Ubuntu 22.04 (Jammy)
* Ubuntu 24.04 (Noble)

## Requirements

* Ansible 2.17 or later
* Ubuntu 22.04 or later
* Sudo privileges on the target host

## Installation

Install the role from Ansible Galaxy:

```bash
ansible-galaxy role install binaryvikash.jenkins_enterprise
```

## Role Variables

The following variables can be customized.

| Variable             | Default Value  | Description                  |
| -------------------- | -------------- | ---------------------------- |
| jenkins_java_package | openjdk-21-jdk | Java package used by Jenkins |
| jenkins_http_port    | 8080           | Jenkins HTTP port            |
| jenkins_package_name | jenkins        | Jenkins package name         |
| jenkins_service_name | jenkins        | Jenkins service name         |

### Default Values

```yaml
jenkins_java_package: openjdk-21-jdk
jenkins_http_port: 8080
jenkins_package_name: jenkins
jenkins_service_name: jenkins
```

## Example Playbook

```yaml
---
- hosts: jenkins
  become: true

  roles:
    - role: binaryvikash.jenkins_enterprise
      vars:
        jenkins_http_port: 8080
```

## What This Role Does

This role performs the following actions:

1. Installs prerequisite packages.
2. Installs OpenJDK 21.
3. Adds the official Jenkins repository and GPG key.
4. Installs Jenkins.
5. Configures Jenkins through a systemd override.
6. Enables and starts the Jenkins service.
7. Supports repeated executions without unnecessary changes.

## Testing

Run the included test playbook:

```bash
ansible-playbook -i tests/inventory tests/test.yml --become -K
```

Validate the role:

```bash
ansible-lint .
```

## Current Limitations

The following features are planned for future releases:

* Jenkins plugin management with dependency resolution
* Jenkins security hardening
* Initial admin user creation
* Jenkins Configuration as Code (JCasC)
* Job provisioning
* Agent provisioning

## Roadmap

### Version 1.x

* Stable Jenkins installation
* Service management
* Basic configuration

### Version 2.x

* Plugin management
* Security automation
* JCasC support
* Automated Jenkins bootstrap

## License

MIT

## Author

Vikash Kumar Baitha

## Source Code

GitHub Repository:

https://github.com/binaryvikash/ansible-role-jenkins-enterprise
