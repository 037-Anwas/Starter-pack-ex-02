# Starter-pack-ex-02

# 🧑‍💻 Workshop: IDE, Terminal & Git Fundamentals

> คู่มือ Workshop ฉบับสมบูรณ์ สำหรับผู้เริ่มต้นที่ยังไม่เคยใช้ Git มาก่อน  
> ใช้เวลารวมประมาณ **3–4 ชั่วโมง**

---

## 📋 สารบัญ

1. [git init และการสร้าง Repository](#7-git-init-และการสร้าง-repository)
2. [git config](#8-git-config)
3. [git credential](#9-git-credential)
4. [git clone](#10-git-clone)

---

## 1. git init และการสร้าง Repository

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

## 2. git config

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

## 3. git credential

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

## 4. git clone

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
