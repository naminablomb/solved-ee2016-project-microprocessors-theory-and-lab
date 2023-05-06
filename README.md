Download Link: https://assignmentchef.com/product/solved-ee2016-project-microprocessors-theory-and-lab
<br>
To implement a fully functioning controller for a washing machine using AVR ATMEL ATmega8 Microcontroller. With the given inputs and outputs, write a program (assembly or C) and implement hardware emulation in the lab.

2          Engineering Problem

<h3>2.1            Basic operation sequence of a washing machine :-</h3>

There are 4 relays to be controlled in a regular sequence. The basic operation sequence is as follows

<ol>

 <li>Water filling (at actual time)</li>

 <li>Agitronic soak (15mins)</li>

 <li>First wash (15mins)</li>

 <li>First drain (4mins)</li>

 <li>Second wash or first rinse (10mins)</li>

 <li>Second drain (4mins)</li>

 <li>Spin (5mins)</li>

 <li>Buzzer chim (15sec)</li>

</ol>

<h3>2.2        Design Specifications</h3>

This includes both hardware and software specifications.

<ol>

 <li>The system should have three load conditions: <em>Soft</em>, <em>Medium </em>and <em>Heavy</em>. The user should be able to choose one.</li>

 <li>The system should have three tasks to choose from : <em>Washing only</em>, <em>Drying only </em>and <em>Washing + Drying</em>. These options should be made available for user input.</li>

 <li>The system should have two external interrupts. One interrupt acting as a “pause” button and theother as a “Lid open” interrupt.</li>

 <li>When the Pause interrupt is triggered, the user should be able to reset the load, washing cycle inputs.After the new inputs are given, the system should abandon the previous washing cycle and start off the new washing cycle.</li>

 <li>When the lid is open, the system should stop its functioning. Only after ensuring that lid is closed, theoperation may continue from where it left off.</li>

</ol>

<h2>3         Problem Definition</h2>

<strong>Inputs</strong>

<table width="572">

 <tbody>

  <tr>

   <td rowspan="3" width="169"><strong>Load Condition of the</strong><strong>Washing Machine</strong><strong>(Through Switches)</strong></td>

   <td width="246">Soft</td>

   <td width="63">A.0</td>

   <td width="94"> </td>

  </tr>

  <tr>

   <td width="246">Medium</td>

   <td width="63">A.1</td>

   <td width="94"> </td>

  </tr>

  <tr>

   <td width="246">Heavy</td>

   <td width="63">A.2</td>

   <td width="94"> </td>

  </tr>

  <tr>

   <td rowspan="3" width="169"><strong>Task to perform</strong><strong>(Through Switches)</strong></td>

   <td width="246">Washing &amp; Drying</td>

   <td width="63">A.4</td>

   <td width="94"> </td>

  </tr>

  <tr>

   <td width="246">Washing Only</td>

   <td width="63">A.5</td>

   <td width="94"> </td>

  </tr>

  <tr>

   <td width="246">Drying Only</td>

   <td width="63">A.6</td>

   <td width="94"> </td>

  </tr>

  <tr>

   <td width="169"> </td>

   <td width="246"><strong>Outputs (Displayed using LED’s)</strong></td>

   <td width="63"> </td>

   <td width="94"> </td>

  </tr>

  <tr>

   <td width="169">Soft</td>

   <td width="246">Green LED will glow throughout the operation</td>

   <td width="63">B.0</td>

   <td width="94"> </td>

  </tr>

  <tr>

   <td width="169">Medium</td>

   <td width="246">Blue LED will glow throughout the operation</td>

   <td width="63">B.1</td>

   <td width="94"> </td>

  </tr>

  <tr>

   <td width="169">Heavy</td>

   <td width="246">White LED will glow throughout the operation</td>

   <td width="63">B.2</td>

   <td width="94"> </td>

  </tr>

  <tr>

   <td width="169">Washing (Soft load)</td>

   <td width="246">Two LED’s will glow for 2 seconds each for 3 times with a gap of 2 seconds</td>

   <td width="63">B.4,B.5</td>

   <td width="94"> </td>

  </tr>

  <tr>

   <td width="169">Washing (Medium load)</td>

   <td width="246">Two LED’s will glow for 2 seconds each for 5 times with a gap of 2 seconds</td>

   <td width="63">B.4,B.5</td>

   <td width="94"> </td>

  </tr>

  <tr>

   <td width="169">Washing (Heavy load)</td>

   <td width="246">Two LED’s will glow for 2 seconds each for 7 times with a gap of 2 seconds</td>

   <td width="63">B.4,B.5</td>

   <td width="94"> </td>

  </tr>

  <tr>

   <td width="169">Drying (Soft load)</td>

   <td width="246">Two Red LED’s will glow for 4 seconds</td>

   <td width="63">B.6</td>

   <td width="94"> </td>

  </tr>

  <tr>

   <td width="169">Drying (Medium load)</td>

   <td width="246">Two Red LED’s will glow for 8 seconds</td>

   <td width="63">B.7</td>

   <td width="94"> </td>

  </tr>

  <tr>

   <td width="169">Drying (Heavy load)</td>

   <td width="246">Two Red LED’s will glow for 12 seconds</td>

   <td width="63">B.8</td>

   <td width="94"> </td>

  </tr>

 </tbody>

</table>

<strong>After all the desired operations have been completed, sound a buzzer for 2 seconds indicating that the washing/drying cycle has been completed.</strong>

<strong>Program Flow</strong>

<ol>

 <li>The inputs are the load condition of the washing machine (soft, medium, heavy) and the task to perform(washing &amp; drying, washing only, drying only), which is given by the user. The user enters the inputs through the switches which comes to the assigned ports (Please note port numbers can be changed after checking the datasheet).</li>

 <li>As mentioned in the above table, for the required inputs perform the required tasks and display theoutputs using LED’s.</li>

 <li>There is an extra input through a push switch corresponding to the <strong>Start button </strong>in the washing machine. This switch doubles up as a pause button which goes to the <strong>interrupt pin </strong>of the microcontroller.</li>

 <li>If the user presses the pause button, an <strong>interrupt </strong>will come and he/she can change any of the above inputs, i.e. he/she can change the load condition or the task to perform.</li>

 <li>Then according to the above changed rule, the washing machine has to perform the activity and displaythe output.</li>

</ol>

<strong>Notes: </strong>The time delays in the program must be performed through timers in the microcontroller.

<h2>4         Hardware Setup</h2>

We herewith give the ATmega8 break out board with 6 inputs and 4 outputs. Here is the schematic diagram of controller. This is for your reference only and not the actual schematic that is to be implemented by you. Understand the problem and make a flowchart of the operations (along with interrupts).

List out all the input and output devices you require for the project. The codes may be written in assembly language or C.

<h2>5       References</h2>

<ol>

 <li>Washing Machine Controller Using AVR ATMEL ATmega8 Microcontroller Using Assembly Languagehttp://vu3xvr.blogspot.com/2016/03/washing-machine-controller-using-avr.html</li>

 <li>https://www.youtube.com/watch?time_continue=201&amp;v=iCkHyHlh5oI</li>

 <li>https://www.beestarlabel.com/Content/Files/Schedule12-WM.pdf</li>

 <li>https://pic-microcontroller.com/embedded-system-for-automatic-washing-machine-using-microchip-pic18fseries-microcontroller/</li>

</ol>