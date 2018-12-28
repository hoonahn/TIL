# Django

[Official Website](https://www.djangoproject.com/)

[Official Documentation](https://docs.djangoproject.com/)

> *"Django makes it easier to build better Web apps more quickly and with less code."*

## Django project directory

### Basic directory and file structure

Command for starting django project.

```bash
$ django-admin.py startproject {project_name}
```

Result:

```bash
{project_name}/     # 단순한 디렉토리 이름. 변경 가능.
    {project_name}/ # 실제 Python 패키지들이 저장되는 디렉토리
        __init__.py # 패키지처럼 다루도록 알려주는 빈 파일
        settings.py # 현 Django project의 각종 환경 설정
        urls.py     # url 규칙 작성
        wsgi.py     # 현 project를 서비스 하기 위한 WSGI 호환 웹 서버의 진입점.
    manage.py       # Command-line utility.
```

Running development server

```
$ python manage.py runserver {port_number}
```


## Django app directory

### Basic directory and file structure

Command for starting django app.

```
$ python manage.py startapp {app_name}
```

```bash
{app_name}/
    __init__.py
    admin.py    # 관리자 및 관리자페이지 설정
    apps.py
    migrations/ # 데이터베이스 관련 작업이 있을 때 파일이 생성되는 폴더
        __init__.py
    models.py   # 데이터베이스 모델 설계
    tests.py    # test code
    views.py    # 페이지 접속시, 보여줄 html을 설정하거나 행동을 규정
```

[Example of Django powered by docker compose](../docker/dockercompose_django)

---

#### References

##### Django

- [Django Tutorials KR](https://docs.djangoproject.com/ko/2.0/intro/)
- [Django 자습](https://wikidocs.net/book/837)