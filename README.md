owncloud
========

This role installs and configures private cloud server owncloud on a specified host, with mariadb database 
as a backend and apache webserver with ssl support using self-signed certificate and the latest php.


Role variables
--------------

Available variables are listed below, along with default values (see defaults/main.yml):

	OWNCLOUD_FILE: "owncloud-10.4.0.tar.bz2"
	OWNCLOUD_URL: "https://download.owncloud.org/community/{{ OWNCLOUD_FILE }}"
	APACHE_CONF_LOCAL: "owncloud.conf.j2"
	APACHE_CONF: "owncloud.conf"
	APACHE_SSL_CONF_LOCAL: "owncloud-ssl.conf.j2"
	APACHE_SSL_CONF: "owncloud-ssl.conf"
	APACHE_SERVER_NAME: "192.168.1.55"
	APACHE_DOCUMET_ROOT: "/var/www/html/owncloud/"
	SSL_CRT_PATH: "/etc/ssl/certs"
	SSL_KEY_PATH: "/etc/ssl/private"
	SSL_CSR_PATH: "/etc/ssl/csr"
	SSL_CRT: "owcloud-selfsigned.crt"
	SSL_CSR: "owcloud-selfsigned.csr"
	SSL_KEY: "owcloud-selfsigned.key"
	SSL_COUNTRY: "ES"
	SSL_COMMON_NAME: "{{ APACHE_SERVER_NAME }}"

Tags
-----

	install : Use this tag for the installation of all the components.
	install_owncloud : Use this tag to download only the owncloud tar file and uncompress it under /var/www/html/
	install_apache: Use thiis tag to install only the apache2.x and the required modules.
	install_mariadb: Use this tag to intall the mariadb latest version.
	install_php: Use this tag to install the latest version of php and the required modules.
	uninstall : Use this tag to remove completely all the components.


Example Playbook
----------------

	- hosts: all
      roles:
         - { role: owncloud, tags: "owncloud" }
      become: true

For the direct one line command installation on localhost use :

	ansible-playbook --connection=local --inventory 127.0.0.1, owncloud.yaml --tags install

Uninstall :

	ansible-playbook --connection=local --inventory 127.0.0.1, owncloud.yaml --tags uninstall
	
	* Use with caution as it will delete the following directories :

		/etc/apache2
		/etc/mysql/
		/var/lib/mysql
		/var/www/html/owncloud


Tested on
---------

	- Raspberry pi buster (Linux raspberrypi 4.19.97-v7+)


Requirements :

	- ansible 2.7.7
	- python-pexpect
	- python-pymysql

Author Information
------------------

	Raman Deep
	27th March 2020
	deep.raman85@gmail.com
