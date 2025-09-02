---
layout: post
title: "Tooling"
date: 2023-11-28
---
# Tooling Meeting WriteUp (23/11/28):

## Art of Development:

### Luigi and the Luigi Analysis Workflow (Law)

* What:
  * Python-based workflow management system
  * Design your analysis in single tasks, build trees
* Why:
  * Better code structure
  * Increased reproducibility
  * Awesome plugins (CMD, Dropbox, Telegram, …)
* How:
  * Each task becomes python class:
    * class Task(law.Task):
      * def requires(self): … (Input)
      * def output(self): … (Output)
      * def run(self): … (Workload)
  * Try it out @ [binder](https://mybinder.org/v2/gh/riga/law/master?filepath=examples%2Floremipsum%2Findex.ipynb)


Luigi is an open-source Python module used to build complex pipelines in data processing.
It's a framework that helps in managing dependencies between tasks, scheduling jobs, and orchestrating workflows in a structured and efficient manner.
It has originally been developed by Spotify but is now an independent open source project.
Law is a python package which extends luigi according to the need of modern scientific data analysis.

Luigi/LAW allows developers to define tasks, their dependencies, and their execution logic. These tasks can range from simple processes like file copying to more intricate data analysis and transformation steps. Its visual representation is similar to a directed acyclic graph (DAG), where nodes represent tasks, and edges depict dependencies between these tasks.

Users can create pipelines by defining tasks and their relationships, enabling parallel execution and automatic handling of dependencies. This makes it easier to manage and execute data pipelines, ensuring reliability and repeatability in data processing workflows.

Overall, Luigi/Law simplifies the creation and management of data pipelines, making it easier for developers to handle complex data workflows efficiently.


### homebrew hep

* What:
  * homebrew-hep: assorted homebrew packages for pheno projects
* Why:
  * Useful packages for pheno projects
* How:
  * homebrew-hep: https://davidchall.github.io/homebrew-hep/formula/

Homebrew-hep is a collection of software packages tailored to the needs of the HEP community, aiming to streamline the installation and management of various tools and libraries used in this field.

Similar to how Homebrew simplifies software installation on macOS, homebrew-hep provides a convenient way for physicists and researchers in the high-energy physics domain to access, install, and update specialized software packages. These packages might include analysis tools, simulation software, data processing libraries, and frameworks crucial for conducting experiments and performing computations in particle physics and related disciplines.

Homebrew-hep typically curates and manages a repository of HEP-specific software, allowing users to easily install and maintain these tools on their systems. By offering a centralized and standardized approach to software management, it aims to reduce the complexity and time required for physicists to set up their computing environments, enabling them to focus more on their research and data analysis tasks.

### Python function acceleration & vectorization
* What:
    * Translates Python functions to optimized machine code
    * Vectorization of python loops, math operations
* Why:
    * MUCH FASTER PYTHON CODE (C-level performance)
* How: Numba, CuPy

The discussion focused on optimization tools such as NumPy, Numba, Jax, and Cython, emphasizing their capability to enhance simple math calculations through parallel and multi-threaded operations. Participants noted that utilizing packages like Numba could result in significant speed boosts, sometimes up to 10 times faster, compared to standard calculations. It was highlighted that Numba is akin to Jax and NumPy in terms of functionality, enabling operations similar to NumPy with comparable or even superior performance.
Participants explored the differences between Numba and Jax, particularly their underlying compilers—Numba utilizing LLVM and Jax employing JaxLN. There was curiosity about how these different compilers impact code translation into C and subsequent performance. Cython was also brought into the conversation, described as a tool to convert Python code into C for enhanced performance. Some participants shared their method of writing C code and compiling it using CPPYY to integrate C functions into Python, leveraging the performance benefits of C within their Python workflow.

### Ruff:
* What:
  * An extremely fast Python linter and code formatter
* Why:
  * Linter: static code analysis tool used to flag programming errors, bugs, stylistic errors, etc
  * Replace Flake8, Black, isort, pydocstyle, pyupgrade, autoflake, and more, all while executing many times faster than any individual tool
* How:
  * [Github](https://github.com/astral-sh/ruff)
  * pip install ruff

The discussion centered on the Ruff library (also known as Kade), recommended as a pre-compiler check for Python code. Participants highlighted its usefulness in identifying simple mistakes like variable definitions, indentation errors, or other common Python coding errors before actual execution or compilation. They noted its straightforward command-line interface (accessible via 'pip install ruff' and 'ruff check'), allowing users to specify directories or files to review. The tool provides output indicating potential mistakes and related suggestions to improve code readability and catch bugs early on. Notably, Ruff consolidates functionalities from existing libraries like Flake while significantly boosting productivity due to its speed. It was mentioned that Ruff is written in Rust, contributing to its efficiency.

### multiprocessing
* What:
  * multiprocessing: Python package for easy process-based parallelism
* Why:
  * Easy speed up of Python code
* How:
  * multiprocessing: https://docs.python.org/3/library/multiprocessing.html 

## Craft of Research:

### Python debugging:
* What:
  * Debug your code interactively in python, ipython, jupyter notebook (lab)
* Tools
  * Built-in python debugger pdb
  * Notebook pdb magic
  * IPython pdb
    * With nice code listing, pretty printing of variables
    * Tab completion, syntax highlighting, better tracebacks

The discussion emphasized debugging techniques in Python, particularly using the Python Debugger (PDB) and its functionalities. Participants highlighted the effectiveness of placing a 'PDB.set_trace()' phrase in code to initiate a terminal where one can inspect variables, trace errors, and execute commands just before encountering an error. It was noted that within Jupyter Notebooks, '%pdb' magic automatically triggers traceback upon encountering an error, streamlining the debugging process.
Additionally, an extension to the default Python debugger was mentioned, offering more flexibility in terminal outputs during debugging sessions. Participants stressed the importance of such debugging tricks for both Python and C++ coding.
Furthermore, IPython's 'embed' feature was introduced as a powerful tool beyond mere debugging, enabling the opening of an IPython shell within Python code. This functionality allows users to experiment with commands and variables, enhancing code exploration and analysis. While not covered in-depth, it was mentioned that IPython has several other useful 'magic' tricks, encouraging exploration of these features for enhanced productivity and problem-solving in Python.
Let me know when you're ready with the next part!

### TMUX:
* What:
  * Command line manager
  * Hop between “terminals” with different tasks without maintaining multiple terminal windows open
* Why:
  * If your connection drops, the session stays active
  * Easier to organize multiple simultaneous projects
* How:
  * https://www.hamvocke.com/blog/a-quick-and-easy-guide-to-tmux/


The conversation revolved around Tmux, a terminal multiplexer, and its benefits for managing terminal sessions. Participants highlighted scenarios where sudden disconnections during critical tasks or dealing with multiple terminal tabs led to frustrations before adopting Tmux. Tmux was praised for its ability to create sessions within one's laptop, providing advantages like organizing different workspaces for various projects or tasks. It was mentioned that Tmux facilitates multiple tabs and split screens within sessions, allowing for efficient code editing and prototyping while keeping the work environment well-structured. Its capability to easily reconnect to sessions after disconnection was particularly highlighted as valuable, especially during remote work in places with intermittent internet access.
There was also a brief query regarding the comparison between Tmux and Screen, where participants shared their preferences based on familiarity and keyboard shortcut convenience. Some expressed a preference for Screen due to its initial usage and adapted keyboard shortcuts, while others found Tmux more user-friendly and modified their Screen commands to alleviate conflicts with existing shortcuts. The discussion hinted at an upcoming slide on Screen, acknowledging its existence and potentially exploring its functionalities.

### bashrc:
* alias work="cd /clusterfs/ml4hep/mpettee"
* alias emacs="emacs -nw"
* alias nv='watch -n0.1 nvidia-smi'      # continuously-updating nvidia-smi

Participants shared their favorite customizations within their Bash RC or Bash profile. This included shortcuts for navigating directories, configuring commands like 'emacs' to prevent GUI windows from opening, and utilizing commands like 'Nvidia SMI' to monitor GPU usage continuously. There was a discussion about using 'screen' to manage different screens for each GPU, with preferences varying among participants based on familiarity.
Several helpful Bash profile modifications were suggested, such as customizing the output length when navigating directories, changing cursor colors, and defining functions within the profile to streamline environment setups for specific projects. Functions were particularly highlighted for simplifying the setup of parameters and environment configurations for various projects, aiding in avoiding repetitive steps and ensuring consistency across multiple environments.
The conversation briefly touched on the choice of shell, with some mentioning using Zsh but noting that it might not be supported on certain remote servers like NERSC, making Bash the more practical choice in those instances.

### Jupyter notebook extensions (esp. gist)
* What:
  * Add-ons to Jupyter
  * My favorite is a Gist plugin that allows you to directly export a Gist
* Why:
  * Makes it easy to quickly share a notebook without sending the .ipynb or creating an entire Github repo 
* How:
  * https://medium.com/deena-does-data-science/jupyter-notebook-extensions-e6b57d004e8e


The conversation revolved around the use of Jupyter Notebook extensions, accessible via a simple installation using 'pip install' to enable additional functionalities. Participants highlighted the convenience of this approach, providing a list of available extensions that can be easily enabled within Jupyter Notebooks.
Among various extensions, a favorite was discussed—connecting Jupyter to Gist, which simplifies sharing Jupyter Notebooks. Gist, described as a single-file repository on GitHub, allows users to quickly share a notebook by creating a Gist containing the entire notebook with a simple button press. The resulting link to the Gist enables others to view or edit the notebook online, streamlining the sharing process without the need for multiple downloads or GitHub repositories.
Queries arose regarding the organization of Gists, to which the participant mentioned a lack of organization or folder structure within their Gists. Version control and organization were not prioritized within Gists, with serious version control reserved for GitHub repositories when necessary.

### wandb:
* What:
  * Tracks all your ML runs in a single, beautiful website
* Why:
  * You can check on how your runs are doing without opening up your terminal 
  * You can save all your hyperparameters for each run & do hyperparameter optimization
* How:
  * https://wandb.ai/site/

Code:
```python
import wandb
from wandb.keras import WandbMetricsLogger

# Initialize a new W&B run
wandb.init(config={"bs": 12})

# Pass the WandbMetricsLogger to model.fit
model.fit(
    X_train, y_train, validation_data=(X_test, y_test), callbacks=[WandbMetricsLogger()]
)
```
The conversation highlighted the utility of Weights and Biases (W&B) as a tool for managing machine learning runs and experiments. Initially perceived as a hyperparameter optimization tool, it evolved into a means of tracking various machine learning runs, especially for longer processes. Participants appreciated its lightweight integration into workflows, achieved by adding a callback for W&B metrics during model training. This allowed remote monitoring of runs via a browser, even after closing the terminal or laptop, providing an overview of ongoing experiments.
W&B was praised for its ability to compare hyperparameters and track system metrics like GPU utilization, power, and others beyond validation metrics. While primarily used for machine learning trainings, its flexibility for custom logging or other applications beyond ML was uncertain among the participants.
Queries arose regarding storage limitations due to the accumulation of artifacts, which led to discussions about managing storage quotas on systems like Perlmutter. Participants suggested utilizing scratch space or customizing artifact saving locations to address storage limitations. Concerns were raised about the volume of saved artifacts, prompting considerations for optimizing storage usage within W&B.

### Custom Jupyter kernels:
* What:
  * Custom kernel perlmutter
* Why:
  * If you want to make a custom ipykernel with custom packages
* How:
  * Create conda env and make a shell script pointing to the conda env
  * https://docs.nersc.gov/services/jupyter/how-to-guides/


The conversation centered on the process of creating a custom kernel within the Jupyter Notebook environment on Perlmutter, primarily for users looking to install specific packages or configurations beyond default options. Participants highlighted the ability to craft a personalized kernel environment by installing custom packages, Root, alternate Huda or TensorFlow versions, or any required software. This process involved creating a helper script to link the custom kernel environment within Jupyter Notebook.
Gupp shared personal experiences and showcased a simplified method for custom kernel creation, emphasizing the usefulness for installations requiring unique configurations or specialized software. Although a detailed guide by NERSC existed, Gupp mentioned the possibility of missing information within the guide, encouraging further exploration and discussion among users facing similar issues.
The advantages of the custom kernel were discussed, including its appearance as an option when starting new Jupyter Notebooks or Jupyter Lab sessions. Participants acknowledged the flexibility and utility of custom kernels, highlighting their potential for executing remote tasks or submitting jobs to systems like HD Condor.

### NeoVIM
It seems like Fernando shared thoughts on NeoVim, highlighting its benefits such as being command-line based, offering Vim key bindings, and having compatibility with tools like Tmux. He also mentioned Evil Mode, which combines elements of Vim and Emacs, adopting Vim key bindings within Emacs, known for its keyboard-oriented navigation and editing approach.
Regarding the poll, Fernando initiated a survey in the room about Emacs versus Vim preferences, though it appears that the majority of participants don't use either Emacs or Vim exclusively. It seems there's a diverse array of preferences among the group, with some using alternatives like VS Code or NeoVim.

System and networking.

### Screen
  * Using “screen” to open sessions for each GPU. e.g. 
  * screen -S gpu3

### rscreen:
What:
Simple bash function
Open ssh connection and jump into screen
Why:
Very easy way to work on remote machines
Use same session every time
How 1:
Put in .bashrc
# Directly ssh jump to screen session
```bash
rscreen() {
    ssh $1 -Yt screen -D -RR $2
}
```

How 2:
Enjoy with beautiful .screenrc (remote)

```bash
#.screenrc
dnoll@ml4hep2 ~ 12:47:00 ➤ cat .screenrc 
shell -$SHELL
shelltitle "> |bash"

hardstatus on
hardstatus string "%h > %t"
caption always "%{= wk} %-w%{= kW} %n %t %{-}%+w %= | %l"

screen -t htop 0 nice htop -u $USER
screen 1
screen 2
select 1
        
autodetach on
startup_message off
defscrollback 1000000
        
bindkey "^[[1;2C" next
bindkey "^[[1;2D" prev
bindkey "^[[1;3C" bumpright
bindkey "^[[1;3D" bumplef
```

RScreen, written by a former colleague from Dennis, Benjamin Fischer, was described as a simple yet highly effective one-line Bash function. This function combines SSH connection with direct access to a Screen session on a remote machine, simplifying remote work by swiftly jumping into specific project sessions. By incorporating this function into the BashRC or custom function loading, users can utilize it by typing 'R-Screen' followed by the SSH host and project name, swiftly accessing desired remote sessions.
Participants highlighted the usefulness of R-Screen in conjunction with customized ScreenRC configurations, enabling the automatic opening of multiple sessions, including terminals for commands, an H-top session, and potentially incorporating commands like 'watch NVIDIA SMI' for a comprehensive command center on the remote machine.
Queries arose about the necessity to specify the same login node for the Screen sessions, similar to the requirements of Tmux or S-Screen, and potential methods to streamline access across different nodes.
Following this discussion, the conversation briefly touched on using SSH jump to navigate to specific login nodes before accessing the desired Screen session on remote machines.

### Rectangle:
* What:
  * Window manager for MacOS
* Why:
  * SplitView isn’t always enough
  * Supports multiple monitor aspect ratios (16:10, 21:9, 9:16)
  * Easily customizable
* How:
  * https://rectangleapp.com
  * brew install rectangle
  * Choose snap area actions

Rectangle was introduced as a window manager specifically designed for macOS, catering to users who prefer more control over window arrangements beyond the built-in macOS options. Its utility becomes evident, especially when dealing with multiple monitors or different orientations, as the native macOS functions might become tedious in such scenarios.
The tool offers a user-friendly interface with convenient keyboard shortcuts and the ability to snap and arrange windows efficiently, a feature not always available in all window managers. It's praised for its ease of installation, accessible either through their website or via Homebrew, with a free open-source version and additional paid versions with extra features, although the specifics of these extra features weren't discussed extensively.
Participants discussed the possibility of creating shortcuts to position windows in specific regions. While the free version doesn't permit custom region creation, it does offer a variety of pre-selected regions with assignable shortcuts. Additionally, there's a mention of an extensive list of terminal commands available on the project's GitHub, providing options for defining custom regions by leveraging these commands.

## Productivity and organization

### Zotero:
* What:
  * Library tool to collect, organize, annotate, cite literature (ZoteroBib)
* Why:
  * Easy way to organize & sync literature on any device
  * Collaborate on library & paper
* How:
  * Support Chrome plugin


Zotero, a paper organization tool, caught attention due to its user-friendly features. Participants highlighted its Chrome plugin, allowing users to easily save papers directly to specified collections. Moreover, Zotero supports collaborative library building, allowing users to collaborate on paper and library construction, and facilitates syncing across multiple devices, including iPads, iPhones, and computers.
Questions arose about Zotero's compatibility with Overleaf. While some haven't experimented with this integration, there was curiosity about how well Zotero works with LaTeX and if it automatically syncs bibliographies (bib files) with Overleaf. Users mentioned Zotero's ability to export bibliographies to bib files and its auto-export feature for bib files in local directories, but it's uncertain if this directly uploads to remote spaces like Overleaf.
The discussion extended to managing bib files locally, with some users utilizing Zotero's ability to export to bib files and syncing them to Overleaf via Git. However, there were mentions of potential syncing issues when using Overleaf directly. Additionally, Dropbox integration in Overleaf was praised for its automatic syncing, allowing for smoother paper writing without much hassle in managing pushes and pulls.
Furthermore, a note about Overleaf Git integration not supporting Large File Support (LFS) emerged, suggesting alternative methods for handling projects requiring LFS.

### Safari Web Apps

* What:
  * Save frequent web apps as standalone apps
  * Jupyter, Overleaf, Google Slides on the dock
* Why:
  * Switching native apps instead of tabs in a browser
  * Easier to switch, less distractions
  * Better implementation than Electron/Fluid
* How:
  * Go to website (jupyter page for example)
  * “Share” → Save to dock

Fernando discussed using Safari web apps as a way to convert specific URLs into native-style applications on macOS. He finds this method helpful for organizing his workflow, separating different tasks into their respective web apps. This approach minimizes distractions and enhances productivity.
The Safari web apps feature allows users to export web pages into native applications. These apps appear in the dock and the command switcher, providing a cleaner interface compared to keeping multiple tabs open in a browser.
Fernando demonstrated how simple it is to create these web apps. By clicking the share icon in Safari, users can export a specific URL to create a web app.
He shared an image of his dock, showcasing various web apps he uses, including Perlmutter Jupiter notebooks, Overleaf, and MLPerhub. Each of these web apps serves a specific purpose, allowing for a more organized and focused workflow.
Overall, this approach seems to enhance productivity and streamline task management by converting specific web pages into standalone native applications.
Okay very nice any more questions for this slide?
There's also an option to create home screen icons for specific web pages on an iPhone, providing a similar convenience and accessibility as the macOS web apps feature.
It appears that some participants may need to update their operating systems to access this functionality in Safari. Overall, this feature seems beneficial for customizing the workspace and optimizing task management by creating separate applications for different web-based tools and platforms.

### Pomodoro Technique:
* What:
  * Automatic timer for Pomodoro sessions (25 minute work sprints)
* Why:
  * The Pomodoro technique is great for tackling big projects in doable chunks
  * Short breaks built into your day for stretching/tea/snacks
  * You get metrics tracking how much work you’ve done on different projects over the year
* How:
  * https://pomofocus.io/ (I also use the desktop app) 


Marielle highlighted the Pomodoro Technique as a key to her productivity. The method involves working in focused 25-minute sprints, followed by five-minute breaks. This approach encourages a flow state during the work session and offers a manageable timeframe for completing tasks, even if they're challenging or unpleasant.
The Pomodoro Technique involves committing to a focused session by eliminating distractions (using "do not disturb") and choosing a specific task to tackle during the 25-minute sprint. Marielle also enjoys the social aspect of this technique, as it can be a shared experience when working with others, creating a collegial environment.
Additionally, Marielle mentioned using the Pomofocus app, a tool that provides metrics tracking work time on different projects. This app allows users to outline tasks for the day, estimate how many Pomodoros they'll need for each task, and then track their time spent on various projects over weeks or months.
Participants inquired about the effectiveness of the 25-minute time frame and the quality of focus during these sessions. Marielle suggested that committing to the timed session and ensuring a distraction-free environment, combined with selecting a specific task, helps in achieving a focused work session.
Overall, the Pomodoro Technique, with its structured work and break intervals, seems to be an effective method for Marielle's productivity and focused work time.

### General Productivity Tips
In the final segment, one presenter shared a slide featuring productivity tips. They highlighted habits that contributed to their productivity, such as starting the day outdoors with a hot beverage and consistently carrying a physical notebook for note-taking during meetings. They also emphasized using a paper-based task list and adopting various life maintenance practices like exercise. The presenter discussed a recent approach involving the Reminders app, where they organize research tasks by month. This method helps visualize progress and manage research tasks effectively by segregating them into monthly lists, enabling better tracking of accomplishments and sorting tasks by categories within a month.
Following this, a participant shared a contrasting method of task management where they immediately write a reminder upon task completion and later create a task in Google Tasks, providing a journal-like record of completed work.