---
## Front matter
lang: ru-RU
title: Лабораторная работа №4
subtitle: Работа с программными пакетами
author:
  - Ришард Когенгар
institute:
  - Российский университет дружбы народов, Москва, Россия
date: 16 сентября 2025

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

Получить навыки работы с репозиториями, менеджерами пакетов **dnf** и **rpm** в операционной системе Linux.

# Ход выполнения работы

## Работа с репозиториями DNF

![Просмотр содержимого каталога и файла rocky.repo](Screenshot_1.png){ #fig:001 width=70% }

## Работа с репозиториями DNF

![Список репозиториев](Screenshot_2.png){ #fig:002 width=70% }

## Поиск и установка пакетов

![Информация о пакете nmap](Screenshot_3.png){ #fig:003 width=70% }

## Поиск и установка пакетов

![Установка пакета nmap](Screenshot_4.png){ #fig:004 width=70% }

## Удаление и работа с группами пакетов

![Удаление пакета nmap](Screenshot_5.png){ #fig:005 width=70% }

## Удаление и работа с группами пакетов

![Работа с группами пакетов](Screenshot_6.png){ #fig:006 width=70% }

## История dnf

![История и откат изменений](Screenshot_9.png){ #fig:007 width=70% }

## Установка lynx

![Загрузка пакета lynx](Screenshot_10.png){ #fig:008 width=70% }

## Установка lynx

![Установка пакета lynx](Screenshot_11.png){ #fig:009 width=70% }

## Изучение пакета lynx

![Список файлов пакета lynx](Screenshot_12.png){ #fig:010 width=70% }

## Изучение пакета lynx

![Просмотр man-страницы lynx](Screenshot_14.png){ #fig:011 width=70% }

## Проверка и удаление lynx

![Запуск lynx](Screenshot_15.png){ #fig:012 width=70% }

## Проверка и удаление lynx

![Конфигурационные файлы lynx](Screenshot_16.png){ #fig:013 width=70% }

## Установка dnsmasq

![Установка и определение расположения dnsmasq](Screenshot_17.png){ #fig:014 width=70% }

## Документация и файлы dnsmasq

![Список файлов пакета dnsmasq](Screenshot_18.png){ #fig:015 width=70% }

## Документация и файлы dnsmasq

![Документация и man dnsmasq](Screenshot_19.png){ #fig:016 width=70% }

## Конфигурация и скрипты dnsmasq

![Установочные скрипты dnsmasq](Screenshot_20.png){ #fig:017 width=70% }

# Итоги работы

## Вывод

В ходе работы были закреплены практические навыки управления пакетами в Linux с помощью **dnf** и **rpm**:  
- работа с репозиториями и группами пакетов,  
- установка, удаление и изучение содержимого пакетов,  
- использование конфигурационных файлов и скриптов,  
- контроль безопасности устанавливаемых пакетов.  