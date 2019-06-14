# Udacity Item Catalog Web Application

This is a README for a web application of an item catalog written for the
Udacity Full Stack Web Developer Nanodegree.

---

To access the web application, go to the URI:

    [54.184.75.80](http:54.184.75.80 "John Robert Legro's Web Application")

This will take you to the homepage of the Item Catalog to view in a Web
browser! The application is served on port 80, for your information.

To access the server via the command line there has been a user of "grader"
created and set up for use by using this command:

    ssh -i [location of "grader" ssh key] grader@54.184.75.80 -p 2200

The password for the "grader" user is "grader". The user "grader" does have
sudo capabilities, and the only way to login to the server is via SSH key.

Note that there is a `-p 2200` flag used to designate logging in on port 2200.
The SSH port is not default, but has been changed to port 2200.
This is the only port available for SSH login.

*It is also not possible to login to the server as root for security purposes.*

---

## Dependencies Needed For Web Application To Run

This is a list of the dependencies needed for the web application to run.
These dependencies have been installed in the virtual environment used for
production of this application, but would need to be installed in any other
environment if trying to execute web application.

    python3
    python3-pip
    apache2
    flask
    postgresql
    sqlite
    oauth2client
    sqlalchemy
    libapache2-mod-wsgi-py3
    requests

---

## How To Install & Configure Apache2 server

First login to the server via the command line using this command, and then
enter the "grader" password of "grader":

    ssh -i [location of "grader" ssh key] grader@54.184.75.80 -p 2200

Then change directories to where the `catalog2.conf` file is located and open
for editing by using this command:

    sudo nano /etc/apache2/sites-available/catalog2.conf

When you are in the nano editor for the `/etc/apache2/sites-available/catalog2.conf` file, enter this code:

```
<VirtualHost *:80>
            ServerName 54.184.75.80
            ServerAdmin JRLegro@gmail.com
            WSGIScriptAlias / /var/www/Catalog2/catalog2.wsgi
            <Directory /var/www/Catalog2/>
                    Order allow,deny
                    Allow from all
            </Directory>
            Alias /static /var/www/Catalog2/static
            <Directory /var/www/Catalog2/static/>
                    Order allow,deny
                    Allow from all
            </Directory>
            Alias /templates /var/www/Catalog2/templates
            <Directory /var/www/Catalog2/templates/>
                    Order allow,deny
                    Allow from all
            </Directory>
            ErrorLog ${APACHE_LOG_DIR}/error.log
            LogLevel warn
            CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>
```

Then save the file by pressing `Control-O` and exit the editor by pressing
`Control-X`.

## How To Install & Configure .wsgi file

Once logged in to the server, change directories for editing the `.wsgi` file
by using this command:

      sudo nano /var/www/Catalog2/catalog2.wsgi

Then you should be in the nano editor. Enter this text in that file as you see it here:

    ```
    #!/usr/bin/python3
    import sys
    import logging
    logging.basicConfig(stream=sys.stderr)
    sys.path.insert(0,"/var/www/Catalog2")

    from __init__ import app as application
    # app.secret_key = 'Woosie'
    ```

Then save the file by pressing `Control-O` and exit the editor by pressing
`Control-X`.

Restart the Apache2 service by using this command:

    sudo service apache2 restart

---

## Resources Used For Deployment Of Web Application

    <https://www.digitalocean.com/community/tutorials/how-to-configure-the-apache-web-server-on-an-ubuntu-or-debian-vps>

    <http://flask.pocoo.org/docs/0.12/deploying/mod_wsgi/>

    <https://study-hall.udacity.com/conversations/community:conversation:105080404-434038576?contextType=room>
