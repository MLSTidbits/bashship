<div align="center">
 <image
  src="images/screenshot.png"
  alt="HealthGPT Logo"
  width=auto
  height="480">
  <h1><b>BASHSHIP</b></h1>
  <p>A minimal, fast, and customizable Bash prompt.</p>
</div>

## Introduction

Bashship is a minimal, fast, and highly customizable prompt for Bash. It is designed to be easy to install and configure, while providing useful information at a glance. Inspired by the popular [Starship](https://starship.rs/) prompt, Bashship aims to bring similar functionality built on pure Bash.

### Why Style Prompts Natively?

While on most systems a third-party prompt is not likely to cause performance issues, there are scenarios where a native Bash prompt can be beneficial. One such scenario is when working in constrained environments, such as Docker, Podman or LXC where resources are limited. In these cases, a lightweight prompt can help reduce overhead and improve performance.

The biggest issue with third-party prompts especially with posix shells like Bash and Zsh command history is often funky requiring some manual intervention to fix. This is especially true when the prompt is slow or buggy causing commands to be lost or duplicated. A native prompt can help avoid these issues by being more reliable and consistent.

Additionally, a native prompt can be more secure as it does not require executing external binaries which may be compromised or contain vulnerabilities.

One of the main goals of Bashship is to be fast and lightweight, this is done be minimizing the number of external dependencies and limiting the amount of work done in the prompt. Even **Starship** would move slowly if doe to excessive git status checks in large repositories and loading of multiple modules.

## Features

- **Minimal and Fast**: Designed to be lightweight and efficient, ensuring quick load times.
- **Highly Customizable**: Easily configure the prompt to suit your preferences.
- **Git Integration**: Displays the current Git branch and status.
- **Cross-Platform**: Works on any system that supports Bash.
- **Container Awareness**: Indicates if you are inside a containerized environment.
- **Modular Design**: Add or remove prompt components as needed.

## Installation

The recommended way to install Bashship on Debian/Ubuntu based systems through the package manager. To do so follow the instructions below, on the [archive page](https://archive.mlstidbits.com).

```bash
echo "deb [arch=amd64 signed-by=/usr/share/keyrings/MLSTidbits.gpg] https://archive.mlstidbits.com/ stable main" |
sudo tee /etc/apt/sources.list.d/MLSTidbits.list

wget -qO - https://archive.mlstidbits.com/key/MLSTidbits.gpg | sudo dd of=/usr/share/keyrings/MLSTidbits.gpg
```

Then update your package lists and install bashship:

```bash
sudo apt update
sudo apt install bashship -y
```

Once installed, you can enable Bashship by adding the following to the bottom of your `~/.bashrc` file: `source /usr/bin/bashship
`.

Then, restart your terminal or run `source ~/.bashrc` to apply the changes. You should now see the Bashship prompt in your terminal.

## CONFIGURATION

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

The `CHARACTER` variable sets the symbol used at the end of the prompt. You can also customize its color using the `CHARACTER_COLOR` variable. If the last command failed (non-zero exit status), the prompt symbol will change to the value of `CHARACTER_ROOT` and its color will change to `CHARACTER_COLOR_ERROR`.

| Variable                | Description                                          | Common Values             |
|-------------------------|------------------------------------------------------|---------------------------|
| `CHARACTER`             | The symbol used at the end of the prompt             | `>`, `$`, `#`             |
| `CHARACTER_COLOR`       | Color of the user component                          | 256 bit ASCII color codes |
| `CHARACTER_COLOR_ERROR` | Color of the user component when last command failed |  |

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

## Contributing

Contributions are welcome! If you find a bug or have a feature request, please open an issue. Feel free to submit pull requests for any improvements or new features.

## License

Bashship is licensed under the GPL-3.0 License. See the [LICENSE](LICENSE) file for more details.
