Download Link: https://assignmentchef.com/product/solved-csci2500-homework-5-simulation-of-mips-pipelining
<br>
For this individual homework assignment, you will use C to implement a simulation of MIPS pipelining. As we’ve covered in lecture, there are five stages to the pipeline, i.e., IF, ID, EX, MEM, and WB.

For your simulation, you are required to support the add, sub, and, or, lw, and sw instructions; note that some of these are pseudo-instructions, which is fine. More specifically, you must simulate (and output) how a given sequence of instructions would be pipelined in a five-stage MIPS implementation.

Do <strong>not </strong>implement forwarding in your simulation.

You can assume that each given instruction will be syntactically correct. You can also assume that there is a single space character between the instruction and its parameters. Further, each parameter is delimited by a comma or parentheses. Below are a few example instructions that you must support:

add $t0,$s2,$s3 add $t1,$t3,73 or $s0,$s0,$t3 lw $a0,12($sp) sw $t6,32($a1)

<h2>Required Command-Line Argument</h2>

Your program must accept one command-line argument as input. This argument (i.e., argv[1]) specifies the input file containing MIPS code to simulate. You may assume that no more than five instructions are given in the input file. And note that each instruction will end with a newline character (i.e., ‘
’).

<h2>Required Output</h2>

For your output, you must show <em>each cycle </em>of program execution. Each cycle will correspond to a column of output. Initially, each column is empty, indicated by a period (i.e., ‘.’). Use TAB characters (i.e., ‘t’) to delimit each column. And assume that you will have no more than nine cycles to simulate.

Recall that a <em>data hazard </em>describes a situation in which the next instruction cannot be executed in the next cycle until a previous instruction is complete. Your code should be able to detect when it is necessary to insert one or more “bubbles” (see Section 4.7 of the textbook and corresponding lecture notes for more details).

More specifically, you will need to properly handle data hazards by adding nop instructions as necessary. Show these cases by indicating an asterisk (i.e., ‘*’) in the appropriate columns and adding the required number of nop instructions. To ensure proper formatting, add an extra TAB character after the nop.

On the next few pages, we present a few example runs of your program that you should use to better understand how your program should work, how you can test your code, and what output formatting to use for Submitty.

The first example (i.e., ex01.s) includes no data hazards.

START OF SIMULATION

