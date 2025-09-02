# RetryIX Memory RAID Engine

## 🚀 最新動態 / Latest Updates

### 中文
🔬 最新進展預告  
我們已成功完成 4MB 與 8MB / 4096B 對齊編碼技術的穩定化運行，並已送交學術界進行驗證與研究。  
此技術不僅突破現有記憶體編碼瓶頸，也已具備實際應用價值。未來我們將：
- ✨ 向 arXiv 提交技術論文，取得國際學術認證
- 💼 採取商業授權模式，針對產業應用提供正式授權與技術支持  
這是 RetryIX 在記憶體架構與高效能運算領域邁出的關鍵一步，更多細節將於正式論文與授權公告中揭曉。

### English
🔬 Upcoming Milestone Announcement  
We have successfully achieved stable execution of 4MB and 8MB / 4096B-aligned encoding techniques, now undergoing academic validation and peer research.  
This breakthrough not only overcomes existing memory encoding bottlenecks but also demonstrates strong potential for real-world applications.
- ✨ Submit a technical paper to arXiv for international academic recognition
- 💼 Adopt a commercial licensing model to provide formal authorization and technical support for industry use cases  
This marks a crucial step for RetryIX in the field of memory architecture and high-performance computing. More details will be unveiled in the official paper and licensing announcements.

---

## 📚 原始說明 / Original Documentation

### RetryIX-OpenCL2.0-512B

- 🚀 4MB block encoding with 512B alignment using OpenCL 2.0 + SVM.
- ✅ Runs on standard OpenCL ICD without ROCm or CUDA dependencies.

- 🚀 使用 OpenCL 2.0 + SVM 實現 4MB 區塊編碼與 512B 對齊記憶體操作。
- ✅ 支援 ICD 標準運行，無需依賴 ROCm 或 CUDA。

---

## ✨ Features / 功能特點

- ✅ 4MB 區塊級記憶體編碼 / Block-level memory encoding
- ✅ 512B 對齊記憶體存取 / 512B-aligned memory access
- ✅ 基於 OpenCL 2.0 的共享虛擬記憶體（SVM） / Uses Shared Virtual Memory (SVM)
- ✅ 無需 ROCm / CUDA 環境 / No ROCm / CUDA required
- ✅ 相容各類 OpenCL ICD 驅動 / Compatible with OpenCL ICD (Intel, AMD, Mesa)

---

## 📦 Components / 模組構成

| File                    | Description (EN/中文)                                          |
|-------------------------|---------------------------------------------------------------|
| retryix_cli.c           | CLI for OpenCL device query / 指令列工具查詢 OpenCL 裝置與參數 |
| retryix_device_utils.c  | Device info export with JSON / 裝置資訊提取，支援 JSON 輸出     |
| retryix_host.c          | Host logic for block encoding / Host 模組，支援區塊編碼        |
| retryix_runtime.h       | Runtime abstraction / 運行時 API 抽象層                        |
| host_comm.h             | Local-only communication interface / 本地通訊模組定義           |
| module_descriptor.h     | Module registration and tagging / 模組註冊與語義標記           |
| retryix_query_all_resources.c | Batch resource scanner / 批次查詢所有資源               |

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

```
gcc retryix_cli.c retryix_device_utils.c retryix_host.c -lOpenCL -o retryix_cli
```

### Run 執行

```
./retryix_cli
```

---

⚠️ No Blockchain / 無區塊鏈依賴  
本專案未使用任何區塊鏈、加密、分散式架構，所有模組皆為本地 C 語言實作，專為開源與重現性設計。

---

## 📜 License / 授權條款

**Dual License / 雙授權：**

- 🧪 學術 / 研究用途：免費 / Academic & Research Use: Free
- 🛠 個人 / 測試用途：免費 / Personal Testing Use: Free
- 💼 商業用途請聯繫作者 / Commercial Use: Contact Maintainer

---

## 🖥️ 實測硬體環境 / Verified Hardware Environment

- CPU：AMD Ryzen™ 9 3950X (16-core, 32-thread)
- 主機板：ASUS Crosshair VIII Hero (X570)
- GPU：AMD Radeon™ RX 5700 (Navi10)
- 記憶體：64GB DDR4 RAM
- 作業系統：Windows 10 / Windows 11

