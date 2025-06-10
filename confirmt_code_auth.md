# Подтверждение кода авторизации (confirmt_code_auth)

Подтверждение кода, отправленного на номер телефона, для завершения авторизации.

POST https://apiamb.kosmoslogistic.ru/api?command=confirmt_code_auth

## Заголовки

| Заголовок     | Значение           |
|---------------|--------------------|
| Content-Type  | application/json   |

## Тело запроса

```json
{
  "id": "1753161462280937617", // идентификатор пользователя (обязательно)
  "code": "1234"               // код подтверждения из СМС (обязательно)
}
```

---

## Ответы

### <span style="color: green;">200 OK</span>

#### Тело ответа

```json
{
  "access_token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9..." // токен доступа
}
```

---

### <span style="color: red;">400 Bad Request</span>
Запрос содержит неправильные данные.

```json
{
  "result": "error",
  "message": "Неверный код подтверждения или отсутствует поле."
}
```
