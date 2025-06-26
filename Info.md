**Grafana**
https://grafana-new.dev.bnovo.ru

Dashboards->Loki->All logs
https://grafana-new.dev.bnovo.ru/d/cb191419-bb3e-41a7-8caf-cbb6a2d1a890/all-logs?orgId=1&from=now-10m&to=now&timezone=browser&var-query0=&var-query1=&var-query2=default

**Wiki**
Отпуска:
https://wiki.yandex.ru/dokumentacija-komand/internalteam/grafik-otpuskov

**xdebug**
проверка, что он есть в php:
```shell
php -v
```
```shell
php -m
```

**Other:**
![](_attachments/Pasted%20image%2020250513165940.png)

> [!NOTE]  Евгений Лебедев
> Друзья. У многих дома установлены wifi-роутеры, и у всех там есть настройка - сеть в которой работает роутер и выдает IP подключающимся к нему устройствам. В нашей корп сети зарезервированы следующие подсети: 
> 10.0.0.0/8 
> 192.168.248.0/24 
> 192.168.0.0/24 
> 192.168.1.0/24 
> 192.168.2.0/24 
> 
> Просьба не используйте в настройках роутера эти сети. Замените например на: 192.168.3.0 или на 192.168.100.0 и т.д. 
> 
> Пересечение по сетям - одна из причин почему у вас могут не работать наши ресурсы со включенным корпоративным VPN.

# Тестирование
Информация для тестирования для разработчиков:

Смоук тест ББД находится [тут](https://bnovo.doqa.app/ru/home/detail/1/1/checklists?selected=135)

Смоук тест для Админки смотрим [тут](https://bnovo.doqa.app/ru/home/detail/1/1/checklists?selected=139)

Процесс: Выбираем нужный смоук, создаем по нему прогон, запускаем его, отмечаем успех/провал/пропуск пунктов чек-листа, завершаем прогон.

Раскатываем на **старый** стейджинг? Выбираем пайплайн/ветку [тут](https://git.dev.bnovo.ru/internal/bnovo.booking.desk/-/pipelines) и по кнопке play тыкаем только "deploy-staging"

Раскатываем на **новый** стейджинг? Выбираем пайплайн/ветку [тут](https://git.dev.bnovo.ru/internal/bnovo.booking.desk/-/pipelines) и по кнопке play тыкаем сначала "swarm-build-staging", ждем завершения, затем тыкаем "swarm-deploy-staging-6"

Инструкция по билду и деплою на новые стейджи (в том числе и ббд) смотрим [тут](https://wiki.yandex.ru/dokumentacija-komand/platforma-team/testovye-stendy/instrukcija-po-jekspluatacii/)

Посмотреть, какая ветка раскатана на стейджинге можно [тут](https://git.dev.bnovo.ru/internal/bnovo.booking.desk/-/environments) (staging - старый стенд ббд, staging-6 - новый стенд ббд, по кнопке "open" можно перейти в окружение)

[https://bbd-6.staging.bnovo.ru/](https://bbd-6.staging.bnovo.ru/) - новый стенд ббд

[https://staging.bnovo.booking-desk.ru/](https://staging.bnovo.booking-desk.ru/) - старый стенд ббд

[https://staging6.pms.bnovo.ru/](https://staging6.pms.bnovo.ru/) - наш 6 стенд PMS для теста Админки (желательно, на всякий случай, отписываться в канале devs-staging о том, что вы его заняли)