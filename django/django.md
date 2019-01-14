# Django

[Official Website](https://www.djangoproject.com/)

[Official Documentation](https://docs.djangoproject.com/)

> *"Django makes it easier to build better Web apps more quickly and with less code."*

## Django Design Pattern

### MTV

Django's design pattern is so called MTV(Model, Template, View), similar to MVC.

#### Model

Expresses data. Coded with ```class```.\
One Model class is expressed as one table in database system.

```python
class News(models.Model):
    title = models.CharField(max=100)
    contents = models.textField()
    date = models.DateTimeField(default=timezone.now)

    def publish(self):
        self.save()
```

Each variables in class is a table field in db. Each field creates class instance of each models.~Field() and allocate them.\
Therefore field creates class variable instead of instance variables.

#### Template

Made with HTML and has only presentation logic for presenting the view.\
Dynamically uses data fretched from View on templates.\
(Similar role of View from MVC pattern.)

##### Django Template Language

Syntax used in Django Template.\
Consists of:

```django
{# Template Variables #}
<h3>{{ data }}</h3>

{# Template Tags #}
{% for item in data %}
    <ol>
        <li>{{ item.name }}</li>
    </ol>
{% endfor %}

{# Template Filters #}
{{ title|upper }}
{{ date|data:"Y/m/d" }}

{# Template Comments #}
{# one-line comment #}
{% multi-line comment %}
say something
{% endcomment %}
```

#### View

Consist of methods, form of getting HTTPRequest and returning HTTPResponse.\
View is the core of the logic. Gets the data from Model and hand it to Template.\
(Similar to Controller from MVC pattern.)

##### create view & check

create a view and check it from web.

1. url

URL(Uniform Resource Locator) locates a resource in web. Location of resource must be wroted in ```urls.py``` file in order to let django access to resoures.

2. view

## Django project directoryand file structure

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

## Django app directory and file structure

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

[Example of Django powered by docker compose](https://github.com/HoonAhn/dockercompose_django)

### Django w/ Docker Compose

Docker Compose 로 정의된 Django 프로젝트의 경우 명령어를 입력할 때에 다음과 같이 진행한다.

```bash
docker-compose run {name_of_webapp} django-admin.py startproject {name_of_django_project} .
docker-compose run {name_of_webapp} python manage.py startapps {name_of_django_app}
```

```migrate``` 이나 ```createsuperuser``` 와 같은 명령어도 동일하게 위와 같은 방식으로 사용할 수 있다.\
Web App 뿐만 아니라 DB App 의 경우 ```run``` 뒤에 DB App의 이름을 넣고 실행하면 접근할 수 있다.

[TIL of Docker-Compose](../docker/docker-compose.md)


### Migration

> "History of changes of Model"

[Doc of Migration](https://docs.djangoproject.com/en/1.10/topics/migrations/)
[초보몽키의 개발공부로그 Django 기본 05 - Migration](https://wayhome25.github.io/django/2017/03/20/django-ep6-migrations/)

---

#### References

##### Django

- [Django Tutorials KR](https://docs.djangoproject.com/ko/2.0/intro/)
- [Django 자습](https://wikidocs.net/book/837)
- [코딩장이 블로그 #django](https://itholic.github.io/tags/#django)