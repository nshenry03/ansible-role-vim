Ansible Role: vim
=================

[![Build Status](https://travis-ci.org/nshenry03/ansible-role-vim.svg?branch=master)](https://travis-ci.org/nshenry03/ansible-role-vim)

Installs VIM

The following roles where designed to neatly work together with this role:

- [user][grog.user], for managing users.
- [authorized-key][grog.authorized-key], for managing authorized-keys.
- [sudo][grog.sudo], for managing sudo rights.

The [management-user][grog.management-user] role combines all these roles in
one easy to use role.

Requirements
------------

- [Ansible 2.5 or later](https://www.ansible.com/blog/loop-plays-past-present-future)

Role Variables
--------------

| Variable                        | Description                                                   | Default value                                                               |
|---------------------------------|---------------------------------------------------------------|-----------------------------------------------------------------------------|
| `vim_bash_support_src`          | Default URL for bash-support archive. Needs to be a tar file  | `https://github.com/WolfgangMehner/bash-support/archive/version-4.3.tar.gz` |
| `vim_bash_support_full_name`    | Default value for bash-support's `AUTHOR` SetMacro            | `YOUR NAME`                                                                 |
| `vim_bash_support_initials`     | Default value for bash-support's `AUTHORREF` SetMacro         | `''`                                                                        |
| `vim_bash_support_email`        | Default value for bash-support's `EMAIL` SetMacro             | `''`                                                                        |
| `vim_bash_support_organization` | Default value for bash-support's `ORGANIZATION` SetMacro      | `''`                                                                        |
| `vim_bash_support_company`      | Default value for bash-support's `COMPANY` SetMacro           | `''`                                                                        |
| `vim_bash_support_copyright`    | Default value for bash-support's `COPYRIGHT` SetMacro         | `Copyright (c) |YEAR|, |AUTHOR|`                                            |
| `vim_bash_support_license`      | Default value for bash-support's `LICENSE` SetMacro           | `GNU General Public License`                                                |
| `vim_bash_support_date_format`  | Default value for bash-support's `DATE` SetFormat             | `%x`                                                                        |
| `vim_bash_support_time_format`  | Default value for bash-support's `TIME` SetFormat             | `%H:%M`                                                                     |
| `vim_bash_support_year_format`  | Default value for bash-support's `YEAR` SetFormat             | `%Y`                                                                        |

See [user][grog.user] role for additional role variables.

#### `user_list` details

`user_list`, `user_list_host` and `user_list_group` are merged when
managing the users. You can use the host and group lists to specify
users per host or group of hosts.

The user list allows you to define which users must be managed. Each item in
the list can have following attributes in addition to those defined in
[grog.user](https://github.com/GROG/ansible-role-user/blob/master/README.md#user_list-details):

| Variable          | Description                                | Required | Default                         |
|-------------------|--------------------------------------------|----------|---------------------------------|
| `full_name`       | User's full name                           | no       | `vim_bash_support_full_name`    |
| `initials`        | User's initials                            | no       | `vim_bash_support_initials`     |
| `email`           | User's email                               | no       | `vim_bash_support_email`        |
| `organization`    | User's organization                        | no       | `vim_bash_support_organization` |
| `company`         | User's company                             | no       | `vim_bash_support_company`      |
| `copyright`       | Copyright to use in VIM templates for user | no       | `vim_bash_support_copyright`    |
| `license`         | License to use in VIM templates for user   | no       | `vim_bash_support_license`      |
| `vim_date_format` | VIM date format to use for user            | no       | `vim_bash_support_date_format`  |
| `vim_time_format` | VIM time format to use for user            | no       | `vim_bash_support_time_format`  |
| `vim_year_format` | VIM year format to use for user            | no       | `vim_bash_support_year_format`  |

###### Example `user_list`

```yaml
user_list:
  - name: user1
  - name: user2
    uid: 1001
    groups:
      - test
      - sudo
  - name: user3
    uid: 1002
    state: absent
  - name: jdoe
    full_name: John Doe
    initials: JD
    email: john.doe@example.com
    organization: Acme, Inc.
```

Dependencies
------------

-   [grog.user][grog.user]

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: all
      roles:
         - src: https://github.com/nshenry03/ansible-role-vim

License
-------

MIT

Author Information
------------------

This role was created in 2018 by [Nick Henry](http://TechNickal.net).
