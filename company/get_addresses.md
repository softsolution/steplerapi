## content.get_addresses.company

Возвращает адреса авторизованного компании. Адреса используются при добавлении и редактировании вакансий. Метод требует авторизацию пользователя.

### Параметры

| Название |Описание | Тип |
|----|----|----|
| **email** | Email пользователя с профилем работодателя. Необязательный параметр, если [авторизация](/auth/login.md) произведена ранее  | string |
| **password** | Пароль пользвателя - работодателя. Необязательный параметр, если [авторизация](/auth/login.md) произведена ранее  | string |
| **ids** | Идентификаторы адресов (их id), информацию о которых необходимо вернуть. Список положительных чисел, разделенных запятыми. Параметр необязательный. | string |

### Пример

```
https://step-ler.ru/api/method/content.get_addresses.company?api_key=API_KEY
```

### Результат

После успешного выполнения возвращает объект, содержащий общее число категорий адресов в поле count и массив объектов адресов в поле items.

![](https://step-ler.ru/upload/api/company-get-addresses.png "company-get-addresses.png")

### Коды ошибок

В ходе выполнения также могут произойти [общие ошибки](/docs/errors.md)

[НА ГЛАВНУЮ](/README.md)