- 通常:
	- dir,help;两个函数
	- 数据与数据集
		- dataset
			- 每一个数据以及其标签
			- 一共多少数据
		- dataloder 提供不同的格式
- 自定义数据集
	- 继承:torch中dataset,image,os
	- __ init __  初始化对象
	- __ getitem __   重点::可以
	- __ len __ 取得总长度
- tensorboard以及transfor
	- ```cmd
	  tensorboard --logdir="dataloader"
	  ```
- transforms
	- ![图片](http://pic.yupoo.com/mumukehao/2e7dd719/748039c5.png)
	-
	- 输入
		- PIL Img.open()
	- 输出
		- tensor  Totensor
	- 作用
		- naddary cv.imread
	- 如何使用transform  #重点复习
		- 关注输入和输出
		- 多看官方文档
		- 关注方法需要什么参数
			- args
		- 不知道输出什么类型
			- print
			- print(type)
			- debug 重点中重点
			-
- torchvision  常用的  注意:其中有常用的数据集
	- ```python
	  train_set=torchvision.datasets.CIFAR10(root="./dataset",train=True,transform=dataset_transform,download=True)
	  ```
	- 常用方法:transform.compose
		- ```python
		  dataset_transform=torchvision.transforms.Compose([torchvision.transforms.ToTensor()])
		  ```
- dataloader
	- ```python
	  test_loader = DataLoader(dataset=test_data,batch_size=4,shuffle=True,num_workers=0,drop_last=False)#drop_last是否删掉最后一栏
	  ```
-
- 常用神经网络工具:torch.nn
	- 骨架 containers
		- module 所有要进行的修改都要继承这个类
		- 最终要两个:
			- __init __继承
			- forward函数
	- convert 2d
		- 卷积操作实质
			- 控制横向或者纵向走,输入一个turple
			- 卷积核  #重点复习
				- ![卷积](http://pic.yupoo.com/mumukehao/287509f0/e4975fa4.png)
				- ```python
				  import torch.nn.functional as F
				  input=torch.reshape(input,(1,1,5,5))
				  kernel=torch.reshape(kernel,(1,1,3,3))
				  
				  output=F.conv2d(input,kernel,stride=1)
				  ```
			- 卷积padding=1
				- ![卷积](http://pic.yupoo.com/mumukehao/08d6887a/d634fd88.png)
		- 神经网络:卷积层
			- 卷积层 output=2       点乘求和
				- ![输出等于2](http://pic.yupoo.com/mumukehao/6df80710/81501b7c.png)
				- ```python
				  self.conv1=Conv2d(in_channels=3,out_channels=6,kernel_size=3,stride=1,padding=0)
				  ```
		- 神经网络:最大池化的使用   最大值函数
			- 作用:保持最大特征
			- ![最大池化](http://pic.yupoo.com/mumukehao/71065aeb/b3344ea3.png)
			  id:: 6475b965-b338-4a06-951b-0cd8ed9cf70c
			- maxpool2d  stride默认kernel
		- 神经网络:非线性激活
			- padding曾:进行填充
			- ![一个参数](http://pic.yupoo.com/mumukehao/a5f6dd97/935fc877.png)
		- 神经网络:线性层以及其它层介绍
			- 正则化层(用得少)
			- recurrent层常用语文字识别
			- transformers层
			- 线性层 linear
			- dropout layer
		- 神经网络:搭建小实战
			- sequence真的好用
			- CIFAR10model
				- ![CIFAR10MODEL](http://pic.yupoo.com/mumukehao/5fff979c/a5e875e6.png)
				- 第一步：计算padding
					- ![计算padding](http://pic.yupoo.com/mumukehao/66f8334c/55fbf4fe.png)
					-
				-
		- 损失函数和反向传播
			- 重点,处理分类问题            CROSSENTROPYLOSS
			- 损失函数的两个作用
				- 1.为实际输出和目标之间的差距
				- 2.为我们更新输出提供一定的依据 grad
					- 如何使用？优化器
					- 利用loss
					- optimizer
						- ```python
						  optimizer = optim.SGD(model.parameters(), lr=0.01, momentum=0.9)
						  ```
			- 梯度下降法：
				- 达到最优解
-