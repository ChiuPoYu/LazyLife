# LazyLife

> 2026 YTP 黑客松 - 以最人性化、最精準的方式知道你想去哪玩

LazyLife 是一個智能旅遊規劃平台，結合 AI 技術與政府開放資料，幫助使用者以最人性化的方式找到最適合的旅遊景點與活動。

## 📋 目錄

- [專案簡介](#專案簡介)
- [技術架構](#技術架構)
- [專案結構](#專案結構)
- [系統需求](#系統需求)
- [快速開始](#快速開始)
- [開發指南](#開發指南)
- [部署](#部署)
- [貢獻指南](#貢獻指南)
- [授權條款](#授權條款)

## 🎯 專案簡介

LazyLife 透過以下核心功能提供智能旅遊建議：

- **自然語言理解 (NLU)**：理解使用者的偏好與需求
- **檢索增強生成 (RAG)**：結合政府開放資料提供精準建議
- **智能推薦**：基於使用者行為與偏好的個性化推薦
- **政府資料整合**：整合台灣政府開放資料平台的旅遊資訊

## 🏗️ 技術架構

### Backend (.NET)
- **Framework**: ASP.NET Core
- **Architecture**: Clean Architecture (Domain-Driven Design)
  - `Api/`: Web API 層，處理 HTTP 請求
  - `App/`: 應用服務層，實作業務邏輯
  - `Domain/`: 領域層，核心業務實體與規則
  - `Infrastructure/`: 基礎設施層，資料存取與外部服務

### AI/ML (Python)
- **NLU Module**: 自然語言處理與意圖識別
- **RAG Module**: 檢索增強生成系統
- **Stats Module**: 資料分析與統計功能

### Plugins
- **Gov Data Plugin**: 政府開放資料串接與處理

## 📁 專案結構

```
LazyLife/
├── backend-dotnet/          # .NET 後端服務
│   ├── Api/                 # Web API 專案
│   ├── App/                 # 應用服務層
│   ├── Domain/              # 領域模型
│   └── Infrastructure/      # 基礎設施層
│
├── ai-python/               # Python AI/ML 服務
│   ├── nlu/                 # 自然語言理解模組
│   ├── rag/                 # 檢索增強生成模組
│   └── stats/               # 統計分析模組
│
├── plugins/                 # 外掛模組
│   └── gov-data/            # 政府資料整合外掛
│
├── docs/                    # 專案文件
│
├── docker-compose.yml       # Docker Compose 配置
├── .gitignore              # Git 忽略規則
└── README.md               # 專案說明文件
```

## 💻 系統需求

### Backend Development
- .NET SDK 8.0 或更高版本
- Visual Studio 2022 / Rider / VS Code

### AI/ML Development
- Python 3.10 或更高版本
- pip 或 poetry

### Container Deployment
- Docker 20.10 或更高版本
- Docker Compose 2.0 或更高版本

### Development Tools (推薦)
- Git 2.30 或更高版本
- Postman 或其他 API 測試工具

## 🚀 快速開始

### 使用 Docker Compose（推薦）

```bash
# 克隆專案
git clone https://github.com/ChiuPoYu/LazyLife.git
cd LazyLife

# 啟動所有服務
docker-compose up -d

# 查看服務狀態
docker-compose ps

# 查看日誌
docker-compose logs -f
```

### 本地開發環境

#### Backend (.NET)

```bash
# 進入 backend 目錄
cd backend-dotnet

# 還原相依套件
dotnet restore

# 建置專案
dotnet build

# 執行 API 服務
cd Api
dotnet run
```

API 預設運行在 `https://localhost:5001` 或 `http://localhost:5000`

#### AI/ML (Python)

```bash
# 進入 ai-python 目錄
cd ai-python

# 建立虛擬環境
python -m venv venv

# 啟動虛擬環境
# Windows
venv\Scripts\activate
# macOS/Linux
source venv/bin/activate

# 安裝相依套件
pip install -r requirements.txt

# 執行 AI 服務
python main.py
```

## 🛠️ 開發指南

### 開發流程

1. **分支管理**
   - `main`: 主要分支，穩定版本
   - `develop`: 開發分支
   - `feature/*`: 新功能開發
   - `bugfix/*`: 錯誤修復
   - `hotfix/*`: 緊急修復

2. **程式碼風格**
   - .NET: 遵循 Microsoft C# Coding Conventions
   - Python: 遵循 PEP 8 風格指南
   - 使用適當的命名規範與註解

3. **測試**
   - 撰寫單元測試確保程式碼品質
   - 整合測試驗證模組間的互動
   - 執行測試確保沒有破壞現有功能

### Backend 開發

```bash
# 執行測試
dotnet test

# 程式碼格式化
dotnet format
```

### AI/ML 開發

```bash
# 執行測試
pytest

# 程式碼檢查
flake8 .
pylint **/*.py

# 型別檢查
mypy .
```

### API 文件

啟動後端服務後，可以透過以下網址查看 API 文件：
- Swagger UI: `http://localhost:5000/swagger`

## 🐳 部署

### Docker Compose 部署

```bash
# 建置並啟動所有服務
docker-compose up -d --build

# 停止所有服務
docker-compose down

# 停止並清除所有資料
docker-compose down -v
```

### 環境變數設定

在專案根目錄建立 `.env` 檔案：

```env
# Database
DATABASE_CONNECTION_STRING=your_connection_string

# API Keys
GOV_DATA_API_KEY=your_gov_data_api_key

# AI Service
AI_MODEL_PATH=/path/to/models

# Other settings
ASPNETCORE_ENVIRONMENT=Production
```

## 🤝 貢獻指南

我們歡迎所有形式的貢獻！

1. Fork 本專案
2. 建立您的特性分支 (`git checkout -b feature/AmazingFeature`)
3. 提交您的更改 (`git commit -m 'Add some AmazingFeature'`)
4. 推送到分支 (`git push origin feature/AmazingFeature`)
5. 開啟 Pull Request

### 提交訊息規範

```
<type>(<scope>): <subject>

<body>

<footer>
```

**Type 類型：**
- `feat`: 新功能
- `fix`: 錯誤修復
- `docs`: 文件更新
- `style`: 程式碼格式調整
- `refactor`: 重構
- `test`: 測試相關
- `chore`: 建置流程或輔助工具變動

## 📝 授權條款

本專案採用 MIT License - 詳見 [LICENSE](LICENSE) 檔案

## 📧 聯絡資訊

- 專案負責人: [ChiuPoYu](https://github.com/ChiuPoYu)
- 專案連結: [https://github.com/ChiuPoYu/LazyLife](https://github.com/ChiuPoYu/LazyLife)

## 🙏 致謝

感謝所有貢獻者以及以下資源：

- [ASP.NET Core](https://dotnet.microsoft.com/apps/aspnet)
- [Python](https://www.python.org/)
- [政府資料開放平臺](https://data.gov.tw/)

---

**Made with ❤️ for 2026 YTP Hackathon**
