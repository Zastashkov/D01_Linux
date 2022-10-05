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