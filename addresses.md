# Получить список адресов пользователя

Запрос получения списка адресов доставки

GET https://apiamb.kosmoslogistic.ru/api?command=addresses

## Заголовки

| Заголовок           | Значение                       |
|---------------------|--------------------------------|
| Content-Type        | application/json              |
| Authorization       | `<your-token>`         |

## Тело запроса

Запрос выполняется без тела.

---

## Ответы

### <span style="color: green;">200 ОК</span>

#### Тело ответа

```json
{
    "addresses": [
        {
            "ref": 363,
            "entrance": 1,
            "floor": 5,
            "intercom": "42",
            "elevator_type": "Грузовой",
            "full_address": "ул. Ленина 15, кв. 42",
            "name": "Иван Петров",
            "phone": "+79991234567"
        },
        {
            "ref": 364,
            "entrance": 2,
            "floor": 3,
            "intercom": "28",
            "elevator_type": "Легковой",
            "full_address": "ул. Мира 8, кв. 28",
            "name": "Мария Сидорова",
            "phone": "+79992345678"
        },
        {
            "ref": 487,
            "entrance": 1,
            "floor": 7,
            "intercom": "51",
            "elevator_type": "Грузовой",
            "full_address": "пр. Красной Армии 32, кв. 51",
            "name": "Алексей Иванов",
            "phone": "+79993456789"
        }
    ],
    "result": false
}
```

#### Описание полей:

| Поле | Тип | Описание |
|------|-----|---------|
| addresses | array | массив адресов пользователя |
| ref | integer | идентификатор адреса || entrance | integer | номер подъезда || floor | integer | номер этажа |
| intercom | string | номер кв/офиса |
| elevator_type | string | тип лифта |
| full_address | string | полный адрес доставки |
| name | string | ФИО получателя |
| phone | string | номер телефона получателя |
| result | boolean | флаг результата (обычно false) |

---

### <span style="color: red;">401 Unauthorized</span>

Неверный или отсутствующий токен авторизации.

#### Тело ответа

```json
{
    "result": "error",
    "errors": [
        {
            "message": "Неверный или отсутствующий токен авторизации"
        }
    ]
}
```
