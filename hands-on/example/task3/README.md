## タスク

クライアント側で計算幾何学計算を行う [geometryEngine](https://developers.arcgis.com/javascript/latest/api-reference/esri-geometry-geometryEngine.html) を使用して、クリック地点から 1km のバッファーを作成し、作成したバッファーをマップに表示してみましょう。

## 回答例

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
