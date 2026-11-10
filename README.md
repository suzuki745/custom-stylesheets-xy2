# custom-stylesheets-xy2

## letter.css

和文レター（依頼状・案内状など）を A4 1枚で組むためのスタイル。front matter で
`css: https://suzuki745.github.io/custom-stylesheets-xy2/letter.css` を指定し、
`jaif/scripts/markdown_to_html.cjs` で HTML 化する。

全体を `:::: letter` で囲み、各ブロックを次のクラスで書く。

| クラス | 用途 |
| --- | --- |
| `doc-no` | 文書番号・日付（右寄せ） |
| `addressee` | 宛先 |
| `sender` | 差出人（右寄せ） |
| `#` 見出し / `subject` | 件名（中央・太字） |
| `content` | 本文・注意書き（段落を1字下げ） |
| `kigaki` | 記書きの表（罫線付き。`kigaki no-border` で罫線なし） |
| `contact` | 問い合わせ先（枠囲み・右寄せ） |
| `ki` / `ijo` | 「記」「以上」（`記{.ki}` のように付ける） |
| `right` / `center` / `no-indent` | 行単位の補助（拝啓・【】見出しは `no-indent`） |

```markdown
:::: letter

::: doc-no
原産協発（情報）第8号\
2026年11月　日
:::

# 件名

::: content
拝啓　…{.no-indent}

本文…
:::

敬具{.right}

記{.ki}

::: kigaki
|---|---|
|項目|内容|
:::

以上{.ijo}

::::
```

1枚に収まらないときは、`.letter` に付けた変数で文字サイズや余白を調整する。
`:::: letter` の行にはクラスしか書けないため、変数を変えるときは `<div class="letter" style="--letter-font-size: 10pt">` のように HTML で書く。

| 変数 | 既定値 |
| --- | --- |
| `--letter-font-size` | `10.5pt` |
| `--letter-line-height` | `1.65` |
| `--letter-padding` | `14mm 24mm 8mm` |
| `--letter-gap` | `1em`（ブロック間の間隔） |
