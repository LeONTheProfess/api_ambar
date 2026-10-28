# Получить должников

Запрос на получение должников в системе ЕМЕ

GET https://apiamb.kosmoslogistic.ru/api?command=debtors

## Заголовки

| Заголовок           | Значение                       |
|---------------------|--------------------------------|
| Authorization       | `<your-token>`         |

---

## Ответы

### <span style="color: green;">200 ОК</span>

#### Тело ответа

```json
[
    {
        "owner_id": "1001",                // id должника в виде строки
        "amount_due": 1500.00              // сумма задолженности
    },
    {
        "owner_id": "1002",
        "amount_due": 2500.00
    }
]
```
---
### <span style="color: red;">400 Bad Request</span>
Запрос содержит неправильные данные.
#### Тело ответа

```json
{
    "message": "В запросе не задано поле owner_id.",
    "error": "error"
}
```
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
### <span style="color: red;">404 Not Found</span>
Запрашиваемый ресурс не найден.
#### Тело ответа

```json
{
    "message": "Ресурс не найден.",
    "error": "error"
}
```
