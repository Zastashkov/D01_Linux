## Part 1. Installation of the OS
- ![Installation of the OS](./Pictures/Part_1_.Installation_of_the_OS.png)
- Вывод версии Ubuntu через команду 
`cat /etc/issue`

## Part 2. Creating a user
- ![Creating a user](./Pictures/Part_2_.Creating_a_user_1_useradd.png)
- Создание пользователя через команду 
`sudo useradd -g users username`

- ![Creating a user](./Pictures/Part_2_.Creating_a_user_2_cat.png)
- Вывод команды `cat /etc/passwd`

## Part 3. Setting up the OS network
1. _Изменение имени машины_
- ![Machinename](./Pictures/Part_3_.Setting_up_the_OS_network_1_machinename.png)
- Для изменения имени используем команду `hostnamectl set-hostname user-1`
Также можно в текстовом редакторе изменить файл hostname

- ![Machinename](./Pictures/Part_3_.Setting_up_the_OS_network_2_machinename.png)
- Чтобы убедиться, что имя было изменено, используем команду
`cat /etc/hostname`

2. _Временная зона_
- ![Set-timezone](./Pictures/Part_3_.Setting_up_the_OS_network_1_set_timezone.png)
- Для установки временной зоны, соответствующей определенному местоположению,
используем команду `sudo timedatectl set-timezone Europe/Moscow`
- ![Check-timezone](./Pictures/Part_3_.Setting_up_the_OS_network_2_check_timezone.png)
- Чтобы узнать какая временная зона установлена используем команду
`timedatectl`

3. _Сетевые интерфейсы_
- ![Show network interfaces](./Pictures/Part_3_.Setting_up_the_OS_network_3_show_network_interfaces.png)
- Для просмотра сетевых интерфейсов используем команду 
`ip -br a show` (_-br brief_ для вывода в кратком виде)
- _lo (loopback device)_ – локальный виртуальный интерфейс, использующийся для отладки сетевых программ и запуска серверных приложений на локальной машине.

- ![IP from DHCP](./Pictures/Part_3_.Setting_up_the_OS_network_4_ip_from_dhcp.png)
- Чтобы получить IP-адрес текущего устройства от DHCP-сервера используем команду
`sudo dhclient -v interfacename` (в данном случае _enp0s3_)