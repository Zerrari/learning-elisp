
# Table of Contents

1.  [Day1](#org86c1249)
    1.  [symbol](#org9549812)
        1.  [it can be defined as a function and a variable which returns a value](#orgb01fee7)
        2.  [when symbol is in a pair of parenthese and is the first position.It stands for a function.](#org1d99cb8)
        3.  [when symbol is not in a pair of parenthese it stands for a variable.](#orgdcedc08)
        4.  [a quotation before a pair of parenthese return what is written](#org31abc00)
        5.  [atoms which in a pair of parenthese are separated by a white space](#orgb1c6389)
    2.  [evaluate](#org9fff4b9)
        1.  [how](#org39d51be)
    3.  [function](#org4aa6aa4)
        1.  [something basic](#orgea54e3c)
        2.  [set and setq](#org2b99c1a)
        3.  [buffer](#org85eb9f8)
2.  [Day2](#org7fdb3e2)
    1.  [function](#org8c154ef)
        1.  [defun](#org09149ff)
        2.  [let](#orga6be4cf)
        3.  [if](#org7616fde)
        4.  [save excurison](#orgd1712c6)
        5.  [beginning of buffer](#org908281a)
        6.  [mark-whole-buffer](#orgda39c39)
        7.  [append-to-buffer](#org2689ae8)
3.  [Day3](#orgeaebffe)
    1.  [narrowing and widening](#org9224b16)
        1.  [key binding](#org1c1e964)
    2.  [save-restriction](#org0c34062)
        1.  [use save-restriction and save-excurison](#orgf56f237)
    3.  [what-lines](#org17f6899)
        1.  [](#org4a85a9f)
    4.  [more about interactive](#orga1191fc)
        1.  [input many arguments](#org3c022c6)
        2.  ["r" stands for a region](#org1ee611e)
        3.  ["p" and "P"](#orgb361918)
    5.  [car,cdr and cons](#org4960899)
        1.  [car](#org8fecbc2)
        2.  [cdr](#orgaf37eab)
        3.  [cons](#orgd180cb0)
        4.  [nthcdr](#org58672ef)
        5.  [nth](#org2d580ce)
        6.  [setcar](#orgf07e4f0)
        7.  [setcdr](#org76dcd79)


<a id="org86c1249"></a>

# Day1


<a id="org9549812"></a>

## symbol


<a id="orgb01fee7"></a>

### it can be defined as a function and a variable which returns a value


<a id="org1d99cb8"></a>

### when symbol is in a pair of parenthese and is the first position.It stands for a function.

1.  

        (+ 1 2)


<a id="orgdcedc08"></a>

### when symbol is not in a pair of parenthese it stands for a variable.

1.  

        fill-column    


<a id="org31abc00"></a>

### a quotation before a pair of parenthese return what is written

    '(lion tigger)

    '(lion "a tree")


<a id="orgb1c6389"></a>

### atoms which in a pair of parenthese are separated by a white space


<a id="org9fff4b9"></a>

## evaluate


<a id="org39d51be"></a>

### how

move the cursor after the parenthese,and type **C-x C-e** to evaluate the expression


<a id="org4aa6aa4"></a>

## function


<a id="orgea54e3c"></a>

### something basic

1.  a funtion returns two things

    -   return a value
    -   side effects(*print something on the screen*)


<a id="org2b99c1a"></a>

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


<a id="org85eb9f8"></a>

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


<a id="org7fdb3e2"></a>

# Day2


<a id="org8c154ef"></a>

## function


<a id="org09149ff"></a>

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


<a id="orga6be4cf"></a>

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


<a id="org7616fde"></a>

### if

1.  example

        (if (> 5 4)
             (message "yes")
             (message "no"))

2.  truth and falsehood

    -   anything except nil represents true
    -   the **empty** list is falsehood


<a id="orgd1712c6"></a>

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


<a id="org908281a"></a>

### beginning of buffer

1.  push-mark

    the function stores the current positon of the cursor in mark ring
    
        (defun simple-bob
         (interactive)
         (push-mark)
         (goto-char (point-min)))


<a id="orgda39c39"></a>

### mark-whole-buffer

(defun z-mark-whole-buffer()
  (interactive)
  (progn
    (goto-char (point-max))
    (set-mark (point))
    (goto-char (point-min))))
(z-mark-whole-buffer)


<a id="org2689ae8"></a>

### append-to-buffer

insert-buffer-substring


<a id="orgeaebffe"></a>

# Day3


<a id="org9224b16"></a>

## narrowing and widening

with narrowing, the rest of buffer is invisible


<a id="org1c1e964"></a>

### key binding

**C-x n n** for *narrow-to-rigion*
**C-x n w** for *widen*


<a id="org0c34062"></a>

## save-restriction


<a id="orgf56f237"></a>

### use save-restriction and save-excurison

    (save-excurison
      (save-restriction 
         body))

    (save-restriction 
      (widen)
      (save-excurison
      body))


<a id="org17f6899"></a>

## what-lines


<a id="org4a85a9f"></a>

### 

    (defun simple-whatline()
      (interactive)
      (save-restriction
        (widen)
        (save-excursion
          (let ((lines))
    	(setq  lines (count-lines 1 (point)))
    	(message "The line number is %d" lines)))))


<a id="orga1191fc"></a>

## more about interactive

Sepreate string with **\n**


<a id="org3c022c6"></a>

### input many arguments

-   **"s"** string
-   **"n"** number

    (defun hello(name age country)
      (interactive "sinput your name: \nnage: \nscountry: ")
      (message "name:%s age:%d country:%s" name age country))


<a id="org1ee611e"></a>

### "r" stands for a region

    (defun hello1 (start end)
      (interactive "r")
      (message "start:%d end:%d" start end))


<a id="orgb361918"></a>

### "p" and "P"

invoke a function by typing **C-u prefix-argument M-x fun-name**

1.  "p" prefix argument convert to a number

2.  "P" prefix argument is a raw type

        (defun hello2 (num)
          (interactive "p")
          (message "%d" num))


<a id="org4960899"></a>

## car,cdr and cons

-   cons to construct lists
-   car and cdr to take apart lists


<a id="org8fecbc2"></a>

### car

the car of the list is the first item

    (car '(tiger lion))


<a id="orgaf37eab"></a>

### cdr

returns the rest of the list

    (cdr '(tiger lion))
    (cdr '(tiger lion cat))


<a id="orgd180cb0"></a>

### cons

    (cons 'tiger '(lion cat))


<a id="org58672ef"></a>

### nthcdr

use cdr repeatedly

    (nthcdr 1 '(tiger lion cat))

    (nthcdr 3 '(tiger lion cat))


<a id="org2d580ce"></a>

### nth

use car repeatedly

    (nth 1 '(lion tiger cat))


<a id="orgf07e4f0"></a>

### setcar

set the **car** a new value

    (setq animals (list 'tiger 'cat 'lion))
    (setcar animals 'pig)
    animals


<a id="org76dcd79"></a>

### setcdr

set the **cdr** a new value

    (setq animals (list 'tiger 'cat 'lion))
    (setcdr animals (list 'pig 'dog))
    animals

