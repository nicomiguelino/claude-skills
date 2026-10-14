# claude-skills

Personal Claude Code skills.

- `commit`: create a conventional commit
- `open-pr`: open a pull request

The repo is mounted at `.claude/skills` in a project as a submodule.

## Add to a new or existing repo

```sh
git submodule add git@github.com:nicomiguelino/claude-skills.git .claude/skills
git config -f .gitmodules submodule..claude/skills.ignore all
git add .gitmodules .claude/skills
git commit -m "chore(claude): use shared skills submodule"
```

- If `.claude/skills` already exists, remove it first with `git rm -r .claude/skills`.
- `ignore = all` keeps changes inside the submodule out of `git status` in the parent repo.

## Clone a repo that uses it

```sh
git clone --recurse-submodules <repo-url>
```

For an existing clone:

```sh
git submodule update --init
```

## Update the skills

Commit and push changes from inside `.claude/skills`, then in each project:

```sh
git submodule update --remote .claude/skills
git add .claude/skills
git commit -m "chore(claude): update skills submodule"
```

Because of `ignore = all`, `git status` won't show the new submodule commit. Use `git add .claude/skills` explicitly.
