# Choosing a Naming Convention for ASSISTANT Git Branches

When working with AI coding assistants, using a consistent branch naming convention is essential for clarity, organization, and auditability. This document provides guidance on selecting an appropriate naming scheme.

## Recommended Naming Conventions

Based on the project's principles and best practices, here are recommended branch naming conventions for AI coding assistant sessions:

> For a detailed discussion about including parent branch names in your branches, see [Parent Branch References in AI Branch Naming](../../../branches/ai-branch-parent-naming.md).

1. **`ai/agent-name/task-description`**

   - Example: `ai/claude/add-authentication-feature`
   - Reasoning: Clearly identifies it as AI-generated code, which agent created it, and the purpose

2. **`ai/agent-name/YYYYMMDD/task-description`**

   - Example: `ai/github-copilot/20250423/fix-memory-leak`
   - Reasoning: Includes date for chronological tracking of AI sessions

3. **`ai/parent-branch/agent-name/purpose`**

   - Example: `ai/feature-x/aider/refactor-api`
   - Reasoning: Shows which feature branch the AI work is based on

4. **`ai/JIRA-ID/agent-name`**
   - Example: `ai/PROJ-123/claude`
   - Reasoning: Links the AI work to a specific ticket or task for traceability

## Benefits of Consistent Branch Naming

These naming conventions provide several benefits:

- **Transparency**: Clear indication that branch contains AI-assisted code
- **Traceability**: Easy to identify which AI tool generated the code
- **Purpose-driven**: Communicates the goal of the AI assistance
- **Consistency**: Follows the project's noun-verb naming pattern
- **Discoverability**: Allows filtering branches by AI tool or purpose
- **Audit trail**: Supports code review processes for AI-generated code

## Implementation Guidance

When implementing these naming conventions:

1. Choose the format that best fits your team's workflow and the nature of your project
2. Document your chosen convention in your project's CONTRIBUTING.md or equivalent
3. Consider automating branch name creation through your AI safety tooling
4. Enforce the convention through tooling like git hooks or repository settings
5. Include the convention in onboarding documentation for all team members