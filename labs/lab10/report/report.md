---
## Front matter
title: "Отчёт по лабораторной работе №10"
subtitle: "Основы работы с модулями ядра операционной системы"
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

Получить навыки работы с утилитами управления модулями ядра операционной системы.

# Ход выполнения

## Управление модулями ядра из командной строки

1. В терминале были получены полномочия администратора. После входа под пользователем **root** была просмотрена информация о подключённом оборудовании и связанных с ним модулях ядра.  
   Команда lspci -k показала устройства, среди которых: видеоконтроллер VMware SVGA II, сетевой адаптер Intel 82540EM, виртуальная служба VirtualBox Guest Service, аудиоконтроллер Intel AC'97, USB-контроллер Apple Inc. и SATA-контроллер Intel.  
   Для каждого устройства отображены используемые драйверы ядра и возможные модули.  

   ![Вывод команды lspci -k](Screenshot_1.png){ #fig:001 width=80% }

2. Выполнена проверка списка всех загруженных модулей с помощью команды lsmod | sort.  
   Выведен обширный перечень загруженных модулей: сетевые драйверы, файловые системы, звуковые и USB-модули, а также модули подсистемы VirtualBox.  

   ![Просмотр загруженных модулей](Screenshot_2.png){ #fig:002 width=80% }

3. Проверено наличие загруженного модуля **ext4**, отвечающего за работу одноимённой файловой системы.  
   После выполнения команды lsmod | grep ext4 модуль не был найден.  
   Затем с помощью modprobe ext4 модуль был загружен, и повторная проверка подтвердила его присутствие в системе.  

   ![Загрузка и проверка модуля ext4](Screenshot_3.png){ #fig:003 width=80% }

4. Командой modinfo ext4 была получена подробная информация о модуле **ext4**:  
   - путь к файлу модуля (/lib/modules/.../ext4.ko.xz);  
   - описание (Fourth Extended Filesystem);  
   - авторы — Remy Card, Stephen Tweedie и др.;  
   - лицензия GPL;  
   - зависимые модули (jbd2, mbcache);  
   - цифровая подпись ядра Rocky Linux.  
   У модуля отсутствуют параметры, что подтверждает его статическую конфигурацию.  

   ![Информация о модуле ext4](Screenshot_4.png){ #fig:004 width=80% }

5. Попытка выгрузить модуль **ext4** (modprobe -r ext4) завершилась без ошибок, а последующая команда для модуля **xfs** выдала сообщение о невозможности удаления, так как модуль находится в использовании. Это штатное поведение для активных файловых систем.  

## Загрузка модулей ядра с параметрами

1. Проверено наличие модуля **bluetooth** в системе (lsmod | grep bluetooth).  
   После его загрузки (modprobe bluetooth) модуль стал активен, что подтверждено повторной проверкой.  

   ![Загрузка и проверка модуля bluetooth](Screenshot_5.png){ #fig:005 width=80% }

2. Командой modinfo bluetooth получена информация о модуле:  
   - описание — Bluetooth Core ver 2.22;  
   - автор — Marcel Holtmann;  
   - лицензия GPL;  
   - зависимость от модуля rfkill;  
   - подпись и версия ядра 6.12.0-55.12.1.el10_0.x86_64.  
   Также указаны параметры, регулирующие поведение Bluetooth:  
   disable_esco, disable_ertm, enable_ecred.  

3. После проверки модуль был успешно выгружен (modprobe -r bluetooth).  

   ![Выгрузка модуля bluetooth](Screenshot_6.png){ #fig:006 width=80% }

## Обновление ядра системы

1. Определена версия используемого ядра (uname -r) — **6.12.0-55.12.1.el10_0.x86_64**.  
   Затем выведен список установленных и доступных пакетов ядра (dnf list kernel).  
   Обнаружено, что доступна более новая версия — **6.12.0-55.37.1.el10_0.x86_64**.  

   ![Проверка версии ядра и доступных пакетов](Screenshot_7.png){ #fig:007 width=80% }

2. Выполнено обновление системы и ядра с помощью команд:  
   dnf update kernel, dnf update, dnf upgrade --refresh.  
   Обновление прошло успешно, система подтвердила отсутствие дополнительных зависимостей.  

   ![Обновление ядра и системы](Screenshot_8.png){ #fig:008 width=80% }

3. После перезагрузки команды uname -r и hostnamectl подтвердили, что система использует новое ядро **6.12.0-55.37.1.el10_0.x86_64**, дистрибутив — **Rocky Linux 10.0 (Red Quartz)**, а виртуализация выполняется в среде **VirtualBox**.  

   ![Проверка новой версии ядра](Screenshot_9.png){ #fig:009 width=80% }

# Контрольные вопросы

1. Чтобы узнать текущую версию ядра, используется команда **uname -r**.  

2. Более подробную информацию о текущей версии ядра можно получить с помощью команды **hostnamectl**, которая выводит сведения о системе, включая версию ядра, архитектуру и платформу.  

3. Для отображения списка загруженных модулей ядра используется команда **lsmod**.  

4. Определить параметры модуля ядра позволяет команда **modinfo имя_модуля**, где в выводе отображаются все возможные параметры и их описание.  

5. Для выгрузки модуля ядра применяется команда **modprobe -r имя_модуля**.  

6. Если при попытке выгрузить модуль появляется сообщение об ошибке, это означает, что модуль используется системой или другими зависимыми модулями. В этом случае необходимо сначала остановить соответствующие процессы или выгрузить зависимые модули.  

7. Чтобы определить, какие параметры поддерживает модуль, используется команда **modinfo имя_модуля** — в разделе *parm* указаны все доступные параметры и их назначение.  

8. Новую версию ядра можно установить при помощи менеджера пакетов командой **dnf update kernel** или **dnf upgrade --refresh**, после чего требуется перезагрузить систему и выбрать новое ядро при старте.

# Заключение

В ходе работы были изучены команды управления модулями ядра Linux, их загрузка, выгрузка и просмотр параметров. Также выполнено обновление системы и ядра, что позволило закрепить навыки администрирования в среде Rocky Linux.
