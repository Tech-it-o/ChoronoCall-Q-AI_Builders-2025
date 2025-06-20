# AIB2025 ChronoCall-Q

## 🧠 Project Overview

**ChronoCall-Q** is a project that fine-tunes the Qwen3 model to understand scheduling-related commands  
such as adding, deleting, editing, and viewing events — and integrates with Google Calendar to improve time management.

**ChronoCall-Q** คือโปรเจคที่พัฒนาโมเดล Qwen3 ให้สามารถรับคำสั่งจากผู้ใช้เพื่อจัดการตารางเวลา (Schedule)  
เช่น การเพิ่ม ลบ แก้ไข และดูนัดหมาย ให้มีความแม่นยำมากขึ้น
และเชื่อมต่อกับ Google Calendar เพื่อเพิ่มประสิทธิภาพในการจัดการเวลา

---

## 🎯 Main Goals | เป้าหมายหลัก

- Train a model to understand natural language scheduling commands  
- Automatically manage appointments on Google Calendar  
- Build a responsive and efficient scheduling assistant system

- พัฒนาโมเดลให้เข้าใจคำสั่งที่เกี่ยวข้องกับการจัดการตารางเวลา  
- เชื่อมต่อและจัดการนัดหมายบน Google Calendar โดยอัตโนมัติ  
- สร้างระบบตอบสนองคำสั่งได้อย่างแม่นยำและรวดเร็ว

---

## 🔍 Development Pipeline | กระบวนการพัฒนา

1. **Data Collection**  
   Collect and design scheduling command components from user input → used to generate training examples  
   **การรวบรวมข้อมูล**: สร้างชุดข้อมูลจาก Component ที่ได้จากแบบสอบถาม เพื่อสร้างตัวอย่างคำสั่ง

2. **Data Cleaning**  
   Format and clean the data for fine-tuning  
   **ทำความสะอาดข้อมูล**: ปรับโครงสร้างและจัดระเบียบข้อมูลให้เหมาะสม

3. **Fine-tuning**  
   Train Qwen3 on the prepared dataset  
   **ปรับแต่งโมเดล**: Fine-tune โมเดลด้วยข้อมูลที่เตรียมไว้

4. **Evaluation**  
   Assess model performance with test data and metrics  
   **ประเมินผล**: ทดสอบและประเมินความแม่นยำของโมเดล

5. **Deployment**  
   Deploy the model with a Streamlit interface integrated with Google Calendar  
   **นำไปใช้งานจริง**: ใช้งานโมเดลผ่าน Streamlit และเชื่อมต่อ Google Calendar

---

## 📁 Project Structure | โครงสร้างโปรเจค

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

## 📂 Folder Descriptions | รายละเอียดแต่ละโฟลเดอร์

### 1. `Data`
This folder contains JSON files that have been generated, split, and transformed into a format ready for model fine-tuning.  
โฟลเดอร์นี้เก็บไฟล์ JSON ที่ผ่านการสร้าง แบ่ง และแปลงข้อมูลเรียบร้อยแล้ว จนได้ Data ที่พร้อมสำหรับนำไปใช้ในการ Finetune โมเดล  

---

### 2. `notebook`

#### **Evaluate**
Folder for each model used in evaluation.  
- JSON file for evaluation input  
- JSON predictions generated by the model  
- Tool JSON definition  
- Notebook to run model predictions  
- Notebook to compute accuracy and generate confusion matrix  

โฟลเดอร์สำหรับเก็บโมเดลแต่ละชุด พร้อมไฟล์ JSON สำหรับการประเมินผล  
- ไฟล์ JSON สำหรับ Evaluate  
- ไฟล์ JSON ที่โมเดลทำการ Predict  
- ไฟล์ JSON สำหรับ Tool  
- Notebook สำหรับให้โมเดล Predict  
- Notebook สำหรับคำนวณ Accuracy และสร้าง Confusion Matrix  

#### **Finetuned**
Folder containing fine-tuned models and training notebooks.  
- Notebook for fine-tuning  
- Converted JSON dataset ready for training  
- Tool JSON file  

โฟลเดอร์เก็บโมเดลแต่ละชุดที่ผ่านการ Finetune  
- Notebook สำหรับ Finetune โมเดล  
- ไฟล์ JSON ที่ถูก Convert แล้ว พร้อมสำหรับ Finetune  
- ไฟล์ JSON Tool  

#### **Spliter_and_Converter**
Notebook for converting, splitting, and shuffling the dataset, and combining two data sources for training.  
- JSON data files (before and after conversion)  

Notebook สำหรับ Convert + Split + สลับข้อมูล และรวมข้อมูล 2 ชุด เพื่อเตรียมสำหรับ Finetune  
- ไฟล์ JSON Data 1 และ Data 2  
- ไฟล์ JSON ที่ถูก Convert แล้ว พร้อมสำหรับ Finetune  

---

### 3. `script`
Contains all scripts and files used for dataset generation.  
- Folder with JSON components for dataset creation  
- Python scripts for generating datasets (Type 1 & 2)  
- Resulting `dataset.json` files for each method  

เก็บไฟล์และสคริปต์ที่เกี่ยวข้องกับการสร้าง Dataset  
- โฟลเดอร์เก็บ JSON component สำหรับสร้าง Dataset  
- Python script สำหรับ Generate Dataset แบบที่ 1 และ แบบที่ 2  
- dataset.json หลังผ่านการสร้าง

---

### 4. `streamlit_deploy`
Deployment files for launching the scheduling assistant using Streamlit interface.  
ไฟล์สำหรับการ Deploy ด้วย Streamlit  

---

## 🚀 Getting Started | วิธีใช้งานเบื้องต้น

1. Use the Python script in the `script` folder to generate a dataset.  
   ใช้ไฟล์ Python ในโฟลเดอร์ `script` สำหรับสร้าง Dataset  

2. Use notebooks in `notebook/Spliter_and_Converter` to convert and prepare data.  
   ใช้ Notebook ในโฟลเดอร์ `notebook/Spliter_and_Converter` เพื่อเตรียมข้อมูล  

3. Use the notebook in `notebook/Finetuned` to fine-tune the model.  
   ใช้ Notebook ในโฟลเดอร์ `notebook/Finetuned` สำหรับ Fine-tune โมเดล  

4. Use the notebook in `notebook/Evaluate` to test and evaluate model performance.  
   ใช้ Notebook ใน `notebook/Evaluate` เพื่อทดสอบและประเมินผลโมเดล  

5. Deploy the full system using files in the `streamlit_deploy` folder through Streamlit Web UI.  
   ใช้ไฟล์ใน `streamlit_deploy` สำหรับ Deploy ระบบให้ใช้งานผ่าน Web Interface  

---

## 👾 Link

Medium : https://medium.com/@techitotamani.irl/aib2025-chronocall-q-f46820ba5caa

Space : https://aib-2025-chronocall-q-01.streamlit.app/
