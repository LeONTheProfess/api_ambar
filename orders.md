# Получить список возвратов пользователя

Запрос возвратов товаров

GET https://apiamb.kosmoslogistic.ru/api?command=orders

## Заголовки

| Заголовок           | Значение                       |
|---------------------|--------------------------------|
| Content-Type        | application/json              |
| Authorization       | `<your-token>`         |

## Тело запроса

```json
{
  "page_size": 20,              // количество заказов в ответе (максимум 50)(не обязательно)
  "page": 1,                    // номер страницы (не обязательно)
  "from_date": "26.11.2024",    // дата от (не обязательно)
  "to_date": "28.11.2024",      // дата до (не обязательно)
  "status": "PICKUP"            // статус заказа (не обязательно)
}
```
## Статусы заказа
- **PROCESSING**  
  Заказ введён и взят в работу
- **PACKED**  
  Заказ собран и готов к отгрузке
- **DELIVERY**  
  Заказ передан в доставку
- **CLOSED**  
  Заказ выполнен
  
---

## Ответы

### <span style="color: green;">200 ОК</span>

#### Тело ответа

```json
    {
        "orders":   // массив заказов
        [
            {
                "order_no": "ord123",                           // номер заказа
                "status": "PACKED",                             // статус
                "comment": "Упаковать в пакет из пятёрочки",    // коммент
                "need_delivery": false,                         // нужна доставка
                "plan_delivery_date": "27.11.2024",             // плановая дата отгрузки
                "time_min": "9:00",                             // время от
                "time_max": "13:00",                            // время до
                "pass": // пропуск
                {
                    "name": "Джон Доу",     // ФИО водителя
                    "car_num": "T123СТ777"  // номер машины
                },
                "items":    // грузовые места
                [
                    {
                        "grm": "GRM000013", // id грузового места
                        "weight": 1.2,      // вес
                        "volume": 0.2,      // объём
                        "image": "https://host/images/GRM000013.jpeg"   // ссылка на картинку
                    }
                ]
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


