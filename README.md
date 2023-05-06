Download Link: https://assignmentchef.com/product/solved-ecet370-week-5-ilab-ilab-5-of-7-search-techniques-and-hashing
<br>
ECET 370 week 5 ILAB

iLab 5 of 7: Search Techniques and Hashing

Note!

Submit your assignment to the Dropbox, located at the top of this page.

(See the Syllabus section “Due Dates for Assignments &amp; Exams” for due dates.)

<strong>iLAB OVERVIEW</strong>

<strong>Scenario and Summary </strong>

The purpose of the lab exercises is to help the student acquire skills in developing programs that involve search algorithms and techniques.

<strong>Deliverables </strong>

There are four exercises in this lab, although not all of them will be required for submission. Be sure to read the following instructions carefully.

Exercise 1: No submission is required.

Note that one of the exercises requires sections of code to be timed. To review how to time a section of your source code, please refer to the beginning of the Projects section in Chapter 4 of our textbook.

Exercise 2 requires not only software development but also explanations about the results of the experiments that are conducted. Create a separate Word document to provide the details required in the exercise.

Create a folder and name it <em>Week 5 Lab</em>. Inside this folder, create the subfolders Ex2, Ex3, and Ex4. Place the solution to each of the three exercises required for submission in the corresponding subfolder. Compress the folder <em>Week 5 Lab</em>, and place the resulting zipped folder into the Dropbox.

Note that Exercises 2, 3, and 4 require software development. Place in the corresponding folders only .java files. Do not submit the .class files or other files or folders that are generated by the IDE.

<strong>Required Software </strong>

<strong>Eclipse</strong>

Access the software at <a href="https://lab.devry.edu/">https://lab.devry.edu </a>.

<strong>iLAB STEPS</strong>

<strong>Exercise 1: Review of the Lecture Content</strong>

<a href="https://devry.equella.ecollege.com/file/180e4791-f825-4b20-9f30-f0d62bace024/30/ECET370_W5_iLab.html#top">Back to Top</a>

Create a project using the ArrayList class and the Main class in <a href="https://devry.equella.ecollege.com/file/180e4791-f825-4b20-9f30-f0d62bace024/30/Search_Algorithms.zip">Search Algorithms</a>. The ArrayList class contains implementations of the first three search methods explained in this week’s lecture: sequential, sorted, and binary search. The Main class uses these three methods. These programs test the code discussed in the lecture. Compile the project, run it, and review the code that is given carefully.

<strong><u>Code :</u></strong>

Main:

/*******************************************

*  Week 5 lab – exercise 1 and exercise 2: *

*   ArrayList class with search algorithms *

********************************************/




import java.util.*;




/**

* Class to test sequential search, sorted search, and binary search algorithms

* implemented in ArrayList.

*/

public class Main

{




public static void main(String[] args)

{

Main myAppl = new Main();

}




public Main()

{

Scanner in = new Scanner(System.in);




//List creation and display

int n = 20;

ArrayList numbers = new ArrayList(n);




for (int i = 0; i &lt; n; i++)

numbers.add((int) (Math.random() * 100));




System.out.println(“List of integers:”);

System.out.println(numbers);




//Searching with sequential search

System.out.print(“
(Sequential Search) Enter a number:”);

int x = in.nextInt();

if (numbers.sequentialSearch(x))

System.out.println(“Found!”);

else

System.out.println(“Not found!”);




//Sorting the list

numbers.quicksort();

System.out.println(“
Sorted list of integers:”);

System.out.println(numbers);




//Searching with sorted search

System.out.print(“
(Sorted Search) Enter a number:”);

x = in.nextInt();

if (numbers.sortedSearch(x))

System.out.println(“Found!”);

else

System.out.println(“Not found!”);




//Searching with binary search

System.out.print(“
(Binary Search) Enter a number:”);

x = in.nextInt();

if (numbers.binarySearch(x))

System.out.println(“Found!”);

else

System.out.println(“Not found!”);

}

}




Array List:

