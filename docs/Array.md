# Array
値を数値のインデックスを使って保持するやつです。

## 単体で使う
単体で使う場合は、`newmod`で作成することができます。
```hsp
newmod map, JSON_Array
```

## 固有の命令・関数
### 値を読み出す
```
get@Json_Array module, p1, "key"

module : Objectが入ってるモジュール型変数。
p1 : "key"に対応する値が代入される変数
"key" : キー
```

### 値を全部見る
```
v = foreach_array(module, p1, p2)

module : Objectが入ってるモジュール型変数。
p1 : 値が代入される変数
p2 : ループ用変数（→[json_start_foreach](./index.md#内容の走査準備)）
戻り値 : 値が読み出せれば0、読み出せなければ（全て読みだしたら）1
```
```hsp
json_start_foreach a
repeat 
if (foreach_array(module, value, a) = 1) : break
//...
loop
```
みたいな感じで使うと思われる



### 普通の型の値を入れる
```
push_normal module, p1

module : Objectが入ってるモジュール型変数。
p1 : 入れる値
```
statに作成した値のindexが代入されます。

### 普通じゃない型の値を入れる
```
push_special module, p1

module : Objectが入ってるモジュール型変数。
p1 : 入れる型の種類
```
p1は[型を表す定数](./index.md#型を表す定数)に対応しています。
statに作成した値のindexが代入されます。