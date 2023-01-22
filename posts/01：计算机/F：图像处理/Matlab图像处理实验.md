# 实验一  **数字图像的基本认识**
## 代码说明：数字图像处理基本认识
~~~matlab
x=imread('w1.jpg');

%whos

%x

figure;imshow(x);

[c,r,p]=impixel(x); %指定完毕后单击右键

[c r p] %不加 ; 可以在命令行窗口显示指定像素的坐标

%% 2.基本图像类型

x1=rgb2gray(x); %将RGB图像转换为灰度图像

figure;imshow(x1);

[x2,map]=rgb2ind(x,256); %将RGB图像转换为索引图像

figure;imshow(x2,map);colormap(map);colorbar('horiz');colorbar('southoutside');

%colorbar 显示色阶的函数

x3=im2bw(x1); %将灰度图像转换为二值图像

figure;imshow(x3);

%% 3.图像的二维离散卷积

H=fspecial('unsharp',0.3); %产生模糊对比增强滤波器

H=double(H);

x1=double(x1);

x4=conv2(H,x1)/255;

figure;imshow(x4);title('图像的二维离散卷积');

%% 4.图像的灰度直方图

figure;

imhist(x1);
~~~

## 运行结果

![[Pasted image 20220416122758.png]]
## 函数说明
### rgb2ind
调用格式：

[X,map] = rgb2ind(RGB, n)

使用第二种算法把真彩色图像转换为索引图像，其中n指定map中颜色项数， n最大不能超过65536。

返回值中map即索引图像的调色板。
### colormap
文档介绍：https://ww2.mathworks.cn/help/matlab/ref/colormap.html
函数功能：查看并设置当前颜色图
` colormap(map)`将当前图窗的颜色图设置为 `map` 指定的颜色图。
### colorbar
文档介绍：https://ww2.mathworks.cn/help/matlab/ref/colorbar.html
函数功能：显示色阶的颜色栏
语法：colobar('location');
参数说明：location-相对于坐标区的未知：
|参数|表示位置|表示方向|

`'southoutside'`：坐标区的底部外侧，水平

绘制横着的colorbar：colorbar('horiz')


# 实验二 
## 代码分析
~~~ matlab
%%数字图像处理基本运算

%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%

%%1.点运算

%%调整图像的对比度

x=imread('w1.jpg');

figure('name','调整图像的对比度','NumberTitle','off','MenuBar','none');

subplot(1,3,1);imshow(x);title('调整前的图像');

a=input('a=? 请输入一个大于1的值 ');b=input('b=?');

x1=a*double(x)+b;

x1=uint8(x1);

subplot(1,3,2);imshow(x1);title('对比度增强');

c=input('c=? 请输入一个小于1的值 ');d=input('d=?');

x2=c*double(x)+d;

x2=uint8(x2);

subplot(1,3,3);imshow(x2);title('对比度减小');

%%输入不同的a与b的值，观察图像效果。例如a=1.2,b=0 c=0.7,d=0。

%% 2.代数运算

% 加法

x1=imread('w2.jpg');x2=imread('w3.png');

figure('name','图像的代数运算','NumberTitle','off','MenuBar','none');

subplot(1,3,1);imshow(x1);title('图像1');

subplot(1,3,2);imshow(x2);title('图像2');

a=input('a=? 请输入一个小于1的值 ');b=input('b=? 保证a+b=1 ');

x3=a*double(x1)+b*double(x2);

x3=uint8(x3);

subplot(1,3,3);imshow(x3);title('合成后的图像');

%% 图像的梯度幅度

x=imread('w1.jpg');

x=rgb2gray(x);

figure('name','图像的梯度幅度','NumberTitle','off','MenuBar','none');

% subplot(1,2,1);

imshow(x);title('原始图像');

s=size(x);

x1=diff(double(x));

x1=abs(x1);

x1(s(1),:)=0;

