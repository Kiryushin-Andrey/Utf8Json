# The Byte Order Mark of Zorro

Once upon a time, in a quiet corner of a production server, there lived a JSON parser named Reginald.

Reginald was very proud. He could chew through gigabytes of UTF-8 without breaking a sweat. "Zero allocations!" he would boast at parties, mostly to a confused garbage collector who had nothing to do and was starting to feel unemployed.

One Monday morning, a mysterious payload arrived. It began with three invisible bytes: `EF BB BF`.

"Who goes there?" cried Reginald.

The bytes said nothing. They were invisible. That was the whole point.

"Unexpected token at position 0!" Reginald screamed, and threw an exception so dramatic that the logging service wept.

The developer, Dave, stared at the error. The JSON looked perfect. He copied it into his editor. Perfect. He pasted it into a validator. Perfect. He read it out loud to his rubber duck. The duck, as always, remained noncommittal.

"It's `{ "name": "Dave" }`," said Dave. "What's wrong with it?"

"NOTHING," wailed Reginald. "IT'S HAUNTED."

Three hours later, Dave discovered the culprit: a colleague had saved the file in Notepad. Notepad, that old prankster, had quietly slipped a Byte Order Mark in front of it, like a tiny, invisible top hat.

Dave added a three-byte check. Reginald now greets every payload with a polite nod to the mysterious masked bytes, and quietly steps over them.

The garbage collector is still unemployed. Dave still talks to the duck. And somewhere, Notepad is chuckling.

**The moral:** Always trust your parser, but verify your bytes. And never, ever trust a text editor that wears a hat.

*The End.* 🎩
