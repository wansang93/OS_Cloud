## 14-01 NFS 서버-nfs 서버 설치와 운영

### NFS 서버 구현

리눅스 컴퓨터끼리 저장 공간을 공유할 수 있도록 해 주는 시스템 NFS(Network File System)

구현 개요도

![14-01 NFS 서버 구현](./assets/14-01NFS서버구현.png)

### [실습1] NFS 서버 구축

서버 초기화 후 터미널에서

```bash
$ rpm -qa nfs-utils
$ vi /etc/exports
> /share      192.168.111.*(rw,sync)
> :wq
$ mkdir /share
$ chmod 707 /share/  # 일반 사용자 사용 가능
$ systemctl restart nfs-server
$ systemctl enable nfs-server
$ exportfs -v  # 공유 폴더들 목록 보기
$ systemctl stop firewalld
```

리눅스 클라이언트의 터미널에서

```bash
$ rpm -qa nfs-utils
$ showmount -e 192.168.111.100
$ pwd
$ mkdir myShare
$ su -c 'mount -t nfs 192.168.111.100:/share myShare'  # 마운트 시키기
$ mount  # monut로 확인
$ cp /boot/vmlinuz-4* ~/myShare/testFile  # 파일 옮겨서 확인해보기
# 재부팅 하여도 계속 마운트 되게 하기
$ su
$ gedit /etc/fstab
# 제일 아래에 적고 저장하기
> 192.168.111.100:/share  /home/centos/myShare    nfs defaults    0   0
# 재부팅하고 잘 되는지 확인하기(옵션)
```

서버 터미널로 돌아가서 확인해보기

```bash
ls -l /share/
```

윈도우 클라이언트에서(Enterprise Evaluation에서 가능)

검색 -> windows 기능 켜기/끄기 -> NFS용 서비스 -> NFS용 클라이언트 클릭 후 확인 후 cmd에서

```powershell
mount 192.168.111.100:/share *
```

파일 탐색기 열면 share가 추가되어서 공유 디렉토리로 사용 가능
