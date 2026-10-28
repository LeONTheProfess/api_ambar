## Транзакции банка

Получить список банковских транзакций.

GET https://apiamb.kosmoslogistic.ru/api?command=bank_transactions

## Заголовки

| Заголовок     | Значение           |
|---------------|--------------------|
| Content-Type  | application/json   |
| Authorization | `<your-token>`     |


---

## Ответ (200 OK)

```json
{
        "bank_transactions": [
                {
                        "id": "3136226651",
                        "amount": 62,
                        "comment": "",
                        "status": "paid",
                        "type": "services",
                        "date": "23.10.2025",
                        "time": "17:36"
                }
        ]
}
```

### Описание полей

| Поле       | Тип    | Описание                                  |
|------------|--------|-------------------------------------------|
| id         | string | Идентификатор транзакции                  |
| amount     | number | Сумма транзакции (обычно в целых единицах)|
| comment    | string | Комментарий к транзакции                  |
| status     | string | Статус (paid, rejected, returned)  |
| type       | string | Тип транзакции (services, storage )  |
| date       | string | Дата в формате DD.MM.YYYY                 |
| time       | string | Время в формате HH:MM                     |

---

## Ошибки

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
