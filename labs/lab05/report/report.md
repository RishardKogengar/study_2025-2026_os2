---
## Front matter
title: "Отчёт по лабораторной работе №5"
subtitle: "Управление системными службами"
author: "Ришард Когенгар"

## Generic otions
lang: ru-RU
toc-title: "Содержание"

## Bibliography
bibliography: bib/cite.bib
csl: pandoc/csl/gost-r-7-0-5-2008-numeric.csl

## Pdf output format
toc: true
toc-depth: 2
lof: true
lot: true
fontsize: 12pt
linestretch: 1.5
papersize: a4
documentclass: scrreprt
## I18n polyglossia
polyglossia-lang:
  name: russian
  options:
    - spelling=modern
    - babelshorthands=true
polyglossia-otherlangs:
  name: english
## I18n babel
babel-lang: russian
babel-otherlangs: english
## Fonts
mainfont: IBM Plex Serif
romanfont: IBM Plex Serif
sansfont: IBM Plex Sans
monofont: IBM Plex Mono
mathfont: STIX Two Math
mainfontoptions: Ligatures=Common,Ligatures=TeX,Scale=0.94
romanfontoptions: Ligatures=Common,Ligatures=TeX,Scale=0.94
sansfontoptions: Ligatures=Common,Ligatures=TeX,Scale=MatchLowercase,Scale=0.94
monofontoptions: Scale=MatchLowercase,Scale=0.94,FakeStretch=0.9
mathfontoptions:
## Biblatex
biblatex: true
biblio-style: "gost-numeric"
biblatexoptions:
  - parentracker=true
  - backend=biber
  - hyperref=auto
  - language=auto
  - autolang=other*
  - citestyle=gost-numeric
## Pandoc-crossref LaTeX customization
figureTitle: "Рис."
tableTitle: "Таблица"
listingTitle: "Листинг"
lofTitle: "Список иллюстраций"
lotTitle: "Список таблиц"
lolTitle: "Листинги"
## Misc options
indent: true
header-includes:
  - \usepackage{indentfirst}
  - \usepackage{float}
  - \floatplacement{figure}{H}
---

# Цель работы

Получить навыки управления системными службами операционной системы посредством systemd.

# Ход выполнения

## Управление сервисом Very Secure FTP (vsftpd)

