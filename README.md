# fpclock 

**fpclock** – a program measuring process execution time

Author: Paul Lipkowski

## Installation

- Required: FreePascal Compiler `fpc` (version 3.0.4 or newer)
- So far works on Linux amd64 and Windows x64 only. 
- Not designed for 32-bit computers.
- If using Linux, then just compile by executing `compile.sh`
    * Then you can install fpclock to `$PATH` using `installBash.sh`
- If using Windows, then compile by executing `compile.bat`
    * The default version of FPC is 3.0.4. If you use the another version of it, then edit the `compile.bat` script and change the setting containing version of FPC (variable `ver`) in order to match your FPC version.

## Usage 
- Syntax: `fpclock 'process' [flags]`
- Available flags:
    *  (no flag) – Show execution time of COMMAND in seconds with precision of 4 digits and feed the line afterwards
    * `-c`, `--cstring` – Input command is C-like formatted (e.g. `'echo \"Hello world\"'`)
    * `-e`, `--env=E` – Choose the environment – `E` is either `cmd` (default) or `powershell` (*Windows only*)
    * `-h`, `--help` – Print help
    * `-n`, `--no-feed-line` – Do not feed the line after having shown output
    * `-p N`, `--prec=N` – Set precision to N digits (default N=4)
    * `-P`, `--prompt` – Prompt for a command from standard input
    * `-u U`, `--units=U` – Set measurement unit to U' (see more Us below)
    * `-w`  , `--wait` – Pause after measuring time (Windows only)
    * `-w N`, `--wait=N` – Wait N milliseconds after measuring time (Windows only, default N=0)
- Available units with their flag values (`U`):
    * days – `d` or `days`
    * minutes – `m`, `mins` or `minutes`
    * seconds – `s`, `secs` or `seconds`
    * milliseconds – `ms`, `milli` or `milliseconds`
    * microseconds – `μs`, `mus`, `micro` or `microseconds`
    * ticks – `ticks`
    * nanoseconds – `ns`, `nano` or `nanoseconds` (The stopwatch is accurate to 1 tick = 100 ns though)
    * clock – `c`, `clock` (output like `00:00:00.0000`, amount of decimal numbers depends on `prec` flag).
- Example: 
    * `fpclock 'ls -l'`
    * `fpclock 'cp ./foo/ ./bar -r' -n`
    * `fpclock 'cp ./foo/ ./bar -r' -n -p 6 -u ms`
    * `fpclock 'cp ./foo/ ./bar -r' -n --prec=6 --units=milliseconds`
