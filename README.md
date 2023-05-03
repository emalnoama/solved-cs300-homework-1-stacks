Download Link: https://assignmentchef.com/product/solved-cs300-homework-1-stacks
<br>
In this homework, first, you will implement a program which will generate a random maze of size MxN, where M represents the number of rows, and N represents the number of columns. Then, you will also need to implement a function which will find the path between designated entry and exit points in a given maze.

To do this homework, you are required to implement a <strong>Stack</strong>​ using a <strong>LinkedList</strong>​ data structure, i.e., you can not use vectors in the stack implementation. The stack class <strong>MUST</strong>​ be a template-based class. You may want to store basic data types, structs or classes in this stack.

<h3>The Maze</h3>

The mazes are presented as MxN (M rows and N columns) 2D vectors as given below. The left bottom of the mazes are considered to be the (0,0) coordinate. There are 2 important rules for a given 2D vector to be a maze:

<ul>

 <li>Every cell must be reachable from any other cell.</li>

 <li>The reachability of cells from one to another must be unique, i.e., there must be only <strong><u>one</u></strong><u>​</u> path<u>​</u> from a cell to another.</li>

</ul>

Some example mazes of size 5×5 and 3×6 can be found below. Note there are no entry or exit points yet.

<table width="624">

 <tbody>

  <tr>

   <td width="336"> </td>

   <td width="288"> </td>

  </tr>

  <tr>

   <td width="336"> </td>

   <td width="288"></td>

  </tr>

 </tbody>

</table>




We also share some invalid maze examples below. In both mazes, for some cell pairs (c1 ,c2), there are more than one path to reach from c1 to c2.

<table width="624">

 <tbody>

  <tr>

   <td width="320"> </td>

   <td width="304"> </td>

  </tr>

 </tbody>

</table>




<strong> </strong>

<h1>Program Flow</h1>

There are 2 phases of this homework;

<ol>

 <li>The maze generation.</li>

 <li>Finding a path for given entry and exit points.</li>

</ol>

In both phases, you <strong>MUST</strong>​ use the stacks to solve the problem!​

<h2>The maze generation</h2>

In this phase, you need to generate K random MXN mazes using stacks for given M, N and K values. The general idea to generate a maze is to knock down walls between 2 cells, iteratively, until no unvisited cell remains. Hence, you need to knock down exactly MxN-1 walls. In each step, the maze rules (given above in the maze definition) must apply all the time.

The basic steps are:

<ol>

 <li>Start with an initially empty stack.</li>

 <li>Push (0,0) cell to your stack.</li>

 <li>Use the top element (currentCell) in the stack to choose the next cell to be added to your maze.</li>

 <li>Choose a <u>random</u>​ wall of the currentCell to add a new unvisited cell to the maze.​</li>

 <li>Knock down the wall and add the new cell to the stack.</li>

 <li>If no wall exists to knock down for the currentCell, backtrack using the stack until you find a cell which has an unvisited neighbour cell.</li>

 <li>Continue steps 3-6 until no cell remains unvisited.</li>

</ol>

<h2>Path discovery in a maze</h2>

Finding a path is almost the same as the maze generation process. First, the program will ask the user which maze should be chosen among the ones generated in the first phase. Then, the program;

<ol>

 <li>Start with an initially empty stack.</li>

 <li>Push the entry cell to your stack (will be entered by the user).</li>

 <li>Use the top element in the stack to choose the next cell to visit.</li>

 <li>If you cannot find any cell to go, backtrack using the stack until you find an unvisited cell to go.</li>

 <li>Continue steps 3-4 until you reach the exit point. Note that the path generated in this phase <strong>MUST</strong>​ be unique!​   <strong>You can assume that: </strong></li>

</ol>

<ul>

 <li>All the inputs entered by the user are valid, you do not need to validate them.</li>

 <li>The entry and exit points of the mazes are on the edges or corners of the mazes.</li>

</ul>




<h2>Input and Output</h2>

In the first phase, your program will ask the user to enter 3 inputs, namely, K, M, and N. You can assume that M and N are greater than 1, and K is a positive integer. However, your program should be able to generate huge mazes, too.

