---
theme: '@ktym4a/slidev-theme-ktym4a'
title: 易讀程式之美學
author: Juju Chu
date: 2026-04-23
slide-number: true
---

# 易讀程式之美學

Juju Chu

2026/04/23

---

# 關於
- 原文書名：The Art of Readable Code
- 作者：Dustin Boswell、Trevor Foucher
- 出版社：歐萊禮
<img src="/assets/the-art-of-readable-code.jpg" class="max-h-[45vh] mx-auto mt-4 object-contain" />

---

# 本書目標
- 協助讀者改善程式碼
- 希望本書能對讀者日常的程式設計工作有所助益，願意推薦給團隊其他成員

---

# 本書主題
- 介紹如何寫出有高度可讀性的程式碼
- 程式碼必需易於理解
- 撰寫程式碼時應將他人理解程式碼所需的時間縮到最短

---
layout: center
class: text-center
---

這本書避開了程式語言的進階特性  
即使不熟悉這些程式語言的讀者  
也能夠輕易理解內容  
（畢竟，可讀性概念大多與程式語言本身無關）

---

# 四個層面
- 第一部分：表層改善
- 第二部分：簡化迴圈與邏輯
- 第三部分：重新組織程式碼
- 第四部分：精選主題

---
layout: center
class: text-center
---

# 第一部分 表層改善

---

# 富含資訊的名稱 1/2
1. 使用特定詞彙  
   - 例如 `fetch` 或 `download` 可能比 `get` 更好
2. 避免通用名稱  
   - 例如 `tmp`、`retval`
3. 使用具體名稱  
   - 例如 `DISALLOW_COPY_AND_ASSIGN` 可能比 `DISALLOW_EVIL_CONSTRUCTOR` 更好

---

# 富含資訊的名稱 2/2
4. 在名稱中加入重要細節  
   - 例如在代表毫秒的變數字尾加上 `_ms`
5. 在較大的範圍使用較長的名稱  
   - 應含有讀者理解所需的資訊
6. 有意義的使用大寫、底線等符號

---

# 不被誤解的名稱
```txt
printf integer_range(start=0, stop=4)
```

<table class="w-full table-fixed text-center">
  <thead>
    <tr>
      <th style="text-align: center;">0</th>
      <th style="text-align: center;">1</th>
      <th style="text-align: center;">2</th>
      <th style="text-align: center;">3</th>
      <th style="text-align: center;">4</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>start</td>
      <td></td>
      <td></td>
      <td>stop?</td>
      <td>stop?</td>
    </tr>
  </tbody>
</table>

---

# 不被誤解的名稱
```txt
printf integer_range(first=0, last=4)
```

<table class="w-full table-fixed text-center">
  <thead>
    <tr>
      <th style="text-align: center;">0</th>
      <th style="text-align: center;">1</th>
      <th style="text-align: center;">2</th>
      <th style="text-align: center;">3</th>
      <th style="text-align: center;">4</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>first</td>
      <td></td>
      <td></td>
      <td></td>
      <td>last</td>
    </tr>
  </tbody>
</table>

---

# 不被誤解的名稱
```txt
printf integer_range(begin=0, end=4)
```

<table class="w-full table-fixed text-center">
  <thead>
    <tr>
      <th style="text-align: center;">0</th>
      <th style="text-align: center;">1</th>
      <th style="text-align: center;">2</th>
      <th style="text-align: center;">3</th>
      <th style="text-align: center;">4</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>begin</td>
      <td></td>
      <td></td>
      <td></td>
      <td>end</td>
    </tr>
  </tbody>
</table>

---

# 美學
- 以一致有意義的方式排版，能讓程式碼更容易閱讀
- 讓有相似行為的程式碼有相同的剪影
- 挑個有意義的順序並堅守這個順序
- 利用空白行將大區塊切割成有邏輯意義的「段落」

---

# 認識註解
- 註解為何（why）而非什麼（what）或如何（how）
- 範例，先直接打出自己的 OS：
```txt
// 天阿，如果串列裡出現重複，情況就會十分棘手
```

---

# 認識註解
- 註解為何（why）而非什麼（what）或如何（how）
- 範例，先直接打出自己的 OS：
```txt
// 「天阿」，如果串列裡出現重複，情況就會十分棘手
// 注意，
```

---

# 認識註解
- 註解為何（why）而非什麼（what）或如何（how）
- 範例，先直接打出自己的 OS：
```txt
// 天阿，如果串列裡出現重複，「情況」就會十分棘手
// 注意，程式碼無法處理串列中的重複
```

---

# 認識註解
- 註解為何（why）而非什麼（what）或如何（how）
- 範例，先直接打出自己的 OS：
```txt
// 天阿，如果串列裡出現重複，情況就會「十分棘手」
// 注意，程式碼無法處理串列中的重複（因為太難實作）
```

---

# 認識註解

| 標記 | 意義 |
|---|---|
| TODO: | 作者還沒處理 |
| FIXME: | 已知的問題 |
| HACK: | 承認解決方法不夠優雅 |
| XXX: | 危險！重要問題 |

---

# 認識註解
- 不需要的註解：
  - 能由程式碼快速推導的事實
  - 「輔助註解」應直接修正程式碼
- 應記錄的想法：
  - 選用特定寫法的原因
  - 程式碼中的缺陷（使用如 `TODO:` 或 `XXX:` 等標記）
  - 常數使用特定數值的原因

---

