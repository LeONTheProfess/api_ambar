# Выход из системы (logout)

Позволяет завершить сессию пользователя и аннулировать токен авторизации.

POST https://apiamb.kosmoslogistic.ru/api?command=logout

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

Успешный выход из системы. Тело ответа может быть пустым или содержать подтверждение:

```json
{
  "result": "ok"
}
```

---

### <span style="color: red;">401 Unauthorized</span>
Токен не задан или не передан в заголовке Authorization.
#### Тело ответа
```json
{
  "error": "access_denied",
  "message": "Токен не задан."
}
```

---

### <span style="color: red;">403 Forbidden</span>
Токен невалиден или истёк срок действия.
#### Тело ответа
```json
{
  "error": "access_denied",
  "message": "Причина ошибки авторизации"
}
```
