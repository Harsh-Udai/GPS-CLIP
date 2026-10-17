<div align="center">

# 🧭 GPS-CLIP

### Beyond Hard Negatives: Grounded Positive Supervision for Compositional CLIP

**Harsh Udai**<sup>1</sup> &nbsp;·&nbsp; **Konda Reddy Mopuri**<sup>1</sup> &nbsp;·&nbsp; **Vineeth N. Balasubramanian**<sup>2,3</sup>

<sup>1</sup>Dept. of Artificial Intelligence, IIT Hyderabad &nbsp;&nbsp;
<sup>2</sup>Dept. of CSE, IIT Hyderabad &nbsp;&nbsp;
<sup>3</sup>Microsoft Research India

<br>

[![NeurIPS 2026](https://img.shields.io/badge/NeurIPS-2026-6f42c1?style=for-the-badge)](TODO-link-to-paper)
[![Paper](https://img.shields.io/badge/Paper-PDF-b31b1b?style=for-the-badge&logo=adobeacrobatreader&logoColor=white)](TODO-link-to-paper)
[![arXiv](https://img.shields.io/badge/arXiv-coming%20soon-lightgrey?style=for-the-badge&logo=arxiv&logoColor=white)](TODO-arxiv-link)
[![License: MIT](https://img.shields.io/badge/License-MIT-2ea44f?style=for-the-badge)](LICENSE)
[![Code](https://img.shields.io/badge/Code-coming%20soon-orange?style=for-the-badge&logo=github)](#-release-plan)

</div>

<!-- Optional: add your teaser figure (e.g., Fig. 1 or Fig. 2 from the paper) -->
<!-- <p align="center"><img src="assets/teaser.png" width="90%"></p> -->

---

> [!NOTE]
> 🚧 **Code is coming soon.** We are cleaning up the training and evaluation pipeline and will release it here before the conference. Star ⭐ or watch 👀 the repo to get notified.

## ✨ TL;DR

CLIP models are good at *what* is in an image but often miss *how things relate*: who is chasing whom, which object is red, what is on top of what. Instead of teaching CLIP to reject synthetic "hard negative" captions, **GPS-CLIP pulls each image toward its own grounded structure**: its regions, their descriptions, and the relations between them.

The result is better compositional reasoning, **better** zero-shot recognition and retrieval, and **zero extra cost at inference**.

## 🔍 Method at a Glance

GPS-CLIP adds two structured **positive** objectives on top of the standard CLIP contrastive loss:

- 🟩 **IoU-weighted multi-positive region loss** aligns image regions with their text spans. Overlapping same-image regions are treated as *weighted positives*, non-overlapping same-image pairs are *masked*, and cross-image pairs stay *negatives*.
- 🔗 **Relation-triplet loss** aligns each image with its ⟨subject, relation, object⟩ triplets, giving the model an *ordered* relational inductive bias (e.g., "dog chasing frisbee" ≠ "frisbee chasing dog").
- 🌐 **Global CLIP loss** keeps the standard image–caption contrastive alignment, preserving general zero-shot ability.

**Why it's practical:**

- ✅ Same dual-encoder architecture
- ✅ Scene graphs used only during training
- ✅ No extra latency, parameters, or FLOPs at inference
- ✅ Works with InfoNCE *and* SigLIP-style sigmoid loss

## 🗺️ Release Plan

- [ ] Training code (OpenCLIP + LoRA)
- [ ] Region–span and relation-triplet loss implementations
- [ ] Triplet extraction pipeline (Qwen2.5-7B-Instruct)
- [ ] Evaluation scripts: COLA, What'sUp, Winoground, SugarCrepe/++, MMVP-VLM, retrieval, ImageNetV2
- [ ] Pretrained checkpoints (ViT-B/32, ViT-L/14)

## 📝 Citation

If you find this work useful, please consider citing:

```bibtex
@inproceedings{udai2026gpsclip,
  title     = {Beyond Hard Negatives: Grounded Positive Supervision for Compositional {CLIP}},
  author    = {Udai, Harsh and Mopuri, Konda Reddy and Balasubramanian, Vineeth N.},
  booktitle = {Advances in Neural Information Processing Systems (NeurIPS)},
  year      = {2026}
}
```

## 🙏 Acknowledgments

This codebase builds on [OpenCLIP](https://github.com/mlfoundations/open_clip) and uses [Graph-Based Captioning (GBC)](https://arxiv.org/abs/2407.06723) supervision. We thank the authors for making their work publicly available.

## 📄 License

Released under the [MIT License](LICENSE). Datasets, pretrained models, and benchmarks used in this work remain governed by their original licenses.
