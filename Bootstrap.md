## Bootstrap Kütüphanesi

[Bootstrap Link](https://getbootstrap.com/)

Verilen linkten Bootstrap kütüphanesine gidiniz. Versiyonu 5.1 seçebilirsiniz.  
Css linkini tarayıcınıza yapıştırın ve çıkan bütün kodları kopyalayın. Ana dizinimizdeki static klasörümüz içindeki css klasörümüze bootstrap.min.css dosyası açalım. Kopyaladığımız kodları bu dosya içine ekleyelim.

Javascript dosyalarımız için ana dizindeki static klasörümüz içindeki js klasörüne bootstrap.min.js dosyası açıp bu dosya içine js kütüphanesinin kodlarını yapıştıralım. 

Şimdi bu kütüphaneleri kendi uygulamamızda kullannmaya çalışalım. base.html dosyamıza eklemelerimizi yapalım. Hangi sayfada kullanacağımızı belirlemek için base.html dosyamıza block açalım. Kullanacağım js dosyaları için blog klasörümüzde static/blog/js klasör dizinimize yeni bir dosya açalım (script.js). Sadece belirli sayfalarda kullanacağımız js kodlarımızı bu dosyaya ekleyeceğiz. (script.js dosyamızı index.html için kullandığımızı varsaylım.)

base.html ve index.html dosyalarımızın son hali aşağıdaki gibi olmalıdır:
```html
{% load static %}

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel="stylesheet" href="{% static 'css/base.css' %}">
    <link rel ="stylesheet" href="{% static 'css/bootstrap.min.css' %}"

    {% block css_files %}{% endblock %}

    <title>
        {% block title %}{% endblock %} | Blogapp
    </title>
</head>
<body>
    <ul>
        <li><a href="">Home</a></li>
        <li><a href="">Blogs</a></li>
    </ul>
    {% block content %}{% endblock %}

    <script src="{% static 'js/bootstrap.min.js'%}"></script>
    <script src="{% static 'js/base.js' %}"></script>

    {% block js_file %}{% endblock %}
</body>
</html>
```
```html
{% extends "base.html" %}
{% load static %}

{% block css_files %}
<link rel="stylesheet" href="{% static 'blog/css/style.css'%}"
{% endblock %}

{% block title %} Home {% endblock%}
{% block content%}

<h1>Homepage</h1>
<img src="{% static 'img/django.png' %}" alt="" width="100">

{% endblock %}
```

Bootstrap ile tasarım yapmayı daha sonra öğreneceğiz.
