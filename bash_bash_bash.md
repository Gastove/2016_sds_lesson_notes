# What on Earth Even Is This


# You Should Totally Get Familiar With:


## `pwd` |> "print working directory"

`pwd` tells you which directory you're currently inside.

```sh
pwd
```

    /home/rdonaldson


## `cd`  |> "change directory"

`cd` changes your current working directory. Pairs well with `pwd`.

```sh
pwd
```

    /home/rdonaldson

```sh
cd /tmp
pwd
```

    /tmp

`cd` has three different ways to take you back to your home directory!

```sh
# These are all the same!
cd $HOME                        # Using the env var containing your home dir
cd ~                            # Using the tilde abbreviation for your home dir
cd                              # Supplied with no arguments, cd defaults to taking you home
pwd
```

    /home/rdonaldson


## `ls` |> "list"

`ls` is your best buddy for knowing what's inside a directory.

Given no arguments, `ls` will print only the names of non-dotted files and directories, using a sort of wrapped horizontal formatting (which may not display correctly on this page, but I promise it is there):

```sh
ls
```

    Arduino
    bin
    Code
    Data
    Desktop
    diary
    docker
    docker-machine-driver-kvm2
    Documents
    Downloads
    Dropbox
    gocode
    home
    index.html?c=1&url=https:%2F%2Flh4.googleusercontent.com%2FrWraLAqGZgF8wz9rCIl_bitm_szrE7RDEUNGnLsfbZ98JQexdavV6mlPJNUamqI3UKN83FvkbgI3F1akUVApNbbx1BSKfWWOdW7xMfiNqGqqbokcY2o5S4jllPqvQ-VYMiuqVhgk
    Music
    my-bluetoothd.te
    pcsc-spy
    Pictures
    Public
    supplication.txt
    Templates
    Videos

To always format the results of `ls` as a vertical list, pass `-l`:

```sh
ls -l
```

    total 37232
    drwxr-xr-x.  5 rdonaldson rdonaldson     4096 Apr 21 19:00 Arduino
    drwxr-xr-x.  6 rdonaldson rdonaldson     4096 Aug 27 10:59 bin
    drwxrwxr-x. 40 rdonaldson rdonaldson     4096 Sep 13 09:54 Code
    drwxr-xr-x.  2 rdonaldson rdonaldson     4096 Apr  4 07:19 Data
    drwxr-xr-x.  2 rdonaldson rdonaldson     4096 Apr  3 10:32 Desktop
    -rw-r--r--.  1 rdonaldson rdonaldson      254 Sep  5 16:31 diary
    drwx--x--x. 11 root       root           4096 Apr  3 21:27 docker
    -rw-r--r--.  1 rdonaldson rdonaldson 37967168 Apr  6 13:30 docker-machine-driver-kvm2
    drwxr-xr-x.  5 rdonaldson rdonaldson     4096 Sep 24 16:43 Documents
    drwxr-xr-x.  9 rdonaldson rdonaldson     4096 Sep 18 12:39 Downloads
    drwx------. 45 rdonaldson rdonaldson     4096 Aug 14 09:37 Dropbox
    drwxr-xr-x.  5 rdonaldson rdonaldson     4096 Apr  4 11:40 gocode
    drwxr-xr-x.  3 rdonaldson rdonaldson     4096 Sep 21 11:50 home
    -rw-r--r--.  1 rdonaldson rdonaldson    25363 Aug 27 13:37 index.html?c=1&url=https:%2F%2Flh4.googleusercontent.com%2FrWraLAqGZgF8wz9rCIl_bitm_szrE7RDEUNGnLsfbZ98JQexdavV6mlPJNUamqI3UKN83FvkbgI3F1akUVApNbbx1BSKfWWOdW7xMfiNqGqqbokcY2o5S4jllPqvQ-VYMiuqVhgk
    drwxr-xr-x. 82 rdonaldson rdonaldson     4096 Jul 27 14:15 Music
    -rw-r--r--.  1 rdonaldson rdonaldson      181 Apr  6 11:25 my-bluetoothd.te
    prw-r--r--.  1 rdonaldson rdonaldson        0 May 19 09:09 pcsc-spy
    drwxr-xr-x.  3 rdonaldson rdonaldson     4096 Sep 20 19:10 Pictures
    drwxr-xr-x.  2 rdonaldson rdonaldson     4096 Apr  3 10:32 Public
    -rw-r--r--.  1 rdonaldson rdonaldson    48656 May  8 07:13 supplication.txt
    drwxr-xr-x.  2 rdonaldson rdonaldson     4096 Apr  3 10:32 Templates
    drwxr-xr-x.  2 rdonaldson rdonaldson     4096 Apr  3 10:32 Videos

