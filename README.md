# IIP-Net--Robust-Impact-Representation-Learning-from-Surface-Damage

IIP-Net is a **non-contact indirect measurement system** for quantitative reconstruction of stabbing impact parameters directly from post-incident surface damage images of stab-resistant UHMWPE composite materials. It establishes a complete metrological chain from optical surface morphology to three key physical quantities:

<div style="text-align: center;">
  <img src="/figs/image1.png" alt="IIP-Net Framework" style="width: 100%; max-width: 800px;">
</div>

*Fig. 1. Overview of the proposed IIP-Net two-stage framework.*

---

### Experimental System

#### 1. Laboratory: Dynamic Stabbing Test (SPFCT-2000)

The standardized drop-weight stabbing system complies with **NIJ Standard 0115.00**.

| Component             | Specification |
|-----------------------|-------------------------------|
| Instrument            | SPFCT-2000 |
| Impactor + knife mass | 2 kg total |
| Drop height range     | 45–185 cm |
| Repeats per height    | 6 |
| Force sensor          | Between knife base and impactor |
| Velocity measurement  | Photoelectric gate at knife–sample contact point |
| Penetration sensing   | Aluminum film circuit, 10 µm, sampling 2 MHz, range 10 V |
| Sample material       | UHMWPE, 50 layers, 200 × 200 mm |


#### 2. Real-World: Human Stabbing Test

| Component | Specification |
|---|---|
| Backing | Configured per NIJ Standard 0115.00 |
| Knife fixture | CNC-machined, self-customed |
| High-speed camera | 700 fps |
| Ring light | Illumination + knife entry height reference|
| Participants | 10 volunteers |


#### 3. Image Acquisition System

| Component | Specification |
|---|---|
| Camera | Industrial camera, 4022 × 3036 resolution |
| Lens | 8 mm focal length, 12 MP |
| Light source | 300 × 300 mm industrial panel light |
| Image resolution (model input) | 512 × 512 px |

---

### Method: IIP-Net Two-Stage Architecture

#### Stage 1 — TraceNet

<div style="text-align: center;">
  <img src="/figs/image2.png" alt="TraceNet Architecture" style="width: 100%; max-width: 800px;">
</div>

*Fig. 2. TraceNet architecture.*

#### Stage 2 — S-CNN

A shallow CNN directly regresses the three impact parameters from the segmented damage image.

---

### IIP-Net Performance

| Method | Overall MAE (%) | Params (M) | Memory (GB) | Perf. Drop (%) | Annotation |
|---|---|---|---|---|---|
| ResNet-50 | 6.83 | 23.5 | 2.1 | 27 | Yes |
| VGG-16 | 8.53 | 15.2 | 1.8 | 30 | Yes |
| DenseNet-121 | 6.90 | 8.0 | 1.5 | 25 | Yes |
| ResNet-50 + Attention | 6.23 | 25.8 | 2.3 | 22 | Yes |
| Vision Transformer | 7.80 | 86.4 | 4.2 | 28 | Yes |
| Multi-task CNN | 8.23 | 12.3 | 1.2 | 24 | Yes |
| FPN | 6.90 | 18.7 | 1.9 | 21 | Yes |
| **IIP-Net** | **4.03** | **3.2** | **0.8** | **8** | **No** |

---

### Perpetrator Identification Performance

Key impact parameters predicted by IIP-Net ($E_k$, $F$, $N$) are fed into nine ML classifiers to identify which participant performed each stab. Best result with **KNN**: accuracy 92.50%, precision 94.47%, recall 92.50%, F1 92.27%.

<div style="text-align: center;">
  <img src="/figs/image7.png" alt="TraceNet Architecture" style="width: 100%; max-width: 800px;">
</div>

*Fig. 3. Performance comparison of nine ML classifiers.*

---

### Citation

```bibtex
@article{liu2026iipnet,
  title   = {IIP-Net: Robust Impact Representation Learning from Surface Damage for Stab-Resistant Material},
  author  = {Liu, Mengzhen, and others},
  year    = {2026},
}
```

