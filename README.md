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
    git config gtw.remote origin

If gtw.repository is unset, the taskwarrior repository will be created in .git/task.

If gtw.branch is unset, tasks branch will be used by default.

If gtw.command is unset, task will be used by default.

If gtw.remote is unset, origin will be used by default. This is the remote that
changes to the gtw.branch are pushed. Set it to the empty string to deactivate
this feature.

Usage
-----

    cd your-project-repository/
    gtw <taskwarrior command>
    gtw add demonstrate usage # calls "task add demonstrate usage"
    git log tasks # taskwarrior changes are pushed into this branch

License
-------

Licensed under GPLv3, see http://www.gnu.org/licenses/gpl-3.0.html