# AIB2025 ChronoCall-Q

## 🧠 Project Overview

**ChronoCall-Q** คือโปรเจคที่พัฒนาโมเดล Qwen3 ให้สามารถรับคำสั่งจากผู้ใช้เพื่อจัดการตารางเวลา (Schedule)  
เช่น การเพิ่ม ลบ แก้ไข และดูนัดหมาย ให้มีความแม่นยำมากขึ้น
และเชื่อมต่อกับ Google Calendar เพื่อเพิ่มประสิทธิภาพในการจัดการเวลา

---

## 🎯 เป้าหมายหลัก

- พัฒนาโมเดลที่เข้าใจคำสั่งเกี่ยวกับการจัดการตารางเวลา  
- เชื่อมต่อและจัดการนัดหมายบน Google Calendar โดยอัตโนมัติ  
- สร้างระบบที่ตอบสนองคำสั่งได้อย่างมีประสิทธิภาพ

---

## 🔍 กระบวนการพัฒนา

1. **Data Collection**  
   สร้างชุดข้อมูลโดยรวบรวม Component ที่ได้จากแบบสอบถาม  
   และนำ Component เหล่านั้นมาสร้างตัวอย่างคำสั่งที่เกี่ยวข้องกับการจัดการตารางเวลา

2. **Data Cleaning**  
   ทำความสะอาดและจัดระเบียบข้อมูลให้เหมาะสมสำหรับการฝึกโมเดล  

3. **Fine-tuning**  
   ปรับแต่งโมเดล Qwen3 ด้วยชุดข้อมูลที่เตรียมไว้ เพื่อให้สามารถเข้าใจและตอบสนองคำสั่งได้  

4. **Evaluation**  
   ทดสอบและประเมินผลโมเดลเพื่อวัดประสิทธิภาพ  

5. **Deployment**  
   นำโมเดลไปใช้งานจริงโดยเชื่อมต่อกับ Google Calendar ผ่านระบบ Streamlit  

---

## โครงสร้างโปรเจค

```bash
.
├── Data
│ └── (ไฟล์ JSON ที่ได้มาจากโค้ดเจน, DataSplitter + Converter)
├── notebook
│ ├── Evaluate
│ │ ├── (โฟลเดอร์โมเดลต่างๆ)
│ │ │ ├── json Data สำหรับ Evaluate
│ │ │ ├── json Data ที่ Model predict ออกมา
│ │ │ ├── json tool
│ │ │ ├── notebook สำหรับให้ Model predict
│ │ │ └── notebook สำหรับทำ Accuracy และ ConfusedMatrix
│ ├── Finetuned
│ │ ├── (โฟลเดอร์โมเดลต่างๆ)
│ │ │ ├── notebook สำหรับ Finetune โมเดล
│ │ │ ├── json Data (พร้อมสำหรับ Finetune)
│ │ │ └── json tool
│ ├── Spliter_and_Converter
│ │ ├── notebook สำหรับ Convert+Split+สลับข้อมูลให้อยู่ในรูปแบบพร้อม Finetune + รวม Data 2 ชุด
│ │ ├── json Data 1
│ │ ├── json Data 2
│ │ └── json Data ที่ถูก Convert จาก notebook อันแรก (พร้อมสำหรับ Finetune)
├── script
│ ├── โฟลเดอร์เก็บไฟล์ JSON component สำหรับสร้าง Dataset
│ ├── Python script สำหรับ Generate Dataset แบบที่ 1
│ ├── Python script สำหรับ Generate Dataset แบบที่ 2
│ ├── dataset.json แบบที่ 1
│ └── dataset.json แบบที่ 2
└── streamlit_deploy
└── ไฟล์สำหรับ Deploy ระบบด้วย Streamlit
```

---

## รายละเอียดแต่ละโฟลเดอร์

### 1. Data
โฟลเดอร์นี้เก็บไฟล์ JSON ที่ผ่านการสร้าง แบ่ง และแปลงข้อมูลเรียบร้อยแล้ว  
จนได้ Data ที่พร้อมสำหรับนำไปใช้ในการ Finetune โมเดล

### 2. notebook

- **Evaluate:**  
  โฟลเดอร์สำหรับเก็บโมเดลแต่ละชุด พร้อมไฟล์ JSON สำหรับการประเมินผล  
  - ไฟล์ JSON สำหรับ Evaluate  
  - ไฟล์ JSON ที่โมเดลทำการ Predict  
  - ไฟล์ JSON สำหรับ Tool  
  - Notebook สำหรับให้โมเดล Predict  
  - Notebook สำหรับคำนวณ Accuracy และสร้าง Confusion Matrix

- **Finetuned:**  
  โฟลเดอร์เก็บโมเดลแต่ละชุดที่ผ่านการ Finetune  
  - Notebook สำหรับ Finetune โมเดล  
  - ไฟล์ JSON ที่ถูก Convert แล้ว พร้อมสำหรับ Finetune  
  - ไฟล์ JSON Tool

- **Spliter_and_Converter**  
  - Notebook สำหรับ Convert + Split + สลับข้อมูล และรวมข้อมูล 2 ชุด เพื่อเตรียมสำหรับ Finetune  
  - ไฟล์ JSON Data 1 และ Data 2  
  - ไฟล์ JSON ที่ถูก Convert แล้ว พร้อมสำหรับ Finetune

### 3. script

เก็บไฟล์และสคริปต์ที่เกี่ยวข้องกับการสร้าง Dataset  
- โฟลเดอร์เก็บ JSON component สำหรับสร้าง Dataset  
- Python script สำหรับ Generate Dataset แบบที่ 1  
- Python script สำหรับ Generate Dataset แบบที่ 2  
- dataset.json แบบที่ 1 และ แบบที่ 2 หลังผ่านการสร้าง

### 4. streamlit_deploy

ไฟล์สำหรับการ Deploy ด้วย Streamlit

---

## วิธีใช้งานเบื้องต้น

1. ใช้ ไฟล์ python ในโฟลเดอร์ `script` สำหรับสร้าง Dataset
2. ใช้ Notebook ในโฟลเดอร์ `notebook/Spliter_and_Converter` เพื่อเตรียมข้อมูล
3. ใช้ Notebook ในโฟลเดอร์ `notebook/Finetuned` Finetune โมเดล  
4. ใช้ Notebook ใน `notebook/Evaluate` เพื่อทดสอบและประเมินผลโมเดล    
5. ใช้ไฟล์ใน `streamlit_deploy` สำหรับ Deploy ระบบให้ใช้งานผ่าน Web Interface

---
