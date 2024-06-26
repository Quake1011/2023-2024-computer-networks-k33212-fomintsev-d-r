## Лабораторная работа № 3.  
## Установка коммутаторов уровня агрегации/распределения и уровня ядра. Установка и настройка модуля DHCP корпоративной сети.  

## Оглавление:
- [Цель работы](#section1)
- [Краткие теоретические сведения](#section1.2)
- [Требования](#section1.3)
- [Описание задач](#section1.4)
- [Ход работы](#section1.5)
  - [Часть 1. Установка коммутаторов уровня агрегации и ядра.](#section2)
  - [Часть 2. Установка и настройка модуля DHCP корпоративной сети](#section2.1)
- [Вывод](#section3) 

## <a name="section1">Цель работы</a>   

Установка коммутаторов уровня агрегации/распределения и уровня ядра в корпоративную сеть. Настройка коммутаторов уровня агрегации/распределения и уровня ядра. Установка и настройка модуля DHCP корпоративной сети.
## <a name="section1.3">Требования</a> 
для выполнения работы необходима установленная среда моделирования Cisco Packet Tracer. 


## <a name="section1.2">Краткие теоретические сведения</a>
DHCP — протокол автоматизации назначения IP-адреса клиенту. Он широко используется в современных сетях. В статье рассмотрим принципы работы, процесс DORA, основные опции и другие аспекты протокола.
DHCP — протокол прикладного уровня модели TCP/IP, служит для назначения IP-адреса клиенту. Это следует из его названия — Dynamic Host Configuration Protocol. IP-адрес можно назначать вручную каждому клиенту, то есть компьютеру в локальной сети. Но в больших сетях это очень трудозатратно, к тому же, чем больше локальная сеть, тем выше возрастает вероятность ошибки при настройке. Поэтому для автоматизации назначения IP был создан протокол DHCP.
Впервые протокол был описан в 1993 году в документе RFC 1531, но с тех пор в описание вносились правки. На сегодняшний день основным документом, регламентирующим протокол, является RFC 2131. Помимо автоматизации процесса настройки IP, DHCP позволяет упростить диагностику подключения и переход из одной подсети в другую, оставляя уведомления для системного администратора в логах.


## <a name="section1.4">Описание задачи</a>  
Некой организации требуется объединить в единую сеть оборудование (компьютеры, принтеры, Web камеры, IP телефоны, wifi точки доступа), установленное в нескольких помещениях нескольких зданиях. Нужно определить тип используемых проводов, расположить розетки, проложить провода, выбрать место для серверной, выбрать места для установки Wi-Fi точек, подвести провода в патч-панель стойки для серверной. 
После того, как организация выполнила данную процедуру, необходимо выполнить подключение данных устройств к коммутаторам 2-го уровня – коммутаторам уровня доступа. 
Устройства уровня доступа это, как правило, коммутаторы второго уровня (L2) модели OSI, т.е. без функции маршрутизации. Коммутаторы осуществляют первичное сегментирование сети (технология VLAN).
После того, как организация выполнила данную процедуру необходимо выполнить подключение данных устройств к коммутаторам 3-го уровня – коммутаторам уровня агрегации и ядра.
Поскольку лабораторные работы моделируют небольшую сеть, но добавлять все устройства необходимо, то для выполнения этой работы будем считать, что один коммутатор уровня ядра будет стоять в наиболее отстоящем здании от других, а другой коммутатор уровня ядра будет объединять два других здания. Т. е. будет 2 коммутатора уровня ядра и 3 коммутатора уровня распределения (по одному коммутатору уровня распределения в каждом здании).
К коммутатору уровня распределения будет подключен модуль DHCP корпоративной сети. Модуль будет состоять из DHCP сервера ( и маршрутизатора, при необходимости), который будет адресовать запросы к этому серверу. 
Сети разграничиваются VLAN, которые были определены в предыдущей лабораторной работе. Адреса для сетей выбрать самостоятельно. 

## <a name="section1.5">Ход работы</a>

## <a name="section2">Часть 1</a>

Были добавлены 2 коммутатора L3 уровня ядра и 3 коммутатора L3 уровня распределения

<p align=center><img src="https://github.com/DeFomin/2023-2024-computer-networks-k33212-fomintsev-d-r/assets/90705279/40d30763-7d6a-4d66-abea-dc6af1f86e27" width="700"></p>

<p align=center><img src="https://github.com/DeFomin/2023-2024-computer-networks-k33212-fomintsev-d-r/assets/90705279/954582e6-a0d8-4bf6-93f6-88ebb25a349c" width="700"></p>


## <a name="section2.1">Часть 2</a>

Итоговая схема сети

<p align=center><img src="https://github.com/DeFomin/2023-2024-computer-networks-k33212-fomintsev-d-r/assets/90705279/6ae4ac2c-b2ea-4cab-9aa4-551eea7b2d4a" width="700"></p>

Настройка существующих vlan

<p align=center><img src="https://github.com/DeFomin/2023-2024-computer-networks-k33212-fomintsev-d-r/assets/90705279/5ae2c497-3400-45c0-8ffc-64845640d45e" width="700"></p>

Настройка статического адреса сервера

<p align=center><img src="https://github.com/DeFomin/2023-2024-computer-networks-k33212-fomintsev-d-r/assets/90705279/582735e6-75df-4b55-9340-d0d2885954a6" width="700"></p>


Для каждого VLAN, в коммутатор L3 была добавлена информация о всех существующих VLAN. 
```
interface vlan N
ip address 10.N.0.254 255.255.255.0
ip helper-address 10.70.0.1
```

После этого для порта, в который подключен другой коммутатор включаем инкапсуляцию и включаем транк мод:  
```
interface FastEthernet0/n
switchport trunk encapsulation dot1q
switchport mode trunk
```

Настройка порта, в который подключен DHCP сервер. Поскольку сервер находится в VLAN 70:  
```
interface FastEthernet0/n
switchport access vlan 70
```
<p align=center><img src="https://github.com/DeFomin/2023-2024-computer-networks-k33212-fomintsev-d-r/assets/90705279/d92ee7ff-c0c1-43e5-8e93-acc7f7d259b1" width="700"></p>

Проверка выдачи ip адресов dhcp сервером

<p align=center><img src="https://github.com/DeFomin/2023-2024-computer-networks-k33212-fomintsev-d-r/assets/90705279/3bb15f72-7b85-4473-bd66-69a55b80bc0f" width="700"></p>

Для ip телефонов:
```switchport voice vlan N```

## <a name="section3">Вывод</a>

В ходе выполнения лабораторной работы были установлены коммутаторы уровня агрегации/распределения и уровня ядра, а также была произведена установка и настройка модуля DHCP корпоративной сети.

