# 在图片中写入数据

## JPEG
JPEG 是 Joint Photographic Experts Group（联合图像专家小组）的缩写，是第一个国际图像压缩标准。JPEG图像压缩算法能够在提供良好的压缩性能的同时，具有比较好的重建质量，被广泛应用于图像、视频处理领域。JPEG是有损压缩，压缩后的数据在恢复时会丢失一部分不重要的信息。

## 标记码（TAG）
标记码由两个字节构成，前一个字节是固定字符 0xFF，后一个字节根据不同的意义有不同的数值。在每个标记码之前还可以添加数目不限的无意义 0xFF 填充，也可以理解为连续的多个 0xFF 为一个 0xFF，并表示一个标记码的开始。而在一个完整的两字节标记码之后，就是该标记码对应的压缩数据流，记录了关于文件的诸多信息。

 - SOI - Start Of Image ，图像开始，标记代码：0xFFD8。
 - APP0 - Application ，应用程序保留标记，标记代码：0xFFE0。
 - APPn - Application，应用程序保留标记n，其中 n = 1~15（任选），标记代码： 0xFFE1~0XFFEF。
 - DQT - Define Quantization Table，定义量化表，标记代码：0xFFDB。
 - SOFO - Start of Frame，帧图像开始，标记代码：0xFFC0。
 - DHT - Define Huffman Table，定义哈夫曼表，标记代码：0xFFC4。
 - DRI - Define Restart Interval，定义差分编码累计复位间隔，标记代码：0xFFDD。
 - SOS - Start of Scan，扫描开始12字节，标记代码：0xFFDA。
 - EOI - End of Image，图像结束，标记代码：0xFFD9。

## 写入数据到图片
熟悉了标记码后，我们可以按照格式拼接标记码结构，然后插入到图片中。

 - 将图片数据转为 byte[] 类型 imageByte。
 - 使用 App2 格式，以 0xFFE2 开头，然后拼接需要写入数据的 byte[] ，再以 0x00 结尾，组装好需要接入的数据 dataByte。
 - 将拼接的数据 dataBtye 插入 imageByte，在任意 tag 的结尾 EOI Tag 之前即可。