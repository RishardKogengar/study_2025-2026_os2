---
## Front matter
title: "Отчёт по лабораторной работе №11"
subtitle: "Управление загрузкой системы"
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

Получить навыки работы с загрузчиком системы GRUB2.

# Ход выполнения

## Модификация параметров загрузчика GRUB2

1. Вход выполнен под пользователем **rkogengar**. Получены права администратора командой **su**.  
   После ввода пароля открыт файл **/etc/default/grub** для редактирования.  
   В параметрах конфигурации установлен интервал отображения меню загрузчика **GRUB_TIMEOUT=20**.  

   ![Редактирование файла /etc/default/grub](Screenshot_1.png){ #fig:001 width=80% }

2. После сохранения изменений выполнена генерация нового конфигурационного файла загрузчика с помощью команд **grub2-mkconfig > /boot/grub2/grub.cfg** и **grub2-mkconfig -o /boot/grub2/grub.cfg**.  
   Процесс завершился успешно, о чём сообщает вывод утилиты.  

   ![Создание нового файла конфигурации GRUB2](Screenshot_2.png){ #fig:002 width=80% }

3. После перезагрузки системы появилось меню загрузчика **GRUB version 2.12**, содержащее несколько пунктов загрузки ядра **Rocky Linux**.  

   ![Отображение меню GRUB](Screenshot_3.png){ #fig:003 width=80% }

## Устранения неполадок

4. Для перехода в режим восстановления (rescue mode) выбран текущий пункт ядра и нажата клавиша **e**.  
   В строку, начинающуюся с **linux ($root)/vmlinuz**, добавлен параметр **systemd.unit=rescue.target**, после чего система загружена комбинацией **Ctrl + X**.  

   ![Редактирование параметров ядра для rescue.target](Screenshot_4.png){ #fig:004 width=80% }

5. После входа в систему в режиме восстановления выполнена проверка загруженных модулей с помощью команды **systemctl list-units**.  
   Видно, что загружена минимальная системная среда. Также просмотрены переменные окружения командой **systemctl show-environment**.  

   ![Проверка загруженных модулей и переменных окружения](Screenshot_5.png){ #fig:005 width=80% }

6. После перезагрузки снова открыт режим редактирования записи ядра и добавлен параметр **systemd.unit=emergency.target**, что позволяет перейти в аварийный режим.  

   ![Настройка загрузки в emergency.target](Screenshot_6.png){ #fig:006 width=80% }

7. В аварийном режиме проверено состояние активных системных юнитов командой **systemctl list-units**.  
   Вывод показывает минимальный набор активных служб и устройств.  

   ![Проверка активных юнитов в emergency.target](Screenshot_7.png){ #fig:007 width=80% }

## Сброс пароля root

8. Для сброса пароля root при загрузке система переведена в минимальный режим с параметром **rd.break**, который добавлен в конце строки ядра.  

   ![Загрузка с параметром rd.break](Screenshot_8.png){ #fig:008 width=80% }

9. После остановки на этапе **initramfs** выполнена попытка монтирования корневой файловой системы в режиме чтения-записи и входа в системную среду с помощью команд **mount -o remount,rw /sysroot**, **chroot /sysroot**, **passwd**.  
   Однако команды **chroot** и **passwd** оказались недоступны на данном этапе, что подтверждается сообщениями об ошибке.  

   ![Попытка сброса пароля root](Screenshot_9.png){ #fig:009 width=80% }

# Контрольные вопросы

1. Для применения общих изменений в загрузчике **GRUB2** необходимо редактировать файл конфигурации **/etc/default/grub**.  

2. Основной конфигурационный файл **GRUB2**, в который записываются изменения и который используется при загрузке системы, — это **/boot/grub2/grub.cfg**.  

3. После внесения изменений в настройки **GRUB2** нужно выполнить команду **grub2-mkconfig -o /boot/grub2/grub.cfg**, чтобы обновлённая конфигурация была сохранена и применена при следующей загрузке системы.  


# Заключение

В ходе работы были изучены методы настройки и модификации загрузчика **GRUB2**, а также способы восстановления системы и сброса пароля root с использованием различных режимов загрузки.  
