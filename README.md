# The Short Introduction to LaTeX2e

2022.2.8

### 一、LaTeX的基本概念

#### 1.3 LaTeX命令和代码结构

```latex
\LaTeX{}	% 大小写敏感，{}不忽略后续空格
[<optional>]{<mandatory>}	% 可选参数和必选参数
% 源代码结构
\documentclass{}
% 导言区，调用宏包和全局设置
\begin{document}
% 正文
\end{document}
% 后续内容会被忽略
```

#### 1.4 LaTeX宏包和文档类

```latex
\documentclass
[11pt, twoside, a4paper]
{article, report, book, ctexart, ctexrep, ctexbook, proc, slides, minimal}
\usepackage[]{tabularx, makecell, multirow}
```

```shell
texdoc <pkg>	# 查文档
tlmgr install/remove/info <pkg>
tlmgr update --all --self
```

#### 1.6 文件的组织方式

```latex
\include{<file>}	% 默认扩展名为.tex，另起一页读入，文件名无空格
\input{<file>}		% 纯粹的文本插入，文件名无空格
\includeonly{<file1>, <file2>}	% 在导言区限定导入的文件
\usepackage{syntonly} \syntaxonly	% 只编译不生成PDF，加快编译速度
```

### 二、用LaTeX排版文字

#### 2.3 LaTeX中的字符

