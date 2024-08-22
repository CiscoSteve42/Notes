Notes on the `date` Command
===========================

* `date` is a simple command with a lot of formatting options, I felt like it would be more efficent to list them out in a separate file.

* This is more intended to cover the various available formats and not the flags available for the command. For more information on the available flags for date, consult your local manpage.

* Helping Linux users get a `date` since 2024


Okay, to the Content...
-----------------------

* You can use `date +` if you just want to print something to the terminal like `echo` or `printf`, for example:

```bash 
$ date +69
69
```

* Now, thats neat and all but its better used in conjunction with `%` to do stuff like this:

```bash 
date +%I:%M
04:20
```

* In this example, I use `%I` to list the hour (`%H` lists the hour in military time), and `%M` to list the minute, separated by the `:` to make it a familiar format.

* Note that you can make the separator whatever you want, for example if I wanted to list just the date, but in a specific format, I could use something like the following example:

```bash 
$ date +"Hello Steven. Today is
 %A, the %dnd of %B in this foul year of our Lord, %Y"
Hello Steven. Today is Thursday, the 22nd of August in this foul year of our Lord, 2024
```

* As you can see, I used `%A` to print the full name of the day of the week (you can use `%a` to print the abbreviated weekday name.) Then I used `%d` listed the numeric day of the month. `%B` lists the full name of the month (`%b` prints the abbreviated version, in the same fashion as the day of the week.) Then I finish using `%Y` to print the year. I could use `%C` to print just the last 2 digits of the year (`20`) or `%y` to print the last 2 digits (`24`) so with that logic, `date +%C%y` would give you the same output as `date +%Y`, which is the case for a lot of these commands. 

