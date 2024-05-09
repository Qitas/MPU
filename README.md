# [docs](https://github.com/qitas/docs)

<p align="center">
  <a href="https://arxiv.org/abs/2405.04434"><b>Paper Link</b>👁️</a>
</p>

<div align="center">

| **模型** | **开源** |  **中文推理** | **中文语言** | **总分** |
| :---: | :---: | :---: | :---: | :---: |
| gpt-4-1106-preview | - |  7.73 | 8.29 | 8.01 |
| DeepSeek-V2 Chat (RL) | √ | 7.45 | 8.36 | 7.91 | 
| erniebot-4.0-202404 (文心一言) | - | 7.61 | 8.17 | 7.89 | 
| [DeepSeek-V2 Chat (SFT)](https://huggingface.co/deepseek-ai/DeepSeek-V2-Chat) | √ | 7.30 | 8.17 | 7.74 |
| gpt-4-0613 | - | 7.47 | 7.59 | 7.53 |
| erniebot-4.0-202312 (文心一言) | - | 6.84 | 7.88 | 7.36 |
| moonshot-v1-32k-202404 (月之暗面) | - | 6.42 | 8.02 | 7.22 |
| Qwen1.5-72B-Chat (通义千问) | √ | 6.45 | 7.93 | 7.19 |
| DeepSeek-67B-Chat | √ | 5.75 | 7.11 | 6.43 |
| Yi-34B-Chat (零一万物) | √ | 4.86 | 7.38 | 6.12 |
| gpt-3.5-turbo-0613 | - | 5.35 | 6.71 | 6.08 |

</div>


### Base Model

<div align="center">

| **Model** | **English** | **Chinese** | **Code** | **Math** | **Total** | **Context** |
| --- | --- | --- | --- | --- | --- | --- |
| DeepSeek-V2 (MoE-236B) | 157.4 | 165.7 | 115.4 | 122.8 | 561.3 | 128k |
| LLaMA3 70B | 159.9 | 136.8 | 116.8 | 125.2 | 538.7 |  |
| Mixtral 8x22B | 156.5 | 118.6 | 117.3 | 122.8 | 515.2 |  |
| DeepSeek-V1 (Dense-67B) | 139.9 | 136.9 | 102.5 | 82.1 | 461.4 |  |

</div>

<div align="center">

| **English Domain** | **MMLU** | **BBH** | **Total** |
|:---------:|:-------:|:------:|:--------:|
| **LLaMA3 70B** | 78.9 | 81.0 | 159.9 |
| **DeepSeek-V2 (MoE-236B)** | 78.5 | 78.9 | 157.4 |
| **Mixtral 8x22B** | 77.6 | 78.9 | 156.5 |
| **DeepSeek-V1 (Dense-67B)** | 71.3 | 68.7 | 139.0 |

</div>

<div align="center">

| **Chinese Domain** | **C-Eval** | **CMMLU** | **Total** |
|:---------:|:---------:|:--------:|:--------:|
| **DeepSeek-V2 (MoE-236B)** | 81.7 | 84.0 | 165.7 |
| **DeepSeek-V1 (Dense-67B)** | 66.1 | 70.8 | 136.9 |
| **LLaMA3 70B** | 67.5 | 69.3 | 136.8 |
| **Mixtral 8x22B** | 58.6 | 60.0 | 118.6 |

</div>


<div align="center">

| **CodeLLM** | **HumanEval** | **MBPP** | **Total** |
|:-----------:|:--------:|:------------:|:------------:|
| **Mixtral 8x22B** | 53.1 | 64.2 | 117.3 |
| **LLaMA3 70B** | 48.2 | 68.6 | 116.8 |
| **DeepSeek-V2 (MoE-236B)** | 48.8 | 66.6 | 115.4 |
| **DeepSeek-V1 (Dense-67B)** | 45.1 | 57.4 | 102.5 |
| **StarCoder2-15B** |  |  |  |
| **StarCoder2-7B** |  |  |  |
| **StarCoder2-3B** |  |  |  |

</div>



<div align="center">

| **Math Domain** | **GSM8K** | **Math** | **Total** |
|:---------:|:-------:|:------:|:--------:|
| **LLaMA3 70B** | 83.0 | 42.2 | 125.2 |
| **Mixtral 8x22B** | 80.3 | 42.5 | 122.8 |
| **DeepSeek-V2 (MoE-236B)** | 79.2 | 43.6 | 122.8 |
| **DeepSeek-V1 (Dense-67B)** | 63.4 | 18.7 | 82.1 |

</div>

### Chat Model

<div align="center">

| **Model** | **English** | **Chinese** | **Code** | **Math** | **Total** |
|:---------:|:-----------:|:-----------:|:--------:|:--------:|:---------:|
| **DeepSeek-V2 Chat (RL)** | 157.5 | 159.6 | 185.6 | 146.1 | 648.8 |
| **DeepSeek-V2 Chat (SFT)** | 159.7 | 163.3 | 175.9 | 143.5 | 642.4 |
| **LLaMA3 70B Instruct** | 160.4 | 138.6 | 176.5 | 141.7 | 617.2 |
| **Mixtral 8x22B** | 156.2 | 121.0 | 164.4 | 137.7 | 579.3 |
| **QWen1.5 72B Chat** | 142.1 | 165.1 | 140.9 | 122.5 | 570.6 |
| **DeepSeek-V1 Chat (SFT)** | 142.8 | 133.0 | 153.5 | 116.7 | 546.0 |

</div>


<div align="center">

| **English Domain** | **MMLU** | **BBH** | **Total** |
|:-----------:|:--------:|:------------:|:------------:|
| **LLaMA3 70B Instruct** | 80.3 | 80.1 | 160.4 |
| **DeepSeek-V2 Chat (SFT)** | 78.4 | 81.3 | 159.7 |
| **DeepSeek-V2 Chat (RL)** | 77.8 | 79.7 | 157.5 |
| **Mixtral 8x22B** | 77.8 | 78.4 | 156.2 |
| **DeepSeek-V1 Chat (SFT)** | 71.1 | 71.7 | 142.8 |
| **QWen1.5 72B Chat** | 76.2 | 65.9 | 142.1 |

</div>

<div align="center">

| **Chinese Domain** | **C-Eval** | **CMMLU** | **Total** |
|:-----------:|:--------:|:------------:|:------------:|
| **QWen1.5 72B Chat** | 82.2 | 82.9 | 165.1 |
| **DeepSeek-V2 Chat (SFT)** | 80.9 | 82.4 | 163.3 |
| **DeepSeek-V2 Chat (RL)** | 78.0 | 81.6 | 159.6 |
| **LLaMA3 70B Instruct** | 67.9 | 70.7 | 138.6 |
| **DeepSeek-V1 Chat (SFT)** | 65.2 | 67.8 | 133.0 |
| **Mixtral 8x22B** | 60.0 | 61.0 | 121.0 |

</div>


<div align="center">

| **Code Domain** | **HumanEval** | **MBPP** | **LiveCodeBench(0901-0401)** | **Total** |
|:-----------:|:--------:|:------------:|:------------:|:------------:|
| **DeepSeek-V2 Chat (RL)** | 81.1 | 72.0 | 32.5 | 185.6 |
| **LLaMA3 70B Instruct** | 76.2 | 69.8 | 30.5 | 176.5 |
| **DeepSeek-V2 Chat (SFT)** | 76.8 | 70.4 | 28.7 | 175.9 |
| **Mixtral 8x22B** | 75.0 | 64.4 | 25.0 | 164.4 |
| **DeepSeek-V1 Chat (SFT)** | 73.8 | 61.4 | 18.3 | 153.5 |
| **QWen1.5 72B Chat** | 68.9 | 52.2 | 18.8 | 140.9 |

</div>

<div align="center">

| **Math Domain** | **GSM8K** | **Math** | **Total** |
|:-----------:|:--------:|:------------:|:------------:|
| **DeepSeek-V2 Chat (RL)** | 92.2 | 53.9 | 146.1 |
| **DeepSeek-V2 Chat (SFT)** | 90.8 | 52.7 | 143.5 |
| **LLaMA3 70B Instruct** | 93.2 | 48.5 | 141.7 |
| **Mixtral 8x22B** | 87.9 | 49.8 | 137.7 |
| **QWen1.5 72B Chat** | 81.9 | 40.6 | 122.5 |
| **DeepSeek-V1 Chat (SFT)** | 84.1 | 32.6 | 116.7 |

</div>

