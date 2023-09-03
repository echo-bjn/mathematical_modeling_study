# Latex学习

## 一、LaTeX中文处理方法

1.设置TeXstudio：XeLaTeX编译器(速度快且支持中文)+UTF-8编码

2.引入宏包ctex

```tex
\usepackage{ctex}
```

## 二、LaTeX源文件的基本结构(包含数学公式、字体字号)

```tex
%导言区(全局设置)
\documentclass[10pt]{article} %{article}设置article,book,report,letter等文档类,[10pt]设置normalsize等级的字体大小为10pt(一般只有10-12pt)

\usepackage{ctex} %解决输出中文问题

\newcommand{\degree}{^\circ} %\newcommand定义新命令\degree

\title{\heiti My First Document} %\heiti可以设置字体
\author{\kaishu BJN} 
\date{\today}


%正文区(文稿区)
\begin{document} %document(环境名称)
	\maketitle %在正文中输出标题
	
	 %内容:下面空一行或者\par表示生成的文件对应换行，"\\"只换行不空两格
	Hello World! \par 很多机构和研究公司...
	
	%1.数学公式
	%[1]$...$(单$模式：行内公式)和$$...$$(双$模式：行间未编号公式)内包含的成为数学模式，外面的是文本模式	
	(1)Let $f(x)$ be defined by the formula
	$f(x)=3x^2+x-1$.  
	(2)Let $g(x)$ be defined by the formula
	$$g(x)=3x^2+x-1$$.
	
	%[2]\begin{equation}和\end{equation}(行间编号公式)
	(3)Let $g(x)$ be defined by the formula
	\begin{equation}
		g(x)=3x^2+x-1.
	\end{equation}


	%2.字体字号，其中{}可以设置限定字体的适用范围
	%[1]字体族设置(两种方法)(罗马字体、无衬线字体、打字机字体)
	\textrm{Roman Family}%罗马字体 
	\textsf{Sans Serif Family}%无衬线字体 
	\texttt{Typewriter Family}%打字机字体
	
	{\rmfamily Roman Family}%罗马字体 
	{\sffamily Sans Serif Family}%无衬线字体 
	{\ttfamily Typewriter Family}%打字机字体
	
	%[2]字体系列设置(两种方法)(粗细、宽度)
	\textmd{Medium Series}%粗细
	\textbf{Boldface Series}%宽度(粗体)
	
	{\mdseries Medium Series}%粗细
	{\bfseries Boldface Series}%宽度(粗体)
	
	%[3]字体形状设置(两种方法)(直立、斜体、伪斜体、小型大写)
	\textup{Upright Shape}%直立
	\textit{Italic Shape}%斜体
	\textsl{Slanted Shape}%伪斜体
	\textsc{Small Caps Shape}%小型大写
	
	{\upshape Upright Shape}%直立
	{\itshape Italic Shape}%斜体
	{\slshape Slanted Shape}%伪斜体
	{\scshape Small Caps Shape}%小型大写
	
	%[4]中文字体
	{\songti 宋体}
	{\heiti 黑体}
	{\fangsong 仿宋}
	{\kaishu 楷书}
	
	%[5]字体大小
	{\tiny			Hello}
	{\scriptsize	Hello}
	{\footnotesize	Hello}
	{\small			Hello}
	{\normalsize	Hello}
	{\large			Hello}
	{\Large			Hello}
	{\LARGE			Hello}
	{\huge			Hello}
	{\Huge			Hello}
	
	%[6]中文字体大小(-0：小初号,5：五号,-5：小五号)
	\zihao{-0}	你好！
	\zihao{5}	你好！
	\zihao{-5}	你好！
	
	
\end{document} %document(环境名称)
```

## 三、LaTeX文档的基本结构(目录、小节、子小节、子子小节格式的设置)