/*******************************************

*  Week 5 lab – exercise 1 and exercise 2: *

*   ArrayList class with search algorithms *

********************************************/




/**

* Class implementing an array based list. Sequential search, sorted search, and

* binary search algorithms are implemented also.

*/

public class ArrayList

{




/**

* Default constructor. Sets length to 0, initializing the list as an empty

* list. Default size of array is 20.

*/

public ArrayList()

{

SIZE = 20;

list = new int[SIZE];

length = 0;

}




/**

* Determines whether the list is empty

*

* @return true if the list is empty, false otherwise

*/

public boolean isEmpty()

{

return length == 0;

}




/**

* Prints the list elements.

*/

public void display()

{

for (int i = 0; i &lt; length; i++)

System.out.print(list[i] + ” “);




System.out.println();

}




/**

* Adds the element x to the end of the list. List length is increased by 1.

*

* @param x element to be added to the list

*/

public void add(int x)

{

if (length == SIZE)

System.out.println(“Insertion Error: list is full”);

else

{

list[length] = x;

length++;

}

}




/**

* Removes the element at the given location from the list. List length is

* decreased by 1.

*

* @param pos location of the item to be removed

*/

public void removeAt(int pos)

{

for (int i = pos; i &lt; length – 1; i++)

list[i] = list[i + 1];

length–;

}




//Implementation of methods in the lab exercise

/**

* Non default constructor. Sets length to 0, initializing the list as an

* empty list. Size of array is passed as a parameter.

*

* @param size size of the array list

*/

public ArrayList(int size)

{

SIZE = size;

list = new int[SIZE];

length = 0;

}




/**

* Returns the number of items in the list (accessor method).

*

* @return the number of items in the list.

*/

public int getLength()

{

return length;

}




/**

* Returns the size of the list (accessor method).

*

* @return the size of the array

*/

public int getSize()

{

return SIZE;

}




/**

* Removes all of the items from the list. After this operation, the length

* of the list is zero.

*/

public void clear()

{

length = 0;

}




/**

* Replaces the item in the list at the position specified by location.

*

* @param location location of the element to be replaced

* @param item value that will replace the value at location

*/

public void replace(int location, int item)

{

if (location &lt; 0 || location &gt;= length)

System.out.println(“Error: invalid location”);

else

list[location] = item;

}




/**

* Adds an item to the list at the position specified by location.

*

* @param location location where item will be added.

* @param item item to be added to the list.

*/

public void add(int location, int item)

{

if (location &lt; 0 || location &gt;= length)

System.out.println(“Error: invalid position”);

else if (length == SIZE)

System.out.println(“Error: Array is full”);

else

{

for (int i = length; i &gt; location; i–)

list[ i] = list[ i – 1];

list[location] = item;

length++;

}

}




/**

* Deletes an item from the list. All occurrences of item in the list will

* be removed.

*

* @param item element to be removed.

*/

public void remove(int item)

{

for (int i = 0; i &lt; length; i++)

if (list[i] == item)

{

removeAt(i);

i–;  //onsecutive values won’t be all removed; that’s why i– is here

}

}




/**

* Returns the element at location

*

* @param location position in the list of the item to be returned

* @return element at location

*/

public int get(int location)

{

int x = -1;




if (location &lt; 0 || location &gt;= length)

System.out.println(“Error: invalid location”);

else

x = list[location];




return x;

}




/**

* Makes a deep copy to another ArrayList object.

*

* @return Copy of this ArrayList

*/

public ArrayList copy()

{

ArrayList newList = new ArrayList(this.SIZE);




newList.length = this.length;




for (int i = 0; i &lt; length; i++)

newList.list[i] = this.list[i];




return newList;

}




/**

* Bubble-sorts this ArrayList

*/

public void bubbleSort()

{

for (int i = 0; i &lt; length – 1; i++)

for (int j = 0; j &lt; length – i – 1; j++)

if (list[j] &gt; list[j + 1])

{

//swap list[j] and list[j+1]

int temp = list[j];

list[j] = list[j + 1];

list[j + 1] = temp;

}

}




/**

* Quick-sorts this ArrayList.

*/

public void quicksort()

{

quicksort(0, length – 1);

}




/**

* Recursive quicksort algorithm.

*

* @param begin initial index of sublist to be quick-sorted.

* @param end last index of sublist to be quick-sorted.

*/

private void quicksort(int begin, int end)

{

int temp;

int pivot = findPivotLocation(begin, end);




// swap list[pivot] and list[end]

temp = list[pivot];

list[pivot] = list[end];

list[end] = temp;




pivot = end;




int i = begin,

j = end – 1;




boolean iterationCompleted = false;

while (!iterationCompleted)

{

while (list[i] &lt; list[pivot])

i++;

while ((j &gt;= 0) &amp;&amp; (list[pivot] &lt; list[j]))

j–;




if (i &lt; j)

{

//swap list[i] and list[j]

temp = list[i];

list[i] = list[j];

list[j] = temp;




i++;

j–;

} else

iterationCompleted = true;

}




//swap list[i] and list[pivot]

temp = list[i];

list[i] = list[pivot];

list[pivot] = temp;




if (begin &lt; i – 1)

quicksort(begin, i – 1);

if (i + 1 &lt; end)

quicksort(i + 1, end);

}




/*

* Computes the pivot location.

*/

private int findPivotLocation(int b, int e)

{

return (b + e) / 2;

}




/*The methods listed below are new additions to the ArrayList class

* of Week 4*/

/**

* This method returns a string representation of the array list elements.

* Classes with this method implemented can get its objects displayed in a

* simple way using System.out.println. For example, if list is an ArrayList

* object, it can be printed by using

*

* System.out.println(list);

*

* @return a string representation of the array list elements.

*/

public String toString()

{

String s = “”;




for (int i = 0; i &lt; length; i++)

s += list[i] + ” “;




return s;

}




/**

* Determines if an item exists in the array list using sequential (linear)

* search.

*

* @param x item to be found.

* @return true if x is found in the list, false otherwise.

*/

public boolean sequentialSearch(int x)

{

for (int i = 0; i &lt; length; i++)

if (list[i] == x)

return true;




return false;

}




/**

* Determines if an item exists in the array list using sorted search. List

* must be sorted.

*

* @param x item to be found.

* @return true if x is found in the list, false otherwise.

*/

public boolean sortedSearch(int x)

{

//The list must ne sorted to invoke this method!

int i = 0;

while (i &lt; length &amp;&amp; list[i] &lt; x)

i++;




if (i &lt; length &amp;&amp; list[i] == x)

return true;   // x is in the array

else

return false;                             // x is not in the array

}




/**

* Determines if an item exists in the array list using binary search. List

* must be sorted.

*

* @param x item to be found.

* @return true if x is found in the list, false otherwise.

*/

public boolean binarySearch(int x)

{

int first = 0, last = length – 1, pivot;




boolean found = false;

while (first &lt;= last &amp;&amp; !found)

{

pivot = (first + last) / 2;

if (list[pivot] == x)

found = true;

else if (x &lt; list[pivot])

last = pivot – 1;

else

first = pivot + 1;

}




if (found)

return true;

else

return false;

}

private static int SIZE;    //size of the array that stores the list items

private int[] list;         //array to store the list items

private int length;          //amount of items in the list

}







