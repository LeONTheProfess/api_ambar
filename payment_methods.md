# Получить список способов оплаты (payment_methods)

Возвращает список сохранённых способов оплаты пользователя (банковских карт).

GET https://apiamb.kosmoslogistic.ru/api?command=payment_methods

## Заголовки

| Заголовок     | Значение         |
|---------------|------------------|
| Content-Type  | application/json |
| Authorization | `<your-token>`   |

## Тело запроса

Тело запроса отсутствует.

---

## Ответы

### <span style="color: green;">200 OK</span>

```json
{
  "payment_methods": [
    {
      "id": 123456,      // id карты
      "type": "VISA",         // тип карты
      "last_nums": "1234",     // последние 4 цифры
      "default": true         // карта по умолчанию
    }
    // ...
  ]
}
```

Если у пользователя нет сохранённых карт:
```json
{
  "payment_methods": [ ]
}
```

---

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
Пользователь не найден.
#### Тело ответа
```json
{
    "error": "error",
    "message": "Пользователь не найден"
}
```
