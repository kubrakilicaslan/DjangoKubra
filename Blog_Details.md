# **Django Apps**

## Blog Details
Daha önceden herbir blog bağlantımız için detay sayfası oluşturmuştuk. viewws.py dosyamızda oluşturduğumuz liste ile bloglarımızı idlerine göre birbirinden ayırmış ve farklı özellikler vermiştik. Yine views.py dosyamızda oluşturduğumuz fonksiyonların içinde bu listedeki bilgileri kullanmıştık. Şimdi de benzer bir işlem yapacağız. Gelen her blog bilgisinin detaylarına bakabilmemiz için bir döngü kurmamız gerekecek. views.py dosyamızdaki blog_details fonksiyonumuzun içi şu şekilde gözükecek:

```python
def blog_details(request, id):
    blogs = data["blogs"]
    selectedBlog = None
    for blog in blogs:
        if blog["id"] == id:
            selectedBlog = blog
            
    return render(request, "blog/blog_details.html", {
        "blog":selectedBlog
    })
```
Tabiki blog_details.html sayfamızda sadece id değil farklı bilgilerin de gözükmesini istiyoruz. Daha önce _blog.html sayfamızda yazdıklarımızı kopyala yapıştırla blog_details.html dosyamıza taşıyalım. Böylece daha önceki kart görünümümüz detay sayfamızda da var olacak. blog_details.html dosyamızın son hali :

```html
{% extends "base.html" %}
{% load static %}


{% block title %} Blog Details {% endblock %}
{% block content%}

    
    <div class="container mt-3">
        <div class="row">
            <div class="col-3">
                {% include 'partials/_categories.html' %}
            </div>
            <div class="col-9">
                                
                <div  class="card mb-3">
                    <div class="row">
                        <div class="col-md-3">
                            <img src="/static/img/{{blog.image}}" alt="" class="img-fluid">
                        </div>
                        <div class="col-md-9">
                            <div class="card-body">
                                <h5 class="card-title">
                                    {{ blog.title }}
                                </a>
                                </h5>
                                <p class="card-text">{{ blog.description }}</p>
                            </div>
                        </div>
                    </div>
                </div>
                
            </div>
        </div>
    </div>

{% endblock %}
```
