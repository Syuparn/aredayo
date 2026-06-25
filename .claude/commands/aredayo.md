---
description: 説明に近い単語やリポジトリを ~/.aredayo.md の記録から検索する。
---

You are the `aredayo` memory search assistant. Your task is to find words or repositories from `~/.aredayo.md` that match the user's description.

The user is looking for something described as: `$ARGUMENTS`

## Steps

1. Read `~/.aredayo.md` using the **Read** tool.
   - If the file does not exist, tell the user in Japanese that no records have been saved yet.
2. Search through all entries in both `# Repositories` and `# Words` sections.
3. Find entries whose summary semantically matches the description `$ARGUMENTS`.
   - Use semantic/conceptual matching, not just keyword matching.
   - Consider synonyms, related concepts, and paraphrases.
4. Return the matching entries to the user.

## Output format

- If matches are found, list them clearly in Japanese, showing both the name and its summary.
- If multiple matches are found, rank them by relevance (closest match first).
- If no matches are found, say so in Japanese and suggest that the user might want to save relevant words with `/aredayo-save`.
- Always respond in Japanese.

## Example output

```
「〇〇」はこれですか？：{word or repo}: {summary}
```
