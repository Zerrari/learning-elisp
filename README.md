
# Table of Contents

1.  [Day1](#org482acde)
    1.  [symbol](#org1f4f36d)
    2.  [evaluate](#orga77fd30)
        1.  [how](#orge95b82e)
    3.  [function](#org19e1cc9)
        1.  [something basic](#org05cbab2)
        2.  [set and setq](#org0268a7e)
        3.  [buffer](#orgec3a10a)
2.  [Day2](#orgf2f9897)
    1.  [function](#org3c3a7d5)
        1.  [defun](#org6b4eecd)
        2.  [let](#org78d93d6)
        3.  [if](#orgaeb3134)
        4.  [save excurison](#org69d3ba7)
        5.  [beginning of buffer](#orga21807b)
        6.  [mark-whole-buffer](#orgfd05690)
        7.  [append-to-buffer](#orgca6ceee)
3.  [Day3](#org5881f13)
    1.  [narrowing and widening](#org452836a)
        1.  [key binding](#orga3d431c)
    2.  [save-restriction](#org11fd999)
        1.  [use save-restriction and save-excurison](#org8d933b4)
    3.  [what-lines](#org2cfcd19)
        1.  [](#orgb291786)
    4.  [more about interactive](#org6436f69)
        1.  [input many arguments](#org21793f8)
        2.  ["r" stands for a region](#org9880087)
        3.  ["p" and "P"](#orgb1770f8)
    5.  [car,cdr and cons](#org5fb0298)
        1.  [car](#orga22a5e5)
        2.  [cdr](#orga541f10)
        3.  [cons](#orgc6c59e8)
        4.  [nthcdr](#orgbfe7601)
        5.  [nth](#org0247107)
        6.  [setcar](#org7539e21)
        7.  [setcdr](#org927a014)
4.  [Day4](#orga61dd8d)
    1.  [defvar](#org69f63df)
    2.  [loops and recursion](#org2bb52ee)
        1.  [while](#orgb19c085)
        2.  [increment loop](#org139db4a)
        3.  [dolist and dotimes](#org7b5573e)
5.  [Day5](#org71117a7)
    1.  [numbers](#org51f0827)
        1.  [basics](#org619c8de)
        2.  [type predicates](#org170010a)
        3.  [comparison of numbers](#orgf324ed5)
        4.  [conversion](#orgb4e059c)
        5.  [arithmetic operations](#org8b871fa)
        6.  [float rounding](#org77d3f41)
        7.  [bitwise operations](#org7f76494)
        8.  [mathmatical functions](#org1183e07)
        9.  [random numbers](#orgdebe96d)


<a id="org482acde"></a>

# Day1


<a id="org1f4f36d"></a>

## symbol

-   it can be defined as a function and a variable which returns a value
-   when symbol is in a pair of parenthese and is the first position.It stands for a function.

    (+ 1 2)

-   when symbol is not in a pair of parenthese it stands for a variable.

    fill-column    

-   a quotation before a pair of parenthese return what is written

    '(lion tigger)

    '(lion "a tree")

-   atoms which in a pair of parenthese are separated by a white space


<a id="orga77fd30"></a>

## evaluate


<a id="orge95b82e"></a>

### how

move the cursor after the parenthese,and type **C-x C-e** to evaluate the expression


<a id="org19e1cc9"></a>

## function


<a id="org05cbab2"></a>

### something basic

1.  a funtion returns two things

    -   return a value
    -   side effects(*print something on the screen*)


<a id="org0268a7e"></a>

### set and setq

1.  set

        (set 'flowers '(rose))
        flowers

2.  setq

    -   an easy way to use set
        
            (setq animals '(lion tigger))
            animals

3.  something important

    If you don't add **'** before symbol,it will be explanined as a function.
    
    For example, if you don't add **'** before (lion tigger),
    
    the lisp interpretor will think lion is a function.
    
    So it will return a error message.


<a id="orgec3a10a"></a>

### buffer

1.  buffer-name and buffer-file-name

    -   buffer-name
    
    It returns the current buffer name
    
        (buffer-name)
    
    -   buffer-file-name
    
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


<a id="orgf2f9897"></a>

# Day2


<a id="org3c3a7d5"></a>

## function


<a id="org6b4eecd"></a>

### defun

-   template

    (defun fun-name (arguments)
         "optional document"
         (optional interactive)
         (body))

-   interactive(*need input in a minibuffer*)

    (defun add (x)
         (interactive "p")  
         (message "The result is %d" (+ x 3)))

-   invoke an interactive function by typing **C-u argument M-x fun-name**
-   **p** stands for prefix which means you should type before invoke a function


<a id="org78d93d6"></a>

### let

-   template

    (let varlist body)

    (let ((variable value1)
          (variable value2))
          body)

    (let ((one "apple")
          (two "banana"))
          (message "the fruit is %s" one))

-   something important

unintialized variables will be bond to **nil**

    (let ((one)
          (two "banana"))
          (message "the fruit is %s" one))


<a id="orgaeb3134"></a>

### if

-   example

    (if (> 5 4)
         (message "yes")
         (message "no"))

-   truth and falsehood
-   anything except nil represents true
-   the **empty** list is falsehood


<a id="org69d3ba7"></a>

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


<a id="orga21807b"></a>

### beginning of buffer

1.  push-mark

    the function stores the current positon of the cursor in mark ring
    
        (defun simple-bob
         (interactive)
         (push-mark)
         (goto-char (point-min)))


<a id="orgfd05690"></a>

### mark-whole-buffer

    (defun z-mark-whole-buffer()
      (interactive)
      (progn
        (goto-char (point-max))
        (set-mark (point))
        (goto-char (point-min))))
    (z-mark-whole-buffer)


<a id="orgca6ceee"></a>

### append-to-buffer

insert-buffer-substring


<a id="org5881f13"></a>

# Day3


<a id="org452836a"></a>

## narrowing and widening

with narrowing, the rest of buffer is invisible


<a id="orga3d431c"></a>

### key binding

**C-x n n** for *narrow-to-rigion*
**C-x n w** for *widen*


<a id="org11fd999"></a>

## save-restriction


<a id="org8d933b4"></a>

### use save-restriction and save-excurison

    (save-excurison
      (save-restriction 
         body))

    (save-restriction 
      (widen)
      (save-excurison
      body))


<a id="org2cfcd19"></a>

## what-lines


<a id="orgb291786"></a>

### 

    (defun simple-whatline()
      (interactive)
      (save-restriction
        (widen)
        (save-excursion
          (let ((lines))
    	(setq  lines (count-lines 1 (point)))
    	(message "The line number is %d" lines)))))


<a id="org6436f69"></a>

## more about interactive

Sepreate string with **\n**


<a id="org21793f8"></a>

### input many arguments

-   **"s"** string
-   **"n"** number

    (defun hello(name age country)
      (interactive "sinput your name: \nnage: \nscountry: ")
      (message "name:%s age:%d country:%s" name age country))


<a id="org9880087"></a>

### "r" stands for a region

    (defun hello1 (start end)
      (interactive "r")
      (message "start:%d end:%d" start end))


<a id="orgb1770f8"></a>

### "p" and "P"

invoke a function by typing **C-u prefix-argument M-x fun-name**

1.  "p" prefix argument convert to a number

2.  "P" prefix argument is a raw type

        (defun hello2 (num)
          (interactive "p")
          (message "%d" num))


<a id="org5fb0298"></a>

## car,cdr and cons

-   cons to construct lists
-   car and cdr to take apart lists


<a id="orga22a5e5"></a>

### car

the car of the list is the first item

    (car '(tiger lion))


<a id="orga541f10"></a>

### cdr

returns the rest of the list

    (cdr '(tiger lion))
    (cdr '(tiger lion cat))


<a id="orgc6c59e8"></a>

### cons

    (cons 'tiger '(lion cat))


<a id="orgbfe7601"></a>

### nthcdr

use cdr repeatedly

    (nthcdr 1 '(tiger lion cat))

    (nthcdr 3 '(tiger lion cat))


<a id="org0247107"></a>

### nth

use car repeatedly

    (nth 1 '(lion tiger cat))


<a id="org7539e21"></a>

### setcar

set the **car** a new value

    (setq animals (list 'tiger 'cat 'lion))
    (setcar animals 'pig)
    animals


<a id="org927a014"></a>

### setcdr

set the **cdr** a new value

    (setq animals (list 'tiger 'cat 'lion))
    (setcdr animals (list 'pig 'dog))
    animals


<a id="orga61dd8d"></a>

# Day4


<a id="org69f63df"></a>

## defvar

-   it only sets the value of the variable when it doesn't exits
-   if the value has exited,defvar will not overrider the initial value
-   defvar has document string

    (defvar num 3)
    num


<a id="org2bb52ee"></a>

## loops and recursion


<a id="orgb19c085"></a>

### while

    (setq animals '(pig cat tiger dog))
    (defun print-list-element (list)
      (while list
       (print (car list))
       (setq list (cdr list))))
    (print-list-element animals)nil


<a id="org139db4a"></a>

### increment loop

use counter to stop a loop

    (setq count 1)
    (defun counter-stop (num)
      (while (< count num))
       body
       (setq count (+ 1 count))))


<a id="org7b5573e"></a>

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


<a id="org71117a7"></a>

# Day5


<a id="org51f0827"></a>

## numbers


<a id="org619c8de"></a>

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


<a id="org170010a"></a>

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


<a id="orgf324ed5"></a>

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


<a id="orgb4e059c"></a>

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


<a id="org8b871fa"></a>

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


<a id="org77d3f41"></a>

### float rounding

return the float whose value is nearby integer

-   ffloor

    (ffloor 3.5)

-   fceiling
-   ftruncate
-   fround


<a id="org7f76494"></a>

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


<a id="org1183e07"></a>

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


<a id="orgdebe96d"></a>

### random numbers

1.  set the seed to a constant value

        (random "")
    
        
        (random 5)

