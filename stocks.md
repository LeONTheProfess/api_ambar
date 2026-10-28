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
    "page_size": 50,         // размер страницы (по умолчанию 50, максимум 100, необязательно)
    "page": 1                // номер страницы (по умолчанию 1, необязательно)
}
```

За один запрос возвращается одна страница. Для получения следующей страницы передайте её номер в `page`. Если `page_size` больше 100, API вернёт ошибку `400 Bad Request`.

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
    "message": "В запросе не задано поле owner_id.",
    "error": "error"
}
```

Если `page_size` больше 100:

```json
{
    "message": "Размер страницы не может быть больше 100.",
    "error": "page_size_too_large"
}
```

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
### <span style="color: red;">404 Not Found</span>
Запрашиваемый ресурс не найден.
#### Тело ответа

```json
{
    "message": "Ресурс не найден.",
    "error": "error"
}
```

