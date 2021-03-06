### execute

Универсальный метод, который позволяет запускать последовательность других методов, сохраняя промежуточные результаты и возвращая их все в одном ответе.
Внимание! Запрос будет иметь другой базовый вид:
```
https://step-ler.ru/api/execute?PARAMETERS&api_key=API_KEY
```

### Параметры

| Название |Описание |
|----|----|
| **code** | Строка JSON (UTF-8), описывающая массив запросов методов. Может содержаться не более 10 запросов к методам API. Одна ячейка массива методов должна иметь ключ **method** со значением названия метода и необязательный ключ **params** с массивом параметров метода. |

Обращаем ваше внимание, что JSON код должен быть валидным в контексте [RFC 4627](http://www.faqs.org/rfcs/rfc4627), не основывайтесь на валидности JavaScript объектов. Имя и значение должны помещаться в двойные кавычки, одинарные кавычки использовать нельзя. Не должно быть завершающей запятой (без последующего элемента).

### Пример

Пример поля **code**:

```
[{"method":"content.get_categories.articles","params":{"is_tree":"1"}},{"method":"content.get_datasets.articles"}]
```

### Результат

После успешного выполнения возвращает объект response, содержащий объекты с одноименными названиями методов и результатами согласно их спецификации.

![](https://step-ler.ru/upload/api/m_execute.png "m_execute.png")

### Коды ошибок

|Код| Описание |
|----|----|
| **12** | Невозможно скомпилировать код.  |
| **13** | Ошибка выполнения кода. |

В ходе выполнения также могут произойти [общие ошибки](/docs/errors.md)

[НА ГЛАВНУЮ](/README.md)