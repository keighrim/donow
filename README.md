Time tracker for Todo.txt
=========================

Donow add-on allows to keep track of the total time spent on an activity. This software was originally developed at https://github.com/clobrano/todo.txt-cli under the GPL3 license. 

# Keep track of current work

Donow writes on the stdout the **current activity and the time spent on it** since the last start. Each X minutes (default=10) a **desktop notification** will remind you the current running activity, to avoid to forget to stop the timer when not needed anymore.
  * Desktop notificaions are sent via `notify-send` (`libnotify` pacakge) on Linux, and via apple script on Mac. Notification is not supported on Windows at for moment. 


# Logging

##### All logging mechanisms below can be toggled by editing `donow` file. 
When the timer is stopped using CTRL-C, donow will log worked time if configured. 

## todo.txt logging

This will append a substring *min:total-time-spent* (being **time** expressed in minutes) to the todo.txt item.
When the pattern "min:number" already exists, donow just updates the counter.

## Text file logging

This will log start and end time of your work in a text file. East start and end will be logged as seprate lines

## CSV file logging 
This will log start and end time of your work in a CSV file. Each session will be logged on a single line, with following columns ; 
```
Year, Month, Day, Time, Duration, Start (seconds since epoch), End (seconds since epoch)
```
NB: The output function is very simple and cannot handle edge cases such as commas (`0x002c`) and double quotes (`0x0022`) in the task item. Please refrain from using those characters in todo.txt file until the function gets updated. 

 

# Example of use

```
    $ todo.sh list
    1 design Python interface for Todo.txt
    2 write a basic description of donow addon min:5
    --
    TODO: 2 of 2 tasks shown
    $ todo.sh donow 1
    Working on: design Python interface for Todo.txt
    [design Python interface for Todo.txt] 11 minute(s) passed^C
    1 design Python interface for Todo.txt min:11
    $ todo.sh donow 2
    Working on: write a basic description of donow addon min:5
    [write a basic description of donow addon min:5] 12 minute(s) passed^C
    2 write a basic description of donow addon min:5
    TODO: Replaced task with:
    2 write a basic description of donow addon min:17
```
