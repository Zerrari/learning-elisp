
# Table of Contents

1.  [Day1](#orga152f0c)
    1.  [symbol](#orgf86ac0c)
        1.  [it can be defined as a function and a variable which returns a value](#org8149917)
        2.  [when symbol is in a pair of parenthese and is the first position.It stands for a function.](#orgd247a72)
        3.  [when symbol is not in a pair of parenthese it stands for a variable.](#orgedd6e06)
        4.  [a quotation before a pair of parenthese return what is written](#org8d35392)
        5.  [atoms which in a pair of parenthese are separated by a white space](#orgf54936e)
    2.  [evaluate](#orgd142278)
        1.  [how](#orge962efb)
    3.  [function](#org3a31d4e)
        1.  [something basic](#org1b2067c)
        2.  [set and setq](#orgc9d4a7e)
        3.  [buffer](#org3dd225a)
2.  [Day2](#org2341ae2)
    1.  [function](#org782a795)
        1.  [defun](#orga2fab0a)
        2.  [let](#orge9acbd2)
        3.  [if](#org65a0c53)
        4.  [save excurison](#org8ca02e1)
        5.  [beginning of buffer](#org7e36f9e)
        6.  [mark-whole-buffer](#org9c318f7)
        7.  [append-to-buffer](#org1ddb919)
3.  [Day3](#orgbd58d4b)
    1.  [narrowing and widening](#org332d272)
        1.  [key binding](#orga1767d1)
    2.  [save-restriction](#org4536a93)
        1.  [use save-restriction and save-excurison](#org7d04ca6)
    3.  [what-lines](#org02a06d9)
        1.  [](#org91c2189)
    4.  [more about interactive](#org92a586b)
        1.  [input many arguments](#org446ebbe)
        2.  ["r" stands for a region](#orga97c8c1)
        3.  ["p" and "P"](#orgb5a2032)
    5.  [car,cdr and cons](#org6935dde)
        1.  [car](#org6052a73)
        2.  [cdr](#org0710d36)
        3.  [cons](#orgc8fdda0)
        4.  [nthcdr](#org0da639c)
        5.  [nth](#orgecc8745)
        6.  [setcar](#org21dff84)
        7.  [setcdr](#org98eac81)
4.  [Day4](#orga98b01f)
    1.  [defvar](#org258da1c)
    2.  [loops and recursion](#orgcf70c63)
        1.  [while](#org9bc1593)
        2.  [increment loop](#orgd482f44)
        3.  [dolist and dotimes](#org8b773f4)
5.  [Day5](#org4fc4a94)
    1.  [numbers](#orgd4f449f)
        1.  [basics](#orgb07b173)
        2.  [type predicates](#orge8c7671)
        3.  [comparison of numbers](#orgbcd4c2e)
        4.  [conversion](#orgb8d4279)
        5.  [arithmetic operations](#org81c1387)
        6.  [float rounding](#org916af15)
        7.  [bitwise operations](#org42bf3bf)
        8.  [mathmatical functions](#org90290b0)
        9.  [random numbers](#orga45b891)


<a id="orga152f0c"></a>

# Day1


<a id="orgf86ac0c"></a>

## symbol


<a id="org8149917"></a>

### it can be defined as a function and a variable which returns a value


<a id="orgd247a72"></a>

### when symbol is in a pair of parenthese and is the first position.It stands for a function.

1.  

        (+ 1 2)


<a id="orgedd6e06"></a>

### when symbol is not in a pair of parenthese it stands for a variable.

1.  

        fill-column    


<a id="org8d35392"></a>

### a quotation before a pair of parenthese return what is written

    '(lion tigger)

    '(lion "a tree")


<a id="orgf54936e"></a>

### atoms which in a pair of parenthese are separated by a white space


<a id="orgd142278"></a>

## evaluate


<a id="orge962efb"></a>

### how

move the cursor after the parenthese,and type **C-x C-e** to evaluate the expression


<a id="org3a31d4e"></a>

## function


<a id="org1b2067c"></a>

### something basic

1.  a funtion returns two things

    -   return a value
    -   side effects(*print something on the screen*)


<a id="orgc9d4a7e"></a>

### set and setq

1.  set

        (set 'flowers '(rose))
        flowers

2.  setq

    1.  an easy way to use set
    
    2.  
    
            (setq animals '(lion tigger))
            animals

3.  something important

    If you don't add **'** before symbol,it will be explanined as a function.
    For example, if you don't add **'** before (lion tigger),the lisp interpretor will think lion is a function.
    So it will return a error message.


<a id="org3dd225a"></a>

### buffer

1.  buffer-name and buffer-file-name

    1.  buffer-name
    
        It returns the current buffer name
        
            (buffer-name)
    
    2.  buffer-file-name
    
        It returns a full path which the file belongs to.
        
            (buffer-file-name)

2.  current-buffer

    It returns the name of current buffer.
    
        (current-buffer)

3.  other-buffer

    It returns the buffer which you visited.
    
        (other-buffer)

4.  switch-to-buffer

        (switch-to-buffer (other-buffer))


<a id="org2341ae2"></a>

# Day2


<a id="org782a795"></a>

## function


<a id="orga2fab0a"></a>

### defun

1.  template

        (defun fun-name (arguments)
             "optional document"
             (optional interactive)
             (body))

2.  interactive(*need input in a minibuffer*)

    1.  example
    
            (defun add (x)
                 (interactive "p")  
                 (message "The result is %d" (+ x 3)))

3.  invoke an interactive function by typing **C-u argument M-x fun-name**

4.  **p** stands for prefix which means you should type before invoke a function


<a id="orge9acbd2"></a>

### let

1.  template

        (let varlist body)
    
        (let ((variable value1)
              (variable value2))
              body)
    
        (let ((one "apple")
              (two "banana"))
              (message "the fruit is %s" one))

2.  something important

    unintialized variables will be bond to **nil**
    
        (let ((one)
              (two "banana"))
              (message "the fruit is %s" one))


<a id="org65a0c53"></a>

### if

1.  example

        (if (> 5 4)
             (message "yes")
             (message "no"))

2.  truth and falsehood

    -   anything except nil represents true
    -   the **empty** list is falsehood


<a id="org8ca02e1"></a>

### save excurison

save the positon of cursor(after evaluating the function,it return the initial location)

1.  point and mark

    1.  point
    
        Point is the current position of the cursor(integer)
    
    2.  mark
    
        Mark is another positon of current buffer.
        
        1.  mark set
        
            Its value can be set.
            type **C-spc** to set mark(it will send a message in minibuffer)
        
        2.  mark ring
        
            If you set several marks,it will be recorded in a mark ring.
            type **C-u C-spc** to jump to the mark you saved
    
    3.  region
    
        The part between point and mark is called a region.

2.  template

        (save-excurison 
          body...)


<a id="org7e36f9e"></a>

### beginning of buffer

1.  push-mark

    the function stores the current positon of the cursor in mark ring
    
        (defun simple-bob
         (interactive)
         (push-mark)
         (goto-char (point-min)))


<a id="org9c318f7"></a>

### mark-whole-buffer

    (defun z-mark-whole-buffer()
      (interactive)
      (progn
        (goto-char (point-max))
        (set-mark (point))
        (goto-char (point-min))))
    (z-mark-whole-buffer)


<a id="org1ddb919"></a>

### append-to-buffer

insert-buffer-substring


<a id="orgbd58d4b"></a>

# Day3


<a id="org332d272"></a>

## narrowing and widening

with narrowing, the rest of buffer is invisible


<a id="orga1767d1"></a>

### key binding

**C-x n n** for *narrow-to-rigion*
**C-x n w** for *widen*


<a id="org4536a93"></a>

## save-restriction


<a id="org7d04ca6"></a>

### use save-restriction and save-excurison

    (save-excurison
      (save-restriction 
         body))

    (save-restriction 
      (widen)
      (save-excurison
      body))


<a id="org02a06d9"></a>

## what-lines


<a id="org91c2189"></a>

### 

    (defun simple-whatline()
      (interactive)
      (save-restriction
        (widen)
        (save-excursion
          (let ((lines))
    	(setq  lines (count-lines 1 (point)))
    	(message "The line number is %d" lines)))))


<a id="org92a586b"></a>

## more about interactive

Sepreate string with **\n**


<a id="org446ebbe"></a>

### input many arguments

-   **"s"** string
-   **"n"** number

    (defun hello(name age country)
      (interactive "sinput your name: \nnage: \nscountry: ")
      (message "name:%s age:%d country:%s" name age country))


<a id="orga97c8c1"></a>

### "r" stands for a region

    (defun hello1 (start end)
      (interactive "r")
      (message "start:%d end:%d" start end))


<a id="orgb5a2032"></a>

### "p" and "P"

invoke a function by typing **C-u prefix-argument M-x fun-name**

1.  "p" prefix argument convert to a number

2.  "P" prefix argument is a raw type

        (defun hello2 (num)
          (interactive "p")
          (message "%d" num))


<a id="org6935dde"></a>

## car,cdr and cons

-   cons to construct lists
-   car and cdr to take apart lists


<a id="org6052a73"></a>

### car

the car of the list is the first item

    (car '(tiger lion))


<a id="org0710d36"></a>

### cdr

returns the rest of the list

    (cdr '(tiger lion))
    (cdr '(tiger lion cat))


<a id="orgc8fdda0"></a>

### cons

    (cons 'tiger '(lion cat))


<a id="org0da639c"></a>

### nthcdr

use cdr repeatedly

    (nthcdr 1 '(tiger lion cat))

    (nthcdr 3 '(tiger lion cat))


<a id="orgecc8745"></a>

### nth

use car repeatedly

    (nth 1 '(lion tiger cat))


<a id="org21dff84"></a>

### setcar

set the **car** a new value

    (setq animals (list 'tiger 'cat 'lion))
    (setcar animals 'pig)
    animals


<a id="org98eac81"></a>

### setcdr

set the **cdr** a new value

    (setq animals (list 'tiger 'cat 'lion))
    (setcdr animals (list 'pig 'dog))
    animals


<a id="orga98b01f"></a>

# Day4


<a id="org258da1c"></a>

## defvar

-   it only sets the value of the variable when it doesn't exits
-   if the value has exited,defvar will not overrider the initial value
-   defvar has document string

    (defvar num 3)
    num


<a id="orgcf70c63"></a>

## loops and recursion


<a id="org9bc1593"></a>

### while

    (setq animals '(pig cat tiger dog))
    (defun print-list-element (list)
      (while list
       (print (car list))
       (setq list (cdr list))))
    (print-list-element animals)nil


<a id="orgd482f44"></a>

### increment loop

use counter to stop a loop

    (setq count 1)
    (defun counter-stop (num)
      (while (< count num))
       body
       (setq count (+ 1 count))))


<a id="org8b773f4"></a>

### dolist and dotimes

1.  dolist

    (dolist element list value)
    
    -   the car of the list is bound to the element
    -   the list is bound the cdr of the list
    -   the return result is value
    
        (setq animals '(cat dog pig))
        (defun reverse-list (list)
          (let ((value ()) (element nil))
           (dolist (element list value)
            (setq value (cons element value))))
            (reverse-list animals)

2.  dotimes

        (let ((value nil))
            (dotimes (number 3)
              (message "%d " number)))


<a id="org4fc4a94"></a>

# Day5


<a id="orgd4f449f"></a>

## numbers


<a id="orgb07b173"></a>

### basics

-   initial sgin
-   followed by a period
-   two's complement notation to  represent negative number

    1.
    +1
    +1.

    (message "%d" most-positive-fixnum)

    (message "%d" most-negative-fixnum)

    (message "%d" integer-width)

    (isnan 3.0)

1.  frexp

    return a cons cell(s . e)
    
    -   s represents significand
    -   e represents exponet
    
    3.5 = 0.875\*2<sup>2</sup>
    
        (frexp 3.5)

2.  ldexp

    give s and e, return x
    
        (ldexp 0.875 2)

3.  copysign

    copy sign of x2 to x1 and return the result
    
        (copysign x1 x2)
    
        (copysign 3.5 -3.5)

4.  logb

    logarithm base 2 of |x|
    round to an integer
    
        (logb 2) 1
    
        (logb 10) 3


<a id="orge8c7671"></a>

### type predicates

-   bignump

    (bignump 2)  nil

-   fixnump

-   floatp

    (floatp 2) nil

-   integerp

    (integerp 2) t

-   numberp

-   natnump/wholenump

check if it is a natural number

    (natnump 3)  t
    (natnump -1) nil

-   zerop

    (zerop 0)  t


<a id="orgbcd4c2e"></a>

### comparison of numbers

1.  **=**

    -   numerical equality
    -   only accept numbers or markers as arguments
    
        (= 2 2)
    
        (= 2 2.0)

2.  **equal**

    check if their valus are indistinguishable
    
        (equal 1 1.0)
    
        (equal 1 1)

3.  **eq**

    check if they are the same object
    
        (eq 1 1) 
    
        (eq 2 2.0) 

4.  max

        (max 1 2 3)

5.  min

        (min 1 2 3)

6.  abs

        (abs -3)


<a id="orgb8d4279"></a>

### conversion

1.  float

    convert integer to float
    
        (float 3)
    
        (float 3.0)

2.  convert to integer

    -   truncate
    
    rounding towards zero
    
        (truncate 1.7)
    
        (truncate 1.2)
    
    -   floor
    
    rounding downward
    
        (floor 1.2)
    
        (floor -1.2)
    
    -   ceiling
    
    rounding upward
    
        (ceiling 1.5)
    
        (ceiling -1.3)
    
    -   round
    
    rounding towards the nearest integer
    if it is a mid-value,round to an even integer
    
        (round 1.2)
    
        (round 1.5)


<a id="org81c1387"></a>

### arithmetic operations

1.  1+ / 1-

    don't change the value of variable
    
        (setq foo 2)
        (1+ foo)
        foo
    
        (1+ 2)

2.  +

        (+)
    
        (+ 1 2 3)

3.  -

        (- 10 1 1 2)
    
        (- 10)

4.  \*

        (*)
    
        (* 1 2 3)

5.  /

        (/ 26 3 1)
    
        (/ 26 3 1.0)
    
        (/ 3.0)

6.  %

        (% 9 4)

7.  mod

    accept float argument,unlike %
    
        (mod 9 4)
    
        (mod 9 -4)


<a id="org916af15"></a>

### float rounding

return the float whose value is nearby integer

-   ffloor

    (ffloor 3.5)

-   fceiling
-   ftruncate
-   fround


<a id="org42bf3bf"></a>

### bitwise operations

1.  ash

    -   shift the bits left if the argument is positive
    -   if it moves right, replace the high position of **0**
    
        (ash 7 1)
    
        (ash 8 -1)

2.  lsh

        (lsh -14 1)
    
        (lsh 14 -1)

3.  logand

    return the bitwise **and** of the arguments
    
        (logand 12 13)

4.  logior

    return the bitwise **or** of the arguments
    
        (logior 12 5)

5.  logxor

    return the bitwise **xor** of the arguments
    
        (logxor 12 5)

6.  lognot

    return the bitwise **not** of the argument
    
        (lognot 5)

7.  logcount

    -   if the integer is positive,return the number of ones
    -   else return the number of zeros
    
        (logcount 43)
    
        (logcount -43)


<a id="org90290b0"></a>

### mathmatical functions

-   sin
-   cos
-   tan
-   asin
-   acos
-   atan
-   exp

return e to the power **arg**

    (exp 2)

-   log

    (log arg &optional base)

if the base isn't specified,the **e** will be provided defaultly

    (log (exp 2))

-   expt

return x rasied to the power y

    (expt x y)

    (expt 3 2)

-   sqrt

-   float-e

    float-e

-   float-pi

    float-pi


<a id="orga45b891"></a>

### random numbers

1.  set the seed to a constant value

        (random "")
    
        
        (random 5)

