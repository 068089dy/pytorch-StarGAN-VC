## [StarGAN-VC](https://github.com/hujinsen/pytorch-StarGAN-VC)

本项目使用pytorch实现了这篇paper: [StarGAN-VC: Non-parallel many-to-many voice conversion with star generative adversarial networks](https://arxiv.org/abs/1806.02169).

**The converted voice examples are in *samples* directory**



## [依赖](https://github.com/hujinsen/pytorch-StarGAN-VC)
- Python 3.6 
- pytorch 1.0
- librosa 
- pyworld 
- tensorboardX
- scikit-learn


## [使用方法](https://github.com/hujinsen/pytorch-StarGAN-VC)

### 下载数据集

下载 vcc 2016 数据集到当前目录

```
python download.py 
```
下载的zip文件会解压到 `./data/vcc2016_training` 和 `./data/evaluation_all`.

1. **训练数据集:** 论文作者收集了四个 **四个演讲者** 的录音 (`./data/vcc2016_training`). 所以我们要移动相应的文件夹(eg. SF1,SF2,TM1,TM2 ) 到 `./data/speakers`.
2. **测试数据集** 论文作者收集了 **four speakers** 的录音 (`./data/evaluation_all`). 所以我们要移动相应的文件夹(eg. SF1,SF2,TM1,TM2 ) 到 `./data/speakers_test`.

data文件夹现在应该是这样:

```
data
├── speakers  (training set)
│   ├── SF1
│   ├── SF2
│   ├── TM1
│   └── TM2
├── speakers_test (testing set)
│   ├── SF1
│   ├── SF2
│   ├── TM1
│   └── TM2
├── vcc2016_training (vcc 2016 training set)
│   ├── ...
├── evaluation_all (vcc 2016 evaluation set, we use it as testing set)
│   ├── ...
```

### 预处理

从每个演讲片段中提取特征 (mcep, f0, ap)。这些功能存储为npy文件，还要计算每个发言者的统计特征。

```
python preprocess.py
```

这个过程会耗费几分钟 !


### 训练

```
python main.py
```



### 转换


```
python main.py --mode test --test_iters 200000 --src_speaker TM1 --trg_speaker "['TM1','SF1']"
```


## [网络结构](https://github.com/hujinsen/pytorch-StarGAN-VC)

![Snip20181102_2](https://github.com/hujinsen/StarGAN-Voice-Conversion/raw/master/imgs/Snip20181102_2.png)



注意: 我们实现的论文中原生的网络结构, 当 [pytorch StarGAN-VC code](https://github.com/liusongxiang/StarGAN-Voice-Conversion) 使用StarGAN的网络，可以产生不错的语音质量。

## [参考](https://github.com/hujinsen/pytorch-StarGAN-VC)
[tensorflow StarGAN-VC code](https://github.com/hujinsen/StarGAN-Voice-Conversion)

[StarGAN code](https://github.com/taki0112/StarGAN-Tensorflow)

[CycleGAN-VC code](https://github.com/leimao/Voice_Converter_CycleGAN)


[pytorch-StarGAN-VC code](https://github.com/liusongxiang/StarGAN-Voice-Conversion)

[StarGAN-VC paper](https://arxiv.org/abs/1806.02169)

[StarGAN paper](https://arxiv.org/abs/1806.02169)

[CycleGAN paper](https://arxiv.org/abs/1703.10593v4)

---

If you feel this repo is good, please  **star**  ! 

Your encouragement is my biggest motivation!
