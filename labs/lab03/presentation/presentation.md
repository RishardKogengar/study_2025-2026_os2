---
## Front matter
lang: ru-RU
title: Лабораторная работа №3
subtitle: Управление базовыми разрешениями
author:
  - Ришард Когенгар
institute:
  - Российский университет дружбы народов, Москва, Россия
date: 14 сентября 2025

## i18n babel
babel-lang: russian
babel-otherlangs: english

## Formatting pdf
toc: false
slide_level: 2
aspectratio: 169
section-titles: true
theme: metropolis
header-includes:
 - \metroset{progressbar=frametitle,sectionpage=progressbar,numbering=fraction}
---

# Цель работы

## Основная цель

Получить навыки настройки базовых и специальных прав доступа для пользователей и групп в Linux.

# Ход выполнения работы

## Управление базовыми разрешениями

![Создание каталогов /data/main и /data/third](Screenshot_1.png){ #fig:001 width=70% }

## Управление базовыми разрешениями

![Создание файла emptyfile в каталоге /data/main](Screenshot_2.png){ #fig:002 width=70% }

## Управление специальными разрешениями

![Создание файлов alice1 и alice2](Screenshot_3.png){ #fig:003 width=70% }

## Управление специальными разрешениями

![Создание файлов alice3 и alice4 после setgid и sticky-bit](Screenshot_4.png){ #fig:004 width=70% }

## Управление доступом с использованием ACL

![Назначение ACL для каталогов](Screenshot_5.png){ #fig:005 width=70% }

## Управление доступом с использованием ACL

![Проверка ACL для файлов newfile1 и newfile2](Screenshot_6.png){ #fig:006 width=70% }

## Управление доступом с использованием ACL

![Назначение ACL по умолчанию](Screenshot_7.png){ #fig:007 width=70% }

## Управление доступом с использованием ACL

![Проверка доступа пользователя carol](Screenshot_8.png){ #fig:008 width=70% }

# Итоги работы

## Вывод

В ходе работы были изучены:  
- базовые разрешения для каталогов и групп,  
- специальные биты **setgid** и **sticky-bit**,  
- расширенные списки контроля доступа (**ACL**).  

Получены практические навыки по обеспечению безопасного совместного доступа к файлам и каталогам.
