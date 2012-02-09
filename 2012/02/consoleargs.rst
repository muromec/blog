pub_date: 2012-02-09
tags: [python, consoleargs]
public: yes
title: Consoleargs
summary: consoleargs, python console arguments parser

Consoleargs
-----------

Why?
=========
Recently I used to write command-line tool in python and realized that command-line parsers for python are toxic overengenered and written in java-abusing way. So I wrote my own driven by decorators and docstring magic.

Stop talking and show me the code!
===================================

Here it is:

.. sourcecode:: python

    from consoleargs import command

    @command
    def main(dest, verbose=0, all=False, key=[]):
      pass

    if __name__ == '__main__':
        main()

And this little snippet can parse this many of command line switches and produce different kinds of arguments - boolean, list, integer and positional

.. sourcecode:: shell

    cmd here
    cmd here -v
    cmd here --verbose 2
    cmd here -vvvvv
    cmd here --all
    cmd here -av
    cmd here -k myself -k green --key fat
    cmd --help

Explanation
============
First one is simple. Positional argument "here" stored into variable *dest*, all the other arguments have default values.

Second one shows how to handle verbosity level. Default "verbose" value was 0, so adding one more "-v" to command line increases verbosity level to 1.

Next one sets exact value to same variable unstead of counting and adding. Now "verbose" equals to int(2).

Here you see same magic as in second one, but "-v" switch repeated five times, so "verbose" argument equals to int(5). Keep in mind, this is not just "-v" five times, but "-v" five times plus default "verbose" value.

Next one sets "all" argument to boolean True. 

You can mix short forms of different arguments, increasing verbosity level at the same time as setting boolean argument to True.

Key default value is empty list, so repeating *-k* with different values results with all this values passed to function as list. Key == ["myself", "green", "fat"]

Auto-generated help
====================
Last one shows help! In that short example help would show just list of all options and short forms.

If you want explain params with some usefull messages, use docstring as following:

.. sourcecode:: python

    from consoleargs import command

    @command
    def main(dest, verbose=0, all=False, key=[]):
      """
      :param verbose: talk all the way
      :param all: dont ask confirmations
      :param key: what keys to use when signing
      """
      pass

    if __name__ == '__main__':
        main()

Generated help:

.. sourcecode:: shell

    Usage c.py DEST [OPTIONS]


    Options:
     --all -a  dont ask confirmations
     --verbose -v  talk all the way
     --key -k  what keys to use when signing


Some more magic
===================

All arguments without default values are threated as simple positional arguments. First example shows only one positional argument, but you can have more. Additionaly you can declare first argument as list, so all positional arguments end up there.

.. sourcecode:: python

    @command(positional=("dest",))
    def main(dest=[], verbose=0, all=False, key=[]):
      pass

.. sourcecode:: shell

    cmd here there all we are -v

Now dest == ['here', 'there', 'all', 'we', 'are'] and 'verbose' = int(1)
