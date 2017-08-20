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
