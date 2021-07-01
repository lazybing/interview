# 音视频经典总结

## 经典书籍
[Recent Advances on Video Coding](https://www.intechopen.com/books/recent-advances-on-video-coding)

##  经典文章
[视频编码优化之道](https://cloud.tencent.com/developer/article/1167022)  
[阿里云窄带高清的演进与思考](https://zhuanlan.zhihu.com/p/366605123)  
[Video Codec Testing and Quality Measurement](https://tools.ietf.org/id/draft-ietf-netvc-testing-06.html)  

## Beamer
[optimizing-bitrates-for-user-generated-videos-with-beamr-cabr](https://blog.beamr.com/2020/07/12/optimizing-bitrates-for-user-generated-videos-with-beamr-cabr/)  
[The Patented Visual Quality Measure that was Designed to Drive Higher Compression Efficiency](https://blog.beamr.com/2019/09/11/visual-quality-measure/)  
[A Deep Dive into CABR, Beamr’s Content-Adaptive Rate Control](https://blog.beamr.com/2019/09/11/cabr-content-adaptive-rate-control/)

## Netflix
[Per-Title Encode Optimization](https://netflixtechblog.com/per-title-encode-optimization-7e99442b62a2)  
[More Efficient Mobile Encodes for Netflix Downloads](https://netflixtechblog.com/more-efficient-mobile-encodes-for-netflix-downloads-625d7b082909)  
[Dynamic optimizer — a perceptual video encoding optimization framework](https://netflixtechblog.com/dynamic-optimizer-a-perceptual-video-encoding-optimization-framework-e19f1e3a277f)  
[Optimized shot-based encodes:Now Streaming!](https://netflixtechblog.com/optimized-shot-based-encodes-now-streaming-4b9464204830)  
[Toward a Better Quality Metric for the Video Community](https://netflixtechblog.com/toward-a-better-quality-metric-for-the-video-community-7ed94e752a30)  

## BitMovin
[Cloud-based Per-Title Encoding Workflows (with AWS) – Part 1: Establishing the Architecture](https://bitmovin.com/cloud-based-per-title-encoding-aws-p1/)  
[Cloud-based Per-Title Encoding Workflows (with AWS) – Part 2: Implementing the Encoding Workflow](https://bitmovin.com/cloud-based-per-title-encoding-aws-p2/)  

## BiliBili
[哔哩哔哩点播码率优化实践](https://www.livevideostack.cn/news/bilibili-20200714/)

## Tencent
- [ ] 说一下 RDO。  
- [x] 问:x264 中各个 preset 的设置，有哪些不同点。  
> 答：不同的 preset 设置，导致的结果就是编码速度提升和质量的下降。原因就是不同的 preset 对应的是不同的编码工具、以及程序中不同的代码条件。编码工具的不同，比如说快速搜索算法不同（DIA->HEX->UMH）、快速搜索的半径不同、参考帧的个数不同、亚像素运动估计的质量不同、块分析/块划分的方式不同、码率控制算法不同（是否使用 MB-Tree）、是否使用自适应 B 帧判定。
- [ ] 简述一下编码器的基本架构。  
- [x] 问:说一下 X264 和 OPEN264 的异同，说一下 x264 为什么更好一些。  
> 答：x264 在码率控制上做的更好一些，不会出现码率压不下来，就掉帧的现象。有 10 种 preset 和 7 种 profile，支持不同的 Level 级别。缺点：1. 对变帧率特性不友好；2. 不支持 SVC 工程(视频会议对网络丢包比较敏感，当编码丢失一帧时，对整个 GOP 的解码都会有影响)。
> 
> 变帧率和SVC在openh264上都有实现。码控质量较差：1、运动和静止场景码率波动非常大；2、当画面运动复杂，码率压不下来，openh264会通过掉帧方式，压低码率。但是这样下来，视频流畅性就不那么完美。
- [x] 问：VMAF 受 filter 的影响比较大，怎么看待。  
> 答：VMAF 的特性决定了其能够预测一些图像增强处理对主观质量的提升。这是 VMAF 与 PSNR 和 SSIM 等传统工具的一大区别。但当过度使用一些图像增强效果的时候(比如过度锐化)，主观质量反而会降低，但 VMAF 的值会继续提高。也就是说，在过度增强的情况下，VMAF 并不能真实反映主观图像质量。在VMAF的两个主要feature也就是VIF和DLM里，引入了两个参数，来限制图像增强能够对VMAF产生影响的上限。具体来讲，引入的参数是vif_enhn_gain_limit和adm_enhn_gain_limit。当它们的值设置为很大的时候（比如都为100)，则对VMAF的值没有影响。而当它们的值都为1的话，则能最大限制图像增强对VMAF的值的提升。而当设置一些适当值（比如稍大于1）的话，则可以一定程度地引入图像增强的提升但又不会过度。具体什么为适当值的问题，我们留到后续版本的VMAF模型里来解决。
> 
> 目前引入这两个参数的主要目的是解决VMAF在编解码器测评使用场景下的问题。对于编解码器的测评来讲，希望测试到的是同等质量前提下的压缩性能，而不希望图像增强对比较的结果造成影响。这样的使用场景下，最好的设置是最大限制图像增强对VMAF的值的提升，也就是使用两个参数都设置为1的情况。
> 总结一下，新引入的两个参数能够让用户对图像增强对VMAF的结果造成的影响自定义化。各位可以根据自己的应用场景设置合适的参数。在后续版本的VMAF中，我们会提供这两个参数的标准值。  
> 
> v2.1.0 版本已经支持设置这个参数了。

- [ ] 问： 如何衡量一个编码器的好坏

