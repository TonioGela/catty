# Catty

Let's collect resources as a first thing:

- [Scurses](https://github.com/Tenchi2xh/Scurses) and [jline3](https://github.com/jline/jline3) are good places where to find informations
- [Ansi Escape Code](https://en.wikipedia.org/wiki/ANSI_escape_code) from wikipedia.
- Eugene wrote an interesting post about console games/escape codes: http://eed3si9n.com/console-games-in-scala
- We'll need to investigate about what a tty exactly is, if there are terminal emulators that are not ttys, which and
where escape codes are supported, etc...
- We need to make it work on Windows too
- We need to figure out how to make it work via node too, possibly via: https://nodejs.org/api/tty.html
- It seems like we have two basic problems. Using ansi escape sequences, which should work out of the box for all
platforms, and setting the terminal mode, which will vary a lot depending on the platform.