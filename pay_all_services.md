# Оплатить все услуги пользователя

Запрос на оплату всех услуг пользователя в системе ЕМЕ

POST https://apiamb.kosmoslogistic.ru/api?command=pay_all_services

## Заголовки

| Заголовок           | Значение                       |
|---------------------|--------------------------------|
| Content-Type        | application/json              |
| Authorization       | `<your-token>`         |

---

## Тело запроса

```json
{
    "owner_id": "1001",                // id пользователя в виде строки (обязательно)
    "amount": 5000.00                 // сумма оплаты (обязательно)
}
```

## Ответы

### <span style="color: green;">200 ОК</span>

#### Тело ответа

```json
{
    "result": "Ok",
    "paid_amount": 5000.00,           // оплаченная сумма
}
```
---
### <span style="color: red;">400 Bad Request</span>
Запрос содержит неправильные данные.
#### Тело ответа

```json
{
    "result": "error",
    "errors":
    [
        {
            "message": "В запросе не задано поле owner_id."
        }
    ]
}
```
---
### <span style="color: red;">404 Not Found</span>
Запрашиваемый ресурс не найден.
#### Тело ответа

```json
{
    "result": "error",
    "errors":
    [
        {
            "message": "Ресурс не найден."
        }
    ]
}
```
