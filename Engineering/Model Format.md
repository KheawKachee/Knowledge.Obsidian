---
type: knowledge-note
created: 2026-05-23 15:05
tags:
aliases: []
references:
---


### Summary

> [!abstract] 
> 



### **.pt / .pth (PyTorch Model)**
* **What it is:** ไฟล์บันทึก Weights (และอาจรวมคลาสโครงสร้างโมเดล) ที่ได้จาก PyTorch Direct Saving โดยใช้ Python Pickling
* ไม่เหมาะสำหรับการทำ Production บน Edge Device เพราะต้องการ Python Runtime และ PyTorch Library เต็มรูปแบบในการรัน ซึ่งกิน Resource (CPU/Memory) มหาศาลและขาด Hardware Optimization


### **.onnx (Open Neural Network Exchange)**
* **What it is:** ฟอร์แมตกลางที่เป็นเสมือน "สะพานเชื่อม" (Universal Intermediate Representation) แปลง Operators จากโมเดลของค่ายต่างๆ ให้กลายเป็น Computational Graph อิสระ
* ใช้สำหรับ Export ออกมาจาก PyTorch เพื่อเตรียมป้อนเข้า Compiler ตัวอื่น (เช่น TensorRT) ตัวไฟล์ไม่ผูกติดกับ Hardware แต่ประสิทธิภาพยังไม่ได้ถูก Optimize สูงสุดเพื่อชิปเฉพาะทาง


###  **.engine / .trt (TensorRT Engine)**
* **What it is:** ตัวท็อปสุดของการทำ Edge Optimization โมเดลที่ผ่านการ Compile ด้วย NVIDIA TensorRT เรียบร้อยแล้ว โดยตัว Graph จะถูกปรับแต่ง (Layer Fusion, Kernel Tuning) ให้เข้ากับโครงสร้างของ GPU รุ่นนั้นๆ โดยเฉพาะ พร้อมทำ Quantization (เช่น FP16/INT8)
* บังคับใช้สำหรับ DeepStream และ Jetson** เพราะให้ Throughput สูงสุดและ Latency ต่ำที่สุด *ข้อควรระวัง: ไฟล์ `.engine` ที่รันบน Jetson Nano จะไม่สามารถย้ายไปรันบน Xavier หรือ RTX PC ได้ ต้องทำการ Compile ใหม่บน Target GPU เสมอ*



## Connections
* **Parent:** [[ ]]
* **Similar:** [[ ]]