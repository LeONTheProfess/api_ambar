# Получение информации о пользователе

Получение информации о текущем авторизованном пользователе.

GET https://apiamb.kosmoslogistic.ru/api?command=userinfo

## Заголовки

| Заголовок           | Значение                       |
|---------------------|--------------------------------|
| Authorization       | `<your-token>`         |

---

## Ответы

### <span style="color: green;">200 OK</span>

#### Тело ответа

```json
{
  "id": "1753161462280937617",
  "full_name": "Иванов Иван Иванович",
  "email": "user@example.com",
  "phone": "+79991234567",
  "type": "individual",
  "code": "ABC123",
  "balance": 1234.56,
  "company_name": "ООО Ромашка",
  "inn": "1234567890",
  "kpp": "0987654321",
  "legal_address": "г. Москва, ул. Ленина, д. 1",
  "postal_address": "г. Москва, ул. Ленина, д. 1",
  "bank_name": "АО Банк",
  "bik": "044525225",
  "account_number": "40702810900000012345",
  "correspondent_account": "30101810400000000225"
}
```

---

### <span style="color: red;">401 Unauthorized</span>
Неверный или отсутствующий токен авторизации.

```json
{
  "result": "error",
  "message": "Unauthorized"
}
```