1. Получены права администратора и выполнена проверка состояния службы **vsftpd**.  
   Так как пакет не был установлен, команда вывела сообщение об отсутствии юнита.  

   ![Проверка статуса vsftpd до установки](Screenshot_1.png){ #fig:001 width=80% }

2. Установлен пакет **vsftpd** при помощи пакетного менеджера **dnf**.  
   Установка прошла успешно, зависимости были загружены и проверены.  

3. Служба **vsftpd** была запущена.  
   Проверка состояния показала, что демон активен и работает, но пока отключён от автозапуска.  

   ![Запуск службы vsftpd](Screenshot_2.png){ #fig:002 width=80% }

4. Добавлен сервис **vsftpd** в автозапуск при старте системы.  
   После этого его статус изменился на **enabled**.  

   ![Добавление в автозапуск](Screenshot_3.png){ #fig:003 width=80% }

5. Сервис был удалён из автозапуска с помощью команды **systemctl disable**, однако он остался активным до перезагрузки системы.  

   ![Отключение автозапуска](Screenshot_4.png){ #fig:004 width=80% }

6. Проверен список символических ссылок в каталоге `/etc/systemd/system/multi-user.target.wants`.  
   На момент проверки ссылка на **vsftpd** отсутствовала.  

   Затем сервис снова был добавлен в автозапуск, и в каталоге появилась новая ссылка на юнит **vsftpd.service**.  

7. Повторная проверка статуса показала, что служба работает и имеет состояние **enabled**.  

   ![Статус службы после включения автозапуска](Screenshot_5.png){ #fig:005 width=80% }

8. Выведен список зависимостей юнита **vsftpd**.  
   Из него видно, что сервис входит в цель **multi-user.target**.  

9. Выведен список юнитов, которые зависят от **vsftpd**.  
   Полученная информация позволяет понять, какие службы связаны с его запуском.  

   ![Обратные зависимости vsftpd](Screenshot_6.png){ #fig:006 width=80% }

## Конфликты юнитов: iptables и firewalld

1. Получены полномочия администратора и установлены пакеты **iptables**.  
   Установка прошла успешно, в систему добавлены необходимые зависимости.  

   ![Установка iptables](Screenshot_7.png){ #fig:007 width=80% }

2. Проверен статус служб **firewalld** и **iptables**.  
   FirewallD работает и активен, тогда как iptables находится в состоянии **inactive**.  

   ![Проверка статуса firewalld и iptables](Screenshot_8.png){ #fig:008 width=80% }

3. Выполнена попытка запуска обоих сервисов.  
   При старте одной службы вторая деактивируется, что демонстрирует наличие конфликта.  

   ![Попытка запуска iptables и firewalld](Screenshot_9.png){ #fig:009 width=80% }

4. Просмотрено содержимое файла юнита **firewalld.service**.  
   В настройках зафиксирован конфликт с сервисами `iptables.service`, `ip6tables.service`, `ebtables.service`, `ipset.service`.  

5. Просмотрено содержимое файла юнита **iptables.service**.  
   В нём отсутствует явное указание на конфликтующие службы, но определены параметры запуска iptables.  

   ![Файл юнита iptables](Screenshot_10.png){ #fig:010 width=80% }

6. Служба **iptables** остановлена, после чего снова запущен сервис **firewalld**.  
   Это гарантирует, что в системе активен только FirewallD.  

7. Для предотвращения случайного запуска iptables выполнена команда **systemctl mask iptables**.  
   В результате создана символическая ссылка на `/dev/null` в каталоге `/etc/systemd/system/iptables.service`.  

8. Попытка запуска **iptables** показала сообщение об ошибке: сервис замаскирован и не может быть активирован.  
   Аналогично, добавление в автозапуск также завершилось ошибкой.  

   ![Ошибка запуска замаскированного сервиса](Screenshot_11.png){ #fig:011 width=80% }

## Изолируемые цели

1. Получены полномочия администратора. Выполнен поиск всех целей, которые могут быть изолированы.  
   В результатах видно, что такие цели содержат строку `AllowIsolate=yes`.  

   ![Список изолируемых целей](Screenshot_12.png){ #fig:012 width=80% }

2. Система переведена в режим восстановления с помощью изоляции цели **rescue.target**.  
   Для входа потребовался пароль пользователя **root**.  

3. Выполнен перезапуск системы через изоляцию цели **reboot.target**.  

   ![Изоляция цели reboot.target](Screenshot_13.png){ #fig:013 width=80% }

## Цель по умолчанию

1. Получены полномочия администратора. Проверена текущая цель, установленная по умолчанию — ею оказалась **graphical.target**.  

   ![Проверка цели по умолчанию](Screenshot_14.png){ #fig:014 width=80% }

2. Цель по умолчанию изменена на **multi-user.target** (текстовый режим).  
   При этом была создана соответствующая символическая ссылка.  

3. После перезагрузки система загрузилась в текстовом режиме.  
   Затем снова изменена цель по умолчанию — на **graphical.target** для загрузки графического интерфейса.  

   ![Установка graphical.target как цели по умолчанию](Screenshot_15.png){ #fig:015 width=80% }

# Контрольные вопросы

1. Юнит — это объект управления в systemd, описывающий поведение системных ресурсов. Примеры: сервисы (sshd.service, nginx.service), цели (multi-user.target, graphical.target), устройства (dev-sda.device), сокеты (cups.socket), точки монтирования (home.mount).

2. Команда `systemctl disable` исключает цель из списка автозапуска. Проверить можно просмотром содержимого каталогов с расширением `.wants`.

3. Для отображения всех загруженных сервисных юнитов используется `systemctl list-units --type=service`.

4. Потребность в сервисе создаётся через `systemctl enable`, что приводит к созданию символьной ссылки в каталоге `.wants`.

5. Переключение в режим восстановления выполняется через `systemctl isolate rescue.target`.

6. Цель не может быть изолирована, если в её юнит-файле отсутствует параметр `AllowIsolate=yes`.

7. Для просмотра зависимых юнитов используется `systemctl list-dependencies имя_сервиса --reverse`.


# Заключение

В ходе работы были изучены основы управления сервисами в системе systemd, а также методы их установки, запуска, добавления и удаления из автозагрузки. Рассмотрены конфликты между юнитами, способы их разрешения, изолируемые цели и настройка цели по умолчанию.
