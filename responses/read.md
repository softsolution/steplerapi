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
Прочтение отклика

Метод: POST
URL:  http://careerist.ru/scr/api/read-response   
Ответ: возвращается json массив вида array(‘data’ => ‘success’, ‘errors_message’ =>’’)
В случае успеха ‘data’ содержит ‘success’: -
В случае неудачи ошибки в ‘errors_message’
Входные данные: 
Пример массива на PHP - 
$_POST = array(  'Login' => 'your_mail@maildomain.ua ',  'LoginKey' => md5(login+password), 
'ResponseID' => 'your_response_id'); 
