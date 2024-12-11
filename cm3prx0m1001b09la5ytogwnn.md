---
title: "🚀 TMUX for Beginners: Your DevOps Friend"
datePublished: Wed Nov 20 2024 11:01:41 GMT+0000 (Coordinated Universal Time)
cuid: cm3prx0m1001b09la5ytogwnn
slug: tmux-for-beginners-your-devops-friend
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1732100405738/26fde97a-d21c-4bfe-a836-99e4f2babc5f.png
tags: devops, tmux, devops-tools, devops-journey

---

If you’ve ever felt stuck managing multiple terminal windows while working on a server, tmux is here to rescue you! tmux is a **terminal multiplexer**, allowing you to open, split, and manage multiple terminal sessions in one window. Think of it as having a superpower to juggle tasks on your terminal effortlessly. 💪

### **Who Introduced Me to TMUX? 🤝**

I was introduced to tmux by **Advitya Sharma**, a fellow developer and a React expert. His enthusiasm for efficient workflows inspired me to dive into this amazing tool. Thank you, Advitya, for opening up this world of productivity! 🚀

### **Why Should You Learn TMUX as a Beginner?**

As you start learning about **servers** and exploring terminal-based tools, tmux can help you:

1\. **Keep Sessions Active**: Detach from a session and reconnect without losing progress.

2\. **Monitor Logs**: Check multiple logs simultaneously in split panes.

3\. **Run Long Commands**: Start long-running tasks and revisit them later.

4\. **Work Remotely**: Reconnect to your work on a server, even after disconnection.

---

# **Basic TMUX Commands 🛠️**

**1\. Create a New Session**

Start your first tmux session:

```bash
tmux
```

This opens a fresh tmux session where you can begin your work.

**2\. Detach and Reattach to Sessions**

Working on a server and need to log off without interrupting tasks?

* **Detach from a Session**:
    
    ```bash
    Ctrl+b d
    ```
    

* **Reattach to the Session**:
    
    ```bash
    tmux attach
    ```
    

**3\. List Active Sessions**

If you have multiple sessions running, check them with:

```bash
tmux ls
```

**4\. Rename Your Session**

Give your session a meaningful name to stay organized:

```bash
Ctrl+b $
```

## **How to Exit or Kill a TMUX Session 🛑**

When you’re done with your work in tmux, here’s how to properly exit or kill a session:

**1\. Exit a Session**

* **Exit the Current Pane or Window**:
    
    ```bash
    exit
    ```
    
    This will close the current pane or window you’re in. If it’s the last window, it will terminate the session.
    

**2\. Kill a Session Directly**

* **Kill a Specific Session**:
    
    ```bash
    tmux kill-session -t <session_name>
    ```
    
    Replace &lt;session\_name&gt; with the name of your session.
    

* **Kill All Sessions**:
    
    ```bash
    tmux kill-server
    ```
    
    This will terminate all running tmux sessions.
    

**3\. Use a Shortcut to Kill a Window**

If you’re inside tmux and want to close a specific window:

```bash
Ctrl+b &
```

tmux will prompt you to confirm the action.

## **Using TMUX to Learn About Servers 🌐**

Here’s how you can use tmux while exploring servers:

**1\. Monitor Server Logs**

If you’re learning about web servers like Apache or Nginx, use tmux to monitor logs.

* Open a tmux session and run:
    
    ```bash
    tail -f /var/log/nginx/access.log
    ```
    

* Split the pane and monitor error logs:
    
    ```bash
    Ctrl+b %
    tail -f /var/log/nginx/error.log
    ```
    

**2\. Run Commands Without Losing Progress**

While exploring servers, you might need to run updates or install packages:

* Start the task:
    
    ```bash
    sudo apt update && sudo apt upgrade
    ```
    
* Detach from the session if needed:
    
    ```bash
    Ctrl+b d
    ```
    
* Reattach later to check the progress:
    
    ```bash
    tmux attach
    ```
    

**3\. Practice File and Directory Management**

Learning to navigate server directories? Use tmux to practice commands side by side:

* Split the pane vertically:
    
    ```bash
    Ctrl+b "
    ```
    

* Use one pane to create directories:
    
    ```bash
    mkdir my_server_files
    ```
    

* Use the other pane to view them:
    
    ```bash
    ls -l
    ```
    

---

### **How TMUX Helps in Your Learning Journey**

As a beginner exploring **servers**, tmux lets you:

* Keep logs and commands visible side by side.
    
* Run experiments without worrying about losing progress.
    
* Stay organized with multiple tasks on a server.
    

## **What’s Next?**

This week, as you dive into learning about servers, make tmux your companion. It’ll simplify your work and help you focus on understanding the basics. Start small, practice, and soon you’ll feel confident managing servers like a pro!

Have questions or need more tips? Drop a comment below! Let’s grow together. 🚀