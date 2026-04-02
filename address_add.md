# Добавление адреса

При запросе добавления адреса создается новый адрес в системе ЕМЕ.

POST https://apiamb.kosmoslogistic.ru/api?command=address_add

## Заголовки

| Заголовок           | Значение                       |
|---------------------|--------------------------------|
| Content-Type        | application/json              |
| Authorization       | `<your-token>`         |

---

## Тело запроса

```json
{
  "name": "Джон",                     // имя (не обязательно)
  "last_name": "Доу",                 // фамилия (не обязательно)
  "phone": "+79998887766",            // телефон (обязательно)
  "full_address": "г Москва, Можайское шоссе, д 6 стр 3 кв 51", // адрес (обязательно)
  "entrance": 1,                      // подъезд (не обязательно)
  "floor": 5,                         // этаж (не обязательно)
  "intercom": "123",                  // домофон (не обязательно)
  "elevator_type": "грузовой"         // тип лифта (не обязательно)
}
```

---

## Ответы

### <span style="color: green;">200 ОК</span>

#### Тело ответа

```json
    {
        "result": "OK"
    }
```
---
### <span style="color: red;">400 Bad Request</span>
Запрос содержит неправильные данные (пустые обязательные поля).
#### Тело ответа

```json
    {
        "error": "error",
        "message": "Пустые данные : phone"
    }
```
или
```json
    {
        "error": "error",
        "message": "Пустые данные : full_address"
    }
```
---
### <span style="color: red;">401 Unauthorized</span>
Токен не задан.
#### Тело ответа

```json
    {
        "error": "access_denied",
        "message": "Токен не задан."
    }
```
---
### <span style="color: red;">403 Forbidden</span>
Токен неверный или доступ запрещен.
#### Тело ответа

```json
    {
        "error": "access_denied",
        "message": "Ошибка при проверке токена"
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