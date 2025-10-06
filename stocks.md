# Получить список хранящихся ГРМ пользователя

Запрос на хранимые вещи

POST https://apiamb.kosmoslogistic.ru/api?command=stocks

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

### <span style="color: green;">200 ОК</span>

#### Тело ответа

```json
    {
        "stocks":                       // массив остатков
        [
            {
                "grm": "GRM000013",     // id грузового места
                "weight": 1.2,          // вес
                "volume": 0.2,          // объём
                "qty": 1,               // количество 
                "image": "https://host/images/GRM000013.jpeg", // ссылка на фото грузового места
                "status": "stored",      // состояние товара: stored (хранение) или ordered (в заказе)
                "comment": "Комментарий к ГРМ"  
            }
        ]
    }
```
---
### <span style="color: red;">400 Bad Request</span>
Запрос содержит неправильные данные.
#### Тело ответа

```json
    {
        "result": "error",
        "errors":
        [
            {
                "message": "В запросе не задано поле owner_id."
            }
        ]
    }
```
---
### <span style="color: red;">401 Unauthorized</span>
В запросе не указаны данные для авторизации.
#### Тело ответа

```json
    {
        "result": "error",
        "errors":
        [
            {
                "message": "В запросе не указаны данные для авторизации."
            }
        ]
    }
```
---
### <span style="color: red;">403 Forbidden</span>
Данные для авторизации неверны или доступ к ресурсу запрещен.
#### Тело ответа

```json
    {
        "result": "error",
        "errors":
        [
            {
                "message": "Данные для авторизации неверны."
            }
        ]
    }
```
---
### <span style="color: red;">404 Not Found</span>
Запрашиваемый ресурс не найден.
#### Тело ответа

```json
    {
        "result": "error",
        "errors":
        [
            {
                "message": "Ресурс не найден."
            }
        ]
    }
```