x2=diff(double(x'));

x2=abs(x2');

x2(:,s(2))=0;

fmax=max(x1,x2);

fmax=uint8(255-fmax);%反相显示

% subplot(1,2,2);

figure,

imshow(fmax);title('梯度图像');

%% 3.几何运算

%% 空间变换——旋转任意角度

angle=input('请输入要旋转的角度: ');

x=imread('w1.jpg');

x1=imrotate(x,angle,'bilinear','crop'); %双线性插值

figure('name','空间变换——旋转任意角度','NumberTitle','off','MenuBar','none');

subplot(1,2,1);imshow(x);title('原图像');

subplot(1,2,2);imshow(x1);title('旋转后的图像');

%% 几何变换——图像剪裁

x=imread('w1.jpg');

a=input('a=? ');b=input('b=? ');c=input('c=? ');d=input('d=?');

rect=[a b c d];

x1=imcrop(x,rect);

figure('name','空间变换——图像剪裁','NumberTitle','off','MenuBar','none');

subplot(1,2,1);imshow(x);title('原图像');

subplot(1,2,2);imshow(x1);title('剪裁出的图像');
~~~


# 实验三
~~~ matlab

%%图像变换

%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%

%% 1.二维FFT程序，考察一幅图像的频谱分布

%%请观察傅立叶变换的移位不变性。

x=imread('w1.jpg');x=rgb2gray(x);

figure('name','一幅图像的频谱分布','NumberTitle','off','MenuBar','none');

subplot(2,2,1);imshow(x);title('调整前的图像');

x1=fft2(double(x));

x1=fftshift(x1);

k=max(max(log(1+abs(x1))));

c=255/k;

xd=c*log(1+abs(x1));

subplot(2,2,2);imshow(uint8(xd));title('二维幅值谱');

%%%%%%%%%%%%%%%%%%%%%%%%%%%%

ang=input('请输入图像旋转的角度，数值建议为90 180 270 ');

xf=imrotate(x,ang,'bilinear');

x2=fft2(xf);

x2=fftshift(x2);

k=max(max(log(1+abs(x2))));

c=255/k;

xd1=c*log(1+abs(x2));

%%%%%%%%%%%%%%%%%%%%%%%%%%%%

subplot(2,2,3);imshow(xf);title('旋转的图像');

subplot(2,2,4);imshow(uint8(xd1));title('图像旋转后的幅值谱');

%%一幅图像的傅立叶变换

x=imread('w1.jpg');x=rgb2gray(x);

figure('name','一幅图像的傅立叶变换','NumberTitle','off','MenuBar','none');

subplot(3,3,1);imshow(x);title('原图像');

F=fft2(double(x));

F1=abs(F);

high=max(max(F1));

low=min(min(F1));

F1=(F1-low)./(high-low)*255;

F2=angle(F);F3=real(F);F4=imag(F);F5=fftshift(F1);

%%%%%%%%%%%%%%%%%%%%%%%%%%%%

x2=ifft2(F1);

high=max(max(x2));

low=min(min(x2));

x2=(x2-low)./(high-low)*255;

%%%%%%%%%%%%%%%%%%%%%%%%%%%%

x3=ifft2(F2);

high=max(max(x3));

low=min(min(x3));

x3=(x3-low)./(high-low)*255;

subplot(3,3,2);imshow(F);title('图像的傅立叶变换');

subplot(3,3,3);imshow(F1);title('图像的幅值谱');

subplot(3,3,4);imshow(F2);title('图像的相位谱');

subplot(3,3,5);imshow(F3);title('变换的实部');

subplot(3,3,6);imshow(F4);title('变换的虚部');

subplot(3,3,7);imshow(F5);title('零频移到频谱中心');

subplot(3,3,8);imshow(x2);title('由幅值谱重构的图像');

subplot(3,3,9);imshow(x3);title('由相位谱重构的图像');

%% 2.离散余弦变换

x=imread('w1.jpg');

x=rgb2gray(x);

x1=dct2(x);

figure('name','离散余弦变换','NumberTitle','off','MenuBar','none');

x1(abs(x1)<20)=0;%将DCT系数矩阵中小于20的值置为"0".

x2=idct2(x1)/255;

subplot(1,3,1);imshow(x);title('原图像');

subplot(1,3,2);imshow(log(abs(x1+eps)),[]);colormap(jet(64)),colorbar,title('对数图');

subplot(1,3,3);imshow(x2);title('重构的图像');

%% 3.离散K-L变换

x=imread('w1.jpg');

x=rgb2gray(x);

x=double(x);

x(106:140,:)=[];%将原始图像转变为方阵

xm=cov(x);%计算x的协方差矩阵

[v,d]=eig(xm);

d=max(d);

[d,i]=sort(d,2);

xm(:,i);

xm=fliplr(xm);%矩阵左右翻转

y=xm'*x;

ym1=y(:,1:50);

high=max(max(ym1));

low=min(min(ym1));

ym1=(ym1-low)./(high-low)*255;

ym2=y(:,1:100);

high=max(max(ym2));

low=min(min(ym2));

ym2=(ym2-low)./(high-low)*255;

high=max(max(y));

low=min(min(y));

y=(y-low)./(high-low)*255;

figure('name','一幅图像的离散K-L变换','NumberTitle','off','MenuBar','none');

subplot(2,2,1);imshow(uint8(x));title('原图像');

subplot(2,2,2);imshow(uint8(ym1));title('图像的离散K-L变换(50个分量)');

subplot(2,2,3);imshow(uint8(ym2));title('图像的离散K-L变换(100个分量)');

subplot(2,2,4);imshow(uint8(y));title('图像的离散K-L变换');
~~~