<h1 align="center">Installing Sublime Text & MinGW Compiler</h1>

* [Visit here](https://www.sublimetext.com/download) and click on windows to install Sublime Text.<br>
Since it is a text editor, you need a compiler such as `MinGW` to compile your code.
After installing MinGW, copy the path of bin folder to the system variable path. For details
[Watch this](https://www.youtube.com/watch?v=9PAglZlRolo).
<br><br>
Now your compiler is set up. 
But one problem! You can only output, can't take input. For input, we need to setup new Build System. 
<br><br>

<h1 align="center">Setting Up Sublime Text for Taking Input</h1>

<h3 align="center">3 ways to do it.</h3>

<details><summary><h2>First Method</h2></summary>

* When you run the code `Ctrl+Shift+B`, a pop up window will open which take input and show output.<br> Follow the steps below:
    * Open Sublime Text. 
    * Goto Tools -> Build System -> New Build System..
    * Delete the deafult code and paste the following: 
        ```cmd
        {
            "cmd": ["g++.exe", "-std=c++14", "-o", "$file_base_name", "$file", "&&", "start", "cmd", "/c", "$file_base_name & echo. & echo. & pause"],
            "shell": true,
            "selector": "source.c++"
        }
        ```
    * Click `Ctrl+Shift+S` to save the file. You can name it as you wish. But the extension should be `sublime-build`<br>
    Such as: `C++PopUpWindow.sublime-build`
    
    * Goto Tools -> Build System -> C++PopUpWindow. 
    * Write a cpp code & run it. A pop up window will appear. Enter input & output will be shown.
    
    [Watch this](https://youtu.be/5wQSwOxhpnM)

</details>

<details><summary><h2>Second Method</h2></summary>

* I call this a perfect build system for input-output in sublime text.<br>Follow the steps:
    
    * Goto View -> Layout -> Columns:3
    * Goto View -> Groups -> Max Columns:2
    
    Now you can enter input in the top right side, and get output in bottom right side.<br>

    But first we need to create a new Build System.
    * Goto Tools -> Build System -> New Build System.
    * Delete the deafult code and paste the following:
        ```cmd
        {
            "cmd": ["g++.exe","-std=c++17", "${file}", "-o", "${file_base_name}.exe", "&&" , "${file_base_name}.exe<input.txt>output.txt"],
            "selector":"source.cpp",
            "shell":true,
            "working_dir":"$file_path"
        }
        ```
    
    * Click `Ctrl+Shift+S` to save the file. You can name it as you wish. But the extension should be `sublime-build`<br>
    Such as: `C++Perfect.sublime-build`
    
    * Goto Tools -> Build System -> C++Perfect. 
    * Click on the top right input section and create a new file (`Ctrl+N`). Name it `input.txt`
    * Click on bottom right output section and create a new file. Name it `output.txt`
    * These two files should be in the same directory with .cpp file. Meaning, the `.cpp` file, `input.txt`, `output.txt` should be in same folder.
    
    * Enter input in `input.txt` & run your code.<br>
    You should put your cursor in the `.cpp` file to run it.<br>If you put your cursor in `input.txt` or `output.txt` file & run, error will be shown.
    
    [Watch this](https://youtu.be/CACx2wrpF4I)
    
</details>

<details><summary><h2>Third Method</h2></summary>

Now back to the original.<br>When you installed and setup Sublime and Compiler, you could only output by selecting C++ Single File run.<br><br>
Now we want to take input in the same panel rather than pop up window or sideview described above. For that We need to install a package.

<details><summary><h2>Install Terminus</h2></summary>

   * Goto Tools -> Install Package Control. It will be installed.
   * Now click Preferences -> Package Control. Type `Install Package` and click on it. Now type `Terminus`.
   * If installation does not start, close and reopen sublime.

   * Again search `Terminus` following above instructions. 
   You will see installation ongiong in the `status bar`.
   
</details>

Now, you can choose either of the following option:

   <details><summary><h2>Option 1: (Long one)</h2></summary>
   
   * Goto Tools -> `Command Palette`.
   * Delete deafult text and type `vpf`.
   * Click on `View Package File`. Type `sublime-build c`. 
   * Click on `C++/C++ Single File.sublime-build`. Copy the existing code.
   
   * Create New Build System. Delete default code and paste the code that you copied.
   * Add two extra lines below '{' and before existing first line.<br>
        ```cmd
        "target": "terminus_exec",
        "cancel": "terminus_cancel_build", 
        ```
   
   * Save the file and name it `C++Terminus.sublime-build`.
   * Goto Tools -> Build System -> `C++Terminus`. 
   * Write a cpp code & run it.
   * Enter input in the Terminus Console and get output.
   
   </details>
   <details><summary><h2>Option 2: (Easier one)</h2></summary>
   
   * Create a new build system. Delete the default code and paste the following:
        ```cmd
        {
            "target": "terminus_exec",
            "cancel": "terminus_cancel_build",

            "shell_cmd": "g++ \"${file}\" -o \"${file_path}/${file_base_name}\"",
            "file_regex": "^(..[^:]*):([0-9]+):?([0-9]+)?:? (.*)$",
            "working_dir": "${file_path}",
            "selector": "source.c++",

            "variants":
            [
                {
                    "name": "Run",
                    "shell_cmd": "g++ \"${file}\" -o \"${file_path}/${file_base_name}\" && \"${file_path}/${file_base_name}\""
                }
            ]
        }
        ``` 
    
   * Save the file and name it `C++Terminus.sublime-build`.
   * Goto Tools -> Build System -> `C++Terminus`.
   * Write a cpp code & run it.
   * Enter input in the Terminus Console and get output.
   </details>

[Watch this](https://youtu.be/5Usw4MgIc04)

</details>

<br><br>
That's it. I hope your Sublime Text is set up & you can take input-output and run your code smoothly. 
    
Finally, I have created a [playlist](https://www.youtube.com/watch?v=5Usw4MgIc04&list=PL-Nhn-mmszpOwqWDXcV9KndAKQH3HAjBT) including all the necessary videos to set up Sublime Text.

<p align="center"><b>STAY SAFE, STAY HEALTHY.</b></p>