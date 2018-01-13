# ub---win
tensorboard： http://lib.csdn.net/article/aiframework/67766

saver：http://blog.csdn.net/u011500062/article/details/51728830

错误：
InvalidArgumentError (see above for traceback): Assign requires shapes of both tensors to match. lhs shape= [6] rhs shape= [2]
	 [[Node: save/Assign_29 = Assign[T=DT_FLOAT, _class=["loc:@Variable_9"], use_locking=true, validate_shape=true, _device="/job:localhost/replica:0/task:0/device:CPU:0"](Variable_9/Adam_1, save/RestoreV2_29)]]
解决： 清空checkpoint就ok了。


http://blog.csdn.net/zyfortirude/article/details/70184278

http://blog.csdn.net/qq_20259459/article/details/70316511



    卷积层：
    tf.nn.conv2d(input, filter, strides, padding, use_cudnn_on_gpu=None, data_format=None, name=None)

参数说明：

    data_format：表示输入的格式，有两种分别为：“NHWC”和“NCHW”，默认为“NHWC”

    input：输入是一个4维格式的（图像）数据，数据的 shape 由 data_format 决定：当 data_format 为“NHWC”输入数据的shape表示为[batch, in_height, in_width, in_channels]，分别表示训练时一个batch的图片数量、图片高度、 图片宽度、 图像通道数。当 data_format 为“NHWC”输入数据的shape表示为[batch, in_channels， in_height, in_width]

    filter：卷积核是一个4维格式的数据：shape表示为：[height,width,in_channels, out_channels]，分别表示卷积核的高、宽、深度（与输入的in_channels应相同）、输出 feature map的个数（即卷积核的个数）。

    strides：表示步长：一个长度为4的一维列表，每个元素跟data_format互相对应，表示在data_format每一维上的移动步长。当输入的默认格式为：“NHWC”，则 strides = [batch , in_height , in_width, in_channels]。其中 batch 和 in_channels 要求一定为1，即只能在一个样本的一个通道上的特征图上进行移动，in_height , in_width表示卷积核在特征图的高度和宽度上移动的布长，即 strideheight 和 stridewidth 。

    padding：表示填充方式：“SAME”表示采用填充的方式，简单地理解为以0填充边缘，当stride为1时，输入和输出的维度相同；“VALID”表示采用不填充的方式，多余地进行丢弃。具体公式：

    “SAME”: output_spatial_shape[i]=⌈(input_spatial_shape[i] / strides[i])⌉

    “VALID”: output_spatial_shape[i]=⌈((input_spatial_shape[i]−(spatial_filter_shape[i]−1)/strides[i])⌉

    池化层：
    tf.nn.max_pool( value, ksize,strides,padding,data_format=’NHWC’,name=None)
    或者
    tf.nn.avg_pool(…)

参数说明：

    value：表示池化的输入：一个4维格式的数据，数据的 shape 由 data_format 决定，默认情况下shape 为[batch, height, width, channels]

    其他参数与 tf.nn.cov2d 类型

    ksize：表示池化窗口的大小：一个长度为4的一维列表，一般为[1, height, width, 1]，因不想在batch和channels上做池化，则将其值设为1。

    Batch Nomalization层：
    batch_normalization( x,mean,variance,offset,scale, variance_epsilon,name=None)

    mean 和 variance 通过 tf.nn.moments 来进行计算：
    batch_mean, batch_var = tf.nn.moments(x, axes = [0, 1, 2], keep_dims=True)，注意axes的输入。对于以feature map 为维度的全局归一化，若feature map 的shape 为[batch, height, width, depth]，则将axes赋值为[0, 1, 2]

    x 为输入的feature map 四维数据，offset、scale为一维Tensor数据，shape 等于 feature map 的深度depth。



安装
http://www.cnblogs.com/foxblogs/p/8179143.html

https://jizhi.im/blog/post/install-dl-env-03 安装 使用gpu深度学习


http://www.arduino.cn/thread-11266-1-1.html

$ sudo su  #打开管理员权限
$ apt-get install synaptic #安装新得立软件包管理器
搜索synaptic，打开并更新所有可升级的软件包（可能会很慢），下载好安装完成后重启。ubuntu右上角的error消失，sudo apt-get update没有错误出现，ROS的rqt包也能安装了。

http://blog.exbot.net/archives/2972

http://www.cnblogs.com/Duane/p/6776302.html

http://blog.topspeedsnail.com/archives/10116

http://blog.csdn.net/zhangrelay/article/details/78418393

https://developer.nvidia.com/cuda-downloads?target_os=Linux&target_arch=x86_64&target_distro=Ubuntu&target_version=1604&target_type=deblocal

http://www.tensorflownews.com/2017/09/02/tensorflow-gpu-install-ubuntu-16-04/

https://github.com/eric-wieser/masters-thesis/commit/1858a54f04b7b39ebddb86cfaeb25c79d48a8b68

https://github.com/weiliu620/weiliu620.github.io/blob/master/reinforcement_learning_robotics.md

https://www.w3cschool.cn/tensorflow_python/tensorflow_python-hilj28ym.html
