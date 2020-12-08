## geo.get

Возвращает список стран/регионов/городов.

### Параметры

|Название| Описание |
|----|----|
| **type** | Тип данных для получения: countries, regions, cities. **Это обязательный параметр**. |
| **parent_id** | ID родительского списка. Передаётся при типах regions и cities. |

### Пример

Получение всех стран:
```
https://step-ler.ru/api/method/geo.get?api_key=API_KEY&type=countries
```

Получение регионов для России:
```
https://step-ler.ru/api/method/content.get_ctypes.news?api_key=API_KEY&type=regions&parent_id=3159
```

### Результат

После успешного выполнения возвращает объект, содержащий общее число записей в поле count и массив объектов в поле items.

![](https://step-ler.ru/upload/api/geo-get.png "geo-get.png")

### Коды ошибок

В ходе выполнения также могут произойти [общие ошибки](/docs/errors.md)

[НА ГЛАВНУЮ](/README.md)