---
marp: true
---

# Лекция 8: 

---

## SNMA
**SNMA** - мультикастовый адресс следующего вида : **ff02:1:ff00:** после чего идут 24 бита IPV6 адреса. Таким образом:
> `PC1: ipv6: a::1, SNMA: ff02:1:ff00::1`
> `PC2: ipv6: a::2, SNMA: ff02:1:ff00::2`
## MLD
**MLD** - Multicast listening discovery. Используется для 

---## Пример взаимодействия:
>a::1 (l-l) :arrowr_right: NS :arrowr_right: ff02:1:ff00::2
a::2 (l-l) :arrowr_right: NA :arrowr_right: a::1 (l-l)

**DAD** - Duplicate address detection

---

## PPP CHAP
**CHAP** использует 3-way handshake со следующим принципом:
R1 и R2 имеют некоторые изначальные числа `secret`
> `R1` генерирует `chalenge` :arrow_right:  `R2`
> `R2` считает свой секрет по приципу `hash(chalenge + secret)` :arrow_right: `R1`

---

## Конфигурация CHAP
> `(config)#username R2 password cisco` **AND** `(config)#username R1 password cisco` - команды должны быть применены на обоих роутерах, для создания пользователей ***имя которых - hostname другого***
 
**IP unnumbered** - функция безопасности, которая позволяет в PPP каналах создать временный IP
> `(config-if)#ip unnumbered ethernet 0/0`

---
<!-- _footer: \\* Создание записи типа AAAA аналогично-->
## DHCP классы

> `(config-dhcp-pool)#class CLASS1` - создание класса
> `(config-dhcp-class)#network ` - указание диапазона адрессов 

**DHCP option 82** - резервация адреса по номеру комутатора и порта
## Настройка DNS сервера
>`(config)#ip dns` - включение DNS сервера
>`(config)#ip host ya.ru 9.9.9.9` - создание записи типа A*