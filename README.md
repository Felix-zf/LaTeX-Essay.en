# LaTeX-Essay.EN
用于书写英文论文的模板，涵盖包括标题，摘要在内的全部部分，有注释进行检索。

***LaTeX 模板推荐***  

- 清华大学学位论文 LaTeX 模板：https://github.com/tuna/thuthesis
- 北京大学学位论文 LaTeX 模板：https://github.com/CasperVector/pkuthss
- 复旦大学学位论文 LaTeX 模板：https://github.com/stone-zeng/fduthesis
- 上海交大学位论文 LaTeX 模板：https://github.com/sjtug/SJTUThesis?tab=readme-ov-file
- 浙江大学学位论文 LaTeX 模板：https://github.com/TheNetAdmin/zjuthesis
- 南京大学学位论文 LaTeX 模板：https://github.com/nju-lug/njuthesis
- 北京理工学位论文 LaTeX 模板：https://github.com/BITNP/BIThesis
- 武汉大学学位论文 LaTeX 模板：https://github.com/whutug/whu-thesis
- 华中科大学位论文 LaTeX 模板：https://github.com/XinzeZhang/HUST-PhD-Thesis-Latex
- 中山大学学位论文 LaTeX 模板：https://github.com/SYSU-SCC/sysu-thesis
- 华南理工学位论文 LaTeX 模板：https://github.com/mengchaoheng/SCUT_thesis
- 深圳大学学位论文 LaTeX 模板：https://github.com/jonzhaocn/szu-thesis-master
- 广东工业学位论文 LaTeX 模板：https://github.com/sikouhjw/gdutthesis
- 《数学杂志》(Journal of Mathematics) LaTeX 模板：https://github.com/xkwxdyy/J_Jmath

### PRB期刊的LaTeX模板
- 我们首先用百度进入PRB官网，如下图所示，进入蓝框选中的【Authors】界面，会进入到【Information for Authors】界面，这个界面就是为作者服务，里面会有很多投稿须知之类的内容。
- 【Information for Authors】界面就包含了从投稿到结受，投稿要求，版面要求等一大堆内容，基本上就是投稿者的说明书了。我们往下翻就可以找到文章长度、摘要Abstructs、以及支撑材料Supplemental Material的要求。对于Table和Figure的大小与编号也有一定的要求，都可以在这个页面中找到。
- 往下找，可以看到这一点给出了所用模板文件。第一个蓝色链接REVTeX 4导向了PR系列对REVTeX的一个简介，里面说明了一些要点，比如：
1. REVTeX 4.2是一组旨在与LaTeX2e一起使用的宏程序包，非常适合准备稿件以提交给美国物理学会（APS）和美国物理研究所（AIP）的期刊。
2. 使用TeX向APS，AIPP，AAPM或SOR期刊投稿的作者应使用REVTeX 4.2。正确使用REVTeX提供的命令可以极大地帮助同行评审和发布过程，从而减少引入错误的机会。以及REVTeX的官方文档与下载地址等。
前往[REVTEX](https://journals.aps.org/revtex)下载页面。

### REVTeX 4的APS模板使用教程
下载好安装包以后，进入到`doc/latex/revtex/sample/aapm/aapmsamp.tex`这个文件夹中，用TeXStudio打开里面的apstemplate.tex文件，这就是模板文件，写论文的话直接复制一下这个文件即可。

而教程则是apssamp.tex文件，对应的生成结果为apssamp.pdf文件。里面包含了各种作者、标注的方法与示例，单栏图表与双栏图表的例子，单栏公式与双栏公式的例子等，基本上在写论文中的所有操作技巧与难点都在这里举有例子。
下面我们将选取几个比较常见的、普通的例子。

**模板的基础——一堆宏包的引用**

在apstemplate中，开头只有一行
```
\documentclass[aps,prl,preprint,groupedaddress]{revtex4-2}
```
这就是声明我使用的是rextex4-2模板。有的版本的texlive中还没有包含进revtex4-2，所以我们将revtex4-2改写为revtex4-1也是照常可以编译的。但是需要注意的是，在向期刊提交稿件时最好还是用4-2。

剩余的宏包则根据自己的需要逐个增加。我个人所引用的宏包如下列所示：
```
\documentclass[aps,amsmath,amssymb,reprint]{revtex4-1}

\usepackage{graphicx}% Include figure files
\usepackage{dcolumn}% Align table columns on decimal point
\usepackage{bm}% bold math

\usepackage[utf8]{inputenc}
\usepackage[T1]{fontenc}
\usepackage{booktabs, array, mathptmx, float, tabularx, booktabs, lipsum, amsmath,multirow}
\usepackage{siunitx, xcolor}
\usepackage[version=4]{mhchem}
\graphicspath{{figs/}{figsgaoerb/}} % 读取图片从figs/文件夹中读取，而不是当前文件夹
\usepackage[colorlinks,linkcolor=blue,anchorcolor=blue,citecolor=blue]{hyperref}
```
基本上这一串包含了很多内容，有什么则可以自己再往里面添加。

**单栏表格与双栏表格**

期刊一般都是双栏，因此也就产生了单栏表格和双栏表格的区别。但是普通的LaTeX模板一般都是单栏，所以对于第一次接触的人来说这也是一个大问题,单栏的表格几乎没变
```
\begin{table}[b]
    \centering
    \caption{This is a table caption.}
    \begin{ruledtabular}
    \begin{tabular}{ccc}
        & Variable1 & Variable2 \\
        \colrule
        Subject1 & 0.01 & 123 \\
        Subject2 & 0.25 & 321 \\
    \end{tabular}
    \end{ruledtabular}
\end{table}
```
双栏的表格与单栏的唯一的不同之处在于table环境变成了table*，如
```
\begin{table*}[b]
    \centering
    \caption{This is a table caption.}
    \begin{ruledtabular}
    \begin{tabular}{ccc}
        & Variable1 & Variable2 \\
        \colrule
        Subject1 & 0.01 & 123 \\
        Subject2 & 0.25 & 321 \\
    \end{tabular}
    \end{ruledtabular}
\end{table*}
```

**单栏公式与双栏公式**

单栏公式就是平常用的equation与align的等环境不需要改变，双栏公式则是在外面套了一个widetext环境，如
```
% 单栏公式/普通公式
\begin{equation}
    F = G\dfrac{Mm}{r^2}
\end{equation}
% 双栏公式
\begin{widetext}
\begin{equation}
    F = G\dfrac{Mm}{r^2}
\end{equation}
\end{widetext}
```

**参考文献引用**

在当前文件夹下建立一个bib文件，如references.bib，里面粘贴上从各个期刊网页下载下来的Bib Tex格式的参考文献引用格式。其中一条例子为：
```
@article{2017-NCM-intro,    % 引用时用于cite的名字
title = "Thermoelectric generators: A review of applications",
journal = "Energy Conversion and Management",
volume = "140",
pages = "167 - 181",
year = "2017",
issn = "0196-8904",
doi = "https://doi.org/10.1016/j.enconman.2017.02.070",
url = "http://www.sciencedirect.com/science/article/pii/S0196890417301851",
author = "Daniel Champier",
keywords = "Thermoelectric generators, Review, Thermoelectricity, TEG, Thermoelectric modules, Application"
}
```
然后在正文中，我们可以按照下方的例子来引用
```
Thermoelectric devices can direct convert thermal energy to electrical energy. \cite{2017-NCM-intro}
```
