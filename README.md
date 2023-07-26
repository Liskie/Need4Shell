# Need4Shell

The only configuration guide you need for shell.

## Steps

1. Install Oh-My-Zsh

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


---

If you find this repository useful, please give us a **star**. Thank you!