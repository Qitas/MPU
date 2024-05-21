# [docs](https://github.com/qitas/docs)

<p align="center">
  <a href="https://arxiv.org/abs/2405.04434"><b>Paper Link</b>👁️</a>
</p>

<div align="center">

| **模型** | **开源** |  **中文推理** | **中文语言** | **总分** |
| :---: | :---: | :---: | :---: | :---: |
| GPT-4-1106-preview | - |  7.73 | 8.29 | 8.01 |
| DeepSeek-V2-Chat(RL) | √ | 7.45 | 8.36 | 7.91 | 
| erniebot-4.0-202404 (文心一言) | - | 7.61 | 8.17 | 7.89 | 
| DeepSeek-V2-Chat(SFT) | √ | 7.30 | 8.17 | 7.74 |
| GPT-4-0613 | - | 7.47 | 7.59 | 7.53 |
| erniebot-4.0-202312 (文心一言) | - | 6.84 | 7.88 | 7.36 |
| moonshot-v1-32k-202404 (月之暗面) | - | 6.42 | 8.02 | 7.22 |
| Qwen1.5-72B-Chat (通义千问) | √ | 6.45 | 7.93 | 7.19 |
| DeepSeek-67B-Chat | √ | 5.75 | 7.11 | 6.43 |
| Yi-34B-Chat (零一万物) | √ | 4.86 | 7.38 | 6.12 |
| GPT-3.5-turbo-0613 | - | 5.35 | 6.71 | 6.08 |

</div>

<div align="center">

| **小模型** | **开源** | **中文推理** | **中文语言** | **英文** | **编码** | 
| :---: | :---: | :---: | :---: | :---: | :---: |
| **Yi-1.5-9B** | √ |    |   |   |
| **Yi-1.5-6B** | √ |    |   |   |

</div>



<div align="center">

| **Model** | **English** | **Chinese** | **Code** | **Math** | **Params** | **Context** |
| --- | --- | --- | --- | --- | --- | --- |
| **DeepSeek-V2-Chat(RL)** | 157.5 | 159.6 | 185.6 | 146.1 |   |
| **DeepSeek-V2-Chat(SFT)** | 159.7 | 163.3 | 175.9 | 143.5 |   |
| **LLaMA3-70B-Instruct** | 160.4 | 138.6 | 176.5 | 141.7 |   |
| Mixtral-8x22B | 156.2 | 121.0 | 164.4 | 137.7 | 44/176 |
| QWen1.5-72B-Chat | 142.1 | 165.1 | 140.9 | 122.5 |   |
| **DeepSeek-V2(MoE-236B)** | 157.4 | 165.7 | 115.4 | 122.8 |   | 128k |
| DeepSeek-V1-Chat(SFT) | 142.8 | 133.0 | 153.5 | 116.7 |   |
| LLaMA3-70B | 159.9 | 136.8 | 116.8 | 125.2 |   |  |
| Mixtral-8x7B | |  |  |  |  13/56 |  |
| DeepSeek-V1(Dense-67B) | 139.9 | 136.9 | 102.5 | 82.1 |   |  |
| **DeepSeek-V2-Lite-Chat** |  |  |  |  | 2.4/15.7 |  32K |
| **Arctic-128×3.66B(MoE-480B)** |  |  |  |  | 17/480 |    |

</div>

## English

<div align="center">

