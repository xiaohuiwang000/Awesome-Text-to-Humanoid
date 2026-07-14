# Awesome Text-to-Humanoid

A curated list of research on language-conditioned whole-body motion generation and control for physical humanoid robots.

## Contents

- [Taxonomy](#taxonomy)
- [1. Explicit Motion Intermediate](#1-explicit-motion-intermediate)
- [2. Without Explicit Motion](#2-without-explicit-motion)
- [3. Vision-Language-Action (VLA)](#3-vision-language-action-vla)
- [Related Methods and Resources](#related-methods-and-resources)

## Taxonomy

We organize methods by the **intermediate representation** between language and low-level control:

| Category | Intermediate | Typical form | Strengths |
| --- | --- | --- | --- |
| **1. Explicit Motion Intermediate** | Explicit motion (e.g., joint trajectories / keyframes) | Generator + Tracker | Simple; strong portability; abundant motion data |
| **2. Without Explicit Motion** | None, or non-kinematic intermediates (latent / intent / tokens) | End-to-end, or latent-conditioned policies | Shrinks the generator–tracker gap; often more physically grounded actions |
| **3. Vision-Language-Action (VLA)** | Motion or latent, plus **visual** input | Hierarchical VLA / vision-conditioned generators | Scene-grounded instructions (objects, goals, navigation) |

VLA systems may internally look like Category 1 or 2; we always list them under **Category 3** because they take visual observations as input.

---

## 1. Explicit Motion Intermediate

Language conditions a motion generator that outputs **explicit** kinematic references (poses / trajectories), which a whole-body tracker then executes.

*Pros: simple pipeline, high portability across embodiments, and large available motion datasets.*

| Date | Work | Venue | Validation | Resources |
| --- | --- | --- | --- | --- |
| 2026-03 | **SafeFlow: Real-Time Text-Driven Humanoid Whole-Body Control via Physics-Guided Rectified Flow and Selective Safety Gating** | arXiv | Real Humanoid (Unitree G1) | [Project](https://hanbyelcho.info/safeflow/) · [Paper](https://arxiv.org/abs/2603.23983) |
| 2026-03 | **PhyGile: Physics-Prefix Guided Motion Generation for Agile General Humanoid Motion Tracking** | arXiv | Real Humanoid (Unitree G1) | [Paper](https://arxiv.org/abs/2603.19305) |
| 2026-03 | **PhysMoDPO: Physically-Plausible Humanoid Motion with Preference Optimization** | arXiv | Real Humanoid (Unitree G1) | [Project](https://mael-zys.github.io/PhysMoDPO/) · [Paper](https://arxiv.org/abs/2603.13228) · [Code](https://github.com/Mael-zys/PhysMoDPO) |
| 2026-03 | **RoboForge: Physically Optimized Text-guided Whole-Body Locomotion for Humanoids** | arXiv | Real Humanoid (Unitree G1) | [Paper](https://arxiv.org/abs/2603.17927) |
| 2026-02 | **TextOp: Real-time Interactive Text-Driven Humanoid Robot Motion Generation and Control** | arXiv | Real Humanoid (Unitree G1) | [Project](https://text-op.github.io/) · [Paper](https://arxiv.org/abs/2602.07439) · [Code](https://github.com/TeleHuman/TextOp) |
| 2026-01 | **FRoM-W1: Towards General Humanoid Whole-Body Control with Language Instructions** | arXiv | Real Humanoid (Unitree H1, G1) | [Project](https://openmoss.ai/FRoM-W1/) · [Paper](https://arxiv.org/abs/2601.12799) · [Code](https://github.com/OpenMOSS/FRoM-W1) · [Data](https://huggingface.co/datasets/OpenMOSS-Team/FRoM-W1-Datasets) · [Models](https://huggingface.co/OpenMOSS-Team/FRoM-W1) |
| 2025-12 | **UniAct: Unified Motion Generation and Action Streaming for Humanoid Robots** | arXiv | Real Humanoid (Unitree G1) | [Project](https://jnnan.github.io/uniact/) · [Paper](https://arxiv.org/abs/2512.24321) · [Code](https://github.com/jnnan/uniact-code) |
| 2025-06 | **RL from Physical Feedback: Aligning Large Motion Models with Humanoid Control (RLPF)** | arXiv | Real Humanoid (Unitree G1) | [Project](https://beingbeyond.github.io/RLPF/) · [Paper](https://arxiv.org/abs/2506.12769) |
| 2024-12 | **Learning from Massive Human Videos for Universal Humanoid Pose Control** | Humanoids 2025 Oral | Real Humanoid (Unitree H1-2) | [Project](https://psi-lab.ai/UH-1/) · [Paper](https://arxiv.org/abs/2412.14172) · [Code](https://github.com/sihengz02/UH-1) · [Data](https://huggingface.co/datasets/USC-PSI-Lab/Humanoid-X) · [Models](https://huggingface.co/USC-PSI-Lab/UH-1) |
| 2024-10 | **Harmon: Whole-Body Motion Generation of Humanoid Robots from Language Descriptions** | CoRL 2024 Oral | Real Humanoid (Fourier GR1) | [Project](https://ut-austin-rpl.github.io/Harmon/) · [Paper](https://arxiv.org/abs/2410.12773) |
| 2024-10 | **Robot Motion Diffusion Model: Motion Generation for Robotic Characters** | SIGGRAPH Asia 2024 | Real Humanoid (Disney robotic character) | [Project / Paper](https://la.disneyresearch.com/publication/robot-motion-diffusion-model-motion-generation-for-robotic-characters/) |

## 2. Without Explicit Motion

No explicit kinematic motion reference at deployment: either a single language→action policy, or a **latent / intent / token** intermediate that is not decoded into full poses before control.

*Pros: reduces the domain gap between generator and tracker; actions are often more physically grounded.*

| Date | Work | Venue | Validation | Resources |
| --- | --- | --- | --- | --- |
| 2026-05 | **Before the Body Moves: Learning Anticipatory Joint Intent for Language-Conditioned Humanoid Control (DAJI)** | arXiv | Real Humanoid (Unitree G1) | [Paper](https://arxiv.org/abs/2605.14417) |
| 2025-11 | **Commanding Humanoid by Free-form Language: A Large Language Action Model with Unified Motion Vocabulary (Humanoid-LLA)** | arXiv | Real Humanoid (Unitree G1, Booster T1) | [Project](https://humanoidlla.github.io/) · [Paper](https://arxiv.org/abs/2511.22963) |
| 2025-11 | **SENTINEL: A Fully End-to-End Language-Action Model for Humanoid Whole-Body Control** | CVPR 2026 | Real Humanoid (Unitree G1) | [CVF Paper](https://openaccess.thecvf.com/content/CVPR2026/html/Wang_End-to-End_Language-Action_Model_for_Humanoid_Whole_Body_Control_CVPR_2026_paper.html) · [arXiv](https://arxiv.org/abs/2511.19236) |
| 2025-11 | **ToggleMimic: A Two-Stage Policy for Text-Driven Humanoid Whole-Body Control** | Sensors 2025 | Real Humanoid (Unitree G1) | [Paper](https://doi.org/10.3390/s25237259) |
| 2025-10 | **From Language to Locomotion: Retargeting-free Humanoid Control via Motion Latent Guidance (RoboGhost)** | ICLR 2026 | Real Humanoid (Unitree G1) | [Paper](https://arxiv.org/abs/2510.14952) · [OpenReview](https://openreview.net/forum?id=k3Cyx3Uets) |
| 2025-04 | **LangWBC: Language-directed Humanoid Whole-Body Control via End-to-end Learning** | RSS 2025 | Real Humanoid (Unitree G1) | [Project](https://langwbc.github.io/) · [Paper](https://arxiv.org/abs/2504.21738) · [Code (partial)](https://github.com/YiyangShao2003/LangWBC) |

## 3. Vision-Language-Action (VLA)

Language-conditioned whole-body control that also consumes **visual** observations (egocentric video / scene perception). Internally these may use explicit motion or latents; listed here regardless.

| Date | Work | Venue | Validation | Resources |
| --- | --- | --- | --- | --- |
| 2025-06 | **LeVERB: Humanoid Whole-Body Control with Latent Vision-Language Instruction** | ICLR 2026 | Real Humanoid (Unitree G1) | [Project](https://ember-lab-berkeley.github.io/LeVERB-Website/) · [Paper](https://arxiv.org/abs/2506.13751) |
| 2025-02 | **Humanoid-VLA: Towards Universal Humanoid Control with Visual Integration** | arXiv | Real Humanoid (Unitree G1) | [Paper](https://arxiv.org/abs/2502.14795) |

## Related Methods and Resources

Related skill-learning methods, physics-based character animation / generators, and datasets that support text-to-humanoid research but are not language controllers for physical humanoid robots.

| Date | Work / Resource | Type | Links |
| --- | --- | --- | --- |
| 2026-05 | **MIND: Multi-Scale Intent Diffusion for Text-Driven Physics-Based Humanoid Control** | Physics-based character control (SMPL-like sim) | [Project](https://binlee26.github.io/MIND_page/) · [Paper](https://arxiv.org/abs/2605.26006) |
| 2026-05 | **SCRIPT: Scalable Diffusion Policy with Multi-stage Training for Language-driven Physics-based Humanoid Control** | Physics-based character control (SMPL-like sim) | [Project](https://zhanglele12138.github.io/SCRIPT/) · [Paper](https://arxiv.org/abs/2605.22894) |
| 2026-03 | **Kimodo: Scaling Controllable Human Motion Generation** | Kinematic motion diffusion model | [Project](https://research.nvidia.com/labs/sil/projects/kimodo/) · [Report](https://xbpeng.github.io/projects/Kimodo/Kimodo_2026.pdf) · [Code](https://github.com/nv-tlabs/kimodo) · [Models](https://huggingface.co/collections/nvidia/kimodo-v1) · [Demo](https://huggingface.co/spaces/nvidia/Kimodo) |
