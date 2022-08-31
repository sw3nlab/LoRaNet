# LoRaNet
LoRa point to point network
Организация сети (точка - точка) на радиомодулях LoRa ebyte e32  

1) Конфигурируем модули дефолтной утилитой ebyte, выставляем на одинаковые параметры, (канал,мощность,скорость и т.д)
 
на максимальной мощности при слабом питании от usb ttl адаптера будут проблемы! для работы модуля в режиме 1Ватт нужен внешний источник питания типа li-ion 18650 аккумулятор.

2) Переводим модули в режим радиовещания 
3) Припаиваем к LoRa модулям USB ttl UART конвертеры, подключаем к компуктерам
4) Переходим к настройке сети на gnu/linux машинах


```php
sudo slattach -d -p slip -s 19200 /dev/ttyUSB0
sudo ifconfig sl0 192.168.5.2 pointopoint 192.168.5.1 up
```

где `/dev/ttyUSB0` -> usb ttl адаптер с припаеной лорой

5) Тестируем соединение | check connection

```php
ping 192.168.5.1 
```

скорость соединения оставляет желать лучшего, хватает для администрирования удалённой Raspberry pi по telnet и
редактирования конфигов 

максимальная дальность связи в режиме 20db на открытой местности составила порядка 3км
