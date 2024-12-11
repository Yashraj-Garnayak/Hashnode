---
title: "First Week in DevOps: Mastering Linux Basics"
seoTitle: "DevOps Week 1: Learn Linux Essentials"
seoDescription: "Learn the essentials of Linux for DevOps with navigation, file management, process control, and package management in CentOS Stream 9"
datePublished: Thu Nov 14 2024 21:33:40 GMT+0000 (Coordinated Universal Time)
cuid: cm3htumrp000q09l60pma7kva
slug: first-week-in-devops-mastering-linux-basics
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1731619445462/a02c3a19-9451-404c-b863-1e6a46de1b42.webp
tags: linux, devops, devops-journey, devopscommunity

---

This week, I delved into the core of Linux, specifically on CentOS Stream 9, focusing on directories, files, and the fundamental idea that *everything in Linux is a file*. I worked through navigation commands, file management, process control, and more. Below, I’ll walk you through why Linux is crucial in DevOps, followed by a breakdown of some essential commands with code blocks and simple explanations.

---

### 🔍 **Why Linux is Important for DevOps and System Administration**

Linux is the backbone of most servers and DevOps environments. It’s open-source, highly customizable, and offers great control, making it a must-know for anyone in the DevOps field. Whether you're automating tasks, managing servers, or deploying applications, knowing Linux commands allows you to interact directly with the system, making it more efficient and powerful than relying on GUI-based tools.

Getting familiar with Linux interfaces is essential because you’ll work in environments that depend on the CLI (Command Line Interface). The commands will become second nature once you get the hang of it.

---

### **Essential Linux Commands with Code Blocks and Explanation**

#### **Navigation and File Management Basics**

* `pwd` – *Print Working Directory*: This command shows the current directory you're in. It's useful when you're navigating through the filesystem and want to check your current location.
    
    ```bash
    $ pwd
    /home/user
    ```
    
    **Explanation**: The terminal returns `/home/user`, which is the directory you’re currently inside. It’s like checking your location on a map.
    
* `ls` – *List Files*: Lists all files and directories in the current directory. You can add flags like `-l` for a detailed view or `-a` to include hidden files.
    
    ```bash
    $ ls
    Documents  Downloads  Pictures
    ```
    
    **Explanation**: This lists the contents of the current directory. Here, it shows three directories: Documents, Downloads, and Pictures.
    
* `cd <directory>` – *Change Directory*: Allows you to navigate to another directory. For example, `cd Documents` would take you into the Documents folder.
    
    ```bash
    $ cd Documents
    $ pwd
    /home/user/Documents
    ```
    
    **Explanation**: Here, you use `cd` to go to the "Documents" directory, and `pwd` confirms your new location inside it.
    
* `mkdir <directory_name>` – *Make Directory*: This command creates a new directory (folder).
    
    ```bash
    $ mkdir my_folder
    $ ls
    Documents  Downloads  my_folder
    ```
    
    **Explanation**: The `mkdir` command creates a folder called `my_folder` in the current directory. After running `ls`, you can see it listed.
    
* `touch <file_name>` – *Create a New File*: This command creates a new empty file.
    
    ```bash
    $ touch example.txt
    $ ls
    Documents  Downloads  example.txt
    ```
    
    **Explanation**: The `touch` command creates a new file named `example.txt`. It doesn’t have any content at first; it’s just an empty file.
    
* `cp <source> <destination>` – *Copy Files/Directories*: This command copies a file or directory from one location to another.
    
    ```bash
    $ cp example.txt my_folder/
    $ ls my_folder
    example.txt
    ```
    
    **Explanation**: This copies `example.txt` into `my_folder`. You can verify with `ls` to check that the file is now inside the folder.
    
* `mv <source> <destination>` – *Move or Rename Files*: This command either moves files from one place to another or renames them.
    
    ```bash
    $ mv example.txt renamed_example.txt
    $ ls
    renamed_example.txt
    ```
    
    **Explanation**: Here, `mv` is used to rename `example.txt` to `renamed_example.txt`.
    
