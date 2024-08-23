GNU Core Utils List 
===================

* I'm working my way through every tool on this list, adding on to the bare-bones definitions provided to me by ChatGPT, some may become their own pages depending on the extent of the tool. 

* More info can be found locally using the `info coreutils` command on your Linux system or consulting each page with `man` as I intend to do on this page.  


The List
--------

1. **`basename`**: Strips directory and suffix from filenames, for example `basename ~/Music/Album/song.mp3` would print `song.mp3`


3. **`cat`**: Concatenates and displays file content, for example `cat .bash_history | grep cat | wc -l` would list how many times your user has used cat in the Bash shell.


4. **`chgrp`**: Changes the group ownership of files, for example `chgrp wheel foo.txt`


5. **`chmod`**: Changes file permissions, see my [Notes on Permissions]() for more info.


6. **`chown`**: Changes file owner and group.

7. **`chroot`**: Changes the root directory for the current running process.



8. **`cp`**: Copies files and directories, my most used flag is definitely the recursive `-r` flag for moving folders



9. **`csplit`**: Splits a file into sections determined by context lines.

10. **`cut`**: Removes sections from each line of files.

11. **`date`**: Displays or sets the system date and time, has a lot of options set in the following format `date +"%H:%M"`, which would display the hour and minute in military time, as so `16:20`

12. **`df`**: Reports file system disk space usage, has a `--human-readable` flag.

13. **`dir`**: Lists directory contents (alternative to `ls`).

14. **`dircolors`**: Configures color support for `ls`.

15. **`dirname`**: Strips the last component from the file name.

16. **`du`**: Estimates file space usage.

17. **`echo`**: Displays a line of text.

18. **`env`**: Runs a command in a modified environment.

19. **`expand`**: Converts tabs to spaces.



20. **`expr`**: Evaluates expressions, may need a backslash so that characters are not interpretted by the shell, for example `expr 4 \* 20`



21. **`factor`**: Factors integers, for example `factor 420` would give you `420: 2 2 3 5 7`, which you can check with expr `expr 2 \* 2 \* 3 \* 5 \* 7` 



22. **`false`**: Does nothing (unsuccessfully), returns an exit status of 1.



23. **`fmt`**: Simple text formatter.

24. **`fold`**: Wraps each input line to fit in specified width.

25. **`groups`**: Displays the groups to which a user belongs.

26. **`head`**: Outputs the first part of files.

27. **`hostid`**: Prints the numeric identifier for the current host.

28. **`id`**: Prints user and group information.

29. **`install`**: Copies files and sets attributes.

30. **`join`**: Joins lines of two files on a common field.

31. **`kill`**: Sends signals to processes.

32. **`link`**: Creates a hard link to a file.

33. **`ln`**: Creates symbolic or hard links.

34. **`logname`**: Prints the current login name.

35. **`ls`**: Lists directory contents.

36. **`md5sum`**: Computes MD5 checksums.

37. **`mkdir`**: Creates directories.

38. **`mkfifo`**: Creates named pipes (FIFOs).

39. **`mknod`**: Creates special files.

40. **`mv`**: Moves or renames files and directories.

41. **`nice`**: Runs a command with modified scheduling priority.



42. **`nl`**: cat but also prints out the number of lines





43. **`nohup`**: Runs a command immune to hangups.

44. **`od`**: Dumps files in octal and other formats.

45. **`paste`**: Merges lines of files.

46. **`pathchk`**: Checks file name validity.

47. **`pinky`**: An enhanced version of `who` and `finger`.

48. **`printenv`**: Prints environment variables.

49. **`printf`**: Formats and prints data.

50. **`ptx`**: Produces permuted index of file contents.

51. **`pwd`**: Prints the current working directory.

52. **`readlink`**: Prints the value of a symbolic link or canonical file name.

53. **`rm`**: Removes files or directories.

54. **`rmdir`**: Removes empty directories.

55. **`seq`**: Prints a sequence of numbers.

56. **`shuf`**: Shuffles lines of files.

57. **`sleep`**: Delays for a specified amount of time.

58. **`sort`**: Sorts lines of text files.

59. **`split`**: Splits a file into pieces.

60. **`stat`**: Displays file or file system status.

61. **`stdbuf`**: Adjusts buffering of command’s input/output.

62. **`strings`**: Prints the strings of printable characters in files.

63. **`sum`**: Computes a checksum for files.

64. **`sync`**: Synchronizes cached writes to persistent storage.

65. **`tac`**: Concatenates and displays files in reverse.

66. **`tail`**: Outputs the last part of files.

67. **`tee`**: Reads from standard input and writes to standard output and files.

68. **`test`**: Evaluates conditional expressions.

69. **`timeout`**: Runs a command with a time limit.

70. **`touch`**: Changes file timestamps or creates empty files.

71. **`tr`**: Translates or deletes characters.

72. **`true`**: Does nothing, returns an exit status of 0.

73. **`tsort`**: Topologically sorts lines of files.

74. **`tty`**: Prints the file name of the terminal connected to standard input.

75. **`uname`**: Prints system information.

76. **`unexpand`**: Converts spaces back to tabs.

77. **`uniq`**: Removes duplicate lines from sorted files.

78. **`unlink`**: Removes a single file.

79. **`uptime`**: Shows how long the system has been running.

80. **`useradd`**: Adds a user to the system.

81. **`usermod`**: Modifies a user account.

82. **`userdel`**: Deletes a user account.

83. **`vdir`**: Lists directory contents (alternative to `ls`).

84. **`wc`**: Counts words, lines, and characters in files.

85. **`who`**: Shows who is logged in.

86. **`whoami`**: Prints the effective username of the current user.

87. **`yes`**: Repeatedly outputs a string until killed.

88. **`zcat`**: Displays compressed files (similar to `cat` for `.gz` files).

89. **`zcmp`**: Compares compressed files.

90. **`zdiff`**: Displays differences between compressed files.

91. **`zless`**: Views compressed files (similar to `less` for `.gz` files).

92. **`zmore`**: Views compressed files (similar to `more` for `.gz` files).

93. **`znew`**: Recompresses `.Z` files to `.gz` format.

94. **`zgrep`**: Greps through compressed files.

95. **`zless`**: Views compressed files (similar to `less` for `.gz` files).

96. **`zmore`**: Views compressed files (similar to `more` for `.gz` files).

97. **`zcat`**: Displays compressed files (similar to `cat` for `.gz` files).


Additional Info from GNU Website
================================

* Additional info for the GNU coreutils from [The GNU Website](https://www.gnu.org/software/coreutils/manual/coreutils.html)


* `cp`, `mv`, `install`, and `ln` all have a `b` (`--backup`) flag that ...backs up the file...yeah. 
