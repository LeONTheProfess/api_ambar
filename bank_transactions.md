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

#### 401 Unauthorized

```json
{
    "result": "error",
    "error": "В запросе не указаны данные для авторизации."
}
```

#### 403 Forbidden

```json
{
    "result": "error",
    "error": "Доступ запрещён."
}
```

