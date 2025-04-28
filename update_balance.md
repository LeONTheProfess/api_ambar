# Обновить баланс пользователя

Запрос на обновление баланса пользователя в системе ЕМЕ

PUT https://apiamb.kosmoslogistic.ru/api?command=update_balance

## Заголовки

| Заголовок           | Значение                       |
|---------------------|--------------------------------|
| Content-Type        | application/json              |
| Authorization       | Bearer `<your-token>`         |

---

## Тело запроса

```json
{
    "owner_id": "1001",                // id пользователя в виде строки (обязательно)
    "balance": 2000.00                 // новый баланс (обязательно)
}
```

## Ответы

### <span style="color: green;">200 ОК</span>

#### Тело ответа

```json
{
    "result": "Ok"
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
