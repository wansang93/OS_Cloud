## 04-03 필수개념과 명령어-도움말, DVD 마운트, USB 마운트

### 도움말

```man dnf```: dnf의 명령어 기능들을 볼 수 있습니다.

### DVD 마운트

windows 같은 경우 USB나 CD/DVD를 넣었을 때 자동으로 인식하여 드라이브를 할당받지만 linux에서는 수동으로 연결해 주어야 합니다.  
즉 마운트란 특정 디바이스(device)를 사용하기 위해 하드웨어장치와 원하는 디렉토리를 연결하는 작업을 의미합니다.

[실습6] cd 마운트하기, 마운트된 cd로 들어가보기, 언마운트 하기

1. CD를 마운트 해제하려면 ```umount  /dev/cdrom```
2. CD를 넣고 ```monut```를 입력하면 마지막에 ```/dev/sr0```로 시작하는 파일이 추가됩니다.(VMware가 자동으로 마운트를 해버림)
    ![04-03mount](./assets/04-03mount.png)  
    사실 ```/dev/sr0```가 원래 이름이고 ```/dev/cdrom```은 앞에 이름을 이어주는 링크라고 생각하면 됩니다.  
    대부분 리눅스는 ```/dev/cdrom```의 링크가 있기 때문에 CD를 마운트할 때는 이 경로로 기억해두면 좋습니다.
3. CD의 디렉토리로 들어가려면 위 결과의 두번째 빨간창으로 들어가면 됩니다.  
    따라서 ```cd /run/media/root/CentOS-8-BaseOS-x86_64/```으로 들어가면 cd의 경로로 들어갑니다.
4. 작업이 끝난 후에는 반드시 cd를 빠져나와서 umount를 진행 하여야 합니다.
    빠져나오지 않고 umount를 진행할 경우 ```target is busy```라는 메시지가 전달됩니다.

[실습6 결과]

![04-03umount](./assets/04-03umount.png)
   
### USB 마운트

USB가 FAT32로 설정되어 있는지 확인 후 작업, VMware settings에서 USE3.0으로 작업

CD와 동일하게 마운트 내용을 출력하고 해당 경로로 진입하면 끝

**ServerB**(Text모드) 에서 실행해보자

VMware에서 자동으로 마운트하지 않기 때문에 우리가 직접 해주어야 합니다.

관례적으로 ```/media/``` 디렉토리로 마운트을 합니다.

1. ```cd /media/```: 미디어 디렉토리로 들어갑니다.
2. ```mkdir cdrom```, ```mkdir usb```: cdrom, usb 디렉토리를 생성합니다.
3. ```mount  /dev/cdrom  /media/cdrom```: mount 주소를 meida/cdrom으로 바꿉니다.
4. ```cd /media/cdrom/```: 마운트 된 주소로 들어가면 CD를 조작할 수 있습니다.
5. ```cd /``` -> ```umount /dev/cdrom```: 사용이 끝나면 디렉토리를 빠져나오고 umount를 해줍니다.
