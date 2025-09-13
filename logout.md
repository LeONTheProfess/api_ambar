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

### <span style="color: red;">401 Unauthorized</span>
Неверный или отсутствующий токен авторизации.

```json
{
  "result": "error",
  "message": "Unauthorized"
}
```
