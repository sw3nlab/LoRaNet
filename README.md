# LoRaNet
LoRa point to point network

Организация сети (точка - точка) на радиомодулях **LoRa**

# Linux

В данном примере используется 2 модуля LoRa (433MHz)

Один подключен к нетбуку (Debian GNU/Linux)

![image](https://raw.githubusercontent.com/sw3nlab/LoRaNet/main/img.jpg)


второй к Raspberry Pi (Raspbian)
посредствам радиомодулей поднимается сеть (точка-точка) между нетбуком и малиной.

Пример соединения:
https://youtu.be/z7isqsBQ3kc


***Настройка***

**1)** Конфигурируем модули дефолтной утилитой ebyte (https://www.ebyte.com/en/data-download.html?id=199&pid=196#load), выставляем одинаковые параметры, (канал,мощность,скорость и т.д)
 
 ![image](https://raw.githubusercontent.com/sw3nlab/LoRaNet/main/7675431560100293369-1.jpg)

**2)** Переводим модули в режим радиовещания 

**3)** Переходим к настройке сети на GNU/Linux машинах


```php
sudo apt-get update
sudo apt-get install net-tools
sudo slattach -d -p slip -s 19200 /dev/ttyUSBX
sudo ifconfig sl0 192.168.5.2 pointopoint 192.168.5.1 up
```

где `/dev/ttyUSBX` -> ваш LoRaNet модуль

на модуле который подключен к Raspberry Pi, делаем тоже самое только, меняем местами `192.168.5.2` и `192.168.5.1`

**4)** Тестируем соединение 

```php
ping 192.168.5.1 
```

**5)** Если необходимо, чтобы интерфейс поднимался сразу после подачи питания, добавляем конфиг в `/etc/network/interfaces`на Raspberry Pi

```php
auto sl0
 iface sl0 inet static
 address 192.168.5.1
 netmask 255.255.255.255
 pointopoint 192.168.5.2
 pre-up /sbin/slattach -p slip -s 19200 /dev/ttyUSB0 &
 post-up /sbin/ip route add 1.1.1.1 dev sl0
 #post-down /usr/bin/killall slattach
```

**7)** поднимаем на Raspberry `telnet` и подключаемся 

`telnet 192.168.5.1`

>скорости соединения хватает для администрирования удалённой Raspberry pi по `telnet` и
редактирования конфигов. 
Максимальная дальность связи в режиме 20db на открытой местности составила порядка 3км


# Windows 

>Для передачи файлов HyperTerminal и протокол Kermit



# Android

> USB Serial Terminal тестируется передача файлов...

**Вы можете самостоятельно собрать аналогичные радиомодемы или заказать готовые наборы с антеннами у нас по почте:**

sw3n32@gmail.com

**Обсуждения/Вопросы/Предложения:**

https://discord.com/invite/vcUt6kP
