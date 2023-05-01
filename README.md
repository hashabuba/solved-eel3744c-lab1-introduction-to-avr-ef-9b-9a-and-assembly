Download Link: https://assignmentchef.com/product/solved-eel3744c-lab1-introduction-to-avr%ef%9b%9a-and-assembly
<br>
<h1>OBJECTIVES</h1>

<ul>

 <li>Become introduced to AVR assembly programming and the <em>ATxmega128A1U</em></li>

 <li>Further understand how to utilize <em>Atmel Studio</em> for creating, simulating, and emulating a program.</li>

 <li>Design an assembly program to filter and store data based on certain criteria.</li>

</ul>

<h1>INTRODUCTION</h1>

The foundation of every computer architecture is a specific set of operations. In general, each operation within a computer architecture can be referenced by a unique numeric value known as an <strong>op</strong>eration <strong>code</strong> (<strong>opcode</strong>)<a href="#_ftn1" name="_ftnref1"><strong><sup>[1]</sup></strong></a>, and the set of all operation codes for an architecture defines a low-level programming language often referred to as <strong>machine code</strong>. Additionally, an operation code is also generally given a symbolic name, classifying it as an <strong>instruction</strong>. The collection of all instructions for a given architecture then defines the most abstract level of the architecture, often referred to as the <strong>I</strong>nstruction <strong>S</strong>et <strong>A</strong>rchitecture (<strong>ISA</strong>), or more frequently, the <strong>assembly language</strong>.

With an assembly language, a <strong>computer program<a href="#_ftn2" name="_ftnref2"><sup>[2]</sup></a></strong> can be written much more quickly than with a machine code. However, for a given computer architecture to be able execute a program written in an assembly language, the program must first be converted into an appropriate machine code format with a pre-built software program often referred to as an <strong>assembler<a href="#_ftn3" name="_ftnref3"><sup>[3]</sup></a></strong>, and then stored into some appropriate computer memory.

<h1>LAB STRUCTURE</h1>

In this lab, you will start to gain familiarity with the <em>ATxmega128A1U</em> microcontroller (generally referred to in this course as the <em>XMEGA</em>) as well further understand how to leverage <em>Atmel Studio</em>. First, you will learn various fundamental information regarding the <em>ATxmega128A1U</em>, the AVR assembler, and <em>Atmel Studio</em>. Then, you will begin to utilize the AVR ISA to design your first AVR assembly language program. After creating this program, your microcontroller will be able to filter and store data based on several given conditions.




<h1>REQUIRED MATERIALS                                       SUPPLEMENTAL MATERIALS</h1>

