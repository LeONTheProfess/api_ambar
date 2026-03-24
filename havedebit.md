# Проверить наличие задолженности

Запрос проверки наличия задолженности у пользователя

GET https://apiamb.kosmoslogistic.ru/api?command=havedebit

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
    "result": true
}
```

или

```json
{
    "result": false
}
```

#### Описание полей:

| Поле | Тип | Описание |
|------|-----|---------|
| result | boolean | true - есть задолженность, false - нет задолженности |

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
