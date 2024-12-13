Install and configure infrastructure with Ansible using the command below:
ansible-playbook infra.yaml

Backup restoration instructions:
All the restoration process is made through the root user.

  For restoring MySQL agama data:
    Open console on MySQL master node and use the below listed commands:
    rm -rf /home/backup/restore/mysql/*
    sudo -u backup duplicity --no-encryption restore rsync://timnet238@backup.clickit.io/mysql/ /home/backup/restore/mysql/
    mysql agama < /home/backup/restore/mysql/agama.sql
    
  * The error "Error '[Errno 1] Operation not permitted" does not affect the success of the backup operation and must be ignored.

  
  For restoring InfluxDB telegraf data:
    Open console on InfluxDB node and use the below listed commands:
    systemctl stop telegraf
    influx -execute 'DROP DATABASE telegraf'
    sudo -u backup duplicity --no-encryption restore rsync://timnet238@backup.clickit.io/influxdb/ /home/backup/restore/influxdb/
    influxd restore -portable -database telegraf /home/backup/restore/influxdb/
    systemctl start telegraf
    
Checking results instructions:
  For agama:
    On MySQL node use the command below:
    mysql -e 'SHOW DATABASES'
  For telegraf:
    On InfluxDB node use the command below:
    influx -execute 'show databases'
