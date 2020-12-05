
# Table of Contents

1.  [Day1](#org1cd1364)
    1.  [symbol](#org917de38)
    2.  [evaluate](#org2a8e34f)
        1.  [how](#orge5f4a2a)
    3.  [function](#org0e70040)
        1.  [something basic](#orgac21201)
        2.  [set and setq](#org60e7a37)
        3.  [buffer](#org7c00570)
2.  [Day2](#org3b69772)
    1.  [function](#org2dabe84)
        1.  [defun](#orgd4396b6)
        2.  [let](#orgedcd893)
        3.  [if](#orgbfad197)
        4.  [save excurison](#orgfe80e30)
        5.  [beginning of buffer](#orgfc9195d)
        6.  [mark-whole-buffer](#orgffb3f20)
        7.  [append-to-buffer](#orgab6d7b3)
3.  [Day3](#org39b0900)
    1.  [narrowing and widening](#org447811a)
        1.  [key binding](#org39b4aaf)
    2.  [save-restriction](#orgd7cdd56)
        1.  [use save-restriction and save-excurison](#org49a7d02)
    3.  [what-lines](#org4ab74cf)
        1.  [](#orgb4115df)
    4.  [more about interactive](#org51a6bfe)
        1.  [input many arguments](#org23bf112)
        2.  ["r" stands for a region](#orgdfcd7f3)
        3.  ["p" and "P"](#orgd1eec3d)
    5.  [car,cdr and cons](#org32fd40c)
        1.  [car](#org2ca246f)
        2.  [cdr](#org6d96e78)
        3.  [cons](#orgea68aa8)
        4.  [nthcdr](#orge3bafc2)
        5.  [nth](#org6035f33)
        6.  [setcar](#org6e23d6f)
        7.  [setcdr](#org3fbba27)
4.  [Day4](#orgaa467c6)
    1.  [defvar](#org0056ffd)
    2.  [loops and recursion](#org15f1526)
        1.  [while](#orgba5ced0)
        2.  [increment loop](#orgaa20c57)
        3.  [dolist and dotimes](#org438131a)
5.  [Day5](#org554bcc3)
    1.  [numbers](#orgf1ba727)
        1.  [basics](#org88dc113)
        2.  [type predicates](#orgeec60bb)
        3.  [comparison of numbers](#orgbc70e35)
        4.  [conversion](#org4e9cdde)
        5.  [arithmetic operations](#orgb4b72e1)
        6.  [float rounding](#org5e5a00e)
        7.  [bitwise operations](#org07b3df7)
        8.  [mathmatical functions](#org979ba9a)
        9.  [random numbers](#org5695742)
6.  [Day6](#orgd04825b)
    1.  [strings and characters](#org9338b35)
        1.  [predicates for strings](#org1f83ca1)
        2.  [creating strings](#org6abcdf5)
        3.  [modifying strings](#orgb5ce610)
        4.  [comparison of character and strings](#org256eac6)
        5.  [conversion of characters and strings](#org6c20d05)
7.  [Day7](#org7b07a65)
    1.  [regular expressions](#org4289a91)
        1.  [special characters](#org448468d)
        2.  [character classes](#org7df205f)
        3.  [backslash constructs](#org27431c0)
8.  [Day8](#orgd6959fc)
    1.  [strings and characters](#org733d58f)
        1.  [case conversion](#orgea8fd96)
    2.  [lists](#org28a8ee0)
        1.  [the different lists](#orgd075ca6)
        2.  [predicates on lists](#org43a7d2c)
        3.  [accessing elements of lists](#org8ea01ee)
        4.  [building cons cells and lists](#org78fbfb2)
        5.  [modifying list variables](#org032f46a)
        6.  [modifying existing list structure](#orgcc964d2)
        7.  [using lists as sets](#org1ac0144)
9.  [Day9](#orgf004300)
    1.  [lists](#org1e88dfb)
        1.  [using lists as sets](#org27e4b20)
        2.  [association lists (alist for short)](#orge700fd7)
        3.  [property lists (plist for short)](#orgc500943)
    2.  [sequences,arrays and vectors](#org179beca)
        1.  [sequences](#org54989d7)


<a id="org1cd1364"></a>

# Day1


<a id="org917de38"></a>

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


<a id="org2a8e34f"></a>

## evaluate


<a id="orge5f4a2a"></a>

### how

move the cursor after the parenthese,and type **C-x C-e** to evaluate the expression


<a id="org0e70040"></a>

## function


<a id="orgac21201"></a>

### something basic

1.  a funtion returns two things

    -   return a value
    -   side effects(*print something on the screen*)


<a id="org60e7a37"></a>

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


<a id="org7c00570"></a>

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


<a id="org3b69772"></a>

# Day2


<a id="org2dabe84"></a>

## function


<a id="orgd4396b6"></a>

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


<a id="orgedcd893"></a>

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


<a id="orgbfad197"></a>

### if

-   example

    (if (> 5 4)
         (message "yes")
         (message "no"))

-   truth and falsehood
-   anything except nil represents true
-   the **empty** list is falsehood


<a id="orgfe80e30"></a>

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


<a id="orgfc9195d"></a>

### beginning of buffer

1.  push-mark

    the function stores the current positon of the cursor in mark ring
    
        (defun simple-bob
         (interactive)
         (push-mark)
         (goto-char (point-min)))


<a id="orgffb3f20"></a>

### mark-whole-buffer

    (defun z-mark-whole-buffer()
      (interactive)
      (progn
        (goto-char (point-max))
        (set-mark (point))
        (goto-char (point-min))))
    (z-mark-whole-buffer)


<a id="orgab6d7b3"></a>

### append-to-buffer

insert-buffer-substring


<a id="org39b0900"></a>

# Day3


<a id="org447811a"></a>

## narrowing and widening

with narrowing, the rest of buffer is invisible


<a id="org39b4aaf"></a>

### key binding

**C-x n n** for *narrow-to-rigion*
**C-x n w** for *widen*


<a id="orgd7cdd56"></a>

## save-restriction


<a id="org49a7d02"></a>

### use save-restriction and save-excurison

    (save-excurison
      (save-restriction 
         body))

    (save-restriction 
      (widen)
      (save-excurison
      body))


<a id="org4ab74cf"></a>

## what-lines


<a id="orgb4115df"></a>

### 

    (defun simple-whatline()
      (interactive)
      (save-restriction
        (widen)
        (save-excursion
          (let ((lines))
    	(setq  lines (count-lines 1 (point)))
    	(message "The line number is %d" lines)))))


<a id="org51a6bfe"></a>

## more about interactive

Sepreate string with **\n**


<a id="org23bf112"></a>

### input many arguments

-   **"s"** string
-   **"n"** number

    (defun hello(name age country)
      (interactive "sinput your name: \nnage: \nscountry: ")
      (message "name:%s age:%d country:%s" name age country))


<a id="orgdfcd7f3"></a>

### "r" stands for a region

    (defun hello1 (start end)
      (interactive "r")
      (message "start:%d end:%d" start end))


<a id="orgd1eec3d"></a>

### "p" and "P"

invoke a function by typing **C-u prefix-argument M-x fun-name**

1.  "p" prefix argument convert to a number

2.  "P" prefix argument is a raw type

        (defun hello2 (num)
          (interactive "p")
          (message "%d" num))


<a id="org32fd40c"></a>

## car,cdr and cons

-   cons to construct lists
-   car and cdr to take apart lists


<a id="org2ca246f"></a>

### car

the car of the list is the first item

    (car '(tiger lion))


<a id="org6d96e78"></a>

### cdr

returns the rest of the list

    (cdr '(tiger lion))
    (cdr '(tiger lion cat))


<a id="orgea68aa8"></a>

### cons

    (cons 'tiger '(lion cat))


<a id="orge3bafc2"></a>

### nthcdr

use cdr repeatedly

    (nthcdr 1 '(tiger lion cat))

    (nthcdr 3 '(tiger lion cat))


<a id="org6035f33"></a>

### nth

use car repeatedly

    (nth 1 '(lion tiger cat))


<a id="org6e23d6f"></a>

### setcar

set the **car** a new value

    (setq animals (list 'tiger 'cat 'lion))
    (setcar animals 'pig)
    animals


<a id="org3fbba27"></a>

### setcdr

set the **cdr** a new value

    (setq animals (list 'tiger 'cat 'lion))
    (setcdr animals (list 'pig 'dog))
    animals


<a id="orgaa467c6"></a>

# Day4


<a id="org0056ffd"></a>

## defvar

-   it only sets the value of the variable when it doesn't exits
-   if the value has exited,defvar will not overrider the initial value
-   defvar has document string

    (defvar num 3)
    num


<a id="org15f1526"></a>

## loops and recursion


<a id="orgba5ced0"></a>

### while

    (setq animals '(pig cat tiger dog))
    (defun print-list-element (list)
      (while list
       (print (car list))
       (setq list (cdr list))))
    (print-list-element animals)nil


<a id="orgaa20c57"></a>

### increment loop

use counter to stop a loop

    (setq count 1)
    (defun counter-stop (num)
      (while (< count num))
       body
       (setq count (+ 1 count))))


<a id="org438131a"></a>

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


<a id="org554bcc3"></a>

# Day5


<a id="orgf1ba727"></a>

## numbers


<a id="org88dc113"></a>

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


<a id="orgeec60bb"></a>

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


<a id="orgbc70e35"></a>

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


<a id="org4e9cdde"></a>

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


<a id="orgb4b72e1"></a>

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


<a id="org5e5a00e"></a>

### float rounding

return the float whose value is nearby integer

-   ffloor

    (ffloor 3.5)

-   fceiling
-   ftruncate
-   fround


<a id="org07b3df7"></a>

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


<a id="org979ba9a"></a>

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


<a id="org5695742"></a>

### random numbers

1.  set the seed to a constant value

        (random "")
    
        
        (random 5)


<a id="orgd04825b"></a>

# Day6


<a id="org9338b35"></a>

## strings and characters


<a id="org1f83ca1"></a>

### predicates for strings

1.  stringp

    This function returns t if object is a string, nil otherwise
    
        (stringp "asd")  t
    
        (stringp nil)  nil

2.  string-or-null-p

    This function returns t if object is a string or nil. It returns nil otherwise.
    
        (string-or-null-p nil) t

3.  char-or-string-p

    This function returns t if object is a string or a character (i.e., an integer), nil otherwise.
    
        (char-or-string-p ?a) t
    
        (char-or-string-p "asdf") t


<a id="org6abcdf5"></a>

### creating strings

1.  make-string

        (make-string count character &optional multibyte)
    
        (make-string 5 ?x)  "xxxxx"

2.  string

        (string &rest characters)
    
        (string ?a ?d) "ad"

3.  substring

    -   include the start,exclude the end
    -   a negative argument is accpeted (-1 stands for the last index)
    -   default start stands for 0,end stands for the length of the string
    
        (substring string &optional start end)
    
        (substring "asdfg" 1)    "sdfg"
    
        (substring "asdfg" -2 -1)  "f"

4.  concat

        (concat &rest sequences)
    
        (concat "sda" "sad") "sdasad"
    
    if concat receives no argun=ments,it returns empty string.
    
        (concat)  ""

5.  split-string

        (split-string string &optional separators omit-nulls trim)
    
        (split-string "hello world")  "hello" "world"
    
        (split-string "  hello world   ")


<a id="orgb5ce610"></a>

### modifying strings

1.  store-substring

        (store-substring string idx obj)
    
        (store-substring "asdfg" 1 "asd")  aasdg

2.  aset

        (aset string idx char)
    
        ?????(aset "asdfg" 1 ?a)

3.  clear-string

    -   It clears its contents to zero
    
        (clear-string string)
    
        (clear-string "asdad") nil


<a id="org256eac6"></a>

### comparison of character and strings

    (char-equal character1 character2)

    (char-equal ?a ?c) nil

If case-fold-search is non-nil,this function ignores differences in case

    (char-equal ?a ?A)   t
    (setq case-fold-search nil)
    (char-equal ?a ?A)   nil

1.  string= / string-equal

        (string= string1 string2)
    
        (string= "asdf" "asdf")  t
    
        (string= "asdf" "asd")  nil

2.  string< / string-lessp

    -   a string has no characters which is less than any other string
    
        (string< string1 string2)
    
        (string< "" "sad")  t
    
        (string< "sad" "sadf")  t

3.  string-version-lessp

    -   It trests sequences of numbers as if they comprised a base-ten number,then compare them.
    
        (string-version-lessp string1 string2)
    
        (string-version-lessp "12" "1") nil
    
        (string-version-lessp "foo2.png" "foo12.png")   t

4.  string-prefix-p

    -   This function returns non-nil,if string1 is a prefix of string2.
    -   If the ignore-case is non-nil,the comparison ignores case differences.
    
        (string-prefix-p string1 string2 &optional ignore-case)
    
        (string-prefix-p "asdf" "asdfg" 1)  t
    
        (string-prefix-p "asdf" "ASDFF" nil) nil

5.  string-suffix-p

        (string-suffix-p "asdf" "AASDF" 1) t
    
        (string-suffix-p "asdf" "AASDF") nil

6.  compare-strings

    -   If the parts of strings match,it returns t
    -   Otherwise,the value is an integer which how many leading characters agree.
    -   The sign is negative if the string1 is less.
    
        (compare-strings string1 start1 end1 string2 start2 end2 &optional ignore-case)
    
        (compare-strings "asdfg" 0 3 "dfgasd" 3 6)  t

7.  string-distance

        (string-distance string1 string2 &optional bytecompare)
    
    -   It returns the Levenshtein distance.
    
        (string-distance "asdf" "asd")  1


<a id="org6c20d05"></a>

### conversion of characters and strings

1.  number-to-string

        (number-to-string number)
    
        (number-to-string 123)  "123"
    
        (number-to-string -23)  "-23"

2.  string-to-number

        (string-to-number string &optional base)
    
        (string-to-number "1234")  1234
    
        (string-to-number "asd123")  0
    
        (string-to-number "      23 apples")  23
    
        (string-to-number "23" 8) 19

3.  char-to-string

        (char-to-string character)
    
        (char-to-string ?a)  "a"

4.  (string-to-char)

    -   The function returns the first character of the string.
    -   If the string is empty,it returns 0.
    
        (string-to-char string)
    
        (string-to-char "ASD") ?A
    
        (string-to-char "") 0

5.  formatting strings

        (format string &rest objects)
    
        (format "ASD")  "ASD"
    
    1.  valid format specifications
    
        -   %s
        
        print without "" 
        
            (format "This is an %s" "apple") "This is an apple"
        
        -   %S
        
        print with "" and \\
        
            (format "This is an %S" "apple")  "This is an \"apple\""
        
        -   %o
        
        replace the specification with the base-eight number
        It also accepts float point as an integer,droppong any fraction
        
            (format "%o" 23)  "27"
        
            (format "%o" 23.5)  "27"
        
        -   %x
        
        base-sixteen
        with lower case
        
            (format "%x" 29)  "1d"
        
        -   %X
        
        base-sixteen 
        with upper case
        
            (format "%X" 29)  "1D"
        
        -   %c
        
        repalce the specification with the character
        
            (format "This is %c" ?a) "This is a"
        
        -   %f
        
            (format "%f" 13.5)  "13.500000"
        
        -   %%
        
        replace the specification with single "%"
    
    2.  field numbers in specification
    
        It causes the format specification to convert the argument with the given number.
        
            (format "%s %1$s %% %3$s" "x" "y" "z")  "x x % z"
    
    3.  flag characters
    
        After the '%' and field numbers,ypu can put flag characters.
        
        -   '+'
        
        a plus sign before a nonnegative number
        
            (format "%+d" 23)   "+23"
        
        -   '#'
        
            (format "%#o" 23)   "027"
        
            (format "%#x" 29)  "0x1d"
        
        -   '0'
        
        the padding consists of '0' characters instead of spaces
        this flag is ingored for specification like "%s" "%S" or "%c"
        
            (format "%06d" 23) "000023"
        
            (format "%6d" 23)  "      23"
        
        -   '-'
        
        the flag causes any padding inserted on the right
        If both '0' and '-' are present,'0' is ignored.
        
            (format "%-06d" 23)   "23      "
        
            (format "%-6d" 23)    "23      "

6.  format-message

        (format-message string &rest objects)
    
        (format-message "'asdf'")  'asdf'


<a id="org7b07a65"></a>

# Day7


<a id="org4289a91"></a>

## regular expressions


<a id="org448468d"></a>

### special characters

-   '.'

It matches any single character except a newline

-   '\*'

It is a postfix operator that matches preceding expression repetitively as many times as possible.

-   '+'

It is a postfix operator that matches preceding expression at least once.

-   '?'

It is a postfix operator that matches preceding expression either once or not at all.

-   '\*?','+?','??'

It matches the smallest substring.

-   '[&#x2026;]'

It is a character alternative.
The characters between the brackets are what this character alternative can match.
'c[ad]\*r' matches "cadr","car","cr" etc.

-   '[^&#x2026;]'

It matches any character except the specified ones

-   '^'

It matches the empty string,but only on the beginning of the line.

-   '$'

It is similiar to the '^',but on the end of the line.

-   '\\'

It quotes the special characters(including '\\') and introduces additional special constructs.


<a id="org7df205f"></a>

### character classes

-   '[:ascii:]'

This matches any ASCII character.

-   '[:alnum:]'

This matches any letter or digit.

-   '[:digit:]'

This matches '0' through '9'.

-   '[:lower:]'

This matches any lower-case letter.
If case-fold-search is non-nil,it also matches any upper-case letter.

-   '[:upper:]'

It is similiar with '[:upper:]'.

-   '[:nonascii:]'

It matches any non-ASCII character.

-   '[:xdigit:]'

It matches any hexadecimal digits.

-   '[:punct:]'

It matches any punctuation character.

    "[[:ascii:]]"


<a id="org27431c0"></a>

### backslash constructs

-   '\\|'

'a\\|b' matches either "a" or "b" but on other string.

-   '\\{m\\}'

It is a postfix operator that repeats the previous pattern exactly m times.

    'x\{5\}' matches 'xxxxx'

-   '\\{m,n\\}'

It is a postfix operator that repeats the previous pattern with a minimum of m and a maximum of n.
If m is omitted,the minimun is 0.
If n is omitted,there is no maximum.

-   '\(...\)'
-   To enclose the set of '\\|' alternatives

    '\(bar\|foo\)x'
    it matches either 'barx' or 'foox'

1.  To enclose a complicated expression for the postfix operatores '\*','+' or '?'

    'ba\(na\)*'
    it matches 'ba','bana','banana' and so on


<a id="orgd6959fc"></a>

# Day8


<a id="org733d58f"></a>

## strings and characters


<a id="orgea8fd96"></a>

### case conversion

1.  downcase

        (downcase string-or-char)
    
        (downcase ?Z)     z/122
    
        (downcase "WQER")   "wqer"

2.  upcase

        (upcase string-or-char)
    
        (upcase ?z)    Z/90
    
        (upcase "asdf")   "ASDF"

3.  capitalize

    This function capitalize the string or char.
    That means the first letter of every word converted to the upcase,
    and the rest of the word converted to the downcase.
    
        (capitalize string-or-char)
    
        (capitalize ?z) Z
    
        (capitalize "this is an apple") "This Is An Apple"
    
        (capitalize "thIS is AN APPLe") This Is An Apple

4.  upcase-initials

    It cpnverts the initials of ever word to the upcase,without any change to the rest of every word.
    
        (upcase-initials string-or-char)
    
        (upcase-initials "THIS iS an apple.") THIS IS An Apple.


<a id="org28a8ee0"></a>

## lists


<a id="orgd075ca6"></a>

### the different lists

1.  proper lists

    The cdr of the last cons cell in a list is 'nil'.

2.  circular lists

3.  dotted lists

    The cdr of the last cons cell in a list is come value other than 'nil'.


<a id="org43a7d2c"></a>

### predicates on lists

1.  consp

    It return t if object is a cons cell.     
    
        (consp object)
    
        (consp '(rose cat))      t
    
        (consp (cons 'cat 1))  t
    
        (consp '(rose cat dog))            t
        (consp (list 'rose 'cat 'dog))     t
        (consp ())                         nil

2.  listp

    It returns t if the object is a cons cell or nil.
    
        (listp (cons 1 2))   t
        (listp ())           t

3.  nlistp

    It retuns t if the object is not a list.
    
        (nlistp 3)        t

4.  null

    It returns t  if the object is nil.
    
        (null ())         t
        (null '())        t

5.  proper-list-p

    It returns the length of the list,if it is a proper list.
    Else it returns nil.
    
        (proper-list-p '(1 2 34 4))       4
        (proper-list-p '(1 2 . 3))        nil

6.  atom

    It returns t if the object is an atom.
    All objects except cons cell are atoms.
    
        (atom '(1 23 3))    nil
        (atom "asd")        t
        (atom 1)            t


<a id="org8ea01ee"></a>

### accessing elements of lists

1.  car

    It returns the first slot of the cons cell.
    
        (car cons-cell)
    
        (car '(1 2 3 4))    1

2.  cdr

    It returns the second slot of the cons cell.
    
        (cdr cons-cell)
    
        (cdr '( 1 2 3))    (2 3)

3.  car-safe

    It lets you take the car of the object  while avoiding errors for other types.
    
        (car-safe object)
    
        (car-safe 1)    return nil and no response of error
        (car-safe '(1 2 3))    1

4.  cdr-safe

    It is similiar to the car-safe.

5.  pop

    It returns the car of the list,and saves the cdr of the list to the listname.
    destructive function
    
        (pop listname)
    
        (setq animals '(rose dog cat))  (rose dog car)
        (pop animals)                    "rose"
        animals                          (dog cat)

6.  nth

    It returns the nth elsement of the list.
    If the length of the list is n or less,it returns nil.
    
        (nth n list)
    
        (nth 2 '(1 2 3 4))       3

7.  nthcdr

    It returns the nth cdr of the list.
    if n is 0,it returns the list.
    If the length is  or less,it returns nil.
    
        (nthcdr n list)
    
        (nthcdr 2 '(1 2 3))     (3)
        (nthcdr 0 '(1 2 3))     (1 2 3)
        (nthcdr 3 '( 1 2 3))    nil

8.  last

    It returns the last link of the list.
    If n is "non-nil", it returns the nth-to-last link.
    
        (last list &optional n)
    
        (last '(1 2 3))        (3)
        (last '(1 2 3) 2)      (2 3)
        (last '(1 2 3) 4)      (1 2 3)

9.  safe-length

    It returns the length of the object while avoiding errors of other types.
    It returns 0,if the object is not nil or a cons cell.
    
        (safe-length 1)           0
        (safe-length '( 1 2 3))   3

10. caar,cddr,cadr

        (cadr '(1 2 3))        2
        (car (cdr '(1 2 3)))   2

11. butlast

    It returns the list without the last element
    If n is greater than 0,it makes a copy of the list so as not to damage the original list.
    
        (butlast x &optional n)
    
        (setq animals '(cat dog rose))     (cat dog rose)
        (butlast animals)                 (cat dog)
        animals                          (cat dog rose lily)
        (setq animals '(cat dog rose lily)) (cat dog rose lily)
        (butlast animals 2)                 (cat dog)
        animals                             (cat dog rose lily)
    
        (butlast '(1 2 3))         (1 2)
        (butlast '(1 2 3 4 5) 2)   (1 2 3)

12. nbutlast

    This is version of butlast by destructively modifying the list.
    
        (setq animals '(cat dog rose lily)) (cat dog rose lily)
        (nbutlast animals 2)                 (cat dog)
        animals                             (cat dog)


<a id="org78fbfb2"></a>

### building cons cells and lists

1.  cons

        (cons object1 object2)
    
        (cons 1 2)   (1 . 2)
        (cons 1 '(2)) (1 2)

2.  list

        (list &rest objects)
    
        (list 1 2 3 4 5 ) (1 2 3 4 5)

3.  make-list

        (make-list length object)
    
        (make-list 3 'x)    (x x x)

4.  append

    It is not a destructive function.
    
        (append &rest sequences)
    
        (setq list '(1 2 3))         (1 2 3)
        (append list '(4 5))         (1 2 3 4 5)
        list                         (1 2 3)

5.  copy-tree

    It returns a copy of the tree.
    It the vecp is non-nil,it also copies the vector.
    
        (copy-tree tree &optional vecp)
    
        (copy-tree '(1 2 3))     (1 2 3)

6.  flatten-tree

    It returns a tree with the elements in the same order.
    
        (flatten-tree tree)
    
        (flatten-tree '(1 2 3 (4 5) (6 (7 . 8))))        (1 2 3 4 5 6 7 8)

7.  number-sequence

    It returns a sequence of numbers starting at the **from**,increasing by the **separation** and ending at pr before **to**.
    default separation is 1.
    
        (number-sequence from &optional to separation)
    
        (number-sequence 1 4)  (1 2 3 4)    
        (number-sequence 4 1 -1) (4 3 2 1)
        (number-sequence 1 6 2)  (1 3 5)

8.  modifying list variabels


<a id="org032f46a"></a>

### modifying list variables

1.  push

        (push element listname)
    
        (setq animals '(cat dog))   (cat dog)
        (push 'lion animals)         (lion cat dog)
        animals                     (lion cat dog)

2.  add-to-list

    -   It sets variable symbol by consing element onto the old value.
    -   If the element is not the value of the list,it will be added.
    -   If the compare-fn is nil,it use **equal** to compare.
    -   if the append is non-nil,the element will be added at the end of the list.
    
        (add-to-list symbol element &optional append comapre-fn)
    
        (setq list '(1 2 3 4)) (1 2 3 4)
        (add-to-list 'list 1)  (1 2 3 4)
        (add-to-list 'list 5 nil) (1 2 3 4 5)
    
        (setq list '(1 2 3 4))
        (add-to-list 'list 5)  (5 1 2 3 4)

3.  add-to-ordered-list

        (add-to-ordered-list symbol element &optional order)
    
        (add-to-ordered-list)


<a id="orgcc964d2"></a>

### modifying existing list structure

1.  setcar

    It returns value object.
    
        (setcar cons object)
    
        (setq list '(1 2 3))    (1 2 3)
        (setcar list 5)         5
        list                    (5 2 3) 

2.  setcdr

    It returns the value object.
    
        (setcdr cons object)
    
        (setq list '(1 2 3 4))  (1 2 3 4)
        (setcdr list 5)         5
        list                    (1 . 5) 

3.  nconc

    It return a list containing all elements in the lists.
    
        (nconc &rest lists)
    
        (nconc '(1 2 3) '(4 5))     (1 2 3 4 5)


<a id="org1ac0144"></a>

### using lists as sets

1.  memq

    -   It tests if the object is a member of a list.
    -   If so,it returns the list starting with the first occurrence of object.
    -   If not,it returns nil.
    
        (memq object list)
    
        (memq 'a '(q w e t a s d))   (a s d)

2.  delq

    -   It removes the elements equaling the object.
    -   It returns the resulting list.
    
        (delq object list)
    
        (setq list '(1 2 3 4))   (1 2 3 4)
        (delq 1 list)            (2 3 4)
        list                     (1 2 3 4)
        (delq 2 list)            (1 3 4)
        list                     (1 3 4) 
    
        (delq 'a '(a d f a))    (d f)
        (delq 'a '(q w e r))    (q w e r) 

3.  remq

    -   It returns a copy of list
    
        (remq object list)
    
        (setq list '(1 2 3 4))   (1 2 3 4)
        (remq 1 list)            (2 3 4)
        list                     (1 2 3 4)

4.  memql

    -   It tests if the object is a member of the list.
    -   Comparing with **eql**.
    -   It returns similair to **memq**.
    
        (memql object list)
    
        (memql 1 '(1.0 2 3))     nil
        (memql 1 '(1 2 3))       (1 2 3)


<a id="orgf004300"></a>

# Day9


<a id="org1e88dfb"></a>

## lists


<a id="org27e4b20"></a>

### using lists as sets

1.  member

    It tests if the object is a member of the list,comparing with **equal**.
    
        (member object list)
    
        (member 2 '(1 2 3))      (2 3)
    
        (member "foo" '("foo" "qwer"))     ("foo" "qwer")

2.  delete

        (delete object sequence)
    
        (delete 1 '(1 2 3))   (2 3)

3.  remove

    It is the non-destructive version of **delete**.
    
        (remove object sequence)
    
        (setq list '(1 2 3 4))    (1 2 3 4)
        (remove 3 list)           (1 2 4)
        list                      (1 2 3 4) 


<a id="orge700fd7"></a>

### association lists (alist for short)

-   It records a mapping from key to value.
-   It is a list of cons cells.
-   The car of the cons cell is called **key**.
-   The cdr of the cons cell is called **value**.

    ((pine . cones)
     (oak . acorns))

1.  assoc

    -   It returns the first association for key in alist.
    -   If testfn is nil,it is regarded as **equal**.
    
        (assoc key alist &optional testfn)
    
        (assoc 'rose '((rose . red) (lily . white)))    (rose . red)

2.  rassoc

    -   It returns the first association with value in alist.
    
        (rassoc value alist)
    
        (rassoc 'red '((rose . red) (lily . white)))     (rose . red)

3.  assq

    -   It is like **assoc**,but it compares with **eq**.
    
        (assq key alist)
    
        (assq 'rose '((rose . red) (lily . white)))    (rose . red)

4.  alist-get

    -   If the association isn't found,it returns default.
    -   If **remove** is non-nil,it remove the key's association when the new value is **eql** to **default**.
    
        (alist-get key alist &optional default remove testfn)
    
        (alist-get 'rose '((rose . red) (lily white)))         red          
    
        (alist-get 'cat '((rose . red) (lily white)) 'dog) dog
    
        (setq alist '((rose . red) (lily . white)))
        (alist-get 'rse alist 'rose 1)
        alist

5.  rassq

    -   It returns the first association with value in alist
    
        (rassq value alist)
    
        (rassq 'red '((rose . red) (lily white)))    (rose . red)

6.  assoc-default

        (assoc-default key alist &optional test default)

7.  copy-alist

    -   It creates a new copy of alist
    
        (copy-alist alist)
    
        (copy-alist '((rose . red) (lily . white)))        ((rose . red) (lily . white))

8.  assq-delete-all

    -   It deletes all the association whose car is equal to key.
    -   For correct results,use return value of **assq-delete-all**
    
        (assq-delete-all key alist)
    
        (setq alist '((foo . 1) (qwer . 2) (foo . 3)))      ((foo . 1) (qwer . 2) (foo . 3))
        (assq-delete-all 'foo alist)    ((qwer . 2))
        alist                           ((foo . 1) (qwer . 2))

9.  rassq-delete-all

    -   It deletes all the association whose cdr is equal to value.
    -   It is similiar to **assq-delete-all**
    
        (rassq-delete-all value alist)

10. let-alist

    -   Creates a binding for each symbol used as keys the association list alist, prefixed with dot.
    
        (let-alist alist body)
    
        (setq alist '((rose . red) (lily white)))             ((rose . red) (lily . white))
        (let-alist alist (if (eq .rose 'red) .lily))          (white)


<a id="orgc500943"></a>

### property lists (plist for short)

-   It is a list of paired elements

    (pine cones number (1 2 3) color "blue")

1.  plist-get

        (plist-get plist property)
    
        (plist-get '(foo 4) 'foo)             4
        (plist-get '(foo 4 qwer) 'qwer)       nil

2.  plist-put

    -   For correct results,it is better to use the return value of **plist-put**.
    
        (plist-put plist property value)
    
        (plist-put '(foo 1 qwe 2) 'asd 3)       (foo 1 qwe 2 asd 3)

3.  lax-plist-get

    -   Like **plist-get**,but it compares with **equal**.

4.  lax-plist-put

    -   Like **plist-put**,but it compares with **equal**.

5.  plist-member

    -   It can distinguish between the missing property and a property with the value **nil**.
    
        (plist-member plist property)


<a id="org179beca"></a>

## sequences,arrays and vectors

<table border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">


<colgroup>
<col  class="org-left" />
</colgroup>
<tbody>
<tr>
<td class="org-left">sequence</td>
</tr>


<tr>
<td class="org-left">list</td>
<td class="org-left">array</td>
</tr>


<tr>
<td class="org-left">&#xa0;</td>
<td class="org-left">vector</td>
</tr>


<tr>
<td class="org-left">&#xa0;</td>
<td class="org-left">string</td>
</tr>


<tr>
<td class="org-left">&#xa0;</td>
<td class="org-left">char-table</td>
</tr>


<tr>
<td class="org-left">&#xa0;</td>
<td class="org-left">bool-table</td>
</tr>


<tr>
<td class="org-left">&#xa0;</td>
<td class="org-left">&#xa0;</td>
</tr>
</tbody>
</table>


<a id="org54989d7"></a>

### sequences

1.  sequencep / seqp

    -   It returns **t**,if the object is sequence.
    
        (sequencep object)
    
        (seqp '(1 2 3))      t
        (seqp [1 2 3 4])     t
        (seqp "qwer")        t

2.  length

        (length object)
    
        (length '( 1 2 3)) 3
        (length "string")  6
        (length [1 2 3 (1 2 3)]) 4

3.  elt

        (elt sequence index)
    
        (elt '(1 2 3) 0)   1
        (elt "string" 3)   'i' 

4.  copy-sequence

        (copy-sequence seqr)
    
        (copy-sequence '(1 2 3))      (1 2 3)

5.  reverse

    -   It creates a new sequence.
    -   Original sequence isn't be reversed.
    -   Char-tables cannot be reversed.
    
        (reverse sequence)
    
        (reverse '(1 2 3))      (3 2 1)
        (setq list '(1 2 3))    (1 2 3) 
        (reverse list)          (3 2 1)
        list                    (1 2 3)
    
        (reverse "string")     "gnitrs"

6.  nreverse

    -   The original sequence may be modified.
    -   It doesn't work with **strings**.
    
        (nreverse sequence)
    
        (setq list '(1 2 3))    (1 2 3) 
        (nreverse list)         (3 2 1)
        list                    (1) 

7.  sort

    -   It may be used only for lists and vectors.
    -   Its argument **predicate** must be a function accepting two arguments.
    
        (sort sequence predicate)
    
        (setq nums '( 2 4 3 1 6 5 0)) (2 4 3 1 6 5 0)
        (sort nums #'<)               (0 1 2 3 4 5 6)
        nums                          (2 3 4 5 6)

8.  seq-elt

        (seq-elt sequence index)
    
        (seq-elt '(1 2 3 4 5) 2)        3

9.  seq-length

    -   It returns the number of elements.
    
        (seq-length '(1 2 3 4))     4
        (seq-length [1 2 3 (1 2)])  4
        (seq-length "string")       6

10. seq-drop

    -   It returns all but the first n elements of sequence.
    -   If n is negative or zero,it returns the full sequence.
    
        (seq-drop sequence n)
    
        (seq-drop '(1 2 3 4 5) 3)   (4 5)
        (seq-drop "string" 3)       "ing"

11. seq-take

    -   It returns the first n element of sequence.
    -   If n is negative or zero,it returns **nil**.
    
        (seq-take sequence n)
    
        (seq-take '(1 2 3 4 5 6) 2)   (1 2)

12. seq-take-while

        (seq-take-while predicate sequence)

13. seq-drop-while

