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

