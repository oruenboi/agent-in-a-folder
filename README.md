# Agent in a Folder

**All the software you need is an AI assistant that can already read and edit files.** Give it a folder, some documents, and a few written instructions, and it can build a wiki you can ask questions about.

The idea started with Andrej Karpathy’s LLM Wiki. An assistant can read the material you give it, turn it into linked notes, and keep those notes useful as you add more. Because the work is saved in the folder, you can open it in a new chat or with a different assistant and pick up where you left off. [LLM Wiki](https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f)

## Try it with the sample notes

1. Download or copy this folder and give your AI assistant access to it.
2. Ask it, “Read `AGENTS.md`. When does the sample project review its glossary? Show me where you found the answer.”
3. It should answer **Tuesdays** and point you to the source. Try asking what budget was approved to see how it handles a detail the notes leave open. [Sample wiki note](wiki/bundle/sources/sample-kickoff.md) · [Original evidence](wiki/bundle/references/sample-kickoff.v1.txt)

To add the same setup to a project you already use, copy [bootstrap.md](bootstrap.md) into that folder and tell your assistant, “Set up this project using `bootstrap.md`.”

## How it works

**Add something.** Give the assistant a document and ask it to add it to the wiki. It saves the original and writes a shorter note that points back to it. If the document changes later, the assistant can keep both versions so you can see what changed.

**Ask a question.** The assistant starts with the wiki’s list of topics, opens the relevant notes, and checks their sources. If you ask what was decided in a meeting, it can answer and point to the original record. Questions leave the saved files alone.

**Save a finding.** If an answer is worth keeping, ask the assistant to save it in the wiki. It adds or updates a note, links the evidence, and records what changed. [Wiki log](wiki/bundle/log.md)

## What’s in the folder

| File or folder | What it does |
| --- | --- |
| **Instructions** | `AGENTS.md` is the starting point. It sends the assistant to the wiki rules for questions and updates, and to the capture rules when adding a source. [Root rules](AGENTS.md) · [Wiki rules](wiki/AGENTS.md) · [Capture rules](raw/AGENTS.md) |
| **Original material** | `raw/sources/` holds saved versions of the documents you add. The wiki can carry an approved copy of a source when it needs to travel as a self-contained bundle. [Sample capture](raw/sources/sample-kickoff.v1.md) |
| **Wiki** | `wiki/bundle/` holds the index and linked notes as Markdown text files. It uses Open Knowledge Format (OKF) v0.2 to record each note’s type and sources in a consistent way. [Wiki index](wiki/bundle/index.md) · [OKF specification](https://github.com/GoogleCloudPlatform/open-knowledge-format/blob/main/SPEC.md) |

The index and ordinary file lookup are enough to get started. For a larger wiki, the guide covers QMD and other optional search tools. You can also use Git to track changes if you keep the folder in a repository. [Optional CLI tools](bootstrap.md#7-optional-cli-tools)

## Credits

- Andrej Karpathy’s pattern for turning raw sources into a wiki that an agent maintains over time. [LLM Wiki](https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f)
- Google Cloud’s specification for portable Markdown knowledge bundles and structured provenance. [Open Knowledge Format](https://github.com/GoogleCloudPlatform/open-knowledge-format/tree/main)
- Vivian Balakrishnan’s design for retrieving relevant context from linked, sourced OKF knowledge. [OKF Graph Wiki](https://gist.github.com/VivianBalakrishnan/83d1ea5f929d0ae51bca7fe25129b0d7)

## License

[MIT](LICENSE)
