# Google Maps Route Application with .NET Core

Bu proje, kullanıcıdan alınan başlangıç ve varış noktaları arasında Google Maps API ile rota çizen ve mesafe ile süre bilgilerini gösteren bir uygulamadır.

## Kurulum

### 1. Google Maps API Key Alın
1. Google Cloud Console'da bir proje oluşturun.
2. API ve Hizmetler kısmından **API Key** oluşturun.
3. **Directions API** ve **Maps JavaScript API** servislerini etkinleştirin.
4. API Key'i not alın; bunu proje içinde kullanacağız.

### Kullanım

Aşağıda, projede kullanılan önemli fonksiyonlar ve kod parçacıkları bulunmaktadır:

#### Haritayı Başlatma

```javascript
 const map = new google.maps.Map(document.getElementById('map'), {
                center: { lat: 41.0082, lng: 28.9784 }, // Istanbul koordinatları
                zoom: 7,
            });

```
#### Rota Hesaplama

```javascript
     const directionsService = new google.maps.DirectionsService();
            const directionsRenderer = new google.maps.DirectionsRenderer();
            directionsRenderer.setMap(map);

            const calculateRoute = () => {
                const request = {
                    origin: document.getElementById('departure').value,
                    destination: document.getElementById('arrival').value,
                    travelMode: 'DRIVING',
                };

                directionsService.route(request, (result, status) => {
                    if (status === 'OK') {
                        directionsRenderer.setDirections(result);
                        document.getElementById('distance').innerText = result.routes[0].legs[0].distance.text;
                        document.getElementById('duration').innerText = result.routes[0].legs[0].duration.text;
                    }
                });
            };
```
### Ornek 

![Örnek Harita]([[https://github.com/gokhn/GoogleMapsDrivingRoute/blob/master/route.png])
