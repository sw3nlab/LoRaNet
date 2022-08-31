# LoRaNet
LoRa point to point network
Организация сети (точка - точка) на радиомодулях LoRa ebyte e32  

1) Конфигурируем модули дефолтной утилитой         | Confugure Lora e32 modules 
2) Переводим модуль в режим радиовещания           | Change to UART -> RF
3) Припаиваем к LoRa модулю USB ttl UART конвертер | Add UART TTL USB module 
4) Переходим к настройке сети на gnu/linux машине  | Confugure Point to Poing network on GNU/Linux station 


```php
sudo slattach -d -p slip -s 19200 /dev/ttyUSB0
sudo ifconfig sl0 192.168.5.2 pointopoint 192.168.5.1 up
```

5) Тестируем соединение | check connection

```php
ping 192.168.5.1 
```
