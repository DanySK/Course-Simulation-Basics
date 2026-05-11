# Agent Instructions

## Scope

- Treat the repository as two separate work areas.
- Use the root for the slide deck sources: `Simulation.tex`, `bib.bib`, `img/`, and `isac-slides.sty`.
- Use `ext/SAPERE-incarnation-tutorial/` for the runnable Alchemist tutorial project.
- Treat `out/` as generated output. Edit the LaTeX sources first, and only update generated artifacts when the task requires it.

## Validation

- Do not use `./gradlew` at the repository root. The root does not contain the matching Gradle wrapper files or a root Gradle build.
- When you change anything under `ext/SAPERE-incarnation-tutorial/`, validate it with `cd ext/SAPERE-incarnation-tutorial && ./gradlew build`.
- When you change Kotlin dependencies, Gradle configuration, or runtime behavior in the tutorial project, keep fixing the integration until `./gradlew build` passes in `ext/SAPERE-incarnation-tutorial/`.
- When you change tutorial simulations under `ext/SAPERE-incarnation-tutorial/src/main/yaml/` or `ext/SAPERE-incarnation-tutorial/effects/`, run the most relevant generated Gradle task for the scenario you touched when practical, for example `cd ext/SAPERE-incarnation-tutorial && ./gradlew 10-math`.
- When you change the root LaTeX deck, validate by compiling `Simulation.tex` with the local TeX toolchain if it is available. If you cannot run that validation locally, say so clearly in your final report.

## Formatting And Style

- No repository-local formatter task is exposed at the root or in `ext/SAPERE-incarnation-tutorial/`. Preserve the existing formatting style of the file you edit instead of introducing a new formatter.
- Keep LaTeX, YAML, JSON, and Kotlin edits small and consistent with surrounding files.
- Treat warning suppressions as a last resort. Add a short justification next to every suppression you introduce.

## Submodule Rules

- `ext/SAPERE-incarnation-tutorial/` is a Git submodule, not a normal directory.
- Keep submodule pointer updates intentional. If you edit files inside the submodule, mention that the root repository records the new submodule commit.
- Do not replace submodule-managed files by copying content into the root repository.

## Commits

- For changes committed inside `ext/SAPERE-incarnation-tutorial/`, use conventional commits with the header format `type(scope): summary`.
- Mark breaking changes as `type(scope)!: summary` and add a `BREAKING CHANGE:` footer.
- For the tutorial submodule, follow the `semantic-release-preconfigured-conventional-commits` mapping already present in `package.json` and `release.config.js`: `feat` for minor releases; `fix`, `docs`, `perf`, and `revert` for patch releases; `chore(api-deps)` for minor dependency releases; `chore(core-deps)` for patch dependency releases; `test`, `ci`, `build`, `style`, `refactor`, and other `chore(...)` scopes for non-release maintenance work.
- For agent-instruction or agent-policy changes, prefer `chore(...)` or `ci(...)` instead of `docs(...)`.
- Keep commit subjects imperative and specific. Avoid vague summaries.
