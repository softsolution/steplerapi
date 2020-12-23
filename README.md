# Step-ler.ru API
Описание API сервиса поиска работы, размещения вакансий и резюме Step-ler.ru

### Авторизация
Все запросы к API подписываются ключом доступа, который предоставляет партнерам по запросу. Ключ API может передаваться как в POST/GET параметре, так и в заголовке запроса с именем api_key. Длина ключа может быть не более 32 символов. 

### Синтаксис запроса
Чтобы обратиться к любому методу API (за исключением метода execute, о нём ниже), вам необходимо выполнить POST или GET запрос такого вида: 

> https://step-ler.ru/api/method/METHOD_NAME?PARAMETERS&api_key=API_KEY

Он состоит из нескольких частей: 
* METHOD_NAME (обязательно) — название метода API, к которому Вы хотите обратиться.
* PARAMETERS (опционально) — входные параметры соответствующего метода API, последовательность пар name=value, разделенных амперсандом. Список параметров указан на странице с описанием метода. Значения параметров должны быть в кодировке UTF-8.
* API_KEY — ключ доступа.
Параметры могут передаваться как методом GET, так и POST. Если вы будете передавать большие данные (больше 2 килобайт), следует использовать POST. 

Обратите внимание, ответы возвращаются только в формате JSON.

### Разбивка на страницы
В ответах, где отдаётся список чего-либо с возможностью разбивки на страницы, присутствует объект paging, содержащий ячейки: 
* has_next (true или false) - флаг наличия следующей страницы;
* page - номер текущей страницы;
* per_page - количество элементов на одну страницу.

### Определение IP адреса посетителя
В случае, если запросы к api выполняются из одного места, например из скрипта PHP на сервере, но при этом необходимо, чтобы ip адрес посетителей учитывался в API, вы можете передавать ip адрес в параметре запроса с названием ip, например: 
> https://step-ler.ru/api/method/METHOD_NAME?PARAMETERS&api_key=API_KEY&ip=8.8.8.8

### Обработка ошибок
На все запросы к методам step-ler.ru/api/method/ и step-ler.ru/api/execute/, включая запросы с ошибками возвращают HTTP CODE 200.
Ошибки генерируются в JSON ответе специальным образом: 

```json
{  
    "error":{
       "error_code":101,
       "error_msg":"Неверный ключ доступа",
       "request_params":[  ]
    }
}
```

<a name="errors"></a>
Коды ошибок (error_code) совпадают в своем большинстве с кодами ошибок Вконтакте. 
В ячейке error_msg указывается текстовое представление ошибки на выбранном языке. В некоторых сообщениях об ошибках присутствует непустое поле request_params с массивом названий параметров и ошибками их валидации.

| Код | Описание |
|----|----|
| 1   | Произошла неизвестная ошибка |
| 2   | Ключ доступа выключен | 
| 3   | Передан неизвестный метод | 
| 5   | Авторизация пользователя не удалась | 
| 7   | Нет прав для выполнения этого действия | 
| 71  | Требуется авторизация пользователя | 
| 710 | Требуется административный доступ | 
| 8   | Неверный запрос | 
| 15  | Доступ запрещён | 
| 115 | Параметр sig не передан или является некорректным | 
| 23  | Метод был выключен | 
| 24  | Метод вам недоступен | 
| 100 | Один из необходимых параметров был не передан или неверен | 
| 101 | Неверный ключ доступа | 
| 115 | Параметр sig не передан или является некорректным | 
| 777 | ip адрес посетителя передан некорректный |


### Общие методы

| Название | Описание |
|----|----|
| [execute](methods/execute.md) | Универсальный метод, который позволяет запускать последовательность других методов, сохраняя промежуточные результаты и возвращая их все в одном ответе. |

### Авторизация и регистрация

| Название | Описание |
|----|----|
| [auth.signup_fields](auth/signup_fields.md) | Получает имена полей, обязательных для регистрации. |
| [auth.signup](auth/signup.md) 	| Регистрирует нового пользователя. |
| [auth.confirm](auth/confirm.md) 	| Завершает регистрацию нового пользователя, начатую методом auth.signup. при необходимости подтверждения email |
| [auth.restore](auth/restore.md) 	| Отправка запроса на восстановление пароля пользователя. |
| [auth.login](auth/login.md) 	    | Авторизация пользователя стандартным способом (используются cookie). |
| [auth.logout](auth/logout.md) 	| Разавторизация пользователя. |

### Местоположение

| Название | Описание |
|----|----|
| [geo.get](geo/get.md) | Возвращает список стран/регионов/городов. |
| [geo.get_current_country](geo/get_current_country.md) | Возвращает данные по текущей стране пользователя, если она была определена по его ip адресу. | 
| [geo.get_city](geo/get_city.md) | Поиск города или населенного пункта по параметрам | 

### Пользователи
| Название | Описание |
|----|----|
| [users.get_sig](users/get_sig.md) | Возвращает SIG и csrf_token. |

### Компании

| Название | Описание |
|----|----|
| [content.get_categories.company](company/get_categories.md) | Каталогизатор компаний | 
| [content.update_item_company](company/update_item.md) | Обновление информации о компании | 
| [content.get_item_company](company/get_item.md) | Получение информации о компании по ee Id | 
| [content.get_my_company](company/get_my.md) | Получение информации о моей компаниии (для авторизованной компании) | 


### Вакансии

| Название | Описание |
|----|----|
| [content.add_vacancy](vacancy/add.md) | Создание вакансии |
| [content.vacancy.delete](vacancy/delete.md) 	| Удаление вакансии | ![https://img.shields.io/badge/status-not%20ready-red](https://img.shields.io/badge/status-not%20ready-red) | 
| [content.edit_vacancy](vacancy/edit.md) 	| Редактирование вакансии |
| [vacancy.restore](vacancy/archive.md) 	| Отправка вакансии в архив | ![https://img.shields.io/badge/status-not%20ready-red](https://img.shields.io/badge/status-not%20ready-red) | 
| [vacancy.login](vacancy/.md) 	| Авторизация пользователя стандартным способом (используются cookie). | ![https://img.shields.io/badge/status-not%20ready-red](https://img.shields.io/badge/status-not%20ready-red) | 
| [vacancy.update](vacancy/update.md) 	| Обновление вакансии (поднятие в поиске) | ![https://img.shields.io/badge/status-not%20ready-red](https://img.shields.io/badge/status-not%20ready-red) | 
| [content.get_categories.vacancy](vacancy/get_categories.md) | Каталогизатор вакансий |
| [job.get_langs](job/get_langs.md) | Справочник языков |
| [job.get_langs_levels](job/get_langs_levels.md) | Справочник уровней владения языком |

### Отклики

| Название | Описание | Статус разработки |
|----|----|----|
| [responses.list](responces/list.md)       | Получение списка откликов | ![https://img.shields.io/badge/status-not%20ready-red](https://img.shields.io/badge/status-not%20ready-red) | 
| [responses.delete](responses/delete.md) 	| Удаление отклика | ![https://img.shields.io/badge/status-not%20ready-red](https://img.shields.io/badge/status-not%20ready-red) | 
| [responses.confirm](responses/read.md)    | Получение отклика | ![https://img.shields.io/badge/status-not%20ready-red](https://img.shields.io/badge/status-not%20ready-red) | 
Отказ по отклику
Приглашение по отклику

### Резюме
| Название | Описание |
|----|----|
| [content.get_categories.resume](resume/get_categories.md) | Каталогизатор резюме |