### method.name - имя метода

Описание метода

### Базовые параметры

|Название| Описание |
|----|----|
| **параметр1** | название параметра. Параметр **обязательный**.  или нет |
| **параметр2** | название параметра2. Параметр **обязательный**. или нет |


### особенности


### Пример использвоания

```
step-ler.ru/api/method/auth.login?api_key=API_KEY&sig=SIG&email=EMAIL&password=PASS
```

### Результат

После успешного выполнения возвращает объект, содержащий массив данных в поле ''user_info'', id авторизованного пользователя в поле ''user_id'', имя текущей сессии в поле session_name и id текущей сессии в поле ''session_id''. Если параметр **remember** был передан, отличным от ноля, в ответе также будет поле ''remember_token'', содержащее токен автоавторизации.

картинка если нужна с ответом
![](https://step-ler.ru/upload/api/auth-login1.png "auth-login1.png")



### Коды ошибок

В ходе выполнения также могут произойти [общие ошибки](/docs/errors.md)

[НА ГЛАВНУЮ](/README.md)

----------------------------
Метод: POST
URL:  http://careerist.ru/scr/api/get-responses-list   
Ответ: возвращается json массив вида array(‘data’ => array(), ‘errors_message’ =>’’)
В случае успеха ‘data’ содержит массив откликов вида: -
	Array
        (
          [data] => Array
        (
            [8144064e0e4513fc030cbafe75083d7f] => Array
                (
                    [resumeID] => 860775
                    [view] => 1
                    [FIO] => Arzhanov Alex
                    [mail] => vip.arzhanov@list.ru
                    [res_link] => http://carrierist.tu/alex_resume860775000000
		     [html_link] => ссылка на чистую хтмл версию резюме	
		     [byApplicant] => 1	//Прислан соискателем	
		     [Text] =>”Текст Отклика”	
		     [time] => Время создания
		     [readyToInvite]=> 1/0 – флаг доступности «отправки приглашения»
		     [readyToReject]=>	1/0 - флаг доступности «отказа»
                )

            [0564b7a872353bb460ee4a42dc96b427] => Array
                (
                    [resumeID] => 860776
                    [view] => 0
                    [FIO] => Arzhanov Alex
                    [mail] => vip.arzhanov@list.ru
                    [res_link] => http://carrierist.tu/alex_resume860776000000
		     [byApplicant] => 0 //Прислан по подписке
			[Text] =>”Текст Отклика”	
                ) 
        )
    [errors_message] =>   
        ) 
В случае неудачи, ошибки в ‘errors_message’
Входные данные: 
Пример массива на PHP - 
$_POST = array(  'Login' => 'your_mail@maildomain.ua ',  'LoginKey' => md5(login+password), 
'VacancyID' => 'your_vacancy_id'); 
	Если будет указан долнительный параметр 'new' – в списке будут только новые отклики


