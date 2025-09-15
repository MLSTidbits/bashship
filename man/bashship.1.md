---
title: bashship.conf
section: 1
header: Bashship Configuration File
footer: Bashship
date: 2025-09-14
author: Michael L. Schaecher
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

---

## PROMPT_ORDER

This array defines the order of modules to be displayed in the prompt. Users can add or remove modules as needed. Available modules include `user`, `host`, `path`, `git-branch`, `git-status`, `time`, and more.

The color values correspond to ANSI color codes. To learn more about ANSI colors, refer to [ANSI escape code - Wikipedia](https://en.wikipedia.org/wiki/ANSI_escape_code#8-bit).

```bash
PROMPT_ORDER=( "user" "host" "path" "time" "jobs" )
```

## NEWLINE and NEXTLINE

These options control whether a newline is added before the prompt and whether the prompt symbol appears on a new line.

```bash
NEWLINE="false"
NEXTLINE="true"
```

## SYMBOL and SYMBOL COLORS

These variables define the prompt symbol and its color. Different symbols and colors can be set for normal users and root users.

```bash
SYMBOL="$"
SYMBOL_ROOT="$SYMBOL"
SYMBOL_COLOR="15"
SYMBOL_COLOR_ERROR="1"
```

## PATH MODULE CONFIGURATION

These options customize the appearance of the path module, including colors, truncation settings, and symbols for home and read-only directories.

```bash
DIR_COLOR="4"
DIR_TRUNCATE="0"
DIR_TRUNCATE_SYMBOL=" "
DIR_HOME_SYMBOL="~"
DIR_READONLY_COLOR="1"
DIR_READONLY_SYMBOL=" ! "
```

## GIT MODULE CONFIGURATION

These options configure the appearance of the git branch and status modules, including colors and symbols for various git states.

```bash
GIT_ENABLE="true"
GIT_BRANCH_COLOR="13"
GIT_BRANCH_SYMBOL=""
GIT_BRANCH_OPEN=" ( "
GIT_BRANCH_CLOSE=" ) "
```

## GIT STATUS SYMBOLS

These variables define the symbols used to represent different git statuses, such as added, modified, deleted files, and more.

```bash
GIT_STATUS_ENABLE="true"
GIT_CONFLICT="!"
GIT_UNTRACKED="?"
GIT_STAGED="*"
GIT_MODIFIED="+"
GIT_DELETED="-"
GIT_AHEAD="^"
GIT_CLEAN=""
```

## HOST MODULE CONFIGURATION

These options customize the appearance of the host module, including colors and symbols for SSH connections.

```bash
HOST_COLOR="2"
HOST_SSH_STYLE="@ssh:"
HOST_SSH="true"
HOST_ENABLE="true"
```

## USER MODULE CONFIGURATION

These options configure the appearance of the user module, including colors and symbols for root users.

```bash
USER_COLOR="2"
USER_ROOT_COLOR="13"
USER_COLOR_BG="0"
USER_ROOT_COLOR_BG="15"

# COPYRIGHT

Copyright (c) 2025 Michael Schaecher <michaelschaecher@mlstidbits.com> all rights reserved.
