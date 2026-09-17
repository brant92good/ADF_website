# 保障音訊安全-探討SpeechPrompt架構於語句深偽偵測任務之突破

國科會大專生研究計畫（計畫編號：114-2813-C-035-061-E）

## 研究報告

**[閱讀完整研究報告（PDF，72 頁）](frontend/public/reports/nstc-114-2813-C-035-061-E-report-20260330.pdf)** · [直接下載](https://raw.githubusercontent.com/brant92good/ADF_website/main/frontend/public/reports/nstc-114-2813-C-035-061-E-report-20260330.pdf)

王兆偉｜指導教授：劉怡芬｜114-2813-C-035-061-E

版本：2026/03/30｜72 頁｜約 5 MB

報告以跨資料集測試比較語音深偽偵測系統，並透過量化方式、可學習群集中心與分類後端的消融實驗，探討聲學表示與偵測表現的關係。

建議閱讀：研究問題（PDF 第 8–10 頁）、跨資料集比較與消融（第 44、47、49–52 頁）、展示系統（第 54–57 頁）、結論與限制（第 58–65 頁）。

## 系統架構

- **前端 (Frontend)**：Next.js 網頁介面，支援音訊上傳、即時錄音與結果顯示
- **後端 (Backend)**：FastAPI + PyTorch 推論服務，以 Docker 容器化部署
- **偵測模型 (Countermeasure Models)**：
  - **W2V-AASIST**：基於 wav2vec 2.0 XLSR（317M 參數）搭配圖神經網路後端
  - **MFA-Conformer**：Conformer 架構，處理 80 維梅爾頻譜特徵
  - **SpeechPrompt v2**：生成式語音語言模型（GSLM），使用 Prompt Tuning 方法
- **語音合成 (TTS)**：IndexTTS2
- **語音辨識 (ASR)**：Whisper

## 快速開始

### 啟動後端服務
```bash
git clone --recursive https://github.com/brant92good/ADF_website.git
cd ADF_website
docker compose up
```

> 注意：需要在 `tts/index-tts/.hf_token` 建立包含 Hugging Face Token 的檔案。

### 啟動前端
```bash
cd frontend
npm install
npm run dev
```

## 授權

本專案僅供學術研究使用。
