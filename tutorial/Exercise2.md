```
#!/usr/bin/python
  
import xmlrpc.client as xmlrpclib

user = 'admin' #the user
pwd = 'admin'      #the password of the user
db = 'Demo'    #the database
server = 'localhost'
port = '8069'

# OpenERP Common login Service proxy object 
sock_common = xmlrpclib.ServerProxy ('http://'+server+':'+port+'/xmlrpc/common')
uid = sock_common.login(db, user, pwd)

sock = xmlrpclib.ServerProxy('http://'+server+':'+port+'/xmlrpc/2/object')

record_object = 'product.template'
record_filter = [[]]
new_values = {
    'taxes_id': [[5]],
    'supplier_taxes_id': [[5]]
}

record_ids = sock.execute_kw(db, uid, pwd, record_object, 'search', record_filter)

res = sock.execute_kw(db, uid, pwd, record_object, 'write', [record_ids, new_values])

exit(0)
