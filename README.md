# LLM-FineTune
Deepspeed、Bloom

#### Model
    Bloom_7B1
 
#### Deepspeed
    zero_3、cpuoffload、fp16
 
#### Gpus
    4*48G A6000

#### Para
    length<500,batchsize=32
   
#### Requriements
    pytorch=1.13.1  deepspeed=0.7.5  tansformers=4.21.0

#### Projects
    1.FineTune: deepspeed --master_addr 0.0.0.0 --master_port 6006 --include localhost:0,1,2,3 ./Model_Bloom.py
    2.convert_deepspeedmodel_fp32: python model_convert32_save.py
    3.inference:python test.py
    
  
#### gradient_checkpointing
    use_cache=False;  batch_size 可以增大10倍以上
    token =1024,batchsize=32*4


####  部分数据源整理
```
中文wiki https://dumps.wikimedia.org/zhwiki/latest/

医疗指南 
链接：https://pan.baidu.com/s/1p3chYKVE9s0Zlr2APJAwNQ 
提取码：tw3q

COT数据集 https://huggingface.co/datasets/QingyiSi/Alpaca-CoT

医疗问答数据项目 Chinese-Medical-Question-Answering-System

医疗书籍类资源： 公众号【小航在奔跑】，免费下载的
```



####  注意
最近在使用6b4_zh_Bloom在进行医疗数据增量预训练，发现这个模型预训练的时候在使用和Bloom_7B1相同的lr=5e-5，第二个epoch时，过拟合现象特别严重。
所以我现在用6b4_zh_Bloom时，使用lr=1e-5，感觉还可以更小一点。
改天将预训练的一些东西整理进来
