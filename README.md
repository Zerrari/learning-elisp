
# Table of Contents

1.  [Day1](#org5dacc55)
    1.  [symbol](#org08a276c)
        1.  [it can be defined as a function and a variable which returns a value](#org475c839)
        2.  [when symbol is in a pair of parenthese and is the first position.It stands for a function.](#orgf5080fe)
        3.  [when symbol is not in a pair of parenthese it stands for a variable.](#org5f9bd1b)
        4.  [a quotation before a pair of parenthese return what is written](#org249d8e2)
        5.  [atoms which in a pair of parenthese are separated by a white space](#org45718c3)
    2.  [evaluate](#org24f9ca3)
        1.  [how](#orgf9a9d5e)
    3.  [function](#org900459e)
        1.  [something basic](#org8d5979a)
        2.  [set and setq](#org9fa1208)
        3.  [buffer](#orgc5d9aa0)
2.  [Day2](#orgf259ee5)
    1.  [function](#org8f8627e)
        1.  [defun](#org915cccd)
        2.  [let](#orgdcb016d)
        3.  [if](#orgdd3faa2)
        4.  [save excurison](#orge5bb23d)
        5.  [beginning of buffer](#org0681392)
        6.  [mark-whole-buffer](#org0f69207)
        7.  [append-to-buffer](#orga28eabf)
3.  [Day3](#org5aa455a)
    1.  [narrowing and widening](#orgbddbde1)
        1.  [key binding](#org2362126)
    2.  [save-restriction](#orgc8ea9be)
        1.  [use save-restriction and save-excurison](#org81a75d6)
    3.  [what-lines](#orgf21e735)
        1.  [](#org7afb297)
    4.  [more about interactive](#org0c7579e)
        1.  [input many arguments](#org429284b)
        2.  ["r" stands for a region](#orgbb0d22b)
        3.  ["p" and "P"](#orgbcc6437)
    5.  [car,cdr and cons](#orgc64327e)
        1.  [car](#org780abc5)
        2.  [cdr](#orgc117517)
        3.  [cons](#org277e297)
        4.  [nthcdr](#org5bf8294)
        5.  [nth](#org0c647f3)
        6.  [setcar](#orgb995884)
        7.  [setcdr](#orgb730a97)
4.  [Day4](#org96b208e)
    1.  [defvar](#orga9a4e44)
    2.  [loops and recursion](#org141b149)
        1.  [while](#orgc48e65b)
        2.  [increment loop](#org2967e27)
        3.  [dolist and dotimes](#org0584cb9)
5.  [Day5](#orgb2edfa1)
    1.  [numbers](#orgc3c39f3)
        1.  [basics](#orgb1b6e42)
        2.  [type predicates](#org6625d44)
        3.  [comparison of numbers](#orgddf8501)
        4.  [conversion](#org94071d9)
        5.  [arithmetic operations](#orga7ae415)
        6.  [float rounding](#org9840a44)
        7.  [bitwise operations](#org9e194b3)
        8.  [mathmatical functions](#org12921ab)
        9.  [random numbers](#org410be5c)


<a id="org5dacc55"></a>

# Day1


<a id="org08a276c"></a>

## symbol


<a id="org475c839"></a>

### it can be defined as a function and a variable which returns a value


<a id="orgf5080fe"></a>

### when symbol is in a pair of parenthese and is the first position.It stands for a function.

1.  

        (+ 1 2)


<a id="org5f9bd1b"></a>

### when symbol is not in a pair of parenthese it stands for a variable.

1.  

        fill-column    


<a id="org249d8e2"></a>

### a quotation before a pair of parenthese return what is written

    '(lion tigger)

    '(lion "a tree")


<a id="org45718c3"></a>

### atoms which in a pair of parenthese are separated by a white space


<a id="org24f9ca3"></a>

## evaluate


<a id="orgf9a9d5e"></a>

### how

move the cursor after the parenthese,and type **C-x C-e** to evaluate the expression


<a id="org900459e"></a>

## function


<a id="org8d5979a"></a>

### something basic

1.  a funtion returns two things

    -   return a value
    -   side effects(*print something on the screen*)


<a id="org9fa1208"></a>

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


<a id="orgc5d9aa0"></a>

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


<a id="orgf259ee5"></a>

# Day2


<a id="org8f8627e"></a>

## function


<a id="org915cccd"></a>

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


<a id="orgdcb016d"></a>

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


<a id="orgdd3faa2"></a>

### if

1.  example

        (if (> 5 4)
             (message "yes")
             (message "no"))

2.  truth and falsehood

    -   anything except nil represents true
    -   the **empty** list is falsehood


<a id="orge5bb23d"></a>

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


<a id="org0681392"></a>

### beginning of buffer

1.  push-mark

    the function stores the current positon of the cursor in mark ring
    
        (defun simple-bob
         (interactive)
         (push-mark)
         (goto-char (point-min)))


<a id="org0f69207"></a>

### mark-whole-buffer

    (defun z-mark-whole-buffer()
      (interactive)
      (progn
        (goto-char (point-max))
        (set-mark (point))
        (goto-char (point-min))))
    (z-mark-whole-buffer)


<a id="orga28eabf"></a>

### append-to-buffer

insert-buffer-substring


<a id="org5aa455a"></a>

# Day3


<a id="orgbddbde1"></a>

## narrowing and widening

with narrowing, the rest of buffer is invisible


<a id="org2362126"></a>

### key binding

**C-x n n** for *narrow-to-rigion*
**C-x n w** for *widen*


<a id="orgc8ea9be"></a>

## save-restriction


<a id="org81a75d6"></a>

### use save-restriction and save-excurison

    (save-excurison
      (save-restriction 
         body))

    (save-restriction 
      (widen)
      (save-excurison
      body))


<a id="orgf21e735"></a>

## what-lines


<a id="org7afb297"></a>

### 

    (defun simple-whatline()
      (interactive)
      (save-restriction
        (widen)
        (save-excursion
          (let ((lines))
    	(setq  lines (count-lines 1 (point)))
    	(message "The line number is %d" lines)))))


<a id="org0c7579e"></a>

## more about interactive

Sepreate string with **\n**


<a id="org429284b"></a>

### input many arguments

-   **"s"** string
-   **"n"** number

    (defun hello(name age country)
      (interactive "sinput your name: \nnage: \nscountry: ")
      (message "name:%s age:%d country:%s" name age country))


<a id="orgbb0d22b"></a>

### "r" stands for a region

    (defun hello1 (start end)
      (interactive "r")
      (message "start:%d end:%d" start end))


<a id="orgbcc6437"></a>

### "p" and "P"

invoke a function by typing **C-u prefix-argument M-x fun-name**

1.  "p" prefix argument convert to a number

2.  "P" prefix argument is a raw type

        (defun hello2 (num)
          (interactive "p")
          (message "%d" num))


<a id="orgc64327e"></a>

## car,cdr and cons

-   cons to construct lists
-   car and cdr to take apart lists


<a id="org780abc5"></a>

### car

the car of the list is the first item

    (car '(tiger lion))


<a id="orgc117517"></a>

### cdr

returns the rest of the list

    (cdr '(tiger lion))
    (cdr '(tiger lion cat))


<a id="org277e297"></a>

### cons

    (cons 'tiger '(lion cat))


<a id="org5bf8294"></a>

### nthcdr

use cdr repeatedly

    (nthcdr 1 '(tiger lion cat))

    (nthcdr 3 '(tiger lion cat))


<a id="org0c647f3"></a>

### nth

use car repeatedly

    (nth 1 '(lion tiger cat))


<a id="orgb995884"></a>

### setcar

set the **car** a new value

    (setq animals (list 'tiger 'cat 'lion))
    (setcar animals 'pig)
    animals


<a id="orgb730a97"></a>

### setcdr

set the **cdr** a new value

    (setq animals (list 'tiger 'cat 'lion))
    (setcdr animals (list 'pig 'dog))
    animals


<a id="org96b208e"></a>

# Day4


<a id="orga9a4e44"></a>

## defvar

-   it only sets the value of the variable when it doesn't exits
-   if the value has exited,defvar will not overrider the initial value
-   defvar has document string

    (defvar num 3)
    num


<a id="org141b149"></a>

## loops and recursion


<a id="orgc48e65b"></a>

### while

    (setq animals '(pig cat tiger dog))
    (defun print-list-element (list)
      (while list
       (print (car list))
       (setq list (cdr list))))
    (print-list-element animals)nil


<a id="org2967e27"></a>

### increment loop

use counter to stop a loop

    (setq count 1)
    (defun counter-stop (num)
      (while (< count num))
       body
       (setq count (+ 1 count))))


<a id="org0584cb9"></a>

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


<a id="orgb2edfa1"></a>

# Day5


<a id="orgc3c39f3"></a>

## numbers


<a id="orgb1b6e42"></a>

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


<a id="org6625d44"></a>

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


<a id="orgddf8501"></a>

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


<a id="org94071d9"></a>

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


<a id="orga7ae415"></a>

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


<a id="org9840a44"></a>

### float rounding

return the float whose value is nearby integer

-   ffloor

    (ffloor 3.5)

-   fceiling
-   ftruncate
-   fround


<a id="org9e194b3"></a>

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


<a id="org12921ab"></a>

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


<a id="org410be5c"></a>

### random numbers

1.  set the seed to a constant value

        (random "")
    
        
        (random 5)

