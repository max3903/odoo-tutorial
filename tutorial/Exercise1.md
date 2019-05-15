# Exercise 1

We will create a first module to add a phone extension field on the partner record.

## Step 1

* Create a directory `phone_extension` in custom-addons
* Within that directory, create an empty file `__init__.py`
* Create the manifest file `__manifest__.py` with:

```python
# Copyright 2018 Open Source Integrators
# License AGPL-3.0 or later (https://www.gnu.org/licenses/agpl).
{
    'name': 'Phone extension',
    'summary': 'Store the phone extension of your contacts',
    'version': '11.0.1.0.0',
    'development_status': 'Alpha',
    'category': 'Contacts',
    'website': 'https://github.com/max3903/odoo-tutorial',
    'author': 'Open Source Integrators, Odoo Community Association (OCA)',
    'maintainers': ['max3903'],
    'license': 'AGPL-3',
    'application': False,
    'installable': True,
    'depends': [
        'contacts',
    ],
}
```
* Create the `readme` folder for the documentation
* Restart Odoo
* Activate the developer mode
* Update the Apps list
* Search for your module
* Open the record and check the information

## Step 2

* Create the following directories:

```bash
$ mkdir models views demo
```

### Models

* Edit `__init__.py` to have:

```python
from . import models
```

* In models, create a `__init__.py` file with:

```python
from . import res_partner
```

* In models, create a `res_partner.py` file with:

```python
from odoo import fields, models


class ResPartner(models.Model):
    _inherit = 'res.partner'

    phone_extension = fields.Integer('Phone Extension')
```

### Views

* In views, create a `res_partner_view.xml` file with:

```xml
<?xml version="1.0"?>
<odoo>
    <record id="res_partner_view_form" model="ir.ui.view">
        <field name="name">Phone Extension</field>
        <field name="model">res.partner</field>
        <field name="inherit_id" ref="base.view_partner_form"/>
        <field name="arch" type="xml">
            <field name="phone" position="after">
                #<field name="phone_extension"/>
            </field>
        </field>
    </record>
</odoo>
```

* Update the `__manifest__.py` file to add the `data` keyword:

```python
    'data': [
        'views/res_partner_view.xml',
    ], 
```

### Demo data

* In demo, create a `res_partner_demo.xml` file with:

```xml
<?xml version="1.0"?>
<odoo>
    <record id="base.res_partner_12" model="res.partner">
        <field name="phone_extension">123</field>
    </record>
</odoo>
```

* Update the `__manifest__.py` file to add the `demo` keyword:

```python
    'demo': [
        'demo/res_partner_demo.xml',
    ], 
```

* Restart Odoo
* Update the Apps list
* Upgrade your module

## Step 3

### Security

```bash
$ mkdir security
```

* In security, create a `phone_extension.xml` file with:

```xml
<?xml version="1.0"?>
<odoo>
    <record id="group_phone_extension" model="res.groups">
        <field name="name">Phone Extension Group</field>
    </record>
    
    <record id="base.group_erp_manager" model="res.groups">
        <field name="implied_ids"
               eval="[(4, ref('group_phone_extension'))]"/>
    </record>
    
</odoo>
```

* Update the `__manifest__.py` file to have:

```python
    'data': [
        'security/phone_extension.xml',
        'views/res_partner_view.xml',
    ]
 ```
 
* Update the view to only show the extension to the new group:

```xml
<?xml version="1.0"?>
<odoo>
    <record id="res_partner_view_form" model="ir.ui.view">
        <field name="name">Phone Extension</field>
        <field name="model">res.partner</field>
        <field name="inherit_id" ref="base.view_partner_form"/>
        <field name="arch" type="xml">
            <field name="phone" position="after">
                #<field name="phone_extension"
                        groups="phone_extension.group_phone_extension"/>
            </field>
        </field>
    </record>
</odoo>
```

* Restart Odoo
* Update the Apps list
* Upgrade your module

## Step 3

### Reports

```bash
$ mkdir report
```

* In report, create a `report_due_payment.xml` file with:

```xml
<?xml version="1.0"?>
<odoo>
    <record id="report_due_payment_phone_extension" model="ir.ui.view">
        <field name="name">Payment Due with Phone extension</field>
        <field name="model">res.partner</field>
        <field name="inherit_id" ref="	account.report_overdue_document"/>
        <field name="arch" type="xml">
            <xpath expr="//t/div/div/p/" position="inside">
                Phone: <field name="phone"/> #<field name="phone_extension"/>
            </xpath>
        </field>
    </record>
</odoo>
```

* Update the `__manifest__.py` file to have:

```python
    'data': [
        'security/phone_extension.xml',
        'views/res_partner_view.xml',
        'report/report_due_payment.xml',
    ]
    'depends': ['contacts, 'account']
 ```
 
* Restart Odoo
* Update the Apps list
* Upgrade your module
