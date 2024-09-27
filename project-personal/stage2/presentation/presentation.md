---
## Front matter
lang: ru-RU
title: Второй этап индивидуального проекта
subtitle: Установка DVWA
author:
  - Беличева Д. М.
institute:
  - Российский университет дружбы народов, Москва, Россия

## i18n babel
babel-lang: russian
babel-otherlangs: english

## Formatting pdf
toc: false
toc-title: Содержание
slide_level: 2
aspectratio: 169
section-titles: true
theme: metropolis
header-includes:
 - \metroset{progressbar=frametitle,sectionpage=progressbar,numbering=fraction}
 - '\makeatletter'
 - '\beamer@ignorenonframefalse'
 - '\makeatother'
---

# Информация

## Докладчик

:::::::::::::: {.columns align=center}
::: {.column width="70%"}

  * Озьяс Стев Икнэль Дани
  * студент
  * Российский университет дружбы народов
  * [1032205956@pfur.ru](mailto:1032205956@pfur.ru)
  * <https://dacossti.github.io/ru/>

:::
::: {.column width="25%"}

![](./image/moi.jpg)

:::
::::::::::::::

# Цель работы

Установить и настроить DVWA в гостевую систему к Kali Linux.

# Выполнение лабораторной работы

## Установка DVWA

![Скачивание DVWA: клонирование репозитория](image/1.png){#fig:001 width=70%}

## Настройка DVWA

![Каталог конфигурации](image/2.png){#fig:002 width=60%}

## Настройка DVWA

![Редактирование файла конфигурации](image/3.png){#fig:003 width=70%}

## Настройка базы данных

![Запуск службы mysql](image/4.png){#fig:004 width=70%}

## Настройка базы данных

![Вход в базу данных, создание пользователя](image/5.png){#fig:005 width=70%}

## Настройка сервера Apache

![Переход в нужную директории](image/6.png){#fig:006 width=70%}

## Настройка сервера Apache

![Редактирование файла php.ini](image/7.png){#fig:007 width=70%}

## Настройка сервера Apache

![Запуск службы веб-сервера apache](image/8.png){#fig:008 width=70%}

## Открытие DVWA в веб-браузере

![Запуск приложения DVWA в веб-браузере](image/9.png){#fig:009 width=65%}

## Открытие DVWA в веб-браузере

![Создание базы данных](image/10.png){#fig:010 width=70%}

## Открытие DVWA в веб-браузере

![Вход в систему DVWA](image/11.png){#fig:011 width=50%}

## Открытие DVWA в веб-браузере

![Домашняя страница DVWA](image/12.png){#fig:012 width=70%}

# Выводы

В результате выполнения данного этапа проекта я установил и настроил DVWA в гостевую систему к Kali Linux.

# Список литературы

1. Damn Vulnerable Web Application (DVWA) [Электронный ресурс]. 2024. URL:
https://kali.tools/?p=1820.