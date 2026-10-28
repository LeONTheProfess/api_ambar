# Установить способ оплаты по умолчанию (choose_default_payment)

Устанавливает сохранённый способ оплаты пользователя (банковскую карту) по умолчанию.

POST https://apiamb.kosmoslogistic.ru/api?command=choose_default_payment

## Заголовки

| Заголовок     | Значение         |
|---------------|------------------|
| Content-Type  | application/json |
| Authorization | `<your-token>`   |

---

## Тело запроса

```json
{
  "id": 123456 // id карты (обязательно)
}
```

## Ответы

### <span style="color: green;">200 OK</span>

```json
{
  "result": "Ok",
}
```

---

### <span style="color: red;">400 Bad Request</span>
Запрос содержит неправильные данные.
#### Тело ответа
```json
{
    "error": "invalid_request",
    "message": "Некорректный запрос. Поле id обязательно."
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
Карта с указанным id не найдена.
#### Тело ответа
```json
{
    "error": "not_found",
    "message": "Карта с указанным id не найдена."
}
```
