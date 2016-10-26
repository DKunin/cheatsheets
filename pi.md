## Cron logging

By default, the logging for the cron demon is not enabled in Debian (I assume it is the system you are using). To enable it, please open the file /etc/rsyslog.conf via

    $ vi /etc/rsyslog.conf
and uncomment the line

    # cron.*                          /var/log/cron.log
After that, you need to restart rsyslog via

    $ /etc/init.d/rsyslog restart
and you will find the cron logs in /var/log/cron.log