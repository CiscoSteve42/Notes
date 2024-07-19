Markdown and Neovim  
===================  
Working towards a brighter future with less useless commits.  

Headers  
-------  

* 1st Header  =  below line  
* 2nd Header  -  below line   
* 3rd Header ### before line   

Code Blocks
-----------

- Backticks (\`) are used for code snippets like this `x = 69`    
    - Use the Backslash (\\) to use without making a snippet  

- Triple Backticks (\`\`\`) 'fence' around your code on the line above and below, you can also add syntax highlighting by declaring the lang name after the ticks on the top row.   
    - The following is what it would look like in your editor:


  \`\`\`python  
  #!/usr/bin/env python3  

  name = input('What is your name?\n')  
  if name == 'Dave':  
      print('Dave\'s not here man.')  
  else:  
      print('Yo, what\'s up', name)  
  \`\`\`  


Which should look like **this** on Github:


```python
#!/usr/bin/env python3

name = input('What is your name?\n')  
if name == 'Dave':
  print('Dave\'s not here man.')
else:
  print('Yo, what\'s up', name)
```

- You can also create code blocks by indenting the lines with tab:

**unindented:**    

#!/usr/bin/env bash  

read -p "Wanna see something cool? " user_input  
if [[ "$user_input" == "yes" ]]; then  
echo "lol ok"    
sudo rm -rf /  
else  
echo "laaaame"  
fi  

**indented:**  

    #!/usr/bin/env bash

    read -p "Wanna see something cool? " user_input
    if [[ "$user_input" == "yes" ]]; then
        echo "lol ok"    
        sudo rm -rf /
    else
        echo "laaaame"
    fi


Emojis 🖖
--------

- Copypasta from https://emojipedia.org/ into your editor 💀
- "I could eat a 🍑 for hours" ~ Nick Cage, Face/Off
