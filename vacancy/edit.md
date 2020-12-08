### auth.login

Авторизация пользователя стандартным способом (используются cookie). Используется стандартный механизм сессий и cookie, поэтому при данном запросе и последующих запросах, требующих авторизации пользователя, убедитесь, что cookie передаются.

### Базовые параметры

|Название| Описание |
|----|----|
| **email** | Email пользователя, которого хотим авторизовать. Параметр **обязательный**. |
| **password** | Пароль пользователя, которого хотим авторизовать. Параметр **обязательный**. |
| **sig** | Параметр привязан к ip адресу клиента и к домену сайта. Это **обязательный параметр**. |
| **remember** | Параметр "Запомнить меня". |

### Двухфакторная авторизация

В случае, если требуется двухфакторная авторизация, в объекте ответа будет:

  * поле ''wait_2fa'' со значением **true**;
  * поле ''2fa_type'' со значением типа 2FA авторизации;
  * поле ''2fa_params'' с массивом полей формы подтверждения и данными запроса

В следующий запрос этого метода необходимо будет передать помимо базовых параметров, параметры, необходимые для двухфакторной авторизации. Объект ''2fa_params.data'' будет содержать заполненные базовые параметры, объект ''2fa_params.form'' будет содержать параметры, которые необходимо передать.
В конечном итоге, в случае 2FA авторизации от Гугла, повторный запрос должен содержать:

  * email
  * password
  * sig
  * remember (необязательно)
  * csrf_token
  * ga_confirm_code
  * submit_confirm

### Пример

```
step-ler.ru/api/method/auth.login?api_key=API_KEY&sig=SIG&email=EMAIL&password=PASS
```

### Результат

После успешного выполнения возвращает объект, содержащий массив данных в поле ''user_info'', id авторизованного пользователя в поле ''user_id'', имя текущей сессии в поле session_name и id текущей сессии в поле ''session_id''. Если параметр **remember** был передан, отличным от ноля, в ответе также будет поле ''remember_token'', содержащее токен автоавторизации.

![](https://step-ler.ru/upload/api/auth-login1.png "auth-login1.png")

![](https://step-ler.ru/upload/api/auth-login2.png "auth-login2.png")

![](https://step-ler.ru/upload/api/auth-login3.png "auth-login3.png")

### Коды ошибок

В ходе выполнения также могут произойти [общие ошибки](/docs/errors.md)

[НА ГЛАВНУЮ](/README.md)

Метод: POST
URL:  http://careerist.ru/scr/api/create-vacancy
Ответ: возвращается json массив вида array('data' => array('id' => 123, 'status' => 'moder'), ‘errors_message’ =>’’)
В случае успеха ‘data’ содержит идент созданной вакансии или описание ошибки в ‘errors_message’
Входные данные:
Пример массива на PHP - 
$_POST = array( 
		
    [vacantName] => Create from api
    [vacantDepartment] => 137
    [SubCategoryID] => Array
        (
            [0] => 994
            [2] => 995
            [3] => 996
        )

    [vacantEmployment] => 1
    [vacantCity] => 38
    [vacantRegion] => 12
    [vacantSalary] => 15000
    [vacantSalaryTo] => 25000
    [vacantCommentDesc] => Array
        (
            [-2] => Обязанности 
            [-1] => Условия работы
            [0] => extra data
        )

    [vacantAge] => 18
    [vacantAgeTo] => 45
    [vacantGender] => 0
    [vacantExperience] => 30
    [edu] => 10
    [edumore] => 0
    [vacantlangID] => Array
        (
            [0] => 17
            [1] => 18
        )

    [vacantlangType] => Array
        (
            [0] => 1
            [1] => 3
        )

    [vacantcontContact] => Иванов Иван
    [CountryCode] => Array
        (
            [0] => +7
            [1] => +7
        )

    [CityCode] => Array
        (
            [0] => 234
            [1] => 234
        )

    [PhoneCode] => Array
        (
            [0] => 234444
            [1] => 342344
        )

    [ExtraCode] => Array
        (
            [0] => 43434
            [1] => 33444
        )

    [CountryCodeFax] => Array
        (
            [0] => +7
            [1] => +7
        )

    [CityCodeFax] => Array
        (
            [0] => 2342
            [1] => 344
        )

    [PhoneCodeFax] => Array
        (
            [0] => 4234324
            [1] => 444444
        )

    [ExtraCodeFax] => Array
        (
            [0] => 3434
            [1] => 4444
        )
    [vacantMetro] => Array
        (
            [0] => 326
            [1] => 328
        )
    [vacantcontMail] => apicompany@mail.ua
    [vacantcontWebSite] => http://microsoft.com
    [DataEdit] => 1
    [Login] => your_mail@mail.ua
    [LoginKey] => 4118a43752498559ed16a7a9b3661f1b
    [VacancyID] =>
); 

где, -

    Login => Логин пользователя
    LoginKey => md5(Login + password)
    vacantName => Название вакансии
    vacantDepartment => Сфера деятельности
    SubCategoryID => Каталог должностей
    vacantEmployment => Из списка типов занятости
    vacantCity => Город
    vacantRegion => регион
    vacantMetro => Метро
    vacantSalary => Зарплата, от
    vacantSalaryTo => Зарплата, до
    vacantCommentDesc => Массив данных где         
            [-2] => Обязанности 
            [-1] => Условия работы
            [0]  => Дополнительные комментарии    
    
    vacantAge => Возраст, от
    vacantAgeTo => Возраст, до
    vacantGender =>   Пол ( 2- неважно, 1- женский, 0- мужской)
    vacantExperience =>  Опыт работы ( из каталога )
    edu => Образование (из каталога)
    edumore => Уровень образование (из каталога)
    vacantlangID –Знание языков ( из каталога )
    vacantlangType => Уровень знаний языков ( из  каталога )
    vacantcontContact => Контактное лицо:
    
    Телефон, по анлогии с созданием компании
    CountryCode =>
    CityCode =>
    PhoneCode =>
    ExtraCode => 
    
    Факс, по анлогии с созданием компании

    CountryCodeFax => 
    CityCodeFax => 
    PhoneCodeFax => 
    ExtraCodeFax => 

    vacantcontMail => Электронный адрес контактного лица
    vacantcontWebSite => Сайт компании
    DataEdit => Видимость вакансии: (0 – Не видна никому , 1 – Видна всем)
    vacantWorkAddress => 	адрес места работы


Метод: POST
URL:  http://careerist.ru/scr/api/create-vacancy
Ответ: возвращается json массив вида array('data' => array('id' => 123, 'status' => 'moder'), ‘errors_message’ =>’’)
В случае успеха ‘data’ содержит идент созданной вакансии или описание ошибки в ‘errors_message’
Входные данные: Аналогично созданию вакансии + поле VacancyID, если  вакансия архивная, то в дате вернется идент новой вакансии, так как при этом создается новая вакансія, по сути происходит восстановление. 

