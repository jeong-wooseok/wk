---
Date Added: 2025-09-15
tags:
  - vision-language
  - multimodal
status:
source: https://huggingface.co/Qwen/Qwen2.5-VL-72B-Instruct?library=transformers
created: 2025-09-15
channel name: 게시판
Length: 12500자
Month: 09
Quarter: Q3-2025
Rating:
---
##### AI Summary
**Qwen25VL**
- Qwen2.5-VL is a 72B instruction-tuned vision-language model focused on improved visual understanding, agentic capabilities, long-video comprehension, localization, and structured outputs, with Transformers support and usage examples.
- Key improvements include dynamic resolution/frame-rate video training, streamlined vision encoder, structured JSON outputs, and tools for image/video preprocessing and long-context handling.
- The repo provides evaluation benchmarks, quickstart examples for Transformers and ModelScope, installation notes, and citations (including arXiv papers).

---
##### Contents
Qwen2.5-VL-72B-Instruct

Introduction

In the past five months since Qwen2-VL’s release, numerous developers have built new models on the Qwen2-VL vision-language models, providing us with valuable feedback. During this period, we focused on building more useful vision-language models. Today, we are excited to introduce the latest addition to the Qwen family: Qwen2.5-VL.

Key Enhancements:

- Understand things visually: Qwen2.5-VL is not only proficient in recognizing common objects such as flowers, birds, fish, and insects, but it is highly capable of analyzing texts, charts, icons, graphics, and layouts within images.

- Being agentic: Qwen2.5-VL directly plays as a visual agent that can reason and dynamically direct tools, which is capable of computer use and phone use.

- Understanding long videos and capturing events: Qwen2.5-VL can comprehend videos of over 1 hour, and this time it has a new ability of cpaturing event by pinpointing the relevant video segments.

- Capable of visual localization in different formats: Qwen2.5-VL can accurately localize objects in an image by generating bounding boxes or points, and it can provide stable JSON outputs for coordinates and attributes.

- Generating structured outputs: for data like scans of invoices, forms, tables, etc. Qwen2.5-VL supports structured outputs of their contents, benefiting usages in finance, commerce, etc.

Model Architecture Updates:

Dynamic Resolution and Frame Rate Training for Video Understanding:

We extend dynamic resolution to the temporal dimension by adopting dynamic FPS sampling, enabling the model to comprehend videos at various sampling rates. Accordingly, we update mRoPE in the time dimension with IDs and absolute time alignment, enabling the model to learn temporal sequence and speed, and ultimately acquire the ability to pinpoint specific moments.

[image: qwen2.5vl_arc.jpeg]

Streamlined and Efficient Vision Encoder

We enhance both training and inference speeds by strategically implementing window attention into the ViT. The ViT architecture is further optimized with SwiGLU and RMSNorm, aligning it with the structure of the Qwen2.5 LLM.

We have three models with 3, 7 and 72 billion parameters. This repo contains the instruction-tuned 72B Qwen2.5-VL model. For more information, visit our Blog and GitHub.

Evaluation

Image benchmark

Benchmarks | GPT4o | Claude3.5 Sonnet | Gemini-2-flash | InternVL2.5-78B | Qwen2-VL-72B | Qwen2.5-VL-72B
MMMU_val | 70.3 | 70.4 | 70.7 | 70.1 | 64.5 | 70.2
MMMU_Pro | 54.5 | 54.7 | 57.0 | 48.6 | 46.2 | 51.1
MathVista_MINI | 63.8 | 65.4 | 73.1 | 76.6 | 70.5 | 74.8
MathVision_FULL | 30.4 | 38.3 | 41.3 | 32.2 | 25.9 | 38.1
Hallusion Bench | 55.0 | 55.16 |  | 57.4 | 58.1 | 55.16
MMBench_DEV_EN_V11 | 82.1 | 83.4 | 83.0 | 88.5 | 86.6 | 88
AI2D_TEST | 84.6 | 81.2 |  | 89.1 | 88.1 | 88.4
ChartQA_TEST | 86.7 | 90.8 | 85.2 | 88.3 | 88.3 | 89.5
DocVQA_VAL | 91.1 | 95.2 | 92.1 | 96.5 | 96.1 | 96.4
MMStar | 64.7 | 65.1 | 69.4 | 69.5 | 68.3 | 70.8
MMVet_turbo | 69.1 | 70.1 |  | 72.3 | 74.0 | 76.19
OCRBench | 736 | 788 |  | 854 | 877 | 885
OCRBench-V2(en/zh) | 46.5/32.3 | 45.2/39.6 | 51.9/43.1 | 45/46.2 | 47.8/46.1 | 61.5/63.7
CC-OCR | 66.6 | 62.7 | 73.0 | 64.7 | 68.7 | 79.8

Video benchmark

Benchmarks | GPT4o | Gemini-1.5-Pro | InternVL2.5-78B | Qwen2VL-72B | Qwen2.5VL-72B
VideoMME w/o sub. | 71.9 | 75.0 | 72.1 | 71.2 | 73.3
VideoMME w sub. | 77.2 | 81.3 | 74.0 | 77.8 | 79.1
MVBench | 64.6 | 60.5 | 76.4 | 73.6 | 70.4
MMBench-Video | 1.63 | 1.30 | 1.97 | 1.70 | 2.02
LVBench | 30.8 | 33.1 | - | 41.3 | 47.3
EgoSchema | 72.2 | 71.2 | - | 77.9 | 76.2
PerceptionTest_test | - | - | - | 68.0 | 73.2
MLVU_M-Avg_dev | 64.6 | - | 75.7 |  | 74.6
TempCompass_overall | 73.8 | - | - |  | 74.8

