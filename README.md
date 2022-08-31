# LoRaNet
LoRa point to point network


1) Confugure Lora e32 modules 
2) Change to UART -> RF
3) Add UART TTL USB module 
4) Confugure Point to Poing network 


```php
sudo slattach -d -p slip -s 19200 /dev/ttyUSB0
sudo ifconfig sl0 192.168.5.2 pointopoint 192.168.5.1 up
```

5) check connection

```php
ping 192.168.5.1 
```
