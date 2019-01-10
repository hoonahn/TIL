# Nova

[Official Documentation](https://docs.openstack.org/nova/latest/)

> *"Nova is the OpenStack project that provides a way to provision compute instances (aka virtual servers). Nova supports creating virtual machines, baremetal servers (through the use of ironic), and has limited support for system containers."*

Key required OpenStack services

- Keystone: identity and authentication
- Glance: compute image repository
- Neutron: provisioning the virtual or physical networks

## Accessing Nova

There is three way to access Nova.

1. Dashboard(Horizon)

We can do almost everything through dashboard. In terms of Nova, we can create instance, make a snapshot, delete instance etc. There is no term 'Nova' in dashboard but there is 'Compute'.

![horizon instances](./asset/horizon_1.png)

This is a example of Horizon page where we can control instances.

2. Nova  CLI

[Nova CLI Ref](https://docs.openstack.org/python-novaclient/rocky/cli/nova.html)
[Compute command-line client](https://docs.openstack.org/mitaka/cli-reference/nova.html)

CLI is almost supported.

```bash
# ex) boot command is for booting the server
nova boot --flavor 42 --image {image_id} <name of the server>
```

3. Compute API

[Compute API](https://developer.openstack.org/api-ref/compute/?expanded=create-server-detail#create-server)

We can access to Compute servcie by RESTapi aswell. 

---

#### Reference

- [Nova System Architecture](https://docs.openstack.org/nova/latest/user/architecture.html)
- [Compute Server Overview KR](https://docs.openstack.org/mitaka/ko_KR/install-guide-obs/common/get_started_compute.html)
- [Verify operation](https://docs.openstack.org/nova/latest/install/verify.html)
- [Compute Documentaion - Admin](https://docs.openstack.org/nova/latest/admin/index.html)