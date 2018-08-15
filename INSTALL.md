# Install Odoo dependencies

`$ sudo apt install libffi-dev libgeoip-dev libjpeg-dev libldap2-dev libsasl2-dev libxml2-dev libxslt1-dev node-less postgresql postgresql-server-dev-9.5 python-dev python-pip python-psycopg2 zlib1g-dev`

# Webkit

* Download Webkit from http://download.gna.org/wkhtmltopdf/0.12/0.12.1/wkhtmltox-0.12.1_linux-trusty-amd64.deb
* Install Webkit and create a symlink:

`# ln -s /usr/local/bin/wkhtmltopdf /usr/bin/wkhtmltopdf`

# PostgreSQL
 
* Create a PostgreSQL user for odoo:

```
$ createuser -s odoo
```

# Odoo

* Create an Odoo user
* Clone the repository
* Change the ownership of the repo to odoo
* Create the environment

`$ virtualenv env && . env/bin/activate && pip install -r requirements.txt`

* Enable and start Odoo

`(env)$ odoo -c odoo.conf`
