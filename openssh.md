# Ubuntu Linux: Start OpenSSH Server

Type the following command:
  `$ sudo /etc/init.d/ssh start`
OR
$ `sudo service ssh start`

For systemd based Ubuntu Linux 16.04/18.04/20.04 LTS or above servers, run:
$ `sudo systemctl start ssh`

Ubuntu Linux: Stop OpenSSH server

Type the following command:
$ `sudo /etc/init.d/ssh stop`

OR
$ `sudo service ssh stop`

Again for systemd based Ubuntu Linux 16.04/18.04/20.04 LTS or above server, enter:
$ `sudo systemctl stop ssh`

Ubuntu Linux: Restart OpenSSH server

Type the following command:
$ `sudo /etc/init.d/ssh restart`

OR
$ `sudo service ssh restart`

For systemd based Ubuntu Linux 16.04/18.04/20.04 LTS or above server, execute:
$ `sudo systemctl restart ssh`


# Ubuntu Linux: See status of OpenSSH server

Type the following command:
$ `sudo /etc/init.d/ssh status`

## OR ##
$ `sudo service ssh status`

OR for systemd based Ubuntu Linux 16.04 LTS or above server:
$ `sudo systemctl status ssh`



## 参考
https://www.cyberciti.biz/faq/howto-start-stop-ssh-server/
