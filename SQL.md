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
test