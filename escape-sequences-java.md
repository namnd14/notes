Escape Sequences

A character preceded by a backslash (\) is an escape sequence and has special meaning to the compiler. The following table shows the Java escape sequences:

\t	Insert a tab in the text at this point.
<br>
\b	Insert a backspace in the text at this point.
<br>
\n	Insert a newline in the text at this point.
<br>
\r	Insert a carriage return in the text at this point.
<br>
\f	Insert a form feed in the text at this point.
<br>
\'	Insert a single quote character in the text at this point.
<br>
\"	Insert a double quote character in the text at this point.
<br>
\\	Insert a backslash character in the text at this point.
<br>

When an escape sequence is encountered in a print statement, the compiler interprets it accordingly. For example, if you want to put quotes within quotes you must use the escape sequence, \", on the interior quotes. To print the sentence: She said "Hello!" to me.
you would write:

System.out.println("She said \"Hello!\" to me.");

Refer: https://docs.oracle.com/javase/tutorial/java/data/characters.html
