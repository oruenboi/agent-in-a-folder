# Codex Markdown Wiki Starter

A local Codex project with shared rules in `AGENTS.md`, scoped instructions in `wiki/AGENTS.md` and `raw/AGENTS.md`, and a canonical Markdown wiki in Open Knowledge Format (OKF) v0.2.

## Start here

1. Create a repository from this template and open its root as a local Codex project.
2. Set your project name in `AGENTS.md` and your scope in [the project plan](devplan/plan.md).
3. Ask Codex to ingest an approved source or explore the fictional example through the [wiki index](wiki/bundle/index.md).

The [setup guide](SETUP.md) explains the folder structure and how to add it to an existing project. See [optional CLI tools](SETUP.md#7-optional-cli-tools) if the wiki outgrows the index and text search.

Codex reads and maintains `wiki/bundle/` as the OKF v0.2 bundle. Each concept has typed YAML frontmatter, and sourced claims point to structured provenance. `raw/` holds original captures, and the bundle carries approved local evidence needed to resolve its references. [OKF v0.2 specification](https://github.com/GoogleCloudPlatform/open-knowledge-format/blob/main/SPEC.md)

## Try it

- Ask “From the wiki, when is the sample project’s glossary review? Cite the evidence.” The source records Tuesdays.
- Ask “From the wiki, what budget was approved for the sample project?” Expect an explicit evidence gap. Check that both queries leave the working tree clean.
- Ask “Re-ingest sample-kickoff at revision v1.” Check that the capture and source note are reused.

Record the results in [the setup checklist](devplan/todo.md).
