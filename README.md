# LoRaNet
LoRa point to point network


1) Confugure Lora modules 
2) Change to UART -> RF
3) Confugure Point to Poing network 


```php
sudo slattach -d -p slip -s 19200 /dev/ttyUSB0
sudo ifconfig sl0 192.168.5.2 pointopoint 192.168.5.1 up
```