```tex
%导言区
\documentclass{article}

\usepackage[UTF8,heading = true]{ctex}
%设置标题的格式
\ctexset{
	section={
		%format用于设置章节标题全局格式，作用域为标题和编号
		%字号为小四，字体为黑体，左对齐
		%+号表示在原有格式下附加格式命令
		format+=\zihao{-4} \heiti \raggedright,
		%name用于设置章节编号前后的词语
		%前、后词语用英文状态下,分开
		%如果没有前或后词语可以不填
		name={,、},
		%number用于设置章节编号数字输出格式
		%输出section编号为中文
		number=\chinese{section}
		%beforeskip用于设置章节标题前的垂直间距
		%ex为当前字号下字母x的高度
		%基础高度为1.0ex，可以伸展到1.2ex，也可以收缩到0.8ex
		beforeskip=1.0ex plus 0.2ex minus .2ex,
		%afterskip用于设置章节标题后的垂直间距
		afterskip=1.0ex plus 0.2ex minus .2ex,
		%aftername用于控制编号和标题之间的格式
		%\hspace用于增加水平间距
		aftername=\hspace{0pt}
	},
	subsection={
		format+=\zihao{5} \heiti \raggedright,
		name={(,)},
		%输出subsection编号为阿拉伯数字
		number=\arabic{subsection}
		beforeskip=1.0ex plus 0.2ex minus .2ex,
		afterskip=1.0ex plus 0.2ex minus .2ex,
		aftername=\hspace{opt}
	},
	subsubsection={
		%设置对齐方式为居中对齐
		format+=\zihao{-5} \fangsong \centering,
		%仅输出subsubsection编号，格式为阿拉伯数字，打字机字体
		number=\ttfamily\arabic{subsubsection},
		name={,.},
		beforeskip=1.0ex plus 0.2ex minus .2ex,
		afterskip=1.0ex plus 0.2ex minus .2ex,
		aftername=\hspace{0pt}
	}
}

%正文区
\begin{document}
	%\tableofcontents产生文档的目录
	%\chapter{}构建章节的大纲(book类才有)
	%\section{}构建小节
	%\subsection{}构建子小节
	%\subsubsection{}构建子子小节
	
	\tableofcontents
	
	%\chapter{绪论}
	\section{引言} 
	\section{实验方法}
	\section{实验结果}
	\subsection{数据}
	\subsection{图表}
	\subsubsection{实验条件}
	\subsubsection{实验过程}
	\section{结论}
	\section{致谢}
\end{document}
```

## 四、LaTeX中的特殊字符(空白符号、\LaTeX 控制符、排版符号、引号...)

```tex
%导言区
\documentclass{article}

\usepackage{ctex}

%正文区
\begin{document}
	\section{空白符号}
	%空行分段，多个空行等同一个
	%自动缩进，绝对不能使用空格代替
	%英文中多个空格处理为一个空格，中文中空格将被忽略
	%汉字与其它字符的间距会自动由XeLaTeX处理
	%禁止使用中文全角空格
	%a\quad b或a\ b产生一个空格，a\qquad b产生两个空格，a\,b或a\thinspace b产生1/6个空格，a\enspace b产生0.5个空格
	a\quad b  a\ b  a\qquad b  a\,b  a\thinspace b  a\enspace b
	
	\section{\LaTeX 控制符}
	%\textbackslash产生\
	\#  \$  \%  \{  \}  \~{}  \^{}  \textbackslash  \&
	
	\section{排版符号}
	\S  \P  \dag  \ddag  \copyright  \pounds
	
	\section{\TeX 标志符号}
	\TeX{}  \LaTeX{}  \LaTeXe{}
	
	\section{引号}
	%`左单引号，'右单引号,``左双引号,''右双引号
	`  '  ``  ''
	
	\section{连字符}
	%由短到长
	-  --  ---
	
	\section{非英文字符}
	\oe  \OE  \AA  ...
	
	\section{重音符号(以o为例)}
	\^o  \~o  \.o  ...
    
\end{document}
```

## 五、LaTeX中的插图和表格

### 5.1 LaTeX中的插图(**使用宏包graphicx**)

```tex
%导言区
\documentclass{article}

\usepackage{ctex}

%导言区\usepackage{graphicx}
%语法:\includegraphics[<选项>]{<文件名>}
%格式:EPS、PDF、PNG、JPEG、BMP
\usepackage{graphicx}
\graphicspath{{路径1}，{路径2}}%指定图片所在路径，例如study/figures/

%正文区
\begin{document}
	\LaTeX{}中的插图：
	\includegraphics{lion.jpg}
	\includegraphics{mountain.png}
	
	%scale指定缩放比例
	\includegraphics[scale=0.3]{lion.jpg}
	\includegraphics[scale=0.03]{mountain.png}
	
	%width指定图像宽度,\textwidth表示版心宽度，减去左右边距可以写字的部分的宽度
	\includegraphics[width=2cm]{lion.jpg}
	\includegraphics[width=2cm]{mountain.png}
	\includegraphics[width=0.1\textwidth]{lion.jpg}
	\includegraphics[width=0.1\textwidth]{mountain.png}
	
	%height指定图像高度,\textheight表示版心高度，减去上下边距可以写字的部分的高度
	\includegraphics[height=2cm]{lion.jpg}
	\includegraphics[height=2cm]{mountain.png}
	\includegraphics[height=0.2\textheight]{lion.jpg}
	\includegraphics[height=0.2\textheight]{mountain.png}
	
	%angle指定图像角度
	\includegraphics[angle=-45,height=0.2\textheight,0.1\textwidth]{lion.jpg}
\end{document}
```

