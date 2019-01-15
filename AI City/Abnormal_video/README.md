# 视频异常检测

代码运行过程如下：

- 下载数据集：

[**Avenue Dataset for Abnormal Event Detection**](http://www.cse.cuhk.edu.hk/leojia/projects/detectabnormal/dataset.html)

[**UCSD Anomaly Detection Dataset**](http://www.svcl.ucsd.edu/projects/anomaly/dataset.html)

- 解压两个数据集：

建议使用Avenue数据集进行训练与测试

- 安装ffmpeg 

下载地址：[**ffmpeg** ](http://ffmpeg.org/download.html#build-windows)

windows下将其下载下来解压，并将bin目录配置path中！

linux下安装：sudo apt-get install ffmpeg

mac下安装：brew install ffmpeg for macOS

- 数据集处理

这里以Avenue为例：将数据集中的训练与测试集数据分别拷贝到train与test文件夹！

【**training.npy**】

然后分两次运行process.py，第一次运行如下：

进入process.py，将np.save('training.npy',imagestore)打开，注释掉np.save('test.npy',imagestore)！

运行 

```python
python3 processor.py ./train 5
```

然后会在train目录下得到frame图片，以及得到training.npy文件！

【**test.npy**】

再次进入process.py，将np.save('training.npy',imagestore)注释，打开np.save('test.npy',imagestore)！

运行

```python
python3 processor.py ./test 5
```

然后会在test目录下得到frame图片，以及得到test.npy文件！

- 训练

```python
python3 train.py n_epochs(enter integer)
```

举个例子：

```python
python3 train.py 10  # 根据论文提示，最大不要超过50！
```

运行后得到AnomalyDetector.h5模型！

- 测试

运行test.py

```python
python3 test.py
```

- 应用

运行模型在现实摄像头领域！

```python
python3 start_live_feed.py 'AnomalyDetector.h5'
```

