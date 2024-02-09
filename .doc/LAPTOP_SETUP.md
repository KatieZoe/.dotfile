# LAPTOP SETUP

1. start the machine
    1. choose all sain settings for your locale
    1. log into **iCould account** even for work laptop
       > this will allow you to save documents and notes to the
       > cloud which may be helpful for transferring to another
       > machine, a backup, accessing from a phone or the web,
       > finding your device, etc.

1. **System Update**
    1. once fully booted
    1. run a system update `System Preferences -> Software Updates`
       > every new machine is likely to be behind on software
       > updates

1. install command line tools
   ```
   xcode-select --install
   ```

1. **using existing .dotfiles**
   ```
   git clone --bare git@github.com:KatieZoe/.dotfile.git $HOME/.dotfiles
   # based on which git
   alias config='/usr/bin/git --git-dir=$HOME/.dotfiles/ --work-tree=$HOME'
   config status
   config config --local status.showUntrackedFiles no
   ```

1. **Git**
    1. review your `~/.gitconfig` file using, below, it should be already setup
       ```
       git config --global --edit
       ```
    1. or use the following to set it up
      1. use the default git that comes with mac
      1. create or bring across your ssh key and make sure it's in gitlab
         [Preferences -> User Settings -> SSH
         Keys](https://gitlab.com/-/profile/keys) as per instructions in
         https://docs.gitlab.com/ee/ssh/#rsa-ssh-keys
         ```
         # NEW
         # based on
         #  https://www.keystash.io/guides/how-to-generate-the-best-ssh-keys.html
         ssh-keygen -o -a 100 -t ed25519
         # OLD
         ssh-keygen -t rsa -b 2048 -C "my UNIQUE NAME key"
         ```
      1. setup sane git defaults
         ```
         git config --global pull.rebase true
         git config --global user.name "KatieZoe"
         git config --global user.email 80615590+KatieZoe@users.noreply.github.com
         git config --global core.editor "code --wait"
         git config --global --replace-all core.pager "less -F -X"
         git config --global init.defaultBranch main
         git config --global commit.template ~/.gitmessage.txt
         ```
      1. setup `~/.gitmessage.txt` file with current pairs (NOTE: this can also
         be done per directory tree or repository)
         ```sh
         cat <<EOF > ~/.gitmessage.txt


         # Co-authored-by: Pair Name <pair-email-address-as-per-github>
         EOF
         ```

      1. review your `~/.gitconfig` file using
         ```
         git config --global --edit
         ```
