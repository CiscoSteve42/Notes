Distrotube Bash Scripting Notes
===============================

* [Distrotube]() offers a plethora of excellent Bash scripting content, I wanted to cover a few of his videos to help reinforce my learning.


'While' Loops and 'If' Statements
---------------------------------

* Link to video can be found [here](https://www.youtube.com/watch?v=KgA-MnH9Bpw).


### Hello World

* Basic 'Hello World' script that also prints the current directory and the current date via the `pwd` and `cal` commands:

```bash 
#!/usr/bin/env bash

string="hi mom!"
echo "$string"
pwd
cal
```


### While Loops

* example of a 'while' loop:


```bash
#!/usr/bin/env bash

x=10

while [ $x -ge 1 ] #while x is greater than or equal to 1
do
  echo "$x!"
  x=$(( x - 1 ))
done

echo "Blastoff!"
```


### If Statements 


