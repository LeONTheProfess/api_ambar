# Добавить файл к заказу

Метод загружает PDF-файл в заказ и создает запись о файле в `FilesOrder`.

POST `https://apiamb.kosmoslogistic.ru/api?command=add_file_to_order&order_no=00322-0000440&copies_count=2`

## Заголовки

| Заголовок     | Значение              |
| ------------- | --------------------- |
| Authorization | `<your-token>`        |
| Content-Type  | `multipart/form-data` |

## Параметры запроса

Параметры читаются из query/form:

| Параметр         | Обязательный | Описание                                        |
| ---------------- | ------------ | ----------------------------------------------- |
| `order_no`       | Да           | Номер заказа.                                   |
| `copies_count`   | Нет          | Количество копий. По умолчанию `1`.             |
| Файл (multipart) | Да           | Загружаемый файл, поддерживается только `.pdf`. |

## Что делает метод

1. Проверяет токен в заголовке `Authorization`.
2. Ищет заказ по `order_no` и владельцу токена.
3. Принимает загруженные файлы из multipart.
4. Валидирует расширение файла (только PDF).

## Успешный ответ

### 200 OK

```json
{
  "result": "ok"
}
```

## Ошибки (по коду обработки)

### 401 Unauthorized

Токен не передан.

```json
{
  "error": "access_denied",
  "message": "Токен не задан."
}
```

### 403 Forbidden

Неверный/просроченный токен.

```json
{
  "error": "access_denied",
  "message": "<текст ошибки проверки токена>"
}
```

### 403 Forbidden

Не передан `order_no`.

```json
{
  "error": "field_not_found",
  "message": "Не задан order_ref"
}
```

Примечание: в сообщении используется `order_ref`, хотя проверяется параметр `order_no`.

### 404 Not Found

Заказ не найден или не принадлежит владельцу токена.

```json
{
  "error": "order_not_found",
  "message": "Заказ не найден."
}
```

### 500 Internal Server Error

Неподдерживаемый тип файла (не PDF).

```json
{
  "error": "wrong_extension_file",
  "message": "Неподдерживаемый тип файла"
}
```

### 500 Internal Server Error

Файл с таким именем уже загружался ранее.

```json
{
  "error": "file_is_exists",
  "message": "Файл был загружен ранее"
}
```

### 500 Internal Server Error

Файл не был передан в multipart-запросе или пустой набор файлов.

```json
{
  "error": "file_is_empty",
  "message": "Файл не был добавлен в запрос"
}
```
