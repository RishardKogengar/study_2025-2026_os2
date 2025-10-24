---
## Front matter
lang: ru-RU
title: Лабораторная работа №7
subtitle: Управление журналами событий в системе
author:
  - Ришард Когенгар
institute:
  - Российский университет дружбы народов, Москва, Россия
date: 2 октября 2025

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

Получить навыки работы с журналами мониторинга различных событий в системе Linux.

# Ход выполнения работы

## Мониторинг системных событий

![Мониторинг системных событий](Screenshot_1.png){ #fig:001 width=70% }

## Мониторинг системных событий

![Ошибка авторизации su](Screenshot_2.png){ #fig:002 width=70% }

## Мониторинг системных событий

![Сообщение от logger](Screenshot_3.png){ #fig:003 width=70% }

## Мониторинг системных событий

![Просмотр последних строк secure](Screenshot_4.png){ #fig:004 width=70% }

## Изменение правил rsyslog.conf

![Установка и запуск httpd](Screenshot_5.png){ #fig:005 width=70% }

![Просмотр error_log Apache](Screenshot_6.png){ #fig:006 width=70% }

![Редактирование httpd.conf](Screenshot_7.png){ #fig:007 width=70% }

![Создание правила httpd.conf](Screenshot_8.png){ #fig:008 width=70% }

![Создание debug.conf](Screenshot_9.png){ #fig:009 width=70% }

![Сообщение debug в журнале](Screenshot_10.png){ #fig:010 width=70% }

## Использование journalctl

![Просмотр системного журнала](Screenshot_11.png){ #fig:011 width=70% }

## Использование journalctl

![journalctl без пейджера](Screenshot_12.png){ #fig:012 width=70% }

## Использование journalctl

![journalctl в реальном времени](Screenshot_13.png){ #fig:013 width=70% }

## Использование journalctl

![Фильтрация параметров журнала](Screenshot_14.png){ #fig:014 width=70% }

## Использование journalctl

![События UID=0](Screenshot_15.png){ #fig:015 width=70% }

## Использование journalctl

![Последние 20 строк журнала](Screenshot_16.png){ #fig:016 width=70% }

## Использование journalctl

![Сообщения об ошибках](Screenshot_17.png){ #fig:017 width=70% }

## Использование journalctl

![Журнал с определённой даты](Screenshot_18.png){ #fig:018 width=70% }

## Использование journalctl

![Ошибки со вчерашнего дня](Screenshot_19.png){ #fig:019 width=70% }

## Использование journalctl

![Детализированный вывод verbose](Screenshot_20.png){ #fig:020 width=70% }

## Использование journalctl

![Сообщения sshd.service](Screenshot_21.png){ #fig:021 width=70% }

## Постоянный журнал journald

![Просмотр журнала после перезапуска](Screenshot_21.png){ #fig:022 width=70% }

# Итоги работы

## Вывод

В ходе работы были изучены механизмы регистрации и анализа системных событий в Linux с использованием **rsyslog** и **systemd-journald**. Настроено перенаправление сообщений Apache в системный журнал, организация отдельных логов для ошибок и отладки, а также фильтрация и выборка событий с помощью **journalctl**.  
