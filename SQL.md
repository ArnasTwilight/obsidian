# ББД sql запросы
## УПД
cms_suppliers_bills:
```SQL
SELECT * FROM `cms_suppliers_bills` WHERE id = 531477
```
cms_suppliers_docs:
```SQL
SELECT docs.* FROM `cms_suppliers_docs` as docs
JOIN `cms_suppliers_bills` as bills ON docs.id = bills.supplierdoc_id
WHERE bills.id = 531477
```
cms_suppliers:
```SQL
SELECT suppliers.* FROM `cms_suppliers` as suppliers
JOIN `cms_suppliers_docs` as docs ON docs.supplier_id = suppliers.id
JOIN `cms_suppliers_bills` as bills ON docs.id = bills.supplierdoc_id
WHERE bills.id = 531477
```
## ID bills
### cms_suppliers из id bill
Получение supplier из id bill
```sql
SELECT suppliers.* FROM `cms_suppliers_docs` AS docs
JOIN `cms_suppliers_bills` AS bills ON docs.id = bills.supplierdoc_id
JOIN `cms_suppliers` AS suppliers ON docs.supplier_id = suppliers.id
WHERE bills.id = 544256
```
### cms_suppliers_docs из id suppliers полученный из id bill
Получение всех docs у одного supplier через id bill
```sql
SELECT docs.* FROM `cms_suppliers_docs` AS docs
WHERE docs.supplier_id = 
(
    SELECT suppliers.id FROM `cms_suppliers_docs` AS docs
    JOIN `cms_suppliers_bills` AS bills ON docs.id = bills.supplierdoc_id
    JOIN `cms_suppliers` AS suppliers ON docs.supplier_id = suppliers.id
    WHERE bills.id = 544256
)
```
### cms_suppliers_bills из id bill
Получение всех bills из всех docs одного supplier используя id bill
```sql
SELECT bills.* FROM `cms_suppliers_bills` AS bills WHERE bills.supplierdoc_id IN 
(
    SELECT docs.id FROM `cms_suppliers_docs` AS docs
    WHERE docs.supplier_id = 
    (
        SELECT suppliers.id FROM `cms_suppliers_docs` AS docs
        JOIN `cms_suppliers_bills` AS bills ON docs.id = bills.supplierdoc_id
        JOIN `cms_suppliers` AS suppliers ON docs.supplier_id = suppliers.id
        WHERE bills.id = 544256
    )
)
```
# lcode
### cms_suppliers из lcode
```sql

```
### cms_suppliers_docs из lcode
```sql

```
### cms_suppliers_bills из lcode
```sql

```
# Прочее
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

Получение последнего sql запроса:
```php
$query = Database::instance()->last_query
```