Note that this *also* includes a set of other pieces of information! Who doesn't love that?

If you need to see dotted files too, pass `-a`. Note that for this doc, I'm also using `head` &#x2013; otherwise there's way too much output!

```sh
ls -a | head -n 15
```

    .
    ..
    .android
    .ansible
    .ansible-vault-pw
    Arduino
    .arduino15
    .authinfo.gpg
    .bash_history
    .bash_logout
    .bash_profile
    .bashrc
    bin
    .boot
    .byobu

My personal favorite invocation is `ls -lah`: "list the directory, give me all the information, and render memory in a human-readable format". Again, with `head` to limit output to something manageable:

```sh
ls -lah | head -n 20
```

    total 37M
    drwx--x--x.  70 rdonaldson rdonaldson 4.0K Sep 24 17:33 .
    drwxr-xr-x.   4 root       root       4.0K Feb  7  2018 ..
    drwxr-xr-x.   2 rdonaldson rdonaldson 4.0K Apr 10 11:14 .android
    drwx------.   4 rdonaldson rdonaldson 4.0K Apr  6 15:26 .ansible
    -rw-r--r--.   1 rdonaldson rdonaldson   31 Apr  6 14:29 .ansible-vault-pw
    drwxr-xr-x.   5 rdonaldson rdonaldson 4.0K Apr 21 19:00 Arduino
    drwxr-xr-x.   2 rdonaldson rdonaldson 4.0K Apr 21 19:00 .arduino15
    -rw-r--r--.   1 rdonaldson rdonaldson  157 Jul  2 13:44 .authinfo.gpg
    -rw-------.   1 rdonaldson rdonaldson 2.1K Jul  8 19:41 .bash_history
    -rw-r--r--.   1 rdonaldson rdonaldson   18 Oct 30  2017 .bash_logout
    -rw-r--r--.   1 rdonaldson rdonaldson  254 Apr  3 13:39 .bash_profile
    -rw-r--r--.   1 rdonaldson rdonaldson  322 Apr  3 13:39 .bashrc
    drwxr-xr-x.   6 rdonaldson rdonaldson 4.0K Aug 27 10:59 bin
    drwxr-xr-x.   3 rdonaldson rdonaldson 4.0K Apr 27 10:54 .boot
    drwxr-xr-x.   3 rdonaldson rdonaldson 4.0K Sep 21 14:23 .byobu
    drwxr-xr-x.   7 rdonaldson rdonaldson 4.0K Apr  3 22:00 .cabal
    drwx------.  38 rdonaldson rdonaldson 4.0K Sep 18 11:17 .cache
    drwxr-xr-x.   4 rdonaldson rdonaldson 4.0K May  3 16:13 .cargo
    drwxr-xr-x.   3 rdonaldson rdonaldson 4.0K Apr  9 14:58 .cljs

4.0k is much nicer to interpret than 4096 (the size in bytes).


## `mkdir` |> "make directory"

This one is satisfyingly "does what it says on the tin." You want a new directory? This is the thing.