### 5.2 LaTeX中的表格(使用\begin{tabular}和\end{tabular})

```tex
%导言区
\documentclass{article}

\usepackage{ctex}

%正文区
\begin{document}
	\LaTeX{}中的表格：
	%生成五列表格，分别是左对齐(l)，居中对齐(c)，右对齐(r)，也可以由p产生对应长度的列格式，例如将r换成p{1.5cm}，但超出长度会自动换行。
	%|产生表格竖线,两个|产生双竖线，\hline产生单横线，两个产生双横线
	%\\表示换行，&表示不同的列
	\begin{tabular}{|l||c|c|c|r|}
		\hline
		姓名 & 语文 & 数学 & 外语 & 备注 \\
		\hline \hline
		张三 & 87 & 100 & 93 & 优秀 \\
		\hline
		李四 & 75 & 64 & 52 &  补考另行通知 \\
		\hline
		王二 & 80 & 82 & 78 & 无 \\
		\hline
	\end{tabular}
\end{document}
```

### 5.3 LaTeX中的浮动体 (两大浮动体环境figure和table)

**LaTeX预定义了两大浮动体环境figure和table，动态排版以解决文章中大面积空白的问题**

```tex
%导言区
\documentclass{article}

\usepackage{ctex}
\usepackage{graphicx}
\graphicspath{{路径1}，{路径2}}%指定图片所在路径，例如study/figures/

%正文区
\begin{document}
    %浮动体
    %实现灵活分页(避免无法分割的内容产生的页面留白)
    %给图表添加标题
    %交叉引用
    
    %格式：
    %figure环境(table环境与之类似)
    %\begin{figure}[<允许位置>]
    %	<任意内容>
    %\end{figure}
    
    %<允许位置>参数(默认tbp)
    %h，此处(here)-代码所在的上下文位置
    %t，页顶(top)-代码所在页面或之后页面的顶部
    %b，页底(bottom)-代码所在页面或之后页面的底部
    %p，独立一页(page)-浮动页面
    
    %标题控制(caption、bicaption宏包)
    %并排与子图标(subcaption、subfig、floatrow等宏包)
    %绕排(picinpar、wrapfig等宏包)
    
    
	%插图：浮动体\begin{figure}和\end{figure}，\centering居中对齐
	\LaTeX{}中吉祥物小狮子见图\ref{fig-lion}：
	\begin{figure}
		\centering
		\includegraphics[scale=0.03]{mountain.png}
		%\caption{吉祥物小狮子}设置插图的标题,\label{fig-lion}设置标签，\ref{fig-lion}可以做到交叉引用
		\caption{吉祥物小狮子}\label{fig-lion} 
	\end{figure}
	
	
	%表格：浮动体\begin{table}和\end{table}，\centering居中对齐
	\LaTeX{}中考试成绩单见表\ref{tab-score}：
	\begin{table}
		\centering
		\caption{考试成绩单}\label{tab-score} %设置表格的标题
        \begin{tabular}{|l||c|c|c|r|}
            \hline
            姓名 & 语文 & 数学 & 外语 & 备注 \\
            \hline \hline
            张三 & 87 & 100 & 93 & 优秀 \\
            \hline
            李四 & 75 & 64 & 52 &  补考另行通知 \\
            \hline
            王二 & 80 & 82 & 78 & 无 \\
        \end{tabular}
	\end{table}
	
\end{document}
```

## 六、LaTeX数学公式

### 6.1 LaTeX数学公式初步

