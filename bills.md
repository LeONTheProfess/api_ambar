# Получить список счетов пользователя

Возвращает список счетов пользователя.

GET https://apiamb.kosmoslogistic.ru/api?command=bills

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
  "bills": [
    {
      "date": "01.01.2025",
      "time": "12:00",
      "pay_type": "storage",
      "price": 100.5,
      "paid": true,
      "filepath": "https://bills.kosmoslogistic.ru/path/to/file"
    }
  ]
}
```

### Описание полей

| Поле      | Тип    | Описание |
|-----------|--------|----------|
| date      | string | Дата в формате DD.MM.YYYY |
| time      | string | Время в формате HH:MM |
| pay_type  | string | Тип оплаты: `storage` или `services` |
| price     | number | Сумма счета |
| paid      | boolean | Статус оплаты: `true` — оплачено, `false` — не оплачено |
| filepath  | string | Ссылка на файл счета |

Если у пользователя нет счетов, ответ будет содержать пустой список `bills`.

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
Пользователь не найден.

#### Тело ответа
```json
{
  "error": "error",
  "message": "Пользователь не найден"
}
```
