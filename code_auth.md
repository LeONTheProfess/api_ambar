# Запрос SMS кода авторизации

Запрос SMS кода для авторизации по номеру телефона.

POST https://apiamb.kosmoslogistic.ru/api?command=code_auth

## Заголовки

| Заголовок     | Значение           |
|---------------|--------------------|
| Content-Type  | application/json   |

## Тело запроса

```json
{
  "phone": "+79991234567", // номер телефона (обязательно)
  "registration": false    // флаг регистрации (не обязательно, по умолчанию false)
}
```

---

## Ответы

### <span style="color: green;">200 OK</span>

#### Тело ответа

```json
{
  "id": "1753161462280937617" // идентификатор пользователя
}
```

---

### <span style="color: red;">400 Bad Request</span>
Запрос содержит неправильные данные.

```json
{
  "result": "error",
  "message": "В запросе не задано поле phone."
}
```
