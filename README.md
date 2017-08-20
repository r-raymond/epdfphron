# epdfphron
Epdfphron - The sheppard of your opened pdfs

Have you ever worried to restart your computer because of the currently opened
documents? Fear no longer, for Epdfphron is here!

Epdfphron is a small haskell script that manages pdf (djvu, ...) sessions. It

 * Shows all currently opened pdf's. See subcommand `status`.
 * Saves all currently opened pdf's to a session file. Also makes backups of
   files that reside in the temp directory (E.g. if you opened a pdf directly
   after downloading without saving it). See subcommand `save`
 * Shows all saved sessions. See subcommand `show`
 * Loads a saved session. See subcommand `load`. Note that for this to work, you
   need to specify your prefered pdf viewer.

(C) 2017 Robin Raymond
Licensed under GPL-3
