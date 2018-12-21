# OpenStack

[Official Website](https://www.openstack.org/)

[Official Documentation](https://docs.openstack.org/)

> *"OpenStack is a cloud operating system that controls large pools of compute, storage, and networking resources throughout a datacenter, all managed through a dashboard that gives administrators control while empowering their users to provision resources through a web interface."*


## Issue

### hostname

devstack 설치 과정 마지막에 ```./stack.sh``` 커맨드 실행시 중간에 호스트를 확인하는 과정에서 다음 에러가 발생하며 설치가 중단됨.

```
$ hostname -f
hostname: Name or service not known
```

찾아보니 /etc/hosts 와 /etc/hostname 간에 매핑이 잘 안되어 있어서 그렇다고 하는데, 다시 확인이 필요할 것 같다.

---

#### Reference

##### OpenStack

- [Ref]()