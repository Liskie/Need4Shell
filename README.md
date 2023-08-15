# Need4Shell

The only configuration guide you need for shell.

![GitHub Repo stars](https://img.shields.io/github/stars/Liskie/Need4Shell)
![GitHub watchers](https://img.shields.io/github/watchers/Liskie/Need4Shell)
![GitHub forks](https://img.shields.io/github/forks/Liskie/Need4Shell)

## Steps

1. Install Oh-My-Zsh<a name="install-oh-my-zsh"></a>

    ```shell
    sh -c "$(wget https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh -O -)"
    ```
   

2. Install Starship
   
    Starship can be installed on Linux and macOS with one simple command:
    ```shell
    curl -k -sS https://starship.rs/install.sh | sh
    ```
    Note: Curl's verification of certificate is turned off in this command.
    
    This command will place the Starship binary in `/usr/local/bin` by default. If you'd like to place the binary somewhere else, specify the `--bin-dir` option:
    ```shell
    wget https://starship.rs/install.sh
    sh ./install.sh --bin-dir "your custom bin directory"
    ```
    Also, remember to add the custom bin directory to your `$PATH` variable.

3. Configure Starship
   
    By default, you need to create `~/.config/starship.toml` first and put in any config you want with:
    
    ```shell
    vim ~/.config/starship.toml
    ```
    
    Alternatively, you can just copy the `starship.toml` in this repository to `~/.config/starship.toml`:
    ```shell  
    cp starship.toml ~/.config/starship.toml
    ```
    If you are using our config file, please make sure you have installed **any Nerd font** in your system. If not, you can download one from [here](https://www.nerdfonts.com/font-downloads).
    
    Here is a preview of shell prompt with our configuration file:
    ![Prompt Preview](prompt_preview.png)
    
    If you use conda, you may want to disable the default conda prompt change. To do so, just run: 
    ```shell
    conda config --set changeps1 False
    ```
   
4. Configure zsh plugins
   
    We use a selected minimal set of plugins for zsh. You may edit the zsh config file:
    ```shell
    vim ~/.zshrc
    ```
    and replace the default plugins `plugins=(git)` with the following:
    ```shell
    plugins=(
        git
        extract
        cp
        zsh-autosuggestions
        zsh-syntax-highlighting
        sudo
        tmux
        autojump
    )
    ```
    Some of the plugins are not installed by default. You may want to install them first:
    
    For `autojump`:
    
    Install it with `sudo apt install autojump` on Ubuntu or `brew install autojump` on macOS.
    
    For `zsh-autosuggestions`:
    
    ```shell
    git clone git@github.com:zsh-users/zsh-autosuggestions.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
    ```
    
    For `zsh-syntax-highlighting`:
    
    ```shell
    git clone git@github.com:zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
    ```

5. Restart your shell

    After all these changes, you may need to restart your shell to see the changes.

## Others

- We provide a [Monokai Pro based color scheme](Monokai_Pro_Material.icls) for JetBrains IDEs in this repository.

- If you develop with Python, you may want to optimize your traceback output with _Rich_ globally. 
    To do so, you should first make sure **conda** is installed, and run:

    ```shell
    conda activate "your env name"
    pip install rich
    ```
    
    Next, according to the [Official Documentation of Rich](https://rich.readthedocs.io/en/stable/traceback.html), you need to modify the `sitecustomize.py` file.
    Usually this file is located in your virtual env directory, for example, `~/anaconda3/envs/base/lib/python3.11/site-packages/sitecustomize.py`.
    If you are not sure about where it is, run:
    
    ```shell
    python -c "from distutils.sysconfig import get_python_lib;print(get_python_lib())"
    ```
    
    This prints the path of the `site-packages` directory, and you may find the `sitecustomize.py` file in it. If the file does not exist, just create one.   
    Once you find the `sitecustomize.py` file, you need to add the following code to it:
    
    ```python
    try:
       from rich import traceback
       traceback.install(show_locals=True, width=10000)
    except ImportError:
       pass
    ```
    
    It's done! Now you can enjoy the beautiful traceback output with _Rich_. 
    But notice that these configurations are env-specific, so you need to repeat these steps for every virtual env you have.

## Troubleshooting

1. Zsh is not installed.

    When you install Oh-My-Zsh with the command provided in [Install Oh-My-Zsh](#install-oh-my-zsh), 
    you may find the following error:
    
    ```shell
    Zsh is not installed. Please install zsh first.
    ```

    Which means you should first install zsh with: Which means you should first install zsh with:
    
    ```shell
    sudo apt install zsh # On ubuntu
    ```
    
    or:
    
    ```shell
    brew install zsh # On macOS
    ```
    
    Then you can run [the command](#install-oh-my-zsh) again to install Oh-My-Zsh.
       
    



---

If you find this repository useful, please give us a **star**. Thank you!