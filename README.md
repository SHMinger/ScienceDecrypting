

## Mac系统下~~科学文库~~加密PDF的破解

Time: 2023-04-21

Author: SHMinger

问题的提出：科学文库作为大牌原版PDF书籍的出版商，作为中文图书出版商出版的书籍享有较高的权威性和质量，但其对书籍PDF的加密且旗下的`CAJViewer`糟糕的设计和反人类的操作为大多数同学所诟病，因此找到了能成功破解该PDF的方法，并且保留了原始PDF文字复制、目录检索，保留了原始风味，可谓是居家必备之良方。

1.创建用于破解pdf环境的虚拟环境

```bash
conda create -n ScienceDecrypting python=3.9
pip3 install -U pip
pip3 install -r requirements.txt
```

[注] 在源文件的`requirements.txt`中没有指定pypdf的版本号，会导致后续软件冲突问题的,需添加指定版本`pypdf2 == 1.26.0`

2.使用方法

```bash
# Usage: python3 decrypt.py -i INPUT_FILE -o OUTPUT_FILE
python3 decrypt.py -i /Users/hushuming/Downloads/Document/深度学习（上）.pdf -o /Users/hushuming/Downloads/深度学习（上）.pdf
python3 decrypt.py -i /Users/hushuming/Downloads/Document/OpenCV\ 2计算机视觉编程手册.pdf -o /Users/hushuming/Downloads/OpenCV\ 2计算机视觉编程手册.pdf		# 空格‘’用反斜杠(\)转义
```

3.遇到的问题及相应的解决办法

（1）没有注意pypdf2的版本问题，出现以下报错：

```bash
PyPDF2.errors.DeprecationError: PdfFileWriter is deprecated and was removed in PyPDF2 3.0.0. Use PdfWriter instead.
```

将源文件`decrypt.py`中的`PdfFileWriter` --> `PdfWriter`, `PdfFileReader` --> `PdfReader`

进行以上操作会引出新的问题：

```bash
NotImplementedError: only Standard PDF encryption handler is available
```

即需要将将依赖软件包修改版本号`pypdf2 == 1.26.0`, 并将之前修改的参数改回，即能正常操作。

![image-20230421165044247](/Users/hushuming/Library/Application Support/typora-user-images/image-20230421165044247.png)

__reference__：

1. [ScienceDecrypting源码](https://github.com/skq1998/ScienceDecrypting)

2. [科学文库官网](https://book.sciencereading.cn/shop/main/Login/shopFrame.do)

3. [Python—遇到的问题，使用PyPDF2转化pdf时候遇到的各种问题。](https://blog.csdn.net/weixin_45195493/article/details/128545244)



