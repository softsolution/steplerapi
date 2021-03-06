## content.get_item_vacancy

Возвращает подробное описание вакансии по заданному id.  Аналогичен методам [content.get_item_company](/company/get_item.md) и [content.get_item_resume](/resume/get_item.md).

Для получения вакансии, которая находящейся в архиве, требуется авторизация

### Параметры

| Название |Описание |
|----|----|
| **item_id** | id записи, данные которой нужно вернуть. Положительное число. Параметр **обязательный**. |
| **email** | Email пользователя с профилем работодателя. Если требуется получить вакансию из архива работодателя и он ранее не был авторизован. Необязательный параметр, если [авторизация](/auth/login.md) произведена ранее | string |
| **password** | Пароль пользователя - работодателя. Если требуется получить вакансию из архива работодателя и он ранее не был авторизован. Необязательный параметр, если [авторизация](/auth/login.md) произведена ранее | string |


### Пример

```
https://step-ler.ru/api/method/content.get_item_vacancy?api_key=API_KEY&item_id=7
```

### Результат

После успешного выполнения возвращает объект, содержащий данные записи компании в поле item и объект additionally, содержащий дополнительные параметры

![](https://step-ler.ru/upload/api/vacancy-get-item.png "vacancy-get-item.png")

### Коды ошибок

| Код |Описание |
|----|----|
| **320** | Запись на модерации |
| **321** | Запись не опубликована |

В ходе выполнения также могут произойти [общие ошибки](/docs/errors.md)

[НА ГЛАВНУЮ](/README.md)