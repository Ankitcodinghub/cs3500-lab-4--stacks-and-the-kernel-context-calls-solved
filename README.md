# cs3500-lab-4--stacks-and-the-kernel-context-calls-solved
**TO GET THIS SOLUTION VISIT:** [CS3500 Lab 4- Stacks and the Kernel Context Calls Solved](https://www.ankitcodinghub.com/product/cs3500-operating-systems-solved/)


---

📩 **If you need this solution or have special requests:** **Email:** ankitcoding@gmail.com  
📱 **WhatsApp:** +1 419 877 7882  
📄 **Get a quote instantly using this form:** [Ask Homework Questions](https://www.ankitcodinghub.com/services/ask-homework-questions/)

*We deliver fast, professional, and affordable academic help.*

---

<h2>Description</h2>



<div class="kk-star-ratings kksr-auto kksr-align-center kksr-valign-top" data-payload="{&quot;align&quot;:&quot;center&quot;,&quot;id&quot;:&quot;109945&quot;,&quot;slug&quot;:&quot;default&quot;,&quot;valign&quot;:&quot;top&quot;,&quot;ignore&quot;:&quot;&quot;,&quot;reference&quot;:&quot;auto&quot;,&quot;class&quot;:&quot;&quot;,&quot;count&quot;:&quot;2&quot;,&quot;legendonly&quot;:&quot;&quot;,&quot;readonly&quot;:&quot;&quot;,&quot;score&quot;:&quot;5&quot;,&quot;starsonly&quot;:&quot;&quot;,&quot;best&quot;:&quot;5&quot;,&quot;gap&quot;:&quot;4&quot;,&quot;greet&quot;:&quot;Rate this product&quot;,&quot;legend&quot;:&quot;5\/5 - (2 votes)&quot;,&quot;size&quot;:&quot;24&quot;,&quot;title&quot;:&quot;CS3500 Lab 4- Stacks and the Kernel Context Calls Solved&quot;,&quot;width&quot;:&quot;138&quot;,&quot;_legend&quot;:&quot;{score}\/{best} - ({count} {votes})&quot;,&quot;font_factor&quot;:&quot;1.25&quot;}">

<div class="kksr-stars">

<div class="kksr-stars-inactive">
            <div class="kksr-star" data-star="1" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="2" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="3" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="4" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="5" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
    </div>

<div class="kksr-stars-active" style="width: 138px;">
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
    </div>
</div>


<div class="kksr-legend" style="font-size: 19.2px;">
            5/5 - (2 votes)    </div>
    </div>
Introduction

In the previous labs, we became familiar with system calls. We also learnt the paging mechanism in xv6. This lab will look into the stack management in a process and the kernel’s context. Firstly, we will look at a debugger called qemu-gdb and get some insights into RISC-V assembly. Thereafter, we will introduce a system call to print the kernel state of a process in xv6.

Resources

Please go through the following resources before beginning this lab assignment:

1. The xv6 book: Chapter 4 (Traps and System Calls): sections 4.1, 4.2, 4.5

2. Source files: kernel/trampoline.S and kernel/trap.c

Note

As part of this assignment, we have provided a clean version of the xv6 repo, with the required files included in it. Please implement your solutions in this repo only. We have also attached the LATEXtemplate of this document. Please write your answers in this file and submit the generated PDF (NOT the .tex).

1 Avengers, Assemble! (20 points)

For this section, it will be important to understand a bit of RISC-V assembly.

There is a file named user/call.c as part of the provided xv6 repo. Modify the Makefile suitably to allow user/call.c to be compiled as a user program in xv6. Run the command make fs.img, which compiles user/call.c (among other files) and produces a readable assembly version of the program in user/call.asm. Read the assembly code in user/call.asm for the functions g(), f(), and main(). Here are some questions that you should answer:

1. (3 points) Which registers contain arguments to functions? For example, which register holds 13 in main()’s call to printf()?

1

Solution:

2. (2 points) Where is the function call to f() from main()? Where is the call to g()?

Solution:

3. (2 points) At what address is the function printf() located?

Solution:

4. (2 points) What value is in the register ra just after the jalr to printf() in main()?

Solution:

5. (11 points) Run the following code.

unsigned int i = 0x00646c72; printf(“H%x Wo%s”, 57616, &amp;i);

(a) (3 points) What is the output? Here’s an ASCII table that maps bytes to characters.

Solution:

(b) (5 points) The above output depends on that fact that the RISC-V is littleendian. If the RISC-V were instead big-endian, what would you set i to in order to yield the same output? Would you need to change 57616 to a different value? Here’s a description of little- and big-endian.

Solution:

(c) (3 points) In the following code, what is going to be printed after ‘y=’? (Note: the answer is not a specific value.) Why does this happen?

printf(“x=%d y=%d”, 3);

Solution:

2 The Retreat (30 points)

In each stack frame, the compiler puts a frame pointer that holds the address of the caller’s frame pointer. We can design a backtrace() function using these frame pointers to walk the stack back up and print the saved return address in each stack frame. The GCC compiler, for instance, stores the frame pointer of the currently executing function in the register s0.

1. (30 points) In this section, you need to implement backtrace(). Feel free to refer to the hints provided at the end of this section.

$ bttest backtrace: 0x0000000080002c1a

0x0000000080002a3e

0x00000000800026ba

What are the steps you followed? What is the output that you got?

Solution:

(b) (5 points) Use the addr2line utility to verify the lines in code to which these addresses map to. Please mention the command you used along with the output you obtained.

Solution:

(c) (5 points) Once your backtrace() is working, invoke it from the panic() function in kernel/printf.c. Add a null pointer dereference statement in the exec() function in kernel/exec.c, and then check the kernel’s backtrace when it panics. What was the output you obtained? What functions/line numbers/file names do these addresses correspond to? (Don’t forget to comment out the null pointer dereference statement after you are done with this section.)

Solution:

Additional hints for implementing backtrace()

• Add the prototype void backtrace(void) to kernel/defs.h.

• Look at the inline assembly functions in kernel/riscv.h. Similarly, add your own function, static inline uint64 r fp(), and call this from backtrace() to read the current frame pointer. (HINT: The current frame pointer is stored in the register s0.)

• Here is a stack diagram for your reference. The current frame pointer is represented by $fp and the current stack pointer by $sp. Note that the return address and previous frame pointer live at fixed offsets from the current frame pointer. (What are these offsets?) To follow the frame pointers back up the stack, brush up on your knowledge of pointers.

.

.

.

0x2fe0 +-&gt; +——————+ |

0x2fd8 | | ret addr | |

0x2fd0 | | 0x2ff8 (prev fp) —-+

0x2fc8 | | … |

0x2fc0 | | … |

$fp –&gt; 0x2fb8 | +——————+ &lt;-+

0x2fb0 | | ret addr | |

$sp –&gt; 0x2fa8 +—- 0x2fe0 (prev fp) | |

+——————+ | .

.

2. (30 points) [OPTIONAL] Print the names of the functions and line numbers in backtrace() instead of numerical addresses.

3 The Attack …(20 points)

A process not just has its own virtual address space but, it also has metadata in the kernel. In this part we will try to understand the contents of these metadata.

1. (5 points) Every process is allocated a Process Control Block entry into the proc structure. Introduce a system call pcbread to print the contents of the proc structure.

Write a user program user/attack.c (similar to question 1). Use this program to invoke and test pcbread.

What is the PID of the process?

Solution:

2. (5 points) Fork a child process in attack.c. Use your system call to find the similarities and differences between the parent and child’s PCB. List those differences here.

Solution:

3. (5 points) Just before usertrapret returns, print the contents of the trapframe in the parent and child process in attack.c. This printing should be done only for the fork system call and at no other time. How are the trapframes different?

Solution:

4. (5 points) Print the contents of the a0 to a6 registers from the trapframe. Compare the contents of these registers with system call arguments passed from the attack.c.

Test with several different system calls. List your observations here.

Solution:

Submission Guidelines

1. Implement your solutions in the provided xv6 folder. Write your answers in the attached LATEXtemplate, convert it to PDF and name it as YOUR ROLL NO.pdf. This will serve as a report for the assignment.

2. Put your entire solution xv6 folder, and the YOUR ROLL NO.pdf in a common folder named YOUR ROLL NO LAB5.

3. Compress the folder YOUR ROLL NO LAB5 into YOUR ROLL NO LAB5.tar.gz and submit the compressed folder on Moodle.

4. NOTE: Make sure to run make clean, delete any additional manual and the .git folder from the xv6 folder before submitting.
