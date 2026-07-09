# 🚀 Shell Quest

A tiny, offline **Capture-The-Flag game that teaches basic shell commands**.
You're an engineer aboard the failing starship *Terminal*. Repair all 10 decks
by finding a hidden `SQ{...}` flag on each one — using a real shell command.

No internet, no dependencies beyond a normal Unix shell (`bash`, `grep`,
`find`, `base64`, `sha256sum`).

## Quick start

```bash
cd shellquest
./sq start          # generates the ship and shows your first mission
```

Then for each deck:

```bash
./sq brief                      # read the mission
cd world/level00                # explore the deck with real commands
ls; cat welcome.txt             # ...find the SQ{...} flag
cd -                            # back to the game folder
./sq submit SQ{the_flag_here}   # turn it in to advance
```

Stuck on a deck? `./sq hint`.

## Commands

| Command | What it does |
|---|---|
| `./sq start` | Generate a fresh ship and show deck 0 |
| `./sq brief` | Show the current deck's mission |
| `./sq hint` | Reveal a hint for the current deck |
| `./sq submit SQ{..}` | Submit a flag to advance |
| `./sq status` | Show your progress bar |
| `./sq map` | List all decks and what each teaches |
| `./sq reset` | Rebuild a brand-new ship (new random flags) |
| `./sq help` | Full help screen |

## The 10 decks

| Deck | Theme | You'll learn |
|---|---|---|
| 0 | Wake Up, Engineer | `ls`, `cat` |
| 1 | Nothing to See Here | `ls -a` (hidden dotfiles) |
| 2 | Down the Rabbit Hole | `cd`, `pwd`, `ls` |
| 3 | Needle in a Haystack | `grep -r` |
| 4 | Captain's Log | `tail`, `head` |
| 5 | Lost & Found | `find` |
| 6 | Take Out the Trash | `rm`, `*` wildcards |
| 7 | Access Denied | `chmod`, `ls -l` |
| 8 | The Broken Amulet | `cat file1 file2` |
| 9 | The Reactor Core | `find` + `chmod` + `base64 -d` |

## How it works (for the curious)

- `./sq reset` regenerates everything under `world/` with a fresh random token,
  so flags differ every playthrough — you can't just memorize them.
- Answers are **not** stored in the script in plaintext; `.sq_keys` holds only
  SHA-256 hashes, and `submit` hashes your guess to compare.
- Your progress lives in `.sq_state`.

Flags follow the format `SQ{...}`. Copy the whole thing, braces included.

Have fun, engineer. 🛠️
