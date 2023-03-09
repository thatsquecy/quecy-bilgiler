# Api Nedir?

Elde etmek istediğiniz verileri farklı bir web sitesinden veya uygulamadan almak istediğinizde, genellikle API'ler
kullanılır. API (Application Programming Interface), bir uygulama veya web sitesi tarafından sunulan ve diğer
uygulamalar veya web siteleri tarafından kullanılan bir arayüzdür.

API, HTTP (Hypertext Transfer Protocol) aracılığıyla çalışır. API'ye bir istek göndermek istediğinizde, isteğin URL'sine
ve gerektiği durumlarda parametrelere sahip olmanız gerekir. API, sunucuda isteği işleyecek bir programda kodlanmıştır.
Sunucu, API'den gelen isteği işler, belirtilen verileri veritabanından veya diğer kaynaklardan alır ve sonuçları HTTP
yanıtı olarak geri gönderir.

API'lerin çoğu, JSON (JavaScript Object Notation) olarak adlandırılan bir veri biçiminde yanıt verir. JSON, bir nesne
notasyonu ve veri alışverişi formatıdır. JSON verileri, web tarayıcıları, uygulamalar ve programlama dilleri gibi birçok
platformda kolayca kullanılabilir.

API'ler, genellikle aşağıdaki adımları izler:

İstemci, API'ye bir istek gönderir.
API, isteği işler ve belirtilen kaynaklardan verileri alır.
API, JSON formatında verileri istemciye yanıt olarak gönderir.
İstemci, JSON verilerini alır ve istenen şekilde kullanır.
API'lerin kullanımı, birden fazla uygulama ve web sitesi arasında veri alışverişi yapmak için çok önemlidir. API'ler,
programlama dilleri ve platformlar arasında veri paylaşımını kolaylaştırarak uygulamaların ve web sitelerinin daha hızlı
ve verimli olmasını sağlar.

# Api Hakkında Örnekler

Tabii, bir örnek olarak OpenWeatherMap API'sini gösterebilirim. Bu API, dünya genelindeki hava durumu verilerine erişim
sağlar ve istemcilerin bu verilere erişmesine izin verir. Bu API'yi kullanarak, bir uygulama veya web sitesi,
kullanıcının konumunu veya belirli bir şehir adını kullanarak, o yerdeki hava durumu verilerini alabilir.

Örneğin, bir uygulama, New York'taki hava durumunu almak istiyorsa, OpenWeatherMap API'sine bir HTTP GET isteği gönderir
ve aşağıdaki URL'yi kullanır:

http://api.openweathermap.org/data/2.5/weather?q=NewYork&appid={API_KEY}

Burada, "q" parametresi New York'un adını belirtir ve "appid" parametresi, API'nin kullanımı için gerekli olan bir API
anahtarıdır.

API, bu isteği işler, New York'taki hava durumu verilerini sağlar ve JSON formatında yanıt olarak geri gönderir.
İstemci, bu yanıtı alır, JSON verilerini analiz eder ve kullanıcının hava durumu bilgilerini gösterir.

Bu örnek, OpenWeatherMap API'sinin nasıl kullanılabileceğini göstermektedir. Benzer şekilde, birçok farklı API mevcuttur
ve bunlar farklı veri kaynaklarına erişim sağlamak için kullanılabilir.

# Openweahtermap Apisinin Python Örneği

OpenWeatherMap API'si, istemcilere hava durumu verileri sağlar. Bu verileri kullanarak, uygulamalar veya web siteleri,
kullanıcılara hava durumu tahminlerini göstermek veya belirli bir bölgedeki hava durumunu takip etmek için
kullanılabilir.

API'den aldığınız verileri kullanmak için, genellikle bir programlama dili veya çerçeve kullanmanız gerekir. Bu dil veya
çerçeve, API'den gelen verileri almak ve analiz etmek için kullanılabilir.

Örneğin, Python kullanarak OpenWeatherMap API'sinden hava durumu verilerini almak ve kullanmak için, "requests"
kütüphanesi ve JSON verilerini işlemek için "json" modülü kullanılabilir. Aşağıdaki kod örneği, API'den New York'taki
hava durumu verilerini alır ve JSON verilerini analiz ederek, sıcaklık ve nem gibi bazı bilgileri yazdırır:

```python
import requests
import json

url = "http://api.openweathermap.org/data/2.5/weather?q=NewYork&appid={API_KEY}"
response = requests.get(url)
data = json.loads(response.text)

temp = data['main']['temp']
humidity = data['main']['humidity']

print("Temperature: {} Kelvin".format(temp))
print("Humidity: {}%".format(humidity))
```
