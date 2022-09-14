# Useful Terminal Commands

## Key Commands & Navigation

-   `Up Arrow`: Will show your last command
-   `Down Arrow`: Will show your next command
-   `Tab`: Will auto-complete your command
-   `Ctrl + L`: Will clear the screen
-   `Ctrl + C`: Will cancel a command
-   `Ctrl + R`: Will search for a command
-   `Ctrl + D`: Will exit the terminal

## `date`

```bash
  date
```

## Opening a Folder or File

Mac - `open [dirname]`
Windows - `start [dirname]`
Linux - `xdg-open [dirname]`

You can open folders, files and even URLs

```bash
  open https://traversymedia.com
```

## Right angle bracket >

This symbol tells the system to output results into whatever you specify next. The target is usually a filename. You can use this symbol by itself to create a new file:

```bash
> [filename]
```

When you are done, hit `ctrl+D`

## The `grep` Command

The `grep` command is used to search for a text pattern in a file. It is very powerful and can be used to search for a string or regular expression in a file or set of files.

```bash
  grep [searchterm] [filename]
```

You can also search for a string in multiple files:

```bash
  grep [searchterm] [filename] [filename]
```

## The `find` command

The `find` command is extremely powerful and is used to find the location of files and directories based on conditions that you specify.

To start off by creating something to work with. Let's create 100 files in the current directory. This is one of those things that I talked about earlier where you can do certain things much faster than you could in the GUI. We already know that the `touch` command will create a file. It can also be used to create multiple files.

```bash
  touch file-{001..100}.txt
```

Now we have 100 .txt files in the current directory. Something that would have taken a lot longer to do in the GUI.

Let's do something very simple and find a specific file. The format looks like this:

```bash
  find [dirname] -name [filename]
```

Let's find the file called `file-001.txt`:

```bash
  find . -name "file-001.txt"
```

This will look in the current directory, which is represented with a dot.

We can look in other directories as well. Let's create a file in our home folder called test.txt

```
  touch ~/test.txt
```

To find that file:

```bash
  find ~/ -name "test.txt"
```

We can look for files that match a certain pattern as well. Let's find all files that start with `file-`:

```bash
  find . -name "file-*"
```

We can search for files that are empty:

```bash
  find . -empty
```

Let's append some text to the file `file-002.txt`. We could use the `cat` command, like I showed you earlier, but we can also use the `echo` command:

```bash
  echo "Hello World" >> file-002.txt
```

Now if we find the empty files again, we will see that `file-002.txt` is no longer empty:

```bash
  find . -empty
```

We can remove all of the files that we created with this command:

```bash
  find . -name "file-*" -delete
  rm -f file-* # This will also work
```

There is so much more that you can do with the `find` command, but it goes beyond the scope of this tutorial.

## Piping

Piping is very powerful. It is a way of redirecting standard output to another destination, such as another file. Let's actually use the find command to find a list of files and then pipe them to a new file.

First, we'll create 10 files:

```bash
touch file-{001..010}.txt
```

Now, let's pipe the result from our find into a new file named `output.txt`

```bash
find . -name "file-0*" > output.txt
```

You can see the results now in the new file:

```bash
cat output.txt
```

## Creating a Symlink

A symlink is a special type of file that points to another file. It is a shortcut to the original file. It is useful when you want to access a file in a different location without having to copy it.

We can use the `ln` command to create a symlink:

```bash
  ln -s [filename] [symlinkname]
```

You can remove a symlink with the `rm` command:

```bash
  rm [symlinkname]
```

If you're on Windows and you are not using something like Git Bash, you can use the `mklink` command:

```bash
  mklink [symlinkname] [filename]
```

## File Compression

`tar` is a program for concatenating multiple files into one big file called a **tarball** and reversing this process by extracting the files from the tarball.

| Command                             | Description                |
| ----------------------------------- | -------------------------- |
| tar czvf [dirname].tar.gz [dirname] | Create tarball             |
| tar tzvf [dirname]                  | See what is in the tarball |
| tar xzvf [dirname].tar.gz           | Extract tarball            |

-   -c : Creates Archive
-   -x : Extract the archive
-   -f : creates archive with given filename
-   -t : displays or lists files in archived file
-   -u : archives and adds to an existing archive file
-   -v : Displays Verbose Information
-   -A : Concatenates the archive files
-   -z : zip, tells tar command that creates tar file using gzip
-   -j : filter archive tar file using tbzip
-   -W : Verify a archive file
-   -r : update or add file or directory in already existed .tar file

## The `history` Command

Used to display the history of commands that you have run.

```bash
  history
```

You can also use the `!` to run a command from the history.

```bash
  !100
```

This will run the command that is in the 100th position in the history.
