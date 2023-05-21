# **Django Apps**
Artık uygulamamızı oluşturmaya başlayabiliriz. Bir blog sitesi yapacağız bu yüzden blog isminde bir klasör oluşturalım.

```
python3 manage.py startapp blog
```
Blog klasörümüz içinde yine Django'nun bize sunduğu hazır dosyalarımız gelecek. Şimdi yapmamız gereken klasörlerimiz arasında bağlantı kurmak. Bunun için mysite klasöründen settings.py dosyasına gitmeliyiz. Oluşturmaya başladığımız blog klasörünü settings.py'deki INSTALLED_APPS bölümüne yazalım ve böylece projemize oluşturduğumuz yeni klasörü (blog) tanıtmış olalım.

## **Urls & Views**
Sahip olduğumuz adresten başka sayfalarımızın adreslerine gitmek istersek ne yapacağız?     
Mesela, http://127.0.0.1:8000/ bu adres bizi ana sayfada tutarken biz blog sayfasına gitmek istiyoruz. O halde adresimizin sonuna blogs/ yazısını (ya da nereye gitmek istiyorsak) ekleyebiliriz. Ancak bu adresi henüz tanımlamadık.   
Öncelikle blog klasörümüze gidip urls.py isimli bir dosya açmalıyız.    
Açtığımız urls.py dosyasının içerisini dolduralım:

```python
from django.urls import path
from . import views

urlpatterns = [
    path("",views.index),
    path("blogs",views.blogs),
    path("blogs/<int:id>", views.blog_details),
]
```

Adreslerimizi tanıttık ancak bunların viewsta bir karşılığı yok. Bağlantıyı nasıl kuracağız? 

```python
from django.http.response import HttpResponse
from django.shortcuts import render

def index(request):
    return HttpResponse("homepage")

def blogs(request):
    return HttpResponse("blogs")

def blog_details(request, id):
    return HttpResponse("blog details: " + str(id))
```

Peki şimdi? blog klasörümüz içinde bağlantıları kurduk, etkileşim sağladık. Ancak mysite klosörümüzün içindeki urls.py dosyasına hala ulaşamadık. Şu evrede sitemizi çalıştırırsak sayfamız yüklenemeyecektir. Bu sorunu gidermek için de mysite klasörümüzdeki urls.py dosyasına bir adres eklemesi yapmalıyız. Son durumda dosyamız bu şekilde gözükür: 

```python
from django.contrib import admin
from django.urls import path, include

urlpatterns = [
    path('admin/', admin.site.urls),
    path('', include('blog.urls')),
]
```

Son olarak http://127.0.0.1:8000/ adresini çağırdığımızda 'homepage', http://127.0.0.1:8000/blogs adresini çağırdığımızda 'blogs', http://127.0.0.1:8000/blogs/5 adresini çağırdığımızda 'blog details: 5' yazılarını ekranda görürüz.

*Not: Sayı değeri herhangi bir int değer girilebilir. 5 örnektir.*
