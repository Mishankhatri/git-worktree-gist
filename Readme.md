# GIT WORKTREE

- A Git worktree is a linked copy of your Git repository, allowing you to have multiple branches checked out at a time.
- A worktree has a separate path from your main working copy, but it can be in a different state and on a different branch.
- The advantage of a new worktree in Git is that you can make a change unrelated to your current task, commit the change, and then merge it at a later date, all without disturbing your current work environment.

  More info on: [Git WorkTree](https://git-scm.com/docs/git-worktree)

## GIT WORKTREE COMMANDS-GIST

    - git worktree add [-f] [--detach] [--checkout] [--lock [--reason <string>]]
    [-b <new-branch>] <path> [<commit-ish>]
    - git worktree list [-v | --porcelain [-z]]
    - git worktree lock [--reason <string>] <worktree>
    - git worktree move <worktree> <new-path>
    - git worktree prune [-n] [-v] [--expire <expire>]
    - git worktree remove [-f] <worktree>
    - git worktree repair [<path>…​]
    - git worktree unlock <worktree>

## GIT WORKTREE COMMANDS- DETAILS

- ## add:

  `$git worktree add [-f] [--detach] [--checkout] [--lock [--reason <string>]] [-b <new-branch>] <path> [<commit-ish>]`

  > Create a worktree at <path> and checkout <commit-ish> into it. The new worktree is linked to the current repository, sharing everything except per-worktree files such as HEAD, index, etc.

- ## remove:

  `$git worktree remove [-f] <worktree>`

  > Remove a worktree. Only clean worktrees (no untracked files and no modification in tracked files) can be removed. Unclean worktrees or ones with submodules can be removed with --force. The main worktree cannot be removed.

- ## list:

  `$git worktree list [-v | --porcelain [-z]]`

  > List details of each worktree. The main worktree is listed first, followed by each of the linked worktrees. The output details include whether the worktree is bare, the revision currently checked out, the branch currently checked out (or "detached HEAD" if none), "locked" if the worktree is locked, "prunable" if the worktree can be pruned by the prune command.

- ## lock:

  `$git worktree lock [--reason <string>] <worktree>`

  > If a worktree is on a portable device or network share which is not always mounted, lock it to prevent its administrative files from being pruned automatically. This also prevents it from being moved or deleted. Optionally, specify a reason for the lock with --reason.

- ## unlock:

  `$git worktree unlock`

  > Unlock a worktree, allowing it to be pruned, moved or deleted.

- ## move:

  `$git worktree move <worktree> <new-path>`

  > Move a worktree to a new location. Note that the main worktree or linked worktrees containing submodules cannot be moved with this command. (The git worktree repair command, however, can reestablish the connection with linked worktrees if you move the main worktree manually).

- ## prune:

  `$git worktree prune [-n] [-v] [--expire <expire>]`

  > Prune worktree information in $GIT_DIR/worktrees.

- ## repair:

  `$git worktree repair [<path>…​]`

  > Repair worktree administrative files, if possible, if they have become corrupted or outdated due to external factors.For instance, if the main worktree (or bare repository) is moved, linked worktrees will be unable to locate it.
  
  > Running repair in the main worktree will reestablish the connection from linked worktrees back to the main worktree.Similarly, if the working tree for a linked worktree is moved without using git worktree move, the main worktree (or bare repository) will be unable to locate it. Running repair within the recently-moved worktree will reestablish the connection. If multiple linked worktrees are moved, running repair from any worktree with each tree’s new <path> as an argument, will reestablish the connection to all the specified paths.If both the main worktree and linked worktrees have been moved manually, then running repair in the main worktree and specifying the new <path> of each linked worktree will reestablish all connections in both directions.
