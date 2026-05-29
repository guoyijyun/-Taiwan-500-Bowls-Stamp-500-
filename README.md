# 🍜 Taiwan-500-Bowls-Stamp (台灣500碗數位集章 App)

一個專為台灣美食愛好者設計的 PWA (漸進式網頁應用) 專案。使用者可以透過手機地圖尋找歷年「台灣500碗」的得獎小吃，在實地到訪後，上傳當下拍攝的美食照片，透過 AI 自動去背功能將照片轉化為專屬的「美食徽章」，蓋在數位集章冊上，並留下個人的美食評論。

---

## 🚀 核心功能 (Core Features)

- **📌 500碗互動地圖**：整合歷年 500 碗得獎名單，支援 GPS 定位與店家篩選（年份/區域/小吃類型）。
- **✂️ AI 美食照片去背**：使用者上傳現場美食照，網頁端自動進行 AI 去背，生成專屬的 PNG 食物形狀印章。
- **📒 數位集章冊 (成就牆)**：以視覺化的格子（如集郵冊）呈現已解鎖與未解鎖的店家，點擊可查看當初的去背章。
- **💬 私房評論筆記**：記錄每次到訪的日期、星等評價與用餐心得。
- **📱 PWA 手機主畫面支援**：免下載安裝，一鍵「加入主畫面」即可像原生 App 一樣流暢操作。

---

## 🛠️ 技術棧 (Tech Stack)

- **前端框架**：React.js (搭配 Vite) / Tailwind CSS (UI 樣式)
- **地圖地標**：Leaflet.js / OpenStreetMap (或 Google Maps API)
- **去背技術**：`@imgly/background-removal` (瀏覽器端本地 AI 去背)
- **後端服務**：Firebase (Authentication 登入、Firestore 資料庫、Storage 照片儲存)
- **部署平台**：Vercel / Firebase Hosting

---

## 📊 開發流程與程式架構圖

以下是本專案的完整開發與執行流程。

```mermaid
graph TD
    %% 階段一：資料準備
    subgraph Phase_1 [第一階段：資料與地圖建置]
        A[收集500碗歷年名單] -->|Python / 手動整理| B(轉換地址為經緯度 JSON)
        B --> C[前端引入地圖套件 Leaflet]
        C --> D[將 JSON 資料批次標記於地圖上]
    end

    %% 階段二：使用者互動與登入
    subgraph Phase_2 [第二階段：會員與互動介面]
        D --> E[串接 Firebase Auth 登入]
        E --> F[點擊地圖標記 Marker]
        F --> G{判斷是否登入?}
        G -->|否| H[提示登入]
        G -->|是| I[彈出店家詳細資訊與打卡視窗]
    end

    %% 階段三：核心集章與 AI 去背
    subgraph Phase_3 [第三階段：AI 去背與資料儲存]
        I --> J[使用者拍照/上傳美食照片]
        J --> K[WebAssembly AI 本地端自動去背]
        K --> L[生成 PNG 格式美食印章]
        L --> M[填寫星等與評論文字]
        M --> N[上傳圖片至 Firebase Storage]
        N --> O[寫入打卡紀錄至 Firestore 資料庫]
    end

    %% 階段四：成果展示
    subgraph Phase_4 [第四階段：個人成就牆與 PWA]
        O --> P[個人成就頁拉取 Firestore 紀錄]
        P --> Q[渲染個人專屬數位集章冊]
        Q --> R[配置 Vite PWA 套件]
        R --> S[部署上線並加入手機主畫面]
    end

    style Phase_1 fill:#f9f,stroke:#333,stroke-width:2px
    style Phase_2 fill:#bbf,stroke:#333,stroke-width:2px
    style Phase_3 fill:#fbf,stroke:#333,stroke-width:2px
    style Phase_4 fill:#bfb,stroke:#333,stroke-width:2px



啊！原來是 Mermaid 流程圖語法抓到了後面的標題。在 Mermaid 區塊（````mermaid`）結束時，忘記加上結尾的三個反引號（`````），導致 GitHub 把後面的「🗃️ 資料庫欄位設計」當作圖表語法來解析，才噴出了這個語法錯誤。

我修正了這個漏掉的結尾。你可以直接複製下面這段修正後的完整 Markdown，重新覆蓋貼上到你的 `README.md` 就沒問題了！

---

```markdown
# 🍜 Taiwan-500-Bowls-Stamp (台灣500碗數位集章 App)

一個專為台灣美食愛好者設計的 PWA (漸進式網頁應用) 專案。使用者可以透過手機地圖尋找歷年「台灣500碗」的得獎小吃，在實地到訪後，上傳當下拍攝的美食照片，透過 AI 自動去背功能將照片轉化為專屬的「美食徽章」，蓋在數位集章冊上，並留下個人的美食評論。

---

## 🚀 核心功能 (Core Features)

- **📌 500碗互動地圖**：整合歷年 500 碗得獎名單，支援 GPS 定位與店家篩選（年份/區域/小吃類型）。
- **✂️ AI 美食照片去背**：使用者上傳現場美食照，網頁端自動進行 AI 去背，生成專屬的 PNG 食物形狀印章。
- **📒 數位集章冊 (成就牆)**：以視覺化的格子（如集郵冊）呈現已解鎖與未解鎖的店家，點擊可查看當初的去背章。
- **💬 私房評論筆記**：記錄每次到訪的日期、星等評價與用餐心得。
- **📱 PWA 手機主畫面支援**：免下載安裝，一鍵「加入主畫面」即可像原生 App 一樣流暢操作。

