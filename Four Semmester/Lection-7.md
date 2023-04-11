---
marp: true
---

# Лекция: ICMPv6

---

## ICMPv6
> - Использует 58 вложение
> - Использует заголовок ICMPv4
> - Реализует функции ICMPv4, часть функций DHCP и часть ARP

**NDP** - Network discovery protocol - подсущность ICMPv6
> - RS/RA - Router solicitation / advertisement 133/134 вложение
> - NS/NA - 136/136 Neighbor solicitation / Network advertisement вложение

---

После включения PC он отправляет запрос со случайным адресом на мультикастовый адрес ff02::2, после получения запроса роутер отвечает со своим LLA адресом на мультикастовый адрес ff02::1.
Процедура получения адреса таким образом называется SLAAC. SLAAC использует свой LLA в качестве шлюза по умолчанию.x

---
PC отсылает сообщение, если он отправляет LLA, то такое поведение является DAD - Dublicate Address Detection. Отправка проискходит на адрес SNMA - Solicited-node multicast address

SNMA группа - мультикастовая группа содержащая информацию о конкретном хосте, номер группы SNMA определяется по концу IPv6 адреса. Это позволяет избавиться от ARP. 

---
## DHCPv6

> - Не использует BOOTP вложение
> - Использует мультикаст ff02::1:2
> - Использует UDP порты 546/547
> - Имеет два состояния:
>   - Statlees использует SLAAC + DHCPv6
>   - Statefull использует только DHCPv6
> - Процедура получения представляяет SARR - Solicit, Advertise, Request, Reply 
> - Имеет Rapid mode, в котром процедура получения адреса состоит SR - Solicit, Reply

---

Определение состояния DHCPv6 определяется флагами O и M:
При значении 00 - передача будет только по SLAAC,
При значении 01 - передача будет по SLAAC + DHCPv6
При значении 10 - передача будет только по DHCPv6

---

> `(config-if)#ipv6 dhcp server LESS` - указывает интерфейс сервером
> `(config-if)#ipv6 nd config-flag` - устанавливает флаг O в 1
> `(config-dhcp)#address prefix 2002:abcd:cafe:beef::/64` - конфигурация префикса раздачи dhcp
> `(config-id)#ipv6 nd prefix 2002:abcd:cafe:beef::/64 no advertise` - отключение SLAAC на интерфейсе

<!--не найден способ ipv6 excl на образах и резервирование-->