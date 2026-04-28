# Lesson 03 — Flexbox

> **作業フォルダ**: `exercises/lesson03/`
> **作成するファイル**: `index.html` と `style.css`

---

## Flexbox とは？

Flexbox は、要素を **横並び** にしたり、**中央寄せ** したりできるCSSの機能です。
これを使えば、カードを並べたり、ナビゲーションを作ったりするのが簡単になります。

---

## Step 1 — display: flex で横並びにする

### ファイルを準備しよう

`exercises/lesson03/` に以下の2つのファイルを作成してください。

**index.html**

```html
<!DOCTYPE html>
<html lang="ja">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Flexboxレッスン</title>
  <link rel="stylesheet" href="style.css">
</head>
<body>

  <h1>Flexbox レッスン</h1>

  <h2>横並びにする</h2>
  <div class="container">
    <div class="item">1</div>
    <div class="item">2</div>
    <div class="item">3</div>
  </div>

</body>
</html>
```

**style.css**

```css
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  padding: 40px;
  font-family: sans-serif;
  background-color: #f5f5f5;
}

h1 {
  margin-bottom: 24px;
}

h2 {
  margin-top: 32px;
  margin-bottom: 12px;
}

.container {
  background-color: #e0e0e0;
  padding: 10px;
}

.item {
  background-color: #3498db;
  color: white;
  padding: 20px 30px;
  text-align: center;
  font-weight: bold;
  font-size: 18px;
}
```

保存してブラウザで確認してください。アイテムが **縦に並んで** いるはずです。

### Flexbox を有効にする

`.container` に1行追加するだけで横並びになります。

```css
.container {
  background-color: #e0e0e0;
  padding: 10px;
  display: flex;
}
```

**たった `display: flex` の1行で横並びになります！**

`display: flex` を指定した要素が **親（コンテナ）** で、
その中の要素が **子（アイテム）** になります。

### やってみよう

`index.html` にアイテムを2つ増やして（4と5を追加）、横に5つ並ぶのを確認しましょう。

---

## Step 2 — justify-content（横方向の配置）

横並びになったアイテムを、中央に寄せたり、均等に配置したりできます。

`index.html` の `<body>` に以下を追加してください。

```html
<h2>中央寄せ</h2>
<div class="container jc-center">
  <div class="item">1</div>
  <div class="item">2</div>
  <div class="item">3</div>
</div>

<h2>両端に配置</h2>
<div class="container jc-between">
  <div class="item">1</div>
  <div class="item">2</div>
  <div class="item">3</div>
</div>

<h2>均等に配置</h2>
<div class="container jc-evenly">
  <div class="item">1</div>
  <div class="item">2</div>
  <div class="item">3</div>
</div>
```

`style.css` に以下を追加：

```css
.jc-center  { justify-content: center; }
.jc-between { justify-content: space-between; }
.jc-evenly  { justify-content: space-evenly; }
```

### 図解

```
左寄せ（デフォルト）: [1][2][3]
center:                    [1][2][3]
space-between:       [1]       [2]       [3]
space-evenly:          [1]    [2]    [3]
```

> **space-between** は「ロゴ ←→ メニュー」のように両端に寄せたいときに便利です。

### やってみよう

`justify-content: center` の部分を `space-between` に変えて、見た目の違いを確認しましょう。

---

## Step 3 — align-items: center（縦方向の中央寄せ）

`align-items` を使うと、アイテムを **縦方向** に中央寄せできます。

`index.html` に追加：

```html
<h2>縦方向の中央寄せ</h2>
<div class="container center-both">
  <div class="item">中央!</div>
</div>
```

`style.css` に追加：

```css
.center-both {
  justify-content: center;
  align-items: center;
  height: 200px;
}
```

これで要素が **横にも縦にも中央** に配置されます。

> **この3つのプロパティの組み合わせは超頻出！ 覚えておきましょう。**
> ```css
> display: flex;
> justify-content: center;
> align-items: center;
> ```

---

## Step 4 — gap（アイテム間の隙間）

アイテム同士にスペースを入れたいとき、`gap` を使います。

`index.html` に追加：

```html
<h2>gap で隙間を入れる</h2>
<div class="container gap-demo">
  <div class="item">1</div>
  <div class="item">2</div>
  <div class="item">3</div>
  <div class="item">4</div>
</div>
```

`style.css` に追加：

```css
.gap-demo {
  gap: 16px;
}
```

> `margin` で間隔を作るよりも `gap` のほうが簡単です。

### やってみよう

`gap` の値を `4px`、`16px`、`40px` と変えて、隙間の広さの違いを見てみましょう。

---

## Step 5 — flex-wrap（折り返し）

アイテムが多くてコンテナに収まらないとき、**折り返す** ことができます。

`index.html` に追加：

```html
<h2>折り返しなし（デフォルト）</h2>
<div class="container nowrap-demo">
  <div class="item wide">1</div>
  <div class="item wide">2</div>
  <div class="item wide">3</div>
  <div class="item wide">4</div>
  <div class="item wide">5</div>
</div>

<h2>折り返しあり</h2>
<div class="container wrap-demo">
  <div class="item wide">1</div>
  <div class="item wide">2</div>
  <div class="item wide">3</div>
  <div class="item wide">4</div>
  <div class="item wide">5</div>
</div>
```

`style.css` に追加：

```css
.item.wide {
  min-width: 200px;
}

.nowrap-demo {
  /* デフォルト：折り返さない（はみ出す） */
}

.wrap-demo {
  flex-wrap: wrap;
  gap: 12px;
}
```

> **`flex-wrap: wrap` + `gap`** の組み合わせは、カードを並べるときの基本パターンです。

---

## 練習問題

ここまで学んだ Flexbox を使って、**カードを3つ横並びにしたレイアウト** を作ってみましょう。

`exercises/lesson03/index.html` に以下の構造を作ってください。

```
┌───────────────────────────────────┐
│  [カード1]  [カード2]  [カード3]    │
└───────────────────────────────────┘
```

### チェックリスト

- [ ] カードを囲む親要素に `display: flex` を指定
- [ ] `gap` でカード間に隙間を入れる
- [ ] 各カードに背景色・`padding`・`border-radius` をつける
- [ ] カードの中に `<h3>` と `<p>` を入れる

### ヒント

```html
<div class="card-container">
  <div class="card">
    <h3>タイトル</h3>
    <p>説明文</p>
  </div>
  <!-- カードを3つ作る -->
</div>
```

```css
.card-container {
  display: flex;
  gap: 20px;
}

.card {
  background-color: white;
  padding: 20px;
  border: 1px solid #ddd;
  border-radius: 8px;
}
```

---

次のレッスン → **`04_総合課題.md`**
