# docs
適当に書きます。

### データ型
JSONでは、値の型にObject、Array、文字列、数値、true、false、nullが存在します。
この内、文字列と数値はHSP標準の物をそのまま、ObjectとArrayに関してはそれぞれモジュール変数として扱います。true/false、nullはめんどくさいのであとで作ります。

## 全般
### 文字列からJSONを読み込む
```
parse@JSON p1, p2

p1 : パースした値を入れる変数
p2 : パースする文字列
```

### 文字列に書き出す
```
v = dump@JSON( p1 )

p1 : 書きだす値
戻り値：文字列
```

## Object/Array共通
### 型判別
```
v = getJsonContainerType( p1 )

p1 : 型を判別したい変数
戻り値：下表参照
```
| 戻り値 | 型 |
|----|---|
| 0 | HSP標準の型（str,int,double...）|
| 1 | Object|
| 2 | Array |

### 要素数取得
```
v = getElementCount( module )

module : ObjectかArray
戻り値 : 保持している要素の数
```

### 内容の走査準備
```
json_start_foreach p1
p1 : ループ用の変数。
```
→[Array](./Array.md#値を全部見る)
→[Object](Object.md#値を全部見る)

### Object
[→Object](./Object.md)

### Array
[→Array](./Array.md)
