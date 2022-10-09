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

4. _DHCP_ 
- ![IP from DHCP](./Pictures/Part_3_.Setting_up_the_OS_network_4_ip_from_dhcp.png)
- Чтобы получить IP-адрес текущего устройства от DHCP-сервера используем команду
`sudo dhclient -v interfacename` (в данном случае _enp0s3_)
- DHCP - DynamicHost Configuration Protocol (протокол динамической настройки узла).
- ![Check IP](./Pictures/Part_3_.Setting_up_the_OS_network_5_check_ip.png)
- Проверяем IP командой `ip route`

5. _Внешний, внутренний IP адрес шлюза_ 
- ![External IP gateway](./Pictures/Part_3_.Setting_up_the_OS_network_6_external_ip.png)
- Для проверки внешнего адреса шлюза используем команду 
`wget -qO- eth0.me`
- ![Internal IP gateway](./Pictures/Part_3_.Setting_up_the_OS_network_7_internal_ip.png)
- Для проверки внутреннего адреса шлюза хватит и
`ifconfig`

6. _Статичные настройки ip, gw, dns_ 
- ![Set static ip, gw, dns settings](./Pictures/Part_3_.Setting_up_the_OS_network_8_ip_settings.png)
- Чтобы изменить сетевые настройки (ip, gw, dns), заходим в текстовый файл
`sudo vim /etc/netplan/00-installer-config.yaml`

- ![Set static ip, gw, dns settings VIM](./Pictures/Part_3_.Setting_up_the_OS_network_9_ip_settings_vim.png)
- Отключаем DHCP, добавляем все необходимое

7. _Проверяем настройки_ 
- ![Set static ip, gw, dns settings check](./Pictures/Part_3_.Setting_up_the_OS_network_10_ip_settings_check.png)
- Для сохранения настроек, используем следующую команду:
`sudo netplan apply`. Если в файле конфигурации есть ошибки, вы увидите сообщение об этом. Используя эту команду, `reboot` делать необязательно. 

- ![Set static ip, gw, dns settings check](./Pictures/Part_3_.Setting_up_the_OS_network_11_ip_settings_check_settings.png)
- Проверяем настройки
- ![Set static ip, gw, dns settings check](./Pictures/Part_3_.Setting_up_the_OS_network_12_ip_settings_check_ping.png)
- Используя команду `ping ... -c` проверяем корректность настройки сети. -c нужен для указания количества отсылаемых пакетов.

## Part 4. OS Update
- ![System is updating](./Pictures/Part_4_.OS_Update_1_updating.png)
- После ввода команды `sudo apt update` и подтверждения расходования пространства на диске система начнет обновляться

- ![Updates are checked](./Pictures/Part_4_.OS_Update_2_updates_checked.png)
- Вводим команду `sudo apt update`, видим, что доступных обновлений нет

## Part 5. Using the sudo command
- `sudo` - (substitute user and do) позволяет строго определенным пользователям выполнять указанные команды с административными привилегиями&
- ![sudo](./Pictures/Part_5_.Using_the_sudo_command_1_changing_hostname.png)
- Чтобы выполнить команду от имени другого пользователя ставим флаг -u. `sudo -u elektrab hostnamectl set-hostname newhostname.`