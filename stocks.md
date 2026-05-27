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
{
    "sort_order": "desc",   // порядок сортировки по дате: "desc" или "asc" (необязательно, по умолчанию "asc")
    "status": "stored",     // фильтр по статусу: "stored", "ordered", "returned" (необязательно)
    "page_size": 20,         // размер страницы (необязательно, максимум 50)
    "page": 1                // номер страницы (необязательно)
}
```

Статусы для фильтрации:
- `stored` — в хранении
- `ordered` — в заказах
- `returned` — возвращённые
---

## Ответы

### <span style="color: green;">200 ОК</span>

#### Тело ответа

```json
    {
        "stocks":                       // массив остатков
        [
            {
                "grm": "GRM010791",     // id грузового места
                "weight": 1,             // вес
                "volume": 1.544,         // объём
                "qty": 13,               // количество
                "date": "23.03.2026",  // дата хранения/обновления (используется для сортировки)
                "image": "https://amphoto.kosmoslogistic.ru/s/p0llvdYYzGvLbPtfCGrKy_d", // ссылка на фото грузового места
                "status": "stored",     // состояние товара: stored (хранение) или ordered (в заказе)
                "comment": "Соевая мука"
            }
        ],
        "ordered_qty": 2,    // суммарно в заказах
        "stored_qty": 29,    // суммарно в хранении
        "returned_qty": 59,  // суммарно возвращено
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


