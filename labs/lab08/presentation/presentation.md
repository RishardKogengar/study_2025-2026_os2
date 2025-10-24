---
## Front matter
lang: ru-RU
title: Лабораторная работа №8
subtitle: Планировщики событий
author:
  - Ришард Когенгар
institute:
  - Российский университет дружбы народов, Москва, Россия
date: 10 октября 2025

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

Получить навыки работы с планировщиками задач **cron** и **at** в операционной системе Linux.

# Ход выполнения работы

## Проверка службы crond

![Проверка состояния службы crond](Screenshot_1.png){ #fig:001 width=70% }

## Настройка расписания cron

![Редактирование crontab для root](Screenshot_2.png){ #fig:002 width=70% }

## Проверка выполнения задания

![Результат выполнения cron-задания](Screenshot_3.png){ #fig:003 width=70% }

## Изменение расписания cron

![Изменение расписания cron](Screenshot_4.png){ #fig:004 width=70% }

## Сценарий eachhour

![Создание сценария eachhour](Screenshot_5.png){ #fig:005 width=70% }

## Файл расписания eachhour в /etc/cron.d

![Файл eachhour в /etc/cron.d](Screenshot_6.png){ #fig:006 width=70% }
## Проверка службы atd

![Проверка службы atd](Screenshot_7.png){ #fig:007 width=70% }

# Заключение

В ходе работы были изучены инструменты планирования задач **cron** и **at**.  
Были освоены принципы создания расписаний, настройки периодичности и автоматизации системных действий.  
Полученные знания позволяют эффективно управлять периодическими и одноразовыми задачами в Linux.
