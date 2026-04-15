# Описание API запроса: Доступные даты

### Заголовки

| Заголовок           | Значение                       |
|---------------------|--------------------------------|
| Content-Type        | application/json              |
| Authorization       | `<your-token>`               |

## Метод: GET

### URL
```
http://apiamb.kosmoslogistic.ru/api
```

### Параметры запроса
| Параметр   | Тип    | Обязательный | Описание                     |
|------------|--------|--------------|------------------------------|
| command    | string | Да           | Команда запроса. Значение: `available_dates`. |
| doctype    | string | Да           | Тип документа. Возможные значения: `order`, `asn`. |
| delivery   | bool   | Да           | Указывает, требуется ли доставка. Значение: `true`. |

### Пример запроса
```
GET http://apiamb.kosmoslogistic.ru/api?command=available_dates&doctype=order&delivery=true
```

### Ответ
Ответ возвращается в формате JSON.

#### Пример успешного ответа
```json
{
    "dates": [
        {
            "date": "16.04.2026",
            "times": [
                {
                    "time_from": "13:00",
                    "time_to": "17:00"
                },
                {
                    "time_from": "17:00",
                    "time_to": "22:00"
                }
            ]
        },
        {
            "date": "17.04.2026",
            "times": [
                {
                    "time_from": "09:00",
                    "time_to": "13:00"
                },
                {
                    "time_from": "13:00",
                    "time_to": "17:00"
                },
                {
                    "time_from": "17:00",
                    "time_to": "22:00"
                }
            ]
        },
        {
            "date": "18.04.2026",
            "times": [
                {
                    "time_from": "09:00",
                    "time_to": "13:00"
                },
                {
                    "time_from": "13:00",
                    "time_to": "17:00"
                },
                {
                    "time_from": "17:00",
                    "time_to": "22:00"
                }
            ]
        },
        {
            "date": "20.04.2026",
            "times": [
                {
                    "time_from": "09:00",
                    "time_to": "13:00"
                },
                {
                    "time_from": "13:00",
                    "time_to": "17:00"
                },
                {
                    "time_from": "17:00",
                    "time_to": "22:00"
                }
            ]
        },
        {
            "date": "21.04.2026",
            "times": [
                {
                    "time_from": "09:00",
                    "time_to": "13:00"
                },
                {
                    "time_from": "13:00",
                    "time_to": "17:00"
                },
                {
                    "time_from": "17:00",
                    "time_to": "22:00"
                }
            ]
        },
        {
            "date": "22.04.2026",
            "times": [
                {
                    "time_from": "09:00",
                    "time_to": "13:00"
                },
                {
                    "time_from": "13:00",
                    "time_to": "17:00"
                },
                {
                    "time_from": "17:00",
                    "time_to": "22:00"
                }
            ]
        },
        {
            "date": "23.04.2026",
            "times": [
                {
                    "time_from": "09:00",
                    "time_to": "13:00"
                },
                {
                    "time_from": "13:00",
                    "time_to": "17:00"
                },
                {
                    "time_from": "17:00",
                    "time_to": "22:00"
                }
            ]
        },
        {
            "date": "24.04.2026",
            "times": [
                {
                    "time_from": "09:00",
                    "time_to": "13:00"
                },
                {
                    "time_from": "13:00",
                    "time_to": "17:00"
                },
                {
                    "time_from": "17:00",
                    "time_to": "22:00"
                }
            ]
        },
        {
            "date": "25.04.2026",
            "times": [
                {
                    "time_from": "09:00",
                    "time_to": "13:00"
                },
                {
                    "time_from": "13:00",
                    "time_to": "17:00"
                },
                {
                    "time_from": "17:00",
                    "time_to": "22:00"
                }
            ]
        },
        {
            "date": "27.04.2026",
            "times": [
                {
                    "time_from": "09:00",
                    "time_to": "13:00"
                },
                {
                    "time_from": "13:00",
                    "time_to": "17:00"
                },
                {
                    "time_from": "17:00",
                    "time_to": "22:00"
                }
            ]
        },
        {
            "date": "28.04.2026",
            "times": [
                {
                    "time_from": "09:00",
                    "time_to": "13:00"
                },
                {
                    "time_from": "13:00",
                    "time_to": "17:00"
                },
                {
                    "time_from": "17:00",
                    "time_to": "22:00"
                }
            ]
        },
        {
            "date": "29.04.2026",
            "times": [
                {
                    "time_from": "09:00",
                    "time_to": "13:00"
                },
                {
                    "time_from": "13:00",
                    "time_to": "17:00"
                },
                {
                    "time_from": "17:00",
                    "time_to": "22:00"
                }
            ]
        }
    ]
}
```

#### Пример ошибки
```json
{
    "success": false,
    "error": "field_not_found",
    "message": "Неверно задан doctype"
}
```

```json
{
    "success": false,
    "error": "field_not_found",
    "message": "Неверно задан delivery"
}
```