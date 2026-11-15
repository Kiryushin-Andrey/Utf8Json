# The Last Byte

Mara took the contract because the pay was good and the job was dull: fix a
JSON parser in a server farm outside town. The building had no windows and one
night guard, who never looked up from his crossword.

On the third night, her tests began to fail on an input she hadn't written.

```json
{"name":"Mara","location":"server room 4","behind_you":
```

It was in the log file. The file had no write permissions. She checked the
timestamps. The entry was from tomorrow.

She told herself it was a prank. She grepped the repo for the string. Nothing.
She grepped the disk. One hit, in a file called `unterminated.json`, created
four minutes ago by a user named `mara`.

Her own account. Her own hands, she supposed, though she hadn't touched it.

The parser kept throwing the same error: *unexpected end of input*. Each run,
the log grew by one line. Each line was closer to what she was doing.

`{"name":"Mara","typing":true,"heart_rate":` — and a number, climbing.

`{"name":"Mara","stood_up":true,"light":"flickering","door":` — and the door
behind her, which she had closed, clicked softly open.

She didn't turn around. She opened the log one last time. It read:

```json
{"name":"Mara","looking_at_screen":true,"breathing":
```

The cursor blinked after the colon, waiting for a value. Something behind her
exhaled, slow and close, near her ear.

The parser was only ever missing one thing, she realised: the closing brace.
Something had been writing her story one byte at a time, and it was almost out
of things to say.

Mara reached for the keyboard to type `}` and end it.

Her fingers were already moving. She hadn't decided to. On the screen the
character appeared, and then another, in a rhythm that wasn't hers:

`"stopped"}`

The next morning the guard filled in the last clue of his crossword, locked up,
and found one test still failing in the build. It was a valid file, perfectly
well-formed, and the parser was happy with it at last.
