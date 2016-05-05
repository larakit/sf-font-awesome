# larakit/sf-font-awesome

### Установка пакета 
~~~bash
composer require larakit/sf-font-awesome
~~~
Ничего дополнительно инициализировать не надо, добавив этот пакет в зависимости в composer.json, он сам установится и пропишется на всех страницах автоматически.

### Отключение пакета на некоторых роутах
В файле  ./app/Http/staticfiles.php добавьте
~~~php
\Larakit\StaticFiles\Manager::package('larakit/sf-font-awesome')
    ->addExclude('home')
    ->addExclude('admin.*');
~~~    
тогда пакет не будет включен на главной странице и на всех страницах админки.

### Изменение состава подключаемой статики пакета
Если вы использовали какой-то пакет, который за собой потянул этот пакет, но вас не устраивает версия библиотеки, подключаемая по умолчанию (например не хотите использовать CDN, а хотите отдавать со своего сайта), то вместо базового способа инициализации пакета
~~~php
\Larakit\StaticFiles\Manager::package('larakit/sf-font-awesome')
    ->css('//cdnjs.cloudflare.com/ajax/libs/font-awesome/4.6.2/css/font-awesome.min.css');
~~~
вы можете переопределить его, вызвав инициализацию пакета еще раз
~~~php
\Larakit\StaticFiles\Manager::package('larakit/sf-font-awesome')
    //очистить список подключенных JS и CSS
    ->clearJs()
    ->clearCss()
    //добавить свои
    ->css('/css/font-awesome.css');
~~~
