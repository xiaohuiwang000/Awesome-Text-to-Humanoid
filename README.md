# Awesome Text-to-Humanoid [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

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

| Date | Paper | Venue | Real Robot | Resources |
| --- | --- | --- | --- | --- |
| 2026-06 | **[TEXEDO: Test Time Scaling for Controller-aware Language-conditioned Humanoid Motion Generation](https://arxiv.org/abs/2606.22998)** | arXiv | ✅ | 🏠 [Project](https://jianuocao.github.io/TEXEDO/) · 💻 [Code](https://github.com/JianuoCao/TEXEDO) |
| 2026-03 | **[SafeFlow: Real-Time Text-Driven Humanoid Whole-Body Control via Physics-Guided Rectified Flow and Selective Safety Gating](https://arxiv.org/abs/2603.23983)** | arXiv | ✅ | 🏠 [Project](https://hanbyelcho.info/safeflow/) |
| 2026-03 | **[ECHO: Edge-Cloud Humanoid Orchestration for Language-to-Motion Control](https://arxiv.org/abs/2603.16188)** | arXiv | ✅ |  |
| 2026-03 | **[PhyGile: Physics-Prefix Guided Motion Generation for Agile General Humanoid Motion Tracking](https://arxiv.org/abs/2603.19305)** | IROS 2026 | ✅ | 🏠 [Project](https://baojch.github.io/phygile-page/) · 💻 [Code](https://github.com/Baojch/phygile_tracking) |
| 2026-03 | **[PhysMoDPO: Physically-Plausible Humanoid Motion with Preference Optimization](https://arxiv.org/abs/2603.13228)** | arXiv | ✅ | 🏠 [Project](https://mael-zys.github.io/PhysMoDPO/) · 💻 [Code](https://github.com/Mael-zys/PhysMoDPO) |
| 2026-03 | **[RoboForge: Physically Optimized Text-guided Whole-Body Locomotion for Humanoids](https://arxiv.org/abs/2603.17927)** | arXiv | ✅ | 🏠 [Project](https://xichen-001.github.io/RoboForge/) |
| 2026-02 | **[TextOp: Real-time Interactive Text-Driven Humanoid Robot Motion Generation and Control](https://arxiv.org/abs/2602.07439)** | arXiv | ✅ | 🏠 [Project](https://text-op.github.io/) · 💻 [Code](https://github.com/TeleHuman/TextOp) |
| 2026-01 | **[FRoM-W1: Towards General Humanoid Whole-Body Control with Language Instructions](https://arxiv.org/abs/2601.12799)** | arXiv | ✅ | 🏠 [Project](https://openmoss.ai/FRoM-W1/) · 💻 [Code](https://github.com/OpenMOSS/FRoM-W1) |
| 2025-12 | **[UniAct: Unified Motion Generation and Action Streaming for Humanoid Robots](https://arxiv.org/abs/2512.24321)** | arXiv | ✅ | 🏠 [Project](https://jnnan.github.io/uniact/) · 💻 [Code](https://github.com/jnnan/uniact-code) · 📊 [Dataset](https://jnnan.github.io/uniact/#dataset-section) |
| 2025-06 | **[RL from Physical Feedback: Aligning Large Motion Models with Humanoid Control (RLPF)](https://arxiv.org/abs/2506.12769)** | arXiv | ✅ | 🏠 [Project](https://beingbeyond.github.io/RLPF/) |
| 2024-12 | **[Learning from Massive Human Videos for Universal Humanoid Pose Control](https://ieeexplore.ieee.org/document/11203143/)** | Humanoids 2025 Oral | ✅ | 🏠 [Project](https://psi-lab.ai/UH-1/) · 💻 [Code](https://github.com/sihengz02/UH-1) · 📊 [Dataset](https://huggingface.co/collections/USC-PSI-Lab/universal-humanoid-10) |
| 2024-10 | **[Harmon: Whole-Body Motion Generation of Humanoid Robots from Language Descriptions](https://proceedings.mlr.press/v270/jiang25b.html)** | CoRL 2024 | ✅ | 🏠 [Project](https://ut-austin-rpl.github.io/Harmon/) |
| 2024-10 | **[Robot Motion Diffusion Model: Motion Generation for Robotic Characters](https://la.disneyresearch.com/publication/robot-motion-diffusion-model-motion-generation-for-robotic-characters/)** | SIGGRAPH Asia 2024 | ✅ | 🏠 [Project](https://la.disneyresearch.com/publication/robot-motion-diffusion-model-motion-generation-for-robotic-characters/) |

## 2. Without Explicit Motion

No explicit kinematic motion reference at deployment: either a single language→action policy, or a **latent / intent / token** intermediate that is not decoded into full poses before control.

*Pros: reduces the domain gap between generator and tracker; actions are often more physically grounded.*

| Date | Paper | Venue | Real Robot | Resources |
| --- | --- | --- | --- | --- |
| 2026-05 | **[Before the Body Moves: Learning Anticipatory Joint Intent for Language-Conditioned Humanoid Control](https://arxiv.org/abs/2605.14417)** | arXiv | ✅ | 🏠 [Project](https://hxxxz0.github.io/DAJI_PAGE/) |
| 2025-11 | **[Commanding Humanoid by Free-form Language: A Large Language Action Model with Unified Motion Vocabulary](https://arxiv.org/abs/2511.22963)** | arXiv | ✅ | 🏠 [Project](https://humanoidlla.github.io/) |
| 2025-11 | **[SENTINEL: A Fully End-to-End Language-Action Model for Humanoid Whole-Body Control](https://openaccess.thecvf.com/content/CVPR2026/papers/Wang_End-to-End_Language-Action_Model_for_Humanoid_Whole_Body_Control_CVPR_2026_paper.pdf)** | CVPR 2026 | ✅ |  |
| 2025-11 | **[ToggleMimic: A Two-Stage Policy for Text-Driven Humanoid Whole-Body Control](https://doi.org/10.3390/s25237259)** | Sensors 2025 | ✅ |  |
| 2025-10 | **[From Language to Locomotion: Retargeting-free Humanoid Control via Motion Latent Guidance](https://arxiv.org/abs/2510.14952)** | ICLR 2026 | ✅ | 🏠 [Project](https://gentlefress.github.io/roboghost-proj/) · 💻 [Code](https://github.com/gentlefress/RoboGhost) |
| 2025-04 | **[LangWBC: Language-directed Humanoid Whole-Body Control via End-to-end Learning](https://www.roboticsproceedings.org/rss21/p065.html)** | RSS 2025 | ✅ | 🏠 [Project](https://langwbc.github.io/) · 💻 [Code](https://github.com/YiyangShao2003/LangWBC) |

## 3. Vision-Language-Action (VLA)

Language-conditioned whole-body control that also consumes **visual** observations (egocentric video / scene perception). Internally these may use explicit motion or latents; listed here regardless.

| Date | Paper | Venue | Real Robot | Resources |
| --- | --- | --- | --- | --- |
| 2026-06 | **[WOLF-VLA: Whole-Body Humanoid Optimal Locomotion Framework for Vision-Language-Action Learning](https://arxiv.org/abs/2606.25591)** | arXiv |  |  |
| 2025-12 | **[WholeBodyVLA: Towards Unified Latent VLA for Whole-Body Loco-Manipulation Control](https://arxiv.org/abs/2512.11047)** | ICLR 2026 | ✅ | 🏠 [Project](https://opendrivelab.com/WholeBodyVLA/) |
| 2025-06 | **[LeVERB: Humanoid Whole-Body Control with Latent Vision-Language Instruction](https://arxiv.org/abs/2506.13751)** | arXiv | ✅ |  |
| 2025-02 | **[Humanoid-VLA: Towards Universal Humanoid Control with Visual Integration](https://arxiv.org/abs/2502.14795)** | arXiv | ✅ |  |

## Related Methods and Resources

For broader background, see also these community-curated lists: 
- [awesome-text-to-motion](https://github.com/Zilize/awesome-text-to-motion)
- [awesome-humanoid-robot-learning](https://github.com/YanjieZe/awesome-humanoid-robot-learning).

Related skill-learning methods, physics-based character animation / generators, and datasets that support text-to-humanoid research but are not language controllers for physical humanoid robots.

| Date | Paper / Resource | Type | Resources |
| --- | --- | --- | --- |
| 2026-05 | **[MIND: Multi-Scale Intent Diffusion for Text-Driven Physics-Based Humanoid Control](https://arxiv.org/abs/2605.26006)** | Physics-based character control (SMPL-like sim) | 🏠 [Project](https://binlee26.github.io/MIND_page/) |
| 2026-05 | **[SCRIPT: Scalable Diffusion Policy with Multi-stage Training for Language-driven Physics-based Humanoid Control](https://arxiv.org/abs/2605.22894)** | Physics-based character control (SMPL-like sim) | 🏠 [Project](https://zhanglele12138.github.io/SCRIPT/) |
| 2026-03 | **[Kimodo: Scaling Controllable Human Motion Generation](https://xbpeng.github.io/projects/Kimodo/Kimodo_2026.pdf)** | Kinematic motion diffusion model | 🏠 [Project](https://research.nvidia.com/labs/sil/projects/kimodo/) · 💻 [Code](https://github.com/nv-tlabs/kimodo) |
