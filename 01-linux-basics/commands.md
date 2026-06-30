## Commands we should know to make our work easier

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

* Ubuntu/Debian (APT)

  ex: sudo apt update

  sudo apt install ripgrep fzf bat
