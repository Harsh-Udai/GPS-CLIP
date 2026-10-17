# GPS-CLIP: Beyond Hard Negatives — Grounded Positive Supervision for Compositional CLIP

**NeurIPS 2026**

**Harsh Udai**<sup>1</sup>, **Konda Reddy Mopuri**<sup>1</sup>, **Vineeth N. Balasubramanian**<sup>2,3</sup>

<sup>1</sup>Department of Artificial Intelligence, IIT Hyderabad &nbsp;·&nbsp;
<sup>2</sup>Department of Computer Science and Engineering, IIT Hyderabad &nbsp;·&nbsp;
<sup>3</sup>Microsoft Research India

[[Paper]](TODO-link-to-paper) &nbsp; [[arXiv]](TODO-arxiv-link)

---

> 🚧 **Code coming soon.** We are cleaning up the training and evaluation code and will release it here before the conference.

## Overview

CLIP-style vision-language models transfer broadly but remain brittle for compositional reasoning, often collapsing object–attribute binding and inter-object relations. Many existing fixes rely on caption-edited hard negatives, which can bias learning toward specific perturbation templates and trade off against general alignment.

**GPS-CLIP** improves compositionality by adding multi-granular **positive** constraints to standard contrastive learning:

- **IoU-weighted multi-positive region–span alignment** — overlapping same-image regions are treated as weighted positives, non-overlapping same-image pairs are masked, and cross-image pairs remain negatives.
- **Relation-triplet alignment** — a relation-aware contrastive loss over ⟨subject, relation, object⟩ triplets that provides an ordered relational inductive bias.

Structured annotations are used **only during fine-tuning**. At inference, GPS-CLIP is a standard CLIP dual encoder that needs only images and text, with no extra latency, parameters, or FLOPs.

## Highlights

- State-of-the-art average accuracy on COLA, What'sUp, and Winoground, and strong results on SugarCrepe / SugarCrepe++
- Best MMVP-VLM results for fine-grained visual understanding
- Improves zero-shot ImageNetV2 classification and COCO / Flickr30k retrieval
- Robust to moderately noisy scene-graph supervision, scales to ViT-L/14, and works with a SigLIP-style sigmoid loss

## Planned release

- [ ] Training code (OpenCLIP + LoRA)
- [ ] Region–span and relation-triplet loss implementations
- [ ] Triplet extraction pipeline (Qwen2.5-7B-Instruct prompt)
- [ ] Evaluation scripts (COLA, What'sUp, Winoground, SugarCrepe/++, MMVP-VLM, retrieval, ImageNetV2)
- [ ] Pretrained checkpoints

## Citation

If you find this work useful, please cite:

```bibtex
@inproceedings{udai2026gpsclip,
  title     = {Beyond Hard Negatives: Grounded Positive Supervision for Compositional {CLIP}},
  author    = {Udai, Harsh and Mopuri, Konda Reddy and Balasubramanian, Vineeth N.},
  booktitle = {Advances in Neural Information Processing Systems (NeurIPS)},
  year      = {2026}
}
```

## License

This project is released under the MIT License (see [LICENSE](LICENSE)). Datasets, pretrained models, and benchmarks used in this work are governed by their original licenses.

## Acknowledgments

This codebase builds on [OpenCLIP](https://github.com/mlfoundations/open_clip) and uses Graph-Based Captions (GBC) supervision.
