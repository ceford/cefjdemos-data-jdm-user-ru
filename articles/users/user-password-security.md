<!-- Filename: J5.x:Enhancing_Password_Security_with_Symbolic_Characters / Display title: Безопасность паролей пользователей -->

## Введение

В форме *Пользователи: Параметры* на вкладке *Параметры пароля* минимальные значения для *Цифры*, *Символы*, *Прописные буквы* и *Строчные буквы* по умолчанию установлены в 0. Для повышения безопасности эти значения следует установить на 1. Новые или измененные пароли должны содержать по одному из этих символов.  

## Символы

*Проект по обеспечению безопасности приложений по всему миру* (OWASP) рекомендует, чтобы все специальные символы, доступные на стандартной клавиатуре США, распознавались и принимались при установке требований к паролю.

```
 !"#$%&'()*+,-./:;<=>?@[\]^_`{|}~
 ```

Это не очевидно, но этот список включает пробел.

[OWASP: Специальные символы пароля](https://owasp.org/www-community/password-special-characters)

До версии 5.2 эти символы могли использоваться в паролях, но некоторые из них
не распознавались как символы для целей проверки пароля: 
```
@[]£^+±~<>/'",.
``` 

*Переведено с помощью openai.com*

