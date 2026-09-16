# Assignment 03 — Docker: Build, Publish, Pull, Compose

## ข้อมูลนักศึกษา

* ชื่อ: Pattharaprapha Wongmuengklang
* รหัสนักศึกษา: 671540005019-8
* สาขา: วิศวกรรมคอมพิวเตอร์
* มหาวิทยาลัย: มหาวิทยาลัยกาฬสินธุ์

## Docker Hub

* Docker Hub: https://hub.docker.com/r/pattharaprapha/ceksu-badge
* Image ของตนเอง: `pattharaprapha/ceksu-badge`
* Image ของเพื่อน: `kittiphat26/ceksu-badge:1.0`
* ชื่อเพื่อน: Kittiphat
* รหัสนักศึกษาเพื่อน: `671540005012-3`

## คำตอบ

### 1. หลัง pull tag 1.0 กลับมา หน้าเว็บแสดง Version อะไร เพราะเหตุใด และเรื่องนี้บอกอะไรเกี่ยวกับ tag ของ Docker image

หลังจาก pull tag `1.0` กลับมา หน้าเว็บแสดง `Version 1.0` เพราะ tag `1.0` อ้างอิง image ที่สร้างไว้ในเวอร์ชันนั้น ส่วน `1.1` เป็น tag อีกเวอร์ชันหนึ่งที่มีเนื้อหาต่างกัน จึงทำให้การ pull `1.0` กลับมาได้เนื้อหาเดิมของ Version 1.0

### 2. เมื่อแก้ index.html แล้วสั่ง docker compose up -d เกิดอะไรขึ้น เพราะอะไร และคำสั่งที่ถูกต้องคืออะไร

หลังจากแก้ `index.html` แล้วสั่ง `docker compose up -d` หน้าเว็บอาจยังแสดงข้อมูลเดิม เพราะ image เดิมยังไม่ได้ถูก build ใหม่ คำสั่งที่ถูกต้องคือ `docker compose up -d --build` เพื่อให้ Docker สร้าง image ใหม่จากไฟล์ที่แก้ไข

### 3. service friend แก้ข้อความบนหน้าเว็บไม่ได้ ในขณะที่ service mybadge แก้ได้ อธิบายสาเหตุ

`mybadge` ใช้ `build: .` จึงสามารถสร้าง image ใหม่จาก source code ในเครื่องได้ ส่วน `friend` ใช้ `image:` ที่ดึงมาจาก Docker Hub และเราไม่มี source code ของเพื่อน จึงไม่สามารถแก้หน้าเว็บของเพื่อนได้โดยตรง

### 4. ถ้าต้องส่งงานให้รุ่นน้องนำไปรันต่อ จะเลือกส่งลิงก์ Docker Hub หรือ GitHub repo เพราะอะไร มีข้อดีข้อเสียอย่างไร

Docker Hub เหมาะสำหรับการแจกจ่าย image เพราะสามารถ pull แล้วนำไปรันได้ทันทีโดยไม่ต้องมี source code ข้อเสียคือแก้ไข source code โดยตรงไม่ได้ ส่วน GitHub เหมาะสำหรับการแจกจ่าย source code ซึ่งสามารถศึกษาและแก้ไขได้ แต่ผู้รับต้องเตรียม environment และ build image เอง

### 5. หากเพื่อน push image ทับ tag 1.0 เดิมด้วยเนื้อหาใหม่ ไฟล์ compose ของคุณจะได้รับผลกระทบอย่างไร และจะป้องกันอย่างไร

ถ้าเพื่อน push image ใหม่ทับ tag `1.0` ผู้ที่ pull image ในภายหลังอาจได้รับเนื้อหาใหม่ ทำให้ผลลัพธ์ของ Compose เปลี่ยนได้ การป้องกันทำได้โดยใช้ tag เวอร์ชันที่ชัดเจน เช่น `1.1` หรือใช้ image digest เพื่ออ้างอิง image ที่แน่นอน

## การทดสอบ

* Local Docker port: `8083`
* Friend Docker port: `8084`
* Compose mybadge: `8083`
* Compose friend: `8084`
* Version 1.0: สำเร็จ
* Version 1.1: สำเร็จ
* Docker Hub push: สำเร็จ
* Docker pull: สำเร็จ
* Friend image inspect: สำเร็จ
* Docker Compose: สำเร็จ
* Updated by compose: สำเร็จหลังใช้ `docker compose up -d --build`
