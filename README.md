# Starter-pack-ex-02

# 🧑‍💻 Workshop: IDE, Terminal & Git Fundamentals

> คู่มือ Workshop ฉบับสมบูรณ์ สำหรับผู้เริ่มต้นที่ยังไม่เคยใช้ Git มาก่อน  
> ใช้เวลารวมประมาณ **3–4 ชั่วโมง**

---

## 📋 สารบัญ

1. [IDE และ VS Code](#1-ide-และ-vs-code)
2. [Terminal / CLI เบื้องต้น](#2-terminal--cli-เบื้องต้น)
3. [Introduction: Git คืออะไร และ GitHub คืออะไร](#3-introduction-git-คืออะไร-และ-github-คืออะไร)
4. [Version Control คืออะไร](#4-version-control-คืออะไร)
5. [สร้าง GitHub Account](#5-สร้าง-github-account)
6. [GitHub Profile Markdown](#6-github-profile-markdown)
7. [git init และการสร้าง Repository](#7-git-init-และการสร้าง-repository)
8. [git config](#8-git-config)
9. [git credential](#9-git-credential)
10. [git clone](#10-git-clone)

---

## 1. IDE และ VS Code

### IDE คืออะไร?

**IDE** ย่อมาจาก **Integrated Development Environment** คือโปรแกรมสำหรับเขียนโค้ดที่รวมเครื่องมือต่างๆ ไว้ในที่เดียว ได้แก่

- **Code Editor** — พื้นที่เขียนโค้ดพร้อม syntax highlighting
- **Terminal** — รัน command ได้โดยไม่ต้องออกจากโปรแกรม
- **File Explorer** — จัดการไฟล์และโฟลเดอร์
- **Extensions** — ติดตั้งปลั๊กอินเพิ่มความสามารถ

### ทำไมต้องใช้ VS Code?

**Visual Studio Code (VS Code)** คือ IDE ที่นิยมที่สุดในโลกตอนนี้ เพราะ

- ฟรี และ Open Source
- เบาและเร็ว
- รองรับเกือบทุกภาษาโปรแกรมมิ่ง
- มี Extension มากกว่า 30,000 ตัว
- มี Git integration ในตัวเลย

### ขั้นตอนติดตั้ง VS Code

1. ไปที่ https://code.visualstudio.com
2. คลิก **Download** (จะดาวน์โหลดให้ตรงกับ OS อัตโนมัติ)
3. ติดตั้งตามขั้นตอนปกติ
4. เปิด VS Code ขึ้นมา

### Extensions ที่แนะนำให้ติดตั้ง

เปิด VS Code แล้วกด `Ctrl+Shift+X` (Windows) หรือ `Cmd+Shift+X` (macOS) เพื่อเปิด Extensions และค้นหาชื่อด้านล่าง

| Extension | ประโยชน์ |
|-----------|----------|
| `Prettier - Code formatter` | จัด format โค้ดให้สวยงามอัตโนมัติ |
| `GitLens` | แสดงประวัติ Git ใน editor |
| `indent-rainbow` | ทำให้เห็น indentation ชัดขึ้น |
| `Auto Rename Tag` | เปลี่ยน HTML tag เปิด-ปิดพร้อมกัน |
| `Thai Language Pack` | เปลี่ยนภาษา UI เป็นภาษาไทย |

### Keyboard Shortcuts ที่ใช้บ่อย

| Shortcut (macOS / Windows) | ความหมาย |
|---------------------------|-----------|
| `Cmd+P` / `Ctrl+P` | ค้นหาและเปิดไฟล์ |
| `Cmd+\`` / `Ctrl+\`` | เปิด/ปิด Terminal ใน VS Code |
| `Cmd+Shift+P` / `Ctrl+Shift+P` | เปิด Command Palette |
| `Cmd+/` / `Ctrl+/` | คอมเมนต์โค้ด |
| `Cmd+Z` / `Ctrl+Z` | Undo |
| `Option+↑↓` / `Alt+↑↓` | ย้ายบรรทัดขึ้น/ลง |

---

## 2. Terminal / CLI เบื้องต้น

### Terminal คืออะไร?

**Terminal** (หรือเรียกว่า **CLI — Command Line Interface**) คือหน้าต่างที่ให้เราสั่งงานคอมพิวเตอร์ด้วยการพิมพ์ข้อความ แทนที่จะคลิกผ่าน GUI

เปิด Terminal ได้จาก
- **macOS:** กด `Cmd+Space` แล้วพิมพ์ "Terminal"
- **Windows:** ค้นหา "PowerShell" หรือ "Git Bash" (แนะนำ Git Bash)
- **VS Code:** กด `Ctrl+\`` หรือ `Cmd+\``

### โครงสร้างของ Command

```
คำสั่ง   option   argument
  │         │        │
  ▼         ▼        ▼
  ls       -la    /home/user
```

### คำสั่ง `cd` — เดินทางระหว่างโฟลเดอร์

`cd` ย่อมาจาก **Change Directory**

```bash
# เข้าไปในโฟลเดอร์
cd Documents

# เข้าไปหลายระดับพร้อมกัน
cd Documents/Projects/myapp

# ออกมา 1 ระดับ
cd ..

# ออกมา 2 ระดับ
cd ../..

# กลับไป Home directory (~)
cd ~
cd        # ไม่ใส่ argument ก็ได้ผลเหมือนกัน

# กลับไปโฟลเดอร์ก่อนหน้า
cd -
```

> 💡 **Tip:** กด `Tab` เพื่อให้ terminal เติมชื่อโฟลเดอร์/ไฟล์อัตโนมัติ  
> ไม่ต้องพิมพ์ชื่อทั้งหมด พิมพ์แค่ตัวแรกแล้วกด Tab ได้เลย

### คำสั่ง `mkdir` — สร้างโฟลเดอร์

`mkdir` ย่อมาจาก **Make Directory**

```bash
# สร้างโฟลเดอร์เดียว
mkdir myproject

# สร้างโฟลเดอร์ซ้อนกันหลายชั้นพร้อมกัน (ใช้ -p)
mkdir -p myproject/src/components

# สร้างหลายโฟลเดอร์พร้อมกัน
mkdir src public assets
```

### คำสั่ง `code .` — เปิด VS Code จาก Terminal

```bash
# เปิด VS Code ที่โฟลเดอร์ปัจจุบัน
code .

# เปิด VS Code ที่โฟลเดอร์ที่ระบุ
code /path/to/project

# เปิดไฟล์เดียวใน VS Code
code README.md
```

> ⚠️ **หมายเหตุ:** บน macOS ต้องติดตั้ง `code` command ก่อน  
> เปิด VS Code → กด `Cmd+Shift+P` → พิมพ์ "Shell Command: Install 'code' command in PATH" → กด Enter

### คำสั่งอื่นๆ ที่ใช้บ่อย

```bash
# ดูว่าอยู่โฟลเดอร์ไหน
pwd

# แสดงไฟล์และโฟลเดอร์
ls
ls -la    # แสดงทุกไฟล์ รวมถึงไฟล์ซ่อน พร้อม permission

# สร้างไฟล์เปล่า
touch index.html

# อ่านเนื้อหาในไฟล์
cat README.md

# ล้างหน้าจอ
clear
```

### 🏋️ แบบฝึกหัด — Terminal เบื้องต้น

ให้ทำตามขั้นตอนนี้ผ่าน Terminal เท่านั้น:

```bash
# 1. ไปที่ Desktop
cd ~/Desktop

# 2. สร้างโฟลเดอร์โปรเจกต์
mkdir my-first-project

# 3. เข้าไปในโฟลเดอร์
cd my-first-project

# 4. สร้างโครงสร้างโฟลเดอร์
mkdir -p src/css src/js

# 5. สร้างไฟล์
touch index.html
touch src/css/style.css
touch src/js/main.js
touch README.md

# 6. ตรวจสอบผลลัพธ์
ls -la
ls src/

# 7. เปิดด้วย VS Code
code .
```

โครงสร้างที่ได้:

```
my-first-project/
├── index.html
├── README.md
└── src/
    ├── css/
    │   └── style.css
    └── js/
        └── main.js
```

---

## 3. Introduction: Git คืออะไร และ GitHub คืออะไร

### Git คืออะไร?

**Git** คือโปรแกรม **Version Control System (VCS)** ที่ทำงานในเครื่องของเรา ใช้สำหรับ

- บันทึกประวัติการเปลี่ยนแปลงของโค้ดทุก version
- ย้อนกลับไปแก้ไขโค้ด version เก่าได้ตลอดเวลา
- ทำงานหลาย feature พร้อมกันโดยไม่กระทบกัน (ด้วย Branch)

### GitHub คืออะไร?

**GitHub** คือเว็บไซต์ที่ใช้เก็บ Git repository บน Cloud ทำให้

- โค้ดของเราปลอดภัยแม้เครื่องพัง
- แชร์โค้ดให้คนอื่นดูได้
- ทำงานร่วมกันเป็นทีมได้
- แสดง Portfolio ผลงานของเราได้

### Git vs GitHub

```
┌─────────────────────────────────────────────────────┐
│                                                     │
│   Git  ≠  GitHub                                   │
│                                                     │
│   Git    = โปรแกรมที่ทำงานในเครื่องเรา             │
│             เหมือน "กล้องถ่ายรูป"                  │
│                                                     │
│   GitHub = เว็บไซต์เก็บโค้ดบน Cloud               │
│             เหมือน "Google Photos"                  │
│                                                     │
│   ใช้ Git สร้างประวัติโค้ด                          │
│   แล้ว Push ขึ้น GitHub เพื่อเก็บและแชร์           │
│                                                     │
└─────────────────────────────────────────────────────┘
```

### ทางเลือกอื่นนอกจาก GitHub

| บริการ | จุดเด่น |
|--------|---------|
| **GitHub** | ใหญ่ที่สุด community มากที่สุด |
| **GitLab** | Self-host ได้ นิยมในองค์กร |
| **Bitbucket** | เชื่อมกับ Jira ได้ดี |

---

## 4. Version Control คืออะไร

### ปัญหาที่เกิดขึ้นโดยไม่มี Version Control

เคยเจอสถานการณ์แบบนี้ไหม?

```
📁 โปรเจกต์/
├── index.html
├── index_backup.html
├── index_final.html
├── index_final_v2.html
├── index_final_v2_แก้แล้ว.html
└── index_FINAL_ส่งงาน_จริงๆ.html   ← ใช้อันไหนกันแน่!?
```

Version Control แก้ปัญหานี้ได้ทั้งหมด

### Version Control คืออะไร?

**Version Control** คือระบบที่คอยบันทึกการเปลี่ยนแปลงของไฟล์ตลอดเวลา เหมือนมี "ปุ่ม Undo" ที่ไม่มีวันหมด และบันทึกไว้ตลอดกาล

### ประโยชน์ของ Version Control

**1. ย้อนเวลากลับไปได้**

```
วันจันทร์ → วันอังคาร → วันพุธ (bug!) → ย้อนกลับไปวันอังคาร ✅
```

**2. รู้ว่าใครแก้อะไร เมื่อไหร่**

```
commit a3f9c2d — แก้ bug ปุ่ม login ไม่ทำงาน
Author: สมชาย <somchai@email.com>
Date:   Mon Jun 10 14:32:00 2024
```

**3. ทำงานพร้อมกันได้โดยไม่ชนกัน**

```
main branch:    A ── B ── C ── D
                          │
feature branch:           └── E ── F  ← ทำ feature ใหม่แยกไว้ก่อน
```

**4. ทดลองได้อย่างปลอดภัย**

ถ้าทดลองแล้วพัง ก็แค่ย้อนกลับ ไม่มีอะไรเสียหาย

### แนวคิดหลักของ Git

| คำศัพท์ | ความหมาย |
|---------|----------|
| **Repository (Repo)** | โฟลเดอร์โปรเจกต์ที่ Git ดูแลอยู่ |
| **Commit** | การบันทึก "snapshot" ของโค้ด ณ เวลานั้น |
| **Branch** | สาขาแยกสำหรับพัฒนา feature ใหม่ |
| **Merge** | รวม branch กลับเข้า main |
| **Push** | ส่งโค้ดจากเครื่องขึ้น GitHub |
| **Pull** | ดึงโค้ดล่าสุดจาก GitHub ลงเครื่อง |
| **Clone** | คัดลอก repo จาก GitHub ลงเครื่องครั้งแรก |

---

## 5. สร้าง GitHub Account

### ขั้นตอนการสมัคร

1. ไปที่ https://github.com
2. คลิก **"Sign up"** มุมขวาบน
3. กรอกข้อมูล
   - **Username** — ชื่อที่แสดงบน GitHub เลือกให้ดูเป็นมืออาชีพ (แนะนำ: ชื่อจริง หรือ ชื่อจริง+นามสกุล)
   - **Email address** — ใช้อีเมลจริงที่เช็คได้
   - **Password** — ตั้งให้แข็งแรง
4. ยืนยัน CAPTCHA
5. คลิก **"Create account"**
6. เลือก plan เป็น **Free**
7. ยืนยันอีเมล (เช็คกล่องข้อความในอีเมล)

### ตั้งค่า Profile เบื้องต้น

ไปที่ **Settings → Profile** แล้วกรอก

- **Name** — ชื่อจริงของเรา
- **Bio** — แนะนำตัวสั้นๆ เช่น "Junior Developer | ชอบ Web Development"
- **Location** — กรุงเทพฯ, Thailand
- **Website** — ใส่ได้ถ้ามี

> 💡 **Tip:** Username ที่ดีควรสั้น จำง่าย และดูเป็นมืออาชีพ  
> เพราะจะกลายเป็นส่วนหนึ่งของ URL เช่น `github.com/your-username`

---

## 6. GitHub Profile Markdown

### GitHub Profile README คืออะไร?

GitHub มีฟีเจอร์พิเศษที่ถ้าเราสร้าง repository ชื่อเดียวกับ Username และใส่ `README.md` ไว้ เนื้อหาใน README นั้นจะแสดงบนหน้า Profile ของเราโดยอัตโนมัติ

### ขั้นตอนสร้าง Profile README

1. ไปที่ https://github.com และล็อกอิน
2. คลิก **"+"** → **"New repository"**
3. ตั้งชื่อ Repository เป็น **Username ของคุณ** (ต้องตรงกันเป๊ะ!)
   - ถ้า Username คือ `somchai` ให้ตั้งชื่อ repo ว่า `somchai`
4. GitHub จะแจ้งว่า "✨ somchai/somchai is a special repository!"
5. ติ๊ก **"Add a README file"**
6. คลิก **"Create repository"**
7. คลิก **Edit** (ดินสอ) แล้วแก้ไข README

### ตัวอย่าง Profile README

คัดลอกโค้ดนี้ไปแก้ไขให้เป็นของคุณเอง:

```markdown
# สวัสดี! ฉันชื่อ [ชื่อของคุณ] 👋

## เกี่ยวกับฉัน
- 🎓 กำลังเรียน / ทำงานด้าน Web Development
- 🌱 กำลังเรียนรู้ **Git, JavaScript, และ React**
- 💬 ถามฉันเกี่ยวกับ HTML, CSS ได้เลย
- 📍 กรุงเทพฯ, ประเทศไทย

## ทักษะ
![HTML](https://img.shields.io/badge/HTML5-E34F26?style=flat&logo=html5&logoColor=white)
![CSS](https://img.shields.io/badge/CSS3-1572B6?style=flat&logo=css3&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=flat&logo=javascript&logoColor=black)
![Git](https://img.shields.io/badge/Git-F05032?style=flat&logo=git&logoColor=white)

## GitHub Stats
![GitHub Stats](https://github-readme-stats.vercel.app/api?username=YOUR_USERNAME&show_icons=true&theme=tokyonight)
```

> อย่าลืมเปลี่ยน `YOUR_USERNAME` ให้ตรงกับ Username จริงของคุณ

### Markdown Syntax พื้นฐาน

```markdown
# หัวข้อใหญ่ (H1)
## หัวข้อรอง (H2)
### หัวข้อย่อย (H3)

**ตัวหนา**
*ตัวเอียง*
~~ขีดทับ~~

- รายการแบบจุด
- รายการที่สอง
  - รายการย่อย

1. รายการแบบตัวเลข
2. ข้อสอง
3. ข้อสาม

`code แบบ inline`

[ลิงก์](https://example.com)

![รูปภาพ](https://example.com/image.png)

> blockquote หรือคำพูดอ้างอิง

| คอลัมน์ 1 | คอลัมน์ 2 |
|-----------|-----------|
| ข้อมูล 1  | ข้อมูล 2  |
```

---

## 7. git init และการสร้าง Repository

### git init คืออะไร?

`git init` คือคำสั่งที่เปลี่ยนโฟลเดอร์ธรรมดาให้กลายเป็น **Git Repository**  
มันจะสร้างโฟลเดอร์ซ่อน `.git/` ขึ้นมา ซึ่งเป็นที่เก็บประวัติทั้งหมด

### วิธีที่ 1 — สร้าง Repository ใหม่จากเครื่องเรา

```bash
# สร้างโฟลเดอร์และเข้าไป
mkdir my-project
cd my-project

# เริ่มต้น git repository
git init

# จะเห็นข้อความแบบนี้:
# Initialized empty Git repository in /path/to/my-project/.git/

# ตรวจสอบว่ามีโฟลเดอร์ .git แล้ว
ls -la
# จะเห็น .git/ อยู่ในนั้น
```

### วิธีที่ 2 — สร้าง Repository บน GitHub ก่อน แล้วเชื่อมกับเครื่อง

**ขั้นตอนบน GitHub:**

1. ไปที่ https://github.com
2. คลิก **"+"** → **"New repository"**
3. ตั้งชื่อ Repository
4. เลือก **Public** หรือ **Private**
5. ติ๊ก **"Add a README file"** (ถ้าอยากให้ GitHub สร้าง README ให้)
6. คลิก **"Create repository"**

**เชื่อมกับเครื่อง:**

```bash
# ไปที่โฟลเดอร์โปรเจกต์
cd my-project

# เริ่ม git
git init

# เชื่อมกับ GitHub (เปลี่ยน URL ให้ตรงของคุณ)
git remote add origin https://github.com/username/my-project.git

# ตรวจสอบว่าเชื่อมแล้ว
git remote -v
# origin  https://github.com/username/my-project.git (fetch)
# origin  https://github.com/username/my-project.git (push)
```

### ตรวจสอบ Repository

```bash
# ดูสถานะ repository
git status

# ดูว่า remote เชื่อมกับที่ไหน
git remote -v

# ดูว่าอยู่ branch ไหน
git branch
```

---

## 8. git config

### git config คืออะไร?

`git config` ใช้ตั้งค่าต่างๆ ของ Git โดยเฉพาะ **ชื่อและอีเมล** ที่จะแสดงใน commit ทุกอัน

### ระดับของ git config

| ระดับ | Option | ขอบเขต |
|-------|--------|---------|
| System | `--system` | ทุก user ในเครื่องนี้ |
| Global | `--global` | ทุก project ของ user นี้ |
| Local | `--local` | เฉพาะ project นี้เท่านั้น |

ส่วนใหญ่ใช้ `--global` ก็พอ

### ตั้งค่าพื้นฐาน (ทำแค่ครั้งเดียว)

```bash
# ตั้งชื่อผู้ใช้ (จะแสดงใน commit)
git config --global user.name "ชื่อ นามสกุล"

# ตั้งอีเมล (ควรใช้อีเมลเดียวกับที่สมัคร GitHub)
git config --global user.email "your@email.com"

# ตั้ง default editor เป็น VS Code
git config --global core.editor "code --wait"

# ตั้ง default branch name เป็น main (แทน master)
git config --global init.defaultBranch main
```

### ดูการตั้งค่าทั้งหมด

```bash
# ดูทุก config
git config --list

# ดู config เฉพาะตัว
git config user.name
git config user.email
```

### แก้ไข config โดยตรง

```bash
# เปิดไฟล์ config ด้วย VS Code
git config --global --edit
```

---

## 9. git credential

### Credential คืออะไร?

เมื่อเรา push โค้ดขึ้น GitHub Git ต้องรู้ว่าเราคือใคร และมีสิทธิ์ push จริงไหม  
นั่นคือหน้าที่ของ **Credential** (ข้อมูลยืนยันตัวตน)

### วิธียืนยันตัวตน 2 แบบหลัก

```
แบบที่ 1: HTTPS + Personal Access Token (PAT)  ← แนะนำสำหรับมือใหม่
แบบที่ 2: SSH Key                               ← ใช้ในองค์กร / มืออาชีพ
```

### วิธีที่ 1 — HTTPS + Personal Access Token (PAT)

GitHub ไม่รับ Password ปกติแล้ว ต้องใช้ **Token** แทน

**ขั้นตอนสร้าง Personal Access Token:**

1. ไปที่ GitHub → คลิกรูปโปรไฟล์มุมขวาบน → **Settings**
2. เลื่อนลงมาด้านล่างสุด → คลิก **"Developer settings"**
3. คลิก **"Personal access tokens"** → **"Tokens (classic)"**
4. คลิก **"Generate new token"** → **"Generate new token (classic)"**
5. ตั้งชื่อ Note เช่น "My Laptop"
6. เลือก Expiration (แนะนำ 90 days)
7. ติ๊ก **repo** (ให้สิทธิ์เข้าถึง repository)
8. คลิก **"Generate token"**
9. **คัดลอก token ทันที!** (จะไม่มีให้ดูอีกครั้ง)

**ใช้ Token ตอน Push:**

```bash
git push origin main
# Username: your-github-username
# Password: [วาง token ที่คัดลอกมา — ไม่มีอะไรแสดงขณะพิมพ์ นั่นคือปกติ]
```

**บันทึก Credential ไว้ ไม่ต้องพิมพ์ทุกครั้ง:**

```bash
# macOS — ใช้ Keychain เก็บ token
git config --global credential.helper osxkeychain

# Windows — ใช้ Windows Credential Manager
git config --global credential.helper manager

# Linux — เก็บใน memory 15 นาที
git config --global credential.helper cache

# Linux — เก็บถาวรในไฟล์ (ไม่แนะนำถ้าเครื่องใช้หลายคน)
git config --global credential.helper store
```

### วิธีที่ 2 — SSH Key (สำหรับผู้ที่ต้องการความสะดวกระยะยาว)

**ขั้นตอนสร้าง SSH Key:**

```bash
# สร้าง SSH Key (เปลี่ยน email ให้ตรงกับ GitHub)
ssh-keygen -t ed25519 -C "your@email.com"

# กด Enter 3 ครั้ง (ใช้ค่า default ทั้งหมด)

# ดู Public Key ที่สร้างขึ้น
cat ~/.ssh/id_ed25519.pub
# คัดลอกทั้งหมดตั้งแต่ ssh-ed25519 ... จนถึง email
```

**เพิ่ม SSH Key บน GitHub:**

1. ไปที่ GitHub → Settings → **SSH and GPG keys**
2. คลิก **"New SSH key"**
3. ตั้งชื่อ Title เช่น "My MacBook"
4. วาง Public Key ที่คัดลอกมา
5. คลิก **"Add SSH key"**

**ทดสอบการเชื่อมต่อ:**

```bash
ssh -T git@github.com
# Hi username! You've successfully authenticated...  ← สำเร็จ!
```

---

## 10. git clone

### git clone คืออะไร?

`git clone` คือการ **คัดลอก repository จาก GitHub ลงมาในเครื่องเรา** พร้อมทั้งประวัติ commit ทั้งหมด

ใช้เมื่อ:
- เริ่มทำงานในโปรเจกต์ที่มีอยู่แล้วบน GitHub
- ย้ายเครื่องใหม่ และต้องดึงโค้ดลงมา
- Fork โปรเจกต์ Open Source มาพัฒนาต่อ

### วิธี Clone Repository

**ขั้นตอนที่ 1 — หา URL ของ Repository:**

1. ไปที่ repo บน GitHub
2. คลิกปุ่ม **"<> Code"** (สีเขียว)
3. เลือก **HTTPS** หรือ **SSH**
4. คัดลอก URL

**ขั้นตอนที่ 2 — Clone ลงเครื่อง:**

```bash
# Clone แบบ HTTPS
git clone https://github.com/username/repo-name.git

# Clone แบบ SSH (ถ้าตั้งค่า SSH Key แล้ว)
git clone git@github.com:username/repo-name.git

# Clone แล้วตั้งชื่อโฟลเดอร์เอง
git clone https://github.com/username/repo-name.git my-folder-name

# Clone เฉพาะ branch ที่ต้องการ
git clone -b branch-name https://github.com/username/repo-name.git
```

**ขั้นตอนที่ 3 — เข้าไปในโฟลเดอร์และเริ่มทำงาน:**

```bash
cd repo-name
code .
```

### clone vs pull — ต่างกันอย่างไร?

| | `git clone` | `git pull` |
|--|-------------|------------|
| ใช้เมื่อ | ยังไม่มี repo ในเครื่อง | มี repo อยู่แล้ว อยากดึงของใหม่ |
| ทำอะไร | สร้างโฟลเดอร์ใหม่ + copy ทุกอย่าง | ดึงเฉพาะส่วนที่เปลี่ยนแปลง |
| ใช้บ่อยแค่ไหน | ครั้งแรกครั้งเดียว | ทุกวันก่อนเริ่มทำงาน |

### 🏋️ แบบฝึกหัดสุดท้าย — Clone และแก้ไข

```bash
# 1. Clone repository ที่ Instructor เตรียมให้
git clone https://github.com/instructor/workshop-exercise.git

# 2. เข้าไปในโฟลเดอร์
cd workshop-exercise

# 3. เปิดด้วย VS Code
code .

# 4. แก้ไขไฟล์ participants.md เพิ่มชื่อของคุณ

# 5. ดูสถานะ
git status

# 6. Add และ Commit
git add participants.md
git commit -m "feat: add [ชื่อของคุณ] to participants list"

# 7. Push ขึ้น GitHub
git push
```

---

## 📌 Cheat Sheet สรุปคำสั่งทั้งหมด

### Terminal

| คำสั่ง | ความหมาย |
|--------|-----------|
| `pwd` | ดู path ปัจจุบัน |
| `ls -la` | แสดงไฟล์ทั้งหมดรวมถึงไฟล์ซ่อน |
| `cd folder` | เข้าโฟลเดอร์ |
| `cd ..` | ออกมา 1 ระดับ |
| `mkdir name` | สร้างโฟลเดอร์ |
| `mkdir -p a/b/c` | สร้างโฟลเดอร์ซ้อนหลายชั้น |
| `touch file.txt` | สร้างไฟล์เปล่า |
| `cat file.txt` | อ่านเนื้อหาไฟล์ |
| `code .` | เปิด VS Code ที่โฟลเดอร์นี้ |
| `clear` | ล้างหน้าจอ |

### Git — ตั้งค่า

| คำสั่ง | ความหมาย |
|--------|-----------|
| `git config --global user.name "ชื่อ"` | ตั้งชื่อ |
| `git config --global user.email "email"` | ตั้งอีเมล |
| `git config --global init.defaultBranch main` | ตั้ง default branch |
| `git config --list` | ดูการตั้งค่าทั้งหมด |

### Git — Repository

| คำสั่ง | ความหมาย |
|--------|-----------|
| `git init` | เริ่ม git repository ใหม่ |
| `git clone URL` | คัดลอก repo จาก GitHub |
| `git remote add origin URL` | เชื่อม local กับ GitHub |
| `git remote -v` | ดู remote URL |

### Git — การทำงานประจำวัน

| คำสั่ง | ความหมาย |
|--------|-----------|
| `git status` | ดูสถานะไฟล์ |
| `git add file` | เพิ่มไฟล์เข้า staging |
| `git add .` | เพิ่มทุกไฟล์เข้า staging |
| `git commit -m "message"` | บันทึก commit |
| `git log --oneline` | ดูประวัติ commit |
| `git push` | ส่งโค้ดขึ้น GitHub |
| `git pull` | ดึงโค้ดล่าสุดจาก GitHub |

---

## 🎯 Flow สรุปทั้งหมด

```
1. ติดตั้ง VS Code
        ↓
2. เปิด Terminal (ใน VS Code หรือ แยก)
        ↓
3. สร้างโฟลเดอร์ด้วย mkdir → เข้าด้วย cd → เปิดด้วย code .
        ↓
4. สมัคร GitHub Account + ตั้ง Profile README
        ↓
5. git config (ตั้งชื่อ + อีเมล — ทำครั้งเดียว)
        ↓
6. ตั้งค่า Credential (Token หรือ SSH)
        ↓
7. git init (เริ่ม repo) หรือ git clone (ดึง repo ที่มีอยู่แล้ว)
        ↓
8. แก้ไขโค้ด → git add → git commit → git push
```

---

*Workshop นี้จัดทำสำหรับผู้เริ่มต้น — ใช้เวลารวมประมาณ 3–4 ชั่วโมง*
