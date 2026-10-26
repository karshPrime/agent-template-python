# Changelog

## added/modified:

* chore/ci: `VERSION` file starting at v1.0.0, checked on every pull request, with each merge to main tagged with that version.
* fix/readme-badge: the Copier badge in generated READMEs links to karshosphere/template-python.
* fix/project-builds: generated projects install, start and build, with a uv.lock, the right colorlog package, a working FastAPI lifespan and a pinned uv in the dev container.
* feature/run-script: generated projects ship a run.sh for building, formatting with ruff, testing with pytest and building a wheel and sdist, with starter tests and ruff-clean code.
* feature/github-ci: generated projects ship the shared GitHub CI, a VERSION file and the shared Renovate settings, which copier update leaves alone.
* feature/makefile: generated projects ship a Makefile with build, format, format-dry-run, test and release targets in place of run.sh, with make in the dev container and the shared CI calling make.
* feature/root-answers-file: generated projects keep their Copier answers in `.copier-py-answers.yml` at the root rather than in `.copier-generic-project/`; existing projects move the file once before their next update.
* fix/devcontainer-timezone: the dev container, and CI with it, starts on hosts that have no /etc/timezone.
* fix/bash-history-mount: shell history in the dev container persists between sessions.
* feature/version-file: generated projects take their package version from VERSION; existing projects run `uv lock` once after updating.
* feature/plain-version: VERSION holds a plain X.Y.Z here and in generated projects, with CI adding the v for tags; existing projects remove the v from VERSION once.
* fix/empty-author: generated code passes make format-dry-run when no author is set in the Copier settings.