```tex
%导言区
\documentclass{article}

\usepackage{ctex}
\usepackage{amsmath}

%正文区
\begin{document}
	%自动编号
	%交叉引用

    \section{行内公式}  
    \subsection{美元符号}
    交换律是$a+b=b+a$，如$1+2=2+1=3$。
    
    \subsection{小括号}
    交换律是\(a+b=b+a\),如\(1+2=2+1=3\)。
    
    \subsection{math环境}
    交换律是\begin{math}a+b=b+a\end{math}，如\begin{math}1+2=2+1=3\end{math}
    
    
    \section{上下标}
    \subsection{上标} %"^"
    $3x^{20}-x+2=0$
    
    \subsection{下标} %"_"
    $a_0 a_1 a_2 a_{100}$
    
    
    \section{希腊字母}
    $\alpha$
    $\beta$
    $\gamma$
    $\epsilon$
    $\pi$
    $\omega$
    $\Gamma$
    $\Delta$
    $\Theta$
    $\Pi$
    $\Omega$
    $\alpha^3+\beta^2+\gamma=0$
    
    
    \section{数学函数}
    $\log$
    $\sin$
    $\cos$
    $\acrsin$
    $\ln$
    $\sin^2 x+\cos^2 x=1$
    $y=\sin^{-1}x$
    $\sqrt{2}$
    $\sqrt[4]{x}$ %4次根式
    
    
    \section{分式}
    大约是体积的$3/4$。
    大约是体积的$\frac{3}{4}$
    $\frac{\sqrt{x-1}}{\sqrt{x+1}}$
    $\sqrt{\frac{x}{x^2+x+1}}$
    
    
    \section{行间公式}
    \subsection{美元符号}
    交换律是
    $$a+b=b+a$$
    如
    $$1+2=2+1=3$$
    
    \subsection{中括号}
    交换律是
    \[a+b=b+a\]
    如
    \[1+2=2+1=3\]
    
    \subsection{displaymath环境}
    交换律是
    \begin{displaymath}a+b=b+a
    \end{displaymath}
    如
    \begin{displaymath}
    1+2=2+1=3
    \end{displaymath}
    
    \subsection{自动编号公式equation环境}
    交换律见式\ref{eq:commutative}
    \begin{equation}
    	a+b=b+a \label{eq:commutative}
    \end{equation}
    
    \subsection{不编号公式equation*环境}
    %此时交叉引用编号为小节编号
    交换律见式\ref{eq:commutative2}
    \begin{equation*}
    	a+b=b+a \label{eq:commutative2}
    \end{equation*}
\end{document}
```

### 6.2 LaTeX数学公式的矩阵(使用宏包amsmath)

```tex
%导言区
\documentclass{article}

\usepackage{ctex}
\usepackage{amsmath}

%正文区
\begin{document}
	%矩阵环境，用&分割列，用\\分割行
	%可以使用上下标
	$$
	%matrix环境
	\begin{matrix}
		0 & 1 \\
		1 & 0 
	\end{matrix}
	$$
	$$
	%pmatrix环境(在矩阵两端加小括号)
	\begin{pmatrix}
		0 & -i \\
		i & 0
	\end{pmatrix}
	$$
	$$
	%bmatrix环境(在矩阵两端加中括号)
	\begin{bmatrix}
		0 & -i \\
		i & 0
	\end{bmatrix} 
	$$
	$$
	%Bmatrix环境(在矩阵两端加大括号)
	\begin{Bmatrix}
		0 & -i \\
		i & 0
	\end{Bmatrix}
	$$
	$$
	%vmatrix环境(在矩阵两端加单竖线)
	\begin{vmatrix}
		0 & -i \\
		i & 0
	\end{vmatrix}
	$$
	$$
	%Vmatrix环境(在矩阵两端加双竖线)
	\begin{Vmatrix}
		0 & -i \\
		i & 0
	\end{Vmatrix}
	$$
	$$
	%常用省略号：\dots,\vdots,\ddots
	A=\begin{pmatrix}
		a_{11} & \dots & a_{1n} \\
		\ddots & \vdots \\
		0 & & a_{nn}
	\end{pmatrix}_{n \times n}
	$$
	$$
	%分块矩阵(矩阵嵌套),\text{}在数学模式中切换到文本模式
	\begin{pmatrix}
		\begin{matrix} 1&0\\0&1 \end{matrix}
		&\text{\Large 0} \\
		\text{\large 0} & \begin{matrix}
			1&0\\0&1 \end{matrix}
		\begin{matrix}\end{matrix}
	\end{pmatrix}
	$$
	$$
	%三角矩阵
	\begin{pmatrix}
		a_{11}  & a_{12} & \cdots & a_{1n} \\
		& a{22} & \cdots & a_{2n} \\
		&       & \cdots & \vdots \\
		\multicolumn{2}{c}{\raisebox{1.3ex}[0pt]{\Huge 0}}
		&       & a_{nn}
	\end{pmatrix}
	$$
	%行内小矩阵(smallmatrix)环境
	复数$z=(x,y)$也可用矩阵
	\begin{math}
		\left(
		\begin{smallmatrix}
			x & y \\
			y & x
		\end{smallmatrix}
		\right)
	\end{math}
\end{document}
```

