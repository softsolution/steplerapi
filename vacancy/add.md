## content.add_vacancy

Добавляет вакансию. 

  - Сформировать форму в приложении;
  - Данные с этой формы отправить на этот метод, дополнительно передав явные параметры метода, описанные ниже.

Метод требует авторизации пользователя.

### Явные параметры

| Название | Описание | Тип |
|----|----|----|
| **to_draft** | 1 — сохранять в черновики. Флаг, может принимать значения 1 или 0. Параметр необязательный. | (0 или 1) |
| **sig** | Параметр привязан к ip адресу клиента и к домену сайта. Это **обязательный параметр**. Может быть получен методом [users.get_sig](/users/get_sig.md) | string |
| **csrf_token** | Параметр привязан к текущей сессии пользователя. Это **обязательный параметр**. Может быть получен методом [users.get_sig](/users/get_sig.md) | string |
| **email** | Email пользователя с профилем работодателя. Необязательный параметр, если [авторизация](/auth/login.md) произведена ранее | string |
| **password** | Пароль пользователя - работодателя. Необязательный параметр, если [авторизация](/auth/login.md) произведена ранее | string |
| **title** | Название вакансии. Это **обязательный параметр**. | string | 
| **content** | Описание вакансии. Это **обязательный параметр**. Не менее 150 символов | text html | 
| **category_id** | Основная специализация (профобласть) вакансии. Это категория первого уровня полученная из справочника Профобласти вакансий [content.get_categories.vacancy](/vacancy/get_categories.md) Это **обязательный параметр**. | integer |
| **add_cats** | Дополнительные профобласти для вакансии. Массив id значений полученных из справочника Профобласти вакансий [content.get_categories.vacancy](/vacancy/get_categories.md). До 5 категорий на вакансию | array | 
| **salary_from** | Оплата труда от ... , руб. | Decimal | 
| **salary** | Оплата труда до ... руб. | Decimal |
| **cities** | ID Город(ов) вакансии, Это **обязательный параметр**. Как минимум необходимо передать одно значение. Максимум 10 городов на вакансию. Id городов могут быть получены из справочника городов одним из методов [geo.get](/geo/get.md) или [geo.get_current_country](/geo/get_current_country.md) или [geo.get_city](/geo/get_city.md) | array |
| **showjobaddress** | Флаг показа адреса вакансии на карте. Флаг, может принимать значения 1 или 0. При значении 1, необходимо передать в параметре address_id Id адреса либо в параметре address передать адрес в текстовом формате. Если address_id и address не будут переданы, параметру showjobaddress будет присвоено значение = 0 автоматически. Компания с корректно указанным адресом будет показана на карте вакансий | boolean |
| **address_id** | id адреса вакансии из [справочника адресов компании](/company/get_addresses.md), необходимо передать при showjobaddress=1. Необязательный параметр  | integer |
| **address** | Адрес вакансии в текстовом формате: Страна, Регион, Город, улица(проспект, переулок), номер дома. Необходимо передать при showjobaddress=1 и не указанном параметре address_id. Необязательный параметр . | string |
| **temporary** | Возможно ли временное трудоустройство. Флаг, может принимать значения 1 или 0. | (0 или 1) |
| **employment** | Тип занятости. 10 - Полная занятость, 20 - частичная, 30 - Проектная работа, 40 - Волонтерство, 50 - Стажировка. По-умолчанию  employment=10 |  integer |
| **workmode** | Режим работы. Массив значений. Возможные значения: 10 - Работа только по сб и вс, 20 - Можно работать сменами по 4-6 часов в день, 30 - Можно начинать работать после 16-00  | array |
| **langs** | Знание языков. Массив значений в формате array(0 => array('id' => Id языка, 'level' => Id уровня владения)). Id языков и уровней владения берется из справочника [job.get_langs](/job/get_langs.md) | array |
| **respond** | Кто может откликаться на вакансию. Массив значений. Возможные значения: 10 - Соискатели с инвалидностью, 20 - Соискатели от 14 лет, 30 - Соискатели с неполным резюме, 40 - Только с сопроводительным письмом, 50 - Соискатели пенсионеры | array |
| **workexperience** | Требуемый опыт работы. Возможные значения: 0 - Нет опыта (по-умолчанию), 1 - От 1 года до 3 лет, 2 - От 3 до 6 лет, 3 - Более 6 лет | integer |
| **workschedule** | График работы. Возможные значения: 1 - Полный день (по-умолчанию), 2 - Сменный график, 3 - Гибкий график, 4 - Удаленная работа, 5 - Вахтовый метод | integer |
| **driverlicense** | Категории прав. Массив значений. Возможные значения (Значение - Категория): a - A, b - B, c - C, d - D, e - E, be - BE, ce - CE, de - DE, tm - Tm, tb - Tb | array |
| **contactman** | Контактное лицо. Фамилия, имя контактного человека по вакансии. | string |
| **contactinfo** | Флаг показа контактной информации на странице вакансии 1 - Не показывать (по-умолчанию), 2 - Показывать. При contactinfo = 2 учитываются параметры cemail, phone, comment | integer |
| **cemail** | Контактный email. По-умолчанию, берется значение из профиля пользователя | string |
| **phone** | Контактный телефон. Строка состоящая строго из цифр и знака +, например: 89010030019,  или +79010030019, +380111111111.  | string |
| **comment** | Комментарий к контактной информации. Например, можно указать удобное время звонка. | string |

### Пример

```
https://step-ler.ru/api/method/content.add_vacancy?api_key=API_KEY&sig=SIG&csrf_token=CSRF_TOKEN&title=MyFirstVacancy
```

### Результат

После успешного выполнения возвращает объект, содержащий текст успешного добавления в поле success_text и ID созданной записи в поле item_id.

![](https://step-ler.ru/upload/api/vacancy-add.png "vacancy-add.png")

### Коды ошибок

В ходе выполнения могут произойти как [общие ошибки](/docs/errors.md), так и ошибки формы с кодом 100 и описанием их в request_params.

[НА ГЛАВНУЮ](/README.md)