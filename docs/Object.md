# Object
値をキーと1対1で保持するやつです。

## 単体で使う
単体で使う場合は、`newmod`で作成することができます。
```hsp
newmod map, JSON_Object
```

## 固有の命令・関数
### 値を読み出す
```
get@JSON_Object module, p1, "key"

module : Objectが入ってるモジュール型変数。
p1 : "key"に対応する値が代入される変数
"key" : キー
```

### 値を全部見る
```
v = foreach_object(module, p1, p2, p3)

module : Objectが入ってるモジュール型変数。
p1 : キーが代入される変数
p2 : 値が代入される変数
p3 : ループ用変数（→[json_start_foreach](./index.md#内容の走査準備)）
戻り値 : 値が読み出せれば0、読み出せなければ（全て読みだしたら）1
```
```hsp
json_start_foreach a
repeat 
if (foreach_object(module, key, value, a) = 1) : break
//...
loop
```
みたいな感じで使うと思われる



### 普通の型の値を入れる
```
insert_normal module, "key", p1

module : Objectが入ってるモジュール型変数。
"key" : 値のキー。
p1 : 入れる値
```

### 普通じゃない型の値を入れる
```
insert_special module, "key", p1

module : Objectが入ってるモジュール型変数。
"key" : 値のキー。
p1 : 入れる型の種類
```
p1は[型を表す定数](./index.md#型を表す定数)に対応しています。

例；変数moduleに入ったObjectにキー"a"にtrueを代入する
```
insert_special module, "a", JSON_TYPE_TRUE
```