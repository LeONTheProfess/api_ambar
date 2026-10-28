# Создать счёт (make_payment_bill)

Создать счёт на оплату (генерация PDF-счёта).

POST https://apiamb.kosmoslogistic.ru/api?command=make_payment_bill

## Заголовки

| Заголовок     | Значение           |
|---------------|--------------------|
| Content-Type  | application/json   |
| Authorization | `<your-token>`     |

---

## Тело запроса

```json
{
    "amount": 15,
    "pay_type": "services"
}
```

- amount — сумма счёта (number). Обязательное поле.
- pay_type — тип платежа: `services` или `storage`. Обязательное поле.

---

## Пример запроса (curl)

```bash
curl -X POST \
  'https://apiamb.kosmoslogistic.ru/api?command=make_payment_bill' \
  -H 'Authorization: Bearer <your-token>' \
  -H 'Content-Type: application/json' \
  -d '{"amount":15, "pay_type":"services"}'
```

---

## Пример успешного ответа (200 OK)

```json
{
    "filepath": "https://bills.kosmoslogistic.ru/КЛ1061_/Order_001855_2025-11-06.pdf",
    "result": "OK"
}
```

- `filepath` — ссылка на сгенерированный PDF-счёт.
- `result` — строка `OK` при успешной генерации.

---

## Возможные ошибки (ответы взяты из обработчика)

---
### <span style="color: red;">403 Unauthorized</span>
Данные для авторизации не указаны или указаны неверно, либо пользователю запрещён доступ к ресурсу.
#### Тело ответа

```json
{
    "error": "access_denied",
    "message": "<error message>"
}
```
---
#### 404 Not Found — клиент не найден

```json
{
    "error": "error",
    "message": "Клиент не найден"
}
```

#### 422 Unprocessable Entity — ошибки в данных запроса

Возможные случаи:
- сумма не задана,
- неверный `pay_type`,
- сумма отличается от ожидаемой (для `services`),
- оплата ещё не рассчитана или другие проверки для `storage`.

Примеры тел:

```json
{
    "error": "error",
    "message": "Не задана сумма"
}
```

```json
{
    "error": "error",
    "message": "Не задан тип платежа"
}
```

```json
{
    "error": "error",
    "message": "Сумма 15 отличается от ожидаемой 20"
}
```

#### 400 Bad Request — ошибки внешнего запроса / формирования счёта

Если при запросе к внешнему сервису произошла ошибка или получен неожиданный ответ:

```json
{
    "error": "error",
    "message": "Ошибка запроса cloudpayments <текст ошибки>"
}
```

или

```json
{
    "error": "error",
    "message": "Ошибка запроса счёта <ответ внешнего сервера>"
}
```

---

