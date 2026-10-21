
# Generic Template

[![Copier](https://img.shields.io/endpoint?url=https://raw.githubusercontent.com/copier-org/copier/master/img/badge/badge-grayscale-inverted-border-orange.json)](https://github.com/copier-org/copier)

This repository provides a template for creating Python development environments using `uv`. It got a consistent and reproducible starting point which makes it easier to apply improvements when the template is updated.


### Prerequisites

Install the Copier command:
* **Quick option:** `uv tool install copier`
* **Documentation:** https://copier.readthedocs.io/en/stable


### Create New Project

Run the following command:

```bash
$ copier copy --trust --vcs-ref=python git@github.com:karnull/templates path/to/project
```
* **Project Description:** Answer the Copier prompt with an optional plain‑text description of your project.
* **Library Pack:** Optional selection of libraries to include in the project.
* The `--trust` option is required because the template runs `git` and `uv` commands.


### Default Config

User-specific values are loaded from the global configuration file - `~/.config/copier/settings.yml`. If the file is not present or not saved, empty strings are used as defaults.
```
defaults:
  user_name  : "karsh"
  user_email : "karshmail@icloud.com"
  github_user: "karnull"

```

