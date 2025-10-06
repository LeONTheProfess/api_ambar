# Добавить комментарий к ГРМ (grm_comment)

Метод для добавления комментария к указанному ГРМ - не работает для архивных ГРМ.

POST https://apiamb.kosmoslogistic.ru/api?command=grm_comment

## Заголовки

| Заголовок     | Значение         |
|---------------|------------------|
| Content-Type  | application/json |
| Authorization | `<your-token>`   |

---

## Тело запроса

```json
{
  "grm": "GRM123456", // идентификатор ГРМ (обязательно)
  "comment": "Комментарий к ГРМ" // текст комментария (обязательно)
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

### <span style="color: red;">400 Bad Request</span>
Некорректные данные в запросе.
#### Тело ответа
```json
{
  "error": "error",
  "message": "Пустые данные : grm"
}

{
  "error": "error",
  "message": "Пустые данные : comment"
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

---

### <span style="color: red;">404 Not Found</span>
1. Клиент не найден.
2. ГРМ с указанным идентификатором не найден.
#### Тело ответа
```json
{
  "error": "error",
  "message": "Клиент не найден"
}

{
  "error": "error",
  "message": "grm GRM123456 не найден."
}
```

---

### <span style="color: red;">500 Internal Server Error</span>
Нет доступа к указанному ГРМ.
#### Тело ответа
```json
{
  "error": "error",
  "message": "Нет доступа к этому grm"
}
```