# gemma-2-9b-chinese-instruct with SFT and DPO

<div style="text-align: center;">
  <img src="https://github.com/jiangfeibo/gemma-2-9b-chinese-instruct/blob/main/README.assets/gemma2.jpg" alt="image text" width="500" />
</div>

## 项目简介

Gemma 2系列模型是谷歌于2024年6月27日发布的开源大模型，其中Gemma 2-9B的性能在同类产品中处于领先地位，超过了Llama 3 8B和其他同规模的开源模型。Gemma 2-9B-Instruct模型，凭借其庞大的参数规模、卓越的自然语言理解能力以及灵活的指令执行能力，在全球范围内备受瞩目并赢得了高度评价。该模型在广泛的自然语言处理任务中，如文本创作、智能问答、信息摘要等，均展现出了非凡的性能，为人工智能技术的创新与应用奠定了坚实的基础。

本项目基于Gemma2-9B-Instruct模型，与当前相关工作不同的是，我们采用了指令微调（Instruction Fine-tuning）和直接偏好对齐（Direct Preference Optimization, DPO）二阶段的学习方法，使用近百万条高质量的中英文混合数据进行有监督指令微调，然后应用2500条对齐指令进行直接偏好对齐，旨在不损坏Gemma2基础能力的前提下进一步提升模型在中文语境下的zero-shot理解和生成能力，该能力对于使用大模型的普通用户非常重要。在两个权威的中文评测基准下，C-Eval的zero-shot性能提升了87.41%，CMMLU的zero-shot性能提升了83.34%。我们公开了该项目所有的模型权重和训练数据集，欢迎大家一起学习和探讨。



 

#### 模型特点

基础模型：基于开源的gemma2-9b-instruct，这是一个经过指令微调的大型语言模型。 

指令微调：利用丰富的中文数据集和英文数据集，代码数据集，逻辑推理数据集进行混合微调，旨在不损害模型基础能力的前提下显著提升模型在中文语境下的zero-shot理解和生成能力。

DPO对齐：进一步提升语言模型在特定任务或场景下的输出质量，使其更加符合人类的偏好或需求。

 

## 安装与加载

克隆本项目到本地：https://huggingface.co/jiangfb/gemma-2-chinese-9b-it-dpo

git clone 

 

## 模型测评：

C-Eval：C-Eval 是一个全面的中文基础模型评估套件。它包含了大量的多项选择题，涵盖了人文、社科、理工以及其他专业四个大方向，包括52个不同的学科和四个难度级别。

| C-Eval(0-shot) | Average | Average(hard) | STEM | Social Sciences | Humanities | Other |
| -------------- | ------- | ------------- | ---- | --------------- | ---------- | ----- |
| 原生Gemma2模型        | 29.4    | 22.1          | 27.8 | 29.6            | 31.7       | 29.5  |
| 我们的Gemma2模型         | 55.1    | 43            | 53.5 | 64.3            | 50.8       | 53.8  |

 

CMMLU：CMMLU是一个综合性的中文评估基准，专门用于评估语言模型在中文语境下的知识和推理能力。CMMLU涵盖了从基础学科到高级专业水平的67个主题。它包括：需要计算和推理的自然科学，需要知识的人文科学和社会科学,以及需要生活常识的中国驾驶规则等。

| CMMLU(0-shot) | Average | STEM  | Social Sciences | Humanities | Other |
| ------------- | ------- | ----- | --------------- | ---------- | ----- |
| 原生Gemma2模型        | 31.88   | 30.34 | 31.74           | 30.49      | 34.57 |
| 我们的Gemma2模型       | 58.45   | 51.68 | 60.51           | 57.89      | 62.23 |

 

 

## 数据集

微调数据集：

|                         |                                                              |
| ----------------------- | ------------------------------------------------------------ |
| 中文微调数据集          | https://modelscope.cn/datasets/zhuangxialie/Llama3-Chinese-Dataset/files |
| code                    | https://huggingface.co/datasets/iamtarun/python_code_instructions_18k_alpaca |
| mathglm                 | https://cloud.tsinghua.edu.cn/d/8d9ee3e52bb54afd9c16/        |
| sft-20k                 | https://github.com/CMKRG/QiZhenGPT/blob/main/data/train/sft-20k.json |
| llama_data              | https://github.com/SCIR-HI/Huatuo-Llama-Med-Chinese/tree/main/data |
| ChatMed_Consult_Dataset | https://huggingface.co/datasets/michaelwzhu/ChatMed_Consult_Dataset |
| ChatMed_TCM-v0.2        | https://huggingface.co/datasets/michaelwzhu/ShenNong_TCM_Dataset |
| smile-train             | https://github.com/qiuhuachuan/smile/tree/main/data          |

 

dpo数据集：

|                   |                                                            |
| ----------------- | ---------------------------------------------------------- |
| DPO-En-Zh-20k     | https://huggingface.co/datasets/hiyouga/DPO-En-Zh-20k      |
| orca_dpo_pairs    | https://huggingface.co/datasets/Intel/orca_dpo_pairs       |
| Chinese-dpo-pairs | https://huggingface.co/datasets/wenbopan/Chinese-dpo-pairs |

## 贡献者

朱万运，2909574802@qq.com，湖南师范大学，在读研究生

江沸菠，jiangfb@hunnu.edu.cn，湖南师范大学，副教授

黄鸿洁，sherlor@163.com，湖南师范大学，在读研究生

涂思伟，tusiwei@hunnu.edu.cn，湖南师范大学，在读研究生
 

