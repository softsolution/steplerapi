## content.get_item_company

Возвращает подробное описание компании по заданному id.  Аналогичен методам [content.get_item_vacancy](/vacancy/get_item.md) и [content.get_item_resume](/resume/get_item.md).


### Параметры

| Название |Описание |
|----|----|
| **item_id** | id записи, данные которой нужно вернуть. Положительное число. Параметр **обязательный**. |

### Пример

```
https://step-ler.ru/api/method/content.get_item_company?api_key=API_KEY&item_id=7
```

### Результат

После успешного выполнения возвращает объект, содержащий данные записи компании в поле item и объект additionally, в котором показаны объекты:

  * категория **category**, если компания привязана к категории;

![](https://step-ler.ru/upload/api/company-get-item.png "company-get-item.png")

### Коды ошибок

| Код |Описание |
|----|----|
| **320** | Запись на модерации |
| **321** | Запись не опубликована |

В ходе выполнения также могут произойти [общие ошибки](/docs/errors.md)

[НА ГЛАВНУЮ](/README.md)