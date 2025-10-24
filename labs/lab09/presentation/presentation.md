---
## Front matter
lang: ru-RU
title: Лабораторная работа №9
subtitle: Управление SELinux
author:
  - Ришард Когенгар
institute:
  - Российский университет дружбы народов, Москва, Россия
date: 14 октября 2025

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

Получить навыки работы с контекстом безопасности и политиками SELinux.

# Ход выполнения работы

## Проверка статуса SELinux

![Просмотр статуса SELinux](Screenshot_1.png){ #fig:001 width=70% }

## Проверка статуса SELinux

![Изменение режима работы SELinux](Screenshot_2.png){ #fig:002 width=70% }

## Отключение и повторное включение SELinux

![Отключение SELinux в конфигурационном файле](Screenshot_3.png){ #fig:003 width=70% }

## Отключение и повторное включение SELinux

![SELinux отключён](Screenshot_4.png){ #fig:004 width=70% }

## Отключение и повторное включение SELinux

![Система работает в режиме enforcing](Screenshot_5.png){ #fig:005 width=70% }

## Восстановление контекста безопасности

![Восстановление контекста безопасности и подготовка к перемаркировке](Screenshot_6.png){ #fig:006 width=70% }

## Настройка контекста для веб-сервера

![Создание каталога и файла для веб-сервера](Screenshot_7.png){ #fig:007 width=70% }

## Настройка контекста для веб-сервера

![Изменение DocumentRoot и настроек доступа](Screenshot_8.png){ #fig:008 width=70% }

## Настройка контекста для веб-сервера

![Тестовая страница веб-сервера по умолчанию](Screenshot_9.png){ #fig:009 width=70% }

## Применение контекста httpd_sys_content_t

![Назначение контекста безопасности и перезапуск службы](Screenshot_10.png){ #fig:010 width=70% }

## Применение контекста httpd_sys_content_t

![Отображение пользовательской страницы веб-сервера](Screenshot_11.png){ #fig:011 width=70% }

## Работа с переключателями SELinux

![Работа с переключателями SELinux для FTP](Screenshot_12.png){ #fig:012 width=70% }

# Итоги работы

## Вывод

В ходе работы были изучены принципы управления политиками безопасности SELinux, настройка контекстов доступа и использование переключателей для системных служб.
