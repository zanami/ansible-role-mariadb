MariaDB55
========

This role installs MariaDB 5.5 on Debian Wheezy.
It also installs python-mysqldb.

On first run, the test database and test user is removed.
A .my.cnf config file is written in /root so you can connect without
entering a password with any mariadb/mysql client as user root.

Requirements
------------

Debian Wheezy with the package python-pycurl and python-software-properties installed.

Role Variables
--------------

All the following variables are set in defaults.

Obviously, the mariadb_root_password would be a good candidate to set.
_if you add passwords to a version control system, use ansible-vault, or git-crypt_

Because this role is for a clean install - it assumes an empty root password.
The tasks for resetting the root password are only run on install/first activation of the service.

    # The root password is set, and added to .my.cnf for the root user
    mariadb_root_password: "secret"

    mariadb_base_dir: "/usr"
    mariadb_bind_address: "127.0.0.1"
    mariadb_charsets_dir: "/usr/share/mysql/charsets"
    mariadb_config: "/etc/mysql/my.cnf"
    mariadb_data_dir: "/var/lib/mysql"
    mariadb_install_db_bin: "/usr/bin/mysql_install_db"
    mariadb_log_bin: false
    mariadb_long_query_time: 10
    mariadb_mysql_errorlog: "/var/log/mysql/mysql.err"
    mariadb_mysqld_errorlog: "/var/log/mysql/mysqld.err"
    mariadb_mysqld_slowlog: "/var/log/mysql/mysqld.slow"
    mariadb_pid: "/var/run/mysqld/mysqld.pid"
    mariadb_port: 3306
    mariadb_query_cache_limit: false  # 128K
    mariadb_query_cache_size: false   # 64M
    mariadb_root_password: "secret"
    mariadb_server_id: 1
    mariadb_share_dir: "/usr/share/mysql"
    mariadb_skip_charset_handshake: true
    mariadb_skip_networking: false
    mariadb_socket: "/var/run/mysqld/mysqld.sock"
		mariadb_databases: []
		mariadb_users: []

Example Playbook
----------------

    - hosts: servers
      roles:
         - { role: f500.mariadb55, mariadb_root_password: some_random_string }

License
-------

LGPLv3

Author Information
------------------

Jasper N. Brouwer, jasper@nerdsweide.nl

Ramon de la Fuente, ramon@delafuente.nl
