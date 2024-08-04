# Script installation

- Some hacking tools are developed by some peoples and those peoples make it open-source, that means we can get those scripts/programs from GitHub.
- So we can download and use it. For this purpose git have a feature called ‘clone’
- Syntax
    1. git clone "link_of_the_script_from_GitHub"

# Script modules

- Scripts are made with scripting languages(programming) like{ python,bash,go,ruby,...}.
- So when we use these programming languages to do tasks their is something called modules/libraries these are needed to run the script as the dependencies.
- Example:
    1. **Python**: to install python modules we use -> **pip install "module name"**
            - For requirements file -> **pip install -r requirements.txt**
    2. **Go**: to install go modules -> **go install "module name"**
    3. **Ruby**:  to install ruby modules -> **gem install "module name"**

# Python installation

- If pip is not found there will be an error ---> **sudo apt install python3-pip**
- It will install ---> **pip install "term"**
- If the package is already installed ---> **pip install -r requirement.txt**

# Go package installation

- Go scripts are scripts made with go-lang(go programming language).
- There are 2 installation methods.

1. Old version ---> **go get "link"**
2. New version
    1. Downloading the package ---> **go install "link"**
	2. Moving the file to /usr/bin( the default download place is /home/username/go/bin/)
    	    ---> **mv filename /usr/bin**

## If you need help on linux about commands

1. man(manual)

- This will give you the whole manual and instruction of a tool or command.
        --->**man "your command"**

2. Help

- Some Commands have help option.
**command" -h**
**command" -help**
**command" - -help**

# Linux Processes & Services

- As we interact with Linux, we create numbered instances of running programs called “processes”
- commands

1. **ps**  -> for process running on my shell
2. **ps -A**-> view all running process
3. **ps -u** username -> view users process

- PID = Process ID

- To stop process---> **Kill [options] [PID]**
- More on kill

1. **kill -19 PID**  -> to stop the process
2. **kill -18 PID** -> to resume the process we stopped
3. **kill -9 PID** -> to Stop a process immediately

- there are 31 options.
- For this purpose we have the tool called **top** installed on linux by default.
- But to make this fun we will use **htop**, it is colorful and more enhanced!

## To kill on htop

1. Search for the process
2. Choose KILL(f9) and kill it!


# Foreground / background

- Thus far, we have run commands at the prompt and waited for them to complete. We call this running in the “foreground.”
- Use the **“&”** operator, to run programs in the “background” or press ^Z
- To get the background process back to foreground **Fg** command.
- To stop a process going inside your shell just press ^C.

# Null device

- /dev/null - Redirects output to nowhere.
- If you want to ignore output, you can send it to the null device, /dev/null. 
- The null device is a special file that throws away whatever is fed to it. 
- You may hear people refer to it as the bit bucket. 
- If you do not want to see errors on your screen and you do not want to save them to a file, you can redirect them to /dev/null
- On shell output there are 2 things.
    1. STDERR =  2
    2. STDOUT  =  1
- To redirect the errors from a command result we do 
    - **command 2> filename**  =>  here if you check the file you saved on it have errors only
- To redirect the error-FREE output
    - **command 1>filename**
- So if we redirect our commands output to /dev/null we will get error free result
    - **command 2> /dev/null**

## Symbolic linking

- Symbolic linking is same as Windows shortcut.
- Symbolic linking is a process of creating a linked shortcut form of file to some pre-existed file or folder.
- Also if a file path is too long we can create a symbolic linking.
- Symbolic linked files shows ‘l’ in listing of ls command. Also there will be a ‘->’ to show the linked file.
- Syntax: **ln -s file_path "name"** 

## alias

- Used to give a name to some bunch of commands.
- But this doesn’t work after you closed the terminal.
- If you want to make it work,You will add it to your shell config file.
- Example for bash and fish, zsh…
    1. bash= ~/.bashrc
    2. zsh= ~/.zshrc
    3. fish= ~/.config/fish/config.fish

# Tmux - Terminal Multiplexer

- Tmux is used to classify our terminal work.
- You can install it using apt. On kali it is built-in
- Then to start it just type ‘tmux’
- To Create config file type
    1. create nano .tmux.conf
    2. Type this
        - unbind C-b
        - unbind l
        - set -g prefix C-a
        - unbind %
        - bind e split-window -h
        - bind o split-window -v
        - set -g base-index 1
        - setw -g pane-base-index 1
- Save it and exit tmux and open again.

- shortcuts

    1. To split horizontally --> **^A then o**
    2. To split vertically --> **^A then e**
    3. To exit --> **^A then x or just type ‘exit’**
    4. To create tab --> **^A then c**
    5. To rename the tab --> **^A then ,(comma)**
    6. To switch tabs --> **^A then "numbers"**
    7. TO switch partitions --> **^A  then "arrow"**

## Wget

- Is a tool used to download files from websites/servers
- Syntax --> **wget (options) (link)**
- example ---> **wget https://tldp.org/LDP/intro-linux/intro-linux.pdf**

## find

- ON terminal if you want to search for files/folders/musics/videos, we can use find command. 
- It is very essential tool
- Syntax: --> **find (search path) (options) (search word)**
- More commands
    - **find / -name “linux”** ---> find linux name in /(root) path
    - **find /home -perm 777** ---> find a file that have permission 777 in home dirctory 
    - **find -type f** ---> find files in the given path
    - **find -type d** ---> find directory in the given path