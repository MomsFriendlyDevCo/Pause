@MomsFriendlyDevCo/Pause
=======================
A Command Line Interface (CLI) to, well, *pause* until conditions are satisified and then either run another command or exit with a zero exit code.

```
Usage: pause [options] ["for"|"until"] [conditions...] ["then"] [--] [command]

Pause for one or more conditions then either do-a-thing or return a zero exit
code

Options:
  --loop, --repeat <n>      Repeat N number of times before exiting
  --invert, -v              Invert the match condition
  --timeout <timestring>    Give up and exit after the given time period
  --timeout-as <exit-code>  Raise the given exit code when timing out (default:
                            1)
  --quiet, -q               Suppress the condition progress display
  -h, --help                display help for command

Notes:
  * CONDITION: [timestring] - any valid, parsable timestring compatible expression to denote pause/waiting for a time
  * CONDITION: [time] - pause until the given, relative or parsable time
  * CONDITION: [pid] <"exits"|"fails"|"stops"> - pause until the PID to exit (correctly | non-zero exit|quits for any reason)
  * CONDITION: <"path"|"for changes to"> [path] ["changes"|"to change"]
  * CONDITION: <"load"> <"<"|"<="|">="|"above"|"below"> [number]
  * OPERAND: <a> AND <b>
  * OPERAND: <a> OR <b>

Examples:

  # Pause for one hour then exit
  pause 1h

  # Pause until PID 123 exits with a positive exit code
  pause until 123 exits

  # Pause until the next time 3pm occurs
  pause until 3pm

  # Pause until Tuesday occurs
  pause until tuesday

  # Pause for 1 hour OR PID 123 exits with a non-zero code
  pause for 1h OR 123 fails
```
