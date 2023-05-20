# **Django'ya Giriş**

## **-Django Nedir? Ne işe yarar?**

Django, Python dillerini kullanarak web uygulamalarını oluşturmamızı sağlar. Web uygulamalarını hızlı ve güvenli bir şekilde geliştirmek için uygun ortamı sağlar. Bu sayede popülaritesini arttırmış ve web geliştirmede geniş bir kesim tarafından desteklenmiştir.   
Django öğrenebilmek için birçok web sitesi ve uygulamalı videolar mevcuttur. Ancak en etkili yöntem kendi web sitenizi oluşturmaya çalışmak, hata yapmak ve sonuçları gözlemlemektir. 

## **-Kurulum**

Django kullanmaya başlamadan önce kurulumlarımızı tamamlamamız gerekir. Öncelikle kullanacağımız dil Python olduğundan güncel bir Python sürümü kurmamız gerekir. Kodlarınızı daha rahat yazabilmek için basit bir kod editörü kurabilirsiniz.   
Python projelerinde kullanacağınız paketleri doğru ve sade bir şekilde yönetmek için virtualenv (Virtual Environment) kurabilirsiniz. Kullanacağınız paketlerin listesini tutabilmek için ise requirements dosyası oluşturmalısınız.    
Bahsettiğim kurulumların farklı işleti sistemlerinde farklı adımları olduğundan paylaşacağım bağlantıdan kendi işletim sisteminizi bulup kurulum sağlayabilirsiniz.

[Installation](https://tutorial.djangogirls.org/tr/installation/)

## **-Proje Başlatmak**
Terminalde yeni Django projeniz için kullanacağınız bir dosya oluşturun:
```
$ django-admin startproject myproject .
```
myproject dosyasını oluşturduğunuzda dosyanıza bağlı birden çok dosya yüklenecek. Django'nun en güzel yanı, tüm ihtiyaçlarınız size sunulacak.  
Başladığımız projenin çalışıp çalışmadığını kontrol edelim:
```
python manage.py runserver
```
http://127.0.0.1:8000/ adresimizin doğru bir şekilde çalışması gerekiyor. Eğer hata aldıysanız dosya konumlarınızı kontrol edin.
