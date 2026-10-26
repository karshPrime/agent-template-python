# Changelog

## Added

* 3.0.2
   * a shorter README with the right copy command, gh:karshosphere/template-python
   * the first commit of a new project links to this template
* 3.0.1
   * generated code passes make format-dry-run when no author is set in the Copier settings
* 3.0.0
   * VERSION holds a plain X.Y.Z here and in generated projects, with CI adding the v for tags
   * existing projects remove the v from VERSION once
* 2.2.0
   * generated projects take their package version from VERSION
   * existing projects run `uv lock` once after updating
* 2.1.2
   * shell history in the dev container persists between sessions
* 2.1.1
   * the dev container, and CI with it, starts on hosts that have no /etc/timezone
* 2.1.0
   * generated projects keep their Copier answers in `.copier-py-answers.yml` at the root rather than in `.copier-generic-project/`
   * existing projects move the file once before their next update
* 2.0.0
   * generated projects ship a Makefile with build, format, format-dry-run, test and release targets in place of run.sh
   * make in the dev container, and the shared CI calls make
* 1.2.0
   * generated projects ship the shared GitHub CI, a VERSION file and the shared Renovate settings, which copier update leaves alone
* 1.1.0
   * generated projects ship a run.sh for building, formatting with ruff, testing with pytest and building a wheel and sdist
   * starter tests and ruff-clean code
* 1.0.2
   * generated projects install, start and build
   * a uv.lock, the right colorlog package, a working FastAPI lifespan and a pinned uv in the dev container
* 1.0.1
   * the Copier badge in generated READMEs links to karshosphere/template-python
* 1.0.0
   * `VERSION` file starting at v1.0.0, checked on every pull request
   * each merge to main tagged with that version
