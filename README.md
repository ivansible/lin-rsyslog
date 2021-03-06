# ivansible.lin_rsyslog

[![Github Test Status](https://github.com/ivansible/lin-rsyslog/workflows/test/badge.svg?branch=master)](https://github.com/ivansible/lin-rsyslog/actions)
[![Ansible Galaxy](https://img.shields.io/badge/galaxy-ivansible.lin__rsyslog-68a.svg?style=flat)](https://galaxy.ansible.com/ivansible/lin_rsyslog/)

This role configures rsyslog service so that some chatty subsystems
are logged in separate log files, and configures rotation of these logs:
- mail services
- firewall (ufw)
- cron
- drupal
- keenetic
- php session cleaner


## Requirements

None


## Variables

    lin_rsyslog_max_journal: 200M
If set, limits maximum size of systemd journal.

    lin_rsyslog_keenetic_ip: ""
IP address of keenetic logger, logs keenetic to dedicated log
(empty value keeps it in common log).

    lin_rsyslog_keenetic_timer: daily
Rotate keenetic log daily or weekly.

    lin_rsyslog_separate_ufw: false
Logs ufw (firewall) messages to dedicated log.

    lin_rsyslog_separate_drupal: false
Logs drupal to dedicated log.

    lin_rsyslog_separate_cron: false
Logs cron to dedicated log.

    lin_rsyslog_thin_php_cleaner: false
Thin out messages of the PHP session cleaner.

    lin_rsyslog_force_rules: false
Force overriding previous rsyslog rules.

    lin_rsyslog_remote_enable: true
Enable logging from remote (internal) hosts in the ferm firewall.


## Tags

- `lin_rsyslog_packages` -- install rsyslog and logrotate
- `lin_rsyslog_fixes` -- fix warnings
- `lin_rsyslog_docker` -- disable kernel logging in docker
- `lin_rsyslog_mail` -- configure mail logging
- `lin_rsyslog_ufw` -- configure ufw logging
- `lin_rsyslog_drupal` -- rotate drupal log
- `lin_rsyslog_keenetic` -- rotate keenetic log
- `lin_rsyslog_cron` -- rotate cron log
- `lin_rsyslog_files` -- ensure log files do exist
- `lin_rsyslog_php` -- thin out php cleaner messages
- `lin_rsyslog_journal` -- limit systemd journal size
- `lin_rsyslog_remote` -- enable logging from internal hosts
- `lin_rsyslog_compress` -- enable/disable compression of rotated logs
- `lin_rsyslog_all` -- all actions


## Dependencies

- [ivansible.lin_base](https://github.com/ivansible/lin-base)
  - this role activates only if global flag `lin_use_rsyslog` is `true`
  - global flag `lin_compress_logs` enables compression of rotated logs


## Example Playbook

    - hosts: host1
      roles:
         - role: ivansible.lin_rsyslog


## License

MIT


## Author Information

Created in 2019-2021 by [IvanSible](https://github.com/ivansible)
