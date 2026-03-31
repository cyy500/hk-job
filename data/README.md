# data/

This directory stores CSV datasets generated or used by the crawler.

---

## 目录结构 / Directory Structure

```
data/
├── raw/          # 原始抓取数据（未清洗）/ Raw scraped data (unprocessed)
├── processed/    # 清洗 / 处理后的数据 / Cleaned or processed data
└── README.md     # 本文件 / This file
```

Feel free to create `raw/` and `processed/` subdirectories to keep things tidy.

---

## 命名规范 / Naming Conventions

Use a descriptive, date-stamped filename so files are easy to identify:

```
<topic>_<region>_<YYYY-MM-DD>.csv

# Examples:
jobs_hk_2024-06-01.csv
software_engineer_hk_2024-06-01_raw.csv
accounting_th_2024-06-01_processed.csv
```

---

## ⚠️ 重要安全提示 / Security & Privacy Warning

**Do NOT commit files that contain:**
- API keys, tokens, cookies, or passwords （密钥、Token、Cookie）
- Personal Identifiable Information (PII) such as full names, phone numbers, ID numbers（个人隐私信息，如姓名、电话、身份证号）
- Any data you are not legally allowed to redistribute（未经授权重新分发的数据）

Once committed to a public repo, sensitive data is extremely difficult to remove completely.
如果不小心提交了敏感数据，请立即联系 GitHub Support 并轮换相关密钥。

---

## 大文件处理 / Large Files

| 文件大小 / File Size | 推荐方案 / Recommended Approach |
|---|---|
| < 50 MB | 直接提交到仓库 / Commit directly to repo |
| 50 MB – 2 GB | 使用 [Git LFS](https://git-lfs.github.com/) |
| > 2 GB | 使用外部存储（OSS / S3 / Google Drive），在此处记录下载链接 / Use external storage and link here |

### Git LFS Quick Start

```bash
# Install Git LFS (once per machine)
git lfs install

# Track all CSV files via LFS
git lfs track "data/**/*.csv"

# This creates/updates .gitattributes — commit it
git add .gitattributes
git commit -m "chore: track CSVs with Git LFS"
```

For very large or frequently updated datasets, consider storing the files in an external
service (e.g., AWS S3, Aliyun OSS, Google Drive) and adding a download script under
`scripts/download_data.py` instead of checking the files in directly.

---

## 如何上传 CSV 文件 / How to Upload CSV Files

### 方法 A：GitHub 网页界面（无需安装任何工具）
**Method A: GitHub Web UI (no tools required)**

1. 打开仓库页面 / Open the repository page:  
   `https://github.com/cyy500/hk-job`
2. 点击 `data/` 文件夹 / Click the `data/` folder.
3. 点击右上角 **"Add file" → "Upload files"**  
   Click **"Add file" → "Upload files"** in the top-right area.
4. 将 CSV 文件拖拽到上传区域，或点击 **"choose your files"**  
   Drag & drop your CSV file(s) onto the upload area, or click **"choose your files"**.
5. 滚动到底部，填写提交说明（Commit message），例如：  
   Scroll down, write a commit message, e.g.:  
   `data: add HK jobs snapshot 2024-06-01`
6. 选择 **"Commit directly to the `main` branch"**，然后点击 **"Commit changes"**  
   Select **"Commit directly to the `main` branch"** and click **"Commit changes"**.

> ⚠️ 网页界面单次最多上传 **100 个文件**，单个文件不超过 **25 MB**。超过请改用 git CLI。  
> The web UI supports up to **100 files** and **25 MB per file**. For larger files use git CLI.

---

### 方法 B：git 命令行（推荐，支持大文件）
**Method B: git CLI (recommended, supports larger files)**

```bash
# 1. 克隆仓库（如果还没有）/ Clone the repo (if you haven't already)
git clone https://github.com/cyy500/hk-job.git
cd hk-job

# 2. 把 CSV 文件复制到 data/ 目录 / Copy your CSV file(s) into data/
cp /path/to/your/file.csv data/

# 3. 暂存文件 / Stage the file
git add data/your_file.csv

# 4. 提交 / Commit
git commit -m "data: add HK jobs snapshot YYYY-MM-DD"

# 5. 推送到 GitHub / Push to GitHub
git push origin main
```

---

## 样本数据 / Sample Data

Small sample files (< 1 MB) are welcome in this directory so that others can understand
the data schema without downloading the full dataset. Name them with a `sample_` prefix:

```
data/sample_jobs_hk.csv
```
