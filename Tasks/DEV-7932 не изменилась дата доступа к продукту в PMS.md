#task #BBD #PMS

 22.04.2025
[link](https://tracker.yandex.ru/DEV-7932)

bills
```sql
SELECT * FROM `cms_suppliers_bills` WHERE supplierdoc_id IN (121292, 132738)
```

docs
```sql
SELECT * FROM `cms_suppliers_docs` WHERE id IN (121292, 132738)
```

suppliers
```sql
SELECT suppliers.*, docs.id AS docs_id FROM `cms_suppliers_docs` AS docs
JOIN `cms_suppliers` AS suppliers ON docs.supplier_id = suppliers.id
WHERE docs.id IN (121292, 132738)
```

pms hotel
```sql
SELECT *  
FROM "hotels"
WHERE id = 31380
```

1. Беру последний договор, для каждого lcode, убрать ограничение на выборку постоплатных счетов