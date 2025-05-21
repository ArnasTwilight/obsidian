#project #analytics-tools

**Prod link:**

**GIT link:**
https://git.dev.bnovo.ru/analytics/analytics-tools
**Localhost link:**
http://localhost:18123/play

**Вход в контейнер:**
```bash
make shell analytics_tools
```

**Получить данные из таблицы:**
```sql
SELECT id, deactivated
FROM pms.payment_transactions
```

**Удаление данных из таблицы:**
```sql
TRUNCATE TABLE pms.ИмяТаблицы
```

**Получить все таблицы:**
```sql
SELECT database, name
FROM system.tables
```