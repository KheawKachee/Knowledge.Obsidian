---
type: knowledge-note
created: 2026-05-18 13:38
tags:
aliases: []
references:
---


### Summary

> [!abstract] 
> The approach of applying AI in edge device usually maximize the performance due to physical constrains inherited in edge devices such as processing power or limited inputs.


### Legacy Bottleneck

- Sensor-based device
- Low bandwidth
- Installation cost
- Limited object features (often detect presence, not attributes)

### Applying AI

- Object detection + recognition
- Plate recognition
- Congestion monitoring

### Methodology

- Two steps : Region Proposal Network + Feature Extraction/Classification (R-CNN)
- One step : predict bounding box, classes and confidence score in one step (YOLO)

### Edge vs Cloud

- Edge : ultra low latency / limit computation and data size
- Cloud : higher latency / strong computation capability

### Model Comparison

| Project Constraint   | [[YOLO]] (v10/v12)                            | [[RT-DETR]]                              |
| -------------------- | --------------------------------------------- | ---------------------------------------- |
| **Best Use Case**    | Highways, Toll Booths, Parking Lots           | Complex Urban Intersections, Roundabouts |
| **Primary Strength** | Raw FPS, High localization for License Plates | Severe occlusion, contextual reasoning   |
| **Primary Weakness** | Struggles when targets are heavily blocked    | High memory bandwidth requirement        |
| **Hardware Target**  | Jetson Nano / Orin NX (15W - 25W)             | Jetson AGX Orin / Thor (40W - 60W+)      |
| **Latency Profile**  | Sub-10ms (Ultra-Low)                          | 15ms - 25ms (Moderate)                   |

---
### Efficiency Score

- Eval metric / GFLOPS


### [[Structured Pruning#Summary]] 


### [[Quantization#Summary]]


### [[Knowledge Distillation#Summary]]


### [[Multi-Scale Heads#Summary]]


### [[Deployment & Scale#Summary]]


Batching in multi nput real tiem inference

### [[Transfer Learning#Summary]]

### Next Hackathon maybe

- Car indentification using multi camera
- we detect bbox to get
	- "white Toyota sedan plate number 'xxx' "
- then we use those to query id via re-id with several method
	- bayesian 
	- graph
- finally we get most possible id of that entity

then paper to research is
- lightweight YOLO for Jetson
- License plate OCR
- Re-ID 


### Practical Pipeline

1. find best model
2. train best model as teacher
3. KD in student model MobileNet, ShuffleNet, or GhostNet as yolo backbone
4. Pruning (Gamma, GradCam / ExplainableAI)
5. Quantization + TensorRT with Nsight 
6. Dynamic Batching for multi-camera


### Open question 

- is there trade-offs between one-step and two-steps approach
- For Jetson nano 2GB with 472 GFLOPS

|       Assumed efficiency | Safe model budget for 15 FPS |
| -----------------------: | ---------------------------: |
|         100% theoretical |                  31.5 GFLOPs |
|                 50% good |                  15.7 GFLOPs |
| 40% Practical (TensorRT) |                  12.6 GFLOPs |
|                30% safer |                   9.4 GFLOPs |
|         20% bad pipeline |                   6.3 GFLOPs |

- MCMOT? (probably no)

## Connections
* **Parent:** [[ ]]
* **Similar:** [[ ]]