<table width="0">

 <tbody>

  <tr>

   <td width="183">CPU Cycles ===&gt; 1</td>

   <td width="61">2</td>

   <td width="61">3</td>

   <td width="61">4</td>

   <td width="61">5</td>

   <td width="61">6</td>

   <td width="61">7</td>

   <td width="61">8</td>

   <td width="8">9</td>

  </tr>

  <tr>

   <td width="183">add $s1,$s0,$s0 IF</td>

   <td width="61">.</td>

   <td width="61">.</td>

   <td width="61">.</td>

   <td width="61">.</td>

   <td width="61">.</td>

   <td width="61">.</td>

   <td width="61">.</td>

   <td width="8">.</td>

  </tr>

  <tr>

   <td width="183">add $t2,$s0,$s5 .</td>

   <td width="61">.</td>

   <td width="61">.</td>

   <td width="61">.</td>

   <td width="61">.</td>

   <td width="61">.</td>

   <td width="61">.</td>

   <td width="61">.</td>

   <td width="8">.</td>

  </tr>

  <tr>

   <td width="183">add $t4,$s3,70 .</td>

   <td width="61">.</td>

   <td width="61">.</td>

   <td width="61">.</td>

   <td width="61">.</td>

   <td width="61">.</td>

   <td width="61">.</td>

   <td width="61">.</td>

   <td width="8">.</td>

  </tr>

  <tr>

   <td width="183">CPU Cycles ===&gt; 1</td>

   <td width="61">2</td>

   <td width="61">3</td>

   <td width="61">4</td>

   <td width="61">5</td>

   <td width="61">6</td>

   <td width="61">7</td>

   <td width="61">8</td>

   <td width="8">9</td>

  </tr>

  <tr>

   <td width="183">add $s1,$s0,$s0 IF</td>

   <td width="61">ID</td>

   <td width="61">.</td>

   <td width="61">.</td>

   <td width="61">.</td>

   <td width="61">.</td>

   <td width="61">.</td>

   <td width="61">.</td>

   <td width="8">.</td>

  </tr>

  <tr>

   <td width="183">add $t2,$s0,$s5 .</td>

   <td width="61">IF</td>

   <td width="61">.</td>

   <td width="61">.</td>

   <td width="61">.</td>

   <td width="61">.</td>

   <td width="61">.</td>

   <td width="61">.</td>

   <td width="8">.</td>

  </tr>

  <tr>

   <td width="183">add $t4,$s3,70 .</td>

   <td width="61">.</td>

   <td width="61">.</td>

   <td width="61">.</td>

   <td width="61">.</td>

   <td width="61">.</td>

   <td width="61">.</td>

   <td width="61">.</td>

   <td width="8">.</td>

  </tr>

  <tr>

   <td width="183">CPU Cycles ===&gt; 1</td>

   <td width="61">2</td>

   <td width="61">3</td>

   <td width="61">4</td>

   <td width="61">5</td>

   <td width="61">6</td>

   <td width="61">7</td>

   <td width="61">8</td>

   <td width="8">9</td>

  </tr>

  <tr>

   <td width="183">add $s1,$s0,$s0 IF</td>

   <td width="61">ID</td>

   <td width="61">EX</td>

   <td width="61">.</td>

   <td width="61">.</td>

   <td width="61">.</td>

   <td width="61">.</td>

   <td width="61">.</td>

   <td width="8">.</td>

  </tr>

  <tr>

   <td width="183">add $t2,$s0,$s5 .</td>

   <td width="61">IF</td>

   <td width="61">ID</td>

   <td width="61">.</td>

   <td width="61">.</td>

   <td width="61">.</td>

   <td width="61">.</td>

   <td width="61">.</td>

   <td width="8">.</td>

  </tr>

  <tr>

   <td width="183">add $t4,$s3,70 .</td>

   <td width="61">.</td>

   <td width="61">IF</td>

   <td width="61">.</td>

   <td width="61">.</td>

   <td width="61">.</td>

   <td width="61">.</td>

   <td width="61">.</td>

   <td width="8">.</td>

  </tr>

  <tr>

   <td width="183">CPU Cycles ===&gt; 1</td>

   <td width="61">2</td>

   <td width="61">3</td>

   <td width="61">4</td>

   <td width="61">5</td>

   <td width="61">6</td>

   <td width="61">7</td>

   <td width="61">8</td>

   <td width="8">9</td>

  </tr>

  <tr>

   <td width="183">add $s1,$s0,$s0 IF</td>

   <td width="61">ID</td>

   <td width="61">EX</td>

   <td width="61">MEM</td>

   <td width="61">.</td>

   <td width="61">.</td>

   <td width="61">.</td>

   <td width="61">.</td>

   <td width="8">.</td>

  </tr>

  <tr>

   <td width="183">add $t2,$s0,$s5 .</td>

   <td width="61">IF</td>

   <td width="61">ID</td>

   <td width="61">EX</td>

   <td width="61">.</td>

   <td width="61">.</td>

   <td width="61">.</td>

   <td width="61">.</td>

   <td width="8">.</td>

  </tr>

  <tr>

   <td width="183">add $t4,$s3,70 .</td>

   <td width="61">.</td>

   <td width="61">IF</td>

   <td width="61">ID</td>

   <td width="61">.</td>

   <td width="61">.</td>

   <td width="61">.</td>

   <td width="61">.</td>

   <td width="8">.</td>

  </tr>

  <tr>

   <td width="183">CPU Cycles ===&gt; 1</td>

   <td width="61">2</td>

   <td width="61">3</td>

   <td width="61">4</td>

   <td width="61">5</td>

   <td width="61">6</td>

   <td width="61">7</td>

   <td width="61">8</td>

   <td width="8">9</td>

  </tr>

  <tr>

   <td width="183">add $s1,$s0,$s0 IF</td>

   <td width="61">ID</td>

   <td width="61">EX</td>

   <td width="61">MEM</td>

   <td width="61">WB</td>

   <td width="61">.</td>

   <td width="61">.</td>

   <td width="61">.</td>

   <td width="8">.</td>

  </tr>

  <tr>

   <td width="183">add $t2,$s0,$s5 .</td>

   <td width="61">IF</td>

   <td width="61">ID</td>

   <td width="61">EX</td>

   <td width="61">MEM</td>

   <td width="61">.</td>

   <td width="61">.</td>

   <td width="61">.</td>

   <td width="8">.</td>

  </tr>

  <tr>

   <td width="183">add $t4,$s3,70 .</td>

   <td width="61">.</td>

   <td width="61">IF</td>

   <td width="61">ID</td>

   <td width="61">EX</td>

   <td width="61">.</td>

   <td width="61">.</td>

   <td width="61">.</td>

   <td width="8">.</td>

  </tr>

  <tr>

   <td width="183">CPU Cycles ===&gt; 1</td>

   <td width="61">2</td>

   <td width="61">3</td>

   <td width="61">4</td>

   <td width="61">5</td>

   <td width="61">6</td>

   <td width="61">7</td>

   <td width="61">8</td>

   <td width="8">9</td>

  </tr>

  <tr>

   <td width="183">add $s1,$s0,$s0 IF</td>

   <td width="61">ID</td>

   <td width="61">EX</td>

   <td width="61">MEM</td>

   <td width="61">WB</td>

   <td width="61">.</td>

   <td width="61">.</td>

   <td width="61">.</td>

   <td width="8">.</td>

  </tr>

  <tr>

   <td width="183">add $t2,$s0,$s5 .</td>

   <td width="61">IF</td>

   <td width="61">ID</td>

   <td width="61">EX</td>

   <td width="61">MEM</td>

   <td width="61">WB</td>

   <td width="61">.</td>

   <td width="61">.</td>

   <td width="8">.</td>

  </tr>

  <tr>

   <td width="183">add $t4,$s3,70 .</td>

   <td width="61">.</td>

   <td width="61">IF</td>

   <td width="61">ID</td>

   <td width="61">EX</td>

   <td width="61">MEM</td>

   <td width="61">.</td>

   <td width="61">.</td>

   <td width="8">.</td>

  </tr>

  <tr>

   <td width="183">CPU Cycles ===&gt; 1</td>

   <td width="61">2</td>

   <td width="61">3</td>

   <td width="61">4</td>

   <td width="61">5</td>

   <td width="61">6</td>

   <td width="61">7</td>

   <td width="61">8</td>

   <td width="8">9</td>

  </tr>

  <tr>

   <td width="183">add $s1,$s0,$s0 IF</td>

   <td width="61">ID</td>

   <td width="61">EX</td>

   <td width="61">MEM</td>

   <td width="61">WB</td>

   <td width="61">.</td>

   <td width="61">.</td>

   <td width="61">.</td>

   <td width="8">.</td>

  </tr>

  <tr>

   <td width="183">add $t2,$s0,$s5 .</td>

   <td width="61">IF</td>

   <td width="61">ID</td>

   <td width="61">EX</td>

   <td width="61">MEM</td>

   <td width="61">WB</td>

   <td width="61">.</td>

   <td width="61">.</td>

   <td width="8">.</td>

  </tr>

  <tr>

   <td width="183">add $t4,$s3,70 .</td>

   <td width="61">.</td>

   <td width="61">IF</td>

   <td width="61">ID</td>

   <td width="61">EX</td>

   <td width="61">MEM</td>

   <td width="61">WB</td>

   <td width="61">.</td>

   <td width="8">.</td>

  </tr>

 </tbody>

