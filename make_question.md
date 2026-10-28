# Задать вопрос (make_question)

Метод для отправки вопроса от пользователя.

POST https://apiamb.kosmoslogistic.ru/api?command=make_question

## Заголовки

| Заголовок     | Значение         |
|---------------|------------------|
| Content-Type  | application/json |
| Authorization | `<your-token>`   |

---

## Тело запроса

```json
{
  "theme": "Вопрос по оплате", // тема вопроса (обязательно)
  "message": "Как оплатить услуги?" // текст сообщения (обязательно)
}
```

## Ответы

### <span style="color: green;">200 OK</span>

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
    "error": "error",
    "message": "Пустые данные : theme"
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
