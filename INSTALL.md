# Install Odoo dependencies

```bash
$ sudo apt install libffi-dev libgeoip-dev libjpeg-dev libldap2-dev libsasl2-dev libxml2-dev libxslt1-dev node-less postgresql postgresql-server-dev-9.5 python-dev python-pip python-psycopg2 zlib1g-dev
$ sudo pip install virtualenv
```

# Webkit

* Download Webkit from http://download.gna.org/wkhtmltopdf/0.12/0.12.1/wkhtmltox-0.12.1_linux-trusty-amd64.deb
* Install Webkit and create a symlink:

`# ln -s /usr/local/bin/wkhtmltopdf /usr/bin/wkhtmltopdf`

# PostgreSQL
 
* Create a PostgreSQL user for Odoo (odoo/odoo):

```bash
$ createuser --superuser --createdb --username postgres --no-createrole --pwprompt odoo
```

# Odoo

* Clone the repository

`$ git clone https://github.com/max3903/odoo-tutorial.git`

* Create the environment

```bash
$ cd odoo-tutorial
$ virtualenv env && . env/bin/activate && pip install -r requirements.txt
```

* Create odoo.conf with:

```python
[options]
addons_path=/$HOME/odoo-tutorial/custom-addons
admin_passwd = admin
db_host = localhost
db_port = 5432
db_password = odoo
db_user=odoo
```

* Start Odoo

```bash
(env)$ odoo -c odoo.conf
```