</table>

END OF SIMULATION

The second example (i.e., ex02.s) includes a dependency on register $t1.

<table width="0">

 <tbody>

  <tr>

   <td width="167">START OF SIMULATION</td>

   <td width="77"> </td>

   <td width="61"> </td>

   <td width="61"> </td>

   <td width="61"> </td>

   <td width="61"> </td>

   <td width="61"> </td>

   <td width="61"> </td>

   <td width="8"> </td>

  </tr>

  <tr>

   <td width="167">CPU Cycles ===&gt; 1</td>

   <td width="77">2</td>

   <td width="61">3</td>

   <td width="61">4</td>

   <td width="61">5</td>

   <td width="61">6</td>

   <td width="61">7</td>

   <td width="61">8</td>

   <td width="8">9</td>

  </tr>

  <tr>

   <td width="167">add $t1,$s0,$s0 IF</td>

   <td width="77">.</td>

   <td width="61">.</td>

   <td width="61">.</td>

   <td width="61">.</td>

   <td width="61">.</td>

   <td width="61">.</td>

   <td width="61">.</td>

   <td width="8">.</td>

  </tr>

  <tr>

   <td width="167">add $t2,$s0,42 .</td>

   <td width="77">.</td>

   <td width="61">.</td>

   <td width="61">.</td>

   <td width="61">.</td>

   <td width="61">.</td>

   <td width="61">.</td>

   <td width="61">.</td>

   <td width="8">.</td>

  </tr>

  <tr>

   <td width="167">add $t4,$t1,70 .</td>

   <td width="77">.</td>

   <td width="61">.</td>

   <td width="61">.</td>

   <td width="61">.</td>

   <td width="61">.</td>

   <td width="61">.</td>

   <td width="61">.</td>

   <td width="8">.</td>

  </tr>

  <tr>

   <td width="167">CPU Cycles ===&gt; 1</td>

   <td width="77">2</td>

   <td width="61">3</td>

   <td width="61">4</td>

   <td width="61">5</td>

   <td width="61">6</td>

   <td width="61">7</td>

   <td width="61">8</td>

   <td width="8">9</td>

  </tr>

  <tr>

   <td width="167">add $t1,$s0,$s0 IF</td>

   <td width="77">ID</td>

   <td width="61">.</td>

   <td width="61">.</td>

   <td width="61">.</td>

   <td width="61">.</td>

   <td width="61">.</td>

   <td width="61">.</td>

   <td width="8">.</td>

  </tr>

  <tr>

   <td width="167">add $t2,$s0,42 .</td>

   <td width="77">IF</td>

   <td width="61">.</td>

   <td width="61">.</td>

   <td width="61">.</td>

   <td width="61">.</td>

   <td width="61">.</td>

   <td width="61">.</td>

   <td width="8">.</td>

  </tr>

  <tr>

   <td width="167">add $t4,$t1,70 .</td>

   <td width="77">.</td>

   <td width="61">.</td>

   <td width="61">.</td>

   <td width="61">.</td>

   <td width="61">.</td>

   <td width="61">.</td>

   <td width="61">.</td>

   <td width="8">.</td>

  </tr>

  <tr>

   <td width="167">CPU Cycles ===&gt; 1</td>

   <td width="77">2</td>

   <td width="61">3</td>

   <td width="61">4</td>

   <td width="61">5</td>

   <td width="61">6</td>

   <td width="61">7</td>

   <td width="61">8</td>

   <td width="8">9</td>

  </tr>

  <tr>

   <td width="167">add $t1,$s0,$s0 IF</td>

   <td width="77">ID</td>

   <td width="61">EX</td>

   <td width="61">.</td>

   <td width="61">.</td>

   <td width="61">.</td>

   <td width="61">.</td>

   <td width="61">.</td>

   <td width="8">.</td>

  </tr>

  <tr>

   <td width="167">add $t2,$s0,42 .</td>

   <td width="77">IF</td>

   <td width="61">ID</td>

   <td width="61">.</td>

   <td width="61">.</td>

   <td width="61">.</td>

   <td width="61">.</td>

   <td width="61">.</td>

   <td width="8">.</td>

  </tr>

  <tr>

   <td width="167">add $t4,$t1,70 .</td>

   <td width="77">.</td>

   <td width="61">IF</td>

   <td width="61">.</td>

   <td width="61">.</td>

   <td width="61">.</td>

   <td width="61">.</td>

   <td width="61">.</td>

   <td width="8">.</td>

  </tr>

  <tr>

   <td width="167">CPU Cycles ===&gt; 1</td>

   <td width="77">2</td>

   <td width="61">3</td>

   <td width="61">4</td>

   <td width="61">5</td>

   <td width="61">6</td>

   <td width="61">7</td>

   <td width="61">8</td>

   <td width="8">9</td>

  </tr>

  <tr>

   <td width="167">add $t1,$s0,$s0 IF</td>

   <td width="77">ID</td>

   <td width="61">EX</td>

   <td width="61">MEM</td>

   <td width="61">.</td>

   <td width="61">.</td>

   <td width="61">.</td>

   <td width="61">.</td>

   <td width="8">.</td>

  </tr>

  <tr>

   <td width="167">add $t2,$s0,42 .</td>

   <td width="77">IF</td>

   <td width="61">ID</td>

   <td width="61">EX</td>

   <td width="61">.</td>

   <td width="61">.</td>

   <td width="61">.</td>

   <td width="61">.</td>

   <td width="8">.</td>

  </tr>

  <tr>

   <td width="167">add $t4,$t1,70 .</td>

   <td width="77">.</td>

   <td width="61">IF</td>

   <td width="61">ID</td>

   <td width="61">.</td>

   <td width="61">.</td>

   <td width="61">.</td>

   <td width="61">.</td>

   <td width="8">.</td>

  </tr>

  <tr>

   <td width="167">CPU Cycles ===&gt; 1</td>

   <td width="77">2</td>

   <td width="61">3</td>

   <td width="61">4</td>

   <td width="61">5</td>

   <td width="61">6</td>

   <td width="61">7</td>

   <td width="61">8</td>

   <td width="8">9</td>

  </tr>

  <tr>

   <td width="167">add $t1,$s0,$s0 IF</td>

   <td width="77">ID</td>

   <td width="61">EX</td>

   <td width="61">MEM</td>

   <td width="61">WB</td>

   <td width="61">.</td>

   <td width="61">.</td>

   <td width="61">.</td>

   <td width="8">.</td>

  </tr>

  <tr>

   <td width="167">add $t2,$s0,42 .</td>

   <td width="77">IF</td>

   <td width="61">ID</td>

   <td width="61">EX</td>

   <td width="61">MEM</td>

   <td width="61">.</td>

   <td width="61">.</td>

   <td width="61">.</td>

   <td width="8">.</td>

  </tr>

  <tr>

   <td width="167">nop                                 .</td>

   <td width="77">.</td>

   <td width="61">IF</td>

   <td width="61">ID</td>

   <td width="61">*</td>

   <td width="61">.</td>

   <td width="61">.</td>

   <td width="61">.</td>

   <td width="8">.</td>

  </tr>

  <tr>

   <td width="167">add $t4,$t1,70 .</td>

   <td width="77">.</td>

   <td width="61">IF</td>

   <td width="61">ID</td>

   <td width="61">ID</td>

   <td width="61">.</td>

   <td width="61">.</td>

   <td width="61">.</td>

   <td width="8">.</td>

  </tr>

  <tr>

   <td width="167">CPU Cycles ===&gt; 1</td>

   <td width="77">2</td>

   <td width="61">3</td>

   <td width="61">4</td>

   <td width="61">5</td>

   <td width="61">6</td>

   <td width="61">7</td>

   <td width="61">8</td>

   <td width="8">9</td>

  </tr>

  <tr>

   <td width="167">add $t1,$s0,$s0 IF</td>

   <td width="77">ID</td>

   <td width="61">EX</td>

   <td width="61">MEM</td>

   <td width="61">WB</td>

   <td width="61">.</td>

   <td width="61">.</td>

   <td width="61">.</td>

   <td width="8">.</td>

  </tr>

  <tr>

   <td width="167">add $t2,$s0,42 .</td>

   <td width="77">IF</td>

   <td width="61">ID</td>

   <td width="61">EX</td>

   <td width="61">MEM</td>

   <td width="61">WB</td>

   <td width="61">.</td>

   <td width="61">.</td>

   <td width="8">.</td>

  </tr>

  <tr>

   <td width="167">nop                                 .</td>

   <td width="77">.</td>

   <td width="61">IF</td>

   <td width="61">ID</td>

   <td width="61">*</td>

   <td width="61">*</td>

   <td width="61">.</td>

   <td width="61">.</td>

   <td width="8">.</td>

  </tr>

  <tr>

   <td width="167">add $t4,$t1,70 .</td>

   <td width="77">.</td>

   <td width="61">IF</td>

   <td width="61">ID</td>

   <td width="61">ID</td>

   <td width="61">EX</td>

   <td width="61">.</td>

   <td width="61">.</td>

   <td width="8">.</td>

  </tr>

  <tr>

   <td width="167">CPU Cycles ===&gt; 1</td>

   <td width="77">2</td>

   <td width="61">3</td>

   <td width="61">4</td>

   <td width="61">5</td>

   <td width="61">6</td>

   <td width="61">7</td>

   <td width="61">8</td>

   <td width="8">9</td>

  </tr>

  <tr>

   <td width="167">add $t1,$s0,$s0 IF</td>

   <td width="77">ID</td>

   <td width="61">EX</td>

   <td width="61">MEM</td>

   <td width="61">WB</td>

   <td width="61">.</td>

   <td width="61">.</td>

   <td width="61">.</td>

   <td width="8">.</td>

  </tr>

  <tr>

   <td width="167">add $t2,$s0,42 .</td>

   <td width="77">IF</td>

   <td width="61">ID</td>

   <td width="61">EX</td>

   <td width="61">MEM</td>

   <td width="61">WB</td>

   <td width="61">.</td>

   <td width="61">.</td>

   <td width="8">.</td>

  </tr>

  <tr>

   <td width="167">nop                                 .</td>

   <td width="77">.</td>

   <td width="61">IF</td>

   <td width="61">ID</td>

   <td width="61">*</td>

   <td width="61">*</td>

   <td width="61">*</td>

   <td width="61">.</td>

   <td width="8">.</td>

  </tr>

  <tr>

   <td width="167">add $t4,$t1,70 .</td>

   <td width="77">.</td>

   <td width="61">IF</td>

   <td width="61">ID</td>

   <td width="61">ID</td>

   <td width="61">EX</td>

   <td width="61">MEM</td>

   <td width="61">.</td>

   <td width="8">.</td>

  </tr>

  <tr>

   <td width="167">CPU Cycles ===&gt; 1</td>

   <td width="77">2</td>

   <td width="61">3</td>

   <td width="61">4</td>

   <td width="61">5</td>

   <td width="61">6</td>

   <td width="61">7</td>

   <td width="61">8</td>

   <td width="8">9</td>

  </tr>

  <tr>

   <td width="167">add $t1,$s0,$s0 IF</td>

   <td width="77">ID</td>

   <td width="61">EX</td>

   <td width="61">MEM</td>

   <td width="61">WB</td>

   <td width="61">.</td>

   <td width="61">.</td>

   <td width="61">.</td>

   <td width="8">.</td>

  </tr>

  <tr>

   <td width="167">add $t2,$s0,42 .</td>

   <td width="77">IF</td>

   <td width="61">ID</td>

   <td width="61">EX</td>

   <td width="61">MEM</td>

   <td width="61">WB</td>

   <td width="61">.</td>

   <td width="61">.</td>

   <td width="8">.</td>

  </tr>

  <tr>

   <td width="167">nop                                 .</td>

   <td width="77">.</td>

   <td width="61">IF</td>

   <td width="61">ID</td>

   <td width="61">*</td>

   <td width="61">*</td>

   <td width="61">*</td>

   <td width="61">.</td>

   <td width="8">.</td>

  </tr>

  <tr>

   <td width="167">add $t4,$t1,70 .</td>

   <td width="77">.</td>

   <td width="61">IF</td>

   <td width="61">ID</td>

   <td width="61">ID</td>

   <td width="61">EX</td>

   <td width="61">MEM</td>

   <td width="61">WB</td>

   <td width="8">.</td>

  </tr>

 </tbody>