```latex
\par, \\	% 换行
\^{}, \~{}	% 不加{}会形成重音效果，将后面的字符当做参数
\textbackslash	% \\反斜杠
f{}f{}i{}	% 用{}取消连字
‘’, `'	% 前后引号
-, --, ---	% 连字符，数字间表范围，破折号
\dots, \ldots	% 省略号
```

#### 2.4 手动断行和断页

```latex
\\[<length>], \\*[<length>], \newline	% 换行，换行且不换页，只用于文本段落
\newpage, \clearpage	% 换页
\linebreak[<n>], \nolinebreak[<n>], \pagebreak[<n>], \nopagebreak[<n>]	% 可选参数0-4，越大优先级越高
su\-per\-cal\-i\-frag\-i\-lis\-tic	% 在指定位置断词
```

### 三、文档元素

#### 3.1 章节和目录

```latex
\chapter{⟨title⟩} \section{⟨title⟩} \subsection{⟨title⟩} \subsubsection{⟨title⟩} \paragraph{⟨title⟩} \subparagraph{⟨title⟩}	% 章节标题
\tableofcontents	% 目录
\appendix	% 分隔正文和附录
```

#### 3.2 标题页

```latex
\title{}, \author{}, \date{}, \maketitle	% 标题
```

#### 3.3 交叉引用

```latex
\label{<label>}, \ref{<label>}, \eqref{<label>}, \pageref{<label>}	% 交叉引用
```

#### 3.4 脚注和边注

```latex
\footnote{<text>}	% 直接插入脚注
\footnotemark, \footnotetext{<text>}	% 在表格等不能直接脚注的地方，先计数，再填充内容
\marginpar{\footnotesize <text>}	% 边注
```

#### 3.5 特殊环境

```latex
\begin{enumerate}, \begin{itemize}, \begin{description}, \item[]	% enumerate会自动编号
\begin{center}, \begin{flushleft}, \begin{flushright}	% 对齐环境，会产生一个额外间距
\centering, \raggedleft, \raggedright	% 对齐命令，无额外间距
\begin{quote}, \begin{quotation}, \begin{verse}	% 引用
\begin{verbatim}, \verb|<code>|	% 代码
```

#### 3.6 表格

```latex
\begin{tabular}[<align>]{<column>}	% alian:t,b; column:c,l,r,|,@{}
{*{⟨n⟩}{⟨column⟩}}	% 重复的column
\hline, \cline{<i>,<j>}		% 横线
\multicolumn{<n>}{<column>}{<item>}	% 合并横向单元格
\multirow{⟨n⟩}{⟨width⟩}{⟨item⟩}		% 合并纵向单元格
\makecell{<item1> \\ <item2>}	% 垂直拆分
```

#### 3.7 图片

```latex
\includegraphics[<key>=<value>]{<file>}, \graphicspath	% 导入图片，导入路径 
```

#### 3.8 盒子

```latex
\mbox{}, \makebox[<width>][<align>]{}	% 水平盒子
\fbox, \framebox[<width>][<align>]{}	% 带框的水平盒子
\parbox[⟨align⟩][⟨height⟩][⟨inner-align⟩]{⟨width⟩}{}	% 垂直盒子
\begin{minipage}[⟨align⟩][⟨height⟩][⟨inner-align⟩]{⟨width⟩}	% 小页面
\rule[⟨raise⟩]{⟨width⟩}{⟨height⟩}	% 实心矩形盒子
```

#### 3.9 浮动体

```latex
\begin{table}[<placement>], \begin{figure}[<placement>]
```

### 四、排版数学公式

#### 4.2 公式排版基础

```latex
\begin{equation}	% 行间公式
\tag{}, \notag, \nonumber	% 公式编号
\[<equation>\], \begin{equation*}, \begin{displaymath}	% 不带编号的公式环境
\text{<text>}	% 处理字母文本	
```

#### 4.3 数学符号

```latex
\tfrac{}{}, \dfrac{}{}	% 压缩、放大分式
\sqrt[<n>]{}	% n次根式
\stackrel{}{}	% 自定义符号
```

#### 4.4 多行公式

```latex
\multiline, \align, \gather	% 换行，alian可用&对齐
\aligned, \gathered		% 多个公式一个编号
```

### 五、排版样式设定

#### 5.1 字体和字号

```latex
\fontsize{<size>}{<line-skip>}, \selectfont		% 字号
\setCJKmainfont{SimSun}[BoldFont=SimHei, ItalicFont=KaiTi]	% 字体
```

#### 5.3 段落格式和间距

```latex
\linespread{<n>}, \selectfont		% 行距
\setlength{\leftskip}{⟨length⟩}		% 左缩进
\setlength{\rightskip}{⟨length⟩}	% 右缩进
\setlength{\parindent}{⟨length⟩}	% 首行缩进
\hspace{<length>}, \vspace{<length>}	% 水平、垂直间距
```

#### 5.4 页面和分栏

```latex
\usepackage[hmarin=1.25in, vmargin=1in]{geometry}	% 页边距
```

#### 5.5 页眉页脚

```latex
\usepackage{fancyhdr}, \pagestyle{fancy}, \fancyhead[C]{<text>}, \fancyfoot[]{<text>}
```

### 六、特色工具和功能

#### 6.1 参考文献

```latex
\cite{<label>}, \begin{thebibliography}{<length>}, \bibitem{<length>}
```

#### 6.3 使用颜色

```latex
\color{<color>}		% 颜色
\colorbox{<color>}{<text>}	% 带背景色的盒子
\fcolorbox{<fcolor>}{<color>}{<text>}	% 带背景色和边框的盒子
```

#### 6.4 使用超链接

```latex
\url{<url>}, \href{<url>}{<text>}
```

### 八、自定义LaTeX命令和功能

#### 8.1 自定义命令和环境

```latex
\newcommand{\<name>}[<num>]{<def>}	% 定义命令：新命令名称、参数个数、定义
\newenvironment{<name>}[<num>]{<before>}{<after>}	% 定义环境：环境文本前后处理的命令
```

#### 8.2 编写自己的宏包和文档类

```latex
\ProvidesPachage{<pkg>}		% 扩展名为.sty
\RequirePackage{<pkg>}
```

#### 8.3 计数器

```latex
\newcounter{<name>}		% 定义计数器
\setcounter{<name>}{<num>}		% 修改计数器
\addtocounter{<name>}{<num>}	% 增加计数器数值
\stepcounter{<name>}	% 计数器数值加一
```



