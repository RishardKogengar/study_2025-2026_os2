---
## Front matter
lang: ru-RU
title: Лабораторная работа №2
subtitle: Управление пользователями и группами
author:
  - Ришард Когенгар
institute:
  - Российский университет дружбы народов, Москва, Россия
date: 9 сентября 2025

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

Получить представление о работе с учётными записями пользователей и группами пользователей в операционной системе типа Linux.

# Ход выполнения работы

## Проверка пользователя и переход на root

![Проверка пользователя rkogengar](Screenshot_1.png){ #fig:001 width=70% }

![Переход к пользователю root](Screenshot_1.png){ #fig:002 width=70% }

## Настройка sudoers

![Редактирование файла sudoers](Screenshot_2.png){ #fig:003 width=70% }

## Создание пользователей

![Создание пользователя alice](Screenshot_3.png){ #fig:004 width=70% }

## Создание пользователей

![Создание пользователя bob](Screenshot_4.png){ #fig:005 width=70% }

## Настройка login.defs

![Редактирование login.defs](Screenshot_5.png){ #fig:006 width=70% }

## Изменение .bashrc

![Изменение файла .bashrc](Screenshot_6.png){ #fig:007 width=70% }

## Создание пользователя carol

![Создание пользователя carol](Screenshot_7.png){ #fig:008 width=70% }

## Настройка срока действия пароля

![Настройка срока действия пароля](Screenshot_8.png){ #fig:009 width=70% }

## Проверка системных файлов

![Проверка записей о пользователях](Screenshot_9.png){ #fig:010 width=70% }

## Работа с группами

![Проверка пользователей и групп](Screenshot_10.png){ #fig:011 width=70% }

# Итоги работы

## Вывод

В ходе работы были изучены основы управления пользователями и группами в Linux: создание учётных записей, настройка паролей, редактирование sudoers и работа с группами. Система успешно установлена и проверена в VirtualBox.

