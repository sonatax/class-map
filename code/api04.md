# Step 4. API にリクエストする準備2

index.html

```html
<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8" />
<title>地図を表示する - API Tutorial</title>
<meta name="viewport" content="initial-scale=1,maximum-scale=1,user-scalable=no" />
<!-- ここに Mapbox の JavascriptAPI と css を読み込むコードを書きます -->
<script src="https://api.mapbox.com/mapbox-gl-js/v3.4.0/mapbox-gl.js"></script>
<link href="https://api.mapbox.com/mapbox-gl-js/v3.4.0/mapbox-gl.css" rel="stylesheet" />
<link rel="stylesheet" href="styles.css">
</head>

<body>
<!-- ここにhtmlとjavascript書いていきます -->
<div id="search-widget">
    <input type="text" id="search-term" placeholder="Enter a location">
    <button id="search-button">Search Hotels</button>
</div>
<div id="map"></div>
<script src="script.js"></script>
<script src="https://maps.googleapis.com/maps/api/js?key=Google API KEY&libraries=places&callback=initMap" async defer></script>
</body>
</html>
```

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
      console.log("this is a debug code");
  });
}
```

Next: [api05.md](./api05.md)