### 6.3 LaTeX中的多行数学公式(使用宏包amsmath和amssymb)

```tex
%导言区
\documentclass{article}

\usepackage{ctex}
\usepackage{amsmath}
\usepackage{amssymb}

%正文区
\begin{document}
	%gather(带编号)和gather*环境(不带编号)(可以用\\换行)
	%gather环境中也可以在\\前使用\notag阻止编号
	\begin{gather}
		a+b=b+a \\
		ab ba \notag \\
		1+1=2
	\end{gather}
	
	\begin{gather*}
		a+b=b+a \\
		ab=ba
	\end{gather*}
	
	
	%align(带编号)和align*(不带编号)环境(用&进行对齐)
	\begin{align}
		x&=t&x&=\cos t&x&=t \\
		y=&2t&y=\sin(t+1)&y&=\sin t
	\end{align}
	
	\begin{align*}
		x&=t&x&=\cos t&x&=t \\
		y&=2t&y&=\sin(t+1)&y&=\sin t
	\end{align*}
	
	
	%分段公式split环境(对齐采用align环境的方式&，编号在中间)
	\begin{equation}
	\begin{split}
	\cos 2x &= \cos^2 x - \sin^2 x \\
	&=2\cos^2 x - 1
	\end{split}
	\end{equation}
	
	
	%分段函数case环境(每行公式中使用&分割为两部分，通常表示值和后面的条件)
	%\in是"∈"，\mathbb{}输出对应花体字符
	\begin{equation}
	D(x)=\begin{cases}
	1, & \text{如果 } x \in \mathbb{Q}; \\
	0, & \text{如果 } x \in \mathbb{R}\setminus\mathbb{Q}.
	\end{cases}
	\end{equation}
	
\end{document}
```

## 七、LaTeX中的参考文献

### 7.1普通方法

```tex
%导言区
\documentclass{article}

\usepackage{ctex}

%正文区
\begin{document}
	%一次管理，一次使用
	%参考文献格式：
	%\begin{thebibliography}{标号样本}
	%	\bibitem[记号]{引用标志1}文献条目1
	%	\bibitem[记号]{引用标志2}文献条目2
	%	...
	%\end{thebibliography}
	%其中参考文献条目包括：作者，题目，出版社，年代，版本，页码等。
	%引用的时候可以采用：\cite{引用标志1，引用标志2,...}
	
	引用一篇文章\cite{article1} 引用一本书\cite{latexGuide}等等
	
	\begin{thebibliography}{99} %设置参考文献最多为99个
		\bibitem{article1}陈立辉，苏伟，蔡川，陈晓云，\emph{基于LaTeX的Web数学公式提取方法研究}[J]. 计算机科学. 2014(06)
		\bibitem{latexGuide} Kopka Helmut，W. Daly Patrick,\emph{Guide to \LaTeX}, $4^{th}$ Edition.Available at \texttt{http://ww.amazon.com}.
	\end{thebibliography}
	
\end{document}
```

### 7.2BibTeX格式

使用步骤：

[1]设置 TeXstudio中**”构建“**部分 **默认文献工具为BibTeX**

[2]创建一个新文件以**.bib**后缀结尾，进行相关内容编写

