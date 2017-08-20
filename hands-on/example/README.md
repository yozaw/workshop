# タスクの回答例

## 2. Web アプリの作成

### 2. Web マップ の読み込み・表示

![#c5f015](https://placehold.it/15/c5f015/000000?text=+) タスク

[Web マップクラスのドキュメント](https://developers.arcgis.com/javascript/latest/api-reference/esri-WebMap.html)を参考に、作成した Web マップを読み込んでみましょう。

![#c5f015](https://placehold.it/15/c5f015/000000?text=+) 回答例

```js
var webmap = new WebMap({
  portalItem: {
    id: "Web マップ ID"
  }
});
```

### 3. 最寄りの避難場所を検索

#### 検索地点の表示

![#c5f015](https://placehold.it/15/c5f015/000000?text=+) タスク

作成したグラフィックは symbol プロパティで incidentPointSymbol を参照しています。  
クリック地点を表すシンボルを作成し、incidentPointSymbol に代入しましょう。

![#c5f015](https://placehold.it/15/c5f015/000000?text=+) 回答例

```js
require([
  // モジュールの読み込み
  "esri/symbols/SimpleMarkerSymbol",
  "esri/symbols/SimpleFillSymbol",
  "esri/symbols/SimpleLineSymbol"
], function(SimpleMarkerSymbol, SimpleFillSymbol, SimpleLineSymbol){

  // クリック地点のシンボル
  var incidentPointSymbol = new SimpleMarkerSymbol({
    style: "circle",
    color: [255, 0, 0],
    size: 8
  });

  // バッファーシンボル
  var bufferPolygonSymbol = new SimpleFillSymbol({
    color: [255, 183, 51, 0.25],
    style: "solid",
    outline: {
      color: [255, 183, 51],
      width: 2
    }
  });

  // ルートシンボル
  var routePolylineSymbol = new SimpleLineSymbol({
    color: [89, 95, 35],
    width: 4,
    style: "solid"
  });

});
```

#### facilities（検索の対象となる施設）の設定

![#c5f015](https://placehold.it/15/c5f015/000000?text=+) タスク

クライアント側で計算幾何学計算を行う [geometryEngine](https://developers.arcgis.com/javascript/latest/api-reference/esri-geometry-geometryEngine.html) を使用して、クリック地点から 1km のバッファーを作成し、作成したバッファーをマップに表示してみましょう。

![#c5f015](https://placehold.it/15/c5f015/000000?text=+) 回答例

```js
// クリック地点から 1km のバッファーを作成
var buffer = geometryEngine.buffer(point, 1, "kilometers");

// バッファーのグラフィック
var area = new Graphic({
  geometry: buffer,
  symbol: bufferPolygonSymbol
});

// バッファーをマップに表示
view.graphics.add(area);
```

![#c5f015](https://placehold.it/15/c5f015/000000?text=+) タスク

Web マップに含まれる避難場所レイヤーを取得して shelterLayer 変数へ代入しましょう。

![#c5f015](https://placehold.it/15/c5f015/000000?text=+) 回答例

```js
// レイヤーの取得
var shelterLayer;
webmap.then(function(){
  shelterLayer = webmap.layers.find(function(layer){
    return layer.title === "レイヤーの名前";
  });
});
```
