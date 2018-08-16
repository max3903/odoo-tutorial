# Odoo Tutorial

This is a step-by-step tutorial to discover how to create Odoo modules.

For more information, please read:

* [Odoo documentation](https://www.odoo.com/documentation/11.0/index.html)
* [OCA Guidelines](https://github.com/OCA/maintainer-tools/blob/master/CONTRIBUTING.md)

## Prerequisites

Look at the [INSTALL](./INSTALL.md) file.

## Exercise 1

We will create a first module to add a phone extension field on the partner record.

### Step 1

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
* Upgrade the module list
* Search for your module
* Open the record and check the information
