# workspace

A skeleton workspace designed to be used alongside an AI coding agent (e.g. inside an agentbox container).

The repository only ships the *structure* of the workspace.

## Layout

| Path          | Purpose                                                                  | Visible to agents by default |
| ------------- | ------------------------------------------------------------------------ | ---------------------------- |
| `docs/`       | Documents, use it in the same way you use your normal documents folder.  | Y                            |
| `private/`    | Private folder that is hidden from agents by default.                    | N                            |
| `projects/`   | Work on longer-term projects, e.g. repositories you keep coming back to. | Y                            |
| `resources/`  | Reference material: docs, specs, datasets, assets.                       | Y                            |
| `tasks/`      | One-off tasks that don't belong to an ongoing project.                   | Y                            |
| `tools/`      | Helper scripts and utilities used across projects.                       | Y                            |
| `scratch/`    | Throwaway experiments and temporary output.                              | Y                            |

## Quickstart

```bash
git clone https://github.com/sblmnl/workspace.git ~/workspace
cd ~/workspace
rm -rf .git ./**/.gitkeep .gitignore LICENSE README.md
agentbox init
```

## Agent visibility

`.agentignore` lists paths that coding agents should not read. By default it
contains:

```
/private/
```

Use `private/` for anything an agent should not see: credentials, personal
documents and the like.

## Running the workspace in agentbox

This workspace is meant to be run inside
[agentbox](https://github.com/sblmnl/agentbox-prototype). Its configuration
(`agentbox.toml` and `agentbox.dockerfile`) is gitignored, so each machine keeps
its own. To set it up from the repo root:

1. Run `agentbox init` to generate `agentbox.toml` and `agentbox.dockerfile`.
2. Edit `agentbox.dockerfile` to install whatever agents and tools you want in
   the box.
3. Run `agentbox` to build the image and start the box.

See the agentbox repository for in-depth setup and configuration docs.

## License

Released into the public domain under [The Unlicense](LICENSE).
