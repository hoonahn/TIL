# Horizon (Dashboard)

[Official Github](https://github.com/openstack/horizon)

[Release notes](https://docs.openstack.org/releasenotes/horizon/)

[Project Documentation](https://docs.openstack.org/horizon/latest/)

> *“Horizon is a Django-based project aimed at providing a complete OpenStack Dashboard.”*

## Accessing source code (Django base)

I tried to access to the Horizon dashboard's source code and the path is below.

```{usr}/horizon/openstack_dashboard```

* note that I installed [OpenStack](./openstack.md) via [DevStack](./devstack.md).

Structure is like:

```
openstack_dashboard/
    api/
    conf/
    context_processor.py
    contrib/
    dashboards/
    django_pyscss_fix/
    enabled/
    exceptions.py
    hooks.py
    __init__.py
    karma.conf.js
    local/
    locale/
    management/
    policy.py
    settings.py
    static/
    templates/
    templatetags/
    test/
    themes/
    theme_settings.py
    urls.py
    usage/
    utils/
    views.py
    wsgi/
    wsgi.py
```

## Customize Dashboard

[Customize and configure the Dashboard](https://docs.openstack.org/horizon/rocky/admin/customize-configure.html)

Next step is customizing the Horizon Dashboard.\

If you edited something inside Horizon project, you should this command in Horizon project directory.

```
python manage.py compress
```

---

#### Reference

- [Tutorial: Building a Dashboard using Horizon](https://docs.openstack.org/horizon/latest/contributor/tutorials/dashboard.html)