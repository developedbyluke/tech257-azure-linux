# Linux Commands Documentation

-   [Linux Commands Documentation](#linux-commands-documentation)
    -   [Navigation Commands](#navigation-commands)
    -   [File and Directory Management Commands](#file-and-directory-management-commands)
    -   [File Content Management Commands](#file-content-management-commands)
    -   [Text Editors](#text-editors)
    -   [File Information Commands](#file-information-commands)
    -   [Package Management Commands](#package-management-commands)
    -   [Permissions Commands](#permissions-commands)
    -   [Scripting and Automation](#scripting-and-automation)
        -   [Creating and Running a Provisioning Script for Nginx](#creating-and-running-a-provisioning-script-for-nginx)
        -   [Variables in Shell Scripts](#variables-in-shell-scripts)
    -   [Other Commands](#other-commands)

---

## Navigation Commands

-   `pwd`: Print the current working directory (path).
-   `cd`: Change the directory to the specified path. Without a path, it changes to the home directory of the current user.
-   `cd /`: Change the current working directory to the root directory (`/`).

## File and Directory Management Commands

-   `ls`: List files and directories in the current directory.
-   `ls -a`: List all files and directories, including hidden ones (those starting with a dot `.`).
-   `mkdir [directory_name]`: Create a new directory.
-   `touch [file_name]`: Create an empty file or update the timestamp of an existing file.
-   `cp [source] [destination]`: Copy a file from the source to the destination.
-   `mv [source] [destination]`: Move (rename) a file or directory.
-   `rm [file_name]`: Delete a file.
-   `rm -d [directory_name]`: Remove an empty directory.
-   `rm -r [directory_name]`: Remove a directory and its contents recursively. **Potentially dangerous!**

## File Content Management Commands

-   `cat [file_name]`: Display the contents of a file.
-   `head -n [number] [file_name]`: Display the first n lines of a file.
-   `tail -n [number] [file_name]`: Display the last n lines of a file.
-   `nl [file_name]`: Display the contents of a file with line numbers.
-   `grep [pattern] [file_name]`: Display lines from a file that match a specific pattern or string.
-   `echo [string]`: Print a string to the terminal.

## Text Editors

-   `nano [file_name]`: Open a file in the nano text editor.

    -   **Save Changes**: Press `Ctrl + S` to save the file.
    -   **Exit**: Press `Ctrl + X`. If there are unsaved changes, nano will ask if you want to save them, otherwise it will exit immediately.
    -   **Search Text**: Press `Ctrl + W`, then type the text you're looking for and press `Enter`.
    -   **Cut Text**: Navigate to the line you want to cut and press `Ctrl + K`.
    -   **Paste Text**: Navigate to where you want to paste and press `Ctrl + U`.

-   `vim [file_name]`: Open a file in the vim text editor.
    -   **Enter Insert Mode**: Press `i` to start inserting text at the cursor's location, or `a` to append text after the cursor.
    -   **Save Changes**: Press `Esc` to go back to command mode, then type `:w` and press `Enter` to save the file.
    -   **Exit**: Type `:q` and press `Enter` to quit. If you have unsaved changes, Vim will warn you. To quit without saving, type `:q!` and press `Enter`.
    -   **Search Text**: Press `Esc` to ensure you're in command mode, then type `/{text}` and press `Enter` to search for `{text}`.
    -   **Cut (Delete) Text**: In command mode, navigate to the line you want to cut and press `dd`. To cut a specific number of lines, type `{number}dd`, replacing `{number}` with how many lines you want to cut.
    -   **Paste Text**: After cutting or copying, navigate to where you want to paste and press `p` to paste after the cursor, or `P` to paste before the cursor.
    -   **Undo**: Press `u` in command mode to undo the last action. Press `Ctrl + R` to redo.

## File Information Commands

-   `file [file_name]`: Determine the type of a file.
-   `ps -p $$`: Display the process information for the current shell process (identified by `$$`).
-   `history`: Display the command history of the current shell session.

## Package Management Commands

-   `sudo apt install [package_name]`: Install a package using the apt package manager with superuser privileges.
-   `sudo apt update`: Update the package lists from the repositories.
-   `sudo apt upgrade`: Upgrade all installed packages to their latest versions. Add `-y` to automatically answer "yes" to any prompts.

## Permissions Commands

-   `chmod [permissions] [file_name]`: Change the permissions of a file or directory, e.g. `chmod +x script.sh` to add execute permissions.

## Scripting and Automation

### Creating and Running a Provisioning Script for Nginx

To automate the installation and configuration of Nginx on a Linux system, you can create a shell script. Here's an example script that installs Nginx, starts the service, and enables it to run at boot:

```bash
#!/bin/bash

# Update the package list
sudo apt update

# Install Nginx
sudo apt install -y nginx

# Start the Nginx service
sudo systemctl start nginx

# Enable Nginx to start on boot
sudo systemctl enable nginx

echo "Nginx installation and setup completed."
```

Save this script to a file, for example, `install_nginx.sh`, and make it executable with the command `chmod +x install_nginx.sh`. Run the script using `./install_nginx.sh`.

### Variables in Shell Scripts

1. **Creating a Variable** : Assign a value to a variable with `variable_name=value`. Do not add spaces around the `=` sign. For example, `greeting="Hello, World!"`.
2. **Using a Variable** : Reference the variable with `$variable_name`. For example, `echo $greeting` would print "Hello, World!".
3. **Persisting Variables** : To make variables persistent across sessions and VM restarts, add them to `~/.bashrc`.

```bash
echo 'export greeting="Hello, World!"' >> ~/.bashrc
source ~/.bashrc
```

## Other Commands

-   `curl [URL]`: Transfer data from or to a server using various protocols (e.g., HTTP, FTP).
-   `curl [URL] --output [file_name]`: Download data from a URL and save it to a specified file.
-   `tree`: Display a tree-like representation of directories and files in the current directory. (Note: `tree` might need to be installed separately.)
-   `sudo su`: Switch to the root user account (superuser).

> **Note**: Commands like `rm` and `sudo` can be **potentially dangerous** and cause data loss or system damage if used improperly, so they should be used with caution.
