
# RetryIX-OpenCL2.0-512B

> 🚀 4MB block encoding with 512B alignment using OpenCL 2.0 + SVM.  
> ✅ Runs on standard OpenCL ICD without ROCm or CUDA dependencies.  
> 🚀 使用 OpenCL 2.0 + SVM 實現 4MB 區塊編碼與 512B 對齊記憶體操作。  
> ✅ 支援 ICD 標準運行，無需依賴 ROCm 或 CUDA。

---

## ✨ Features / 功能特點

- ✅ 4MB 區塊級記憶體編碼 / Block-level memory encoding
- ✅ 512B 對齊記憶體存取 / 512B-aligned memory access
- ✅ 基於 OpenCL 2.0 的共享虛擬記憶體（SVM） / Uses Shared Virtual Memory (SVM)
- ✅ 不含加密或區塊鏈模組 / No cryptographic or blockchain modules
- ✅ 無需 ROCm / CUDA 環境 / No ROCm / CUDA required
- ✅ 相容各類 OpenCL ICD 驅動 / Compatible with OpenCL ICD (Intel, AMD, Mesa)

---

## 📦 Components / 模組構成

| File / 檔案 | Description / 說明 |
|-------------|----------------------|
| `retryix_cli.c` | 指令列工具，可查詢 OpenCL 裝置與參數 / CLI for OpenCL device query |
| `retryix_device_utils.c` | 提取裝置資訊，支援 JSON 輸出 / Device info export with JSON |
| `retryix_host.c` | Host 模組邏輯，支援區塊編碼 / Host logic for block encoding |
| `retryix_runtime.h` | 運行時 API 抽象層 / Runtime abstraction |
| `host_comm.h` | 通訊模組定義（僅限本地使用）/ Local-only communication interface |
| `module_descriptor.h` | 模組註冊與語義標記 / Module registration and tagging |
| `retryix_query_all_resources.c` | 批次查詢所有資源 / Batch resource scanner |

---

## 🧪 Benchmark Support / 基準測試支持

- 4MB 區塊編碼一致性測試 / 4MB block reproducibility
- 512B 對齊 SVM 配置 / 512B-aligned SVM memory usage
- 多平台 ICD 一致執行行為 / Cross-ICD consistency

---

## 🛠️ Build & Run / 編譯與執行

### Requirements / 需求
- OpenCL 2.0 相容平台 / OpenCL 2.0 compatible platform
- ICD 環境（Intel/AMD/Mesa） / OpenCL ICD
- C 編譯器（GCC / Clang） / C compiler (GCC / Clang)

### Build 範例
```bash
gcc retryix_cli.c retryix_device_utils.c retryix_host.c -lOpenCL -o retryix_cli
```

### Run 執行
```bash
./retryix_cli
```

---

## ⚠️ No Blockchain / 無區塊鏈依賴

本專案未使用任何區塊鏈、加密、分散式架構。  
所有模組皆為本地 C 語言實作，專為開源與重現性設計。

This project includes no blockchain, crypto, or decentralized tech.  
All modules are pure local C-level implementations.

---

## 📜 License / 授權條款

Dual License / 雙授權：
- 🧪 學術 / 研究用途：免費 / Academic & Research Use: Free
- 🛠 個人 / 測試用途：免費 / Personal Testing Use: Free
- 💼 商業用途請聯繫作者 / Commercial Use: Contact Maintainer

---

## 🌐 Project / 項目介紹