<ul>

 <li><a href="https://mil.ufl.edu/3744/docs/XMEGA/doc8331_XMEGA_AU_Manual.pdf">Atmel XMEGA AU Manual (doc8331)</a> <a href="https://mil.ufl.edu/3744/docs/GCPU_to_ATxmega.pdf">Assembly Language Conversion: GCPU to AVR</a></li>

 <li><a href="https://mil.ufl.edu/3744/docs/XMEGA/doc8385_ATxmega128A1U_Manual.pdf">Atmel </a><a href="https://mil.ufl.edu/3744/docs/XMEGA/doc8385_ATxmega128A1U_Manual.pdf"><em>ATxmega128A1U</em></a><a href="https://mil.ufl.edu/3744/docs/XMEGA/doc8385_ATxmega128A1U_Manual.pdf"> Manual (doc8385)</a>           <a href="https://www.microchip.com/webdoc/GUID-ECD8A826-B1DA-44FC-BE0B-5A53418A47BD/"><em>Atmel Studio</em></a><a href="https://www.microchip.com/webdoc/GUID-ECD8A826-B1DA-44FC-BE0B-5A53418A47BD/"> User Guide</a></li>

 <li><a href="https://mil.ufl.edu/3744/docs/XMEGA/doc0856_AVR_Instruction_Set.pdf">AVR Instruction Set (doc0856)</a>           <a href="https://mil.ufl.edu/3744/docs/Watch_Atmel_Studio.pdf">Utilizing </a><a href="https://mil.ufl.edu/3744/docs/Watch_Atmel_Studio.pdf"><em>Watch</em></a><a href="https://mil.ufl.edu/3744/docs/Watch_Atmel_Studio.pdf"> in </a><a href="https://mil.ufl.edu/3744/docs/Watch_Atmel_Studio.pdf"><em>Atmel Studio</em></a></li>

 <li><a href="http://www.avr-tutorials.com/assembly/avr-assembler-directives">AVR Assembler Directives</a>           <a href="https://mil.ufl.edu/3744/docs/Atmel_Studio_Auto_Complete_for_ASM/Auto%20Complete%20Extension%20for%20Atmel%20Studio.pdf">Assembly Auto Complete Extension User Guide</a></li>

 <li><a href="http://mil.ufl.edu/3744/docs/XMEGA/doc1022_Assembler_Directives.pdf">AVR Assembler User Guide</a> <a href="https://mil.ufl.edu/3744/labs/lab1_u20_skeleton.asm">lab1_u20_skeleton.asm</a></li>

 <li><em>OOTB µPAD v2.0</em> with USB A/B cable</li>

 <li><strong>D</strong>igilent <strong>A</strong>nalog <strong>D</strong>iscovery (<strong>DAD</strong>) with <em>Waveforms </em>software</li>

</ul>




<h1>PRE-LAB PROCEDURE</h1>

<strong><u>REMINDER OF LAB POLICY</u></strong>

You must re-read the <a href="https://mil.ufl.edu/3744/admin/Lab%20Rules%20%26%20Policies.pdf"><em>Lab Rules &amp; Policies</em></a> before submitting any pre-lab assignment and before attending any lab.




Throughout this course, it will be necessary to conduct individual research. When doing so, various types of documentation, e.g., manuals, datasheets, application notes, and tutorials, will all be of interest.

Below, you will begin to become exposed to some important documentation relevant to this course, and will learn some basics regarding the <em>ATxmega128A1U </em>microcontroller, the AVR assembler, and <em>Atmel Studio</em>.

<ol>

 <li>Study §§ 1-4 of th<a href="https://mil.ufl.edu/3744/docs/XMEGA/doc8331_XMEGA_AU_Manual.pdf">e </a><a href="https://mil.ufl.edu/3744/docs/XMEGA/doc8331_XMEGA_AU_Manual.pdf">Atmel XMEGA AU Manual (doc8331)</a><a href="https://mil.ufl.edu/3744/docs/XMEGA/doc8331_XMEGA_AU_Manual.pdf">,</a> a more general user manual describing the XMEGA AU computer architecture. Additionally, study §§ 3, 6, and 7 of th<a href="https://mil.ufl.edu/3744/docs/XMEGA/doc8385_ATxmega128A1U_Manual.pdf">e </a><a href="https://mil.ufl.edu/3744/docs/XMEGA/doc8385_ATxmega128A1U_Manual.pdf">Atmel </a><a href="https://mil.ufl.edu/3744/docs/XMEGA/doc8385_ATxmega128A1U_Manual.pdf"><em>ATxmega128A1U</em></a><a href="https://mil.ufl.edu/3744/docs/XMEGA/doc8385_ATxmega128A1U_Manual.pdf"> Manual (doc8385)</a><a href="https://mil.ufl.edu/3744/docs/XMEGA/doc8385_ATxmega128A1U_Manual.pdf">,</a> the specific datasheet for the ATxmega128A1U microcontroller. Then, skim through the <a href="https://mil.ufl.edu/3744/docs/XMEGA/doc0856_AVR_Instruction_Set.pdf">AVR Instruction Set (doc0856)</a> to get an idea of the operations available to AVR microcontrollers. Next, read both the following <a href="http://www.avr-tutorials.com/assembly/avr-assembler-directives">webpage</a> and <a href="http://mil.ufl.edu/3744/docs/XMEGA/doc1022_Assembler_Directives.pdf">user guide</a> regarding the AVR assembler. Finally, look through the following <a href="https://www.microchip.com/webdoc/GUID-ECD8A826-B1DA-44FC-BE0B-5A53418A47BD/index.html?GUID-696C621E-EE89-4E38-88B6-B4E8B6D9F4B4">section</a> within the <a href="https://www.microchip.com/webdoc/GUID-ECD8A826-B1DA-44FC-BE0B-5A53418A47BD/"><em>Atmel Studio User Guide</em></a> regarding debugging.</li>