---

## 🛠️ 技術棧 (Tech Stack)

- **前端框架**：React.js (搭配 Vite) / Tailwind CSS (UI 樣式)
- **地圖地標**：Leaflet.js / OpenStreetMap (或 Google Maps API)
- **去背技術**：`@imgly/background-removal` (瀏覽器端本地 AI 去背)
- **後端服務**：Firebase (Authentication 登入、Firestore 資料庫、Storage 照片儲存)
- **部署平台**：Vercel / Firebase Hosting

---

## 📊 開發流程與程式架構圖

以下是本專案的完整開發與執行流程。

```mermaid
graph TD
    %% 階段一：資料準備
    subgraph Phase_1 [第一階段：資料與地圖建置]
        A[收集500碗歷年名單] -->|Python / 手動整理| B(轉換地址為經緯度 JSON)
        B --> C[前端引入地圖套件 Leaflet]
        C --> D[將 JSON 資料批次標記於地圖上]
    end

    %% 階段二：使用者互動與登入
    subgraph Phase_2 [第二階段：會員與互動介面]
        D --> E[串接 Firebase Auth 登入]
        E --> F[點擊地圖標記 Marker]
        F --> G{判斷是否登入?}
        G -->|否| H[提示登入]
        G -->|是| I[彈出店家詳細資訊與打卡視窗]
    end

    %% 階段三：核心集章與 AI 去背
    subgraph Phase_3 [第三階段：AI 去背與資料儲存]
        I --> J[使用者拍照/上傳美食照片]
        J --> K[WebAssembly AI 本地端自動去背]
        K --> L[生成 PNG 格式美食印章]
        L --> M[填寫星等與評論文字]
        M --> N[上傳圖片至 Firebase Storage]
        N --> O[寫入打卡紀錄至 Firestore 資料庫]
    end

    %% 階段四：成果展示
    subgraph Phase_4 [第四階段：個人成就牆與 PWA]
        O --> P[個人成就頁拉取 Firestore 紀錄]
        P --> Q[渲染個人專屬數位集章冊]
        Q --> R[配置 Vite PWA 套件]
        R --> S[部署上線並加入手機主畫面]
    end

    style Phase_1 fill:#f9f,stroke:#333,stroke-width:2px
    style Phase_2 fill:#bbf,stroke:#333,stroke-width:2px
    style Phase_3 fill:#fbf,stroke:#333,stroke-width:2px
    style Phase_4 fill:#bfb,stroke:#333,stroke-width:2px

```

---

## 🗃️ 資料庫欄位設計 (Database Schema)

### 1. `stores` (店家靜態資料)

```json
{
  "store_id": "store_001",
  "name": "彰化阿三肉圓",
  "year": [2023, 2024],
  "category": "肉圓/小吃",
  "address": "彰化市三民路242號",
  "lat": 24.0816,
  "lng": 120.5432
}

```

### 2. `check_ins` (使用者集章與評論資料)

```json
{
  "check_in_id": "chk_12345",
  "uid": "user_firebase_uid",
  "store_id": "store_001",
  "visited_at": "2026-05-29T21:15:00Z",
  "stamp_image_url": "https://firebasestorage.../stamps/meatball.png",
  "rating": 5,
  "comment": "外皮超酥脆，干貝內餡很厲害，配特製醬料完美！"
}

```

---

## 🗃️ 資料庫欄位設計 (Database Schema)

### 1. `stores` (店家靜態資料)
```json
{
  "store_id": "store_001",
  "name": "彰化阿三肉圓",
  "year": [2023, 2024],
  "category": "肉圓/小吃",
  "address": "彰化市三民路242號",
  "lat": 24.0816,
  "lng": 120.5432
}

### 2. `stores` (店家靜態資料)

```json
{
  "check_in_id": "chk_12345",
  "uid": "user_firebase_uid",
  "store_id": "store_001",
  "visited_at": "2026-05-29T21:15:00Z",
  "stamp_image_url": "https://firebasestorage.../stamps/meatball.png",
  "rating": 5,
  "comment": "外皮超酥脆，干貝內餡很厲害，配特製醬料完美！"
}

## 🏃‍♂️ 如何在本地端啟動專案 (Getting Started)

### 1. 複製專案

```bash
git clone [https://github.com/your-username/taiwan-500-bowls-stamp.git](https://github.com/your-username/taiwan-500-bowls-stamp.git)
cd taiwan-500-bowls-stamp

```

### 2. 安裝依賴套件

```bash
npm install

```

### 3. 設定環境變數

在根目錄建立 `.env.local` 並填入你的 Firebase 配置（此檔案已被加入 `.gitignore`，切勿推上 GitHub）：

```env
VITE_FIREBASE_API_KEY=your_api_key
VITE_FIREBASE_AUTH_DOMAIN=your_auth_domain
VITE_FIREBASE_PROJECT_ID=your_project_id
VITE_FIREBASE_STORAGE_BUCKET=your_storage_bucket
VITE_FIREBASE_MESSAGING_SENDER_ID=your_sender_id
VITE_FIREBASE_APP_ID=your_app_id

```

### 4. 啟動開發伺服器

```bash
npm run dev

```

```


```


