Introduction
------------

explicate is a debugging wrapper. It takes a command as argument and prints
useful information in case of an error. You can use it as a bash-function or
as stand-alone program.

Examples
--------

# simple example:
        $ ./explicate 'echo "success"' 
        success

# Mode 1: execute command
        $ ./explicate 'echo "success"' 1 "my test"
        success

# Mode 0: Simulation
        $ ./explicate 'echo "success"' 0 "my test"
        echo "success"

# Mode 3: Be verbose
        $ ./explicate 'echo "success"' 3 "my test"
        ============  starting: "my test"  ========== 
        echo "success"
        success
        ------------  done: my test  ---------- 

# Mode 4: What is going on?
        $ ./explicate 'echo "success"' 4 "my test"
        my test

# failing example:
        $ ./explicate 'echo "failure"; exit 2' 1 "my test"
        failure

        *** error: my test
        *** command: echo "failure"; exit 2
        *** error-code: 2
        *** 2017-11-07 12:13:04: host: mycomputer, user: me, directory: /home/me/sources/github/explicate, caller: /home/me/sources/github/explicate/explicate

# failing example with error-reaction
        $ ./explicate 'echo "failure"; exit 2' 1 "my test" 'echo "Im sorry"'
        failure

        Im sorry

        *** error: my test
        *** command: echo "failure"; exit 2
        *** error-code: 2
        *** 2017-11-07 12:14:11: host: mycomputer, user: me, directory: /home/me/sources/github/explicate, caller: /home/me/sources/github/explicate/explicate

    
License
-------

explicate is licensed under "BSD 2-Clause License". You can find the
complete text in ``LICENSE``.

