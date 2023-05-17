### BERT Fine-Tuning 指南（with PyTorch）

摘自：【译】BERT Fine-Tuning 指南（with PyTorch） - 程序员在深圳的文章 - 知乎

知乎链接：https://zhuanlan.zhihu.com/p/143209797

zip文件解压缩的python代码：
```python
import zipfile

zipPath = "dataset/cola_public_1.1.zip"
zipFile = zipfile.ZipFile(zipPath)
zipFile.extractall('./dataset/')
print('解压结束......')
zipFile.close()
```
