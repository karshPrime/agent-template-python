
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
* The `--trust` option is required because the template runs `git` and `uv lock`. Without uv installed, run `uv lock` in the dev container afterwards and commit `uv.lock`.


### Default Config

User-specific values are loaded from the global configuration file - `~/.config/copier/settings.yml`. If the file is not present or not saved, empty strings are used as defaults.
```
defaults:
  user_name  : "karsh"
  user_email : "karshmail@icloud.com"
  github_user: "karnull"

```



### Updating a Project

Generated projects keep their Copier answers in `.copier-py-answers.yml` at the project root. From there:

```bash
$ copier update --defaults --answers-file .copier-py-answers.yml
```

Projects generated before the answers file moved keep it in `.copier-generic-project/`. Move it once before updating:

```bash
$ git mv .copier-generic-project/.copier-py-answers.yml .copier-py-answers.yml
```

Projects generated before v2.2.0 hold a fixed version in `uv.lock`. After the update that takes `pyproject.toml` to the version in `VERSION`, refresh the lock once and commit it, or `make build` fails on the out-of-date lock:

```bash
$ uv lock
```


### Versioning and CI

The template's release version lives in `VERSION` as `vX.Y.Z`. Bump it in every change that should be released:
* `Z` for minor fixes.
* `Y` for minor features and chores.
* `X` for breaking changes, such as renamed questions or moved files that affect `copier update` in existing projects.

GitHub Actions (`.github/workflows/ci.yml`) runs two jobs:
* **version:** on every pull request and push to `main`, checks that `VERSION` holds a single `vX.Y.Z` line.
* **tag:** on push to `main`, tags the merged commit with the version in `VERSION`, so existing projects can move to it with `copier update`. If the tag already exists, nothing is tagged.

The workflow is read-only apart from the tag job, which needs write access to create the tag. It runs on `pull_request`, never `pull_request_target`, so code from a fork never runs with this repository's credentials. Actions are pinned to commit SHAs, and Renovate (`renovate.json`) proposes updates to them weekly.


### Project Tasks

Every generated project has a `Makefile` at its root:
* `make build` installs the locked dependencies and byte-compiles the package.
* `make format` formats the Python sources with ruff; `make format-dry-run` lists unformatted files and fails if there are any.
* `make test` runs the tests with pytest.
* `make release` builds a wheel and an sdist into `dist/`, versioned from the project's `VERSION` file.


### GitHub CI

Generated projects ship with the shared workflow from [template-github-ci](https://github.com/karshosphere/template-github-ci), vendored into `template/.github/`. It expects the project's `Makefile` and `.devcontainer/`, requires a `VERSION` bump on every pull request, and publishes a GitHub release on each merge to main.

To bring in a newer release of the workflow, from this repository's root:

```bash
$ copier update -a .github/.copier-ci-answers.yml template
```
