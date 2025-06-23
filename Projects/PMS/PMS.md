#project #PMS 

**Prod link:**
https://online.bnovo.ru/
**GIT link:**

**Localhost link:**
https://bnovo.loc/planning?dfrom=04-02-2025&daily=0
http://127.0.0.1:12799/?pgsql=db&username=foo&db=pms&ns=public
# Тарифы
На странице **/tariff/tariffs** представлены тарифы, которые в 05:00 обновляют свои статусы (например, если доступ к продукту был остановлен, а это происходит в 22:00, то в 05:00 работает таска по обновлению статусов у тарифов и отключает уже их)
Колонка **OTA** отвечает за возможность работы с **Каналами продаж**, которые находятся на странице **/sales**. Тарифы могут быть подключены к одному или нескольким **Каналам продаж**.
# Каналы продаж (Управление Онлайн-Продажами/Подключение онлайн-продаж)
Представляет собой канал подключения к Avito, WuBook и тому подобным вещам, для продажи на сторонних площадках, взаимодействие происходит через **Тарифы**

**Доступы с ролью владельца тестового аккаунта:**
```
developer@bnovo.ru
```
```
123456789
```
**Доступы суперадмина:**
```
victor@bnovo.ru
```
```
123456789
```
**Доступы прода:**
```
dunovenie2805@yandex.ru
```
```
123456789
```
**Вход в контейнер PMS API:**
```bash
docker exec -it bnovo-api bash
или 
make shell bnovo-api
```
**Запуск консольных команд:**
```bash
./tools/minion bbd:changeTypeProductHotelFromNewToOld --hotel_ids=10
```
~~php index.php --task=Bbd_changeTypeProductHotelFromNewToOld --hotelIdList=10,111,20~~

bnovopms.api/application/classes/Task/Updateexpiringdates.php
Находится таска Task_Updateexpiringdates для продления доступа к продукту
[DEV-7653](https://tracker.yandex.ru/DEV-7653)

```shell
make logs_ui
```
```shell
make logs_api
```

```php
Debug::_error('');
```

# Особенности

## Ошибка контейнера с БД
Если контейнер ББД "db" постоянно перезапускается и не может стартануть и в логах пишет ошибку о повреждении базы, то необходимо остановить ББД командой:
```bash
make down
```
Затем очистить контейнер:
```bash
docker volume rm bbd_bbd_mysql_development
```
Это полностью очищает контейнер и удаляет содержимое БД. 
После этого нужно заново накатить ББД командой:
```bash
make install
```

## POST
Не работает локально метод POST между PMS и BBD по какой-то причине, только GET

Метод find() в модели
> В PMS это работать не будет, так как параметры find() не принимает.
> 
> Однако в ББД есть возможность получать таким образом запись по ID: [orm_new.php](https://git.dev.bnovo.ru/internal/bnovo.booking.desk/-/blob/master/app/modules/orm/classes/kohana/orm_new.php?ref_type=heads#L746) [orm.php](https://git.dev.bnovo.ru/internal/bnovo.booking.desk/-/blob/master/app/modules/orm/classes/kohana/orm.php?ref_type=heads#L747)
> 
> ORM PMS: [https://git.dev.bnovo.ru/core/pms/bnovo.pms/-/blob/master/modules/orm/classes/Kohana/ORM.php?ref_type=heads#L963](https://git.dev.bnovo.ru/core/pms/bnovo.pms/-/blob/master/modules/orm/classes/Kohana/ORM.php?ref_type=heads#L963) Дока: [https://kohana.top/3.3/guide-api/ORM#find](https://kohana.top/3.3/guide-api/ORM#find)