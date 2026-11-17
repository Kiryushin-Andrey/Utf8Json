# The Invalid Byte

Marta had maintained the parser for six years, and in all that time it had never once failed on valid input.

That was the problem. The input that night was not valid.

It arrived at 2:14 a.m. as a bug report with no title and no reproduction steps, only an attachment: `payload.json`, 4 bytes long.

```
0xC0 0xAF 0xFF 0x00
```

She knew those bytes. `0xC0 0xAF` was an overlong encoding of a slash, the classic trick for slipping past a path filter. `0xFF` could never appear in well-formed UTF-8. Nothing in the spec allowed it.

She fed the file to the deserializer, expecting the usual `JsonParsingException` and a tidy offset.

The parser returned an object.

```
{ "name": "Marta", "last_seen": "02:14" }
```

She had not written either of those fields anywhere.

She checked the logs. The parser had logged no warning. It had consumed four bytes and produced twenty-six characters of her own life.

Marta unplugged the network cable, which was foolish, because nothing had come in over the network. The file had been in her repository the whole time. She ran `git log` on it. The first commit was dated six years ago, the week she wrote the first line of the library, and the author field was blank.

She ran the parser again, out of the stubborn curiosity that had made her a good engineer.

```
{ "name": "Marta", "last_seen": "02:15", "location": "the chair by the window" }
```

Behind her, the chair by the window creaked.

She did not turn around. She opened the source and searched for the function that was producing the output. Her fingers knew the codebase. There it was, in `ReadString`, in code she had never written:

```csharp
// TODO: handle what comes after the last valid byte
```

She had left a thousand TODOs in six years, but never that one. The blame view showed her own name and her own email, timestamped four seconds from now.

The timestamp ticked over.

The next line of the file began to write itself, one character at a time, in her own typing rhythm, with the pause she always took before the closing brace.

```
{ "name": "Marta", "last_seen": "02:16", "status": "
```

The cursor blinked. She understood then what a parser does when it reaches the end of the input and the string is still open: it waits. It keeps reading. It reads whatever comes next.

Behind her, something finished clearing its throat.

She never did close the quote.

In the morning her coworkers found the laptop still open and the chair by the window empty. The only thing on the screen was one failing test, the first red test in six years, and the message beneath it read:

```
Unexpected end of input. Expected: '"'
```

The build is still broken. Nobody has dared to fix it, and every night at 2:14 someone's `payload.json` gets a little bit longer.
