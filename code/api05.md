# Step 5. API にリクエストする

script.js

```javascript
mapboxgl.accessToken = '取得したaccessTokenを書いてね';

// 地図を初期化する
var mapbox = new mapboxgl.Map({
    container: 'map', // 地図を表示するコンテナID
    style: 'mapbox://styles/mapbox/streets-v11', // 表示する地図のスタイル
    center: [139.6917, 35.6895], // 東京の経度と緯度
    zoom: 15 // 地図のズームレベル
});

// map の初期化
function initMap() {
  // Googleマップインスタンスを作成
  // ここではマップを表示せず、Places Libraryの機能のみを使用します
  const map = new google.maps.Map(document.createElement('div'));

  // Placesサービスを作成
  const placesService = new google.maps.places.PlacesService(map);

  // Mapboxでの検索ボタンクリックイベント
  document.getElementById('search-button').addEventListener('click', function() {
    let searchTerm = document.getElementById('search-term').value;
    if (searchTerm) {
      fetch('https://api.mapbox.com/geocoding/v5/mapbox.places/' + encodeURIComponent(searchTerm) + '.json?access_token=' + mapboxgl.accessToken)
          .then(response => response.json())
          .then(data => {
              if (data.features.length > 0) {
                  const location = data.features[0].center;
                  searchHotels(location[1], location[0], placesService);
                  mapbox.flyTo({
                      center: location,
                      zoom: 14
                  });
              } else {
                  alert('Location not found');
              }
          }).catch(error => {
              console.error('Error:', error);
              alert('Failed to retrieve location data');
          });
    } else {
      alert('Please enter a location');
    }
  });
}
```

Next: [api06.md](./api06.md)
