# Changelog

## added/modified:

* chore/ci: `VERSION` file starting at v1.0.0, checked on every pull request, with each merge to main tagged with that version.
* fix/readme-badge: the Copier badge in generated READMEs links to karshosphere/template-python.
* fix/project-builds: generated projects install, start and build, with a uv.lock, the right colorlog package, a working FastAPI lifespan and a pinned uv in the dev container.
* feature/run-script: generated projects ship a run.sh for building, formatting with ruff, testing with pytest and building a wheel and sdist, with starter tests and ruff-clean code.
* feature/github-ci: generated projects ship the shared GitHub CI, a VERSION file and the shared Renovate settings, which copier update leaves alone.
* feature/makefile: generated projects ship a Makefile with build, format, format-dry-run, test and release targets in place of run.sh, with make in the dev container and the shared CI calling make.
