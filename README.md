# workspace

A skeleton workspace for multidisciplinary IT and development work, designed to be
used alongside an AI coding agent (e.g. inside an agentbox container).

The repository only ships the *structure* of the workspace. Everything you put
into it — code, notes, downloads, experiments — stays local and is never
committed.

## Layout

| Path          | Purpose                                                              |
| ------------- | -------------------------------------------------------------------- |
| `projects/`   | Work on longer-term projects, e.g. repositories you keep coming back to. |
| `resources/`  | Reference material: docs, specs, datasets, assets.                   |
| `tasks/`      | One-off tasks that don't belong to an ongoing project.               |
| `tools/`      | Helper scripts and utilities used across projects.                   |
| `scratch/`    | Throwaway experiments and temporary output.                          |
| `private/`    | Personal or sensitive files. Hidden from agents (see below).         |
| `CLAUDE.md`   | Optional agent instructions for this workspace (tracked if present). |

Each directory is kept in git with an empty `.gitkeep` file only; its contents
are ignored.

## How the ignore rules work

`.gitignore` is an allowlist. It starts by ignoring everything:

```gitignore
**/*
```

and then re-includes just the directory skeleton (`<dir>/` and `<dir>/.gitkeep`)
plus the top-level files `.agentignore`, `.gitignore`, `CLAUDE.md`, `LICENSE`
and `README.md`. So a fresh clone gives you the empty folder structure, and
nothing you add to the workspace is picked up by `git add` by accident.

To ship something new, add an explicit `!` rule for it in `.gitignore`.

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
