Download Link: https://assignmentchef.com/product/solved-csci1933-project-1-battleboats-game
<br>
<h1>Instructions</h1>

Please read and understand these expectations thoroughly. Failure to follow these instructions could negatively impact your grade. Rules detailed in the course syllabus also apply but will not necessarily be repeated here.

<ul>

 <li><strong>Identification: </strong>Place you and your partner’s x500 in a comment in all files you submit. For example, //Written by shino012 and hoang159.</li>

 <li><strong>Submission: </strong>Submit a zip or tar archive on Moodle containing all your java You are allowed to change or modify your submission, so submit early and often, and <em>verify that all your files are in the submission</em>.</li>

</ul>

Failure to submit the correct files will result in a score of zero for all missing parts. Late submissions and submissions in an abnormal format (such as .rar or .java) will be penalized. Only submissions made via Moodle are acceptable.

<ul>

 <li><strong>Partners: </strong>You may work alone or with <em>one </em> <strong>Failure to tell us who is your partner is indistinguishable from cheating and you will both receive a zero</strong>. Ensure all code shared with your partner is private.</li>

 <li><strong>Code: </strong>We will be using unit tests to grade parts of this project. This means you must follow and specified modifiers and signatures exactly as they are specified. Also your code must be reasonably clean, well-designed, and commented thoroughly. Your code may receive a penalty if it is confusing or demonstrates poor knowledge of Java. Code that doesn’t compile will receive a significant penalty. Code should be compatible with Java 8, which is installed on the CSE Labs computers.</li>

 <li><strong>Extra Work: </strong>If you enjoy this project and want to add extra features, please document the extra features thoroughly and allow them to be disabled for grading purposes. Mystery features we don’t understand could cause grading issues. Extra work may result in a maximum of 5 percent extra credit on this project grade – at the discretion of your TAs and professor.</li>

 <li><strong>Questions: </strong>Questions related to the project can be discussed on Moodle in abstract. This relates to programming in Java, understanding the writeup, and topics covered in lecture and labs. <strong>Do not post any code or solutions on the forum</strong>. Do not e-mail the TAs your questions when they can be asked on Moodle.</li>

 <li><strong>Grading: </strong>Grading will be done by the TAs, so please address grading problems to them (e.g.</li>

</ul>

via the email alias or at office hours).

INTRODUCTION

<h1>Introduction</h1>

Battleboat is a probability-based boardgame that challenges the user to locate enemy boats hidden on a rectangular grid. The purpose of the game is to locate and destroy every enemy boat in the least number of guesses.

You will be modelling this game in Java. <strong>You must implement every part of the description below. This means you must follow and specified modifiers and signatures exactly as they are specified. </strong>Examples of changes that could lose you points: changing a variable to public when it is listed as private, changing the return type of a function, etc.

Your code will also be judged based on style. This should not be a stressful requirement – it simply means that you must create logically organized, well-named and well-commented code so the TAs can grade it.

IMPORTANT: You cannot import anything to help you complete this project. The only exception is importing Scanner to handle the I/O. Note that you do not have to explicitly import Math because Java already does it for you. In other words, you can use Math methods without importing Math

Note: Writing useful helper methods for the functions listed above is allowed and encouraged! Remember part of your grade comes from style and readability of the code you write.

Note: You will find it useful to write your own tests to prove to yourself that your code works. <strong>Please include any test classes you write with your submission</strong>.

<h1>1           Cell Class</h1>

The Battleboats game board is composed of many cells. You are required to create a Cell class that contains the following private attributes:

<ul>

 <li>private int row: indicates the row value of the Cell</li>

 <li>private int col: indicates the column value of the Cell</li>

 <li>private char status: character indicating the status of the Cell. There are four different possibilities for this field:</li>

</ul>

<ol start="2">

 <li>BATTLEBOAT CLASS</li>

</ol>

<table width="340">

 <tbody>

  <tr>

   <td width="79">Character</td>

   <td width="261">Conditions</td>

  </tr>

  <tr>

   <td width="79">’ ’ (space)</td>

   <td width="261">Has not been guessed, no boat present</td>

  </tr>

  <tr>

   <td width="79">’B’</td>

   <td width="261">Has not been guessed, boat present</td>

  </tr>

  <tr>

   <td width="79">’H’</td>

   <td width="261">Has been guessed, boat present</td>

  </tr>

  <tr>

   <td width="79">’M’</td>

   <td width="261">Has been guessed, no boat present</td>

  </tr>

 </tbody>

</table>

In addition, you are required to implement the following functions:

<ul>

 <li>public char get_status(): getter method for status attribute</li>

 <li>public void set_status(char c): setter method for status attribute</li>

 <li>public Cell(int row, int col, char status): Cell class constructor</li>

</ul>

<h1>2           Battleboat Class</h1>

A Battleboat object will have the following attributes:

<ul>

 <li>private int size: indicates the number of Cell objects a Battleboat Default this value to 3</li>

 <li>private boolean orientation: indicates the orientation of the Battleboat (horizontal or vertical, can be randomly decided)</li>

 <li>private Cell[] spaces: array of the Cell objects associated with the Battleboat And the following functions:</li>

 <li>public boolean get_orientation(): getter method for orientation attribute</li>

 <li>public int get_size(): getter method for size attribute</li>

 <li>public Cell[] get_spaces(): getter method for spaces attribute</li>

 <li>public Battleboat(): Battleboat class constructor</li>

</ul>

