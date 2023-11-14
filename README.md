# Catty

Let's collect resources as a first thing:

- [Scurses](https://github.com/Tenchi2xh/Scurses) and [jline3](https://github.com/jline/jline3) are good places where to find informations
- [Ansi Escape Code](https://en.wikipedia.org/wiki/ANSI_escape_code) from wikipedia.
- Eugene wrote an interesting post about console games/escape codes: http://eed3si9n.com/console-games-in-scala
- We'll need to investigate about what a tty exactly is, if there are terminal emulators that are not ttys, which and
where escape codes are supported, etc...
- It seems like we have two basic problems. Using ansi escape sequences, which should work out of the box for all
platforms, and setting the terminal mode, which will vary a lot depending on the platform.

## Terminal IO Interfaces

Interacting with terminal I/O interfaces will be the part of the project that will need code for different operating
systems.

### Posix (Linux, OSX, etc.)

On _Posix_ systems, terminal input can be interacted with via the C library
[termios.h](https://pubs.opengroup.org/onlinepubs/9699919799/basedefs/termios.h.html). There is already bindings for
this library in [Scala Native](https://github.com/scala-native/scala-native/blob/main/posixlib/src/main/scala/scala/scalanative/posix/termios.scala).
Here is a code sample from Java interacting with _termios.h_ on the [JVM through JNA](https://www.source-code.biz/snippets/java/RawConsoleInput/RawConsoleInput.java).

### Windows

It appears that the library needed to interop with windows terminals is _msvcrt.dll_, based on the previously mentioned
[Java snippet](https://www.source-code.biz/snippets/java/RawConsoleInput/RawConsoleInput.java) that works from the JVM.

### JavaScript

For _Scala.js_ interop, there is a node library for interacting with a console: https://nodejs.org/api/tty.html
