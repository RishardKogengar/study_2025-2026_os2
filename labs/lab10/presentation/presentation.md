---
## Front matter
lang: ru-RU
title: Лабораторная работа №10
subtitle: Основы работы с модулями ядра операционной системы
author:
  - Ришард Когенгар
institute:
  - Российский университет дружбы народов, Москва, Россия
date: 21 октября 2025

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

Получить навыки работы с утилитами управления модулями ядра операционной системы Linux.

# Ход выполнения работы

## Просмотр подключённого оборудования

![Вывод команды lspci -k](Screenshot_1.png){ #fig:001 width=70% }

## Список загруженных модулей

![Просмотр загруженных модулей](Screenshot_2.png){ #fig:002 width=70% }

## Проверка и загрузка модуля ext4

![Загрузка и проверка модуля ext4](Screenshot_3.png){ #fig:003 width=70% }

## Информация о модуле ext4

## Выгрузка модулей ext4 и xfs

![Попытка выгрузки модулей ext4 и xfs](Screenshot_4.png){ #fig:004 width=70% }

# Загрузка модулей ядра с параметрами

## Проверка и загрузка bluetooth

![Загрузка и проверка модуля bluetooth](Screenshot_5.png){ #fig:005 width=70% }

## Выгрузка модуля bluetooth

![Выгрузка модуля bluetooth](Screenshot_6.png){ #fig:006 width=70% }

## Проверка версии и списка пакетов ядра

![Проверка версии ядра и доступных пакетов](Screenshot_7.png){ #fig:007 width=70% }

## Обновление ядра и системы

![Обновление ядра и системы](Screenshot_8.png){ #fig:008 width=70% }

## Проверка новой версии ядра

![Проверка новой версии ядра](Screenshot_9.png){ #fig:009 width=70% }

# Итоги работы

## Вывод

В ходе работы были изучены команды управления модулями ядра Linux, их загрузка, выгрузка и просмотр параметров.  
Также выполнено обновление системы и ядра, что позволило закрепить навыки администрирования в среде Rocky Linux.
