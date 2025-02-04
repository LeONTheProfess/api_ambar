# Получить баланс пользователя

Запрос на получение баланса из системы ЕМЕ

GET https://host/api/owner_balance

## Заголовки

| Заголовок           | Значение                       |
|---------------------|--------------------------------|
| Content-Type        | application/json              |
| Authorization       | Bearer `<your-token>`         |

---

## Тело запроса

```json
{
    "owner_id": "1001"                 // id пользователя в виде строки (обязательно)
}
```

## Ответы

### <span style="color: green;">200 ОК</span>

#### Тело ответа

```json
{
    "owner_id": "1001",                // id пользователя в виде строки
    "balance": 1000.00,                // баланс
    "stored_goods_volume": 10.5,       // количество хранимого груза (м3)
    "monthly_payment": 3000.00,        // ежемесячный платёж
    "amount_due": 0.00              // сколько требуется оплатить
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
### <span style="color: red;">401 Unauthorized</span>
В запросе не указаны данные для авторизации.
#### Тело ответа

```json
    {
        "result": "error",
        "errors":
        [
            {
                "message": "В запросе не указаны данные для авторизации."
            }
        ]
    }
```
---
### <span style="color: red;">403 Forbidden</span>
Данные для авторизации неверны или доступ к ресурсу запрещен.
#### Тело ответа

```json
    {
        "result": "error",
        "errors":
        [
            {
                "message": "Данные для авторизации неверны."
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
