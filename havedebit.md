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

---
### <span style="color: red;">403 Unauthorized</span>
Данные для авторизации не указаны или указаны неверно, либо пользователю запрещён доступ к ресурсу.
#### Тело ответа

```json
{
    "error": "access_denied",
    "message": "<error message>"
}
```
---