| **English Domain** | **MMLU** | **BBH** | **Total** |
|:-----------:|:--------:|:------------:|:------------:|
| Claude-3-Opus | 86.8%(5-shot) | 86.8%(3-shot) |  | 
| **LLaMA3-70B-Instruct** | 80.3 | 80.1 | 160.4 |
| **LLaMA3-70B** | 78.9 | 81.0 | 159.9 |
| **DeepSeek-V2-Chat(SFT)** | 78.4 | 81.3 | 159.7 |
| **DeepSeek-V2-Chat(RL)** | 77.8 | 79.7 | 157.5 |
| **DeepSeek-V2(MoE-236B)** | 78.5 | 78.9 | 157.4 |
| **Mixtral-8x22B** | 77.6 | 78.9 | 156.5 |
| **Mixtral-8x7B** | 70.4 |  |  |
| **DeepSeek-V1 Chat(SFT)** | 71.1 | 71.7 | 142.8 |
| **QWen1.5-72B-Chat** | 77.3 | 65.9 | 142.1 |
| **Yi-1.5-34B-Chat** | 76.8 |  |  |
| **Yi-1.5-9B-Chat** | 69.5 | 72.4 |  |
| **Yi-1.5-6B-Chat** | 63.5 | 59.0 |  |
| QWen1.5-32B-Chat | 74.3 | |  |  |
| Mixtral-8x7B-Instruct-v0.1 | 71.4 |  |  |
| Mixtral-8x22B-Instruct-v0.1 | 77.7 |  |  |
| DeepSeek-V1(Dense-67B) | 71.3 | 68.7 | 139.0 |
| GPT-4 | 86.4 | 86.7 |   |   |
| **DeepSeek-V2-Lite-Chat** | 55.7 | 48.1 |  |  
| DeepSeekMoE-16B-Chat | 47.2 | 42.2 |  |   
| DeepSeek-7B-Chat | 49.7 | 43.1 |  |  
| **Arctic-128×3.66B(MoE-480B)** | 67.3? |  |  |  | 

</div>

## Chinese

<div align="center">

