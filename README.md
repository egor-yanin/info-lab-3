# Отчёт по лабораторной работe 3

Для выполнения задания я использовал уже установленный VirtualBox, одну машину с дистрибутивом Ubuntu и две ммашины Ubuntu Server.

В первой машине я обеспечил доступ в сеть Интернет с помощью адаптера NAT. 
![](https://i.ibb.co/PrT2yRs/ping-google.png)  
Затем я настроил второй адаптер у машин А и Б на внутренню сеть с названием "AB".
![](https://i.ibb.co/CB4MYWf/adapter.jpg)!  
В терминале машины А я вывел список сетевых интерфейсов с помощью команды ifconfig -a.
![](https://i.ibb.co/zJw3PLg/ifconfig-A.png)  
enp0s3 - первый адаптер с доступом в Интернет.  
enp0s8 - сеть AB.  
eno0s9 - сеть AC.  
Далее я настроил интерфейсы и ip-адреса  
```bash
sudo ifconfig enp0s8 192.168.1.10 network 255.255.248.0 up
sudo ifconfig enp0s9 192.168.2.10 network 255.255.248.0 up
```
Аналогично в машине Б:
```bash
sudo ifconfig enp0s8 192.168.1.1 network 255.255.248.0 up
```
Теперь в сети "AB" машина А имеет ip-адрес 192.168.1.10, машина Б - 192.168.1.1.  
Проверим наличие сетевого доступа из машины А в Б:
![](https://i.ibb.co/W6Rzt8K/ping-A-B.png)  

Аналогично настроим машину В. Проверим наличие доступпа из А в В:
![](https://i.ibb.co/yBDfD38/ping-A-C.png)  

Проверим доступ из Б в В:  
![](https://i.ibb.co/72R7NLt/no-access.jpg)  
Очевидно, что доступ отсутствует, так как машины находятся в разных сетях.
