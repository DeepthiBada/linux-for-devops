# Commands we should know to make our work easier

1. rg (ripgrep)

   rg is a very fast text search tool. It's a modern replacement for grep.

   syntax:

   rg "pattern" [directory/file]

   ex: rg "error"

   rg -i "sample.sh"

   rg -n "class"

   rg "public" -g *.java
   
2. fzf (fuzzy finder)

   fzf is an interactive fuzzy search tool.

   It helps you quickly search:

   Files

   Directories

   Command history

   Git branches

   Processes

   syntax:

   fzf

   search for respective file name, it will retrieve the path
3. bat

   bat is a modern replacement for cat.

   Features:

   Syntax highlighting

   Line numbers

   Git integration

   Paging

   syntax: bat file_name

To install these commands, use your system's package manager:

* macOS (Homebrew)

  ex: brew install ripgrep fzf bat

  brew install ranger

* Ubuntu/Debian (APT)

  ex: sudo apt update

  sudo apt install ripgrep fzf bat

4. ranger - Terminal File Manager

   ranger is a lightweight terminal-based file manager that provides an intuitive way to navigate directories, browse files, and visualize the       folder structure without leaving the command line.

   ### Why use ranger?
   
📁 Easy navigation through directories

🌳 Visual representation of folder hierarchy

⌨️ Keyboard-driven interface for faster navigation

📄 Preview text files, images, and PDFs (with optional dependencies)

🚀 Faster than repeatedly using cd and ls

Ex: ranger

   <img width="1000" height="900" alt="image" src="https://github.com/user-attachments/assets/b4bf896b-55a9-49ab-9e45-e9b5a2fdc0cc" />

   <img width="1470" height="933" alt="image" src="https://github.com/user-attachments/assets/977a5f77-000e-4727-98da-7b9af49789fd" />

5. lazygit

   lazygit is a simple terminal UI (TUI) for Git that allows you to perform common Git operations using an interactive interface instead of typing long Git commands.

It is ideal for developers who want to manage repositories, commits, branches, and merge conflicts efficiently from the terminal.

Installation:

brew install lazygit

   Ex:
   lazygit

   <img width="1470" height="935" alt="image" src="https://github.com/user-attachments/assets/564aed21-a1fb-4376-b440-3c70828bf99f" />

6. lazydocker

   lazydocker is a terminal-based UI (TUI) for Docker that lets you manage containers, images, volumes, networks, and logs interactively without typing multiple Docker commands.

It is a great productivity tool for developers and DevOps engineers working with Docker.

Installation: brew install lazydocker

Ex: 
lazydocker

<img width="1470" height="933" alt="image" src="https://github.com/user-attachments/assets/68c1ce44-be6b-4953-a483-b652838d9ba8" />

7. glances

   glances is a cross-platform system monitoring tool that provides a real-time overview of your system's performance, including CPU, memory, disk, network, processes, and more—all from a single terminal interface.

It is widely used by Linux administrators, DevOps engineers, and SREs to monitor system health.

Installation: brew install glances

Usage: glances

It displays all top and htop...info's in one dashboard


