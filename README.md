# Ansible Role: ocstore-backup

Backup ocStore on Linux.

## Requirements

None.

## Role Variables

Available variables are listed below, along with default values:

ocstore_backup_dir: "backup/yourdmain"

ocstore_backup_keep: 7

ocstore_backup_to: "/var/tmp"
ocstore_backup_prefix: ""

ocstore_mysql_databases: []
ocstore_backup_from: []

ocstore_backup_dumps_dir: "sql"
ocstore_backup_files_dir: "files"

## Dependencies

None.

## Example Playbook

    - hosts: all
      roles:
        - Akman.ocstore-backup

*Inside `vars/main.yml`*:

ocstore_mysql_databases:
  - name: "ocstore"
    encoding: utf8
    collation: utf8_general_ci

ocstore_backup_dir: "backup/ocstore"

ocstore_backup_keep: 7

ocstore_backup_to: "/var/tmp/ocstore"
ocstore_backup_prefix: "ocstore_"

ocstore_backup_dumps_dir: "sql"
ocstore_backup_files_dir: "shared"

ocstore_backup_from:
  - path: "/var/www/ocstore/shared/"
    filter:
      - "+ /download/"
      - "+ /image/"
      - "- /image/cache/"
      - "- /*/"
      - "- /*"
      - "- index.html"
      - "- .htaccess"

## License

MIT / BSD

## Author Information

This role was created in 2017 by Alexander Kapitman
