# GitHub 社群預覽圖（1280×640）生成指南

原則：**文字不要交給圖像模型**（容易出現錯字、字形破碎）。只生成背景，
再用程式碼或 Figma 疊上字體，這種兩階段做法是正本。趕時間可以用 B 方案（一次生成）。

基準是已提交的 `assets/social-preview.png`。下表是**從該檔案實測的數值**，
重新生成時照這組數值重現。重新生成之後要再實測一次並更新此表。

## 實測疊字規格（1280×640 PNG，2026-10-23 台灣版）

背景由 GPT Image 生成（下方提示詞），文字以 Pillow 疊上。每行字級以下表為上限，
寬度超過 640px 就縮小，讓文字停在燃燒文件（約 x 720）左側。

| # | 文字 | 墨跡框 (y) | 字級 | 墨跡框 (x) | 字體 | 顏色 |
|---|---|---|---|---|---|---|
| 1 | `fire-your-seo-agency-tw` | 198–250 | 56px | 75–714 | SF Pro Bold | `#F6F7F9` |
| 2 | `SEO 代操 · GEO 代操 · 「AI 搜尋優化」顧問` | 289–319 | 31px | 73–709 | 蘋方-繁 Semibold | `#F7941E` |
| 3 | `每月數萬元的工作，交給 AI agent` | 339–377 | 36px | 73–622 | 蘋方-繁 Medium | `#F6F7F9` |
| 4 | `SEO · AEO · GEO · LLMO · TW` | 397–420 | 29px | 73–520 | 蘋方-繁 Medium | `#AEB8C7` |
| 5 | `github.com/lunkerchen/fire-your-seo-agency-tw` | 544–567 | 23px | 73–713 | SF Mono Regular | `#6B7A90` |

- 左側靠左對齊（第 1 行 x=75，其餘 x=73）；背景圖案在右側，不要和文字重疊
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
