## **Models**

Bir model, verileriniz hakkında tek ve kesin bilgi kaynağıdır. Depoladığınız verilerin temel alanlarını ve davranışlarını içerir. Genel olarak, her model tek bir veritabanı tablosuyla eşleşir.

Temel bilgiler:

Her model, django.db.models.Model alt sınıfına sahip bir Python sınıfıdır.
Modelin her bir niteliği bir veritabanı alanını temsil eder.

Modeller hakkında daha detaylı bilgi almak için [Models](https://docs.djangoproject.com/en/4.2/topics/db/models/) sayfasını inceleyebilirsiniz.

Şimdi kendi model.py dosyamızda düzenlemelere başlayabiliriz. Uygulamada değil de veri tabanında tutmak istediğimiz bilgilerin classını oluşturalım.

```python
from django.db import models

class Blog(models.Model):
    title = models.CharField(max_length=200)
    image = models.CharField(max_length=50)
    description = models.TextField()
    is_active = models.BooleanField(default=False)
    is_home = models.BooleanField(default=False)

class Category(models.Model):
    name = models.CharField(max_length =150)
```

Oluşturduğumuz iki model arasında ilişkiyi daha sonra kuracağız.

## **Migrations**

Uygulamamıza iki model eklemiştik ancak bu modellerin veri tabanı tarafına aktarılması gerekiyor. O halde bize gelen ugulamaların migrationlarını ilk olarak aktaralım. Terminalde 
```python
python3 manage.py migrate
```
koduyla bekleyen migrationlarımızı uygulayalım. Peki biz bu uygulanmış hali nerden göreceğiz? db.sqlite3 dosyamızdan göreceğiz bunun için de ssqlite browser isimli uygulamayı indirebilirsiniz. Uygulamayı açtığımızda veri tabanı aç kısmına tıklayıp db.sqlite3 dosyamızı açalım. Şu an migration uyguladığımız tabloları görebiliriz.

Peki yeni bir migration nasıl ekleyeceğiz?  
Modelste bazı değişiklikler yapmıştık bu değişikliklere migration uygulayabilmemiz için yeni bir migration oluşturalım. Terminale şu kodu girmeliyiz:
```python
python3 manage.py makemigrations
```
Blog uygulamamıza migrations isimli yeni bir klasör geldi ve bu klasörün içinde de 0001_initial.py dosyamız var. Bu dosyamız içinde blog ve category modellerimiz için migration uygulandığını görüyoruz. Terminalde tekrar migrate komutu uygulandığında yeni migrationlarımız uygulanmış olur.

*Migration ile ilgili hala sorunuz varsa [Django Migrations](https://youtu.be/3ldPdoApgss) adlı videoyu izleyebilirsiniz.*
