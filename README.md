# Chinese medical dialogue data 中文医疗问答数据集

## 数据

### Data_数据中有6个文件夹分别是:
>**<Andriatria_男科>**  94596个问答对
> **<IM_内科>**        220606个问答对
**<OAGD_妇产科>**      183751个问答对
**<Oncology_肿瘤科>**   75553个问答对
 **<Pediatric_儿科>**  101602个问答对
 **<Surgical_外科>**   115991个问答对
 总计 792099个问答对

### 每个文件夹下有一个csv文件，其中的数据格式为:

department | title | ask |  answer
:-: | :-: | :-: | :-: 
心血管科|高血压患者能吃党参吗？|我有高血压这两天女婿来的时候给我拿了些党参泡水喝，您好高血压可以吃党参吗？|高血压病人可以口服党参的。党参有降血脂，降血压的作用，可以彻底消除血液中的垃圾，从而对冠心病以及心血管疾病的患者都有一定的稳定预防工作作用，因此平时口服党参能远离三高的危害。另外党参除了益气养血，降低中枢神经作用，调整消化系统功能，健脾补肺的功能。感谢您的进行咨询，期望我的解释对你有所帮助。|
消化科|哪家医院能治胃反流|烧心，打隔，咳嗽低烧，以有4年多| 建议你用奥美拉唑同时，加用吗丁啉或莫沙必利或援生力维，另外还可以加用达喜片|

## ChatGLM-6B 微调

### 数据格式

```json
    {
        "instruction": "现在你是一个神经脑外科医生，请根据患者的问题给出建议：",
        "input": "癫痫病能吃德巴金吗，错觉，有时候感觉看到的和听到的不太一样。",
        "output": "巴金是广谱抗病药物，主要作用于中枢神经系统，对动物的药理研究发现德巴金对各种癫痫的实验模型（全身性和部分性）均有抗惊厥作用，对人的各种类型癫痫发作有抑制作用，作用机理可能与增加γ-氨基丁酸的浓度有关。 主要是治癫痫药物。建议在医生的知道下，用药，祝您身体早日康复。"
    },
    {
        "instruction": "现在你是一个生殖医学科医生，请根据患者的问题给出建议：",
        "input": "男性输精管堵塞的症状会出现什么，男性输精管堵塞的症状会出现什么？输精管堵塞的症状会有哪些？",
        "output": "输精管堵塞的症状一\n输精管道的先天性梗阻：先天性输精管缺如或闭塞、先天性附睾发育不良、附睾与睾丸不连接、先天性精囊缺如或射精管缺如。\n输精管堵塞的症状二\n输精管道的感染：这一输精管堵塞的症状有结核、淋病及血丝虫病，当结核杆菌侵及输精管壁，使输精管壁增厚，输精管变硬变粗，呈串珠状，病变可沿输精管蔓延到附睾尾，然后波及整个附睾和睾丸。球菌感染主要破坏附睾尾部，很少侵及附睾头，输精管也常常受累。丝虫病感染侵及输精管、附睾时，同样可造成其阻塞而不通。当感染侵及前列腺、精囊时，输精管道梗阻症状可表现"
    },
```

### 结果
在ChatGLM-6B上微调的结果，随机选择了1/30的数据进行微调，下表为评估结果。

|   分数  |  ChatGLM-6B | P-Tuning V2 (p=64) | LoRA (r=8) | LoRA-INT8 (r=8) |
| ------- | -------- | ----- | ------| -------- |
| BLEU-4  |  3.21   | 3.55 | 4.21 | 3.58 |
| Rouge-1 |  17.19   | 18.42 | 18.74 | 17.88 |
| Rouge-2 |  3.07   | 2.74 | 3.56 | 3.10 |
| Rouge-l |  15.47   | 15.02 | 16.61 | 15.84 |
| 训练参数占比 |  /       | 0.06% | 0.06% | 0.06% |






            

