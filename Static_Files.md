# **Django Apps**
## **-Static Files**  
Öncelikle settings.py dosyamızdan STATIC_URL = 'static/' dosyamız olduğunu görüyoruz (koddaki ismi değiştirebilirsiniz). Böyle bir dosyayı kullanabileceğimize göre önce bu dosyayı elde edelim. blog klasörümüzün içine bir static dosyası açalım. Daha önce templateleri anlatırken söylediğimiz gibi spesifik bir dosya arıyorsak isimlendirmemizi detaylandırmalıyız. Bu yüzden static klasörümüzün içine blog klasörü ve bu klasörün de içine css klasörü açabiliriz (css dosyalarımızı burada tutacağız). Şimdi sayfamızı güzel bir görünüme kavuşturmak için css klasörümüz içine bir style.css dosyası açalım. Şimdilik basit bir örnek olarak sadece arka plan rengini değiştirelim.   
Css dosyamız şu şekilde görülecektir: 
```css
body{
    background-color: yellow
}
```
Peki bu css dosyamızı html dosyalarımıza nasıl bağlayacağız?    
Hatırlıyorsanız bir base.html dosyası hazırlamıştık. Şimdi base.html dosyamızın nasıl görünmesi gerektiğine bakalım:
```html
{% load static %}

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel="stylesheet" href="{% static 'blog/css/style.css' %}">
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
</body>
</html>
```

Şimdi arka planımız sarı oldu. Şimdi blog klasörümüz içine bir img klasörü açalım. Şimdi internetten bulduğumuz bir resmi farklı kaydet yaparak blog klasörümüzün içindeki img klasörümüze kaydedelim. Bu resmimizin ana sayfamızda gözükmesini istiyoruz diyelim. O zaman index.html dosyamıza bir ekleme yapmamız gerekir. 
```html
{% extends "base.html" %}
{% load static %}

{% block title %} Home {% endblock%}
{% block content%}

<h1>Homepage</h1>
<img src="{% static 'blog/img/django.png' %}" alt="" width="100">

{% endblock %}
```
django.png kısmına resim dosyanızın adını yazmanız önemli. Dikkat edelim.   
Daha önce ortak ulaşmak istediğimiz templateleri tek bir dosya da toplamıştık aynı şeyi static dosyalarımız için de yapalım. Ana dizinimizde static isimli bir klasör oluşturalım. Bu klasörün içine de css,img ve js klasörlerimizi ekleyelim. Yeni oluşturduğumuz static klasörümü dışarı açık değil. Bunun için settings.py dosyamızda şu şekilde değişiklik yapmalıyız:
```python

STATIC_URL = 'static/'
STATICFILES_DIRS = [
    BASE_DIR / "static"
]
```
Dosyalarımızı buraya taşıyalım, mesela style.css dosyamızı yeni oluşturduğumuz css klasörümüzün içine alalım. Resim dosyamızı da img klasörümüze alalım. Şimdi dosyalarımız ana dizinin içinde ancak bağlantı adreslerimizi düzeltmedik. index.html ve base.html dosyalarının içindeki bağlantı kodlarımızda blog kısmını silmemiz yeterli olacaktır. Kodlarımız:
```html
<img src="{% static 'img/django.png' %}" alt="" width="100">
```
```html
<link rel="stylesheet" href="{% static 'css/style.css' %}">
```
Peki tüm sayfalarda ortak olması gereken özelliklerimiz dışında sayfalara özgü özellikler eklemek istersek? 
base.html dosyamızda bir yer işaretleyelim.
```html
 <link rel="stylesheet" href="{% static 'css/style.css' %}">

    {% block css_files %}{% endblock %}
    
    <title>
```
Daha sonra blog appimizin içindeki static klasörümüze yeni bir css dosyası açalım, ismine style.css diyelim. Karışıklığı önlemek için ana dizindeki static klasörümüzdeki css dosyamızı base.css olarak değiştirelim, base.html dosyamıza isim değişikliğimizi aktarmayı unutmayalım. Olmasını istediğimiz özelliklerimizi bu dosyaya yazalım.  
Mesela:
```css
h1{
    font-size: 40px;
    border-bottom: 2px solid red;
}
```
Bu özellikleri index.html'de kullanalım:
```html
{% load static %}

{% block css_files %}
<link rel="stylesheet" href="{% static 'blog/css/style.css'%}"
{% endblock %}
```
