# json-hsp
雑に作ったHSPのJSONライブラリ

## example
```hsp
/* パースして、変数dataに一番上の階層の値を代入 */
parse@JSON data, {"{
    "name" : "Taro",
    "age" : 13 
}"}
```
```hsp
/* キーに対応する値を表示 */
get@JSON_Object data, out, "name"
print out  // "Taro"が表示される
```
```hsp
/* 含まれているデータを列挙 */
json_start_foreach loop_var  //ループのカウント用の変数を作成
repeat
    // 全ての要素を列挙し終わるとforeach_object()は0を返す
    if (foreach_object(data, key, val,loop_var) = 0) : break 
    print key + " => " + val
loop
```

[雑に書いたドキュメント](docs/index.md)
## めんどくさくて実装してないリスト
### 数値
- 数値の指数表記（例：`8.984e+8`）
### 文字列
- `\uXXXX`リテラル（Unicode文字）
### Object/Array
- 要素の削除
- 内容も含めたクローン
### その他
- JSONの整形