(补充：(1)内容也可以用**百度学术**和**Google学术**搜索中的**引用**直接获得**BibTeX格式的参考文献**，进行复制粘贴

(2)内容也可以用**知网**的引用直接获得**BibTeX格式的参考文献**([参考博客链接](https://blog.csdn.net/qq_65103357/article/details/130447760?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522169103310816800225554500%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=169103310816800225554500&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-1-130447760-null-null.142^v92^chatsearchT3_1&utm_term=%E7%9F%A5%E7%BD%91%E6%80%8E%E4%B9%88%E8%BE%93%E5%87%BAbib%E6%A0%BC%E5%BC%8F&spm=1018.2226.3001.4187))，进行复制粘贴)

下面为一个.bib文件的例子：文件名：**reference.bib**

```tex
@article{司守奎,
	title = {数学建模算法与应用},
	language = {中文;},
	author = {司守奎，孙玺菁},
	journal = {国防工业出版社},
	year = {2011}
}

@book{吴泉源1995人工智能与专家系统,
	title={人工智能与专家系统},
	author={吴泉源，刘江宁},
	publisher={人工智能与专家系统},
	year={1995},
}
```

[3]在tex源文件的导言区部分加入bibliographystyle命令，设置参考文献样式；

同时在正文中需要输出参考文献的地方，使用bibliography命令输出；

需要引用参考文献时，使用cite命令引用(具体如下面代码块所示)。

(补充：**LaTeX 参考文献标准选项及其样式共有以下8种([参考文章链接](https://zhuanlan.zhihu.com/p/483132093))：**
 plain，按字母的顺序排列，比较次序为作者、年度和标题.
 unsrt，样式同plain，只是按照引用的先后排序.
 alpha，用作者名首字母+年份后两位作标号，以字母顺序排序.
 abbrv，类似plain，将月份全拼改为缩写，更显紧凑.
 ieeetr，国际电气电子工程师协会期刊样式.
 acm，美国计算机学会期刊样式.
 siam，美国工业和应用数学学会期刊样式.
 apalike，美国心理学学会期刊样式.)

```tex
%导言区
\documentclass{article}

\usepackage{ctex}

\bibliographystyle{plain}	%设置参考文献样式，共有8种

\begin{document}
	正文...
	这是一个参考文献的引用：\cite{吴泉源1995人工智能与专家系统}
	\bibliography{reference}   %输出参考文献，其中{}中括起来的是你设置的.bib文件名,但会只出现你引用的参考文献
	\nocite{司守奎}   %输出未引用的参考文献
\end{document}
```

## 八、LaTeX中的自定义命令和环境

```tex
%导言区
\documentclass{article}

\usepackage{ctex}

%1.\newcommand-定义命令
%命令只能由字母构成，不能以\end开头
%\newcommand<命令>[<参数个数>][<首参数默认值>]{<具体定义>}

%1.1简单字符串替换newcommand，例如：
%\emph{}用于在普通(竖排)文本的中间产生斜体形状。如果当前形式为斜体，则将其切换为直立形状。
\newcommand\PRC{People's Republic of \emph{China}}

%1.2newcommand也可以使用参数，参数可以从1到9，使用时用#1,#2,......#9表示：
\newcommand\loves[2]{#1 喜欢 #2}
\newcommand\hateby[2]{#2 不受 #1 喜欢}

%1.3newcommand的参数也可以有默认值
%指定参数个数的同时指定了首个参数的默认值，那么这个命令的第一个参数就成为可选的参数(要使用中括号指定)
\newcommand\love[3][喜欢]{#2#1#3}


%2.\renewcommand-重定义命令，与\newcommand命令作用和用法相同，但只能用于已有命令
%\renewcommand<命令>[<参数个数>][<首参数默认值>]{<具体定义>}
\renewcommand\abstractname{内容简介}


%3.定义和重定义环境
%\newenvironment{<环境名称>}[<参数个数>][<首参数默认值>]
%				{<环境前定义>}
%				{<环境后定义>}
%\renewenvironment{<环境名称>}[<参数个数>][<首参数默认值>]
%				  {<环境前定义>}
%				  {<环境后定义>}
%为book类中定义摘要(abstract)环境
\newenvironment{myabstract}[1][摘要]
				{\small
					\begin{center}\bfseries #1\end{center}
					\begin{quotation}
				}
				{\end{quotation}}

%正文区
\begin{document}
	\PRC
    
    \loves{猫儿}{鱼}
     
    \hateby{猫儿}{萝卜}
     
    \love{猫儿}{鱼}
    
    \love[最爱]{猫儿}{鱼}
     
    \bengin{abstract}
    	这是一段摘要...
    \end{abstract}
    
    \begin{myabstract}
    	这是一段自定义格式的摘要...
    \end{myabstract}
\end{document}
```
