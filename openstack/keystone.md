# Keystone (Identity)

[Official Documentation](https://docs.openstack.org/keystone/latest/)

[API Reference](https://developer.openstack.org/api-ref/identity/index.html)

> *"Keystone is an OpenStack service that provides API client authentication, service discovery, and distributed multi-tenant authorization by implementing OpenStack’s Identity API."*

To make REST API request to Openstack services, we need to supply authentication token in the ```X-Auth-Token``` request header.

## Authentication and token management

바디에 들어가는 payload에 어떤 auth method를 사용할지 명시해줘야한다. 

- **password**
- **token**
- the credentials
- the auth scope(optional)

```POST /v3/auth/tokens```로 request header 에 auth method 를 포함하여 요청을 보내면, ```X-Subject-Token```로 response header에 토큰이 받아진다. 토큰은 1시간 동안 유효하다. 이 토큰은 다른 API를 call 할 때에 ```X-Auth-Token``` request header에 넣어 보내면 된다.


---

#### Reference

- [Ref]()