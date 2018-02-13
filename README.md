# ansible-role-beanstalkd

[![Build Status](https://travis-ci.org/shengyou/ansible-role-beanstalkd.svg?branch=master)](https://travis-ci.org/shengyou/ansible-role-beanstalkd)

=========

安裝 beanstalkd。

* Ubuntu 14.04, 16.04
* CentOS 6, 7

使用時需注意 CentOS 與 Ubuntu 的 beanstalkd config 並不相同，因此如果需要針對 config 做高度的客製，請自行預備 config 並搭配 variables `custom_config_src` 使用。

Requirements
------------

* ansible >= 2.4
* python >= 2.6

Role Variables
--------------

有三個 default variables，可根據實際狀況覆蓋為其他參數。

```
BEANSTALKD_LISTEN_ADDR: 0.0.0.0
BEANSTALKD_LISTEN_PORT: 11300
BEANSTALKD_BINLOG: "/var/lib/beanstalkd"
```

或者你也可以直接用 `custom_config_src:` 完全用你自己的 config 覆蓋 default config。


Example Playbook
----------------

```
- name: default_provision.yml
  hosts: your_host
  gather_facts: yes
  become: yes

  vars:
    BEANSTALKD_LISTEN_ADDR: false
    BEANSTALKD_LISTEN_PORT: 9000
    BEANSTALKD_EXTRA: "-b /var/lib/beanstalkd_temp"

  roles:
    - ansible-role-beanstalkd
```

或

```
- name: default_provision.yml
  hosts: your_host
  gather_facts: yes
  become: yes

  vars:
    custom_config_src: "your_path_to_beanstalkd_config"

  roles:
    - ansible-role-beanstalkd
```


License
-------

MIT
