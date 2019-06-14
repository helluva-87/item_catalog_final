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

**Dependencies Needed For Web Application To Run**

This is a list of the dependencies needed for the web application to run.
These dependencies have been installed in the virtual environment used for
production of this application, but would need to be installed in any other
environment if trying to execute web application.

    python3
    python3-pip
    flask
    postgresql
    sqlite
    oauth2client
    sqlalchemy
    libapache2-mod-wsgi-py3
    requests

---

## Resources Used For Deployment Of Web Application

    <https://www.digitalocean.com/community/tutorials/how-to-configure-the-apache-web-server-on-an-ubuntu-or-debian-vps>

    <http://flask.pocoo.org/docs/0.12/deploying/mod_wsgi/>
