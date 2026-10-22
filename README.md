# SSI Shell

`ssi` is a small interactive shell written in C. It displays a prompt with the username, hostname, and current working directory; runs external commands; supports changing directories; and can launch and list background jobs.

## Requirements

-   A Unix-like system
-   A C compiler
-   GNU Readline development headers and library
-   `make`

## Build

From the project directory:

```sh
make
```

This builds the `ssi` executable and links it with Readline.

To remove the executable and object file:

```sh
make clean
```

## Run

```sh
./ssi
```

Type `exit` to leave the shell.

## Built-in commands

-   `cd PATH` — change the shell’s working directory. A path beginning with `~` is expanded using `$ HOME`.
-   `bg COMMAND [ARGS...]` — start a command as a background job.
-   `bg list` — check and list background jobs currently tracked by the shell.
-   `exit` — quit.

Other commands are launched as external programs using `execvp`. Press `Ctrl+C` to return to the prompt.

## Notes and limitations

-   Command input is split on spaces; quoting, escaping, pipes, redirection, and variable expansion are not implemented.
-   Background jobs are checked for completion after foreground commands and when `bg list` is used.
-   The shell tracks background jobs only for the lifetime of the shell process.
-   The implementation expects a logged-in terminal session and a usable `$ HOME` for `~` expansion.