Agent benchmark

Benchmarks | GPT4o | Gemini 2.0 | Claude | Aguvis-72B | Qwen2VL-72B | Qwen2.5VL-72B
ScreenSpot | 18.1 | 84.0 | 83.0 |  |  | 87.1
ScreenSpot Pro |  |  | 17.1 |  | 1.6 | 43.6
AITZ_EM | 35.3 |  |  |  | 72.8 | 83.2
Android Control High_EM |  |  |  | 66.4 | 59.1 | 67.36
Android Control Low_EM |  |  |  | 84.4 | 59.2 | 93.7
AndroidWorld_SR | 34.5% (SoM) |  | 27.9% | 26.1% |  | 35%
MobileMiniWob++_SR |  |  |  | 66% |  | 68%
OSWorld |  |  | 14.90 | 10.26 |  | 8.83

Requirements

The code of Qwen2.5-VL has been in the latest Hugging face transformers and we advise you to build from source with command:

pip install git+https://github.com/huggingface/transformers accelerate

or you might encounter the following error:

KeyError: 'qwen2_5_vl'

Quickstart

Below, we provide simple examples to show how to use Qwen2.5-VL with 🤖 ModelScope and 🤗 Transformers.

The code of Qwen2.5-VL has been in the latest Hugging face transformers and we advise you to build from source with command:

pip install git+https://github.com/huggingface/transformers accelerate

or you might encounter the following error:

KeyError: 'qwen2_5_vl'

We offer a toolkit to help you handle various types of visual input more conveniently, as if you were using an API. This includes base64, URLs, and interleaved images and videos. You can install it using the following command:

# It's highly recommanded to use `[decord]` feature for faster video loading.
pip install qwen-vl-utils[decord]==0.0.8

If you are not using Linux, you might not be able to install decord from PyPI. In that case, you can use pip install qwen-vl-utils which will fall back to using torchvision for video processing. However, you can still install decord from source to get decord used when loading video.

Using 🤗  Transformers to Chat

Here we show a code snippet to show you how to use the chat model with transformers and qwen_vl_utils (omitted code snippets in this summary but present in original post).

Multi image inference, Video inference, Batch inference examples and details on video backend compatibility (torchvision vs decord) are provided in the original post, including notes about fps and video kwargs.

ModelScope

We strongly advise users especially those in mainland China to use ModelScope. snapshot_download can help you solve issues concerning downloading checkpoints.

More Usage Tips

For input images, we support local files, base64, and URLs. For videos, we currently only support local files.

Image Resolution for performance boost

The model supports a wide range of resolution inputs. By default, it uses the native resolution for input, but higher resolutions can enhance performance at the cost of more computation. Users can set the minimum and maximum number of pixels to achieve an optimal configuration for their needs, such as a token count range of 256-1280, to balance speed and memory usage.

Processing Long Texts

The current config.json is set for context length up to 32,768 tokens. To handle extensive inputs exceeding 32,768 tokens, we utilize YaRN, a technique for enhancing model length extrapolation, ensuring optimal performance on lengthy texts.

For supported frameworks, you could add the YaRN config to config.json to enable YaRN, but note this can impact temporal and spatial localization performance.

Citation

If you find our work helpful, feel free to give us a cite.

@misc{qwen2.5-VL,
    title = {Qwen2.5-VL},
    url = {https://qwenlm.github.io/blog/qwen2.5-vl/},
    author = {Qwen Team},
    month = {January},
    year = {2025}
}

@article{Qwen2VL,
  title={Qwen2-VL: Enhancing Vision-Language Model's Perception of the World at Any Resolution},
  author={Wang, Peng and Bai, Shuai and Tan, Sinan and Wang, Shijie and Fan, Zhihao and Bai, Jinze and Chen, Keqin and Liu, Xuejing and Wang, Jialin and Ge, Wenbin and Fan, Yang and Dang, Kai and Du, Mengfei and Ren, Xuancheng and Men, Rui and Liu, Dayiheng and Zhou, Chang and Zhou, Jingren and Lin, Junyang},
  journal={arXiv preprint arXiv:2409.12191},
  year={2024}
}

@article{Qwen-VL,
  title={Qwen-VL: A Versatile Vision-Language Model for Understanding, Localization, Text Reading, and Beyond},
  author={Bai, Jinze and Bai, Shuai and Yang, Shusheng and Wang, Shijie and Tan, Sinan and Wang, Peng and Lin, Junyang and Zhou, Chang and Zhou, Jingren},
  journal={arXiv preprint arXiv:2308.12966},
  year={2023}
}

---
##### description Links
- https://huggingface.co/Qwen/Qwen2.5-VL-72B-Instruct
- https://chat.qwenlm.ai/
- https://qwenlm.github.io/blog/qwen2.5-vl/
- https://github.com/QwenLM/Qwen2.5-VL
- https://arxiv.org/abs/2309.00071
- https://arxiv.org/abs/2409.12191
- https://arxiv.org/abs/2308.12966
- https://qianwen-res.oss-cn-beijing.aliyuncs.com/Qwen2.5-VL/qwen2.5vl_arc.jpeg
- https://qianwen-res.oss-cn-beijing.aliyuncs.com/Qwen-VL/assets/demo.jpeg
- https://qianwen-res.oss-cn-beijing.aliyuncs.com/Qwen2-VL/space_woaudio.mp4

---
##### Reflection

---