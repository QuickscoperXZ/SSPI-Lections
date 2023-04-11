---
marp: true
---

# Лекция 5: Продвинутая настройка RIP

---
## Таймеры
> **Update** - (30 секунд) время отправки апдейтов
> **Invalid** - (180 секунд) веремя валидности маршрута, после прохождения этого времени он уберается из таблицы маршрутизации но остаётся в базе RIP
> **Flush** - (240 секунд) время жизни апдейта в топологии
> **Holddown** - (180 секунд) таймер, характерный только для устройств Cisco предназначенный для борьбы с петлями маршрутизации.

Holddown - после прошествия Invalid таймера начинается отсчёт Holddown таймера. В течении Holddown роутер остаётся в базе данных RIP и анонсируется с /16 и не принимает такие же маршруты со стороны.

---
## Редистрибьюция 

**Редистрибьюция** - объединение маршрутов из разных источников, вбрасывание внешних, по отношению к какому-либо протоколу, маршрутов
>`(config-router)#reditribute connected metric 5` - редистрибуция маршрутов
>`(config)#ip route 192.168.10.0 255.255.255.0 192.168.0.1 tag 1` - тэггирование маршрутов
>`(config)#route-map MAP1 10` - создание карты фильтров маршрутизации
>`(config-route-map)#match tag` - правило сравнения тэгов.
>`(config-router)#neighbor` - ручная привязка соседа, позволяющая передавать RIP сообщения через unicast

---
## Защита RIP
1. Интерфейс тупиковых сетей назначается пассивным.
2. В транзитных сетях используется аутентификация
> Аутентфикация может быть следующей:
> **Отсутствие** аутентификации
> **Незашифрованным** текстом
> **MD5** хэширование
> *Хэшированные аутенификационные данные передаются в сообщениях. В случае совпадения хэшей происходит добавление в таблицу*
>`(config)#key chain UTMN` - механизм ключевых цепочек
>`(config-keychain)#key 1 key-string cisco`