</table>

END OF SIMULATION

The third example (i.e., ex03.s) includes two dependencies on register $t2.

<table width="0">

 <tbody>

  <tr>

   <td width="182">START OF SIMULATION</td>

   <td width="59"> </td>

   <td width="59"> </td>

   <td width="60"> </td>

   <td width="59"> </td>

   <td width="28"> </td>

   <td colspan="2" width="92"> </td>

   <td width="60"> </td>

   <td width="14"> </td>

   <td width="8"> </td>

  </tr>

  <tr>

   <td width="182">CPU Cycles ===&gt; 1</td>

   <td width="59">2</td>

   <td width="59">3</td>

   <td width="60">4</td>

   <td width="59">5</td>

   <td width="28">6</td>

   <td colspan="2" width="92">7</td>

   <td width="60">8</td>

   <td width="14">9</td>

   <td width="8"> </td>

  </tr>

  <tr>

   <td width="182">lw $t2,20($a0) IF</td>

   <td width="59">.</td>

   <td width="59">.</td>

   <td width="60">.</td>

   <td width="59">.</td>

   <td width="28">.</td>

   <td colspan="2" width="92">.</td>

   <td width="60">.</td>

   <td width="14">.</td>

   <td width="8"> </td>

  </tr>

  <tr>

   <td width="182">and $t4,$t2,$t5 .</td>

   <td width="59">.</td>

   <td width="59">.</td>

   <td width="60">.</td>

   <td width="59">.</td>

   <td width="28">.</td>

   <td colspan="2" width="92">.</td>

   <td width="60">.</td>

   <td width="14">.</td>

   <td width="8"> </td>

  </tr>

  <tr>

   <td width="182">or $t8,$t2,$t6 .</td>

   <td width="59">.</td>

   <td width="59">.</td>

   <td width="60">.</td>

   <td width="59">.</td>

   <td width="28">.</td>

   <td colspan="2" width="92">.</td>

   <td width="60">.</td>

   <td width="14">.</td>

   <td width="8"> </td>

  </tr>

  <tr>

   <td width="182">CPU Cycles ===&gt; 1</td>

   <td width="59">2</td>

   <td width="59">3</td>

   <td width="60">4</td>

   <td width="59">5</td>

   <td width="28">6</td>

   <td colspan="2" width="92">7</td>

   <td width="60">8</td>

   <td width="14">9</td>

   <td width="8"> </td>

  </tr>

  <tr>

   <td width="182">lw $t2,20($a0) IF</td>

   <td width="59">ID</td>

   <td width="59">.</td>

   <td width="60">.</td>

   <td width="59">.</td>

   <td width="28">.</td>

   <td colspan="2" width="92">.</td>

   <td width="60">.</td>

   <td width="14">.</td>

   <td width="8"> </td>

  </tr>

  <tr>

   <td width="182">and $t4,$t2,$t5 .</td>

   <td width="59">IF</td>

   <td width="59">.</td>

   <td width="60">.</td>

   <td width="59">.</td>

   <td width="28">.</td>

   <td colspan="2" width="92">.</td>

   <td width="60">.</td>

   <td width="14">.</td>

   <td width="8"> </td>

  </tr>

  <tr>

   <td width="182">or $t8,$t2,$t6 .</td>

   <td width="59">.</td>

   <td width="59">.</td>

   <td width="60">.</td>

   <td width="59">.</td>

   <td width="28">.</td>

   <td colspan="2" width="92">.</td>

   <td width="60">.</td>

   <td width="14">.</td>

   <td width="8"> </td>

  </tr>

  <tr>

   <td width="182">CPU Cycles ===&gt; 1</td>

   <td width="59">2</td>

   <td width="59">3</td>

   <td width="60">4</td>

   <td width="59">5</td>

   <td width="28">6</td>

   <td colspan="2" width="92">7</td>

   <td width="60">8</td>

   <td width="14">9</td>

   <td width="8"> </td>

  </tr>

  <tr>

   <td width="182">lw $t2,20($a0) IF</td>

   <td width="59">ID</td>

   <td width="59">EX</td>

   <td width="60">.</td>

   <td width="59">.</td>

   <td width="28">.</td>

   <td colspan="2" width="92">.</td>

   <td width="60">.</td>

   <td width="14">.</td>

   <td width="8"> </td>

  </tr>

  <tr>

   <td width="182">and $t4,$t2,$t5 .</td>

   <td width="59">IF</td>

   <td width="59">ID</td>

   <td width="60">.</td>

   <td width="59">.</td>

   <td width="28">.</td>

   <td colspan="2" width="92">.</td>

   <td width="60">.</td>

   <td width="14">.</td>

   <td width="8"> </td>

  </tr>

  <tr>

   <td width="182">or $t8,$t2,$t6 .</td>

   <td width="59">.</td>

   <td width="59">IF</td>

   <td width="60">.</td>

   <td width="59">.</td>

   <td width="28">.</td>

   <td colspan="2" width="92">.</td>

   <td width="60">.</td>

   <td width="14">.</td>

   <td width="8"> </td>

  </tr>

  <tr>

   <td width="182">CPU Cycles ===&gt; 1</td>

   <td width="59">2</td>

   <td width="59">3</td>

   <td width="60">4</td>

   <td width="59">5</td>

   <td width="28">6</td>

   <td colspan="2" width="92">7</td>

   <td width="60">8</td>

   <td width="14">9</td>

   <td width="8"> </td>

  </tr>

  <tr>

   <td width="182">lw $t2,20($a0) IF</td>

   <td width="59">ID</td>

   <td width="59">EX</td>

   <td width="60">MEM</td>

   <td width="59">.</td>

   <td width="28">.</td>

   <td colspan="2" width="92">.</td>

   <td width="60">.</td>

   <td width="14">.</td>

   <td width="8"> </td>

  </tr>

  <tr>

   <td width="182">nop                                 .</td>

   <td width="59">IF</td>

   <td width="59">ID</td>

   <td width="60">*</td>

   <td width="59">.</td>

   <td width="28">.</td>

   <td colspan="2" width="92">.</td>

   <td width="60">.</td>

   <td width="14">.</td>

   <td width="8"> </td>

  </tr>

  <tr>

   <td width="182">nop                                 .</td>

   <td width="59">IF</td>

   <td width="59">ID</td>

   <td width="60">*</td>

   <td width="59">.</td>

   <td width="28">.</td>

   <td colspan="2" width="92">.</td>

   <td width="60">.</td>

   <td width="14">.</td>

   <td width="8"> </td>

  </tr>

  <tr>

   <td width="182">and $t4,$t2,$t5 .</td>

   <td width="59">IF</td>

   <td width="59">ID</td>

   <td width="60">ID</td>

   <td width="59">.</td>

   <td width="28">.</td>

   <td colspan="2" width="92">.</td>

   <td width="60">.</td>

   <td width="14">.</td>

   <td width="8"> </td>

  </tr>

  <tr>

   <td width="182">or $t8,$t2,$t6 .</td>

   <td width="59">.</td>

   <td width="59">IF</td>

   <td width="60">IF</td>

   <td width="59">.</td>

   <td width="28">.</td>

   <td colspan="2" width="92">.</td>

   <td width="60">.</td>

   <td width="14">.</td>

   <td width="8"> </td>

  </tr>

  <tr>

   <td width="182">CPU Cycles ===&gt; 1</td>

   <td width="59">2</td>

   <td width="59">3</td>

   <td width="60">4</td>

   <td width="59">5</td>

   <td width="28">6</td>

   <td colspan="2" width="92">7</td>

   <td width="60">8</td>

   <td width="14">9</td>

   <td width="8"> </td>

  </tr>

  <tr>

   <td width="182">lw $t2,20($a0) IF</td>

   <td width="59">ID</td>

   <td width="59">EX</td>

   <td width="60">MEM</td>

   <td width="59">WB</td>

   <td width="28">.</td>

   <td colspan="2" width="92">.</td>

   <td width="60">.</td>

   <td width="14">.</td>

   <td width="8"> </td>

  </tr>

  <tr>

   <td width="182">nop                                 .</td>

   <td width="59">IF</td>

   <td width="59">ID</td>

   <td width="60">*</td>

   <td width="59">*</td>

   <td width="28">.</td>

   <td colspan="2" width="92">.</td>

   <td width="60">.</td>

   <td width="14">.</td>

   <td width="8"> </td>

  </tr>

  <tr>

   <td width="182">nop                                 .</td>

   <td width="59">IF</td>

   <td width="59">ID</td>

   <td width="60">*</td>

   <td width="59">*</td>

   <td width="28">.</td>

   <td colspan="2" width="92">.</td>

   <td width="60">.</td>

   <td width="14">.</td>

   <td width="8"> </td>

  </tr>

  <tr>

   <td width="182">and $t4,$t2,$t5 .</td>

   <td width="59">IF</td>

   <td width="59">ID</td>

   <td width="60">ID</td>

   <td width="59">ID</td>

   <td width="28">.</td>

   <td colspan="2" width="92">.</td>

   <td width="60">.</td>

   <td width="14">.</td>

   <td width="8"> </td>

  </tr>

  <tr>

   <td width="182">or $t8,$t2,$t6 .</td>

   <td width="59">.</td>

   <td width="59">IF</td>

   <td width="60">IF</td>

   <td width="59">IF</td>

   <td width="28">.</td>

   <td colspan="2" width="92">.</td>

   <td width="60">.</td>

   <td width="14">.</td>

   <td width="8"> </td>

  </tr>

  <tr>

   <td width="182">CPU Cycles ===&gt; 1</td>

   <td width="59">2</td>

   <td width="59">3</td>

   <td width="60">4</td>

   <td width="59">5</td>

   <td width="28">6</td>

   <td colspan="2" width="92">7</td>

   <td width="60">8</td>

   <td width="14">9</td>

   <td width="8"> </td>

  </tr>

  <tr>

   <td width="182">lw $t2,20($a0) IF</td>

   <td width="59">ID</td>

   <td width="59">EX</td>

   <td width="60">MEM</td>

   <td width="59">WB</td>

   <td width="28">.</td>

   <td colspan="2" width="92">.</td>

   <td width="60">.</td>

   <td width="14">.</td>

   <td width="8"> </td>

  </tr>

  <tr>

   <td width="182">nop                                 .</td>

   <td width="59">IF</td>

   <td width="59">ID</td>

   <td width="60">*</td>

   <td width="59">*</td>

   <td width="28">*</td>

   <td colspan="2" width="92">.</td>

   <td width="60">.</td>

   <td width="14">.</td>

   <td width="8"> </td>

  </tr>

  <tr>

   <td width="182">nop                                 .</td>

   <td width="59">IF</td>

   <td width="59">ID</td>

   <td width="60">*</td>

   <td width="59">*</td>

   <td width="28">*</td>

   <td colspan="2" width="92">.</td>

   <td width="60">.</td>

   <td width="14">.</td>

   <td width="8"> </td>

  </tr>

  <tr>

   <td width="182">and $t4,$t2,$t5 .</td>

   <td width="59">IF</td>

   <td width="59">ID</td>

   <td width="60">ID</td>

   <td width="59">ID</td>

   <td width="28">EX</td>

   <td colspan="2" width="92">.</td>

   <td width="60">.</td>

   <td width="14">.</td>

   <td width="8"> </td>

  </tr>

  <tr>

   <td width="182">or $t8,$t2,$t6 .</td>

   <td width="59">.</td>

   <td width="59">IF</td>

   <td width="60">IF</td>

   <td width="59">IF</td>

   <td width="28">ID</td>

   <td colspan="2" width="92">.</td>

   <td width="60">.</td>

   <td width="14">.</td>

   <td width="8"> </td>

  </tr>

  <tr>

   <td width="182">CPU Cycles ===&gt; 1</td>

   <td width="59">2</td>

   <td width="59">3</td>

   <td width="60">4</td>

   <td width="59">5</td>

   <td width="28">6</td>

   <td colspan="2" width="92">7</td>

   <td width="60">8</td>

   <td width="14">9</td>

   <td width="8"> </td>

  </tr>

  <tr>

   <td width="182">lw $t2,20($a0) IF</td>

   <td width="59">ID</td>

   <td width="59">EX</td>

   <td width="60">MEM</td>

   <td width="59">WB</td>

   <td width="28">.</td>

   <td colspan="2" width="92">.</td>

   <td width="60">.</td>

   <td width="14">.</td>

   <td width="8"> </td>

  </tr>

  <tr>

   <td width="182">nop                                 .</td>

   <td width="59">IF</td>

   <td width="59">ID</td>

   <td width="60">*</td>

   <td width="59">*</td>

   <td width="28">*</td>

   <td colspan="2" width="92">.</td>

   <td width="60">.</td>

   <td width="14">.</td>

   <td width="8"> </td>

  </tr>

  <tr>

   <td width="182">nop                                 .</td>

   <td width="59">IF</td>

   <td width="59">ID</td>

   <td width="60">*</td>

   <td width="59">*</td>

   <td width="28">*</td>

   <td colspan="2" width="92">.</td>

   <td width="60">.</td>

   <td width="14">.</td>

   <td width="8"> </td>

  </tr>

  <tr>

   <td width="182">and $t4,$t2,$t5 .</td>

   <td width="59">IF</td>

   <td width="59">ID</td>

   <td width="60">ID</td>

   <td width="59">ID</td>

   <td width="28">EX</td>

   <td colspan="2" width="92">MEM</td>

   <td width="60">.</td>

   <td width="14">.</td>

   <td width="8"> </td>

  </tr>

  <tr>

   <td width="182">or $t8,$t2,$t6 .</td>

   <td width="59">.</td>

   <td width="59">IF</td>

   <td width="60">IF</td>

   <td width="59">IF</td>

   <td width="28">ID</td>

   <td colspan="2" width="92">EX</td>

   <td width="60">.</td>

   <td width="14">.</td>

   <td width="8"> </td>

  </tr>

  <tr>

   <td width="182">CPU Cycles ===&gt; 1</td>

   <td width="59">2</td>

   <td width="59">3</td>

   <td width="60">4</td>

   <td width="59">5</td>

   <td colspan="2" width="59">6</td>

   <td width="60">7</td>

   <td width="60">8</td>

   <td colspan="2" width="21">9</td>

  </tr>

  <tr>

   <td width="182">lw $t2,20($a0) IF</td>

   <td width="59">ID</td>

   <td width="59">EX</td>

   <td width="60">MEM</td>

   <td width="59">WB</td>

   <td colspan="2" width="59">.</td>

   <td width="60">.</td>

   <td width="60">.</td>

   <td colspan="2" width="21">.</td>

  </tr>

  <tr>

   <td width="182">nop                                 .</td>

   <td width="59">IF</td>

   <td width="59">ID</td>

   <td width="60">*</td>

   <td width="59">*</td>

   <td colspan="2" width="59">*</td>

   <td width="60">.</td>

   <td width="60">.</td>

   <td colspan="2" width="21">.</td>

  </tr>

  <tr>

   <td width="182">nop                                 .</td>

   <td width="59">IF</td>

   <td width="59">ID</td>

   <td width="60">*</td>

   <td width="59">*</td>

   <td colspan="2" width="59">*</td>

   <td width="60">.</td>

   <td width="60">.</td>

   <td colspan="2" width="21">.</td>

  </tr>

  <tr>

   <td width="182">and $t4,$t2,$t5 .</td>

   <td width="59">IF</td>

   <td width="59">ID</td>

   <td width="60">ID</td>

   <td width="59">ID</td>

   <td colspan="2" width="59">EX</td>

   <td width="60">MEM</td>

   <td width="60">WB</td>

   <td colspan="2" width="21">.</td>

  </tr>

  <tr>

   <td width="182">or $t8,$t2,$t6 .</td>

   <td width="59">.</td>

   <td width="59">IF</td>

   <td width="60">IF</td>

   <td width="59">IF</td>

   <td colspan="2" width="59">ID</td>

   <td width="60">EX</td>

   <td width="60">MEM</td>

   <td colspan="2" width="21">.</td>

  </tr>

  <tr>

   <td width="182">CPU Cycles ===&gt; 1</td>

   <td width="59">2</td>

   <td width="59">3</td>

   <td width="60">4</td>

   <td width="59">5</td>

   <td colspan="2" width="59">6</td>

   <td width="60">7</td>

   <td width="60">8</td>

   <td colspan="2" width="21">9</td>

  </tr>

  <tr>

   <td width="182">lw $t2,20($a0) IF</td>

   <td width="59">ID</td>

   <td width="59">EX</td>

   <td width="60">MEM</td>

   <td width="59">WB</td>

   <td colspan="2" width="59">.</td>

   <td width="60">.</td>

   <td width="60">.</td>

   <td colspan="2" width="21">.</td>

  </tr>

  <tr>

   <td width="182">nop                                 .</td>

   <td width="59">IF</td>

   <td width="59">ID</td>

   <td width="60">*</td>

   <td width="59">*</td>

   <td colspan="2" width="59">*</td>

   <td width="60">.</td>

   <td width="60">.</td>

   <td colspan="2" width="21">.</td>

  </tr>

  <tr>

   <td width="182">nop                                 .</td>

   <td width="59">IF</td>

   <td width="59">ID</td>

   <td width="60">*</td>

   <td width="59">*</td>

   <td colspan="2" width="59">*</td>

   <td width="60">.</td>

   <td width="60">.</td>

   <td colspan="2" width="21">.</td>

  </tr>

  <tr>

   <td width="182">and $t4,$t2,$t5 .</td>

   <td width="59">IF</td>

   <td width="59">ID</td>

   <td width="60">ID</td>

   <td width="59">ID</td>

   <td colspan="2" width="59">EX</td>

   <td width="60">MEM</td>

   <td width="60">WB</td>

   <td colspan="2" width="21">.</td>

  </tr>

  <tr>

   <td width="182">or $t8,$t2,$t6 . END OF SIMULATION <strong>Assumptions</strong></td>

   <td width="59">.</td>

   <td width="59">IF</td>

   <td width="60">IF</td>

   <td width="59">IF</td>

   <td colspan="2" width="59">ID</td>

   <td width="60">EX</td>

   <td rowspan="2" width="60">MEM</td>

   <td colspan="2" rowspan="2" width="21">WB</td>

  </tr>

  <tr>

   <td colspan="8" width="538">Given the complexity of this assignment, you can make the following assumptions:• Assume all input files are valid.</td>

  </tr>

  <tr>

   <td width="182"></td>

   <td width="59"></td>

   <td width="59"></td>

   <td width="60"></td>

   <td width="59"></td>

   <td width="28"></td>

   <td width="32"></td>

   <td width="60"></td>

   <td width="60"></td>

   <td width="14"></td>

   <td width="8"></td>

  </tr>

 </tbody>

</table>

<ul>

 <li>Assume the length of argv[1] is at most 128 characters, but do not assume that argv[1] is present.</li>

</ul>

<h2>Error Checking</h2>

Given the complexity of this assignment, you can assume that the input file is valid. Be sure to verify that you have the correct number of arguments by checking argc; display an error message if argument(s) are missing.

In general, if an error occurs, use either perror() or fprintf( stderr, “…” ), depending on whether the global errno is set.

And be sure to return either EXIT_SUCCESS or EXIT_FAILURE upon program termination.