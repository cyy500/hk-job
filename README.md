<img src="jobsdb-scraper-master/jobsdb-scraper-master/assets/jobsdb.png" width="300" height="auto"><br>

# hk-job

A JobsDB web scraper for Hong Kong (and other regions) job listings, plus a `data/` directory for storing the resulting CSV datasets.

---

## 项目结构 / Repository Structure

```
hk-job/
├── jobsdb-scraper-master/   # Scraper source code (TypeScript / Node.js)
├── data/                    # CSV datasets (raw & processed)
│   └── README.md            # Data directory guide (naming, upload, LFS, PII warning)
├── .gitignore
└── README.md                # This file
```

---

## 快速开始 / Quick Start

See **[jobsdb-scraper-master/jobsdb-scraper-master/README.md](jobsdb-scraper-master/jobsdb-scraper-master/README.md)** for full installation and usage instructions.

Short version:

```bash
cd jobsdb-scraper-master/jobsdb-scraper-master
npm install
npm run build

# Scrape all Software Engineering jobs in HK, save as CSV
node build/src/scrape_jobsdb scrape https://hk.jobsdb.com/Software-Engineer-jobs -f csv
```

Output files land in `jobsdb_scrape_results/` by default.  
Move or copy them into `data/` when you want to version-control them.

---

## 如何把 CSV 数据上传到仓库 / How to Upload CSV Data

> Full details (including Git LFS guidance) are in **[data/README.md](data/README.md)**.

### 方法 A：GitHub 网页界面（无需安装任何工具）
**Method A: GitHub Web UI (no tools required)**

1. 打开仓库 → 进入 `data/` 目录  
   Open the repo → navigate to the `data/` folder.
2. 点击右上角 **"Add file" → "Upload files"**  
   Click **"Add file" → "Upload files"**.
3. 拖拽 CSV 文件到上传区，或点击 **"choose your files"** 选择文件  
   Drag & drop your CSV, or click **"choose your files"**.
4. 填写 Commit message，例如 `data: add HK jobs 2024-06-01`  
   Write a commit message, e.g. `data: add HK jobs 2024-06-01`.
5. 点击 **"Commit changes"**  
   Click **"Commit changes"**.

> ⚠️ 单文件最大 **25 MB**，单次最多 **100 个文件**。更大的文件请用 git CLI。

---

### 方法 B：git 命令行
**Method B: git CLI**

```bash
# Clone (if you haven't already)
git clone https://github.com/cyy500/hk-job.git
cd hk-job

# Copy your CSV into data/
cp /path/to/your/file.csv data/

# Stage, commit, push
git add data/your_file.csv
git commit -m "data: add HK jobs snapshot YYYY-MM-DD"
git push origin main
```

---

## ⚠️ 安全提示 / Security Note

请勿将以下内容提交到仓库 / Do NOT commit:
- API keys, tokens, cookies, passwords
- Personal Identifiable Information (PII): names, phone numbers, ID numbers
- Data you are not legally allowed to redistribute

---

## License

[MIT](jobsdb-scraper-master/jobsdb-scraper-master/LICENSE)
