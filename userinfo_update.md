# Обновить информацию о пользователе (userinfo_update)

Позволяет обновить данные пользователя (физического или юридического лица).

POST https://apiamb.kosmoslogistic.ru/api?command=userinfo_update

## Заголовки

| Заголовок     | Значение         |
|---------------|------------------|
| Content-Type  | application/json |
| Authorization | `<your-token>`   |

## Тело запроса

Для юридического лица:
```json
{
  "full_name": "Иванов Иван Иванович",      // контактное лицо
  "company_name": "ООО Ромашка",            // название компании
  "inn": "1234567890",                      // ИНН
  "kpp": "123456789",                       // КПП
  "legal_address": "г. Москва, ул. Ленина, д.1", // юр. адрес
  "postal_address": "г. Москва, а/я 123",         // почтовый адрес
  "bank_name": "Сбербанк",                  // банк
  "email": "user@example.com",              // email
  "bik": "044525225",                       // БИК
  "account_number": "40702810900000000001", // расчетный счет
  "correspondent_account": "30101810400000000225" // корр. счет
}
```

Для физического лица:
```json
{
  "full_name": "Петров Петр Петрович", // ФИО
  "email": "user@example.com"           // email
}
```

---

## Ответы

### <span style="color: green;">200 OK</span>
Данные успешно обновлены. Тело ответа отсутствует.

---

### <span style="color: red;">401 Unauthorized</span>
Токен не задан или не передан в заголовке Authorization.
#### Тело ответа
```json
{
  "error": "access_denied",
  "message": "Токен не задан."
}
```

---

### <span style="color: red;">403 Forbidden</span>
Токен невалиден или истёк срок действия.
#### Тело ответа
```json
{
  "error": "access_denied",
  "message": "Причина ошибки авторизации"
}
```

---

### <span style="color: red;">404 Not Found</span>
Пользователь не найден.
#### Тело ответа
```json
{
  "error": "error",
  "message": "Пользователь не найден"
}
```