The most useful flag to know for `mkdir` is `-p`, which allows you to pass multiple directories to `mkdir` at once. (This is because `mkdir` tried to make things from right to left! `mkdir foo/bar/baz` will start by trying to find a `bar` to make `baz` in, and fail if `bar` doesn't exist.)

```sh
mkdir foo/bar/baz/              # This will fail if foo or bar don't exist!
mkdir -p foo/bar/baz/           # This will work every time. Yay!
```


## `touch` |> "create or modify a file"

`touch` is a little like `mkdir` for files. It has two uses:

1.  Make an empty file
2.  Update the "modified" time on a file


## `rm` |> "remove"

`rm` lets you delete a file! Remember: deleting things from the command line *does not* move them to the Trash Can. It is immediately a "real" delete.

The most common flags to use with `rm` are `r` and `f`, usually together. Respectively, they stand for "recursive" and "force." "Recursive" means, "delete this and everything inside of it;" this lets `rm` operate on directories, which is handy! But: `rm` will refuse to delete a directory if it is not empty, unless you specify force.

So, this will error:

```sh
mkdir -p /tmp/blerp
touch /tmp/blerp/what.txt
rm /tmp/blerp
```

But this will not:

```sh
rm -rf /tmp/blerp
```


## `cat` |> "concatenate"

`cat` is actually a pretty sophisticated tool. It can do many, many things. We are going to discuss&#x2026; none of them.

In practice, the thing to get used to doing with `cat` is printing files to standard out:

```sh
cat ~/.bashrc
```

    # .bashrc
    
    # Source global definitions
    if [ -f /etc/bashrc ]; then
    	. /etc/bashrc
    fi
    
    # Uncomment the following line if you don't like systemctl's auto-paging feature:
    # export SYSTEMD_PAGER=
    
    # User specific aliases and functions
    [ -r /home/rdonaldson/.byobu/prompt ] && . /home/rdonaldson/.byobu/prompt   #byobu-prompt#

Woo yeah, it's my `.bashrc`. `cat`'ing a file like this can be especially handy combined with piping; we'll see bits of this below!


## `head` and `tail`

Sometimes you have a file and you want to know what's in it, but you have a *hunch* it might be humongous. For instance: this thing is ~337 megabytes:

```sh
ls -lah ~/Code/language-tour/data-generator/2018-04-29_random_data.csv
```

    -rw-r--r--. 1 rdonaldson rdonaldson 337M Apr 28 23:02 /home/rdonaldson/Code/language-tour/data-generator/2018-04-29_random_data.csv

If I were to `cat` that to my screen, it would scroll forever! I don't want that, but I *do* want to peek inside it. I can do this with `head` and `tail`, which show you the first and last few lines. (By default, "few" means 10 lines, but both are configurable):

```sh
# First 10 lines
head ~/Code/language-tour/data-generator/2018-04-29_random_data.csv
```

    date|phone_number
    Sat, 28 Apr 2018 01:58:56 +0000|438.235.5371
    2017-07-08|545.974.6386
    Thu, 31 Aug 2017 21:58:56 +0000|873.604.4172
    2019-03-10T07:58:56|1-361-552-7473
    2018-12-12T05:58:56|(712) 800-3244
    2017-12-28T02:58:56|1-392-641-2247
    2017-05-28|(452) 461-3433
    2018-05-22T03:58:56|(391) 719-3510
    Fri, 10 Aug 2018 15:58:56 +0000|680.375.2991

With the `-n` flag, less output:

```sh
tail -n 3 ~/Code/language-tour/data-generator/2018-04-29_random_data.csv
```

    Thu, 06 Dec 2018 10:02:16 +0000|889.051.8922
    Thu, 24 Jan 2019 04:02:16 +0000|(536) 841-8005
    Fri, 08 Jun 2018 10:02:16 +0000|324.391.7098


## `less` |> as opposed to "more"

The title may seem glib, but `less` really was made as an alternative to a program called "more". These days, `less` is what we mostly use.

`less` is a "pager," which is in this instance an overloaded term. Rather than "pager" as in "pagerduty" or "the 90s just paged me on my pager," here a "pager" refers to "a thing which produces pages." `less` allows you to send it far more input than will fit on your screen and scroll through it in a reasonable way.

There isn't a good way to demonstrate that in these notes, but here's another way we could have checked the contents of our huge file in the last section:

```sh
cat ~/Code/language-tour/data-generator/2018-04-29_random_data.csv | less
# or:
less ~/Code/language-tour/data-generator/2018-04-29_random_data.csv
```

You can pipe dang near anything to `less`! It's handy as heck.


## `grep` |> "global regular expression print"

`grep` is a phenomenally handy tool, and much less intense to use than the name makes it sound. Note: `grep` is also sufficiently complex that we aren't going to even really scratch the surface of it here.

The essence of `grep` goes like this: given a thing to search for and lines of text to search in, return all the lines that match the specified search.

We'll demonstrate on this tiny file:

```sh
echo "1. cat" > /tmp/grep-demo.txt
echo "2. dog" >> /tmp/grep-demo.txt
echo "3. catdog" >> /tmp/grep-demo.txt
```

We can grep a file directly; here we search for only lines containing "dog":

```sh
grep dog /tmp/grep-demo.txt
```

    2. dog
    3. catdog

By passing the "invert" flag, `-v`, we can get only the lines that *don't* have "dog" in them:

```sh
grep -v dog /tmp/grep-demo.txt
```

    1. cat

With the "insensitive" flag, `-i`, we can do case-insensitive search.

Without:

```sh
grep DOG /tmp/grep-demo.txt
```

With:

```sh
grep -i DOG /tmp/grep-demo.txt
```

    2. dog
    3. catdog

Remember, we can also use `cat` and a pipe to hook operations together!

```sh
cat /tmp/grep-demo.txt | grep '2.'
```

    2. dog

With the `-e` flag, we can activate "extended regexp" support, and do things like, "only match the word 'cat' when it occurs at the end of a line":

```sh
cat /tmp/grep-demo.txt | grep -e 'cat$'
```

    1. cat


## `top` |> "what the heck is my computer **doing?!**"

`top` will list the "top" processes on your computer in a sortable terminal interface. It's a little ugly, but it can be a helpful tool if you'd like a quick look at what your computer is up to.


## `ps` |> "process"

`ps` will list processes your computer knows about. This is the most handy when coupled with `grep`. But&#x2026; first, a note.

`ps`, bless its helpful heart, takes commands in a wide array of different ways, and the commands can be&#x2026; tricky to remember. I look at `man ps` any time I'm deviating from my most usual command, which is: `ps ax`. This gets us a list of *all* the processes the OS knows about, which we can then `grep`. For instance: what if I want to know every python command being run?

```sh
ps ax | grep python
```

     1385 ?        Ssl    0:01 /usr/bin/python3 -Es /usr/sbin/firewalld --nofork --nopid
     2816 tty2     Sl+    0:00 /usr/bin/python3 /usr/bin/seapplet
     4935 tty2     Sl+    0:00 /usr/bin/python3 /usr/bin/chrome-gnome-shell chrome-extension://gphhapmejobijbbhgpjhcjognlahblep/
    13828 ?        S      0:00 grep python

This tells me the process ID (PID), along with some extra info about the python being run &#x2013; and we always find our own grep in our grep of the process tree, which always makes me smile. *Do note* however that this means every `grep` of `ps ax` will always return at minimum one result: itself.

To demonstrate: I promise there is no process on my computer called "fhqwughads". And yet:

```sh
ps ax | grep fhqwughads
```

    13831 ?        S      0:00 grep fhqwughads

Grepping for it returns the grep itself. Neat!


## `kill` |> "kill"

`kill` is one of the least ambiguously named Linux commands I've ever met. It kills a process by process ID (PID). It's safe to use, as long as you're pretty confident in what you're killing.

For instance: maybe I write this python file:

```python
import time

while True:
    time.sleep(1)
```

If I run it, it will never ever exit. Sure, I could cancel it with a keyboard interrupt (control-c, for instance), but I can also find it and kill it with `ps`, `grep`, and `kill`. Like so!

First, we need to find the process:

```sh
ps ax | grep python
```

     680 pts/6    S+     0:00 python /tmp/oh_no.py
    1154 ?        S      0:00 grep python
    1385 ?        Ssl    0:01 /usr/bin/python3 -Es /usr/sbin/firewalld --nofork --nopid
    2816 tty2     Sl+    0:00 /usr/bin/python3 /usr/bin/seapplet
    4935 tty2     Sl+    0:00 /usr/bin/python3 /usr/bin/chrome-gnome-shell chrome-extension://gphhapmejobijbbhgpjhcjognlahblep/

Ah, very good! Our top hit is for `oh_no.py`, which is what I named my bad file. The PID, then, is 680. Perfect. Now, with kill:

```sh
kill 680
```

```sh
ps ax | grep python
```

    1385 ?        Ssl    0:01 /usr/bin/python3 -Es /usr/sbin/firewalld --nofork --nopid
    2707 ?        S      0:00 grep python
    2816 tty2     Sl+    0:00 /usr/bin/python3 /usr/bin/seapplet
    4935 tty2     Sl+    0:00 /usr/bin/python3 /usr/bin/chrome-gnome-shell chrome-extension://gphhapmejobijbbhgpjhcjognlahblep/

Et voila. It is gone.


# If you work on, or interact with, remote servers:


## `ssh`


## `ping`


## `rsync`


# Good to know is there:


## `uniq`


## `sort`


## `wc`


## `sed`


## `cut`


## `find`


## `xargs`


# For the brave: `awk`


## `strace`


## `netstat`


# Useful bits, bobs, and snippets