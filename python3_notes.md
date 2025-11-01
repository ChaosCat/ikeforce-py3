# Notes on python3

Since the project relied on extremely deprecated python2 behavior
I struggled a bit with the indentation mixes of tabs / spaces / inconsistency of indentation width between blocks

what eventually worked as a reliable way to make any file pass `python3 -m py_compile` was

1. manually replace each `\t` occurence with **exactly 8 spaces**, which worked as a nice catch-all for the project's indentation patterns (or lack thereof)
2. Run `python3 -m lib2to3 <file>` and fix any `ParseError`s that arise manually (usually only got a few). watching out of not messing the logic
3. After errors stop up simply run again `lib2to3` but overwriting with `-w`
4. Then simply running `python3 -m py_compile <file>` and fixing any remaining issues (usually some old python2 syntax stuff or reserved names).


