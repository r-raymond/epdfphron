# epdfphron
Epdfphron - The shepherd of your open pdfs

Have you ever worried to restart your computer because of the currently open
documents? Fear no longer, for Epdfphron is here!

Epdfphron is a small haskell script that manages pdf (djvu, ...) sessions. It

 * Shows all currently open pdfs. See subcommand `status`.
 * Saves all currently open pdfs to a session file. Also makes backups of
   files that reside in the temp directory (E.g. if you open a pdf directly
   after downloading without saving it). See subcommand `save`
 * Shows all saved sessions. See subcommand `show`
 * Loads a saved session. See subcommand `load`. Note that for this to work, you
   need to specify your preferred pdf viewer.

## How to install

After installing `stack` you can call this script like any other shell script (tested with `lts-9.1`).

```
> chmod +x epdfphron
> ./epdfphron
Epdfphron v. 0.1.1 - the shepherd of your open pdfs
(C) 2017 Robin Raymond; licensed under GPL 3

Usage: epdfphron [-v|--verbose] (status | save | load | show)

Available options:
  -h,--help                Show this help text
  -v,--verbose             display verbose output

Available commands:
  status                   display information about current session
  save                     save the current session to the database
  load                     restore a session from the database
  show                     show saved sessions
```

## The script executes very sluggishly

Since this is interpreted haskell, the startup time of the script might feel
quite slow. To combat this, you can compile the script as follows.

```
> cp epdfphron Epdfphron.hs
> stack ghc Epdfphron.hs
[1 of 1] Compiling Main             ( Epfphron.hs, Epfphron.o )
Linking Epfphron ...
> file Epdfphron
Epfphron: ELF 64-bit LSB executable, x86-64, version 1 (SYSV), dynamically linked, ...
> ./Epdfphron
Epdfphron v. 0.1.1 - the shepherd of your open pdfs
...
```

## Sample Session

```
> ./epdfphron status

Found 2 running instance(s) of document viewers.

The following 32 open document(s) were found:
  * /home/user/lat/phd/root.pdf
  * /tmp/mozilla_user0/1708.05009-1.pdf
  .
  .
  .

The following 1 open document(s) are temporary:
  * /tmp/mozilla_user0/1708.05009-1.pdf
```

```
> ./epdfphron save -n "test-session" --verbose
Rescuing /tmp/mozilla_user0/1708.05009-1.pdf to
/home/user/.local/share/epdfphron/rescue/test-session/1708-s2R4NAV-Yt_b1xE8i9QATw==.pdf
Saved 2 files in /home/user/.local/share/epdfphron/sessions/test-session
```


```
> ./epdfphron show

Found 1 session(s)
  * test-session
```

## License

(C) 2017 Robin Raymond
Licensed under GPL-3
