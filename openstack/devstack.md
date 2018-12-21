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

### hostname

devstack 설치 과정 마지막에 ```./stack.sh``` 커맨드 실행시 중간에 호스트를 확인하는 과정에서 다음 에러가 발생하며 설치가 중단됨.

```
$ hostname -f
hostname: Name or service not known
```

찾아보니 /etc/hosts 와 /etc/hostname 간에 매핑이 잘 안되어 있어서 그렇다고 하는데, 다시 확인이 필요할 것 같다.

```
+++lib/tls:source:43                         hostname -f
hostname: Name or service not known
++lib/tls:source:43                         DEVSTACK_HOSTNAME=
+++lib/tls:source:43                         err_trap
+++./stack.sh:err_trap:563                   local r=1
+++./stack.sh:err_trap:564                   set +o xtrace
stack.sh failed
Error on exit
World dumping... see /opt/stack/logs/worlddump-2018-12-21-070944.txt for details
/bin/sh: 1: brctl: not found
sudo: unable to resolve host kr-dev02.micfo.com
sudo: unable to resolve host kr-dev02.micfo.com
sudo: unable to resolve host kr-dev02.micfo.com
```
