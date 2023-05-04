Download Link: https://assignmentchef.com/product/solved-csc501-lab0
<br>
The objective of this introductory lab is to familiarize you with the process of compiling and running XINU, the tools involved, and the run-time environment and segment layout.

<h2>2. Lab Setup Guide</h2>

XINU is a small Unix-like operating system originally developed by Douglas Comer for instructional purposes at Purdue University. It is small enough so that we can understand it entirely within one semester. As part of lab assignment, we will re-implement or improve some apsects of XINU.

Step 1: Setting environment variables for lab assignments:

Get access to a customized VCL image — XINU+QEMU (CSC501) — through the <a href="http://vcl.ncsu.edu/">VCL  </a><a href="http://vcl.ncsu.edu/">(</a><a href="http://vcl.ncsu.edu/">http://vcl.ncsu.edu/)</a>facility

Step 2: Untar the XINU source files as follows:

<ol>

 <li>Change to your home directory, if you are not already in it.</li>

</ol>

<h3>cd</h3>

<ol start="2">

 <li>Untar the XINU source by typing the following:</li>

</ol>

<a href="https://moodle-courses1920.wolfware.ncsu.edu/mod/assign/view.php?id=569771">The </a><a href="https://moodle-courses1920.wolfware.ncsu.edu/mod/assign/view.php?id=569771">csc501-lab0.tgz </a><a href="https://moodle-courses1920.wolfware.ncsu.edu/mod/assign/view.php?id=569771">file is available is available on </a><a href="https://moodle-courses1920.wolfware.ncsu.edu/mod/assign/view.php?id=569771">moodle </a><a href="https://moodle-courses1920.wolfware.ncsu.edu/mod/assign/view.php?id=569771">(</a><a href="https://moodle-courses1920.wolfware.ncsu.edu/mod/assign/view.php?id=569771">https://moodlecourses1920.wolfware.ncsu.edu/mod/assi</a><a href="https://moodle-courses1920.wolfware.ncsu.edu/mod/assign/view.php?id=569771">g</a><a href="https://moodle-courses1920.wolfware.ncsu.edu/mod/assign/view.php?id=569771">n/view.php?id=569771)</a><a href="https://moodle-courses1920.wolfware.ncsu.edu/mod/assign/view.php?id=569771">.</a>

<h3>tar xzvf csc501-lab0.tgz</h3>

In your home directory, you will now have a directory named csc501-lab0. The subdirectories under this directory contain source code, header files, etc, for XINU. NOTE: the tar file name may be different from the above depending on the lab you are working on. Please refer to the lab handouts for the location of the tar file for the current lab.

Step 3: Building XINU

To compile the XINU kernel which will be downloaded and run on the backend machines, run “make” in the compile directory as follows:

<table width="709">

 <tbody>

  <tr>

   <td width="709"><strong>cd csc501-lab0/compile make depend make </strong>This creates an OS image called ‘xinu.elf’.</td>

  </tr>

 </tbody>

</table>

If you get a permission denied issue, please go to the config directory and change permission of config file, and then compile using the previous commands.

<h3>chmod 755 config</h3>

Step 4: Running and debugging XINU

The XINU image runs on the QEMU emulator machines. To boot up the image, type:

<h3>make run</h3>

XINU should start running and print a message “Hello World, Xinu lives.”Typing (control-a c) will always bring you to ‘(qemu)’ prompt. From there, you can quit by typing ‘q‘ To debug XINU, run the image in the debug mode by:

<strong>make debug</strong>

Then execute GDB in another ssh session:

<strong>gdb xinu.elf</strong>

In the (gdb) console, connect to the remote server by:

<strong>target remote localhost:1234</strong>

You can use many debugging features provided by GDB, e.g., adding a break point at the main function:

<h3>b main</h3>

To run to the next breakpoint, type:

<strong>c</strong>

The detailed document for GDB can be found <a href="https://www.sourceware.org/gdb">here </a><a href="https://www.sourceware.org/gdb">(</a><a href="https://www.sourceware.org/gdb">https://www.sourceware.or</a><a href="https://www.sourceware.org/gdb">g</a><a href="https://www.sourceware.org/gdb">/</a><a href="https://www.sourceware.org/gdb">g</a><a href="https://www.sourceware.org/gdb">db)</a>

<h2>3. Readings</h2>

<ol>

 <li><a href="https://moodle-courses1920.wolfware.ncsu.edu/mod/assign/view.php?id=569771">The Intel manuals (Volume 1, Volume 2, Volume 3) are available </a><a href="https://moodle-courses1920.wolfware.ncsu.edu/mod/assign/view.php?id=569771">here </a><a href="https://moodle-courses1920.wolfware.ncsu.edu/mod/assign/view.php?id=569771">(</a><a href="https://moodle-courses1920.wolfware.ncsu.edu/mod/assign/view.php?id=569771">https://moodlecourses1920.wolfware.ncsu.edu/mod/assi</a><a href="https://moodle-courses1920.wolfware.ncsu.edu/mod/assign/view.php?id=569771">g</a><a href="https://moodle-courses1920.wolfware.ncsu.edu/mod/assign/view.php?id=569771">n/view.php?id=569771)</a></li>

 <li>A brief <a href="http://www.delorie.com/djgpp/doc/ug/asm/about-386.html">g</a><a href="http://www.delorie.com/djgpp/doc/ug/asm/about-386.html">uide on the 30386 architecture </a><a href="http://www.delorie.com/djgpp/doc/ug/asm/about-386.html">(</a><a href="http://www.delorie.com/djgpp/doc/ug/asm/about-386.html">http://www.delorie.com/d</a><a href="http://www.delorie.com/djgpp/doc/ug/asm/about-386.html">jg</a><a href="http://www.delorie.com/djgpp/doc/ug/asm/about-386.html">pp/doc/u</a><a href="http://www.delorie.com/djgpp/doc/ug/asm/about-386.html">g</a><a href="http://www.delorie.com/djgpp/doc/ug/asm/about-386.html">/asm/about-386.html)</a>.</li>

 <li><a href="https://en.wikibooks.org/wiki/X86_Assembly/GAS_Syntax">AT&amp;T assembly information specific to the gnu assembler is available </a><a href="https://en.wikibooks.org/wiki/X86_Assembly/GAS_Syntax">here (http://en.wikibooks.or</a><a href="https://en.wikibooks.org/wiki/X86_Assembly/GAS_Syntax">g</a><a href="https://en.wikibooks.org/wiki/X86_Assembly/GAS_Syntax">/wiki/X86_Assembl</a><a href="https://en.wikibooks.org/wiki/X86_Assembly/GAS_Syntax">y</a><a href="https://en.wikibooks.org/wiki/X86_Assembly/GAS_Syntax">/GAS_S</a><a href="https://en.wikibooks.org/wiki/X86_Assembly/GAS_Syntax">y</a><a href="https://en.wikibooks.org/wiki/X86_Assembly/GAS_Syntax">ntax)</a><a href="https://en.wikibooks.org/wiki/X86_Assembly/GAS_Syntax"> as a wikibook.</a></li>

 <li>Any man pages/manuals you discover that you need.</li>

</ol>

Note: The Intel document is hundreds of pages long and there is no need to print it. Please do not print it!

<h2>4. Tasks</h2>

You will be using the csc501-lab0.tgz you have downloaded and compiled by following the lab setup guide. And you are asked to write several XINU functions that perform the following tasks:

<h3>1. long zfunction(long param)</h3>

Clear from the 10th to 18th bits (counting left to right), shift the parameter param by 4 bits to the left, and then fill the right most bits with 0. For example, the input parameter 0xaabbccdd should generate a return value of 0xa800cdd0. You can assume that the size of long is 4 bytes. The code for this function should be entirely written in x86 assembly. You should not use inline assembly, (i.e., do not use asm(???)). To investigate the assembly code generated by the compiler, you can use the tool objdump -d &lt;___.o&gt; to disassemble an object file. The object files reside in the /compiledirectory within the main Xinu directory. You can also see some of the *.S files in the /sys directory for reference.

<h3>2. void printsegaddress()</h3>

Print the addresses indicating the end of the text, data, and BSS segments of the Xinu OS. Also print the 4-byte contents (in hexadecimal) preceding and after those addresses. This function can be written in C.

<h3>3. void printtos()</h3>

Print the address of the top of the run-time stack for whichever process you are currently in, right before and right after you get into the printtos() function call. In addition, print the contents of upto four stack locations below the top of the stack (the four or fewer items that have been the most recently pushed, if any). Remember that stack elements are 32 bits wide, and be careful to perform pointer arithmetic correctly. Also note that there are local variables and arguments on the stack, among other things. See the hints given for #4 below, especially on stacktrace.c and proc.h. Your function can be written entirely in C, or you can use in-line assembly if you prefer.

<h3>4. void printprocstks(int priority)</h3>

For each existing process with larger priority than the parameter, print the stack base, stack size, stacklimit, and stack pointer. Also, for each process, include the process name, the process id and the process priority.

To help you do this, please look into proc.h in the h/ directory. Note the proctab[] array that holds all processes. Also, note that the pesp member of the pentry structure holds the saved stack pointer. Therefore, the currently executing process has a stack pointer that is different from the value of this variable. In order to help you get the stack pointer of the currently executing process, carefully study the stacktrace.c file in the sys/ directory. The register %esp holds the current stack pointer. You can use in-line assembly(i.e., asm(“…”)) to do this part.

<h3>5. void printsyscallsummary()</h3>

Print the summary of the system calls which have been invoked for each process. This task is loosely based on the functionality of <a href="https://lttng.org/">LTTn</a><a href="https://lttng.org/">g</a><a href="https://lttng.org/">  (http://lttn</a><a href="https://lttng.org/">g</a><a href="https://lttng.org/">.or</a><a href="https://lttng.org/">g</a><a href="https://lttng.org/">/)</a>. There are 43 system calls declared. Please look into kernel.h in the h/ directory to see all declared system calls. However, only 27 system calls are implemented in this XINU version. The implementation of these 27 system calls are in the sys/ directory. You are asked to print the frequency (how many times each system call type is invoked) and the average execution time (how long it takes to execute each system call type in average) of these 27 system calls for each process. In order to do this, you will need to modify the implementation of these 27 types of system calls to trace them whenever they are invoked. To measure the time, XINU provides a global variable named ctr1000 to track the time (in milliseconds) passed by since the system starts. Please look into sys/clkinit.c and sys/clkint.S to see the details.

You will also need to implement two other functions: <strong>void syscallsummary_start()</strong>: to start tracing the system calls. All the system calls are invoked after calling this function (and before calling syscallsummary_stop()) will be presented in the system call summary.

<strong>void syscallsummary_stop()</strong>: to stop tracing the system calls.

In other words, these two functions determine the duration in which the system calls are traced. <a href="https://moodle-courses1819.wolfware.ncsu.edu/mod/assign/view.php?id=652112">To help you complete this task, we provide two files, </a><a href="https://moodle-courses1819.wolfware.ncsu.edu/mod/assign/view.php?id=652112">syscalls.txt </a><a href="https://moodle-courses1819.wolfware.ncsu.edu/mod/assign/view.php?id=652112">(</a><a href="https://moodle-courses1819.wolfware.ncsu.edu/mod/assign/view.php?id=652112">https://moodlecourses1819.wolfware.ncsu.edu/mod/assi</a><a href="https://moodle-courses1819.wolfware.ncsu.edu/mod/assign/view.php?id=652112">g</a><a href="https://moodle-courses1819.wolfware.ncsu.edu/mod/assign/view.php?id=652112">n/view.php?id=652112)</a><a href="https://moodle-courses1819.wolfware.ncsu.edu/mod/assign/view.php?id=652112"> lists all the sys</a>tem calls you will need to trace, <a href="https://moodle-courses1920.wolfware.ncsu.edu/pluginfile.php/1067002/mod_assign/introattachment/0/test.c?forcedownload=1">and </a><a href="https://moodle-courses1920.wolfware.ncsu.edu/pluginfile.php/1067002/mod_assign/introattachment/0/test.c?forcedownload=1">test.c </a><a href="https://moodle-courses1920.wolfware.ncsu.edu/pluginfile.php/1067002/mod_assign/introattachment/0/test.c?forcedownload=1">(</a><a href="https://moodle-courses1920.wolfware.ncsu.edu/pluginfile.php/1067002/mod_assign/introattachment/0/test.c?forcedownload=1">https://moodle-courses1920.wolfware.ncsu.edu/plu</a><a href="https://moodle-courses1920.wolfware.ncsu.edu/pluginfile.php/1067002/mod_assign/introattachment/0/test.c?forcedownload=1">g</a><a href="https://moodle-courses1920.wolfware.ncsu.edu/pluginfile.php/1067002/mod_assign/introattachment/0/test.c?forcedownload=1">infile.php/1067002/mod_assi</a><a href="https://moodle-courses1920.wolfware.ncsu.edu/pluginfile.php/1067002/mod_assign/introattachment/0/test.c?forcedownload=1">g</a><a href="https://moodle-courses1920.wolfware.ncsu.edu/pluginfile.php/1067002/mod_assign/introattachment/0/test.c?forcedownload=1">n/introattachment/0/test.c? forcedownload=1)</a><a href="https://moodle-courses1920.wolfware.ncsu.edu/pluginfile.php/1067002/mod_assign/introattachment/0/test.c?forcedownload=1"> demonstrates the usage of the functions you will implement (note that this is only the test file and wil</a>l not be used for grading).

Implement this lab as a set of functions that can be called from main(). Each function should reside in a separate file in the sys directory, and should be incorporated into the Makefile. The files should be named after the functions they are implementing with C files having the .c extension and the assembly files having the .S extension. For example, the file that will hold void printsegaddress() should be named printsegaddress.c; and the file that will hold long zfunction(long param) should be named zfunction.S. You should put syscallsummary_start, syscallsummary_stop functions in the same file as printsyscallsummary function and name it as printsyscallsummary.c . If you require a header file, please name it lab0.h. Note: as you create new files, you may need to update the Makefile (located in the compile/directory) to configure it to compile your files correctly. Just look at what is done for the existing files (e.g., main.c) to see what you have to do.

<h2>5. Additional Questions</h2>

Write your answers to the following questions in a file named Lab0Answers.txt(in simple text).

Please place this file in the sys/ directory and turn it in, along with the above programming assignment.

<ol>

 <li>Assuming the XINU text begins at address 0x0, draw a rough diagram of XINU’s memory layout with addresses derived from your experimental measurements. Include the information you uncovered from running your version of printsegaddress() and printprocstks().</li>

 <li>What is the difference in stack top address before and after calling printtos() ? Draw a diagram to illustrate what are the contents of the items pushed into the stack between these two time points.</li>

 <li>Which byte order is adopted in the host machine that we are using ? How did you find out ?</li>

 <li>Briefly describe the mov, push, pusha, pop, and popa instructions in the x86.</li>

 <li>In a stack frame, local variables are stored below the top of the stack. In task 3, does your result show all the local variables declared in your printtos function? If not, can you explain that? (hint: try to disable the compiler optimization by specifying -O0 in your Makefile)</li>

</ol>