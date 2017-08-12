# Linux Server Project
### Server Details
IP Address: 18.220.52.108
SSH Port: 2200
Application URL: http://ec2-18-220-52-108.us-east-2.compute.amazonaws.com/

### Installed software and dependencies
* Flask
* Flask-HTTPAuth
* httplib2
* oauth2client
* passlib
* itsdangerous
* SQLAlchemy
* requests
* Apache2
* PostgreSQL
* psycopg2
* mod_wsgi

### Configuration Changes Summary
* Set up an Amazon Lightsail instance running Ubuntu.
* Connected to the instance from local machine using the instance's private key obtained from the Account page
* Ran `sudo apt-get update` followed by `sudo apt-get upgrade` to update all packages
* Configured Lightsail firewall from the Networking tab to allow TCP on port 80, UDP on port 123 and TCP on 220.
* Changed SSH port to 2200 by editing the /etc/ssh/sshd_config file and configured the UFW to allow incoming connections for SSH (port 2200), HTTP (port 80), and NTP (port 123), and deny all other incoming connections (including default SSH port).
* Created a new user account named `grader`, and gave it permission to run sudo through `sudo visudo`
* Used the `ssh-keygen` tool on the local machine to generate an SSH key pair for the grader. Copied the contents of the generated file into the `.ssh` directory of the instance
* Forced key-based authentication by changing the `/etc/ssh/sshd_config` file's `# Change to no to disable tunnelled clear text passwords'` entry to `no`
* Timezone was already configured to UTC
* Ran `sudo apt-get install apache2` to install Apache
* Ran `sudo apt-get install libapache2-mod-wsgi` to install mod_wsgi
* Ran `sudo apt-get install postgresql` to install PostgreSQL
* Created a `catalog` database user by running `CREATE ROLE catalog WITH LOGIN;` after connecting to psql, and allowed it to only create databases
* Created a `catalog` user on the instance and gave it sudo permissions
* Installed git by running `sudo apt-get install git` and cloned the Project 4 repository
* Ran `sudo apt-get install virtualenv` to install virtualenv and created a virtual environment called virtenv to install all Python dependencies required for the application in the virtual environment
* Set up the application appropriately
* Set up a virtual host and created a .wsgi file
* Changed ownership of the project directory to www-data to allow Apache to serve the application
* Restarted Apache by running `sudo service apache2 restart`

### Resources Consulted
* Consulted the tutorial on https://www.digitalocean.com/community/tutorials/how-to-deploy-a-flask-application-on-an-ubuntu-vps to understand setting up a virtual host and writing a .wsgi file
