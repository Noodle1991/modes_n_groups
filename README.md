Песецкий Станислав - вар.12
===============
### ЛАБОРАТОРНАЯ РАБОТА: Управление пользователями и группами
\
**Цель:**
Ознакомление с понятиеми пользователь, группа. Использование соответсвующего функционала.
\
\
\
**Выполнение:**

1. **Создать пользователя, используя утилиту useradd:**
    - **Команда:**
      ```bash
      sudo useradd -m -s /bin/bash user1
      ```

2. **Удалить пользователя, используя утилиту userdel:**
    - **Команда:**
      ```bash
      sudo userdel -r user1
      ```
3. **Создать группу с использованием утилиты groupadd:**
    - **Команда:**
      ```bash
      sudo groupadd group1
      ```
4. **Сменить группу у пользователя:**
    - **Команда:**
      ```bash
      sudo usermod -g group1 user1
      ```
5. **Удалить пользователя из группы:**
    - **Команда:**
      ```bash
      sudo deluser user1 group1
      ```
6. **Добавить пользователя с правом sudo без пароля:**
    - **Команда:**
      ```bash
      sudo useradd -m -s /bin/bash -G sudo user2
      echo 'user2 ALL=(ALL:ALL) NOPASSWD: ALL' | sudo tee -a /etc/sudoers
      ```
7. **Присвоить права файлам:**
    - **Команда:**
      ```bash
      touch file1 file2
      chmod 644 file1
      chmod 600 file2
      ```
8. **Создать группу developer и настроить совместную работу:**
    - **Команды:**
      ```bash
      sudo groupadd developer
      sudo useradd -m -G developer user3
      sudo useradd -m -G developer user4
      sudo mkdir /shared_directory
      sudo chown :developer /shared_directory
      sudo chmod 2775 /shared_directory
      ```
**Объяснение:**
- **sudo** - выполнение команды с правами суперпользователя.
- **useradd** - утилита для создания нового пользователя.
- **-m** - создание домашнего каталога для пользователя.
- **-s** - shell,  указание оболочки пользователя.
- **userdel -r** - удаление пользователя и его домашнего каталога.
- **groupadd** - утилита для создания новой группы.
- **usermod -g group1** - изменение основной группы пользователя на group1.
- **deluser user1 group1** - удаление пользователя user1 из группы group1.
- **sudo useradd -m -s /bin/bash -G sudo user2** - создание пользователя user2 с правами sudo.
- **echo 'user2 ALL=(ALL:ALL) NOPASSWD: ALL' | sudo tee -a /etc/sudoers** - добавление пользователя user2 в файл sudoers без запроса пароля.
- **touch file1 file2** - создание двух произвольных файлов.
- **chmod 644 file1** - присвоение прав на чтение и запись для владельца и группы, только на чтение для остальных файлу file1.
- **chmod 600 file2** - присвоение прав на чтение и запись только для владельца файла file2.
- **sudo groupadd developer** - создание группы developer.
- **sudo useradd -m -G developer user3** - создание пользователя user3 и добавление его в группу developer.
- **sudo useradd -m -G developer user4** - создание пользователя user4 и добавление его в группу developer.
- **sudo mkdir /shared_directory** - создание директории /shared_directory.
- **sudo chown :developer /shared_directory** - change owner, изменение группы владельца директории на developer.
- **sudo chmod 2775 /shared_directory** - change mod, установка setgid и разрешений для совместной работы в директории /shared_directory.