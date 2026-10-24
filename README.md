# claude-skillset

Claude Code skills I built and use every day. Each one lives in its own repo and installs as a plugin. This repo is the catalog that ties them together: add it once, then install any of them by name.

## Install

In Claude Code:

```
/plugin marketplace add huttonbenj/claude-skillset
/plugin install <tool>@claude-skillset
```

From a terminal, the same two steps are `claude plugin marketplace add huttonbenj/claude-skillset` and `claude plugin install <tool>@claude-skillset`.

## Tools

| Tool | What it does |
|---|---|
| [youtube-reader](https://github.com/huttonbenj/youtube-reader) | Saves YouTube transcripts, video details and top comments to a local library, so Claude can summarize, fact-check and compare what videos, channels and searches say. |

## Updates

Run `claude plugin update <tool>`, then restart Claude Code. Each tool's changelog says what changed.

## How this repo works

The catalog is one file, [`.claude-plugin/marketplace.json`](.claude-plugin/marketplace.json), which lists each tool and where its repo lives. A new tool gets its own repo with a `.claude-plugin/plugin.json` and its skills, has to pass `claude plugin validate`, and then gets an entry here.

Entries point at each repo's HTTPS clone URL rather than the `github` shorthand, because `claude plugin update` tries SSH for the shorthand and fails for anyone without a GitHub SSH key. (Adding the catalog itself by shorthand, as above, is fine.) CI validates `marketplace.json` and checks that every entry uses an HTTPS URL, on pushes to main and on pull requests; each tool's own repo validates its plugin.

## License

MIT. See [LICENSE](LICENSE).