Created by RetryIX AGI Inc  
項目由 RetryIX AGI 開發  
More info: [https://retryixagi.com](https://retryixagi.com)

---


---

## 🖥️ 實測硬體環境 / Verified Hardware Environment

本專案在以下具體硬體與驅動條件下完成實現與測試：

### ✅ 測試平台
- **CPU**：AMD Ryzen™ 9 3950X (16-core, 32-thread)
- **主機板**：ASUS Crosshair VIII Hero (X570)
- **GPU**：AMD Radeon™ RX 5700 (Navi10)
- **記憶體**：64GB DDR4 RAM
- **作業系統**：Windows 10 / Windows 11

### ✅ 驅動版本
- AMD WHQL 驅動：`whql-amd-software-adrenalin-edition-22.5.1-win10-win11-may10.exe`
- 驅動內含 OpenCL 2.0 runtime（支援 SVM 與對齊操作）

---

## 🔁 技術重現步驟 / Reproducibility Steps

1. 安裝相同版本之 AMD 顯示卡驅動（22.5.1 WHQL）
2. 使用支援 OpenCL 2.0 的顯示卡（建議 RX 5700 或同級 Navi10 架構）
3. 編譯本專案：可用 GCC（MinGW）、MSVC 或 Clang
4. 執行 CLI 工具以列出裝置並確認記憶體對齊與 SVM 支援
5. 透過 `retryix_host.c` 進行 4MB / 512B 編碼測試，驗證輸出一致性

如欲在不同平台重現，請確保支援 OpenCL 2.0 並可開啟 SVM 記憶體模型。

If you're reproducing this on another machine, ensure:
- Your GPU supports OpenCL 2.0 + SVM
- You use driver version 22.5.1 or equivalent (tested)
- Use RetryIX CLI to confirm runtime capabilities

---

## 🔍 驅動相容性說明 / Known Driver Compatibility

根據實測，目前以下驅動版本已確認能支援本專案運行：

- ✅ `whql-amd-software-adrenalin-edition-22.5.1-win10-win11-may10.exe`（穩定）

根據社群回報與測試，目前 **新版本 AMD 顯示卡驅動**（特別是 Adrenalin 2023/2024 系列）也可成功載入模組並執行對齊編碼邏輯，  
但尚未全面測試其在 **SVM 記憶體模式下的穩定性** 與大區塊傳輸表現。

🗣 若你使用新版驅動，**歡迎在討論區或 Issue Tracker 提供回報**：  
- 成功載入與否  
- 模組是否出現 crash / error  
- 對齊區塊是否正確完成  

此資料將有助於進一步擴展跨驅動相容性。

---

## 📦 SDK Requirement / 所需 SDK

### ✅ This project requires an OpenCL 2.0 ICD SDK to build and run.
Please refer to the open-source SDK provided here:
👉 https://github.com/Retryixagi/2025_OpenCL2.0

📦 本專案需搭配 OpenCL 2.0 ICD SDK 進行建置與執行

請參考我自製的開源 SDK 倉庫：
👉 https://github.com/Retryixagi/2025_OpenCL2.0

---

## ⚖️ 版權聲明與授權條款 / Copyright & Licensing

本專案為 RetryIX AGI 原創技術模組，並採以下授權方式開放：

### ✅ 免費授權範圍 / Free Use License

**可免費使用於：**
- 個人用途 / Personal use
- 學術研究 / Academic research
- 技術展示與驗證 / Technical demonstrations

### ❌ 禁止項目 / Restrictions

- 禁止對本模組進行任何「改名／變體再發佈」行為  
  No fork/variant may be republished or renamed for derivative branding.
- 禁止以本模組任意修改後進行發佈或宣稱為原創技術  
  No modified derivative may be claimed as original technology.
- 禁止在未授權情況下以任何形式進行商業銷售、SaaS 提供或整合套件使用  
  Commercial resale, SaaS, or integration without permission is strictly prohibited.

### 💼 商業授權申請 / Commercial Licensing

如需整合本模組用於商業用途（如產品、平台、解決方案或顧問交付），請聯絡作者以取得書面授權：  
📩 Email: ixu@retryixagi.com  
🌐 Site: [https://retryixagi.com](https://retryixagi.com)

## 🙏 Acknowledgements / 感謝

This project was developed with the support of various advanced AI assistants that helped with architecture review, code verification, and language editing. Special thanks to:

- [ChatGPT-4o](https://openai.com/chatgpt): for cross-verifying algorithmic logic and assisting in technical writing  
- Claude (Anthropic): for stress-testing early architectural assumptions  
- GitHub Copilot: for real-time code auto-completion and pattern guidance

本專案的誕生，離不開多種 AI 工具的輔助，特別是在架構設計、語義驗證、語言統整等方面提供了極大幫助。特此致謝。

本專案已登錄技術原始證據，所有侵權行為將依法追訴。

> This project is protected under full technical authorship and will enforce licensing violations.

