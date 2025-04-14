```markdown
# Linux & GitHub Cheatsheet

## Linux Commands (Commonly Used)

**Navigation & File System:**

* `pwd`: Print working directory (shows your current location).
* `cd <directory>`: Change directory. Use `cd ..` to go up one level, `cd ~` or `cd` to go to your home directory.
* `ls`: List directory contents.
    * `ls -l`: Long listing (permissions, owner, size, date).
    * `ls -a`: Show all files, including hidden ones (starting with `.`).
    * `ls -h`: Display file sizes in human-readable format.
    * `ls -r`: Reverse order.
    * `ls -t`: Sort by modification time.
    * `ls -al`: Combination of `-a` and `-l`.
* `mkdir <directory>`: Create a new directory.
* `rmdir <directory>`: Remove an empty directory.
* `rm <file>`: Remove a file.
    * `rm -r <directory>`: Remove a directory and its contents recursively (use with caution!).
    * `rm -f <file>`: Force removal (be careful!).
* `touch <file>`: Create an empty file or update the timestamp of an existing one.
* `cp <source> <destination>`: Copy a file or directory.
    * `cp -r <source_dir> <dest_dir>`: Copy a directory and its contents recursively.
* `mv <source> <destination>`: Move or rename a file or directory.
* `cat <file>`: Display the contents of a file.
* `less <file>`: View file contents page by page (use `q` to quit, `/` to search).
* `head <file>`: Display the first few lines of a file (default 10).
    * `head -n <number> <file>`: Display the first `number` lines.
* `tail <file>`: Display the last few lines of a file (default 10).
    * `tail -n <number> <file>`: Display the last `number` lines.
    * `tail -f <file>`: Follow the file in real-time (useful for logs).
* `find <path> -name "<pattern>"`: Find files and directories based on a pattern.
    * `find . -name "*.txt"`: Find all `.txt` files in the current directory and its subdirectories.
* `grep "<pattern>" <file>`: Search for a pattern within a file.
    * `grep -i "<pattern>" <file>`: Case-insensitive search.
    * `grep -r "<pattern>" <directory>`: Search recursively in a directory.
* `sudo <command>`: Execute a command with superuser (administrator) privileges.
* `chmod <permissions> <file>`: Change file permissions.
    * `chmod 755 <file>`: Give owner read, write, execute; group and others read, execute.
    * `chmod +x <file>`: Make a file executable.
* `chown <user>:<group> <file>`: Change file owner and group.
* `df -h`: Display disk space usage in human-readable format.
* `du -sh <directory>`: Display the disk usage of a directory in summary, human-readable format.
* `history`: Show command history.
    * `!n`: Execute the nth command in history.
    * `!!`: Execute the last command.
    * `!string`: Execute the last command starting with "string".

**Process Management:**

* `ps`: Display information about running processes.
    * `ps aux`: Show a detailed list of all processes.
* `top` or `htop`: Display dynamic real-time view of running processes.
* `kill <PID>`: Terminate a process using its Process ID.
    * `kill -9 <PID>` or `kill -KILL <PID>`: Forcefully terminate a process.
* `bg`: Move a stopped job to the background.
* `fg <%job_id>`: Move a background job to the foreground.
* `jobs`: List active jobs.

**Networking:**

* `ip a` or `ifconfig`: Display network interface information.
* `ping <hostname>` or `ping <IP_address>`: Test network connectivity.
* `netstat -tuln`: Display listening ports and network connections.
* `ssh <user>@<host>`: Secure Shell to connect to a remote server.
* `scp <user>@<host>:<remote_file> <local_file>`: Securely copy files between systems (remote to local).
* `scp <local_file> <user>@<host>:<remote_path>`: Securely copy files between systems (local to remote).
* `curl <URL>`: Transfer data from or to a server (often used for web requests).

**Package Management (Examples):**

* **Debian/Ubuntu (apt):**
    * `sudo apt update`: Update package lists.
    * `sudo apt upgrade`: Upgrade installed packages.
    * `sudo apt install <package>`: Install a new package.
    * `sudo apt remove <package>`: Remove a package.
    * `sudo apt purge <package>`: Remove a package and its configuration files.
* **Red Hat/CentOS/Fedora (yum/dnf):**
    * `sudo yum update` or `sudo dnf update`: Update all packages.
    * `sudo yum install <package>` or `sudo dnf install <package>`: Install a package.
    * `sudo yum remove <package>` or `sudo dnf remove <package>`: Remove a package.

**Other Useful Commands:**

* `man <command>`: Display the manual page for a command.
* `echo "<string>"`: Display a string.
* `date`: Display the current date and time.
* `cal`: Display a calendar.
* `alias <new_alias>='<command>'`: Create a shortcut for a command.
    * `unalias <alias>`: Remove an alias.
* `exit`: Close the current terminal session.

## GitHub Basics

**Core Concepts:**

* **Repository (Repo):** A directory containing project files and their version history.
* **Commit:** A snapshot of the repository at a specific point in time.
* **Branch:** An independent line of development within a repository. `main` (or `master`) is usually the primary branch.
* **Pull Request (PR) / Merge Request (MR):** A proposal to merge changes from one branch into another.
* **Fork:** Creating a personal copy of someone else's repository.
* **Clone:** Downloading a repository from GitHub to your local machine.
* **Remote:** A named connection to a remote repository (e.g., `origin` for the main GitHub repo).

**Common Git Commands (Often used with GitHub):**

* **Initialization & Cloning:**
    * `git init`: Initialize a new Git repository in the current directory.
    * `git clone <repository_url>`: Clone a remote repository to your local machine.

* **Basic Workflow:**
    * `git status`: Show the working tree status (modified, staged, untracked files).
    * `git add <file(s)>`: Stage changes for the next commit.
        * `git add .`: Stage all changes in the current directory.
    * `git commit -m "<commit_message>"`: Record staged changes with a descriptive message.
    * `git push <remote> <branch>`: Upload local commits to a remote repository.
        * `git push origin main`: Push commits to the `main` branch of the `origin` remote.
    * `git pull <remote> <branch>`: Download changes from a remote repository and merge them into your current branch.
        * `git pull origin main`: Pull changes from the `main` branch of the `origin` remote.

* **Branching & Merging:**
    * `git branch`: List your local branches.
        * `git branch -r`: List remote branches.
        * `git branch -a`: List all branches (local and remote).
    * `git checkout <branch_name>`: Switch to an existing branch.
    * `git checkout -b <new_branch_name>`: Create a new branch and switch to it.
    * `git merge <branch_to_merge>`: Merge the specified branch into your current branch.
    * `git branch -d <branch_name>`: Delete a local branch (if it has been merged).
    * `git branch -D <branch_name>`: Force delete a local branch (even if not merged).
    * `git push <remote> --delete <branch_name>`: Delete a remote branch.

* **Inspecting History:**
    * `git log`: Show commit history.
        * `git log --oneline`: Show a concise one-line commit history.
        * `git log --graph --oneline --decorate --all`: Visualize the branch and merge history.
        * `git log -n <number>`: Show the last `number` commits.
    * `git show <commit_hash>`: Show details of a specific commit.
    * `git diff`: Show changes between the working directory and the staging area.
    * `git diff --staged`: Show changes between the staging area and the last commit.
    * `git diff <branch1> <branch2>`: Show differences between two branches.

* **Undoing Changes:**
    * `git restore --staged <file>`: Unstage a file.
    * `git restore <file>`: Discard changes in the working directory (revert to the last commit).
    * `git reset --hard <commit_hash>`: Reset your branch and working directory to a previous commit (use with caution, as this can lose data).
    * `git revert <commit_hash>`: Create a new commit that undoes the changes of a specific commit.

* **Remotes:**
    * `git remote -v`: List configured remote repositories.
    * `git remote add <name> <url>`: Add a new remote repository.
        * `git remote add origin <repository_url>`: Add the main GitHub repository as `origin`.
    * `git remote remove <name>`: Remove a remote repository.
    * `git remote rename <old_name> <new_name>`: Rename a remote repository.

**GitHub Specific Actions (Often done via the web interface):**

* Creating a new repository.
* Forking a repository.
* Creating and merging Pull Requests.
* Managing issues and discussions.
* Setting up GitHub Actions for CI/CD.
* Using GitHub Pages for website hosting.

**Helpful Resources:**

* `man <command>` (for Linux commands)
* `git --help` or `git help <command>`
* [GitHub Docs](https://docs.github.com/)
* [Git Documentation](https://git-scm.com/doc)

This cheatsheet provides a good starting point for common Linux and GitHub operations. Remember to practice these commands to become more proficient.
```