| **Chinese Domain** | **C-Eval** | **CMMLU** | **CLUEWSC** |
|:-----------:|:--------:|:------------:|:------------:|
| **DeepSeek-V2 (MoE-236B)** | 81.7 | 84.0 |   |
| **QWen1.5-72B-Chat** | 82.2 | 82.9 |   |
| **DeepSeek-V2-Chat(SFT)** | 80.9 | 82.4 |   |
| **DeepSeek-V2-Chat(RL)** | 78.0 | 81.6 |   |
| **LLaMA3-70B-Instruct** | 67.9 | 70.7 |   |
| DeepSeek-V1(Dense-67B) | 66.1 | 70.8 |   |
| **LLaMA3-70B** | 67.5 | 69.3 |  |
| DeepSeek-V1-Chat(SFT) | 65.2 | 67.8 |   |
| Mixtral-8x22B | 60.0 | 61.0 |   |
| GPT-4 | 69.9| 71.0 |  |
| QWen-14B-Chat | 71.7 | 70.0 |  |
| [Yi-34B-Chat](https://github.com/OrionStarAI/OrionStar-Yi-34B-Chat) | 77.71 | 73.52 |  |
| **QWen1.5-7B-Chat** |  | 73.4 |  |
| **Yi-1.5-9B** |  | 74.8 |   |   |
| **Yi-1.5-6B** |  | 70.8 |   |   |
| **DeepSeek-V2-Lite-Chat** | 60.1 | 62.5 | 80.0 |  
| DeepSeekMoE-16B-Chat | 40.0 | 49.3 | 68.2 |  
| DeepSeek-7B-Chat | 44.7 | 51.2 | 66.2 |  


</div>

## Code

<div align="center">

| **Code Domain** | HumanEval | MBPP | LiveCodeBench(0901-0401) | MT-Bench |
|:-----------:|:--------:|:------------:|:------------:|:------------:|
| Claude-3-Opus | 84.9%(0-shot) |   |   |  |
| **DeepSeek-V2-Chat(RL)** | 81.1 | 72.0 | 32.5 |  |
| **LLaMA3 70B Instruct** | 76.2 | 69.8 | 30.5 |  |
| **DeepSeek-V2-Chat(SFT)** | 76.8 | 70.4 | 28.7 |  |
| **Yi-1.5-34B-Chat** | 75.2 | 74.6 |  | 8.5 |
| **Mixtral-8x22B** | 75.0 | 64.4 | 25.0 |  |
| DeepSeek-V1-Chat(SFT) | 73.8 | 61.4 | 18.3 |  |
| **QWen1.5-72B-Chat** | 64.6 | 72.5 | 18.8 | 8.61 |
| **LLaMA3-70B** | 48.2 | 68.6 |  |
| **DeepSeek-V2(MoE-236B)** | 48.8 | 66.6 |  |
| **Yi-1.5-9B-Chat** | 66.5 | 78.8 |  | 8.2 |
| **Yi-1.5-6B-Chat** | 64.0 | 70.9 |  | 7.5 |
| **LLaMA3-8B-Instruct** | 61.6 | 61.4 |  | 8.0 |
| DeepSeek-V1(Dense-67B) | 45.1 | 57.4 |  |
| **QWen1.5-32B-Chat** | 51.2 | 66.9 |  | 8.3 |
| **QWen1.5-14B-Chat** |   |  |  | 7.91 |
| Mixtral-8x7B-Instruct-v0.1 | 45.1 | 59.5 |  | 8.3 |
| Mixtral-8x22B-Instruct-v0.1 | 76.2 | 73.8 |  | 8.6 |
| **QWen1.5-7B-Chat** | 36.0 | 46.1 |  | 7.60 |
| **Yi-1.5-9B** | 41.4 | 61.1 |   |   |
| **Yi-1.5-6B** | 36.5 | 56.8 |   |   |
| **DeepSeek-V2-Lite-Chat** | 57.3 | 45.8 |   |   |
| DeepSeekMoE-16B-Chat | 45.7 | 46.2 |  |  |
| DeepSeek-7B-Chat | 45.1 | 39.0 | |  |

</div>

<div align="center">

| HumanEval | Pass@1 | Pass@10 | 0-shot | 5-shot |
|:-----------:|:--------:|:------------:|:------------:|:------------:|
| Claude-3-Opus |  |   | 84.9%  |  |
| **StarCoder2-15B** |  |  |  |
| **StarCoder2-7B**  |  |  |  |
| **StarCoder2-3B**  |  |  |  |
| **LLaMA3-70B**     |  |  | 81.7 |
| **LLaMA3-8B**      |  |  | 62.2 |
| Yi-Chat-34B | 7.9 |  |  |  |
| QWen-14B-Chat | 11.1 |  |  |  |
| DeepSeek-Coder-33B-Instruct | 31.7 |  |  |  |
| GPT-4-Turbo | 48.4 |  |  |  |

</div>



## Math


<div align="center">

| **Math Domain** | **GSM8K** | **MATH** | **CMath** |
|:-----------:|:--------:|:------------:|:------------:|
| Claude-3-Opus | 95.0%(0-shot) | 60.1%(0-shot) |  | 
| **DeepSeek-V2 Chat (RL)** | 92.2 | 53.9 |   |
| **DeepSeek-V2 Chat (SFT)** | 90.8 | 52.7 |   |
| **LLaMA3-70B Instruct** | 93.2 | 48.5 |  |
| **Mixtral-8x22B** | 87.9 | 49.8 |  |
| **LLaMA3-70B** | 83.0 | 42.2 |  |
| **DeepSeek-V2 (MoE-236B)** | 79.2 | 43.6 |  |
| **QWen1.5-72B-Chat** | 86.0 | 44.4 |  |
| DeepSeek-V1 Chat (SFT) | 84.1 | 32.6 |  |
| DeepSeek-V1 (Dense-67B) | 63.4 | 18.7 |  |
| **Yi-1.5-34B-Chat** | 90.2 | 50.1 |  |
| **QWen1.5-32B-Chat** | 83.9 | 43.3 |  |
| Mixtral-8x7B-Instruct-v0.1 | 65.7 | 28.4 |  |
| Mixtral-8x22B-Instruct-v0.1 | 84.0 | 41.1 |  |
| **QWen1.5-7B-Chat** | 70.1 | 20.3 |  |
| **LLaMA3-70B** | 54.7 | 21.16 |  |
| **Yi-1.5-9B** | 73.7 | 32.6 |   |   |
| **Yi-1.5-6B** | 62.2 | 28.42 |   |   |
| DeepSeek-7B-Chat | 62.6 | 14.7 | 66.4 |
| DeepSeekMoE-16B-Chat | 62.2 | 15.2 | 67.9 |
| **DeepSeek-V2-Lite-Chat** | 72.0 | 27.9 | 71.7 |
| **Arctic-128×3.66B(MoE-480B)** | 74.2 |  |  |  |    |

</div>

