# 🎓 FriendFind — แอปพลิเคชันค้นหาเพื่อนเรียนและสร้างกลุ่มติว

FriendFind เป็นโปรเจกต์พัฒนาแอปพลิเคชันเพื่อช่วยให้นักศึกษาค้นหาเพื่อนที่มีความสนใจหรือกำลังศึกษาในรายวิชาเดียวกัน โดยมีแนวคิดในการเชื่อมต่อนักศึกษาที่มีเป้าหมายการเรียนคล้ายกัน เพื่อส่งเสริมการแลกเปลี่ยนความรู้ การทำงานร่วมกัน และการสร้างสังคมการเรียนรู้

ระบบประกอบด้วยแอปพลิเคชันบนมือถือสำหรับนักศึกษา ระบบ Backend สำหรับจัดการข้อมูลและการเชื่อมต่อฐานข้อมูล รวมถึงหน้าเว็บไซต์สำหรับผู้ดูแลระบบ (Admin Dashboard)

## ✨ ฟีเจอร์หลัก

<img width="881" height="329" alt="image" src="https://github.com/user-attachments/assets/2d9461b5-efc0-45d6-87c0-b01af6fb31db" />

### 📱 สำหรับนักศึกษา (Mobile Application)

- **สมัครสมาชิกและเข้าสู่ระบบ** — รองรับการลงทะเบียนและเข้าสู่ระบบ
- **จัดการโปรไฟล์** — แก้ไขข้อมูลส่วนตัว คณะ ชั้นปี และความสนใจ
- **ค้นหาเพื่อนเรียน** — ค้นหาและเลือกเชื่อมต่อกับนักศึกษาที่มีความสนใจใกล้เคียงกัน
- **ระบบจับคู่ (Matching)** — แสดงผู้ใช้งานเพื่อเลือกเชื่อมต่อผ่านระบบ Like และ Match
- **จัดการรายวิชา** — เลือกรายวิชาที่กำลังศึกษาและจัดการข้อมูลรายวิชา
- **สร้างกลุ่มเรียน** — สร้างกลุ่มสำหรับการเรียนหรือการติวร่วมกัน
- **ค้นหาและเข้าร่วมกลุ่ม** — ค้นหากลุ่มเรียนและส่งคำขอเข้าร่วม
- **จัดการสมาชิกกลุ่ม** — เพิ่มสมาชิกและจัดการคำขอเข้าร่วมกลุ่ม
- **ระบบแชต** — รองรับการสนทนาระหว่างผู้ใช้งาน
- **ระบบแจ้งเตือน** — แสดงการแจ้งเตือนที่เกี่ยวข้องกับกิจกรรมภายในระบบ

### 🖥️ สำหรับผู้ดูแลระบบ (Admin Dashboard)

- **Dashboard** — แสดงภาพรวมข้อมูลของระบบ
- **จัดการผู้ใช้งาน** — ตรวจสอบและจัดการข้อมูลนักศึกษา
- **จัดการรายวิชา** — จัดการข้อมูลรายวิชาในระบบ
- **จัดการกลุ่มเรียน** — ตรวจสอบและจัดการกลุ่มเรียน
- **ระบบเข้าสู่ระบบผู้ดูแล** — แยกส่วนการเข้าถึงสำหรับผู้ดูแลระบบ

## 🛠️ เทคโนโลยีที่ใช้

| ส่วนประกอบ | เทคโนโลยี |
|---|---|
| Mobile Application | React Native, Expo |
| Frontend Navigation | React Navigation |
| Backend | Node.js, Express.js |
| Database | MySQL |
| Database Driver | mysql2 |
| Authentication | JWT |
| Password Hashing | bcryptjs |
| Admin Dashboard | React, Vite |
| Dashboard Charts | Recharts |
| HTTP Client | Axios |
| Containerization | Docker, Docker Compose |

## 🏗️ ภาพรวมสถาปัตยกรรมระบบ

FriendFind ใช้สถาปัตยกรรมแบบ Client-Server โดยแยกส่วนแอปพลิเคชันผู้ใช้งาน ระบบ API และฐานข้อมูลออกจากกัน

```text
       นักศึกษา                    ผู้ดูแลระบบ
          |                            |
          v                            v
  React Native / Expo             Admin Dashboard
          |                         React / Vite
          |                            |
          +-------------+--------------+
                        |
                        v
                  RESTful API
                  Node.js
                  Express.js
                        |
                        v
                   MySQL Database
```

## 🗄️ โครงสร้างฐานข้อมูล

ระบบใช้ MySQL ในการจัดเก็บข้อมูลหลัก โดยมีตารางสำคัญดังนี้

| ตาราง | รายละเอียด |
|---|---|
| users | ข้อมูลผู้ใช้งาน |
| subjects | ข้อมูลรายวิชา |
| user_subjects | ความสัมพันธ์ระหว่างผู้ใช้งานกับรายวิชา |
| matches | ข้อมูลการจับคู่ระหว่างผู้ใช้งาน |
| study_groups | ข้อมูลกลุ่มเรียน |
| group_members | ข้อมูลสมาชิกและสถานะการเข้าร่วมกลุ่ม |

## 📁 โครงสร้างโปรเจกต์

