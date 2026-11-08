# Codex Markdown Wiki

A local, source-backed wiki that Codex can query and maintain. The wiki is a directory of Markdown files with YAML metadata in Open Knowledge Format (OKF) v0.2.

## The stack

| Layer | What it does |
| --- | --- |
| **Codex and `AGENTS.md`** | Codex reads the applicable project instructions and works with local files. The root file routes wiki work and source capture to their scoped rules. [Root rules](AGENTS.md) · [Wiki rules](wiki/AGENTS.md) · [Capture rules](raw/AGENTS.md) |
| **Markdown, YAML, and OKF v0.2** | `wiki/bundle/` is the canonical knowledge bundle. Each concept has a YAML `type`, and sourced claims use footnotes tied to structured `sources` entries. The bundle has a curated index and a dated change log. [Wiki index](wiki/bundle/index.md) · [OKF specification](https://github.com/GoogleCloudPlatform/open-knowledge-format/blob/main/SPEC.md) |
| **Source captures** | `raw/sources/` stores original revisions. The bundle carries byte-identical copies of approved local evidence under `wiki/bundle/references/` when a concept needs a self-contained citation. [Sample capture](raw/sources/sample-kickoff.v1.md) · [Bundled evidence](wiki/bundle/references/sample-kickoff.v1.txt) |
| **Local search** | Start with the index and search the bundle with `rg` or an equivalent local tool. QMD is optional for indexed search, with hybrid search and MCP available when configured. [Optional CLI tools](bootstrap.md#7-optional-cli-tools) |
| **Git** | Tracks changes to instructions, concepts, and captures when you keep the wiki in a repository. |

## How it works

1. **Ask a question.** Codex opens the index, finds the relevant concepts, and follows their citations to the evidence. It answers with citations, identifies gaps, and leaves the files untouched.
2. **Ingest a source.** On request, Codex saves the approved revision, creates or updates a typed source note, and records the provenance. A repeat ingest reuses the same capture. A changed source gets a new revision-qualified file.
3. **File a finding.** On request, Codex adds or revises a concept and cites its evidence. After a material edit, it refreshes the affected index entries, adds a dated log entry, and checks the metadata and links. [Wiki log](wiki/bundle/log.md)

## Use it

- **Copy the project.** Clone or download this repository and open its root in Codex. The instructions and sample wiki are ready to use. Set your scope in the [project plan](devplan/plan.md).
- **Add the wiki to an existing project.** Copy [bootstrap.md](bootstrap.md) to that project's root and tell Codex, “Set up this project using `bootstrap.md`.” The file contains the layout, instruction templates, and verification steps.

## Try it

- Ask “From the wiki, when is the sample project’s glossary review? Cite the evidence.” The expected answer is Tuesdays. Follow the footnote in the [sample source note](wiki/bundle/sources/sample-kickoff.md).
- Ask “From the wiki, what budget was approved for the sample project?” Expect an explicit evidence gap. Check that both queries leave the working tree clean.
- Ask “Re-ingest sample-kickoff at revision v1.” Check that the capture and source note are reused.

Record the results in [the setup checklist](devplan/todo.md).

## Credits

- Andrej Karpathy’s pattern for turning raw sources into a wiki that an agent maintains over time. [LLM Wiki](https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f)
- Google Cloud’s specification for portable Markdown knowledge bundles and structured provenance. [Open Knowledge Format](https://github.com/GoogleCloudPlatform/open-knowledge-format/tree/main)
- Vivian Balakrishnan’s design for retrieving relevant context from linked, sourced OKF knowledge. [OKF Graph Wiki](https://gist.github.com/VivianBalakrishnan/83d1ea5f929d0ae51bca7fe25129b0d7)

## License

[MIT](LICENSE)
