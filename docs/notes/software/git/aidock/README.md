# AIdock - AI Assistant Safety Precheck Protocol

> _Before allowing Cylons to dock on Galactica, safety protocols must be
> followed to secure the hangar and preserve mission integrity._

## Overview

AIdock is a safety protocol tool designed to protect sensitive project data
before an AI coding assistant is allowed to interact with a file directory.

- Ensures all necessary backups are in place
- Audit for potentially sensitive data
- Ensure auditability of ASSISTANT
- Require explicit user confirmation before access is granted

Think of it as an airlock between your codebase and the assistant — only opening once
it’s safe to do so.

## Glossary

| Term       | Definition                                                                 |
| ---------- | -------------------------------------------------------------------------- |
| ASSISTANT  | AI Coding assistant tool (e.g. Aider, Claude Code, GitHub Copilot, Cursor) |
| GITHOST    | Git Hosting provider (e.g. GitHub.com, Gitlab.com, etc)                    |
| TARGET_DIR | The top level directory the ASSISTANT will have access to                  |

## 1. Preserve Data Integrity

To protect against data loss and facilitate audit / recovery:

- The target directory must be backed up before granting access
- The ASSISTANT must no be able to modify the backup

### Actions

1. Check status of TARGET_DIR and controls in place
1. Recommend changes if appropriate
1. Perform backup if required

### Preferred Method: Git

- Git is ubiquitous and is well suited to ensuring file integrity
- **Alternative Methods (Optional):** Other backup formats (e.g., zip archives or cloud snapshots) may be supported, but Git is the primary method.

#### Questions

- **Git-Ignored Files:** How best to deal with files excluded from backup by `.gitignore`

#### Rules

- TARGET_DIR is within a git repository
- TARGET_DIR contains no uncommitted changes (`git status` is clean)
- All commits have been pushed to a Git remote
- ASSISTANT cannot push to remote branches used for secure backup
- ASSISTANT cannot change history

#### Implementation

Some ideas for review:

- ASSISTANT cannot directly modify `.git/`
- Set read-only permissions on `.git/` directory
- Configure `receive.denyNonFastForwards=true` in git config
- Use git hooks (pre-receive) to reject history-altering commands
- Run ASSISTANT with restricted file permissions or in container
- Create reference snapshot outside ASSISTANT's reach
- Set up filesystem monitoring for changes to `.git/` directory
- Use separate git user with limited permissions for ASSISTANT operations

## 2. Ensure Confidentiality and Integrity of Sensitive Data

To protect against inappropriate access or modification by ASSISTANT,
categorize appropriate access permissions (read, write, none),
for all content in TARGET_DIR (files, dirs, metadata),
and review controls in place to protect them.

1. Categorize appropriate access permissions for files in TARGET_DIR
1. **Review controls in place**: external and ASSISTANT provided.
1. **Report and recommend changes**
1. [Optional] Perform transformations (e.g. reversible string substitution)

### Categorize Appropriate Access Permissions for Sensitive Files

- **Common Targets:** Files like `.env`, `*.pem`, `*.key`, `secrets.json`, and other credential-containing formats.
- **Files referenced in ignorefiles**: `.gitignore`, `.aiderignore`, etc

### Review controls around AI tools access to sensitive data

Prefer verifiable external system controls over promises from ASSISTANT.

- **ASSISTANT provided controls**: Access confined to TARGET_DIR
- **External system controls**: chroot, podman

- **Context-Aware Ignore Rules:**
  - Aider: Respect `.aiderignore` if present.
  - Claude: consider any Claude-specific ignore patterns (e.g., `.claudeignore`).
  - Always check `.gitignore` as a fallback.
- **Action:** Flag potentially sensitive files and present options to exclude them or proceed with a warning.

### 3. Ensure ASSISTANT Actions are auditable

- Code changes made by ASSISTANT should be reviewed being merged into main/master branch.
- It should be easy to review all actions taken by ASSISTANT.

#### ASSISTANT Should Not Impersonate You

## Implementation

- **Sign your own commits with a hardware security key**: ASSISTANT won't have access.
- **Identify ASSISTANT in commit message author field**: e.g. `Mike Bailey (Aider) <mike@failmode.com>`
- **If they need GITHOST account, give them their own**
- **Don't allow ASSISTANT to assume your identity with GITHOST CLI tools:** e.g. GitHub CLI
- **Maybe run ASSISTANT under a different computer user account?**

#### Restrict ASSISTANT to a limited set of Git branches

- **ASSISTANT changes should not be committed directly to `main/master` branch.**
- **ASSISTANT changes should be committed well named branches:** [AI Branch Naming Conventions](./ai-branch-naming-conventions.md)

#### Actions

## 4. User Acknowledgment and Logging

- **Confirmation Required:** Present a summary of backup status and audit results before allowing access.
- **User Approval:** Require explicit user confirmation to continue (e.g., prompt or command-line flag).
- **Logging:** Record tool operations, flagged files, and user decisions in a local log file for audit and traceability.
