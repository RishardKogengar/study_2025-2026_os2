---
## Front matter
lang: ru-RU
title: Лабораторная работа №1
subtitle: Установка Rocky Linux в VirtualBox
author:
  - Ришард Когенгар
institute:
  - Российский университет дружбы народов, Москва, Россия
date: 2 сентября 2025

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

Установить Rocky Linux в VirtualBox, создать пользователя и проверить работу системы.

# Ход выполнения работы

## Создание виртуальной машины

![Создание виртуальной машины](image/Screenshot_1.png){ #fig:001 width=70% }

## Настройка жёсткого диска

![Настройка жёсткого диска](image/Screenshot_2.png){ #fig:002 width=70% }

## Запуск установщика

![Запуск установщика](image/Screenshot_3.png){ #fig:003 width=70% }

## Выбор языка установки

![Выбор языка установки](image/Screenshot_4.png){ #fig:004 width=70% }

## Настройка клавиатуры

![Настройка клавиатуры](image/Screenshot_5.png){ #fig:005 width=70% }

## Выбор окружения

![Выбор окружения](image/Screenshot_6.png){ #fig:006 width=70% }

## Установка пароля root

![Установка пароля root](image/Screenshot_7.png){ #fig:007 width=70% }

## Создание пользователя

![Создание пользователя](image/Screenshot_8.png){ #fig:008 width=70% }

## Обзор параметров и установка

![Обзор параметров](image/Screenshot_9.png){ #fig:009 width=70% }

## Ход установки системы

![Ход установки](image/Screenshot_10.png){ #fig:010 width=70% }

## Установка дополнений VirtualBox

![Guest Additions](image/Screenshot_11.png){ #fig:011 width=70% }

# Анализ системы

## Версия ядра и процессор

![Информация о ядре и CPU](image/Screenshot_12.png){ #fig:012 width=70% }

## Проверка гипервизора

![Проверка гипервизора](image/Screenshot_13.png){ #fig:013 width=70% }

## Смонтированные файловые системы

![Список файловых систем](image/Screenshot_14.png){ #fig:014 width=70% }

# Итоги работы

## Вывод

Rocky Linux установлен в VirtualBox. Создан root и пользователь, настроена клавиатура, добавлены Guest Additions. Система работает правильно и готова к использованию.

