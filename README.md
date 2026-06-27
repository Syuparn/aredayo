# aredayo
An agent command to help you remember repository names!

## Commands

### `/aredayo-save`

Saves the current repository's name and a one-line summary to `~/.aredayo.md`.

```
/aredayo-save
```

### `/aredayo-save {word}`

Saves a word and its one-line summary (derived from the current conversation context) to `~/.aredayo.md`.
If the word hasn't appeared in the conversation, you will be asked to explain it first.

```
/aredayo-save ホットリロード
```

### `/aredayo {description}`

Searches saved records in `~/.aredayo.md` for words or repositories that semantically match the given description.

```
/aredayo コードを変更したらすぐ反映される機能
```

## Storage format

Records are saved to `~/.aredayo.md` with the following structure:

```markdown
# Repositories
- aredayo: リポジトリ名と概要を記録・検索できるagent skill

# Words
- ホットリロード: コードを変更した際にサーバー再起動なしで即座に反映する機能
```

Each entry is a single line of 100 characters or less.