</ol>

<table width="356">

 <tbody>

  <tr>

   <td width="356"><strong><u>PRE-LAB EXERCISES</u></strong>i.         Go through your parts list (available at <a href="https://mil.ufl.edu/3744/docs/uPAD2pX/partsList_uPAD2p0_kit.pdf">here</a><a href="https://mil.ufl.edu/3744/docs/uPAD2pX/partsList_uPAD2p0_kit.pdf">)</a>. Identify any missing parts and report this to your PI and in your lab report. If all parts are there, indicate this in your lab report.ii.       Which type of memory alignment is used for program memory in the <em>ATxmega128A1U</em>? Byte-alignment, or word-alignment? What about for data memory?iii.     In which section of program memory is address 0xF0D0 located?iv.     Which assembler directive places a byte of data in program memory? Which assembler directive allocates space within data memory? Which assembler directives allow you to provide expressions (either constant or variable) with a meaningful name?v.       Which assembly instructions can be used to read from (flash) program memory? For each instruction, list which registers can be used as an operand.vi.     Which assembly instructions can be used to load data <em>indirectly</em> from data memory within XMEGA AU microcontrollers? Which assembly instructions can be used to store data <em>indirectly</em> to data memory?vii.    Which assembly instruction can be used to load data <em>directly</em> from the I/O memory of XMEGA AU microcontrollers? Which assembly instruction can be used to store data <em>directly</em> to the I/O memory?viii.  If you were to use the <em>Memory </em>debug window of <em>Atmel Studio</em> to verify that some datum was correctly stored at address 0xBADD within program memory of the <em>ATxmega128A1U</em>, which address would you specify within the debug window?</td>

  </tr>

 </tbody>

</table>

<ol>

 <li>When using the internal SRAM (not EEPROM), which memory locations can be utilized for the data segment (.dseg)? Why?</li>

 <li>Which is the first (i.e., lowest) <em>program memory</em> address that would require the relevant RAMP register to be changed from its initial value of zero? Why?</li>

 <li>In the context of pointing an index to a specific program memory address within an XMEGA AU architecture, explain why and how the address value should first be altered. Similarly, in the context of pointing an index to a specific data memory address, explain why the address value should not be altered.</li>

</ol>

Now, you will design your first AVR assembly language program, <strong>lab1.asm</strong>. A skeleton for this file is provided on our course website and is also available through the <em>Supplemental Materials </em>section of this document.

Overall, this program should filter data stored within a predefined input table based on a set of given conditions and store a subset of filtered values into an output table. More specifically, the following bulleted list describes an algorithm that should be performed on each item within the predefined input table, until an <strong>e</strong>nd-<strong>o</strong>f-<strong>t</strong>able (<strong>EOT</strong>) value of <em>NULL</em>, defined to be zero, is encountered within the table. Note that the algorithm should be executed in the same order as the bulleted list is provided, and for each iteration of the algorithm, only one of the three overall conditions within the bulleted list should be performed.

<ul>

 <li>If bit 6 of the 8-bit value is set, divide the value by 2. Then, if the resulting value is greater than 55, subtract 8 and store it to the first available location within the output table; otherwise, do not store anything to the output table.</li>

 <li>Else, if bit 6 is not set, multiply the value by 2. Then, if the resulting value of the data is less than or equal to 114, add 191 and store this result to the first available location within the output table.</li>

</ul>

The following are additional specifications for the program:

