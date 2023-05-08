Download Link: https://assignmentchef.com/product/solved-prl-assignment-1
<br>
<ol>

 <li>Learn how to write and use makefile: <u>http://www.delorie.com/djgpp/doc/ug/larger/makefiles.html</u></li>

 <li>Acquaint yourself with flex and bison.</li>

</ol>

<h2>Specifications</h2>

You will extend calc.l and calc.y  to parse programs whose syntax is defined below.

Prog à main() {Stmts}

Stmts à <strong>ε</strong> | Stmt; Stmts

Stmt à Id = E | Id *= E | Id += E | <strong>print</strong> E

E à Integer | Id | E * E | E + E | (-Integer)

Integer à digit





<strong>Prog </strong>is a program that contains one main function.

<strong>Stmts </strong>is empty or a sequence of statements separated using ;




<strong>Integer</strong> is either a positive integer, or a negative integer enclosed in “(“ and “)”

<strong>Id </strong>is an identifier, which is a sequence of one or more lower-case letters or digits.  In addition, <strong>Id</strong> should start with a lower-case letters.  For example, x, x1, xy are identifiers, but 1x and A are not.  <strong> </strong>

<strong>Expression E </strong>is an integer, an identifier, or an infix arithmetic expression with operators “*” and “+”. These two operators are left associative (e.g., 1 + 2 + 3 is equivalent to (1 + 2) + 3). “*” has higher precedence than “+”.

<strong>Id = E </strong>assigns the value of an expression E to the variable Id, <strong>Id *= E </strong>assigns Id * E to Id, and <strong>Id += E </strong>assigns Id + E to Id.  <strong>println E </strong>outputs the value of the expression E.  Assume that Id is already assigned a value prior to the execution of Id *= E and Id += E.

If there is any <strong>syntax error</strong>, you are expected to interpret the program until the statement where you find the error. Also, <strong>your error message must contain the line number where the error was found. </strong>




Tokens  may be separated by <strong>any number of</strong> white spaces, tabs, or new lines.

<strong><em> </em></strong>

<strong><em><u>Compile your program:</u></em></strong>

<strong><em> </em></strong>flex –l calc.l bison -dv calc.y

gcc -o calc calc.tab.c lex.yy.c –lfl

<strong><em> </em></strong>

<strong><em> </em></strong>

<strong><em><u>Execution (example):</u></em></strong>.

<strong>./calc &lt; input </strong>

Where <strong>input</strong> is the name of the input file




<strong><em>Example Programs (Note that the test cases used in grading may be different from the examples) </em></strong>




<strong>Program 1:</strong>

main() {x = 3;}




<strong>Output:</strong>







<strong>Program 2:</strong>

main() {x = 3; print x;}




<strong>Output: </strong>

3




<strong>Program 3:</strong>

main() {x = 3;  x = 5 + 4; print x;}




<strong>Output:</strong>

9




<strong>Program 4:</strong>

main() {x = 3* 4; print x;}




<strong>Output:</strong>

12







<strong>Program 5:</strong>

main() {print 1 + 2 + 4;}




<strong>Output:</strong>

7

<strong> </strong>

<strong> </strong>

<strong>Program 6:</strong>

main() {x = 0; x = 1-2; }




<strong>Output:</strong>

Lexical error: –     Parsing error: line 1




<strong> </strong>

<strong>Program 7:</strong>

main() {                   1x = 3;

}




<strong>Output:</strong>

Lexical error: 1x

Parsing error: line 2




<table width="577">

 <tbody>

  <tr>

   <td width="123"><strong> </strong><strong>Program 8: </strong>main() { </td>

   <td width="454">x = 3;</td>

  </tr>

  <tr>

   <td width="123">                     print} <strong>Output:</strong>3 </td>

   <td width="454">   x;</td>

  </tr>

  <tr>

   <td width="123"> <strong>Program 9: </strong> x = 0; <strong>Output: </strong>Parsing error: line 1 </td>

   <td width="454"></td>

  </tr>

 </tbody>

</table>




<strong>Program 10:</strong>

main() {x = 3;  x += 5 + 4; print x;}




<strong>Output:</strong>

12




<strong>Program 11:</strong>

main() {x = 3;  x = (-5) + 3; print x;}




<strong>Output:</strong>

-2




<strong>Program 12:</strong>

main() {x = 3;  y = 2; print x; print y;}




<strong>Output:</strong>

3

2


