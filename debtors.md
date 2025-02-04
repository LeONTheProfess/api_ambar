# Получить должников

Запрос на получение должников в системе ЕМЕ

GET https://host/api/debtors

## Заголовки

| Заголовок           | Значение                       |
|---------------------|--------------------------------|
| Authorization       | Bearer `<your-token>`         |

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
