# ⚙️ Bearing RUL Prediction via Contrastive Self-Supervised Learning

> Implementation of:  
> **“Bearings RUL prediction based on contrastive self-supervised learning”**  
> *Liu et al., IFAC-PapersOnLine, 2023*  
> https://doi.org/10.1016/j.ifacol.2023.10.661

---

## 📌 What this repository is

This repository is **a full reproducible implementation** of the 2023 paper that proposes a
contrastive self-supervised pretext task for learning robust machine degradation
representations — and then uses those representations to **predict Remaining Useful Life (RUL)**
of rolling element bearings under rotating machinery.

### In simple words:

| Stage | What happens |
|-------|--------------|
| 1. raw vibration signal → windows | convert raw run-to-failure signal into short temporal segments |
| 2. contrastive SSL pretraining | the model learns “what stays invariant” in degradation |
| 3. freeze backbone → RUL regressor | a simple MLP is trained on top to predict Remaining Useful Life |
| 4. deploy | RUL curves track degradation progression on unseen bearings |

---

## 🔥 Why this approach matters

Traditional supervised RUL models need labelled “RUL at every timestamp” — which is mainly hypothetical and highly costly.

**This paper avoids that** by using unlabeled run-to-failure segments to learn structure first (contrastive).

This yields:

- better generalisation across bearings
- reduces label requirement
- captures degradation trend structure automatically
- works well in few-shot labeled regimes

---

## 🧠 Paper contribution (summarised)

This repo implements **the key mechanism that the paper proposes:**

> use self-supervised contrastive learning to first learn health state embeddings,  
> then attach a lightweight regressor for RUL.

Key points we implement:

- positive/negative pair generation from temporal windows
- contrastive InfoNCE objective
- encoder = 1D CNN backbone
- SSL pre-train → freeze → regress RUL

---
@article{liu2023bearings,
  title={Bearings RUL prediction based on contrastive self-supervised learning},
  author={Liu, Zihan and others},
  journal={IFAC-PapersOnLine},
  year={2023},
  doi={10.1016/j.ifacol.2023.10.661}
}
