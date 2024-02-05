# json-hsp
それなりに使えるHSPのJSONライブラリ

## example
```hsp
/* パースして、変数dataに一番上の階層の値を代入 */
newmod parser, JSON, JSON_CRATE_PARSE, {"{
    "name" : "Taro",
    "age" : 13 
}"}
get@JSON parser, data
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
## めんどくさくて実装してないリスト
### 数値
- 数値の指数表記（例：`8.984e+8`）
### 文字列
- `\uXXXX`リテラル（Unicode文字）
### 他の値
- nullとbool型
### その他
- JSONの整形