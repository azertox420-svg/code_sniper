# Code Redeemer

Public repository layout for the Roblox code-redeemer project.

```text
code-redeemer/
  manifest.json
  README.md
  code/
    azertoxbest.lua
  data/
    manifest.json
    azertox_db.lua.txt
```

The active database is one canonical `azertox_db.lua.txt` file. It contains one answer per normalized question, with duplicate wording merged before publication. The older JSON/shard files remain in the repository as source history but are not loaded by the manifest.

Never commit API keys, webhooks, tokens, cookies, or personal configuration files. Enter those locally at runtime.

## GitHub setup

1. Create a public GitHub repository.
2. Upload this folder while preserving `code/` and `data/`.
3. Upload the corrected script as `code/azertoxbest.lua`.
4. Commit that change and upload the updated script.

The direct loader is:

```lua
loadstring(game:HttpGet("https://raw.githubusercontent.com/azertox420-svg/code_sniper/main/code/azertoxbest.lua"))()
```

The script downloads `data/manifest.json`, executes the single canonical Lua return-table database, and caches it locally under `Azertox_v2`. No API key is stored in the repository.

Gemini/Groq keys are entered in the GUI and saved locally under a filename scoped to the Roblox `UserId`; users do not share a key through GitHub.

## Code reader

The reader first uses the game's redeem remote, so the Codes tab does not need to be opened. If that route is unavailable, it uses the textbox as a fallback without forcing the panel open. When a code arrives in several announcements, each block is written into the field immediately and the combined value is submitted only when the configured block count is reached.
