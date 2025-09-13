# Провести оплату (make_payment)

Позволяет списать деньги с карты пользователя через CloudPayments.

POST https://apiamb.kosmoslogistic.ru/api?command=make_payment

## Заголовки

| Заголовок     | Значение         |
|---------------|------------------|
| Content-Type  | application/json |
| Authorization | `<your-token>`   |

## Тело запроса

```json
{
  "method_id": "123456", // id метода оплаты (банковская карта)
  "amount": 1000.0            // сумма к списанию (обязательно)
}
```

---

## Ответы

### <span style="color: green;">200 OK</span>

```json
{
  "result": "OK"
}
```

---

### <span style="color: red;">401 Unauthorized</span>
Токен не задан или не передан в заголовке Authorization.
#### Тело ответа
```json
{
  "error": "access_denied",
  "message": "Токен не задан."
}
```

---

### <span style="color: red;">403 Forbidden</span>
Токен невалиден или истёк срок действия.
#### Тело ответа
```json
{
  "error": "access_denied",
  "message": "Причина ошибки авторизации"
}
```

---

### <span style="color: red;">404 Not Found</span>
Клиент или метод оплаты не найден.
#### Тело ответа
```json
{
  "error": "error",
  "message": "Клиент не найден" // или "Метод оплаты не найден"
}
```

---

### <span style="color: red;">422 Unprocessable Entity</span>
Не задана сумма или ошибка оплаты.
#### Тело ответа
```json
{
  "error": "error",
  "message": "Не задана сумма" // или "Ошибка оплаты cloudpayments <ReasonCode>"
}
```

---

### <span style="color: red;">400 Bad Request</span>
Ошибка запроса к CloudPayments.
#### Тело ответа
```json
{
  "error": "error",
  "message": "Ошибка запроса cloudpayments <текст ошибки>"
}
```
