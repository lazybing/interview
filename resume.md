# 个人信息
- 李冰/男/1989/
- 硕士/沈阳航空航天大学
- 电话：**15715650340**
- 邮箱：**libinglimit@gmail.com**

- 技术博客：[http://lazybing.github.io](http://lazybing.github.io/)
- Github：[https://github.com/lazybing](https://github.com/lazybing/)

# 职业技能
- 熟练掌握C/C++语言开发，了解汇编、shell语言。
- 熟悉 Linux 环境下工作，熟练掌握 Linux 下的 GDB、Valgrind 等调试方法。
- **熟悉 H.264/HEVC/AV1 编码标准规范，运动补偿、码率控制、滤波等算法**，**熟悉 HEVC 硬件解码、X264 软件编码、AV1 软解**。
- 了解 FFMpeg 官方源码，并基于源码进行二次开发。
- 了解 FLV、MP4 等封装格式规范。

# 工作经历

## 工作经历(一)
- 视龙软件/2018.01-至今/Codec 组负责人

### 项目一：窄带高清转码


### 项目二：AV1 解码器 DAV1D 优化

1. 为 Netflix 优化 AV1(DAV1D) 10bit 视频解码库。
2. 对 AOM 工程，优化 AV1 的解码效率，使用 **NEON** 汇编，完成 **Film Grain** 和 **CDEF Filter** 部分的优化。
3. 调研并移植 DAV1D 解码器到 ARM 平台，优化 **Loop FIlter、Loop Restoration、MC、Intra** 等模块，**解码效率提升 150%-200%**。

### 项目三：音频解码器移植开发

1. 为现代汽车 Mobis 开发音频 Codec 解码器，为其提供解码库。
2. 独立完成移植 OPUS、TTA、AAC-ELD、ALS 等音频解码库的开发。
3. 去开源话，将 FFMpeg 中各个音频库提取、去开源话。
4. 解决客户提出的 bug，使得项目顺利完成。

## 工作经历(二)
- 澜至电子/2017.06-1017.12/视频固件工程师(SOC-HW 部分)

### 项目：VDEC IP （机顶盒 IC）验证

1. 负责机顶盒新 IC 中 VDEC 模块的验证工作。
2. 完善验证流程，使效率大幅提升，验证**时间缩短至少 50% 以上**。
3. 完成 VDEC 中的 Firmvare 部分，与 VDEC Driver 交互部分。

## 工作经历(三)
- MTK联发科/2015.04-2017.04/多媒体软件高级工程师(DTV 部门)

工作内容：

# 技术文章
* [FFMpeg 实现视频编解码、封装解封装、转码、缩放](http://lazybing.github.io/blog/2017/01/01/ffmpeg-sdk-learning/)
* [AV1(DAV1D)解码器概述](http://lazybing.github.io/blog/2018/10/15/av1-startup/)
* [AV1(DAV1D)解码算法之CDEF](http://lazybing.github.io/blog/2019/01/28/av1-cdef-filter/)
* [H264 Motion Estimation Algorithm](http://lazybing.github.io/blog/2021/05/17/h264-motion-estimation-algorithm/)
