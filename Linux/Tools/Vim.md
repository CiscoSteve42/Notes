Vim Cheatsheet
==============
Various things that I pick up to make my Vim/NeoVim experiece more productive (don't judge me, I'm slow.)    

f, F, t, and T
--------------
* fQ would go to Q in the following line:

`print('Then Picard exclaimed "Q!!!!!!!!"')`

* tQ would take you to the quotation mark right before it. 

* FQ and TQ do the same thing but backwards.

Capital Letters
---------------
 So I don't freak out due to skill issues everytime I hit caps lock.

* C  #replace whole line

* O  #newline above current line

* I  #insert at beginning of line

* A  #exactly what you think it does based on above context

* U  #repeat last changes on current line



Swap Files
----------
# You should still save your files like a kid playing Pokemon 

* View the swp file for a file with `:swapname`

* or check the path below:

* `ls ~/.local/state/nvim/swap` if using **NeoVim** OR

* `ls ~/.cache/vim/swap` if using vanilla **Vim**

* Open the file that you one that you want with `vim -r /path/to/swpfile.swp`

* write the file under a new filename `:w recovered.txt`


