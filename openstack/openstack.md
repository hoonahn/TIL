# OpenStack

[Official Website](https://www.openstack.org/)

[Official Documentation](https://docs.openstack.org/)

> *"OpenStack is a cloud operating system that controls large pools of compute, storage, and networking resources throughout a datacenter, all managed through a dashboard that gives administrators control while empowering their users to provision resources through a web interface."*

## Issue

### Missing value auth-url required for auth plugin password - Solved

devstack 설치 후 openstack image list 커맨드를 실행할 때 실행이 되지 않는 경우..

```
Missing value auth-url required for auth plugin password
```

먼저, 데모 프로젝트(테넌트)의 admin 계정으로 세팅하고 그 이후에 openstack 명령어들을 사용하면 작동한다. 

```bash
$ . openrc admin demo
```

---

#### Reference

- [Devstack을 활용한 오픈스택 설치하기](https://www.popit.kr/devstack-%EC%9D%B4%EC%9A%A9-%EC%98%A4%ED%94%88%EC%8A%A4%ED%83%9D-%EC%84%A4%EC%B9%98%ED%95%98%EA%B8%B0/)
