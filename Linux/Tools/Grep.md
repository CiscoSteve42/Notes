Grep Notes
==========
* My notes for grep were getting pretty lengthy, so I moved them from Misc to their own page. For more info on grep, visit `man grep`


# grep -A and -B 

* You can use `grep -B x foo` with x being the number of lines **BEFORE** the output that you want printed with the grep'd line, as seen below:

```bash
cat foo.txt | grep -B 5 cow

cat
and
the
fiddle,
the
cow
```

* You can use `grep -A x foo` to the same effect but **AFTER** the grep'd line:

```bash
cat foo.txt | grep -A 5 cow

cow
jumped
over
the
moon
```

# Grepping for Multiple Outputs

* If you wanted to grep multiple outputs at once, you COULD use a pipe `grep "sudo\|nvim" .zsh_history` OR 

* You can achieve the same results with the **-e** flag as so `grep -e "sudo" -e "nvim" .zsh_history` 


# Remove Case Sensitivity

* To remove Case Sensitivity from your search, use the **i** flag: 

```bash
$ ls /bin | grep -i WiReShArK
wireshark
```

# Anti-Grep

* Grep with the **-v** flag is anti-Grep, it excludes all lines containing the parameters:

`grep -v "Season 8" Game\ of\ Thrones`


# Grep for Specific Output

* To print JUST THAT THING, and not the whole line, use the **-o** flag `grep -o "Frodo" LOTR.txt | wc -l`