<ul>

 <li>The input table should be placed in program memory, starting at address 0xABCD, and should consist of the 8-bit data provided in the left-hand of Table 1 (given on the following page), where each value in this column should be stored sequentially in memory, without any padding, in the same format provided. (Data is given in decimal, hexadecimal, binary, octal, and ASCII formats to demonstrate that <em>Atmel Studio </em>can interpret values in each of these given formats.)</li>

 <li>An output table should be allocated within data memory, starting at address 0x3700.</li>

 <li>All values should be interpreted as unsigned, i.e., instructions that interpret data as a signed value (e.g., BRLT, BRGE, etc.) should not be utilized.</li>

 <li>Upon finding the EOT value within the input table, the output table should be terminated with a NULL character.</li>

</ul>

<strong>Table 1:</strong> Memory Table

<table width="199">

 <tbody>

  <tr>

   <td width="86"><strong>Data </strong></td>

   <td width="113"><strong>Data (ASCII)<sup>1</sup> </strong></td>

  </tr>

  <tr>

   <td width="86">99</td>

   <td width="113">c</td>

  </tr>

  <tr>

   <td width="86">0x3B</td>

   <td width="113">;</td>

  </tr>

  <tr>

   <td width="86">0164</td>

   <td width="113">t</td>

  </tr>

  <tr>

   <td width="86">0b00111111</td>

   <td width="113">?</td>

  </tr>

  <tr>

   <td width="86">0x44</td>

   <td width="113">D</td>

  </tr>

  <tr>

   <td width="86">0x55</td>

   <td width="113">U</td>

  </tr>

  <tr>

   <td width="86">‘p’</td>

   <td width="113">p</td>

  </tr>

  <tr>

   <td width="86">0112</td>

   <td width="113">J</td>

  </tr>

  <tr>

   <td width="86">‘t’</td>

   <td width="113">t</td>

  </tr>

  <tr>

   <td width="86">0b00111010</td>

   <td width="113">:</td>

  </tr>

  <tr>

   <td width="86">‘&lt;’</td>

   <td width="113">&lt;</td>

  </tr>

  <tr>

   <td width="86">0x39</td>

   <td width="113">9</td>

  </tr>

  <tr>

   <td width="86">0x57</td>

   <td width="113">W</td>

  </tr>

  <tr>

   <td width="86">49</td>

   <td width="113">1</td>

  </tr>

  <tr>

   <td width="86">100</td>

   <td width="113">d</td>

  </tr>

  <tr>

   <td width="86">0</td>

   <td width="113">NULL</td>

  </tr>

 </tbody>

</table>

<sup>1</sup>ASCII format supported by <em>Atmel Studio </em>

If the program is written as specified above, the resulting output table should contain the message “<em>2021!</em>” (an exclamation for a better year) when the relevant data is viewed in terms of the ASCII encoding format supported by <em>Atmel Studio</em>. To view the data in this format, a <em>Memory</em> debug window within <em>Atmel Studio </em>should be utilized.

<strong>NOTES:</strong>

