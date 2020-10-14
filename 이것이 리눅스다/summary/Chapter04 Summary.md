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

- Path
  - ```clear```: clear console lines
  - ```pwd```: print working directory
  - ```cd <directory_name>```: change directory
  - ```ls <directory_name>```: list show
    - ```-a```: show hidden list
    - ```-l```: long list

- Directory
  - ```mkdir <directory_name>```: make
  - ```rmdir <directory_name>```: remove
    - ```-r```: remove all files in directory
    - ```-f```: force, do not ask

- File
  - ```touch <file_name>```: create a empty file
  - ```cp <file_name> <rename> <destination>```: copy
  - ```mv <file_name> <destination>```: move
  - ```rm <file_name>```: remove
  - ```file <file_name>```: show file extension

- Text info
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

- User command
  - ```useradd <user_name>```: create user
  - ```passwd <user_name>```: change user password
  - ```userdel -r <user_name>```: delete user
  - ```usermod <option> <user_name>```: modify user by option

- Group command
  - ```groups```: show now user's group
  - ```groupadd <group_name>```: create group
  - ```groupdel <group_name>```: delete group

- When you edit ```/etc/skel```, those files will be copied to new user by default

### 04-06 Permissions & Owners, Link 

- Set permissions
  - ```chmod <option> <file_name>```
    - ```ugo+x```: user, group, other + execute
    - ```ugo-rw```: user, group, other - read, write
    - ```753```: -rwxr-x-wx(-, 421, 401, 021)

- Set owner, group
  - ```chown <user_name> <file_name>```: change user
  - ```chgrp <group_name> <file_name>```: change group

- Link
  - ```ln <file_name> <link_file_name>```: create hardlink
  - ```ln -s <file_name> <link_file_name>```: create softlink

### 04-07 RPM for installing package

- ```rpm -Uvh <rpm_file>.rpm```: Install RPM(Upgrade and view)
- ```rpm -ev <package>```: Erase(remove) RPM
- ```rpm -qa```: Display RPM packages

### 04-08 DNF for easy installing package

- ```dnf -y install <package_name>```: Install package(-y is option)
- ```dnf remove <package_name>```: Remove package

### 04-09 Zip, Tar and Find files

- Zip files
  - ```xz <file_name>```: Zip a file
  - ```xz -d <file_name>.xz```: Unzip a file
- Tar(Tape Archive) files
  - ```tar -<c|x|t>f  <tar_name>.tar <file1> <file2>```
    - Compress/Extract/List_content a file
    - ```f```: File, Default option
    - ```v```: View process
    - ```J```: tar+xz
    - ```z```: tar+gzip
    - ```j```: tar+bzip2

### 04-10 System Settings, CRON and AT

- System Settings
  - ```nmtui```: network setting
  - ```firewall-config```: firewall setting
  - ```ntsysv```: service setting
- CRON
  - ```systemctl start crond```: Start crond
  - ```systemctl restart crond```: Restart crond
  - ```systemctl status crond```: Check crond activate
  - ```vi /etc/crontab```: Setting CRON
  - ```cd etc/cron.<monthly|weekly|daily|hourly>```: Go to cron.\<period\> then make scripts you want to do
- AT
  - ```at <time>```: set at command
  - ```at -l```: list at command
  - ```atrm <number>```: remove at command

### 04-11 Network Essential Concepts and Related Files

- ```nmtui```: Setting Network
- ```systemctl <start|stop|restart|status> NetworkManager```: Apply changes to network setting
- ```ifup <device_name>```, ```ifdown <device_name>```: Turn on/off device_name
- ```ifconfig <device_name>```: Show ip info
- ```nslookup```: Test DNS Server
- ```ping <ip_address|URL>```: Receive response from ip_address or URL

### 04-12 Practice nmtui Command and SELinux Concept

- ```/etc/sysconfig/network```: A File with network default information set
- ```/etc/sysconfig/network-scripts/ifcfg-ens160```: A file containing all network information set up on the enc32 device
- ```/etc/resolv.conf```: A file containing the DNS server's information and host name
- ```/etc/hosts```: A file containing the host name and FQDN

### 04-13 Pipe Filter Redirection, Processes, Services and Sockets

- Pipe(|)
  - ex) ```ls -l /etc``` **```|```** ```more```
- Filter(grep, tail, wc, sort, awk, sed, etc...)
  - ex) ```ps -ef |``` **```grep```** ```<process_name>```
- Redirection(>, >>, <, <<)
  - ex) ```ls -l``` **```>```** ```list.txt```

- process
  - ```ps ```: Check process status
  - ```kill -9 <process_number>```: Force End Process
  - ```pstree ```: Show process as tree

- Service and Socket
  - See location of service or socket script file: ```ls /usr/lib/systemd/system/```
  - start, stop, restart service or socket: ```systemctl <start|stop|restart> <service_name|socket_name>```

### 04-14 Emergency Recovery, GRUB Bootloader

- Emergency Recovery
  1. Press ```e```
  2. Delete ```rhgb quiet```, Write there ```init=/bin/sh``` then ```Ctrl``` + ```x```
  3. Write ```mount -o remount, rw  /```
  4. Write ```passwd```, then write new password
  5. Restart

- Change grub password
  1. vi /etc/default/grub
  2. grup2-mkconfig -o /boot/grub2/grub.cfg
  3. cd /etc/grub.d/
  4. vi 00_header then add bottom below
     ```
     cat << E0F
     set  superuser="thisislinux"
     password thisislinux 4321
     E0F
     ```
  6. grup2-mkconfig -o /boot/grub2/grub.cfg
  7. reboot

### 04-15 Compile Kernel

``` bash
# 1. 현재 커널 버전 확인
uname -r  # 현재 커널 보기(4.18.0)
# 커널은 c나 asembly로 짜여있음

# 2. 커널 소스 다운로드
# [linux-5.3.11.tar.xz](https://mirrors.edge.kernel.org/pub/linux/kernel/v5.x/linux-5.3.11.tar.xz)
# 다운로드 후

# 3. 커널 소스 압축 풀기
cd 다운로드/
mv linux-5.3.11.tar.xz /usr/src/
cd /usr/src
ls
tar Jxvf linux-5.3.11.tar.xz
ls -l
cd linux-5.3.11/
pwd
ls  # 리눅스 파일들 보기, 대부분 c언어로 작성 되어있음

# 4. c언어 컴파일 환경 설정하기
dnf -y install make bison flex elfutils-libelf-devel openssl-devel

# 5. 커널 설정 초기화
make mrproper  # 커널 설정 초기화

# 6. 커널 환경 설정
make xconfig
# 커널 환경 설정 후 저장
ls -a  # .config 디렉토리 찾기
vi .config  # .config 열어서 수정
    /CONFIG_SYSTEM_TRUSTED  # CONFIG_SYSTEM_TRUSTED 찾기
    # 아래 두줄 # 처리하기
    :wq
make clean  # 이전 정보 삭제

# 7. 커널 컴파일 및 설치(시간이 정말 오래 걸리니 오타를 조심)
make; make modules_install; make install

# 8. 설치 완료 후 확인
ls -l /lib/modules
reboot
# 추가된 것을 보고 접속 후 터미널로 들어가서 버전확인
uname -r
```