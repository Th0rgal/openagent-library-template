---
name: github-cli
description: >
  Interact with GitHub using the gh CLI - PRs, issues, repos, releases, and actions.
  Trigger terms: github, gh, pull request, PR, issue, release, actions, workflow, repo.
---

## When to Use
- Creating, viewing, or merging pull requests
- Managing issues (create, close, comment)
- Checking workflow/action status
- Creating releases
- Cloning or forking repos

## When NOT to Use
- Local git operations (use `git` directly)
- Non-GitHub remotes (GitLab, Bitbucket)

## Prerequisites
- `gh` CLI installed
- SSH key `~/.ssh/agent` configured for GitHub access
- Set `GIT_SSH_COMMAND` if needed: `export GIT_SSH_COMMAND="ssh -i ~/.ssh/agent"`

## Quick Reference

### Pull Requests
| Action | Command |
|--------|---------|
| List PRs | `gh pr list` |
| View PR | `gh pr view <number>` |
| Create PR | `gh pr create --title "..." --body "..."` |
| Checkout PR | `gh pr checkout <number>` |
| Merge PR | `gh pr merge <number>` |
| PR diff | `gh pr diff <number>` |
| PR checks | `gh pr checks <number>` |

### Issues
| Action | Command |
|--------|---------|
| List issues | `gh issue list` |
| View issue | `gh issue view <number>` |
| Create issue | `gh issue create --title "..." --body "..."` |
| Close issue | `gh issue close <number>` |
| Comment | `gh issue comment <number> --body "..."` |

### Repos & Releases
| Action | Command |
|--------|---------|
| Clone | `gh repo clone <owner>/<repo>` |
| Fork | `gh repo fork <owner>/<repo>` |
| View repo | `gh repo view` |
| Create release | `gh release create <tag> --title "..." --notes "..."` |
| List releases | `gh release list` |

### Actions & Workflows
| Action | Command |
|--------|---------|
| List runs | `gh run list` |
| View run | `gh run view <run-id>` |
| Watch run | `gh run watch <run-id>` |
| Rerun failed | `gh run rerun <run-id> --failed` |
| List workflows | `gh workflow list` |

### API Access
```bash
gh api repos/<owner>/<repo>/pulls
gh api graphql -f query='...'
```

## Procedure

1. Ensure `gh auth status` shows authenticated
2. Use `gh pr list` or `gh issue list` to find items
3. Perform action with appropriate command
4. Verify with `gh pr checks` or `gh run list`

## Checks & Guardrails
- Always check PR status before merging
- Use `--draft` for work-in-progress PRs
- Prefer `gh pr merge --squash` for clean history
- Check `gh run list` after pushing to verify CI
