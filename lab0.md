# 实验零：操作系统实验准备





















	(System > Administration > Synaptic Package Manager)

	set encoding=utf-8
	set fileencodings=utf-8,chinese
	set tabstop=4
	set cindent shiftwidth=4
	set backspace=indent,eol,start
	autocmd Filetype c set omnifunc=ccomplete#Complete
	autocmd Filetype cpp set omnifunc=cppcomplete#Complete
	set incsearch
	set number
	set display=lastline
	set ignorecase
	syntax on
	set nobackup
	set ruler
	set showcmd
	set smartindent
	set hlsearch
	set cmdheight=1
	set laststatus=2
	set shortmess=atI
	set formatoptions=tcrqn
	set autoindent  

可以将上述配置文件保存到：






									Intel: [_boo]
	asm("statements");





	<tr><td>字母</td><td>含义</td></tr>
	<tr><td>m, v, o</td><td>内存单元</td></tr>
	<tr><td>R</td><td>任何通用寄存器</td>	</tr>
	<tr><td>Q</td><td>寄存器eax, ebx, ecx,edx之一</td></tr>
	<tr><td>I, h</td><td>直接操作数</td></tr>
	<tr><td>E, F</td><td>浮点数</td></tr>
	<tr><td>G</td><td>任意</td></tr>
	<tr><td>a, b, c, d</td><td>寄存器eax/ax/al, ebx/bx/bl, ecx/cx/cl或edx/dx/dl</td></tr>
	<tr><td>S, D</td><td>寄存器esi或edi</td></tr>
	<tr><td>I</td><td>常数（0～31）</td></tr>
</table>



	int value=1;
	int buf[10];
	void main()
	{
		asm(
			"cld nt"
			"rep nt"
			"stosl"
		:
		: "c" (count), "a" (value) , "D" (buf[0])
		: "%ecx","%edi"
		);
	}

得到的主要汇编代码为：

	movl count,%ecx
	movl value,%eax
	movl buf,%edi
	#APP
	cld
	rep
	stosl
	#NO_APP

cld,rep,stos就不用多解释了。这几条语句的功能是向buf中写上count个value值。冒号后的语句指明输入，输出和被改变的寄存器。通过冒号以后的语句，编译器就知道你的指令需要和改变哪些寄存器，从而可以优化寄存器的分配。其中符号"c"(count)指示要把count的值放入ecx寄存器。类似的还有：

	a eax



<tr><td>clear FILENAME:NUM</td><td>删除设置在特定源文件特定行上的断点</td></tr>
<tr><td>run</td><td>运行调试程序</td></tr>
<tr><td>step</td><td>单步执行调试程序，不会直接执行函数</td></tr>
<tr><td>next</td><td>单步执行调试程序，会直接执行函数</td></tr>
<tr><td>backtrace</td><td>显示所有的调用栈帧。该命令可用来显示函数的调用顺序</td></tr>
<tr><td>where continue</td><td>继续执行正在调试的程序</td></tr>
<tr><td>display EXPR</td><td>每次程序停止后显示表达式的值,表达式由程序定义的变量组成</td></tr>
<tr><td>file FILENAME</td><td>装载指定的可执行文件进行调试</td></tr>
<tr><td>help CMDNAME</td><td>显示指定调试命令的帮助信息</td></tr>
<tr><td>info break</td><td>显示当前断点列表，包括到达断点处的次数等</td></tr>
<tr><td>info files</td><td>显示被调试文件的详细信息</td></tr>
<tr><td>info func</td><td>显示被调试程序的所有函数名称</td></tr>
<tr><td>info prog</td><td>显示被调试程序的执行状态</td></tr>
<tr><td>info local</td><td>显示被调试程序当前函数中的局部变量信息</td></tr>
<tr><td>info var</td><td>显示被调试程序的所有全局和静态变量名称</td></tr>
<tr><td>kill</td><td>终止正在被调试的程序</td></tr>
<tr><td>list</td><td>显示被调试程序的源代码</td></tr>
<tr><td>quit</td><td>退出 gdb</td></tr>



<table>
<tr><td>info win</td><td>显示窗口的大小</td></tr>
<tr><td>layout next</td><td>切换到下一个布局模式</td></tr>
<tr><td>layout prev</td><td>切换到上一个布局模式</td></tr>
<tr><td>layout src</td><td>只显示源代码</td></tr>
<tr><td>layout asm</td><td>只显示汇编代码</td></tr>
<tr><td>layout split</td><td>显示源代码和汇编代码</td></tr>
<tr><td>layout regs</td><td>增加寄存器内容显示</td></tr>
<tr><td>focus cmd/src/asm/regs/next/prev</td><td>切换当前窗口</td></tr>
<tr><td>refresh</td><td>刷新所有窗口</td></tr>
<tr><td>tui reg next</td><td>显示下一组寄存器</td></tr>
<tr><td>tui reg system</td><td>显示系统寄存器</td></tr>
<tr><td>update</td><td>更新源代码窗口和当前执行点</td></tr>
<tr><td>winheight name +/- line</td><td>调整name窗口的高度</td></tr>
<tr><td>tabset nchar</td><td>设置tab为nchar个字符</td></tr>
</table>
 
##### 2.3.4进一步的相关内容


	tar jxvf qemu.tar.bz2
	configure  --help 



<tr><td>窗口一</td><td>窗口二</td>
chy@laptop: ~/lab1$ qemu -S -hda ./bin/ucore.img  -s
<td>
</tr></table>





![双向循环链表](./lab0/image007.png "双向循环链表")