* `rm <file_name>` – *Remove Files*: Deletes a file permanently.
    
    ```bash
    $ rm renamed_example.txt
    $ ls
    ```
    
    **Explanation**: The `rm` command deletes the file. After executing it, you’ll no longer see `renamed_example.txt` in the directory.
    

#### **Viewing and Editing Files**

* `cat <file_name>` – *Concatenate and Display File Content*: Displays the contents of a file in the terminal.
    
    ```bash
    $ cat greetings.txt
    Hello, Linux!
    ```
    
    **Explanation**: The `cat` command outputs the content of `greetings.txt` to the terminal. In this case, it shows "Hello, Linux!"
    
* `nano <file_name>` – *Text Editor*: Opens the file in the nano text editor, allowing you to edit it.
    
    ```bash
    $ nano file.txt
    ```
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1731618392325/b74d7f60-4f73-4333-9981-708867a2d99e.png align="center")
    
    **Explanation**: `nano` opens a file in the terminal editor. You can make changes, save, and exit with simple keyboard commands.
    
* `echo "text" > <file_name>` – *Write Text to a File*: Writes or overwrites text into a file. Use `>>` to append.
    
    ```bash
    $ echo "Hello, Linux!" > greetings.txt
    $ cat greetings.txt
    Hello, Linux!
    ```
    
    **Explanation**: The `echo` command writes "Hello, Linux!" into the file `greetings.txt`. If the file already existed, it would overwrite its content.
    

#### **Process Management Commands**

* `ps` – *Show Running Processes*: Displays a snapshot of the current processes running on your system.
    
    ```bash
    $ ps
      PID TTY          TIME CMD
     1234 pts/0    00:00:01 bash
     2345 pts/0    00:00:00 ps
    ```
    
    **Explanation**: This shows the current processes, with `PID` representing the unique Process ID. You can use it to monitor running programs.
    
* `top` – *Interactive Process Viewer*: Provides real-time updates on processes, system resource usage (CPU, memory), and more.
    
    ```bash
    $ top
    # (Displays a real-time process list, press `q` to exit)
    ```
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1731618423084/61c5ace6-f4ce-4ea0-8017-e95d410a4526.png align="center")
    
    **Explanation**: `top` gives an interactive list of processes sorted by resource usage. You can monitor how much memory and CPU different processes are using.
    
* `kill <PID>` – *Kill a Process*: Terminates a process using its PID (Process ID).
    
    ```bash
    $ kill 1234
    ```
    
    **Explanation**: The `kill` command is used to stop a process. In this case, it ends the process with PID 1234.
    

#### **Package Management with DNF and RPM (CentOS Stream 9)**

Since CentOS Stream 9 uses the DNF package manager, here are some commands to manage software packages.

* `dnf update` – *Update System*: Updates all installed packages to the latest available versions.
    
    ```bash
    $ sudo dnf update
    ```
    
    **Explanation**: This command checks for updates for all installed packages and applies them, ensuring your system is up to date.
    
* `dnf install <package>` – *Install a Package*: Installs a new package from the CentOS repository.
    
    ```bash
    $ sudo dnf install nano
    ```
    
    **Explanation**: Installs the `nano` text editor, allowing you to edit files from the terminal.
    
* `rpm -ivh <package.rpm>` – *Install an RPM Package*: Installs a package using its `.rpm` file.
    
    ```bash
    $ sudo rpm -ivh example.rpm
    ```
    
    **Explanation**: `rpm` installs an RPM package manually. The `-i` flag installs, `-v` provides verbose output, and `-h` shows hash marks to indicate progress.
    
* `rpm -e <package>` – *Uninstall an RPM Package*: Removes an installed RPM package.
    
    ```bash
    $ sudo rpm -e example
    ```
    
    **Explanation**: This command removes the package named `example` from your system.
    

---

This week’s journey has equipped me with a solid understanding of Linux commands. These fundamental tools are essential for anyone working in DevOps or system administration. As I continue to practice, Linux will become an even more powerful tool in my DevOps toolkit. 🐧