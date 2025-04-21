# Lightweight Intelligent Detection System for Personal Protective Equipment in Laboratories of Higher Education Institutions
## Introduction
Laboratory safety in higher education institutions (HEIs) is an important issue in research and teaching, especially in high-risk environments such as chemical and biological. With the increasing demand for laboratory safety management, traditional manual checking methods face inefficiency and poor real-time performance. Therefore, introducing an automated intelligent detection system has become important to improve laboratory safety management. In this paper, a lightweight laboratory personal protective equipment detection system (LabPPE-DS) based on cross-stage partial darknet (CSPDarknet) is proposed for real-time detection of personal protective equipment (PPE) in laboratories. The system achieves high-precision PPE detection through cross-scale feature-focused fusion. It adopts pruning and knowledge distillation technology to significantly improve the system's computational efficiency and resource adaptation capability. Through experimental validation, LabPPE-DS outperforms existing mainstream detection models in several detection metrics, effectively balancing precision and inference speed. In addition, the system is successfully deployed on computing devices without graphics processing unit (GPU) support, verifying its effectiveness in resource-constrained environments. In addition to enhancing laboratory security management, the system has a wide range of potential applications.
## Document
### Experimental Environment
✅ Python 3.10.14  
✅ PyTorch 2.1.0  
✅ NVIDIA GeForce RTX 4090
✅ Intel(R) Xeon(R) Platinum 8457C
✅ Ubuntu 22.04

  Training parameter setting
|Parameter Name  |Parameter Value |
| -------------- | ------------ |
| Epoch          | 300          |
| Batch Size     | 32           |
| lr             | 0.01         |
| Optimizer      | SGD          |
| Image Size     | 640 × 640    |
| Momentum       | 0.937        |
| Weight_decay   | 0.0005       |

```bash
pip install pypi
pip install timm==1.0.7 thop efficientnet_pytorch==0.7.1 einops grad-cam==1.4.8 dill==0.3.8 albumentations==1.4.11 pytorch_wavelets==1.3.0 tidecv PyWavelets opencv-python -i https://pypi.tuna.tsinghua.edu.cn/simple
pip install -e .
```

```bash
from ultralytics import YOLO

# Load a model
model = YOLO("LabPPE-DS.yaml") # pase model

# Train the model
model.train(
                data='data.yaml', # pase your dataset
                cache=False,
                imgsz=640,
                epochs=300,
                batch=32,
                close_mosaic=0,
                workers=4, 
                optimizer='SGD', 
                project='runs/train',
                name='exp',
)
```
## LabPPE-DS Dataset
```bash
@misc{safety-lab_dataset,
  title = { Safety Lab Dataset },
  type = { Open Source Dataset },
  author = { UAEU },
  howpublished = { \url{ https://universe.roboflow.com/uaeu-oc33o/safety-lab } },
  url = { https://universe.roboflow.com/uaeu-oc33o/safety-lab },
  journal = { Roboflow Universe },
  publisher = { Roboflow },
  year = { 2022 },
  month = { sep },
  note = { visited on 2025-04-18 },
}
```
