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
p3 : ループ用変数（→json_start_foreach）
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
insertPrimitiveValue module, "key", p1

module : Objectが入ってるモジュール型変数。
"key" : 値のキー。
p1 : 入れる値
```

### 中身が空のObjectを入れる
```
insertMap module, "key"

module : Objectが入ってるモジュール型変数。
"key" : 値のキー。
```
```
insertMapR module, "key", p1

module : Objectが入ってるモジュール型変数。
"key" : 値のキー。
p1 : 追加したMapへの参照が入る変数
```
Q. Rがついてないやつとついてるやつの違いは？  
A. 追加した値を参照する変数が帰ってくるか

### 中身が空のArrayを入れる
```
insertArray module, "key"

module : Objectが入ってるモジュール型変数。
"key" : 値のキー。
```
```
insertArray module, "key", p1

module : Objectが入ってるモジュール型変数。
"key" : 値のキー。
p1 : 追加したMap
```
Q. Rがついてないやつとついてるやつの違いは？  
A. 上に同じ
