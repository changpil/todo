
# initalization
python3 manage.py makemigrations todo

python3 manage.py migrate

tdnf install mysql

#Running mysql in Photon
1. tdnf install mysql
2. useradd mysql; groupadd mysql
3. mkdir -p /var/lib/mysql/; chown mysql:mysql -R /var/lib/mysql
4. mkdir -p /var/log/mysql/; chown mysql:mysql -R /var/log/mysql
5. create conf file
  a. mkdir -p /etc/mysql/
  b. Create mysqld.cnf file in /etc/mysql/ folder.

      [mysqld_safe]
      socket		= /var/run/mysqld/mysqld.sock
      nice		= 0

      [mysqld]
      user		= mysql
      pid-file	= /var/run/mysqld/mysqld.pid
      socket		= /var/run/mysqld/mysqld.sock
      port		= 3306
      basedir		= /usr
      datadir		= /var/lib/mysql
      tmpdir		= /tmp
      lc-messages-dir	= /usr/share/mysql
      skip-external-locking
      bind-address		= 127.0.0.1
      key_buffer_size		= 16M
      max_allowed_packet	= 16M
      thread_stack		= 192K
      thread_cache_size       = 8
      myisam-recover-options  = BACKUP
      query_cache_limit	= 1M
      query_cache_size        = 16M
      log_error = /var/log/mysql/error.log
      expire_logs_days	= 10
      max_binlog_size   = 100M


6. mysqld  --user=root &;   mysqld_safe --skip-grant-tables &

7. python3 manage.py runserver 0.0.0.0:8000



