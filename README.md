### BERT Fine-Tuning 学习（with PyTorch）
参考：【译】BERT Fine-Tuning 指南（with PyTorch） - 程序员在深圳的文章 - 知乎
知乎链接：https://zhuanlan.zhihu.com/p/143209797

#### zip文件解压缩
```python
import zipfile

zipPath = "dataset/cola_public_1.1.zip"
zipFile = zipfile.ZipFile(zipPath)
zipFile.extractall('./dataset/')
print('解压结束......')
zipFile.close()
```
#### 设置Jupyter内核
在参考这篇文章练习时踩了一些坑，比如jupyter notebook切换内核时，如果从网页端的terminal进去安装，这样使用的不是已经安装好的环境中的python和依赖包。此时我们应该在Anaconda prompt虚拟环境中直接安装jupyter notebook，然后启动。
```bash
# 激活虚拟环境
conda activate pytorch
# 在虚拟环境中安装ipykernal
conda install ipykernel
# 继续在该环境中安装nb_conda
conda install -c conda-forge nb_conda
# 在该环境中启动 jupyter notebook
jupyter notebook
```
切换内核的方法
![image](https://github.com/QiufenChen/CPPPred/assets/52032167/db1a9a2b-aba0-4b33-ac42-5f9380cafc68)

#### 查看pytorch版本的方法
```python
import torch
print(torch.__version__)  #注意是双下划线
# cuda是否可用
print(torch.cuda.is_available())
```
#### 遇到的BUG
```bash
NameError: name 'PartialState' is not defined.
```
原因分析：transformers的版本过高，需要指定安装4.28版本
```bash
pip install transformers==4.28.0
```
**Out of memery**
![image](https://github.com/QiufenChen/CPPPred/assets/52032167/8a8c4d7a-8cf0-4bf1-aa68-35c03dc90208)
原因分析：我的电脑显存不够, 顺利跑通prot-bert-bfd, 至少需要10G(需要配置一个16G的显卡), 而我的只有8G显存!!
![image](https://github.com/QiufenChen/CPPPred/assets/52032167/7a175be5-d14e-443d-8404-f9d1f57f5f29)

#### CPP数据集上的初步表现
关于蛋白的诸多预训练模型见链接：https://huggingface.co/Rostlab \
本实验用的预训练模型是prot-bert-bfd, 代码参考：https://github.com/agemagician/ProtTrans/blob/19741d0e1e5f528235dec9508d01faadef0dced8/Fine-Tuning/ProtBert_BFD_FineTuning_MS.ipynb \
通过将fine-tune之后，我们的实验数据取得了不错的效果，如下图所示：
![cffd98767e12279528f49171a9237dd](https://github.com/QiufenChen/CPPPred/assets/52032167/01282527-0b26-476b-9f20-8289977fc808)

#### 接下来的学习方向
目标: 做一个序列生成模型, 设计一个我们自己的CPPGan
当前的想法：参考SeqGan的设计思路, 先把这条路走通, 然后再魔改
![image](https://github.com/QiufenChen/CPPPred/assets/52032167/4b2905d9-4f07-468e-9b4e-6a7d5609f3ea)
