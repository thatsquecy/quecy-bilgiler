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

# HTML Üzerinde Apilerin Kullanımı

HTML, web sayfalarının tasarımını ve içeriğini belirtmek için kullanılan bir işaret dili olduğundan, API'leri doğrudan HTML üzerinde kullanmak pek mümkün değildir. Ancak, web sayfalarında API'lerin kullanılması için JavaScript kullanılabilir.

JavaScript, web sayfalarında etkileşimli öğeler oluşturmak ve API'lerden veri almak için kullanılan bir programlama dilidir. Örneğin, bir web sayfasında OpenWeatherMap API'sini kullanarak, belirli bir şehir için hava durumu verilerini alabilir ve kullanıcılara gösterebilirsiniz.

Aşağıdaki örnek kod, OpenWeatherMap API'sini kullanarak, New York'taki hava durumu verilerini alır ve kullanıcılara gösterir:

```html
<!DOCTYPE html>
<html>
<head>
	<title>Weather App</title>
</head>
<body>
	<h1>Weather in New York</h1>
	<div id="weather-info"></div>
	<script src="https://code.jquery.com/jquery-3.6.0.min.js"></script>
	<script>
		$(document).ready(function() {
			var apiKey = '{API_KEY}';
			var apiUrl = 'http://api.openweathermap.org/data/2.5/weather?q=NewYork&appid=' + apiKey;
			
			$.getJSON(apiUrl, function(data) {
				var temp = data.main.temp;
				var humidity = data.main.humidity;
				var description = data.weather[0].description;
				
				$('#weather-info').html('Temperature: ' + temp + ' Kelvin<br>Humidity: ' + humidity + '%<br>Description: ' + description);
			});
		});
	</script>
</body>
</html>
```
Bu kod, jQuery kütüphanesini kullanarak, API'den hava durumu verilerini alır ve HTML sayfasında belirli bir <div> öğesi içinde gösterir. JavaScript kodu, jQuery'nin $.getJSON() fonksiyonunu kullanarak API'ye bir GET isteği gönderir ve API'den gelen JSON verilerini alır. Ardından, JavaScript, bu verileri analiz eder ve HTML sayfasındaki belirli bir öğeye yazdırır.

Bu örnek, HTML sayfalarında API'leri kullanmak için JavaScript'in nasıl kullanılabileceğini göstermektedir. Ancak, API'lerin kullanımı için gerekli olan diğer programlama dilleri veya araçlar da kullanılabilir.
