# kaggle-The-Global-Multimedia-Deepfake-Detection
   随着人工智能领域技术的飞速发展，深度伪造技术已成为一把双刃剑。它不仅创造了大量 AI 生成的内容，还对数字安全提出了前所未有的挑战Global Multimedia Deepfake旨在真实场景中针对各种类型的 Deepfake 攻击开发、测试和进一步发展更准确、有效和创新的检测模型，并激发创新的防御策略并提高 Deepfake 识别的准确性。
## 项目任务
在这个项目中，项目任务是判断一张人脸图像是否为Deepfake图像，并输出其为Deepfake图像的概率评分。参赛者需要开发和优化检测模型，以应对多样化的Deepfake生成技术和复杂的应用场景，从而提升Deepfake图像检测的准确性和鲁棒性。
#### 数据集下载地址
所有文件都可以使用以下 URL 下载。（如果链接无效，请复制 URL 并将其粘贴到浏览器。由于文件非常大，建议使用以下命令从命令控制台下载数据集：
curl 'http://zoloz-open.oss-cn-hangzhou.aliyuncs.com/waitan2024_deepfake_challenge%2F_%E8%B5%9B%E9%81%931%E5%AF%B9%E5%A4%96%E5%8F%91%E5%B8%83%E6%95%B0%E6%8D%AE%E9%9B%86%2Fphase1.tar.gz?Expires=1726603663&OSSAccessKeyId=LTAI5tAfcZDV5eCa1BBEJL9R&Signature=wFrzBHn5bhULqWzlZP7Z74p1g9c%3D' -o multiFFDI-phase1.tar.gz
视频音频转换好的MEL频谱图下载地址
curl 'https://www.kaggle.com/datasets/ricardosakura/deepfakeoutput'
#### 数据集说明
数据集分为训练集和验证集两部分。使用训练集 (train_label.txt) 来训练模型，而验证集 (val_label.txt) 仅用于模型调优。文件的每一行包含两个部分，分别是图片文件名和标签值（label=1 表示Deepfake图像，label=0 表示真实人脸图像）。例如：

**train_label.txt**

```
img_name,target
3381ccbc4df9e7778b720d53a2987014.jpg,1
63fee8a89581307c0b4fd05a48e0ff79.jpg,0
7eb4553a58ab5a05ba59b40725c903fd.jpg,0
…
```

**val_label.txt**

```
img_name,target
cd0e3907b3312f6046b98187fc25f9c7.jpg,1
aa92be19d0adf91a641301cfcce71e8a.jpg,0
5413a0b706d33ed0208e2e4e2cacaa06.jpg,0
…
```

## 评价指标


#### 评估指标
比赛的性能评估主要使用ROC曲线下的AUC（Area under the ROC Curve）作为指标。AUC的取值范围通常在0.5到1之间。若AUC指标不能区分排名，则会使用TPR@FPR=1E-3作为辅助参考。

**相关公式：**

> 真阳性率 (TPR)：
>
> TPR = TP / (TP + FN)
>
> 假阳性率 (FPR)：
>
> FPR = FP / (FP + TN)
>
> 其中：
> - TP：攻击样本被正确识别为攻击；
> - TN：真实样本被正确识别为真实；
> - FP：真实样本被错误识别为攻击；
> - FN：攻击样本被错误识别为真实。

参考文献：[Aghajan, H., Augusto, J. C., & Delgado, R. L. C. (Eds.). (2009). Human-centric interfaces for ambient intelligence. Academic Press.](https://books.google.com/books?hl=zh-CN&lr=&id=64icBAAAQBAJ&oi=fnd&pg=PP1&dq=Human-centric+interfaces+for+ambient+intelligence&ots=mKNsJrymuK&sig=_ZrNLwqT9R6BDddTLy02FF1B3WE)

# PS
首先感谢dataWhale提供这次难得学习机会，还有感谢Inclusion会议提供的这次比赛，很遗憾因为个人原因没有提交最后的结果导致错失了决赛，但是也从这次比赛中学到了很多，在此对两个团队人员表示真挚的感谢。这篇内容是对这次学习的一个总结，对于这次音视频的识别主要还是对于音频进行一个检测，虽然没有用到多模态的检测，但也取得了不错的效果。讲一下可以优化的点：1.在进行音频转化时，可以进行一个并行处理或利用GPU处理，提升转换速度。 2.增加数据多样性，可以增加高斯处理。3.利用多模态进行一个处理，只利用音频还是较为局限。

