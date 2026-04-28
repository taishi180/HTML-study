# Lesson 04 ヒント集

困ったときにこのファイルを見てください。
**まずは自分で考えてから見るのがおすすめです！**

---

## 使える画像一覧

| ファイルパス | 内容 |
|-------------|------|
| `img/logo.png` | TeamOCAのロゴ |
| `img/about.jpg` | About用の背景画像（チャレンジ用） |
| `img/member/member_01.jpeg` | メンバー1の画像 |
| `img/member/member_02.jpeg` | メンバー2の画像 |
| `img/member/member_03.jpeg` | メンバー3の画像 |
| `img/member/member_04.jpeg` | メンバー4の画像 |
| `img/game/game_01.jpeg` | ゲーム1の画像 |
| `img/game/game_02.jpeg` | ゲーム2の画像 |

---

## ヒント① ヘッダーのHTML

```html
<div class="header">
  <img src="img/logo.png" alt="TeamOCAロゴ" width="80">
  <div class="header-nav">
    <a href="#">news</a>
    <a href="#">schedule</a>
    <a href="#">shop</a>
  </div>
</div>
```

---

## ヒント② AboutのHTML

```html
<div class="about">
  <h1>TeamOCA</h1>
  <p>チームの説明文をここに書こう</p>
</div>
```

---

## ヒント③ メンバー1人分のHTML

```html
<div class="member">
  <img src="img/member/member_01.jpeg" alt="メンバー1">
  <p>member 1</p>
</div>
```

これを `.member-list` の中に4人分並べよう。

---

## ヒント④ Flexboxで横並びにするCSS

```css
.member-list {
  display: flex;
  justify-content: center;
  gap: 24px;
}
```

この3行で横並び＋中央寄せ＋隙間ができる！

---

## ヒント⑤ 画像を丸くするCSS

```css
.member img {
  width: 150px;
  height: 150px;
  border-radius: 50%;
  object-fit: cover;
}
```

- `border-radius: 50%` → 丸くなる
- `object-fit: cover` → 画像が歪まない

---

## ヒント⑥ 背景色の参考カラーコード

| 色 | コード | 用途の例 |
|----|--------|---------|
| 暗い紺 | `#0f1923` | bodyの背景 |
| やや明るい紺 | `#1a2a3a` | ヘッダー・フッターの背景 |
| 白 | `white` | メインの文字色 |
| 薄いグレー | `#aaa` | 説明文の文字色 |
| もう少し薄いグレー | `#ccc` | ナビリンク・メンバー名の文字色 |
| 暗いグレー | `#888` | フッターの文字色 |

---

## ヒント⑦ よく使うCSSプロパティ早見表

| やりたいこと | プロパティ | 例 |
|------------|-----------|-----|
| 横並びにする | `display: flex` | `.header { display: flex; }` |
| 両端に寄せる | `justify-content: space-between` | ロゴ←→ナビ |
| 中央に寄せる | `justify-content: center` | メンバー一覧 |
| 縦方向の中央 | `align-items: center` | ヘッダー内 |
| 隙間を入れる | `gap: 24px` | アイテム間 |
| 折り返す | `flex-wrap: wrap` | 画面が狭いとき |
| 中央寄せ（テキスト） | `text-align: center` | 見出し |
| 内側の余白 | `padding: 40px` | セクション |
| 下線を消す | `text-decoration: none` | リンク |
| 角を丸くする | `border-radius: 8px` | カード・画像 |

---

## 完成イメージ

```
┌──────────────────────────────────────────┐
│  [ロゴ]              news schedule shop  │
├──────────────────────────────────────────┤
│                                          │
│              TeamOCA                     │
│         チームの説明文                    │
│                                          │
├──────────────────────────────────────────┤
│               MEMBER                     │
│    (丸画像) (丸画像) (丸画像) (丸画像)     │
│   member1  member2  member3  member4     │
├──────────────────────────────────────────┤
│             GAME TITLE                   │
│       [ゲーム画像]  [ゲーム画像]           │
│        GAME 1       GAME 2              │
├──────────────────────────────────────────┤
│              CONTACT                     │
│       お問い合わせはこちら                 │
├──────────────────────────────────────────┤
│          © 2026 TeamOCA                  │
└──────────────────────────────────────────┘
```
