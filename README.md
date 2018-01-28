# SharePlatform
The Platform of Machine and Deep Learning.

# GPU
## [tensorflow中使用指定的GPU及GPU显存](https://www.cnblogs.com/darkknightzh/p/6591923.html)

## 终端执行程序时设置使用的GPU
如果电脑有多个GPU，tensorflow默认全部使用。如果想只使用部分GPU，可以设置CUDA_VISIBLE_DEVICES。在调用python程序时，可以使用：
```
CUDA_VISIBLE_DEVICES=1 python my_script.py

Environment Variable Syntax      Results
CUDA_VISIBLE_DEVICES=1           Only device 1 will be seen
CUDA_VISIBLE_DEVICES=0,1         Devices 0 and 1 will be visible
CUDA_VISIBLE_DEVICES="0,1"       Same as above, quotation marks are optional
CUDA_VISIBLE_DEVICES=0,2,3       Devices 0, 2, 3 will be visible; device 1 is masked
CUDA_VISIBLE_DEVICES=""          No GPU will be visible
```

## python代码中设置使用的GPU
如果要在python代码中设置使用的GPU（如使用pycharm进行调试时），可以使用下面的代码：
```
import os
os.environ["CUDA_VISIBLE_DEVICES"] = "2"
```

## 设置tensorflow使用的显存大小
定量设置显存
默认tensorflow是使用GPU尽可能多的显存。可以通过下面的方式，来设置使用的GPU显存：
```
gpu_options = tf.GPUOptions(per_process_gpu_memory_fraction=0.7)
sess = tf.Session(config=tf.ConfigProto(gpu_options=gpu_options))
```
上面分配给tensorflow的GPU显存大小为：GPU实际显存*0.7。
可以按照需要，设置不同的值，来分配显存。
### 按需设置显存
上面的只能设置固定的大小。如果想按需分配，可以使用allow_growth参数：
```
gpu_options = tf.GPUOptions(allow_growth=True)
sess = tf.Session(config=tf.ConfigProto(gpu_options=gpu_options))   
```

# Jupyter Notebook
```
jupyter notebook
```

# TensorBoard
```
tensorboard --logdir=temp/tflog --port=6006
tensorboard --logdir=temp/tflog_mnist --port=6007
```

# Mnist
```failed
python tensorflow/tensorflow/examples/tutorials/mnist/mnist_with_summaries.py --data_dir=data/MNIST/source/ --log_dir=temp/tflog_mnist/
```
```
python tensorflow/tensorflow/examples/tutorials/mnist/mnist_softmax.py --data_dir=data/MNIST/source/
```
```
python tensorflow/tensorflow/examples/tutorials/mnist/fully_connected_feed.py --input_data_dir=data/MNIST/source/ --log_dir=temp/tflog_mnist/
```

