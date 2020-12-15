# Noise-patch-for-RISR
# 测试TestSet的PSNR, SSIM, LPIPS，并按照最终数值划分出较好的图片。

## 说明：

**输入数据集：**

**①真实图像 ②Ours的测试图像 ③对比方法的测试图像**

**输出结果：**

**①真实图像与Ours的PSNR, SSIM, LPIPS三个数值 ②真实图像与对比方法的PSNR, SSIM, LPIPS三个数值**
**③真实图像patch与Ours patchs的PSNR, SSIM, LPIPS三个数值**
**④真实图像patch与对比方法patch的PSNR, SSIM, LPIPS三个数值**
**⑤Ours相比对比方法三个数值都要好的原图片及图片patch，分别保存为六个文件夹（真实图像、真实图像patch、Ours、Ours patch、对比方法、对比方法patch）并记录数据。**

## 运行步骤

1.首先运行extract_subimages.py，把三个输入数据集分别crop成patch，如下图
![image-20201214203420694](https://gitee.com/house_lee/PicGo/raw/master/20201214203427.png)

2.分别运行calculate_PSNR_SSIM.py得到①②③④的结果。

![image-20201214203745338](https://gitee.com/house_lee/PicGo/raw/master/20201214203745.png)

3.根据2中结果，选出Ours比对比方法好的数据（可以用python shutil包写一个脚本，当PSNR_1>PSNR_2 &&  LPIPS1<LPIPS2时(或者按照2中结果的平均值设个阈值比较)，把其中数据分别放入⑤中所述的六个文件夹），并记录相关数据，如下图（用Excel简单记录不用图片也可以）。（其中PSNR、SSIM越高越好，LPIPS越低越好）

![image-20201214204357902](https://gitee.com/house_lee/PicGo/raw/master/20201214204358.png)

4.根据3中结果继续筛选出肉眼看起来比较明显区别的patch图片，如上图，再保存为相应文件夹。
