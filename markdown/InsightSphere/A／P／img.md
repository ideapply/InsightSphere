- > 图片压缩算法
- 前期资料收集
    - [JPEG凭什么称霸互联网 30 多年？你大爷永远是你大爷！【柴知道】_哔哩哔哩_bilibili](https://www.bilibili.com/video/BV1H2421F7sg/)
    - [JPEG - 维基百科，自由的百科全书](https://zh.wikipedia.org/zh-cn/JPEG)
    - [YUV - 维基百科，自由的百科全书](https://zh.wikipedia.org/wiki/YUV)
        - **YCbCr**不是一种[绝对色彩空间](https://zh.wikipedia.org/wiki/%E7%B5%95%E5%B0%8D%E8%89%B2%E5%BD%A9%E7%A9%BA%E9%96%93)，是[YUV](https://zh.wikipedia.org/wiki/YUV)压缩和偏移的版本。YCbCr的Y与YUV中的Y含义一致，Cb和Cr与UV同样都指色彩，Cb指蓝色色度，Cr指红色色度。
- ## 基于人眼敏感度的图片压缩算法 - JPEG
    - **JPEG**或称**JPG**，是一种针对照片影像而广泛使用的[有损压缩](https://zh.wikipedia.org/wiki/%E6%9C%89%E6%8D%9F%E6%95%B0%E6%8D%AE%E5%8E%8B%E7%BC%A9)标准方法，由**联合图像专家小组**（英语：**J**oint **P**hotographic **E**xperts **G**roup）开发。此团队创立于1986年，1992年发布了JPEG的标准而在1994年获得了ISO 10918-1的认定。
    - ### 颜色/亮度感知
        - 人眼对亮度变化的感知要比对色彩变化敏感的多。因为人眼中感受亮度的视杆细胞（1.25亿）要比感受色彩的视锥细胞（600～700万）要多得多。因此，可以将原先的RGB色彩编码转换成基于亮度和色彩的[YCbCr编码](((fzGmRBAHB)))。
        - $$\begin{aligned}
\rm{Y} &= 0.299R + 0.587G + 0.114B \\
\rm{Cb} &= -0.1687R - 0.3313G + 0.5B + 128 \\
\rm{Cr} &= 0.5R - 0.4187G - 0.0813B + 128
\end{aligned}
$$
        - ![](https://firebasestorage.googleapis.com/v0/b/firescript-577a2.appspot.com/o/imgs%2Fapp%2FInsightSphere%2Fg8FpxTOigd.png?alt=media&token=57933659-2e94-4a52-9138-010c0d1f5160)
#.flex-row
            - ![](https://firebasestorage.googleapis.com/v0/b/firescript-577a2.appspot.com/o/imgs%2Fapp%2FInsightSphere%2F9zRk0LqPF0.png?alt=media&token=392ea898-bb00-42a3-b975-5e4b0b33cf88)
        - 压缩时对亮度Y不动，对颜色Cb、Cr进行四合一压缩。
    - ### 低/高频信号感知
        - 人眼擅长感受低频信号，却不擅长感受高频信号。低频信号（LFS）指像素之间变化比较平缓的信号，高频信号（HFS）指像素之间变化比较剧烈的线条。
        - 首先，利用二维DCT频域变换使颜色/亮度信号转换成正弦信号的叠加。
        - ![](https://firebasestorage.googleapis.com/v0/b/firescript-577a2.appspot.com/o/imgs%2Fapp%2FInsightSphere%2F1tI_kPbq0O.png?alt=media&token=4e11e268-c991-4205-ad0f-4e85c339248d)
#.flex-row
            - ![](https://firebasestorage.googleapis.com/v0/b/firescript-577a2.appspot.com/o/imgs%2Fapp%2FInsightSphere%2F9Cz1TYHO76.png?alt=media&token=ba4116fe-db28-4632-a0b5-7a4f43a53903)
        - 然后对其中视觉不太敏感，且数值较小的高频信号进行压缩。
        - ![](https://firebasestorage.googleapis.com/v0/b/firescript-577a2.appspot.com/o/imgs%2Fapp%2FInsightSphere%2FBHjBfHWbku.png?alt=media&token=e292d52a-d82c-40a9-9cb1-feb11a4d74c1)
#.flex-row
            - ![](https://firebasestorage.googleapis.com/v0/b/firescript-577a2.appspot.com/o/imgs%2Fapp%2FInsightSphere%2FDhoMLhmkf5.png?alt=media&token=ea5866a0-62b9-475f-bafb-f365032706af)
        - 根据画面质量需求，将压缩后的图片信息进行熵编码，并存储。以上便是JPEG图片压缩算法的基本逻辑。
        - ![](https://firebasestorage.googleapis.com/v0/b/firescript-577a2.appspot.com/o/imgs%2Fapp%2FInsightSphere%2F10p2ZrFbqq.png?alt=media&token=d02e2840-ea62-45e5-bd66-fcf16d9e81e2)
