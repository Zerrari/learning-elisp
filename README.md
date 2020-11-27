
# Table of Contents

1.  [Day1](#orgf69323a)
    1.  [symbol](#orgb40f1ab)
        1.  [it can be defined as a function and a variable which returns a value](#org8559aea)
        2.  [when symbol is in a pair of parenthese and is the first position.It stands for a function.](#org66ca7e0)
        3.  [when symbol is not in a pair of parenthese it stands for a variable.](#org6b3bad7)
        4.  [a quotation before a pair of parenthese return what is written](#orgaef0143)
        5.  [atoms which in a pair of parenthese are separated by a white space](#org38299b9)
    2.  [evaluate](#org31d6f62)
        1.  [how](#orgd34ec92)
    3.  [function](#orgd428e71)
        1.  [something basic](#org58cfe95)
        2.  [set and setq](#org2833e8e)
        3.  [buffer](#orgc8a6576)
2.  [Day2](#org2b022fa)
    1.  [function](#org00f5108)
        1.  [defun](#org172d2ae)
        2.  [let](#org47f94d6)
        3.  [if](#orga7f8aa2)
        4.  [save excurison](#org3a54bee)
        5.  [beginning of buffer](#orgce1aaa8)
        6.  [mark-whole-buffer](#orgbdfdffe)
        7.  [append-to-buffer](#orgcdef924)
3.  [Day3](#orge712774)
    1.  [narrowing and widening](#org07503cf)
        1.  [key binding](#orgf1d921f)
    2.  [save-restriction](#org9fae82c)
        1.  [use save-restriction and save-excurison](#org8c974e2)
    3.  [what-lines](#orgbbb3489)
        1.  [](#org841b921)
    4.  [more about interactive](#orgddd60a9)
        1.  [input many arguments](#orgc6c23e7)
        2.  ["r" stands for a region](#org975279c)
        3.  ["p" and "P"](#orgd99f250)
    5.  [car,cdr and cons](#org1600c4f)
        1.  [car](#orgef870da)
        2.  [cdr](#orgfd62f36)
        3.  [cons](#org2d93339)
        4.  [nthcdr](#org4356095)
        5.  [nth](#org6ffd679)
        6.  [setcar](#orgff6ddbb)
        7.  [setcdr](#orgc1854a4)
4.  [Day4](#orgd1cb74f)
    1.  [defvar](#org8000156)
    2.  [loops and recursion](#org03ebde3)
        1.  [while](#org7d4c263)
        2.  [increment loop](#org00f424b)
        3.  [dolist and dotimes](#org6c90ad8)


<a id="orgf69323a"></a>

# Day1


<a id="orgb40f1ab"></a>

## symbol


<a id="org8559aea"></a>

### it can be defined as a function and a variable which returns a value


<a id="org66ca7e0"></a>

### when symbol is in a pair of parenthese and is the first position.It stands for a function.

1.  

        (+ 1 2)


<a id="org6b3bad7"></a>

### when symbol is not in a pair of parenthese it stands for a variable.

1.  

        fill-column    


<a id="orgaef0143"></a>

### a quotation before a pair of parenthese return what is written

    '(lion tigger)

    '(lion "a tree")


<a id="org38299b9"></a>

### atoms which in a pair of parenthese are separated by a white space


<a id="org31d6f62"></a>

## evaluate


<a id="orgd34ec92"></a>

### how

move the cursor after the parenthese,and type **C-x C-e** to evaluate the expression


<a id="orgd428e71"></a>

## function


<a id="org58cfe95"></a>

### something basic

1.  a funtion returns two things

    -   return a value
    -   side effects(*print something on the screen*)


<a id="org2833e8e"></a>

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


<a id="orgc8a6576"></a>

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


<a id="org2b022fa"></a>

# Day2


<a id="org00f5108"></a>

## function


<a id="org172d2ae"></a>

### defun

1.  template

    (defun fun-name (arguments)
         "optional document"
         (optional interactive)
         (body))
    
    1.  example
    
            (defun add (x y)
                 "add two numbers"
                 (+ x y))
            (add 3 4) 

2.  interactive(*need input in a minibuffer*)

    1.  example
    
            (defun add (x)
                 (interactive "p")  
                 (message "The result is %d" (+ x 3)))

3.  invoke an interactive function by typing **C-u argument M-x fun-name**

4.  **p** stands for prefix which means you should type before invoke a function


<a id="org47f94d6"></a>

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


<a id="orga7f8aa2"></a>

### if

1.  example

        (if (> 5 4)
             (message "yes")
             (message "no"))

2.  truth and falsehood

    -   anything except nil represents true
    -   the **empty** list is falsehood


<a id="org3a54bee"></a>

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
      body&#x2026;)


<a id="orgce1aaa8"></a>

### beginning of buffer

1.  push-mark

    the function stores the current positon of the cursor in mark ring
    
        (defun simple-bob
         (interactive)
         (push-mark)
         (goto-char (point-min)))


<a id="orgbdfdffe"></a>

### mark-whole-buffer

(defun z-mark-whole-buffer()
  (interactive)
  (progn
    (goto-char (point-max))
    (set-mark (point))
    (goto-char (point-min))))
(z-mark-whole-buffer)


<a id="orgcdef924"></a>

### append-to-buffer

insert-buffer-substring


<a id="orge712774"></a>

# Day3


<a id="org07503cf"></a>

## narrowing and widening

with narrowing, the rest of buffer is invisible


<a id="orgf1d921f"></a>

### key binding

**C-x n n** for *narrow-to-rigion*
**C-x n w** for *widen*


<a id="org9fae82c"></a>

## save-restriction


<a id="org8c974e2"></a>

### use save-restriction and save-excurison

    (save-excurison
      (save-restriction 
         body))

    (save-restriction 
      (widen)
      (save-excurison
      body))


<a id="orgbbb3489"></a>

## what-lines


<a id="org841b921"></a>

### 

    (defun simple-whatline()
      (interactive)
      (save-restriction
        (widen)
        (save-excursion
          (let ((lines))
    	(setq  lines (count-lines 1 (point)))
    	(message "The line number is %d" lines)))))


<a id="orgddd60a9"></a>

## more about interactive

Sepreate string with **\n**


<a id="orgc6c23e7"></a>

### input many arguments

-   **"s"** string
-   **"n"** number

    (defun hello(name age country)
      (interactive "sinput your name: \nnage: \nscountry: ")
      (message "name:%s age:%d country:%s" name age country))


<a id="org975279c"></a>

### "r" stands for a region

    (defun hello1 (start end)
      (interactive "r")
      (message "start:%d end:%d" start end))


<a id="orgd99f250"></a>

### "p" and "P"

invoke a function by typing **C-u prefix-argument M-x fun-name**

1.  "p" prefix argument convert to a number

2.  "P" prefix argument is a raw type

        (defun hello2 (num)
          (interactive "p")
          (message "%d" num))


<a id="org1600c4f"></a>

## car,cdr and cons

-   cons to construct lists
-   car and cdr to take apart lists


<a id="orgef870da"></a>

### car

the car of the list is the first item

    (car '(tiger lion))


<a id="orgfd62f36"></a>

### cdr

returns the rest of the list

    (cdr '(tiger lion))
    (cdr '(tiger lion cat))


<a id="org2d93339"></a>

### cons

    (cons 'tiger '(lion cat))


<a id="org4356095"></a>

### nthcdr

use cdr repeatedly

    (nthcdr 1 '(tiger lion cat))

    (nthcdr 3 '(tiger lion cat))


<a id="org6ffd679"></a>

### nth

use car repeatedly

    (nth 1 '(lion tiger cat))


<a id="orgff6ddbb"></a>

### setcar

set the **car** a new value

    (setq animals (list 'tiger 'cat 'lion))
    (setcar animals 'pig)
    animals


<a id="orgc1854a4"></a>

### setcdr

set the **cdr** a new value

    (setq animals (list 'tiger 'cat 'lion))
    (setcdr animals (list 'pig 'dog))
    animals


<a id="orgd1cb74f"></a>

# Day4


<a id="org8000156"></a>

## defvar

-   it only sets the value of the variable when it doesn't exits
-   if the value has exited,defvar will not overrider the initial value
-   defvar has document string

    (defvar num 3)
    num


<a id="org03ebde3"></a>

## loops and recursion


<a id="org7d4c263"></a>

### while

    (setq animals '(pig cat tiger dog))
    (defun print-list-element (list)
      (while list
       (print (car list))
       (setq list (cdr list))))
    (print-list-element animals)nil


<a id="org00f424b"></a>

### increment loop

use counter to stop a loop

    (setq count 1)
    (defun counter-stop (num)
      (while (< count num))
       body
       (setq count (+ 1 count))))


<a id="org6c90ad8"></a>

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

