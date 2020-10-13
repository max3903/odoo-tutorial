# Install Odoo dependencies

```bash
$ sudo apt install git libffi-dev libgeoip-dev libjpeg-dev libldap2-dev libsasl2-dev \
  libxml2-dev libxslt1-dev node-less postgresql postgresql-server-dev-13 python3-dev \
  python3-pip python3-psycopg2 python3-venv python3-wheel wkhtmltox zlib1g-dev
```

# PostgreSQL
 
* Create a PostgreSQL user for Odoo (odoo/odoo):

```bash
$ createuser --superuser --createdb --username postgres --no-createrole --pwprompt odoo
```

# Odoo

* Clone the repository

```bash
$ git clone https://github.com/max3903/odoo-tutorial.git
```

* Create the environment

```bash
$ cd odoo-tutorial
$ python3 -m venv env
$ . env/bin/activate
(env)$ pip install -r requirements.txt
```

* Create odoo.conf with:

```editorconfig
[options]
addons_path = /$HOME/odoo-tutorial/custom-addons
admin_passwd = admin
db_host = localhost
db_port = 5432
db_password = odoo
db_user = odoo
```

* Start Odoo

```bash
(env)$ odoo -c odoo.conf
```
