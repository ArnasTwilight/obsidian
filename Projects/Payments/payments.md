#project #paymets

**Prod link:**

**GIT link:**
https://git.dev.bnovo.ru/core/paygate/payments
**Localhost link:**
http://localhost:3000/
http://localhost:3307/

```php
'host'   => 'bnovo_payment_mysql',
'username'   => 'payment',
'password'   => 'payment',
```

Яркий представить такого обращения к ББД с добавление флага (Оплачен онлайн) - это [PaymentSystemAbstract](https://git.dev.bnovo.ru/core/paygate/payments/-/blob/master/v2/src/lib/PaymentSystemAbstract.php?ref_type=heads "https://git.dev.bnovo.ru/core/paygate/payments/-/blob/master/v2/src/lib/PaymentSystemAbstract.php?ref_type=heads") имеет метод [sendReplyPayment](https://git.dev.bnovo.ru/core/paygate/payments/-/blob/master/v2/src/lib/PaymentSystemAbstract.php?ref_type=heads#L166), в нём и происходит обращение к ББД через [file_get_contents](https://git.dev.bnovo.ru/core/paygate/payments/-/blob/master/v2/src/lib/PaymentSystemAbstract.php?ref_type=heads#L181 ) Есть ещё [src/Paygate.php](https://git.dev.bnovo.ru/core/paygate/payments/-/blob/master/src/Paygate.php?ref_type=heads) в нём есть нечто похожее в [processPayment](https://git.dev.bnovo.ru/core/paygate/payments/-/blob/master/src/Paygate.php?ref_type=heads#L112) однако я не уверен, что он вообще используется. На данный момент используется точно [v2/src/Paygate.php](https://git.dev.bnovo.ru/core/paygate/payments/-/blob/master/v2/src/Paygate.php?ref_type=heads ) В нём как раз и подготавливается ссылка на оплату ([generatePaymentURL](https://git.dev.bnovo.ru/core/paygate/payments/-/blob/master/v2/src/Paygate.php?ref_type=heads#L389)) и записывается инфа по транзакции и вроде как определяется способ оплаты с банком, но тут не ручаюсь за достоверность, дошёл дебагом до самой оплаты, но дальше проверить затруднительно. 

Предполагаю, что работает как-то так: 
После генерации ссылки, переходим по ней, далее определяется способ оплаты и банк, а после вызывается класс банка в **payments** и уже где-то там дёргается [sendReplyPayment](https://git.dev.bnovo.ru/core/paygate/payments/-/blob/master/v2/src/lib/PaymentSystemAbstract.php?ref_type=heads#L166), так как все классы банков наследуют [PaymentSystemAbstract](https://git.dev.bnovo.ru/core/paygate/payments/-/blob/master/v2/src/lib/PaymentSystemAbstract.php?ref_type=heads). Ну и после ББД фиксирует у себя флаг **"(Оплачен онлайн)"**. И теперь главный вопрос. Кто же всё же меняет сам статус. Payments похоже тут не виновен.
