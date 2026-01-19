# Расчет стоимости доставки (delivery_cost)

Вычисляет стоимость доставки для указанных товаров (ГРМ) на основе их объема и тарифа пользователя.

POST https://apiamb.kosmoslogistic.ru/api?command=delivery_cost

## Заголовки

| Заголовок     | Значение         |
|---------------|------------------|
| Content-Type  | application/json |
| Authorization | `<your-token>`   |

---

## Тело запроса

```json
{
  "grms": [
    {
      "num": "GRM004310",  // идентификатор ГРМ (обязательно)
      "qty": 3             // количество (обязательно, должно быть > 0)
    },
    {
      "num": "GRM004603",  // идентификатор ГРМ (обязательно)
      "qty": 5             // количество (обязательно, должно быть > 0)
    }
  ]
}
```

## Ответы

### <span style="color: green;">200 OK</span>

```json
{
  "cost": 23419,
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
  "message": "Не задан grms"
}

{
  "error": "error",
  "message": "Задан пустой grm"
}

{
  "error": "error",
  "message": "Задано неверное количество для grm GRM004310"
}

{
  "error": "error",
  "message": "ГРМ GRM004310 не найдено"
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
Клиент не найден.
#### Тело ответа
```json
{
  "error": "error",
  "message": "Клиент не найден"
}
```

---

### <span style="color: red;">500 Internal Server Error</span>
Внутренняя ошибка сервера.
#### Тело ответа
```json
{
  "error": "error",
  "message": "Нет доступа к grm GRM004310"
}

{
  "error": "error",
  "message": "Не задан тариф пользователя"
}

{
  "error": "error",
  "message": "В тарифе пользователя не найдена услуга доставки"
}
```
