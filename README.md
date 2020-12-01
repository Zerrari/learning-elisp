
# Table of Contents

1.  [Day1](#org6c4089a)
    1.  [symbol](#org24f4e73)
    2.  [evaluate](#orgaf597f6)
        1.  [how](#orgcd0f688)
    3.  [function](#orgc7cbb81)
        1.  [something basic](#orgb4264a5)
        2.  [set and setq](#org9c0b4d5)
        3.  [buffer](#org2ca5e13)
2.  [Day2](#orgdf2118d)
    1.  [function](#orgdb5968f)
        1.  [defun](#org62cc58a)
        2.  [let](#orgf88c164)
        3.  [if](#orgc202cf4)
        4.  [save excurison](#org90e3bb4)
        5.  [beginning of buffer](#org6e12633)
        6.  [mark-whole-buffer](#orgc3c2123)
        7.  [append-to-buffer](#org7a5763a)
3.  [Day3](#org42c6ca9)
    1.  [narrowing and widening](#org1e2c5b3)
        1.  [key binding](#orgaac7cdb)
    2.  [save-restriction](#org53e879d)
        1.  [use save-restriction and save-excurison](#orge63a518)
    3.  [what-lines](#orgf913786)
        1.  [](#org8254334)
    4.  [more about interactive](#org708cba6)
        1.  [input many arguments](#orgd3a709d)
        2.  ["r" stands for a region](#orge70c1ed)
        3.  ["p" and "P"](#org3804e76)
    5.  [car,cdr and cons](#org48c0895)
        1.  [car](#org1bc730b)
        2.  [cdr](#org65f2ebd)
        3.  [cons](#org389c047)
        4.  [nthcdr](#org7bbe263)
        5.  [nth](#orgb238ca6)
        6.  [setcar](#orgf72465f)
        7.  [setcdr](#org759507e)
4.  [Day4](#org8f9fa50)
    1.  [defvar](#org140785d)
    2.  [loops and recursion](#org110f555)
        1.  [while](#org22cd503)
        2.  [increment loop](#org33afd2a)
        3.  [dolist and dotimes](#orge8b82d3)
5.  [Day5](#orgf2b77db)
    1.  [numbers](#org77bb5c5)
        1.  [basics](#org78c61ca)
        2.  [type predicates](#orgca14061)
        3.  [comparison of numbers](#orgcc51307)
        4.  [conversion](#orgf53a16d)
        5.  [arithmetic operations](#org56a5661)
        6.  [float rounding](#orge40a332)
        7.  [bitwise operations](#org3067c3a)
        8.  [mathmatical functions](#orgfa01acb)
        9.  [random numbers](#org1f660ad)
6.  [Day6](#org0f30cad)
    1.  [strings and characters](#org8f90037)
        1.  [predicates for strings](#orge613dc1)
        2.  [creating strings](#orge5c45b3)
        3.  [modifying strings](#org8c96885)
        4.  [comparison of character and strings](#org1b66bd4)
        5.  [conversion of characters and strings](#org3e37097)


<a id="org6c4089a"></a>

# Day1


<a id="org24f4e73"></a>

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


<a id="orgaf597f6"></a>

## evaluate


<a id="orgcd0f688"></a>

### how

move the cursor after the parenthese,and type **C-x C-e** to evaluate the expression


<a id="orgc7cbb81"></a>

## function


<a id="orgb4264a5"></a>

### something basic

1.  a funtion returns two things

    -   return a value
    -   side effects(*print something on the screen*)


<a id="org9c0b4d5"></a>

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


<a id="org2ca5e13"></a>

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


<a id="orgdf2118d"></a>

# Day2


<a id="orgdb5968f"></a>

## function


<a id="org62cc58a"></a>

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


<a id="orgf88c164"></a>

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


<a id="orgc202cf4"></a>

### if

-   example

    (if (> 5 4)
         (message "yes")
         (message "no"))

-   truth and falsehood
-   anything except nil represents true
-   the **empty** list is falsehood


<a id="org90e3bb4"></a>

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


<a id="org6e12633"></a>

### beginning of buffer

1.  push-mark

    the function stores the current positon of the cursor in mark ring
    
        (defun simple-bob
         (interactive)
         (push-mark)
         (goto-char (point-min)))


<a id="orgc3c2123"></a>

### mark-whole-buffer

    (defun z-mark-whole-buffer()
      (interactive)
      (progn
        (goto-char (point-max))
        (set-mark (point))
        (goto-char (point-min))))
    (z-mark-whole-buffer)


<a id="org7a5763a"></a>

### append-to-buffer

insert-buffer-substring


<a id="org42c6ca9"></a>

# Day3


<a id="org1e2c5b3"></a>

## narrowing and widening

with narrowing, the rest of buffer is invisible


<a id="orgaac7cdb"></a>

### key binding

**C-x n n** for *narrow-to-rigion*
**C-x n w** for *widen*


<a id="org53e879d"></a>

## save-restriction


<a id="orge63a518"></a>

### use save-restriction and save-excurison

    (save-excurison
      (save-restriction 
         body))

    (save-restriction 
      (widen)
      (save-excurison
      body))


<a id="orgf913786"></a>

## what-lines


<a id="org8254334"></a>

### 

    (defun simple-whatline()
      (interactive)
      (save-restriction
        (widen)
        (save-excursion
          (let ((lines))
    	(setq  lines (count-lines 1 (point)))
    	(message "The line number is %d" lines)))))


<a id="org708cba6"></a>

## more about interactive

Sepreate string with **\n**


<a id="orgd3a709d"></a>

### input many arguments

-   **"s"** string
-   **"n"** number

    (defun hello(name age country)
      (interactive "sinput your name: \nnage: \nscountry: ")
      (message "name:%s age:%d country:%s" name age country))


<a id="orge70c1ed"></a>

### "r" stands for a region

    (defun hello1 (start end)
      (interactive "r")
      (message "start:%d end:%d" start end))


<a id="org3804e76"></a>

### "p" and "P"

invoke a function by typing **C-u prefix-argument M-x fun-name**

1.  "p" prefix argument convert to a number

2.  "P" prefix argument is a raw type

        (defun hello2 (num)
          (interactive "p")
          (message "%d" num))


<a id="org48c0895"></a>

## car,cdr and cons

-   cons to construct lists
-   car and cdr to take apart lists


<a id="org1bc730b"></a>

### car

the car of the list is the first item

    (car '(tiger lion))


<a id="org65f2ebd"></a>

### cdr

returns the rest of the list

    (cdr '(tiger lion))
    (cdr '(tiger lion cat))


<a id="org389c047"></a>

### cons

    (cons 'tiger '(lion cat))


<a id="org7bbe263"></a>

### nthcdr

use cdr repeatedly

    (nthcdr 1 '(tiger lion cat))

    (nthcdr 3 '(tiger lion cat))


<a id="orgb238ca6"></a>

### nth

use car repeatedly

    (nth 1 '(lion tiger cat))


<a id="orgf72465f"></a>

### setcar

set the **car** a new value

    (setq animals (list 'tiger 'cat 'lion))
    (setcar animals 'pig)
    animals


<a id="org759507e"></a>

### setcdr

set the **cdr** a new value

    (setq animals (list 'tiger 'cat 'lion))
    (setcdr animals (list 'pig 'dog))
    animals


<a id="org8f9fa50"></a>

# Day4


<a id="org140785d"></a>

## defvar

-   it only sets the value of the variable when it doesn't exits
-   if the value has exited,defvar will not overrider the initial value
-   defvar has document string

    (defvar num 3)
    num


<a id="org110f555"></a>

## loops and recursion


<a id="org22cd503"></a>

### while

    (setq animals '(pig cat tiger dog))
    (defun print-list-element (list)
      (while list
       (print (car list))
       (setq list (cdr list))))
    (print-list-element animals)nil


<a id="org33afd2a"></a>

### increment loop

use counter to stop a loop

    (setq count 1)
    (defun counter-stop (num)
      (while (< count num))
       body
       (setq count (+ 1 count))))


<a id="orge8b82d3"></a>

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


<a id="orgf2b77db"></a>

# Day5


<a id="org77bb5c5"></a>

## numbers


<a id="org78c61ca"></a>

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


<a id="orgca14061"></a>

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


<a id="orgcc51307"></a>

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


<a id="orgf53a16d"></a>

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


<a id="org56a5661"></a>

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


<a id="orge40a332"></a>

### float rounding

return the float whose value is nearby integer

-   ffloor

    (ffloor 3.5)

-   fceiling
-   ftruncate
-   fround


<a id="org3067c3a"></a>

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


<a id="orgfa01acb"></a>

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


<a id="org1f660ad"></a>

### random numbers

1.  set the seed to a constant value

        (random "")
    
        
        (random 5)


<a id="org0f30cad"></a>

# Day6


<a id="org8f90037"></a>

## strings and characters


<a id="orge613dc1"></a>

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


<a id="orge5c45b3"></a>

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


<a id="org8c96885"></a>

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


<a id="org1b66bd4"></a>

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


<a id="org3e37097"></a>

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

7.  

