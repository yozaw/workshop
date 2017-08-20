## タスク

作成したグラフィックは symbol プロパティで incidentPointSymbol を参照しています。  
クリック地点を表すシンボルを作成し、incidentPointSymbol に代入しましょう。

## 回答例

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
