
# Table of Contents

1.  [Day1](#org879526c)
    1.  [symbol](#org879e003)
        1.  [it can be defined as a function and a variable which returns a value](#orgc1d7420)
        2.  [when symbol is in a pair of parenthese and is the first position.It stands for a function.](#org609d4e0)
        3.  [when symbol is not in a pair of parenthese it stands for a variable.](#org2f6e9bc)
        4.  [a quotation before a pair of parenthese return what is written](#org2cc2bae)
        5.  [atoms which in a pair of parenthese are separated by a white space](#org439d923)
    2.  [evaluate](#org19af97b)
        1.  [how](#orgdfc6a6e)
    3.  [function](#org3517fb1)
        1.  [something basic](#org2a44614)
        2.  [set and setq](#org6b2d120)
        3.  [buffer](#orgcd42899)
2.  [Day2](#org9a2711f)
    1.  [function](#orgecf0af8)
        1.  [defun](#org751aa1a)
        2.  [let](#orgfac280d)
        3.  [if](#orgb37f282)
        4.  [save excurison](#orgd4768a6)
        5.  [beginning of buffer](#orge70b600)
        6.  [mark-whole-buffer](#org3aa7c3a)
        7.  [append-to-buffer](#orgac0a5b2)


<a id="org879526c"></a>

# Day1


<a id="org879e003"></a>

## symbol


<a id="orgc1d7420"></a>

### it can be defined as a function and a variable which returns a value


<a id="org609d4e0"></a>

### when symbol is in a pair of parenthese and is the first position.It stands for a function.

1.  

        (+ 1 2)


<a id="org2f6e9bc"></a>

### when symbol is not in a pair of parenthese it stands for a variable.

1.  

        fill-column    


<a id="org2cc2bae"></a>

### a quotation before a pair of parenthese return what is written

    '(lion tigger)

    '(lion "a tree")


<a id="org439d923"></a>

### atoms which in a pair of parenthese are separated by a white space


<a id="org19af97b"></a>

## evaluate


<a id="orgdfc6a6e"></a>

### how

move the cursor after the parenthese,and type **C-x C-e** to evaluate the expression


<a id="org3517fb1"></a>

## function


<a id="org2a44614"></a>

### something basic

1.  a funtion returns two things

    -   return a value
    -   side effects(*print something on the screen*)


<a id="org6b2d120"></a>

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


<a id="orgcd42899"></a>

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


<a id="org9a2711f"></a>

# Day2


<a id="orgecf0af8"></a>

## function


<a id="org751aa1a"></a>

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


<a id="orgfac280d"></a>

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


<a id="orgb37f282"></a>

### if

1.  example

        (if (> 5 4)
             (message "yes")
             (message "no"))

2.  truth and falsehood

    -   anything except nil represents true
    -   the **empty** list is falsehood


<a id="orgd4768a6"></a>

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


<a id="orge70b600"></a>

### beginning of buffer

1.  push-mark

    the function stores the current positon of the cursor in mark ring
    
        (defun simple-bob
         (interactive)
         (push-mark)
         (goto-char (point-min)))


<a id="org3aa7c3a"></a>

### mark-whole-buffer

(defun z-mark-whole-buffer()
  (interactive)
  (progn
    (goto-char (point-max))
    (set-mark (point))
    (goto-char (point-min))))
(z-mark-whole-buffer)


<a id="orgac0a5b2"></a>

### append-to-buffer

insert-buffer-substring

