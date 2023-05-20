# **Django Apps**
Artık uygulamamızı oluşturmaya başlayabiliriz. Bir blog sitesi yapacağız bu yüzden blog isminde bir klasör oluşturalım.

```
python3 manage.py startapp blog
```
Blog klasörümüz içinde yine Django'nun bize sunduğu hazır dosyalarımız gelecek. Şimdi yapmamız gereken klasörlerimiz arasında bağlantı kurmak. Bunun için mysite klasöründen settings.py dosyasına gitmeliyiz. Oluşturmaya başladığımız blog klasörünü settings.py'deki INSTALLED_APPS bölümüne yazalım ve böylece projemize oluşturduğumuz yeni klasörü (blog) tanıtmış olalım.

## **Urls & Views**