<strong>Exercise 2: Search Algorithms and Techniques</strong>

<a href="https://devry.equella.ecollege.com/file/180e4791-f825-4b20-9f30-f0d62bace024/30/ECET370_W5_iLab.html#top">Back to Top</a>

Expand the project developed in the previous exercise to perform the following experiment: Time the sequential search and the binary search methods several times each for randomly generated values, and record the results in a table. Do not time individual searches, but groups of them. For example, time 100 searches together or 1,000 searches together. Compare the running times of these two search methods that are obtained during the experiment.

Regarding the efficiency of both search methods, what conclusion can be reached from this experiment? Both the table and your conclusions should be included in a separate Word document.

<strong>Exercise 3: Searching Applications</strong>

<a href="https://devry.equella.ecollege.com/file/180e4791-f825-4b20-9f30-f0d62bace024/30/ECET370_W5_iLab.html#top">Back to Top</a>

The following problem is a variation of Project 4 in the “Projects” section of Chapter 18 in our textbook:

Consider an array <em>data</em> of <em>n</em> numerical values in sorted order and a list of two numerical target values. Your goal is to compute the smallest range of array indices that contains both of the target values. If a target value is smaller than <em>data[0]</em>, the range should start with a <em>-1</em>. If a target value is larger than <em>data[n-1]</em>, the range should end with<em> n</em>.