```text
FriendFind/
│
├── frontend/                 # แอปพลิเคชัน React Native
│   ├── components/           # Components ที่ใช้ร่วมกัน
│   ├── constants/            # ค่าคงที่ของระบบ
│   ├── context/              # Context สำหรับจัดการ State
│   ├── navigation/           # ระบบ Navigation
│   ├── screens/               # หน้าจอแอปพลิเคชัน
│   ├── services/              # การเชื่อมต่อ API
│   └── utils/                 # ฟังก์ชันช่วยเหลือ
│
├── backend/
│   └── backend/
│       ├── config/            # การตั้งค่าระบบ
│       ├── controllers/       # จัดการ Business Logic
│       ├── middleware/        # Middleware
│       ├── models/            # Models
│       ├── routes/            # API Routes
│       ├── app.js             # Express Application
│       └── server.js          # จุดเริ่มต้น Backend
│
├── admin-web/                 # เว็บไซต์ผู้ดูแลระบบ
│   └── src/
│       ├── components/
│       └── pages/
│
├── schema.sql                 # โครงสร้างฐานข้อมูล
├── docker-compose.yml         # การตั้งค่า Docker
├── .env.docker.example        # ตัวอย่าง Environment Variables
└── README.md
```

## 🚀 การติดตั้งและเริ่มต้นใช้งาน

### 1. สิ่งที่ต้องเตรียม

- Node.js และ npm
- Docker Desktop และ Docker Compose
- Expo Go สำหรับทดสอบแอปพลิเคชันบนมือถือ
- Git

### 2. ดาวน์โหลดโปรเจกต์

```bash
git clone https://github.com/XBalanceZ/FriendFind.git

cd FriendFind
```

### 3. ตั้งค่า Environment Variables

คัดลอกไฟล์ตัวอย่างสำหรับ Docker

```bash
cp .env.docker.example .env
```

แก้ไขไฟล์ `.env` ให้เหมาะสมกับสภาพแวดล้อมที่ใช้งาน

```env
MYSQL_ROOT_PASSWORD=your_secure_password
MYSQL_DATABASE=study_match_db
MYSQL_PORT=3306
BACKEND_PORT=5000
JWT_SECRET=your_secret_key
```

**หมายเหตุ:** ควรเปลี่ยนรหัสผ่านและ JWT Secret ก่อนนำระบบไปใช้งานจริง และไม่ควรนำไฟล์ `.env` ที่มีข้อมูลลับขึ้น GitHub

### 4. เริ่มต้น Backend และ Database ด้วย Docker

```bash
docker compose up --build -d
```

ตรวจสอบสถานะ Container

```bash
docker compose ps
```

ตรวจสอบการทำงานของ Backend ผ่าน Health Check

```text
http://localhost:5000/api/health
```

### 5. เริ่มต้น Mobile Application

เปิด Terminal ใหม่ แล้วดำเนินการดังนี้

```bash
cd frontend

npm install

npx expo start
```

จากนั้นสแกน QR Code ด้วยแอป Expo Go เพื่อเปิดใช้งานบนมือถือ

หากทดสอบบนมือถือจริง ต้องตั้งค่า `EXPO_PUBLIC_API_URL` ในไฟล์ `frontend/.env` ให้ชี้ไปยัง IP ของเครื่องที่รัน Backend เช่น

```env
EXPO_PUBLIC_API_URL=http://YOUR_PC_LAN_IP:5000
```

มือถือและเครื่องที่รัน Backend ต้องเชื่อมต่อเครือข่ายที่สามารถติดต่อกันได้

### 6. เริ่มต้น Admin Dashboard

เปิด Terminal ใหม่

```bash
cd admin-web

npm install

npm run dev
```

จากนั้นเปิด URL ที่ Vite แสดงใน Terminal เพื่อเข้าใช้งานหน้า Admin Dashboard

## 🐳 การจัดการ Docker

เริ่มต้นระบบ

```bash
docker compose up --build -d
```

หยุดการทำงานของ Container

```bash
docker compose down
```

ตรวจสอบ Logs ของ Backend

```bash
docker compose logs -f backend
```

เข้าใช้งาน phpMyAdmin

```text
http://localhost:8080
```

## ⚠️ ข้อควรระวัง

- ไฟล์ `schema.sql` มีคำสั่งลบและสร้างตารางใหม่ การนำไปใช้กับฐานข้อมูลเดิมอาจทำให้ข้อมูลสูญหาย ควรสำรองข้อมูลก่อนเสมอ
- ควรตั้งค่า JWT Secret และข้อมูลเชื่อมต่อฐานข้อมูลผ่าน Environment Variables
- ควรตรวจสอบสิทธิ์การเข้าถึง API และการกำหนดสิทธิ์ผู้ดูแลระบบก่อนใช้งานจริง
- ควรตรวจสอบการตั้งค่า CORS และความปลอดภัยของฐานข้อมูลก่อนนำระบบขึ้น Production

## 🔮 แนวทางการพัฒนาต่อ

- พัฒนาระบบ Matching ให้สามารถแนะนำเพื่อนจากรายวิชาและความสนใจได้ดียิ่งขึ้น
- เพิ่มระบบแชตแบบ Real-time
- เพิ่มระบบ Push Notification
- ปรับปรุงประสิทธิภาพและความปลอดภัยของ API
- เพิ่มระบบจัดการตารางเวลาเรียนและนัดหมายติว
- พัฒนาหน้า Admin Dashboard ให้รองรับการวิเคราะห์ข้อมูลได้มากขึ้น

## 👥 ข้อมูลโปรเจกต์

- **ชื่อโปรเจกต์:** FriendFind
- **ประเภท:** Team Project
- **GitHub Repository:** [XBalanceZ/FriendFind](https://github.com/XBalanceZ/FriendFind)

---

*FriendFind — Connecting Students, Growing Together.*

