---
marp: true
---

**EVE-NG** - Профессиональное ПО для эмуляции, являющееся форком Unitlab. Распространяется с https://eve-ng.net.
**CML / VIRL** - Профессиональное ПО для эмуляции от Cisco.

Текущая стабильная версия EVE-NG - 5.01-13 (2/21/23)
Не ресурсотребуемый билд: 2.0.0

Документация: https://www.eve-ng.net/index.php/documentation/howtos/

pnetlab - китайский форк Unitlab, полностью бесплатный: https://pnetlab.com/pages/main

Windows Client Sidepack (WCS) - дополнительный пакет для работы утилит Windows в EVE-NG

---
## Развёртывание EVE-NG
> 1. Развернуть EVENG_VM в VMware.
> 2. EVE-NG должна построить сетевой мост с устройством и получить адресс по DHCP.
>   - В случае если построить сетевой мост не удалось, необходимо использовать основной адаптер.
> 3. Для добавления образов:
>   - Подключиться по SFTP используя адрес EVE-NG.
>   - В папке \Opt\Unitlab\Addons\ добавить в содержащиеся папки соответствующие образы.
>   - Доставить образы в исходном виде.
>   - Изменить права если необходимо. 
Новый роутер: **CSR**

---
<!-- _footer: \\*Пароль: eve -->
Учётные записи*:
>   **root** - для работы с файлами
>   **admin** - для работы с топологией

Для работы необходимо использовать веб-интерфейс.
Соединять можно только выключенные устройства.