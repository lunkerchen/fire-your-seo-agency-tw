# GitHub 社群預覽圖（1280×640）生成指南

原則：**文字不要交給圖像模型**（容易出現錯字、字形破碎）。只生成背景，
再用程式碼或 Figma 疊上字體，這種兩階段做法是正本。趕時間可以用 B 方案（一次生成）。

基準是已提交的 `assets/social-preview.png`。下表是**從該檔案實測的數值**，
重新生成時照這組數值重現。重新生成之後要再實測一次並更新此表。

> 注意：目前已提交的 PNG 仍是上游的文字（`fire-your-seo-agency`、韓文標語、`NEO(Naver)`、
> `github.com/leopard627/...`），尚未換成台灣版。必須依下表的台灣版文字重新生成後覆蓋；
> 下表的位置與字級沿用上游實測值，換成中文後須重新實測。

## 實測疊字規格（1280×640 PNG）

| # | 文字（台灣版） | 墨跡框 (y) | 大寫高度 | 左側 x | 顏色 |
|---|---|---|---|---|---|
| 1 | `fire-your-seo-agency-tw` | 198–262 | 65px | 75 | `#F6F7F9` |
| 2 | `SEO 代操 · GEO 代操 · 「AI 搜尋優化」顧問` | 289–316 | 28px | 73 | `#F7941E` |
| 3 | `每月數萬元的工作，交給 AI agent` | 339–364 | 26px | 73 | `#F6F7F9` |
| 4 | `SEO · AEO · GEO · LLMO · TW` | 397–417 | 21px | 73 | `#AEB8C7` |
| 5 | `github.com/lunkerchen/fire-your-seo-agency-tw` | 544–563 | 20px | 73 | `#6B7A90` |

- 字級約等於大寫高度 ÷ 0.72：第 1 行約 90px、第 2 行約 39px、第 3 行約 36px、第 4 行約 29px、第 5 行約 28px
- 左側 73px 靠左對齊。背景圖案（燃燒的文件、放大鏡）放在右側，不要和文字重疊
- 第 3 行的價格描述要和兩份 README 一起改，只改一邊會讓說法不一致

## 背景提示詞（Midjourney／DALL-E／Stable Image 通用）

```
A dramatic dark navy tech background (deep #0D2137 to near-black gradient),
a single burning orange-red flame emerging from a paper invoice document
that is dissolving into small glowing data particles and search-bar icons,
subtle grid of faint chart lines in the far background, cinematic rim light,
high contrast, minimal composition with empty space on the left 60% for text,
no letters, no words, no typography, 16:9
```

## 重新生成之後（必做）

```bash
python3 tools/optimize_assets.py            # 無損重新壓縮（像素有變就拒絕）
python3 tools/validate.py                   # 檢查 1280×640、體積預算、README 嵌入
```

- 合成結果要**放大到原始尺寸逐字檢查**，中文錯字或字形破碎在縮小圖上看不出來
- 存成 1280×640 的 PNG，提交前兩個指令都要通過（CI 也跑同樣的檢查）

## B 方案：一次生成（連英文字也交給模型的快速版）

```
Minimal GitHub social preview banner, 1280x640, dark navy background,
huge bold white monospace text "fire-your-seo-agency-tw" centered-left,
a small orange flame icon replacing the hyphen dot, subtitle line in amber
"SEO · AEO · GEO · LLMO · TW", clean flat vector style, subtle noise texture,
professional developer-tool aesthetic
```

注意：B 方案連英文也可能拼錯，生成後一定要逐字檢查。中文字絕對不要放進去。

## Logo（正方形頭像）用

```
Flat vector logo icon, a stylized flame formed by a magnifying glass handle,
orange-red gradient flame (#ED1C24 to #F7941E) on deep navy circle background,
minimal, bold silhouette, no text, app-icon style, centered
```
