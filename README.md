
# Table of Contents

1.  [Day1](#orgcdbfe11)
    1.  [symbol](#org3bfd349)
        1.  [it can be defined as a function and a variable which returns a value](#orgc7baa39)
        2.  [when symbol is in a pair of parenthese and is the first position.It stands for a function.](#org8338c22)
        3.  [when symbol is not in a pair of parenthese it stands for a variable.](#org019cade)
        4.  [a quotation before a pair of parenthese return what is written](#org8806b7e)
        5.  [atoms which in a pair of parenthese are separated by a white space](#org31b6db6)
    2.  [evaluate](#org1b2bb48)
        1.  [how](#org131aae4)
    3.  [function](#org27b916a)
        1.  [something basic](#orgf5a1fc5)
        2.  [set and setq](#orgc30f219)
        3.  [buffer](#org9c9efed)
2.  [Day2](#orgd68891f)
    1.  [function](#org4e120bb)
        1.  [defun](#org650737d)
        2.  [let](#orgae6cb51)
        3.  [if](#orgd1b1433)
        4.  [save excurison](#org4577740)
        5.  [beginning of buffer](#org03f264a)
        6.  [mark-whole-buffer](#org7be95a4)
        7.  [append-to-buffer](#org7db3b27)
3.  [Day3](#org1b0f53b)
    1.  [narrowing and widening](#org7f3f210)
        1.  [key binding](#orge24c15d)
    2.  [save-restriction](#org50d6669)
        1.  [use save-restriction and save-excurison](#org0cde45b)
    3.  [what-lines](#org3379159)
        1.  [](#org57e94a5)
    4.  [more about interactive](#orgb5a182c)
        1.  [input many arguments](#orgf940dc4)
        2.  ["r" stands for a region](#org1c34bc2)
        3.  ["p" and "P"](#orgec7556c)
    5.  [car,cdr and cons](#org0fd41d4)
        1.  [car](#orgfc6ed06)
        2.  [cdr](#orgd1bce16)
        3.  [cons](#org7f0a237)
        4.  [nthcdr](#orgb2220b8)
        5.  [nth](#org754db2a)
        6.  [setcar](#orgf01cb20)
        7.  [setcdr](#orgb85adaf)
4.  [Day4](#orgc93b60c)
    1.  [defvar](#org763ee2b)
    2.  [loops and recursion](#orgd37df8b)
        1.  [while](#org8210c62)
        2.  [increment loop](#org5e72c74)
        3.  [dolist and dotimes](#org7320a86)


<a id="orgcdbfe11"></a>

# Day1


<a id="org3bfd349"></a>

## symbol


<a id="orgc7baa39"></a>

### it can be defined as a function and a variable which returns a value


<a id="org8338c22"></a>

### when symbol is in a pair of parenthese and is the first position.It stands for a function.

1.  

        (+ 1 2)


<a id="org019cade"></a>

### when symbol is not in a pair of parenthese it stands for a variable.

1.  

        fill-column    


<a id="org8806b7e"></a>

### a quotation before a pair of parenthese return what is written

    '(lion tigger)

    '(lion "a tree")


<a id="org31b6db6"></a>

### atoms which in a pair of parenthese are separated by a white space


<a id="org1b2bb48"></a>

## evaluate


<a id="org131aae4"></a>

### how

move the cursor after the parenthese,and type **C-x C-e** to evaluate the expression


<a id="org27b916a"></a>

## function


<a id="orgf5a1fc5"></a>

### something basic

1.  a funtion returns two things

    -   return a value
    -   side effects(*print something on the screen*)


<a id="orgc30f219"></a>

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


<a id="org9c9efed"></a>

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


<a id="orgd68891f"></a>

# Day2


<a id="org4e120bb"></a>

## function


<a id="org650737d"></a>

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


<a id="orgae6cb51"></a>

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


<a id="orgd1b1433"></a>

### if

1.  example

        (if (> 5 4)
             (message "yes")
             (message "no"))

2.  truth and falsehood

    -   anything except nil represents true
    -   the **empty** list is falsehood


<a id="org4577740"></a>

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


<a id="org03f264a"></a>

### beginning of buffer

1.  push-mark

    the function stores the current positon of the cursor in mark ring
    
        (defun simple-bob
         (interactive)
         (push-mark)
         (goto-char (point-min)))


<a id="org7be95a4"></a>

### mark-whole-buffer

    (defun z-mark-whole-buffer()
      (interactive)
      (progn
        (goto-char (point-max))
        (set-mark (point))
        (goto-char (point-min))))
    (z-mark-whole-buffer)


<a id="org7db3b27"></a>

### append-to-buffer

insert-buffer-substring


<a id="org1b0f53b"></a>

# Day3


<a id="org7f3f210"></a>

## narrowing and widening

with narrowing, the rest of buffer is invisible


<a id="orge24c15d"></a>

### key binding

**C-x n n** for *narrow-to-rigion*
**C-x n w** for *widen*


<a id="org50d6669"></a>

## save-restriction


<a id="org0cde45b"></a>

### use save-restriction and save-excurison

    (save-excurison
      (save-restriction 
         body))

    (save-restriction 
      (widen)
      (save-excurison
      body))


<a id="org3379159"></a>

## what-lines


<a id="org57e94a5"></a>

### 

    (defun simple-whatline()
      (interactive)
      (save-restriction
        (widen)
        (save-excursion
          (let ((lines))
    	(setq  lines (count-lines 1 (point)))
    	(message "The line number is %d" lines)))))


<a id="orgb5a182c"></a>

## more about interactive

Sepreate string with **\n**


<a id="orgf940dc4"></a>

### input many arguments

-   **"s"** string
-   **"n"** number

    (defun hello(name age country)
      (interactive "sinput your name: \nnage: \nscountry: ")
      (message "name:%s age:%d country:%s" name age country))


<a id="org1c34bc2"></a>

### "r" stands for a region

    (defun hello1 (start end)
      (interactive "r")
      (message "start:%d end:%d" start end))


<a id="orgec7556c"></a>

### "p" and "P"

invoke a function by typing **C-u prefix-argument M-x fun-name**

1.  "p" prefix argument convert to a number

2.  "P" prefix argument is a raw type

        (defun hello2 (num)
          (interactive "p")
          (message "%d" num))


<a id="org0fd41d4"></a>

## car,cdr and cons

-   cons to construct lists
-   car and cdr to take apart lists


<a id="orgfc6ed06"></a>

### car

the car of the list is the first item

    (car '(tiger lion))


<a id="orgd1bce16"></a>

### cdr

returns the rest of the list

    (cdr '(tiger lion))
    (cdr '(tiger lion cat))


<a id="org7f0a237"></a>

### cons

    (cons 'tiger '(lion cat))


<a id="orgb2220b8"></a>

### nthcdr

use cdr repeatedly

    (nthcdr 1 '(tiger lion cat))

    (nthcdr 3 '(tiger lion cat))


<a id="org754db2a"></a>

### nth

use car repeatedly

    (nth 1 '(lion tiger cat))


<a id="orgf01cb20"></a>

### setcar

set the **car** a new value

    (setq animals (list 'tiger 'cat 'lion))
    (setcar animals 'pig)
    animals


<a id="orgb85adaf"></a>

### setcdr

set the **cdr** a new value

    (setq animals (list 'tiger 'cat 'lion))
    (setcdr animals (list 'pig 'dog))
    animals


<a id="orgc93b60c"></a>

# Day4


<a id="org763ee2b"></a>

## defvar

-   it only sets the value of the variable when it doesn't exits
-   if the value has exited,defvar will not overrider the initial value
-   defvar has document string

    (defvar num 3)
    num


<a id="orgd37df8b"></a>

## loops and recursion


<a id="org8210c62"></a>

### while

    (setq animals '(pig cat tiger dog))
    (defun print-list-element (list)
      (while list
       (print (car list))
       (setq list (cdr list))))
    (print-list-element animals)nil


<a id="org5e72c74"></a>

### increment loop

use counter to stop a loop

    (setq count 1)
    (defun counter-stop (num)
      (while (< count num))
       body
       (setq count (+ 1 count))))


<a id="org7320a86"></a>

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

