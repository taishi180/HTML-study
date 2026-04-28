# Lesson 02 — CSS基礎

> **作業フォルダ**: `exercises/lesson02/`
> **作成するファイル**: `index.html` と `style.css`

---

## CSSとは？

CSS（Cascading Style Sheets）は、HTMLの **見た目** を整える言語です。
HTMLが「構造」を担当し、CSSが「デザイン」を担当します。

---

## Step 1 — CSSファイルを作って読み込む

CSSは **別ファイル** に書いて、HTMLから読み込むのが基本です。

### まずファイルを2つ作ろう

`exercises/lesson02/` に以下の2つのファイルを作成してください。

**index.html**

```html
<!DOCTYPE html>
<html lang="ja">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>CSS基礎レッスン</title>
  <link rel="stylesheet" href="style.css">
</head>
<body>

  <h1>CSS基礎レッスン</h1>
  <p>CSSでこのページの見た目を変えていきます。</p>

  <h2>自己紹介</h2>
  <p>私はWeb制作を勉強中です。</p>

  <h2>リストの例</h2>
  <ul>
    <li>HTML</li>
    <li>CSS</li>
    <li>JavaScript</li>
  </ul>

  <div class="box">ボックスA</div>
  <div class="box">ボックスB</div>

  <div class="card">
    <h2>カードタイトル</h2>
    <p>カードの説明文がここに入ります。</p>
  </div>

</body>
</html>
```

**style.css**（最初は空でOK）

```css
/* ここにCSSを書いていきます */
```

> **ポイント**: `<link rel="stylesheet" href="style.css">` の1行が、HTMLとCSSをつなぐ大事な部分です。

### CSSの書き方

```css
タグ名 {
  プロパティ: 値;
}
```

例えば「すべての `<h1>` の文字色を紺色にする」なら：

```css
h1 {
  color: navy;
}
```

---

## Step 2 — 文字の色とサイズを変える

`style.css` に以下を書いて保存してください。

```css
h1 {
  color: #333;
  font-size: 28px;
}

p {
  color: #555;
  font-size: 16px;
}
```

保存してブラウザを確認しましょう。文字の色とサイズが変わっていればOKです。

### よく使うプロパティ

| プロパティ | 意味 | 例 |
|-----------|------|-----|
| `color` | 文字の色 | `color: red;` |
| `font-size` | 文字の大きさ | `font-size: 20px;` |

### 色の指定方法

```css
color: red;           /* 色の名前 */
color: #ff0000;       /* 16進数（HEX） ← よく使う */
color: #333;          /* 短縮形（#333333と同じ） */
```

> **実務では `#333` のような16進数** をよく使います。

### やってみよう

`h1` の色を好きな色に変えてみましょう。（例：`#e74c3c` は赤系、`#3498db` は青系）

---

## Step 3 — 背景色をつける

```css
body {
  background-color: #fafafa;
}
```

`body` に薄いグレーの背景をつけました。
他の要素にも背景色をつけてみましょう。

```css
h1 {
  color: white;
  background-color: #2c3e50;
  padding: 16px;
}
```

> `padding` は「内側の余白」です。次のStepで詳しく学びます。
> ここでは「文字と背景の端の間にスペースを作る」と覚えてください。

### やってみよう

`h1` の背景色を好きな色に変えてみましょう。

---

## Step 4 — クラスで特定の要素だけスタイルを変える

ここまでは `h1` や `p` など **タグ名** でスタイルを指定してきました。
でも「この `<div>` だけ色を変えたい」という場面があります。

そんなとき使うのが **クラス** です。

### HTMLでクラスをつける

```html
<div class="box">ボックスA</div>
```

`class="box"` がクラスです。

### CSSでクラスを指定する

クラス名の前に **`.`（ドット）** をつけます。

```css
.box {
  background-color: #3498db;
  color: white;
  padding: 16px;
  margin-bottom: 8px;
}
```

これで `class="box"` がついた要素だけにスタイルが当たります。

> **クラスの良いところ**: 同じクラスを複数の要素につけられるので、スタイルを使い回せます。

### やってみよう

`index.html` の `<p>` タグに `class="highlight"` を1つ追加して、
`style.css` で `.highlight` に背景色 `#fffde7`（薄い黄色）をつけてみましょう。

---

## Step 5 — 余白（margin と padding）

CSSでは、すべての要素は **箱（ボックス）** として扱われます。
箱には2種類の余白があります。

```
┌─────────────── margin（外側の余白：他の要素との間隔）
│  ┌──────────── border（枠線）
│  │  ┌───────── padding（内側の余白：中身と枠の間隔）
│  │  │         │
│  │  │  中身   │
│  │  │         │
│  │  └───────── padding
│  └──────────── border
└─────────────── margin
```

### padding（内側の余白）

```css
.box {
  padding: 20px;          /* 上下左右すべて 20px */
  padding: 10px 20px;     /* 上下 10px、左右 20px */
}
```

### margin（外側の余白）

```css
.box {
  margin-bottom: 16px;    /* 下の要素との間隔 */
}

.card {
  margin: 20px;           /* 上下左右すべて 20px */
}
```

### やってみよう

`.box` の `padding` を `40px` に変えて、余白が広がるのを確認してみましょう。

---

## Step 6 — 枠線と角丸

### 枠線（border）

```css
.card {
  border: 1px solid #ddd;
}
```

`border` は `太さ 種類 色` の順に書きます。

| 種類 | 意味 |
|------|------|
| `solid` | 実線 |
| `dashed` | 破線 |

### 角丸（border-radius）

```css
.card {
  border: 1px solid #ddd;
  border-radius: 8px;
  padding: 20px;
  margin-bottom: 16px;
}
```

`border-radius` の値を大きくするほど角が丸くなります。

### やってみよう

`.card` に `border-radius: 20px` を指定して、角がさらに丸くなるのを確認しましょう。

---

## 練習問題

Lesson 01 で作った自己紹介ページに CSS を適用してみましょう。

1. `exercises/lesson01/` に `style.css` を新しく作成
2. `index.html` の `<head>` 内に `<link rel="stylesheet" href="style.css">` を追加
3. 以下のスタイルを適用してみましょう

### チェックリスト

- [ ] `body` に背景色を設定
- [ ] `h1` に文字色と背景色を設定
- [ ] `p` の文字色と文字サイズを設定
- [ ] クラスを1つ使ってスタイルを適用（好きな要素に）
- [ ] 何か1つに `border` と `border-radius` をつける

---

次のレッスン → **`03_Flexbox.md`**
