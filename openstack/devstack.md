# DevStack
[Official Documentation](https://docs.openstack.org/devstack/latest/)
> *“DevStack is a series of extensible scripts used to quickly bring up a complete OpenStack environment based on the latest versions of everything from git master.”*

## DevStack Download

``` bash
 git clone https://git.openstack.org/openstack-dev/devstack
```

*Updating ```apt-get``` to lastest before installing is recommanded.*

Tutorials to install DevStack is in the documentation link.

## Issue

### unable to resolve host - Solved

devstack 설치 과정 마지막에 ```./stack.sh``` 커맨드 실행시 중간에 호스트를 확인하는 과정에서 다음 에러가 발생하며 설치가 중단됨.

```bash
$ hostname -f
hostname: Name or service not known
```

찾아보니 ```/etc/hosts```와 ```/etc/hostname``` 간에 매핑이 잘 안되어 있어서 그렇다고 하는데, 다시 확인이 필요할 것 같다.

확인 결과 ```/etc/hostname```에 있는 호스트 명과 ```/etc/hosts```에 127.0.1.1 호스트 명이 일치하지 않았다. 같은 호스트 명으로 일치 시키니 ```stack.sh``` 스크립트가 정상적으로 작동하며 설치가 진행되었다.

```bash
$ cat /etc/hostname
{name_of_host}

$ cat /etc/hosts
127.0.0.1   localhost
127.0.1.1   {name_of_host}
...
```

### ALLOWED_HOST - Solved

OpenStack이 ./stack.sh 실행되고 있으나 대시보드 접근이 안되고, horizon.log에서 ALLOWED_HOST 관련 에러가 발생시 직접 활성 등록을 하면 해결된다.

```bash
sudo vi /opt/stack/horizon/openstack_dashboard/local/local_settings.py

ALLOWED_HOSTS = ['www.example.com']
↓
ALLOWED_HOSTS = ['{host_ip_address}']
```

---

#### Reference to solve this issue

[Error message “sudo: unable to resolve host (none)”
](https://askubuntu.com/questions/59458/error-message-sudo-unable-to-resolve-host-none)