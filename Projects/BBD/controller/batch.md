#BBD 

[link](https://git.dev.bnovo.ru/internal/bnovo.booking.desk/-/blob/master/app/application/classes/controller/batch.php?ref_type=heads)

**Все таски запускаются по МСК**

```php
action_generate_bills()
```
Таска запускается в 18:00. Выставляет счета на договоры по условиям, обращается к методу `generate_bill()` в [Model_Supplierdoc](Projects/BBD/model/supplierdoc)