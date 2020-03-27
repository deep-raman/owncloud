owncloud
========

This role installs and configures private cloud server owncloud on a specified host, with MySQL database 
as a backend and apache webserver with ssl support using self-signed certificate.

Example Playbook
----------------


For the direct one line command installation on localhost use :

	ansible-playbook --connection=local --inventory 127.0.0.1, owncloud.yaml --tags install

Uninstall :

	ansible-playbook --connection=local --inventory 127.0.0.1, owncloud.yaml --tags uninstall
	* Use with caution as it will delete the following directories : /etc/apache2, /etc/mysql/ , /var/lib/mysql, /var/www/html/owncloud


Tested on
---------

	- Rasberry pi buster (Linux raspberrypi 4.19.97-v7+)


Requirements :

	- ansible 2.7.7
	- python-pexpect
	- python-pymysql

Author Information
------------------

	Raman Deep
	27th March 2020
	deep.raman85@gmail.com
