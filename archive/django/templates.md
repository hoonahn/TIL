# Templates

[Official Documentation](https://docs.djangoproject.com/en/2.1/topics/templates/)

> *"Being a web framework, Django needs a convenient way to generate HTML dynamically. The most common approach relies on templates. A template contains the static parts of the desired HTML output as well as some special syntax describing how dynamic content will be inserted."*

## Django Template Language

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

## include vs extends in django templates

### Template Extending

Extending allows tou to overwrite blocks (```{% block content %} {% endblock %}```) from parent template.

Including does a simple include rendering a template into current context.

```html
<!-- Example -->

<!-- /app/head.html -->
<!-- some html head codes -->
...
<link rel="stylesheet" type="text/css" href="{% static 'css/style.css' %}">
...

# /app/template_page.html
<!DOCTYPE html>
<html lang="en">
<head>
{% include 'app/head.html' %}
<title>{% block title %}{% endblock %}</title>
</head>
<body>
    {% block body %}
    {% endblock %}
</body>
</html>

<!-- /app/index.html -->
{% extends 'app/template_page.html' %}
{% block title%}Welcome{% endblock %}
{% block body %}
<div class="container"> 
    <a>Welcome!</a>
</div>
{% endblock %}

<!-- Final rendered html file -->
<!DOCTYPE html>
<html lang="en">
<head>
...
<link rel="stylesheet" type="text/css" href="{% static 'css/style.css' %}">
...
<title>Welcome</title>
</head>
<body>
    <div class="container">
        <a>Welcome!</a>
    </div>
</body>
</html>
```



---

#### Reference

- [{% include %} vs {% extends %} in django templates](https://stackoverflow.com/questions/2863695/include-vs-extends-in-django-templates)