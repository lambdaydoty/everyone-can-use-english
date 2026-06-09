# 軟體設定

Enjoy 只需要登入後即可直接使用，**無需其他設定**。但是，你仍然可以根據需要做個性化的設定。

開啟 Enjoy 軟體，點選左側欄最下面的齒輪按鈕，即可開啟 `軟體設定`。

## 基本設定

### 母語

請選擇您的母語，預設為`簡體中文`。

請注意，此設定關係到學習過程中的翻譯內容、分析等，並不影響軟體的介面語言。

### 學習語言

請選擇您要學習的語言，預設為 `English(United States)`。

### 語音轉文字服務

::: info 設定路徑
軟體設定 -> 基本設定 -> 語音轉文字服務
:::

語音轉文字（即 STT，Speech to Text）服務是 Enjoy 提供的核心功能之一，也是 [跟讀訓練](./audios.md#跟讀音訊) 的前提條件。

此處設定為預設值，在語音轉文字時仍可選擇不同服務。

<details>
<summary>
本地(whisper)
</summary>

該設定預設項為 `本地`，即利用 Enjoy 整合的 whisper 元件，完全利用本地計算機的算力提供 STT 服務，該服務完全免費。

Enjoy 預設選擇 whisper 模型 `tiny.en`，如果電腦配置較高，可以選用更大的模型以提高語音轉文字的準確度。

::: tip 關於 whisper 模型的選擇
首次使用時，程式會自動下載模型，選擇的模型越大，下載所需要的時間也越長。推薦一般使用 `medium` 以下模型即可。

理論上，模型越大，識別的準確度也更高，但是執行得越慢，甚至在一些配置不高的電腦中無法執行。

凡是以 `.en` 結尾的模型均只支援英文，識別英文準確性也更高，例如 `base.en`；而不以 `.en` 結尾的模型則可以支援多種語言，例如 `base`。
:::

::: warning 檢查本地 whisper 服務
有些電腦或者系統（例如 macOS 11）可能會因為相容性問題（或其他未知問題）無法使用本地的 whisper 服務。點選 `檢查` 按鈕即可檢查 whisper 服務在本地計算機是否工作正常。如果提示無法正常工作，可以選用其他服務。
:::
</details>

<details>
<summary>
Azure AI STT
</summary>

利用微軟 Azure AI 的語音識別 API 服務提供的 STT，該服務為**收費服務**，每次使用均會在 Enjoy 賬戶餘額中扣費，，餘額不足則需要 [充值](#充值) 後才可繼續使用。
</details>

<details>
<summary>
Cloudflare AI STT
</summary>

利用 Cloudflare 提供的 whisper 雲服務，該服務目前免費。經實測，對於一些時長較短的音訊，識別會有較大誤差。
</details>

<details>
<summary>
OpenAI STT
</summary>

利用 OpenAI 提供的 whipser 雲服務，該服務需要[配置自己的 OpenAI 金鑰](#openai-配置)。
</details>

### 文字轉語音服務

::: info 設定路徑
軟體設定 -> 基本設定 -> 文字轉語音服務
:::

文字轉語音（即 TTS，Text to Speech）可以將文字合成為語音，以便於跟讀訓練。此處設定為預設值，在文字轉語音時仍可選擇不同服務。

EnjoyAI 除了提供 OpenAI 的 TTS 服務，還整合了 Azure 的 TTS 服務，語音模型選擇 `azure/speech` 即可。 Azure TTS 提供了更豐富的音色供選擇。

### 預設 AI 引擎

::: info 設定路徑
軟體設定 -> 基本設定 -> 預設 AI 引擎
:::

Enjoy 中提供了很多方便的功能。

預設值為 `Enjoy AI`，由 Enjoy 提供該服務，每次使用均會在賬戶餘額中扣費，餘額不足則需要 [充值](#充值) 後才可繼續使用。EnjoyAI 提供了除 OpenAI 以外，目前流行的熱門模型，使用者可以靈活選用。

如果您配備了可用的 [OpenAI 金鑰](#openai-配置)，也可以將 **預設 AI 引擎** 選為 `OpenAI`。

在預設模型，您還可以對不同的服務選用不同的模型。

## 詞典設定

### 詞典匯入

::: info 設定路徑
軟體設定 -> 詞典設定 -> 詞典匯入
:::

#### 匯入 Enjoy 適配過的詞典

| 詞典名稱 | 語言 | 支援發音 | 檔名 | 大小 |
| -------- | ---- | -------- | ------ | ------ |
| Longman Dictionary of Contemporary English | 英-英 / 英-中 | 是 | ldocd5.zip | 1.63GB |
| Collins COBUILD Advanced British EN-CN Dictionary | 英-中 | 否 | ccalecd.zip | 13.879MB |
| Collins COBUILD Advanced British English Learners Dictionary | 英-英 | 是 | ccabeld.zip | 485.6MB |
| Oxford Dictionary of English | 英-英 | 否 | oxford_en_mac.zip | 33.6MB |
| Korean English Dictionary | 韓-英 | 否 | koen_mac.zip | 52.1MB |
| Japanese English Dictionary | 日-英 | 否 | jaen_mac.zip | 39.8MB |
| German English Dictionary | 德-英 | 否 | deen_mac.zip | 32.1MB |
| Russian English Dictionary | 俄-英 | 否 | ruen_mac.zip | 18.1MB |

::: tip 下載詞典
網盤下載： [連結](https://pan.baidu.com/share/init?surl=zK-dHs40HpfYNUEdoYxZUw)
提取碼: 7975
:::

下載 `zip` 格式的詞典檔案後，點選 `匯入詞典` 按鈕，即可匯入詞典。

#### 匯入 mdx 詞典

mdx 詞典是 mdict 格式的詞典檔案。

如果下載的 mdict 詞典只有一個 `.mdx` 檔案，則可以直接匯入。如果下載的 mdict 詞典包含有多個檔案，匯入時應該選擇所有檔案，包括 `.mdx` `.mdd` `.js` 等檔案。

## 高階設定

### API 設定

設定 Enjoy 服務的 API 地址。預設為 `https://enjoy.bot`。

### 代理設定

為 Enjoy App 設定代理服務。

### 網路狀態

檢查 Enjoy 客戶端與服務端之間的網路狀態。

### OpenAI 配置

::: info 設定路徑
軟體設定 -> 基本設定 -> OpenAI
:::

配置 OpenAI API 金鑰，可以在 [官網](https://platform.openai.com/api-keys) 申請。配置好的 OpenAI 服務可以在 [聊天](./chat.md)等服務中使用。

- 金鑰：OpenAI API 金鑰
- 模型：預設使用的模型
- 介面地址：如果使用的是官方申請的金鑰，則不需要填；否則請根據金鑰提供方的資訊填寫。

::: warning 介面地址
由於 OpenAI 在某些地區不提供服務，有些使用者會使用第三方提供的中轉服務。請務必根據服務提供方的資訊填寫好 **介面地址**。如果使用時出現報錯，可能需要在介面地址結尾加上 `/v1`。
:::

### 重置設定選項

退出登入並將 Enjoy App 的所有設定重置為預設值。

### 重置所有

將退出登入，並刪除所有個人資料。

## 賬戶設定

### 資源庫儲存路徑

::: info 設定路徑
軟體設定 -> 基本設定 -> 資源庫儲存路徑
:::

Enjoy 採用 **本地優先** 的設計原則，大部分資料均儲存在本地，即 **資源庫儲存路徑** 下。
所謂資源庫是一個名為 `EnjoyLibrary` 的資料夾，預設放置在 `My Documents` （即 `我的文件`）下。

隨著 Enjoy 的使用時間增長，資源庫資料夾裡可能會產生比較大的快取檔案，導致佔用空間較大。根據具體需要，你也可以修改資源庫的路徑，例如從 _C 盤_ 改到空間更大的 _D 盤_。

如果已經產生了資料，修改時，可以先把原來的 `EnjoyLibrary` 資料夾複製到目標路徑下，再在 Enjoy 軟體中點`修改`按鈕，選中目標路徑，然後重啟軟體，即可完成修改。

::: tip 資源庫裡都有什麼
開啟 `EnjoyLibrary` 資料夾，你能看到類似以下的目錄結構

```
.
├── 2400xxxx
│   ├── audios
│   │   ├── 0687ae31c4178bbf0466503e56d887f8.mp3
│   │   └── ...
│   ├── enjoy_database.sqlite
│   ├── recordings
│   │   ├── 025542894635903d5ea6f2395cb404c0.wav
│   │   └── ...
│   ├── speeches
│   │   ├── 0687ae31c4178bbf0466503e56d887f8.mp3
│   │   └── ...
│   └── videos
│       ├── 23876d46305bae2e049c691872dd3cde.mkv
│       └── ...
├── cache
│   ├── 0687ae31c4178bbf0466503e56d887f8.json
│   └── ...
├── logs
│   ├── main.log
│   └── main.old.log
├── waveforms
│   ├── 0687ae31c4178bbf0466503e56d887f8.waveform.json
│   └── ...
└── whisper
│   ├── models
│   │   ├── tiny.en.bin
│   │   └── ...
```

- `/2400xxxx/`: 登入的 Enjoy 帳號 ID，該資料夾下的資料均是你使用產生的個人資料
  - `/2400xxxx/audios/`: 新增的音訊檔案
  - `/2400xxxx/speeches/`: TTS 生成的語音檔案
  - `/2400xxxx/videos/`: 新增的影片檔案
  - `/2400xxxx/recordings/`: 錄音檔案
  - `/2400xxxx/enjoy_database.sqlite`: 個人資料庫檔案
- `/cache/`: 使用過程中產生的快取檔案，如果佔用空間過大，可以安全地刪除
- `/logs/`: 儲存軟體執行的日誌，用於幫助開發人員排除故障
- `/waveforms/`: 音影片解碼後的波形資料快取
- `/whisper/models`: 語音轉文字服務軟體 whisper 的模型檔案

:::

::: danger 個人資料安全
`EnjoyLibrary/2400xxxx/` 資料夾下儲存的均為使用 Enjoy 過程中產生的個人資料，請務必**不要刪改**該資料夾下的任何檔案，否則可能會導致資料丟失，或者使得 Enjoy 軟體無法正常執行。

如前文所說，Enjoy 採用本地優先的設計原則，絕大部分資料並沒有上傳雲伺服器，請妥善保管好自己的個人資料。
:::

### 磁碟使用情況

點選 `詳情` 可檢視當前 Enjoy App 資源庫的磁碟使用情況。

點選 `釋放磁碟` 可以批次刪除錄音檔案，釋放磁碟空間。

### 充值

::: info 設定路徑
軟體設定 -> 賬戶設定 -> 餘額
:::

Enjoy 提供了部分收費的 AI 服務，均為 **按使用量收費**，每次使用會在餘額中扣除相應的費用，直到餘額不足，則停止提供該服務。

如果需要繼續使用，請點選 `充值` 按鈕進行充值。

::: danger 充值前須知
需要特別注意的是，充值成功後將在 Enjoy 賬戶的餘額體現，所有餘額僅可作為支付 Enjoy 收費服務使用，**不支援退款**，**不支援提現**。

請謹慎考慮，按需充值。
:::

## 快捷鍵

Enjoy App 可用的快捷鍵，點選鍵位可以修改。

## 外觀

可修改主題和介面語言。

## 關於

當前版本和更新連結。