For example, given the array

<table width="100%">

 <tbody>

  <tr>

   <td width="95">0</td>

   <td width="95">1</td>

   <td width="95">2</td>

   <td width="96">3</td>

   <td width="95">4</td>

   <td width="96">5</td>

   <td width="95">6</td>

   <td width="96">7</td>

  </tr>

  <tr>

   <td>5</td>

   <td>8</td>

   <td>10</td>

   <td>13</td>

   <td>15</td>

   <td>20</td>

   <td>22</td>

   <td>26</td>

  </tr>

 </tbody>

</table>

the following table illustrates target values and their corresponding ranges:

<table width="100%">

 <tbody>

  <tr>

   <td width="390"><strong>Target Values </strong></td>

   <td width="385"><strong>Smellest Range of Indices </strong></td>

  </tr>

  <tr>

   <td>2, 8</td>

   <td> [-1, 1]</td>

  </tr>

  <tr>

   <td>9, 14</td>

   <td> [1, 4]</td>

  </tr>

  <tr>

   <td>12, 21</td>

   <td> [2, 6]</td>

  </tr>

  <tr>

   <td>14, 30</td>

   <td> [3, 8]</td>

  </tr>

 </tbody>

</table>

Devise and implement an algorithm that solves this problem.

<strong>Exercise 4: Hashing</strong>

<a href="https://devry.equella.ecollege.com/file/180e4791-f825-4b20-9f30-f0d62bace024/30/ECET370_W5_iLab.html#top">Back to Top</a>

Suppose that the type of key in a hashing application you are implementing is string (Sections 21.7 and 21.8 in our textbook explain hash functions for strings). Design and implement a hash function that converts a key to a hash value. Test your function by computing the hash values for the Java keywords. Was a key collision produced?

<strong>iLab Grading Rubric</strong>

<a href="https://devry.equella.ecollege.com/file/180e4791-f825-4b20-9f30-f0d62bace024/30/ECET370_W5_iLab.html#top">Back to Top</a>

<table>

 <tbody>

  <tr>

   <td width="77"><strong>YourPoints </strong></td>

   <td width="68"><strong>MaxPoints </strong></td>

   <td width="425"></td>

  </tr>

  <tr>

   <td colspan="3" width="570"><strong>Complete Weekly iLab (52 points)</strong></td>

  </tr>

  <tr>

   <td width="77"><strong>0 </strong></td>

   <td width="68"><strong>6 </strong></td>

   <td width="425">The student has submitted the lab solutions using the requirements for deliverables specified in the iLab Content document.</td>

  </tr>

  <tr>

   <td width="77"><strong>0 </strong></td>

   <td width="68"><strong>6 </strong></td>

   <td width="425">Code organization and readability</td>

  </tr>

  <tr>

   <td width="77"><strong>0 </strong></td>

   <td width="68"><strong>40 </strong></td>

   <td width="425">Each of the lab programming exercises has been successfully accomplished:– Exercise 2: 18 points (source code, 14 points; conclusions in separate document, 4 points)– Exercise 3: 16 points– Exercise 4: 6 points</td>

  </tr>

  <tr>

   <td colspan="2" width="145"><strong>Total Points: 52 </strong></td>

   <td width="425"></td>

  </tr>

 </tbody>

</table>