<ul>

 <li>The second column of Table 1 provides the relevant input table data in terms of the ASCII encoding format supported by <em>Atmel Studio</em>, simply to allow ease of verification if debugging with a <em>Memory</em> view window in <em>Atmel Studio</em>. (In general, ASCII provides a standard set of encoded values, often in terms of seven bits although sometimes in terms of eight bits if additional symbols are supported, for</li>

</ul>

<strong> </strong>

<table width="356">

 <tbody>

  <tr>

   <td width="356">commonly used symbols in human language. An example ASCII table can be found at <a href="http://www.asciitable.com/">www.asciitable.com</a><a href="http://www.asciitable.com/">.</a>)v  In order to make your code modular and portable (i.e., able to be reused in different contexts), utilize assembler directives. For example, use assembler directives to create constant or variable identifiers for pertinent memory addresses within your input/output tables, for EOT values, etc.v  A <em>Watch</em> window, available under <em>Debug | Windows | Watch </em>within <em>Atmel Studio</em>, is used to view memory locations while debugging a program; to learn more about <em>Watch </em>windows, navigate to <em>Debugging | Memory View</em> within the <a href="https://www.microchip.com/webdoc/GUID-ECD8A826-B1DA-44FC-BE0B-5A53418A47BD/index.html?GUID-F1B6FDAB-FFC7-4555-BDF3-F3930C082061"><em>Atmel Studio</em></a><a href="https://www.microchip.com/webdoc/GUID-ECD8A826-B1DA-44FC-BE0B-5A53418A47BD/index.html?GUID-F1B6FDAB-FFC7-4555-BDF3-F3930C082061"> User Guide</a><a href="https://www.microchip.com/webdoc/GUID-ECD8A826-B1DA-44FC-BE0B-5A53418A47BD/index.html?GUID-F1B6FDAB-FFC7-4555-BDF3-F3930C082061">,</a> as well as to the <a href="https://mil.ufl.edu/3744/docs/Watch_Atmel_Studio.pdf">Using</a><a href="https://mil.ufl.edu/3744/docs/Watch_Atmel_Studio.pdf"><em> Watch </em></a><a href="https://mil.ufl.edu/3744/docs/Watch_Atmel_Studio.pdf">in</a> <a href="https://mil.ufl.edu/3744/docs/Watch_Atmel_Studio.pdf"><em>Atmel Studio</em></a> <a href="https://mil.ufl.edu/3744/docs/Watch_Atmel_Studio.pdf">d</a>ocument located on the course website, listed under <em>Software/Docs</em>.v  To facilitate programming in the AVR assembly language within <em>Atmel Studio</em>, it is recommended that you install the <em>Auto Complete Extension </em>created by a former <em>3744</em> student. To learn how to do so, refer to the <em>Supplemental Materials </em>section of this document.</td>

  </tr>

 </tbody>

</table>

<ol>

 <li>Make a flowchart or write pseudocode for the above program. (This is required for <strong>ALL </strong>lab programs and may not be specifically requested in future lab documents.)</li>

 <li>Create the relevant assembly language program, <strong>asm</strong>, as specified above. A skeleton for this file is provided on our course website and is also available through the <em>Supplemental Materials </em>section of this document.</li>

 <li>Test your program using the <em>Atmel Studio</em> software simulator. Utilize debugging tools to verify that the program works as specified.</li>

 <li>Emulate the program on your <em>µPAD</em> to verify that the program also works on your hardware. Utilize the same debugging tools.</li>

 <li>Take a screenshot of a <em>Memory</em> view window after executing the relevant program, showing the entire output table at the appropriate memory locations.</li>

</ol>




<strong><u>PRE-LAB PROCEDURE SUMMARY</u></strong>

1) Read the specified sections within the relevant documentation. 2) Answer all pre-lab exercises.

<ul>

 <li>Make a flowchart or write pseudocode for the described program.</li>

 <li>Write the relevant assembly program, <strong>asm</strong>. Verify its correctness.</li>

 <li>Capture a screenshot of a <em>Memory </em>view window displaying the resulting output table after executing the program.</li>

</ul>

<a href="#_ftnref1" name="_ftn1">[1]</a> Operation codes are often represented in terms of fields of zeroes and ones, otherwise referred to as <strong>bit fields</strong>, where these fields represent a unique, encoded binary number. For hardware to handle bit fields, some form of encoding/decoding circuitry must be utilized.

<a href="#_ftnref2" name="_ftn2">[2]</a> A <strong>program</strong>, or <strong>program of execution</strong>, is a collection of either computer instructions or operation codes that direct which operations a computer is to perform.

<a href="#_ftnref3" name="_ftn3">[3]</a> Normally, assemblers are paired with an additional software program, generally known as a <strong>preprocessor</strong>, to recognize additional keywords, known as <strong>assembler directives</strong>, which specify actions to be performed directly by the assembler (and not by the computer for which the code is assembled).