Hint: To generate random numbers, the Math.random() method can be used. However, this method returns a double in the range 0 to 1. We will need to scale this and then round it to a whole. To do this, use the Math.floor(x) function, which takes a double x and rounds it down to the nearest integer. For example, Math.floor(2.9) is 2.

<ol start="3">

 <li>BOARD CLASS</li>

</ol>

<h1>3           Board Class</h1>

The computer will simulate a rectangular <em>m</em>×<em>n </em>board. A Board object will contain the following:

<ul>

 <li>private int num_rows: indicates the number of rows a Board has</li>

 <li>private int num_columns: indicates the number of columns a Board has</li>

 <li>private int num_boats: indicates the number of Battleboat objects a Board has</li>

 <li>private Battleboat[] boats: array of all the Battleboat objects associated with a Board object</li>

 <li>private Cell[][] board: 2-dimensional Cell array required to represent the Board</li>

 <li>private boolean debugMode: flag to indicate if Board should be printed in debugMode</li>

</ul>

The minimum Board size is 3 × 3 and the maximum is 12 × 12. Assume that the points in the Board range from (0<em>,</em>0) to (<em>m </em>− 1<em>,n </em>− 1) inclusive.

Each boat is represented by a line of consecutive squares on the board. Boats may not overlap other boats, extend outside the game board, or be placed diagonally. They may be horizontal or vertical. A boat is considered “sunk” when all the squares of the boat have been “hit” by the user.

Examples: Valid coordinates for a boat of size 3 are {(0<em>,</em>0)<em>,</em>(0<em>,</em>1)<em>,</em>(0<em>,</em>2)} and {(1<em>,</em>1)<em>,</em>(2<em>,</em>1)<em>,</em>(3<em>,</em>1)}. Examples of invalid coordinates are {(0<em>,</em>0)<em>,</em>(0<em>,</em>1)}, which is invalid because there are not enough points. {(0<em>,</em>0)<em>,</em>(0<em>,</em>2)<em>,</em>(0<em>,</em>3)} is invalid because the points are not consecutive. {(−1<em>,</em>0)<em>,</em>(0<em>,</em>0)<em>,</em>(1<em>,</em>0)} is invalid because the first coordinate is out of bounds.

Finally, two boats cannot contain the same point because they cannot overlap.

After the gameboard has been sized, <strong>the program should place boats randomly on the board</strong>. This requires randomly generating a coordinate (<em>x,y</em>) where the boat will be placed as well as randomly choosing whether the boat should be horizontal or vertical. The quantity of boats is defined by the width and height of the game board. As mentioned prior, all boats should be of length 3. Recall the smallestBoardis 3 × 3 and the largestBoardis 12 × 12.

<table width="391">

 <tbody>

  <tr>

   <td width="283">Smallest Dimension</td>

   <td width="108">Boat Quantity</td>

  </tr>

  <tr>

   <td width="283">width == 3 or height == 3</td>

   <td width="108">1</td>

  </tr>

  <tr>

   <td width="283">3 &lt; width &lt;= 5 or 3 &lt; height &lt;= 5</td>

   <td width="108">2</td>

  </tr>

  <tr>

   <td width="283">5 &lt; width &lt;= 7 or 5 &lt; height &lt;= 7</td>

   <td width="108">3</td>

  </tr>

  <tr>

   <td width="283">7 &lt; width &lt;= 9 or 7 &lt; height &lt;= 9</td>

   <td width="108">4</td>

  </tr>

  <tr>

   <td width="283">9 &lt; width &lt;= 12 or 9 &lt; height &lt;= 12</td>

   <td width="108">6</td>

  </tr>

 </tbody>

</table>

<ol start="4">

 <li>THE MAIN METHOD AND DEBUG MODE</li>

</ol>

Use the table above to determine how many boats to place. Recall that the Board may be rectangular, so a Board that is 9 × 3 should have just one boat of length 3 (the first case). The user should be told how many boats are on the Board when the game begins.

Hint: To randomly place a boat, consider the coordinate in the upper left. If the upper left corner was (0<em>,</em>0), consider how the boat looks if it is horizontal or vertical. What upper left corner coordinates are invalid? The placing of the boats may be the most challenging aspect of this project: see what assumptions you can make to simplify it.

Required functions:

<ul>

 <li>public Board(int m , int n, boolean debugMode): constructor for theBoard This method should assign appropriate number of boats to num_boats variable, initialize theBoard as a 2-D Cell array, initialize boats as a Battleboat array, place Battleboat objects appropriately on the Board, and add them to the board’s boats</li>

 <li>public int guess(int r, int c): returns an int based on the guess for the cell. The statuses of the Cell must also be changed according reflect the statuses from the table in the Cell class portion of this writeup</li>

 <li>public int unsunkBoats(): calculates the number of unsunk boats on the Board</li>

</ul>

<h1>4           The main method and debug mode</h1>

A main method is provided to you in the Game class which will run the game once all the functions are implemented as specified. If the debugMode flag is set to false, the view of the board will be obscured during play so that the player only sees the spots they have already guessed. Setting debugMode to true may be helpful to you while debugging and testing your code.

<h1>5           Honors</h1>

Now that you have a working Battleboats game, let’s make it a bit more interesting. In addition to guessing a cell location, the user will have the option to utilize a recon “drone” to reveal a 3×3 area centered around the input location. You will have to edit the main method to do so, and it should be plain to the user what must be done to use the drone.

Using the drone should increment the number of guesses by 4 as a penalty. If the 3×3 area exceeds the boundaries of the board, the user is still penalized the 4 guesses, but the area is not revealed.