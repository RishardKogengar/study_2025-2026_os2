---
## Front matter
lang: ru-RU
title: Лабораторная работа №11
subtitle: Управление загрузкой системы (GRUB2)
author:
  - Ришард Когенгар
institute:
  - Российский университет дружбы народов, Москва, Россия
date: 26 октября 2025

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

Получить навыки работы с загрузчиком системы **GRUB2**, его конфигурацией и методами восстановления загрузки системы.

# Ход выполнения работы

## Модификация параметров GRUB2

![Редактирование файла /etc/default/grub](Screenshot_1.png){ #fig:001 width=70% }

## Модификация параметров GRUB2

![Создание нового файла конфигурации GRUB2](Screenshot_2.png){ #fig:002 width=70% }

## Проверка меню загрузки

![Отображение меню GRUB](Screenshot_3.png){ #fig:003 width=70% }

# Устранение неполадок

## Переход в режим восстановления

![Редактирование параметров ядра для rescue.target](Screenshot_4.png){ #fig:004 width=70% }

## Проверка системных модулей

![Проверка загруженных модулей и переменных окружения](Screenshot_5.png){ #fig:005 width=70% }

## Аварийный режим

![Настройка загрузки в emergency.target](Screenshot_6.png){ #fig:006 width=70% }

## Аварийный режим

![Проверка активных юнитов в emergency.target](Screenshot_7.png){ #fig:007 width=70% }

# Сброс пароля root

## Загрузка с параметром rd.break

![Загрузка с параметром rd.break](Screenshot_8.png){ #fig:008 width=70% }

## Попытка восстановления доступа

![Попытка сброса пароля root](Screenshot_9.png){ #fig:009 width=70% }

# Итоги работы

## Вывод

В ходе лабораторной работы были изучены принципы настройки загрузчика **GRUB2**, методы устранения ошибок загрузки и процедуры восстановления системы, включая сброс пароля пользователя root.