You will write your mazes into a file named as maze_mazeID.txt, where mazeID will go from 1 to K such as maze_1.txt and maze_4.txt. Your output format must be <strong><u>exactly</u></strong>​<strong><u> the same format</u></strong> as we give below. In the first line, sizes of the maze, M and N, must be given. In the following lines, for each cell, the x and y coordinates of the cell, as well as the walls of the cell, must be given. If there is a wall on the left (l), right (r), up (u), or down (d), assign 1 to the wall, if not, assign 0. For example, in the maze_1.txt below, at (0,0) cell, there are walls on the left, right and down side, but not on the up side.  <strong>maze_1.txt </strong>

5 4

x=0 y=0 l=1 r=1 u=0 d=1

x=1 y=0 l=1 r=0 u=1 d=1 x=2 y=0 l=0 r=0 u=1 d=1

…




In the second phase (after the mazes are generated), your program will ask the user to enter 5 more inputs; mazeID, entryX, entryY, exitX, and exitY. Maze ID will be a number between 1 and K, i.e., 1 &lt;= mazeID &lt;= K, indicating the specific mazes that are generated in the first phase to be traveled. For example, if mazeID = 3, then, the program needs to find a path for the third maze. entryX and entryY are the coordinates for entry point, and exitX and exitY are the coordinates for the exit point. <u>Note</u>​<u> that, y</u> <u>coordinates becomes the row of the maze and x coordinates becomes the column of the maze. For</u> <u>instance, the point (2,4) refers to the 4th row and 2nd column of the maze.</u>

The output will be written to a file named as maze_mazeID_path_entryX_entryY_exitX_exitY.txt. For instance, for the maze with mazeID = 2, entry = (0,0) and exit = (3,4), the file name will be maze_2_path_0_0_3_4.txt.

In the output file, the coordinates of the cells to get the exit point from entry point must be written line by line. See example output file below: <strong>maze_2_path_0_0_3_4.txt </strong>

0 0

…

…

3 4




<strong> </strong>

<h2>Debugging your code</h2>

We will provide a mazeDrawer program (mazeDrawer.exe for windows, mazeDrawer.linux for Linux and mazeDrawer.mac for macOS machines) for you to draw any given maze. To draw the maze for a given input file described above (maze_1txt), you must apply the following rules:

<u>On windows machine:</u>

<ol>

 <li>Put the mazeDrawer.exe and the input files into the same folder.</li>

 <li>Click on mazeDrawer.exe.</li>

 <li>Follow the instructions as needed.</li>

</ol>

<u>On macOS or Linux machine:</u>

<ol>

 <li>Put the mazeDrawer (mazeDrawer.mac for macOS and mazeDrawer.linux for Linux) program and the input files into the same folder.</li>

 <li><u>For macOS;</u>

  <ol>

   <li>Open a Terminal.app</li>

   <li>Copy the folder with Command+C (this will copy the path to reach the folder)</li>

  </ol></li>

</ol>

<ul>

 <li>In terminal, type <strong>cd</strong>​</li>

</ul>

<ol>

 <li>Use Command+V to paste the folder path and click enter Example usage (assuming mazeDrawer.mac is in the following path):</li>

</ol>

<h2>cd /Users/oguzozsaygin/Homework1</h2>

<u>For Linux;</u>

<ol>

 <li>Go to the folder.</li>

 <li>Right click anywhere in the folder. iii. Click open a terminal<strong> .</strong>​</li>

 <li>Execute the following command on the terminal by typing:</li>

 <li>For macOS;</li>

</ol>

<h2>./mazeDrawer.mac</h2>

<ol>

 <li>For Linux;</li>

</ol>

<strong>./mazeDrawer.linux</strong>  4.          Follow the instructions as needed.

<u>If you face any issues running the mazeDrawer program, please go to an office hour or ask your</u> <u>TA to explain it in the recitation.</u>

You will be given the file maze_example.txt to draw the maze below as an example. Use it as a way to understand how to use the program. This program is for you to better visualize your maze, though you are not obligated, we highly recommended you to use it for debugging your code.




<h1>Sample Run</h1>

Enter the number of mazes: 5

Enter the number of rows and columns (M and N): 20 32

All mazes are generated.




Enter a maze ID between 1 to 5 inclusive to find a path: 1

Enter x and y coordinates of the entry points (x,y) or (column,row): 0 0

Enter x and y coordinates of the exit points (x,y) or (column,row):