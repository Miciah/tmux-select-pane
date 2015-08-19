# tmux-select-pane

This is a shellscript for selecting a Tmux pane based on the process
running in that pane.

## Installation

Copy the script into a directory in your `PATH`.

## Usage

The script may be run in one of two ways:

    tmux-select-pane -p <pid>

or

    tmux-select-pane -f <filename>

In the first form, the script attempts to determine the Tmux pane in
which the process with the specified pid is running.  If successful, the
script selects the pane and the window containing that pane.

In the second form, the script attempts to determine the process that
has the specified file open, and if exactly one such process is found,
then the script proceeds as if it had been run with the `-p` flag with
the pid of that process.

The script searches for `TMUX_PANE` in `/proc/<pid>/environ` to relate
pid to Tmux window and pane, and it uses `lsof` to relate file to pid,
so it is unlikely to work on other operating systems beside Linux or if
`lsof` is not installed.

For use with Vim, see [the tmux-select-pane.vim Vim plugin].

[the tmux-select-pane.vim Vim plugin]: https://github.com/Miciah/tmux-select-pane.vim/

## Copyright

Copyright (c) 2015 Miciah Dashiel Butler Masters
