[ ![Image](https://cloud.githubusercontent.com/assets/5514990/21614528/5c56d772-d20c-11e6-8670-577f2dd7ca9b.png "Ansible") ](https://www.ansible.com/ "Ansible")

[![Build Status](https://travis-ci.org/ansyble/role-oh-my-zsh.svg?branch=master)](https://travis-ci.org/ansyble/role-oh-my-zsh)
[![Ansible Role](https://img.shields.io/ansible/role/16910.svg)](https://galaxy.ansible.com/ansyble/oh-my-zsh/)

[Ansible](http://www.ansible.com/home) role to deploy [oh-my-zsh](https://github.com/robbyrussell/oh-my-zsh).

### Install

```sh
ansible-galaxy install ansyble.oh-my-zsh
```

### Usage

```yml
oh_my_zsh_users:
  - name: root

  - name: mongkok
    theme: pyzsh
    plugins: git
```

**Plugins**
```yml
oh_my_zsh_plugins:
  custom_virtualenv: |
    function virtualenv_prompt_info(){
      if [[ -n $VIRTUAL_ENV ]]; then
        printf "%s(%s) " "%{${fg_bold[cyan]}%}" ${${VIRTUAL_ENV}:t}
      fi
    }

    export VIRTUAL_ENV_DISABLE_PROMPT=1
```

**Themes**
```yml
oh_my_zsh_themes:
  pyzsh: |
    local ret_status="%(?:%{$fg_bold[green]%}➜ :%{$fg_bold[red]%}➜ )"
    PROMPT=${PYZSH_PROMPT:-'${ret_status} %{$fg[cyan]%}%c%{$reset_color%} $(git_prompt_info)'}

    ZSH_THEME_GIT_PROMPT_PREFIX="%{$fg_bold[blue]%}git:(%{$fg[red]%}"
    ZSH_THEME_GIT_PROMPT_SUFFIX="%{$reset_color%} "
    ZSH_THEME_GIT_PROMPT_DIRTY="%{$fg[blue]%}) %{$fg[yellow]%}✗"
    ZSH_THEME_GIT_PROMPT_CLEAN="%{$fg[blue]%})"
```
