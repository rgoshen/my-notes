# Git Cheatsheet

## Git configuration {collapsible="true" default-state="expanded"}

- `git config --global color.ui auto`
- **Define author name**: `git config --global user.name 'user name'`
- **Define author email**: `git config --global user.email 'user email'`
- **Create alias for git command**: `git config --global alias.<alias_name><git-command>`
- **Define text editor used by git commands**: `git config --system core.editor '<editor> --wait'`
- **Open the global configuration file in a text editor for manual editing**: `git config --global --edit`

> NOTE:
>
> `--global`: sets to all repos on the machine
>
> `--local` or not passing a config level option: sets it local repo only
>
> `--system` set config for entire system, all users, all repos on the machine

## Commands Related to Remote Repository {collapsible="true" default-state="expanded"}

### Adding

- **Option 1 (Cloning)**: `git clone <url>`
- **Option 2 (Clone to a specific directory)**: `git clone <repo_URL><directory>`
- **Option 3 (map to a remote repo to a reference in your local repo)
  **: `git remote add <remote_name> <remote-repo-url>`

### Pushing

- **Push to remote repo**: `git push` or `git push origin main`
- **Push local branches to remote (first time)**: `git push -u <remote_name><local_branch_name>`
- **Push the local repo branch under**: `<local_branch_name>` to the remote repo @ `<remote_name>`

### Removing

- `git remote rm upstream`

### Misc

- **Fetching remote**: `git fetch <remote name>/<branch name>`
- **Checkout remote**: `git checkout <remote name>/<branch name>`

## Commands Related to Starting a Git Repo {collapsible="true" default-state="expanded"}

- **Option 1 (starting from remote)**:`git clone <url>`

**Option 2 (Local directory already created)**:

```bash
cd <project-folder>
git init
```

**Option 3 ((Local directory NOT already created)**: `git init <project_directory>`

**Option 4: (initialize empty repo)**: `git init --bare <project_directory>`

## Commands Related to Workflow {collapsible="true" default-state="expanded"}

### Saving Changes to the Repo

Option #1 (add single file): `git add <project_file>`

Option #2 (add all files): `git add .`

Option #3 (interactive staging session): `git add -p`

### Committing Changes to the Repo

Option #1 (open interactive editor): `git commit`

Option #2 (commit with a short message): `git commit -m "some short message"`

Option #3 (change a commit message): `git commit --amend`

### Delete a branch

- **Delete a branch (local)**: `git branch -D <branch-name>`
- **Option 1 (Delete remote branch)**: `git push origin :<branch-name>`
- **Option 2 (Delete remote branch)**: `git push origin --delete <branch-name>`

### Misc

- **Create a branch from remote**: `git checkout -b <new_branch_name> <remote>`

## Commands Related to Checking Status or History {collapsible="true" default-state="expanded"}

Option #1: `git diff --color-words`

Option #2: `git diff-highlight`

Option #3: `git diff branch1 ... branch2`

Option #4: `git diff <branch1><branch2> ./file.txt`

## Glossary {collapsible="true"}

A definition list or a glossary:

First Term
: This is the definition of the first term.

Second Term
: This is the definition of the second term.


<seealso>
    [Setting up Git](https://www.theodinproject.com/paths/foundations/courses/foundations/lessons/setting-up-git)
</seealso>