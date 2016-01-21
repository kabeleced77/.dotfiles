.dotfiles
=========

Provides basic dotfiles for

- ``bash``
- ``vim``
- ``tmux``
- ``top``
- ``git``

Requirements:
-------------
- ``git`` client to check this repository out
- ``rcm`` (https://github.com/thoughtbot/rcm) for dotfile management
  --> creates links of the dotfiles to the checked out repository
- ``cmake`` to build a ``tmux`` cpu-stats plugin

Installation
------------
- clone this repository to your home: ``~/.dotfiles``

  ```
  git clone https://github.com/kabeleced77/.dotfiles.git ~/.dotfiles
  ```

  ATTENTION: This name and location of the cloned repository is required as the pre-up hook for ``rcup`` is using it via a magic string (hard coded).

- run ``rcup`` to create all the links to the dotfiles and directories of this repository
  + dryrun with ``lsrc`` to see what would be created or might be overridden!

    ATTENTION: Dryrun for the first time does not use the pre-up hooks and therfore the ``rcm`` configuration file ``~/.rcrc`` is not used.
      --> will be created by the pre-up hook when rcup is run.
  + run ``rcup`` to create dotfiles based on this repository

- load submodules of this repository


  ```
  cd ~/.dotfiles

  git submodule init

  git submodule update
  ```

- ``tmux`` is configured through submodule ``tmux-conifg`` which itself has also a submodule which can be loaded

  HINT: Only required once per system as it is installed system wide.

  ```
  cd ~/.dotfiles/gitsubmodules/tmux-config

  git submodule init

  git submodule update

  cd vendor/tmux-mem-cpu-load

  cmake .

  make

  sudo make install
  ```

  run ``tmux`` and enjoy

- ``vim`` configuration
  + run ``~/.vim/sync-bundles.sh`` to prepare ``vim`` using ``vundle`` - could take a while

    HINT: Errors regarding missing of misconfigured ``vim`` plugins can be ignored here as they will be installed/configured in this step.

    ```
    cd ~/.vim

    ./sync-bundles.sh
    ```
