# sleepuntil
<img src="https://travis-ci.org/jnidzwetzki/sleepuntil.svg?branch=master">

This program acts as the famous ``sleep`` unix command. The main difference is,  that ``sleepuntil`` sleeps until a certain time is reached. ``sleep`` in contrast sleeps a fixed amount of seconds.

``sleepuntil`` was written to take over simple jobs in maintenance work (e.g., shutdown the mysql server at 06:00 am).

## Usage
```bash
$ ./sleepuntil -help

Usage: sleepuntil <time> <flags>

  -help
    	Show help.
  -progress
    	Show a progress animation for the remaining time.
  -verbose
    	Be verbose.

Version: 0.1
Please report bugs here: https://github.com/jnidzwetzki/sleepuntil/issues
```

## Examples
__Note:__ You should use the ``&&`` operator to schedule commands. In contrast to ``;``, the next command is only executed if the execution of the previous command (``sleepuntil``) was successful. The ``;`` operator executes the next command in any case. When a wrong date format was specified (or a date in the past) the execution of ``sleepuntil`` fails. When ``;`` is used, the next command is executed immediately, when ``&&`` is used, the next command is not executed.

```bash
# Sleep until 04:00 and shutdown the MySQL server afterwards
sleepuntil 04:00 && service mysql stop

# Sleep until 2019-01-02 15:04:05, show the remaining time and restart the apcahe webserver afterwards
sleepuntil 2019-01-02 15:04:05 -progress && service apache2 restart
|****--------------------------------------------------------------------------------------------|
```

## License
This project is licensed under the Apache 2.0 license. See the [LICENSE](./LICENSE) file for details.
