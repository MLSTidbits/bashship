---
title: bashship.conf
section: 1
header: Bashship Configuration File
footer: Bashship
date: 2025-09-14
author:
  - Bashship Contributors
---

# NAME

bashship - configurable bash prompt

bashship.conf - configuration file for bashship

# DESCRIPTION

`bashship` is a highly configurable bash prompt written in bash inspired by spaceship-prompt. It is modular, allowing users to enable or disable various components of the prompt according to their preferences. The configuration file `bashship.conf` in the `~/.config` directory allows users to customize the appearance and behavior of the prompt.

# CONFIGURATION

By default, `bashship` loads the a basic configuration if **user configuration file** is not found at `~/.config/bashship/bashship.conf`. To create a user configuration file, copy the default configuration file from the installation directory to `~/.config/bashship/`:

```bash
touch ~/.config/bashship/bashship.conf
```

The configuration file is a bash script that sets various variables to customize the prompt. Below are some of the key configuration options available in `bashship.conf`:

Below is an example configuration file with explanations for each option. To learn more about each option, please see `/usr/share/bashship/bashship.conf` or the http://github.com/MLSTidbits/bashship repository.

## Configuration Options

### MODULES ORDER

The order in which the prompt components are displayed can be customized using the `PROMPT_ORDER` variable. The available components are: `user`, `host`, `path`, `git-branch`, `git-status`, `time`, `jobs`, and `container`.

### PROMPT SYMBOL

The `PROMPT_SYMBOL` variable defines the symbol used at the end of the prompt. You can customize its appearance using the `SYMBOL_COLOR` and `SYMBOL_COLOR_ERROR` variables.

| Variable               | Description                                          | Common Values               |
|------------------------|------------------------------------------------------|-----------------------------|
| `PROMPT_SYMBOL`        | The symbol used at the end of the prompt             | `>`, `$`, `#`               |
| `SYMBOL_COLOR`         | Color of the user component                          | 256 bit ASCII color codes   |
| `SYMBOL_COLOR_ERROR`   | Color of the user component when last command failed |  |

### CONTAINER

Container environments (like Docker) can be indicated in the prompt using the `CONTAINER` component. You can customize its appearance with the following variables:

| Variable               | Description                                          | Common Values               |
|------------------------|------------------------------------------------------|-----------------------------|
| `CONTAINER_COLOR`      | Color of the container component                     |  |
| `CONTAINER_SYMBOL`     | Symbol indicating a container environment            | `C:`, or an emoji like `🐳` |

### DIRECTORY

Customize the appearance of the directory path in the prompt using the following variables:

| Variable               | Description                                          | Common Values               |
|------------------------|------------------------------------------------------|-----------------------------|
| `DIR_COLOR`            | Color of the directory component                     |  |
| `DIR_TRUNCATE`         | Number of directory levels to show                   | `1`, `2`, `3`, etc.         |
| `DIR_TRUNCATE_SYMBOL`  | Symbol used when truncating directories              | `..`, `»`, etc.             |
| `DIR_HOME_SYMBOL`      | Symbol used to represent the home directory          | `~`, or an emoji like `🏠`  |
| `DIR_READONLY_COLOR`   | Color of the read-only directory indicator           | 256 bit ASCII color codes   |

### GIT

In order to enable Git information in the prompt, ensure that `git` is installed and accessible in your system's PATH. The Git components can be customized using the following variables:

| Variable               | Description                                          | Common Values               |
|------------------------|------------------------------------------------------|-----------------------------|
| `GIT_COLOR`            | Color of the Git open/close symbols                  | 256 bit ASCII color codes   |
| `GIT_SYMBOL`           | Emoji used to represent Git                          | `🌿`, `🌳`, `🔀`, etc.      |
| `GIT_OPEN`             | Symbol used before the Git branch name               | `(`, `[`, `{`, etc.         |
| `GIT_CLOSE`            | Symbol used after the Git branch name                | `)`, `]`, `}`, etc.         |

### GIT STATUS

In order to enable Git status information in the prompt, ensure that `git` is installed and accessible in your system's PATH. The Git status components can be customized using the following variables:

| Variable               | Description                                          | Common Values               |
|------------------------|------------------------------------------------------|-----------------------------|
| `GIT_COLOR`            | Color of the Git open/close symbols                  | 256 bit ASCII color codes   |
| `GIT_CONFLICT`         | Symbol indicating merge conflicts                    | `!`, `⚠️`, etc.             |
| `GIT_UNTRACKED`        | Symbol indicating untracked files                    | `?`, `+`, etc.              |
| `GIT_STAGED`           | Symbol indicating staged changes                     | `*`, `✔️`, etc.             |
| `GIT_MODIFIED`         | Symbol indicating modified files                     | `+`, `~`, etc.              |
| `GIT_DELETED`          | Symbol indicating deleted files                      | `-`, `✖️`, etc.             |
| `GIT_AHEAD`            | Symbol indicating commits ahead of remote            | `^`, `↑`, etc.              |
| `GIT_BEHIND`           | Symbol indicating commits behind remote              | `v`, `↓`, etc.              |
| `GIT_CLEAN`            | Symbol indicating a clean working directory          | `✔️`, `✓`, etc.             |

### HOSTNAME

The hostname portions of the prompt can be customized such as only showing when connected via SSH, changing the color, and modifying the symbol used before the hostname.

| Variable               | Description                                          | Common Values               |
|------------------------|------------------------------------------------------|-----------------------------|
| `HOST_ENABLE`          | Enable or disable user hostname info                 | `true`, `false`             |
| `HOST_COLOR`           | Color of the hostname component                      | 256 bit ASCII color codes   |
| `HOST_SYMBOL`          | Symbol used before the hostname                      | `@`, `in`, etc.             |
| `HOST_SSH`             | Show if connected via SSH                            | `true`, `false`             |
| `HOST_SSH_STYLE`       | Style of SSH indicator                               | `@ssh:`, `🔒`, etc.         |
| `JOBS_COLOR`           | Color of the jobs component                          | 256 bit ASCII color codes   |

### JOBS

The jobs component displays the number of background jobs running in the current shell session. You can customize its appearance using the following variables:

| Variable               | Description                                          | Common Values               |
|------------------------|------------------------------------------------------|-----------------------------|
| `JOBS_SYMBOL`          | Symbol used before the jobs count                    | `⚙`, `⚒`, `J:`              |
| `JOBS_COLOR`           | Color of the jobs component                          | 256 bit ASCII color codes   |

### TIME

The time component displays the current time in the prompt. You can customize its appearance using the following variables:

| Variable               | Description                                          | Common Values               |
|------------------------|------------------------------------------------------|-----------------------------|
| `TIME_COLOR`           | Color of the time component                          | 256 bit ASCII color codes   |
| `TIME_12H`             | Use 12-hour format for time                          | `true`, `false`             |

### USER

The user component displays the current username in the prompt. You can customize its appearance using the following variables:

| Variable               | Description                                          | Common Values               |
|------------------------|------------------------------------------------------|-----------------------------|
| `USER_COLOR`           | Color of the user component                          | 256 bit ASCII color codes   |
| `USER_COLOR_ROOT`      | Color of the user component when root                |  |
| `USER_COLOR_BG`        | Background color of the user component               |  |
| `USER_COLOR_BG_ROOT`   | Background color of the user component when root     |  |

# SEE ALSO

bash(1), sh(1), dash(1), zsh(1), fish(1)

# COPYRIGHT

Copyright (c) 2025 MLS Tidbits <contact@mlstidbits.com> all rights reserved.
