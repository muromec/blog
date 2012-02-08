pub_date: 2012-02-09
tags: [python, consoleargs]
public: yes
title: Consoleargs

Consoleargs
-----------

Why?
=========
Недавно мне для одного питоновского проекта нужно было делать консольный интерфейс. Стал смотреть, чем в питончике модно парсить арументы командной строки. Посмотрел, увидел argparse и заплакал - писали какие-то жависты, не знаю, куда смотрит Гвидо.

Поэтому я сделал свой парсер с человекопитоновским интерфейсом - consoleargs <i>(произносится сос-ноль-аргс)</i>. Чтобы описать параметры, которые принимает консольное приложение, достаточно импортнуть модуль и повесить на main() декоратор.


Example
========
Вот так, например

.. sourcecode:: python

    from consoleargs import command

    @command
    def main(dest, verbose=0, all=False, key=[]):
      pass

    if __name__ == '__main__':
        main()

И это уже можно вызывать из консоли с вот такими аргументами:

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
Что тут происходит? Начиная с самого первого: скрипту передается один аргумент - "here". Соответственно, в функцию *main()* приходит переменная dest с значением "here". Достаточно просто.

Следующий пример интереснее: библиотека сама догадалась, что "verbose" может иметь сокращенную форму "-v". В функцию вместо дефолтного значения "0" (интовый нуль) передалась единица.

В третьем примере используется полная форма аргумента и явное указание значения. В функцию передается интовое значение "2".

В следующем случае, библиотека суммирует количество аргументов "-v" и в функцию передается знаечение "5". Пять - это количество ключей -v прибавленное к дефолтному значениею (нулю), а не просто количество ключей.

Параметр "--all" указывается в полной форме, в функцию передается булево значение True.

Параметр "key" имеет дефолтоное значение в виде списка, поэтому при указании "-k" несколько раз, в функцию передается список из всех аргументов -k.


Auto-generated help
====================
И самое главное - автоматически генерируется хелп. Если указать для функции main() докстринг, то в хелпе будет указано назначение параметров:

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

.. sourcecode:: shell

    Usage c.py DEST [OPTIONS]


    Options:
     --all -a  dont ask confirmations
     --verbose -v  talk all the way
     --key -k  what keys to use when signing


Some more magic
===================

Если хочется еще больше, то можно сделать вот так:

.. sourcecode:: python

    @command(positional=("dest",))
    def main(dest=[], verbose=0, all=False, key=[]):
      pass

Теперь можно вызвать команду с несколькими аргументами, которые все упадут в dest: "cmd here there aur -vvv".

