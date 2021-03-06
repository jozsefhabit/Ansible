<!-- START doctoc generated TOC please keep comment here to allow auto update -->

<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

**Table of Contents**  _generated with [DocToc](https://github.com/thlorenz/doctoc)_

-   [ansible-openstack-dashboard](#ansible-openstack-dashboard)
    -   [Requirements](#requirements)
    -   [Role Variables](#role-variables)
    -   [Dependencies](#dependencies)
    -   [Example Playbook](#example-playbook)
    -   [License](#license)
    -   [Author Information](#author-information)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# ansible-openstack-dashboard

An [Ansible](https://www.ansible.com) role to install/configure [OpenStack Dashboard](https://docs.openstack.org/ocata/install-guide-ubuntu/horizon-install.html)

## Requirements

None

## Role Variables

```yaml
---
# defaults file for ansible-openstack-dashboard

# List of names or IP addresses of the hosts running the dashboard.
openstack_dashboard_allowed_hosts:
  - '*'

openstack_dashboard_debug: false

# default, ubuntu, material
openstack_dashboard_default_ubuntu_theme: 'default'

# Configure these for your outgoing email host
openstack_dashboard_email: []
  # host_password: 'top-secret!'
  # host_user: 'djangomail'
  # host: 'smtp.my-company.com'
  # port: 25

# Overrides for OpenStack API versions. Use this setting to force the
# OpenStack dashboard to use a specific API version for a given service API.
# Versions specified here should be integers or floats, not strings.
# NOTE: The version should be formatted as it appears in the URL for the
# service API. For example, The identity service APIs have inconsistent
# use of the decimal point, so valid options would be 2.0 or 3.
# Minimum compute version to get the instance locked status is 2.9.
openstack_dashboard_openstack_api_versions:
  identity: 3
  image: 2
  volume: 2

# The hostname of the Identity service server used for authentication if you
# only have one region.
openstack_dashboard_openstack_host: '127.0.0.1'

# Defines if Neutron networking provides layer 3 functionality and self-service
# networks. This would be if selecting option 2 from the setup guides
# https://docs.openstack.org/ocata/install-guide-ubuntu/neutron-controller-install-option2.html
openstack_dashboard_enable_neutron_l3: false

# Overrides the default domain used when running on a single-domain model with
# version 3 of the Identity service. All entities will be created in the default
# domain
openstack_dashboard_openstack_keystone_default_domain: 'Default'

# The role to be assigned to a user when they are added to a project. The
# value must correspond to an existing role name in the Identity service.
# In general, the value should match the member_role_name defined in keystone.conf.
openstack_dashboard_openstack_keystone_default_role: '_member_'

# Set this to True if running on a multi-domain model. When this is enabled, it
# will require the user to enter the Domain name in addition to the username
# for login.
openstack_dashboard_openstack_keystone_multidomain_support: false

openstack_dashboard_memcached_servers:
  - '127.0.0.1'

openstack_dashboard_site_branding: 'OpenStack Dashboard'
```

## Dependencies

None

## Example Playbook

```yaml
---
- hosts: openstack_controllers
  vars:
  roles:
    - role: ansible-openstack-dashboard
  tasks:
```

## License

MIT

## Author Information

Larry Smith Jr.

-   [@mrlesmithjr](https://www.twitter.com/mrlesmithjr)
-   [EverythingShouldBeVirtual](http://www.everythingshouldbevirtual.com)
-   mrlesmithjr [at] gmail.com
