---
type: knowledge-note
created: 2026-05-23 15:07
tags:
aliases: []
references:
---


### Summary

> [!abstract] 
> NVIDIA DeepStream เป็น Multi-Stream Video Analytics Framework ที่ทำงานอยู่บน GStreamer (Hardware-accelerated pipeline) โดยดึงข้อมูลจากโมเดลระดับ `.engine` มาประมวลผลผ่าน Zero-copy memory path



1. **Gst-nvstreammux (Batching Engine)**
* หัวใจหลักในการทำ **Dynamic Batching** รับ Input Streams จากหลายกล้องพร้อมกัน แล้วทำการจัดกลุ่มเฟรมรวมเป็น Single Batch ก่อนส่งต่อให้ AI Inference Engine (ช่วยเพิ่ม GPU Utilization ให้เต็มประสิทธิภาพบน Edge)

1. **Gst-nvinfer (Inference Engine)**
* ปลั๊กอินที่ทำหน้าที่โหลดไฟล์ TensorRT `.engine` เข้ามาเพื่อรันโมเดล สามารถตั้งค่าผ่าน `config_infer.txt` เพื่อกำหนดประเภทการทำงาน:
* **PGIE (Primary GIE):** ใช้สำหรับทำโมเดลตัวแรกสุด (มักจะเป็น One-step Object Detection เช่น YOLO เพื่อหา Region of Interest)
* **SGIE (Secondary GIE):** รันต่อจาก PGIE โดยดึงเฉพาะ Bounding Box ที่ตัดครอปไว้มาทำ Classification หรือ Feature Extraction ต่อ (เช่น ตรวจจับรถใน PGIE แล้วส่งแผ่นป้ายมาอ่านทะเบียนใน SGIE)

1. **Gst-nvtracker (State Tracking)**
* ปลั๊กอินสำหรับใส่ Object ID ให้กับวัตถุที่ตรวจจับได้ ช่วยประหยัด Resource ของ AI เพราะแทนที่จะต้องทำ Heavy Detection ทุกๆ เฟรม ระบบจะใช้การ Track เคลื่อนที่ตามวัตถุเดิมแทนในเฟรมถัดๆ ไป

 
 
## Connections
* **Parent:** [[ ]]
* **Similar:** [[ ]]