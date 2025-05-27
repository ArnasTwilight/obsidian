# ББД sql запросы
## ID bills
### cms_suppliers из id bill
```sql
SELECT suppliers.* FROM `cms_suppliers_docs` AS docs
JOIN `cms_suppliers_bills` AS bills ON docs.id = bills.supplierdoc_id
JOIN `cms_suppliers` AS suppliers ON docs.supplier_id = suppliers.id
WHERE bills.id = 544256
```
### cms_suppliers_docs из id suppliers полученный из id bills
```sql
SELECT docs.* FROM `cms_suppliers_docs` AS docs
WHERE docs.supplier_id = (SELECT suppliers.id FROM `cms_suppliers_docs` AS docs
JOIN `cms_suppliers_bills` AS bills ON docs.id = bills.supplierdoc_id
JOIN `cms_suppliers` AS suppliers ON docs.supplier_id = suppliers.id
WHERE bills.id = 544256)
```
### cms_suppliers_docs из id bills
```sql

```

Для включения логирования запросов в БД у ББД добавить в 
```
\\wsl.localhost\Ubuntu-22.04\home\bnovo\projects\bnovo.booking-desk\.docker\images\mysql\conf.d\sql-mode.cnf
```
cледующее:
```
general_log = 1  
general_log_file = /var/log/mysql/mysql-general.log  
log_output = FILE
```