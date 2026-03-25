# Удаление адреса

При запросе удаления адреса удаляется адрес из системы ЕМЕ.

POST https://apiamb.kosmoslogistic.ru/api?command=address_del

## Заголовки

| Заголовок           | Значение                       |
|---------------------|--------------------------------|
| Content-Type        | application/json              |
| Authorization       | `<your-token>`         |

---

## Тело запроса

```json
{
  "address_ref": 123  // id адреса (обязательно)
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
Адрес не найден или не принадлежит пользователю.
#### Тело ответа

```json
    {
        "error": "error",
        "message": "Неверно задан адрес"
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
---
### <span style="color: red;">501 Not Implemented</span>
Токен имеет ограниченный доступ (только просмотр).
#### Тело ответа

```json
    {
        "error": "error",
        "message": "Только просмотр!"
    }
```