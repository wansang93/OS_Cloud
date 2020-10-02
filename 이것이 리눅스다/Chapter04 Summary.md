## Chapter04 Summary

### 04-01 Start & Exit, Virtual Console, Runlevel, Autocomplete & History

1. Start, Exit
   - ```shutdown -P now```, ```init0```
   - ```shutdown -r +5```, ```init6```
   - ```shutdown -k +3```

2. Virtual Console
   - ```Ctrl```+ ```Alt``` + ```F2``` ~ ```F6```

3. Runlevel
   - 0 Power off, 1 Rescue, 2~4 Multi-User, 5 Graphic User, 6 Reboot
   - ```ls -l /lib/systemd/system/runlevel?.target```: It shows runlevel

4. Autocomplete & History
   - ```Tab```, ```Arrow keys```, ```history```

### 04-02 Gedit, Using Vi Editor

1. Text Editor
   - ```gedit <file_name>```: open text editor

2. Vi Editor
   - ```:set number```: show line numbers

### 04-03 Help, Mount

1. ```man <command>```: get a detailed manual of a command

2. Mount
   1. ```cd /media/```: go to media
   2. ```mkdir <directory_name>```: make directory
   3. ```mount /dev/cdrom```: mount
   4. ```unmount /dev/cdrom```: unmount

### 04-04 Basic Linux Command

link -> [https://www.hostinger.com/tutorials/linux-commands](https://www.hostinger.com/tutorials/linux-commands)  
mylink -> [Chapter04-04](Chapter04-04.md)

- path
  - ```clear```: clear console lines
  - ```pwd```: print working directory
  - ```cd <directory_name>```: change directory
  - ```ls <directory_name>```: list show
    - ```-a```: show hidden list
    - ```-l```: long list

- directory
  - ```mkdir <directory_name>```: make
  - ```rmdir <directory_name>```: remove
    - ```-r```: remove all files in directory
    - ```-f```: force, do not ask

- file
  - ```touch <file_name>```: create a empty file
  - ```cp <file_name> <rename> <destination>```: copy
  - ```mv <file_name> <destination>```: move
  - ```rm <file_name>```: remove
  - ```file <file_name>```: show file extension

- text info
  - ```cat <file_name>```: print file's text, concatenate
  - ```head -5 <file_name>```: print the top 5 of data
  - ```tail -3 <file_name>```: print the end 3 of data
  - ```more <file_name>```: display one screen at a time in case the file is large
  - ```less <file_name>```: display one screen per time(it don’t access complete file, but access it page by page)

### 04-05 User & Group

- ```vi /etc/passwd```: show accounts information
  - user_name : hashed password : user_id : group : full_name : home_diretory : base_shell
- ```vi /etc/shadow```: show password and account expiration information
  - group_name : hashed password : group_id : users_in_group

- user command
  - ```useradd <user_name>```: create user
  - ```passwd <user_name>```: change user password
  - ```userdel -r <user_name>```: delete user
  - ```usermod <option> <user_name>```: modify user by option

- group command
  - ```groups```: show now user's group
  - ```groupadd <group_name>```: create group
  - ```groupdel <group_name>```: delete group

### 04-06 Permissions & Owners, Link 

- set permissions
  - ```chmod <option> <file_name>```
    - ```ugo+x```: user, group, other + execute
    - ```ugo-rw```: user, group, other - read, write
    - ```753```: -rwxr-x-wx(-, 421, 401, 021)

- set owner, group
  - ```chown <user_name> <file_name>```: change user
  - ```chgrp <group_name> <file_name>```: change group

- link
  - ```ln <file_name> <link_file_name>```: create hardlink
  - ```ln -s <file_name> <link_file_name>```: create softlink

### 04-07 RPM for installing package



### 04-08 DNF for easy installing package