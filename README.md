## 这是50层的实现，网络结构见论文。

对于shortcut的方式，作者提出了三个选项：

A. 使用恒等映射，如果residual block的输入输出维度不一致，对增加的维度用0来填充；

B. 在block输入输出维度一致时使用恒等映射，不一致时使用线性投影以保证维度一致，即使用一个kernel_size=1的卷积层，让维度一致；

C. 对于所有的block均使用线性投影。

对这三个选项都进行了实验，发现虽然C的效果好于B的效果好于A的效果，但是差距很小，因此线性投影并不是必需的，而使用0填充时，可以保证模型的复杂度最低，这对于更深的网络是更加有利的。



# RestNet
[ResNet-50](http://ethereon.github.io/netscope/#/gist/db945b393d40bfa26006)  test Model 

[ResNet-101](http://ethereon.github.io/netscope/#/gist/b21e2aae116dc1ac7b50)  
[ResNet-152](http://ethereon.github.io/netscope/#/gist/d38f3e6091952b45198b)


        --input image--
         [256 256   3]
               ||
        [  1  64  64 256]
        [  1  32  32 512]
        [   1   16   16 1024]
        [   1    8    8 2048]
        [   1    2    2 2048]
