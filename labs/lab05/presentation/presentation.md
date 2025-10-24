---
## Front matter
lang: ru-RU
title: Лабораторная работа №5
subtitle: Управление системными службами
author:
  - Ришард Когенгар
institute:
  - Российский университет дружбы народов, Москва, Россия
date: 21 сентября 2025

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

Получить навыки управления системными службами операционной системы посредством systemd.

# Ход выполнения работы

## Управление сервисом vsftpd

![Проверка статуса vsftpd до установки](Screenshot_1.png){ #fig:001 width=70% }

## Управление сервисом vsftpd

![Запуск службы vsftpd](Screenshot_2.png){ #fig:002 width=70% }

## Управление сервисом vsftpd

![Добавление в автозапуск](Screenshot_3.png){ #fig:003 width=70% }

## Управление сервисом vsftpd

![Отключение автозапуска](Screenshot_4.png){ #fig:004 width=70% }

## Управление сервисом vsftpd

![Статус службы после включения автозапуска](Screenshot_5.png){ #fig:005 width=70% }

## Управление сервисом vsftpd

![Обратные зависимости vsftpd](Screenshot_6.png){ #fig:006 width=70% }

## Конфликты юнитов: iptables и firewalld

![Установка iptables](Screenshot_7.png){ #fig:007 width=70% }

## Конфликты юнитов: iptables и firewalld

![Проверка статуса firewalld и iptables](Screenshot_8.png){ #fig:008 width=70% }

## Конфликты юнитов: iptables и firewalld

![Попытка запуска iptables и firewalld](Screenshot_9.png){ #fig:009 width=70% }

## Конфликты юнитов: iptables и firewalld

![Файл юнита iptables](Screenshot_10.png){ #fig:010 width=70% }

## Конфликты юнитов: iptables и firewalld

![Ошибка запуска замаскированного сервиса](Screenshot_11.png){ #fig:011 width=70% }

## Изолируемые цели

![Список изолируемых целей](Screenshot_12.png){ #fig:012 width=70% }

## Изолируемые цели

![Изоляция цели reboot.target](Screenshot_13.png){ #fig:013 width=70% }

## Цель по умолчанию

![Проверка цели по умолчанию](Screenshot_14.png){ #fig:014 width=70% }

## Цель по умолчанию

![Установка graphical.target как цели по умолчанию](Screenshot_15.png){ #fig:015 width=70% }

# Итоги работы

## Вывод

В ходе работы были изучены основы управления сервисами в системе systemd, их установка, запуск, автозагрузка и удаление. Рассмотрены конфликты между юнитами, способы их разрешения, изолируемые цели и настройка цели по умолчанию.