### 驅動版本

- AMD WHQL 驅動：whql-amd-software-adrenalin-edition-22.5.1-win10-win11-may10.exe
- 驅動內含 OpenCL 2.0 runtime（支援 SVM 與對齊操作）

---

## 🔁 技術重現步驟 / Reproducibility Steps

1. 安裝相同版本之 AMD 顯示卡驅動（22.5.1 WHQL）
2. 使用支援 OpenCL 2.0 的顯示卡（建議 RX 5700 或同級 Navi10 架構）
3. 編譯本專案：可用 GCC（MinGW）、MSVC 或 Clang
4. 執行 CLI 工具以列出裝置並確認記憶體對齊與 SVM 支援
5. 透過 retryix_host.c 進行 4MB / 512B 編碼測試，驗證輸出一致性

> 如欲在不同平台重現，請確保支援 OpenCL 2.0 並可開啟 SVM 記憶體模型。

If you're reproducing this on another machine, ensure:
- Your GPU supports OpenCL 2.0 + SVM
- You use driver version 22.5.1 or equivalent (tested)
- Use RetryIX CLI to confirm runtime capabilities

---

## 🔍 驅動相容性說明 / Known Driver Compatibility

- whql-amd-software-adrenalin-edition-22.5.1-win10-win11-may10.exe（穩定）
- 社群回報：新版本 AMD 顯示卡驅動（Adrenalin 2023/2024 系列）也可載入模組並執行對齊編碼，SVM 穩定性與大區塊傳輸仍待測試。

> 若你使用新版驅動，歡迎在討論區或 Issue Tracker 提供回報（成功與否、crash/error、對齊區塊正確性）

---

## 📦 SDK Requirement / 所需 SDK

- This project requires an OpenCL 2.0 ICD SDK to build and run.
- 👉 https://github.com/Retryixagi/2025_OpenCL2.0

---

## ⚖️ 版權聲明與授權條款 / Copyright & Licensing

本專案為 RetryIX AGI 原創技術模組，並採以下授權方式開放：

### 免費授權範圍 / Free Use License

- 個人用途 / Personal use
- 學術研究 / Academic research
- 技術展示與驗證 / Technical demonstrations

### 禁止項目 / Restrictions

- 禁止改名／變體再發佈 / No fork/variant may be republished or renamed for derivative branding.
- 禁止任意修改後發佈／宣稱原創 / No modified derivative may be claimed as original technology.
- 禁止未授權商業銷售、SaaS、整合套件 / Commercial resale, SaaS, or integration without permission.

### 商業授權申請 / Commercial Licensing

如需整合本模組用於商業用途（產品、平台、顧問交付），請聯絡作者以取得書面授權：

- 📩 Email: ixu@retryixagi.com
- 🌐 Site: https://retryixagi.com

---

## 🙏 Acknowledgements / 感謝

This project was developed with the support of various advanced AI assistants:

- ChatGPT-4o: algorithmic logic cross-verification, technical writing
- Claude (Anthropic): architecture stress-testing
- GitHub Copilot: code auto-completion & pattern guidance

---

## 🤝 開放創新聲明 / Open Innovation Statement

RetryIX 誠摯歡迎全球研究者、開發者與產業伙伴基於本技術進行創新探索與合作。  
我們堅信共利共享才能推動真正的技術突破。

- 技術可自由研究、測試與延伸應用
- 鼓勵貢獻回饋，促進知識共創
- 使用過程產生之法律責任由使用者自行承擔

RetryIX warmly welcomes researchers, developers, and industry partners worldwide to explore and innovate based on this technology.

- Technology may be freely studied, tested, and extended for new applications
- Contributions and feedback are encouraged to foster knowledge co-creation
- Any legal responsibilities arising from usage remain solely with the user

本技術已登錄技術原始證據，所有侵權行為將依法追訴。

---

項目由 RetryIX AGI 開發 / Created by RetryIX AGI Inc  
更多資訊: https://retryixagi.com