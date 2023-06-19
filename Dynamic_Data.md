# Django Apps

## Dinamik Veri
Verilerimizi dinamik halde kullanmayı öğreneceğimizi söylemiştik. Öncelikle views.py dosyamızın içinde bir içiçe liste oluşturalım ve dinamik olmasını istediğimiz parametreleri girelim. Üç blog oluşturduğumuzdan yazdığımız parametreleri üç kere tekrarlayalım. id,title,image,is_active,is_home ve description parametrelerini girelim ve şimdilik bu verilerle hareket edelim. views.py dosyamızda daha önceden açtığımız ana sayfamız, blog sayfamız ve blog detayları sayfamız için fonksiyonlarımız mevcuttu. Bu fonksiyonların içine context isimli bir liste tanımlayıp listeler arası bağlantıyı kurmaya çalışalım.  
Burada işlemimiz bittiğinde views.y dosyamız aşağıdaki gibi görünmeli:
```python
from django.http.response import HttpResponse
from django.shortcuts import render


data = {
    "blogs": [
        {
            "id": 1,
            "title": "Köprü",
            "image": "1.jpeg",
            "is_active": True,
            "is_home": False,
            "description": "Çok güzel bir köprü"
        },
        {
            "id": 2,
            "title": "Kız",
            "image": "2.jpeg",
            "is_active": True,
            "is_home": True,
            "description": "Resim çeken kız"
        },
        {
            "id": 3,
            "title": "Ağaç",
            "image": "3.jpeg",
            "is_active": False,
            "is_home": True,
            "description": "Çok güzel bir ağaç"
        },

    ]
}
def index(request):
    context = {
        "blogs": data["blogs"]
    }
    return render(request,"blog/index.html",context)

def blogs(request):
    context ={
        "blogs": data["blogs"]
    }
    return render(request, "blog/blogs.html",context)

def blog_details(request, id):
    return render(request, "blog/blog_details.html", {
        "id":id
    })
```
*Verileri kendi istekleriniz doğrultusunda değiştirebilirsiniz.*

index.html dosyamıza daha önceden yazdığımız {% include 'blog/partials/_blog.html' %} kod satırlarından fazlalık olanları silip sadece bir tanesini bırakabiliriz. Peki bu bir taneyi dinamik olarak nasıl çoğaltacağız?    
Bir for döngüsü ile göndermiş olduğumuz context içerisindeki bütün blogs bilgilerine bakabilmemiz lazım. 
index.html dosyamızın div class="col-9" etiketinin içi şimdilik bu şekilde gözükecek:
```html
<div class="col-9">
    <h1>Homepage</h1>
    <hr>
    {% for blog in blogs %}
        {% include 'blog/partials/_blog.html' %}
    {% endfor %}
            
</div>
```
Şu an sitemizde üç bloğumuz var ancak isimleri,resimleri,açıklamaları her şey aynı. Blog bilgilerimizi güncellemek için _blog.html dosyamızda değişiklikler yapmamız gerekir.

```html
{% load static %}

<div  class="card mb-3">
    <div class="row">
        <div class="col-md-3">
            <img src="/static/img/{{blog.image}}" alt="" class="img-fluid">
        </div>
        <div class="col-md-9">
            <div class="card-body">
                <h5 class="card-title">
                    <a href="{% url 'blog_details' blog.id %}">
                    {{ blog.title }}
                </a>
                </h5>
                <p class="card-text">{{ blog.description }}</p>
            </div>
        </div>
    </div>
</div>
```

blog.image , blog.id , blog.title, blog.description gibi basit değişikliklerle blog bilgilerimizi dinamik hale getirdik. Şimdi sayfayı yenilediğinizde değişimi gözlemleyebilirsiniz.   
Peki anasayfada bütün bloglarımı görmek istemiyorum sadece is_home parametresi True olan bloglarımı görmek istiyorum diyelim. Bu filtreleme işlemini nasıl yapacağız? index.html dosyamızda bir if bloğu oluşturarak bu filtrelemeyi sağlayabiliriz.
```html
{% for blog in blogs %}
    {% if blog.is_home and blog.is_active %}
        {% include 'blog/partials/_blog.html' %}
    {% endif %}
{% endfor %}
```
Şimdi is_active ve is_home parametreleri True olan bloglar ana sayfada gözükürken diğerleri gözükmez. Ancak blogs sayfasına girdiğimizde bütün bloglarımızın orada gözüktüğünü görürüz.
Blogs sayfamızda tüm blogları değil de sadece aktif olan bloglarımızı görmek istersek benzer bir if bloğunu blogs.html dosyamıza ekleyebiliriz.
```html
 {% for blog in blogs %}
    {% if blog.is_active %}
        {% include 'blog/partials/_blog.html' %}
    {% endif %}
{% endfor %}
            
```




*Renklerin daha ayırt edici olması için django eklentisi ekleyebilirsiniz.*