# 認識註解
- 為使用者設身處地：
  - 將使用者會對程式碼想不透的部分加上註解
  - 記錄一般使用者預期之外的情況
  - 在檔案或類別層級加上「全局」註解，解釋各部分交互運作方式
  - 摘要程式碼區塊，避免使用者深陷細節當中

---
layout: center
class: text-center
---

# 第二部份 簡化迴圈與邏輯

---

# if / else 區塊順序
- 先處理 `肯定` 條件，例如用 `if (debug)` 而非 `if (!debug)`
- 先處理 `簡單` 的情況
- 先處理比較 `有趣` 或 `明顯` 的情況
<img src="/assets/if-else.png" class="h-[33vh] ml-auto mt-4 object-contain" />

---

# 提高控制流程可讀性
- 撰寫比較時，將 `會變動` 的數值放在左側，較 `固定不變` 的數值放右側
- 巢狀程式區塊需要更多心力才能理解，盡可能使用「線性」程式流程
- `儘早返回` 能夠清除巢狀結構並讓程式碼更為簡潔

---

# 解釋性變數
例如：
```txt
if line.split(':')[0].strip() === "root"
```

---

# 解釋性變數
例如：
```txt
if line.split(':')[0].strip() === "root"
```

加入解釋性變數的版本：
```txt
username = line.split(':')[0].strip()
if username === "root"
```

---

# 摘要變數
例如：
```txt
if (request.user.id === document.owned_id) { // 使用者可以編輯這份文件 ... }
if (request.user.id !== document.owned_id) { // 文件狀態是唯獨 ... }
```

---

# 摘要變數
例如：
```txt
if (request.user.id === document.owned_id) { // 使用者可以編輯這份文件 ... }
if (request.user.id !== document.owned_id) { // 文件狀態是唯獨 ... }
```

加入摘要變數的版本：
```txt
final boolean user_owns_document = (request.user.id === document.owned_id)
if (user_owns_document) { // 使用者可以編輯這份文件 ... }
if (!user_owns_document) { // 文件狀態是唯獨 ... }
```

---

# 笛摩根定律
例如：
```txt
if ( !(a && !b) )  改寫成  if (!a || b)
```

---

# 縮限變數的範圍
- 有效減少使用者同時需要記得的變數數量
  - 避免使用全域變數
  - 儘可能減少可看到變數的程式碼行數
  - 儘量使用只寫入一次的變數，例如 `const`

---
layout: center
class: text-center
---

# 第三部分 重新組織程式碼

---

# 重組
- 工程就是將大問題分解成小問題…也更易於閱讀
- 單獨處理較小的函數，比較容易 `加入新功能`、`改善可靠度` 以及 `處理邊界情況` 等
- 分離工作於不同段落的好處是彼此 `互相獨立` —— 讀任何一個段落時不需要考慮其他段落的情況

---

# 將想法轉化為程式碼
- 用口語描述程式行為再轉為程式碼，有助寫出更自然的程式碼
- 讀描述行為的文字與語句也有助於找出應該分解的子問題
- 這個技巧一般成為「橡膠鴨」（rubber ducking）

---
layout: center
class: text-center
---

# 第四部份 精選主題

---

# 測試與可讀性
- 讓測試更易閱讀：對使用者隱藏不重要的細節（建立輔助函式），突顯重要的細節
- 選擇良好的測試輸入資料：能完整測試程式碼，且簡單易閱讀
- 簡化輸入值：優先使用 `簡單`、`明確` 但能 `達到測試效果`的輸入值
- 測試函數的命名：不要害怕使用長又繁複的名稱
- 測試失敗的訊息要足夠清楚：要對進一步除錯有幫助

---

# 測試友善的開發
- 如果寫程式的時候就知道稍後得寫測試程式，就會發生十分有趣的情況：
  - 會開始將程式設計得很容易被測試
  - 這一般也代表寫出較好的程式碼
  - 測試友善的設計幾乎都能產生組織良好的程式碼，不同的部份負責不同的工作

---

# 較少測試程式的特質及對設計造成的問題

| 特徵 | 可測性問題 | 設計問題 |
|---|---|---|
| 使用全域變數 | 每次測試都需重設所有全域狀態 | 各函數無法單獨考慮 |
| 依賴大量外部元件的程式碼 | 幾乎無法寫測試<br>因為需要太多的設定過程 | 很難知道任何變動造成的影響<br>更難重構類別<br>系統需要考慮更多失效模式以及回覆的方法 |
| 行為不確定的程式 | 測試很容易無效也不夠可靠 | 程式容易產生難以重現的 bug<br>bug 難追蹤與修正 |

---

# 高可測試性程式的特質及產生的良好設計

| 特徵 | 可測性問題 | 設計優點 |
|---|---|---|
| 類別有較少內部狀態 | 測試較易寫<br>測試方法時需要較少設定<br>只需驗證少量的隱藏狀態 | 狀態較少的類別較簡單好懂 |
| 類別 / 函數只做一件事 | 完整測試需較少測試案例 | 模組化 |
| 類別與較少類別相依 | 能獨立測試每個類別 | 系統能平行開發 |
| 函數有簡單、定義良好的介面 | 有定義明確的行為可供測試 | 較可能被重複使用 |

---
layout: center
class: text-center
---

# 心得

---

# 心得
- 簡單好讀，覺得讀完有提升自己對程式碼的美感
- 在 coding 時會多一層思考
- 命名時會更留意

---
layout: center
class: text-center
---

完成！
謝謝收聽

<style>
.slidev-code {
  font-size: 10px !important;
}
</style>