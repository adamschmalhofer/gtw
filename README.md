gtw - git-taskwarrior wrapper
=============================

Keeps taskwarrior tasks in a separate branch of a git repository.

All commands are passed as-is to taskwarrior. Any modifications by taskwarrior
are then automatically committed and pushed to the main repository's branch.

Configuration
-------------

gtw uses four optional config variables from the main git repository:

    git config gtw.repository /path/to/taskwarrior-repository
    git config gtw.branch tasks
    git config gtw.command task
    git config gtw.taskdata-var-name TASKDATA

If gtw.repository is unset, the taskwarrior repository will be created in .git/task.

If gtw.branch is unset, tasks branch will be used by default.

If gtw.command is unset, task will be used by default.

If gtw.taskdata-var-name is unset, TASKDATA will be used by default. You won't
want to change this if you use taskwarrior. This changes the variable name that
is used to pass the path to the directory that the command uses for its files.

Usage
-----

    cd your-project-repository/
    gtw <taskwarrior command>
    gtw add demonstrate usage # calls "task add demonstrate usage"
    git log tasks # taskwarrior changes are pushed into this branch

Using todo.txt instead of taskwarrior
-------------------------------------

It is possible to use todo.txt shell script instead of taskwarrior. First you
need to set command to use todo.sh (or todo-txt under Debian):

    git config --global --add gtw.command todo.sh

And then set the name of the shell variable that todo.txt uses to know which
folder to look in:

    git config --global --add gtw.taskdata-var-name TODO_DIR

Now make sure your todo.cfg allows use to override the TODO_DIR-variable. Instead of a line like

    export TODO_DIR="/Users/gina/Documents/todo"

replace it with something like:

    export TODO_DIR=${TODO_DIR:-"/Users/gina/Documents/todo"}

This tells todo.sh to only use the TODO_DIR value in the configuration file if
it hasn't already been set (like we do with gtw). Now you should be ready to go.

License
-------

Licensed under GPLv3, see http://www.gnu.org/licenses/gpl-3.0.html
