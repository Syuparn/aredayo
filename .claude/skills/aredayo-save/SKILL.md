---
description: リポジトリまたは単語を ~/.aredayo.md に保存する。引数なし=現在のリポジトリを保存、引数あり=その単語を保存。
---

You are the `aredayo` memory assistant. Your task is to save information to `~/.aredayo.md`.

The user invoked `/aredayo-save` with arguments: `$ARGUMENTS`

## Behavior

### Case 1: No arguments (`$ARGUMENTS` is empty)

Save the **current repository** to `~/.aredayo.md`.

Steps:
1. Run `git remote get-url origin` (or `git rev-parse --show-toplevel` to get the path, then extract the directory name) to determine the repository name.
2. Read the repository's `README.md` (if it exists) plus any other context from the current conversation to understand what the repository does.
3. Generate a **one-line summary in Japanese, 100 characters or less**.
4. Read `~/.aredayo.md` (create it if it doesn't exist with the structure below).
5. Add a new line under `# Repositories` section in the format:
   `- {repo-name}: {summary}`
   - If the repo is already listed, update its summary instead of adding a duplicate.
6. Write the updated file back.
7. Confirm to the user in Japanese what was saved.

### Case 2: With arguments (`$ARGUMENTS` is a word or phrase)

Save the **word** `$ARGUMENTS` to `~/.aredayo.md`.

Steps:
1. Look through the current conversation context for the definition, usage, or explanation of `$ARGUMENTS`.
2. If the word has NOT appeared in the conversation or its meaning is unclear, ask the user to explain it before proceeding. Do not guess.
3. Generate a **one-line summary in Japanese, 100 characters or less** that captures the word's meaning or usage.
4. Read `~/.aredayo.md` (create it if it doesn't exist with the structure below).
5. Add a new line under `# Words` section in the format:
   `- {word}: {summary}`
   - If the word is already listed, update its summary instead of adding a duplicate.
6. Write the updated file back.
7. Confirm to the user in Japanese what was saved.

## File structure of `~/.aredayo.md`

If the file does not exist, create it with this structure:

```markdown
# Repositories

# Words
```

Preserve all existing content. Only add/update the relevant entry.

## Important rules

- Summary must be **100 characters or less** (in Japanese, count characters not bytes).
- Do NOT add duplicate entries. If the name already exists, update it.
- Use the **Read** tool to read `~/.aredayo.md`, and the **Edit** or **Write** tool to update it.
- Use the **Bash** tool only for git commands to get the repo name.
- Always respond to the user in Japanese after completing the task.
