# Parent Branch References in AI Branch Naming

When working with AI coding assistants, deciding whether to include the parent branch name in your AI branch naming convention involves several considerations.

## Value of including parent branch in name

1. **Immediate visibility**: Provides context about the source branch without requiring git commands
2. **Clear merge target**: Makes it obvious where the branch should be merged back into
3. **Development context**: Shows what codebase state the AI was working with
4. **Organizational benefits**: Helps organize multiple AI sessions branching from different feature branches
5. **Easier code review**: Reviewers immediately understand the starting point for AI changes

## Alternatives to including parent branch in name

If you choose not to include the parent branch in the name, you can check the parent/upstream branch using:

```bash
# Show all branches with their tracking information
git branch -vv

# Visual representation of branch history
git log --graph --oneline --all

# Show upstream branch for a specific branch
git for-each-ref --format='%(upstream:short)' refs/heads/branch-name

# Show branches and their relationships
git show-branch -a
```

## Trade-offs to consider

- **Branch name length**: Including too many components (agent, date, parent, task) can make names unwieldy
- **Information vs. brevity**: Balance between providing context and keeping names manageable
- **Project complexity**: More valuable in projects with many parallel development branches
- **Team familiarity**: Consider how familiar your team is with git commands for checking branch relationships

## Recommendation

For projects with complex branching strategies or multiple parallel development efforts, include the parent branch in the name. For simpler projects with a small number of long-lived branches, it may be unnecessary.

Example with parent branch included:

```
ai/main/claude/add-authentication
ai/feature-x/copilot/fix-memory-leak
```

Example without parent branch:

```
ai/claude/add-authentication
ai/copilot/fix-memory-leak
```

