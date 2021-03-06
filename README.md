#Backformer 2.5.0

Форма обратной связи - [скачать](https://github.com/Rugoals/backformer/archive/2.5.1.zip).

#####Системные требования
* PHP5 >= 5.2.0
* Jquery >= 1.7

## Как подключить 

#####1. Подключить скрипты в указанной последовательности

    <script src="//ajax.googleapis.com/ajax/libs/jquery/1.11.1/jquery.min.js"></script>
    
    <!-- backformer -->
    <link href="/backformer/core/themes/default/bf.css" type="text/css" rel="stylesheet" />
    <script src="/backformer/core/components/jquery.form.min.js"></script> 
    <script src="/backformer/core/components/backformer.js"></script>
    <!-- // backformer -->

#####2. Вызов для встроенной формы на странице

Для подключения достаточно навесить на форму атрибут **data-bf-config=""** и передать ему название конфигурации.
 
По умолчанию, при пустом вызове конфигурации, будет браться из папки **/configs/default**. Можно создать сколько угодно конфигураций, просто копируя папку **default** с другим названием.  

Поддерживается наследование конфигураций. Например в новой можно не указывать почту получателя, она возьмётся из папки - **default**.

#####3. Вызов всплывающего окна

Нужно навесить атрибут **data-bf-config=""** на любой тег, кроме формы, по нажатию на который ожидается вызов всплывающего окна.

В всплывающую форму можно передать параметры через data-атрибуты, например: 

    data-bf-field-title="Параметр title"  

В шаблоне отправки на почту можно будет добавить переменную **{{bf_field_title}}**, в которой будет передаваемое содержимое. Стоит учесть, что здесь используется нижнее подчёркивание.

В шаблоне формы будет доступен класс **.bf-field-title**, в который будет передаваться значение заданной переменной.

Пример:

    <p class="bf-field-title">Тут будет значение.</p>
    
Где **title** можно заменить на своё название.

Также доступны два системных класса:

    .bf-page-link - адрес страницы оформления формы
    .bf-page-h1 - тег H1 страницы оформления формы


#####4. Что внутри

* config.php - конфигурационный файл. Внутри него комментарии для настройки.
* /templates/report.html - шаблон отправки на почту. В качестве шаблона для полей используется конструкция **{{название_поля}}**. Работает с использованием шаблонизатора Twig.
* /templates/form.html - форма для всплывающего окна.
* /model/events.class.php - php-класс, расширяющий функционал формы.

#####5. Шаблон отправки на почту

В нём доступны две переменные со страницы оформления формы:

* {{bf_page_link}} - адрес страницы оформления формы
* {{bf_page_h1}} - тег **H1** страницы оформления формы

 
