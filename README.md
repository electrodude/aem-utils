# aem-utils

Miscellaneous short shell utilities I use frequently

## `makemore` and `makeless`

Inject or steal jobserver tokens from GNU make.  Useful for when you want to
increment or decrement the `-j` setting on a long-running parallel `make`.

Expect `make` to emit warnings such as the following after using this:
```
make: INTERNAL: Exiting with 7 jobserver tokens available; should be 5!
```

## `vim-cp` and `vim-mv`

Copy or move a file, and also move the `vim` undofile.  Assumes all undofiles
are kept in `~/.vim/undo`.  Currently, it only moves one file at a time, it
requires absolute paths, and it requires the second argument to be the filename
and not just the target directory.  It won't do the right thing if you only
specify the target directory.

BUG: Should be more robust, and should at least complain instead of doing the wrong thing.

## `git-vim-cp` and `git-vim-mv`

Like `vim-cp` and `vim-mv`, but also renames it in git.

## `rmsame`

Compare two files, and ask if you want to delete the first if the two are identical.

## `rmlnsame`

Compare two files, and ask if you want to replace the first with a symlink to the second if the two are identical.

## `samefile`

Returns success if two files are the same inode, and otherwise returns failure.

BUG: Doesn't make sure the files are actually on the same device.

## `unswap`

For each specified swap device, or, if none are specified on the command line,
for each swap device in /proc/swaps, calls `swapoff` and then `swapon`.  Useful
for loading swapped-out pages back into RAM after recovering from a low-memory
condition.
