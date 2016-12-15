---
title: Установка Composer
---

Composer является обычным PHP-приложением, упакованным в Phar-архив,
поэтому для его установки требуется только установленный PHP с обычным 
набором модулей. Впоследствии для работы могут потребоваться клиенты 
различных VCS, в частности, Git.

Composer может устанавливаться как глобально (доступен в виде 
консольной команды, работающей во всех директориях), так и локально
(доступен в виде исполняемого файла в проекте). В случае локальной 
установки рекомендуется исключать Composer из списка файлов, хранимых
системой контроля версий.

С официальной документацией по установке можно ознакомиться 
[здесь][installation].

# Linux / Mac

Стабильная версия Composer вышла в апреле 2016, поэтому некоторые 
дистрибутивы Linux позволяют установить Composer через менеджер 
пакетов. Например, в Ubuntu 16.04+ установка может выглядеть так:
 
    apt-get install composer
    
В том случае, если в системе нет пакетного менеджера или в нем не 
присутствует Composer, его можно установить с помощью самого PHP.

Для этого достаточно так или иначе получить PHP-установщик, 
распространяемый по адресу [https://getcomposer.org/installer](), и
запустить с его с ключами `--install-dir` и `--filename` для указания
желаемого местоположения:

    curl https://getcomposer.org/installer -o installer.php 
    php installer.php --install-dir . --filename composer
    
или, в одну строчку:

    curl -Ss https://getcomposer.org/installer | php -- --install-dir . --filename composer
    
В приведенном примере установщик установит Composer в текущую 
директорию (`.`) файлом `composer`, и его можно будет запускать с 
помощью команды `php composer`.

Для глобальной установки достаточно установить Composer в директорию, 
присутствующую в системной переменной `$PATH`, например, в `/usr/local/bin`

    # sudo необходим для записи в системный каталог
    sudo php installer.php --install-dir /usr/local/bin --filename composer
    # добавление прав на исполнение в UNIX-системах
    sudo chmod a+x /usr/local/bin/composer
    
После этого Composer будет доступен консольной командой, как, например,
`git` или `php`

    composer about
    
    > Composer - Package Management for PHP
    > Composer is a dependency manager tracking local dependencies of your projects and libraries.
    > See https://getcomposer.org/ for more information.

# Windows

Самым простым способом установки Composer на Windows является 
официальный установщик, распространяемый по адресу 
[https://getcomposer.org/Composer-Setup.exe](). После выполнения
процедуры установки этим установщиком Composer будет доступен как 
обычная консольная программа, и им можно будет пользоваться из любой 
директории.

# Обновление Composer

Для обновления Composer по мере выхода новых версий достаточно просто 
вызывать его с командой self-update:

    composer self-update
    
В случае, если Composer установлен глобально, может потребоваться 
получение привилегий суперпользователя (UNIX, sudo) или администратора 
(Windows, запуск командной строки с привилегиями администратора).

  [installation]: https://getcomposer.org/doc/00-intro.md