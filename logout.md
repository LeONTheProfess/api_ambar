# Выход из системы

Выход пользователя из системы и инвалидация токена доступа.

POST https://apiamb.kosmoslogistic.ru/api?command=logout

## Заголовки

| Заголовок           | Значение                       |
|---------------------|--------------------------------|
| Content-Type        | application/json              |
| Authorization       | `<your-token>`         |

## Тело запроса

```json
{}
```

---

## Ответы

### <span style="color: green;">200 OK</span>

#### Тело ответа

```json
{
  "result": "Ok"
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
