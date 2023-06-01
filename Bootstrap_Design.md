## Bootstrap ile Sayfa Tasarımı

base.html sayfamıza gelip liste halinde eklediğimiz linkleri silelim ve body etiketi içine nav etiketi açalım. Her iki static klasörümüzde de css dosyalarımızın içini temizleyelim. Böylece sayfamızı bootstarp ile tasarlamaya çalışalım.     
Bu tasarı ile ilgili kendi base.html dosyamın kodlarını bırakacağım.. Yapılan değişiklikleri gözlemleyip araştırın.
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
    <nav class="navbar navbar-dark bg-primary navbar-expand-lg">
        <div class="container">
            <a class="navbar-brand" href="">Blogapp</a>
            <ul class="navbar-nav me-auto">
                <li class="nav-item">
                    <a class="nav-link" href="">Home</a>
                </li>
                <li class="nav-item">
                    <a class="nac-link" href="">Blogs</a>
                </li>
            </ul>
                
        </div>
    </nav>

    <div class="container mt-3">
        <div class="row">
            <div class="col-3">
                <div class="list-group">
                    <a class="list-group-item list-group-item-action" href="">Programlama</a>
                    <a class="list-group-item list-group-item-action" href="">Web Programlama</a>
                    <a class="list-group-item list-group-item-action" href="">Mobil Uygulamalar</a>
                </div>
            </div>
            <div class="col-9">
                <div  class="card mb-3">
                    <div class="row">
                        <div class="col-md-3">
                            <img src="{% static 'img/1.jpeg' %}" alt="" class="img-fluid">
                        </div>
                        <div class="col-md-9">
                            <div class="card-body">
                                <h5 class="card-title">Köprü</h5>
                                <p class="card-text">Lorem ipsum dolor sit amet, consectetur adipisicing elit. Modi, velit.</p>
                            </div>
                        </div>
                    </div>
                </div>
                <div  class="card mb-3">
                    <div class="row">
                        <div class="col-md-3">
                            <img src="{% static 'img/2.jpeg' %}" alt="" class="img-fluid">
                        </div>
                        <div class="col-md-9">
                            <div class="card-body">
                                <h5 class="card-title">Kadın</h5>
                                <p class="card-text">Lorem ipsum dolor sit amet consectetur adipisicing elit. Temporibus.</p>
                            </div>
                        </div>
                    </div>
                </div>
                <div  class="card mb-3">
                    <div class="row">
                        <div class="col-md-3">
                            <img src="{% static 'img/3.jpeg' %}" alt="" class="img-fluid">
                        </div>
                        <div class="col-md-9">
                            <div class="card-body">
                                <h5 class="card-title">Ağaç</h5>
                                <p class="card-text">Lorem ipsum dolor sit, amet consectetur adipisicing elit.</p>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
    {% block content %}{% endblock %}

    <script src="{% static 'js/bootstrap.min.js'%}"></script>
    <script src="{% static 'js/base.js' %}"></script>

    {% block js_file %}{% endblock %}
</body>
</html>
```

Şuan bütün base.html dosyamız bu şekilde gözüküyor. Peki sayfamızda ne gibi değişikler oldu?
style.css ve base.css dosyalarımızın içini temizleyelim. 
Böylelikle yazdığımız kodlar düzgünce çalışacak. Ancak kodlarımızı base.html dosyamıza yazdığımız için farklı sayfalara da gitsek sayfa görüntümüz değişmeyecek bunu da düzenlemek için base.html içindeki kodlarımızı parçalamamız lazım. Bu işlemler için aşağıdaki YouTube linkinden adımları takip edebilirsiniz.

[Partial Templates](https://youtu.be/slq_tlEX6Rk)
