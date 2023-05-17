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
