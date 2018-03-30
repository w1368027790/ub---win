# ub---win
http://opencv-python-tutroals.readthedocs.io/en/latest/py_tutorials/py_imgproc/py_houghlines/py_houghlines.html


opencv 的H范围是0~180，红色的H范围大概是(0~8)∪(160,180) 
S是饱和度，一般是大于一个值,S过低就是灰色（参考值S>80)，0-255
V是亮度，过低就是黑色，过高就是白色(参考值220>V>50)。0-255




http://mp.weixin.qq.com/s/KGchk6IK6G9plp9I7miAqQ

暂时保存： https://wenku.baidu.com/view/112149386fdb6f1aff00bed5b9f3f90f76c64d6c.html
	https://danijar.com/materials/


tensorflow基础全： http://blog.csdn.net/lenbow
        配套目录： http://blog.sina.com.cn/s/blog_53dd83fd0102x37w.html
	构建： https://danijar.com/structuring-your-tensorflow-models/
rnn： http://wiki.jikexueyuan.com/project/tensorflow-zh/tutorials/recurrent.html
     http://blog.csdn.net/mydear_11000/article/details/52414342
     http://m-4.me/tensorflow-rnn-apis/
 
 TF图层指南：构建卷积神经网络 ： http://blog.csdn.net/u010859707/article/details/73201328

.eval（） ：eval() 函数用来执行一个字符串表达式，并返回表达式的值。还可以将字符串对应的名字的变量转换成该变量对应的值：

pytorch: http://pytorch.apachecn.org/cn/0.3.0/

opencv: https://docs.opencv.org/3.4.0/index.html    http://blog.csdn.net/column/details/opencv-tutorial.html

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
    
    
运动目标检测跟踪： http://blog.csdn.net/carson2005/article/details/7229797
               https://www.cnblogs.com/zjb0823/p/3806333.html
	       https://www.zhihu.com/question/26493945
 单目视觉的运动目标跟踪定位 硬创公开课
