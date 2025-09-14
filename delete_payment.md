# Удалить способ оплаты (delete_payment)

Удаляет сохранённый способ оплаты пользователя (банковскую карту).

POST https://apiamb.kosmoslogistic.ru/api?command=delete_payment

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
  "result": "OK"
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
1. Токен невалиден или истёк срок действия.
2. Запрещено удалять последний метод оплаты.
#### Тело ответа
```json
{
  "error": "access_denied",
  "message": "Причина ошибки авторизации"
}

{
  "error": "error",
  "message": "Запрещено удалять последний метод оплаты"
}
```

---

### <span style="color: red;">404 Not Found</span>
1. Клиент не найден.
2. Карта с указанным id не найдена.
#### Тело ответа
```json
{
  "error": "error",
  "message": "Клиент не найден"
}

{
  "error": "not_found",
  "message": "Карта с указанным id не найдена."
}
```

---

### <span style="color: red;">422 Unprocessable Entity</span>
Не задан id метода оплаты.
#### Тело ответа
```json
{
  "error": "error",
  "message": "Не задан id метода оплаты"
}
```