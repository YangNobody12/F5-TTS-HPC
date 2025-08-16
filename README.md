# F5-TTS-HPC

**F5-TTS-HPC** เป็นเวอร์ชันที่ปรับแต่งมาจาก [F5-TTS](https://github.com/SWivid/F5-TTS)  
สำหรับใช้งานบน **Supercomputer / HPC Cluster** โดยปิดการดาวน์โหลดโมเดลอัตโนมัติ (auto-download)  
และให้ผู้ใช้จัดการดาวน์โหลดเอง

---

## ✨ Features

✅ เหมาะสำหรับสภาพแวดล้อมที่ไม่สามารถเชื่อมต่ออินเทอร์เน็ตตรง ๆ  
✅ ควบคุมเวอร์ชันของโมเดลเองได้  
✅ รองรับทั้ง **Inference** และ **Training / Fine-tuning**

---

## 📂 โครงสร้างไฟล์

หลังจากติดตั้งโค้ดแล้ว ควรสร้างโฟลเดอร์ดังนี้:

```bash
F5-TTS-HPC/
│
├── pretrain_checkpoint/    # สำหรับเก็บ pretrain model (จาก HuggingFace)
│   └── F5TTS_v1_Base
│       ├── model_1250000.pt
│       └── vocab.txt
│
├── vocoder/                # สำหรับเก็บ vocoder (เช่น Vocos) 
│   ├── config.yaml
│   └── pytorch_model.bin
│
└── src/
    └── f5_tts/             # source code
```
**📥 การดาวน์โหลดโมเดล (Manual Download)**
1. Pretrain Model (F5-TTS)

ดาวน์โหลดจาก HuggingFace:
👉 https://huggingface.co/SWivid/F5-TTS/tree/main

นำไฟล์ .pt หรือ checkpoint ใส่ในโฟลเดอร์:

F5-TTS-HPC/pretrain_checkpoint/

2. Vocoder (Vocos)

ดาวน์โหลดจาก HuggingFace:
👉 https://huggingface.co/charactr/vocos-mel-24khz/tree/main

นำไฟล์ config.yaml และ pytorch_model.bin ไปวางในโฟลเดอร์:

F5-TTS-HPC/vocoder/

**⚙️ การติดตั้ง สร้าง environment สำหรับ Python 3.11**
```bash
conda create -n f5-tts-hpc python=3.11
conda activate f5-tts-hpc
```

**ติดตั้ง PyTorch ตาม GPU/Device ที่ใช้ (CUDA, ROCm, Intel, Apple MPS)**
*ตัวอย่าง NVIDIA CUDA 11.8*
```bash
pip install torch==2.3.0+cu118 torchaudio==2.3.0+cu118 --extra-index-url https://download.pytorch.org/whl/cu118
```
# clone repo
```bash
git clone https://github.com/yourname/F5-TTS-HPC.git
cd F5-TTS-HPC
pip install -e .
```

📌 หมายเหตุสำหรับ HPC

❌ ไม่มีการดาวน์โหลดไฟล์อัตโนมัติ

✅ ผู้ใช้ต้องเตรียมโมเดลเองและวางไว้ในโฟลเดอร์ตามที่กำหนด

🎯 เหมาะสำหรับการรันงานบน เครื่อง LANTA และ HPC Cluster อื่น ๆ

🙏 ขอบคุณ

ขอขอบคุณ HPC-Ignite สำหรับการสนับสนุนการทดลองโมเดลนี้บนเครื่อง LANTA Supercomputer