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


### Applying AI

- Object detection + recognition
- Plate recognition
- Congestion monitoring

### Methodology

- Two steps : Region Proposal Network + Feature Extraction/Classification (R-CNN)
- One step : predict bounding box, classes and confidence score in one step (YOLO)

### Efficiency Score

- Eval metric / GFLOPS



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


## Connections
* **Parent:** [[ ]]
* **Similar:** [[ ]]