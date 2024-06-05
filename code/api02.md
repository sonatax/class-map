# Step 2. ボタンを表示させる

index.html

```html
<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8" />
<title>地図を表示する - API Tutorial</title>
<meta name="viewport" content="initial-scale=1,maximum-scale=1,user-scalable=no" />
<!-- ここに Mapbox の JavascriptAPI と css を読み込むコードを書きます -->
<script src="https://api.mapbox.com/mapbox-gl-js/v1.6.1/mapbox-gl.js"></script>
<link href="https://api.mapbox.com/mapbox-gl-js/v1.6.1/mapbox-gl.css" rel="stylesheet" />
<link rel="stylesheet" href="styles.css">
</head>

<body>
<!-- ここにhtmlとjavascript書いていきます -->
<div id="search-widget">
    <input type="text" id="search-term" placeholder="Enter a location">
    <button id="search-button">Search Hotels</button>
</div>
<div id="map"></div>
<input id="button" type="button" value="Exec" onclick="OnButtonClick();"/>
<script>
// mapbox の accessToken を設定
mapboxgl.accessToken = '取得したaccessTokenを書いてね';
// 紀尾井町周辺の地図を表示させる
var map = new mapboxgl.Map({
    container: 'map',
    style: 'mapbox://styles/mapbox/outdoors-v11',
    center: [139.736897, 35.679584],
    zoom: 15
});
</script>
</body>
</html>
```

styles.css

```css
body, html {
    margin: 0;
    padding: 0;
    height: 100%;
    width: 100%;
}

#map {
    position: absolute;
    top: 50px;
    bottom: 0;
    width: 100%;
}

#search-widget {
    position: absolute;
    z-index: 1; /* 上に表示 */
    top: 10px;
    left: 50%;
    transform: translateX(-50%);
    background: white;
    padding: 10px;
    border-radius: 3px;
    box-shadow: 0px 0px 10px rgba(0,0,0,0.5);
}

#search-term {
    width: 300px;
    padding: 10px;
    border: 1px solid #ddd;
    border-radius: 3px;
    margin-right: 10px;
}

#search-button {
    padding: 10px 20px;
    background: #1e90ff;
    color: white;
    border: none;
    border-radius: 3px;
    cursor: pointer;
}

#search-button:hover {
    background: #007bff;
}
```

Next: [api03.md](./api03.md)
