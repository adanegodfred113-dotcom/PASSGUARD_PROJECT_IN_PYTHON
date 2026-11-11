# PassGuard - A Password Security Toolkit

A desktop app built with Python and Tkinter that checks how strong a password is, generates strong passwords, and hashes passwords safely.

Built for Lab 1 (Python, Level 200) at Ghana Communication Technology University (GCTU), Faculty of Engineering.


## Features

1. **Live strength checker**: the strength bar, label and tips update every time you press a key.
2. **Show/hide password**: a checkbox to reveal what you typed.
3. **Password generator**: creates a random password (8 to 32 characters) that is always rated STRONG, and copies it to the clipboard.
4. **SHA-256 hashing**: turns any password into a hash with one click.
5. **Check history**: every saved check is logged with the time, part of the hash, the score and the label. The real password is never stored.
6. **Common password detection**: passwords like `123456` or `password` are rated VERY WEAK straight away.
7. **Bonus (Extension challenge 1)**: a Clear history button that asks "Are you sure?" and then empties the log file and the list box.

## How the score works

The score is out of 6.

| Rule | Points |
|---|---|
| 12 or more characters | 2 |
| 8 to 11 characters | 1 |
| Has an uppercase letter | 1 |
| Has a lowercase letter | 1 |
| Has a number | 1 |
| Has a symbol | 1 |

| Score | Label |
|---|---|
| 0 to 2 | WEAK |
| 3 to 4 | MEDIUM |
| 5 to 6 | STRONG |

Any password found in the common passwords list scores 0 and is labelled VERY WEAK.

## Requirements
- pycharm 2026.2.3 or newer
- Python 3.8 or newer
- Tkinter (comes with the standard Python installer on Windows and macOS)

No extra packages are needed. The app only uses the standard library: `string`, `secrets`, `hashlib`, `datetime` and `tkinter`.

## How to run

```
Just run it in pycharm the app will open
```

## How it works

The code is split into three parts:

- **Logic functions** (`check_strength`, `generate_password`, `hash_password`, `save_to_log`, `load_log`): no GUI code, so they are easy to test.
- **Event handlers** (`live_check`, `on_check`, `on_generate`, `on_copy`, `on_hash`, `on_clear`): these run when the user types or clicks.
- **Window building**: creates the Tkinter window with three sections (check, generate, history).

The app is event-driven. For example, `password_entry.bind("<KeyRelease>", live_check)` runs the strength check every time a key is released, and `root.mainloop()` keeps the window waiting for the next event.

## Security notes

- Passwords are never written to disk. The log (`passguard_log.txt`) only keeps the first 10 characters of the SHA-256 hash.
- Generated passwords use the `secrets` module, which is designed for security (unlike `random`).
- SHA-256 is used here to learn the idea of hashing. Real systems should also use a salt and a slow hashing method such as bcrypt or Argon2.

## Author

Adane Godfred Amofah
BSc Computer Engineering, Ghana Communication Technology University (GCTU)
Index No: 2526404689
