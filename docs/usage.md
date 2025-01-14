# Keepmenu Usage

[Installation](install.md) - [Configuration](configure.md)

## Basic

- [Configure](docs/configure.md) config.ini as desired.
- Run `keepmenu` or bind to keystroke combination.
- Enter database/keyfile paths on first run if not already configured in config.ini.
- Start typing to match entries, `Enter` to type with default autotype sequence
  `{USERNAME}{TAB}{PASSWORD}{ENTER}`.

## CLI Options

`keepmenu [-h] [-a AUTOTYPE] [-d DATABASE] [-k KEY_FILE]`

--help, -h Output a usage message and exit.

-a AUTOTYPE, --autotype AUTOTYPE Override autotype sequence in config.ini

-d DATABASE, --database DATABASE File path to a database to open, skipping the database selection menu

-k KEYFILE, --keyfile KEY_FILE File path of the keyfile needed to open the database specified by --database/-d

## Features

- *General features*
    - Open .kdbx databases, not .kdb.
    - Switch databases on the fly.
    - Alternate keyboard languages and layouts supported via xdotool or ydotool (for
      Wayland)
    - Display of expiring/expired passwords and shows the expiration time where set
    - Add, edit and type TOTP codes. RFC 6238, Steam and custom settings are supported.
- *Type entries*
    - Auto-type username and/or password on selection. No clipboard copy/paste
      involved. Use xdotool or ydotool for non-U.S. English keyboard layout.
    - Use a custom [Keepass 2.x style auto-type sequence][1] if you have one defined
      (except for character repetition and the 'special commands'). Set it per entry
      or set a global default. Disable autotype for an entry, if desired.
    - Auto-type custom attributes by hitting `Enter` on the desired attribute or
      by using the `{S:<ATTR_NAME>}` action code in your auto-type sequence.
    - Select any single field and have it typed into the active window. Notes fields
      can be viewed line-by-line and the selected line will be typed when
      selected.
    - `Enter` to open the URL in the default web browser from the View/Type menu.
- *Edit*
    - Edit entry title, username, URL, attributes, and password (manually typed or auto-generate)
    - Edit notes using terminal or gui editor (set in config.ini, or uses $EDITOR)
    - Add and Delete entries
    - Rename, move, delete and add groups
- *Configure* ([docs](configure.md))
    - Prompts for and saves initial database and keyfile locations if config file
      isn't setup before first run.
    - Set multiple databases and keyfiles in the config file.
    - Hide selected groups from the default and 'View/Type Individual entries' views.
    - Keepmenu runs in the background after initial startup and will retain the
      entered passphrase for `pw_cache_period_min` minutes after the last activity.
    - Configure the characters and groups of characters used during password
      generation in the config file (see config.ini.example for instructions).
      Multiple character sets can be selected on the fly when using Rofi if the
      `-multi-select` option is passed via `dmenu_command`.
    - Optional Pinentry support for secure passphrase entry.
    - [Keepass field references][2] are supported.

[1]: https://keepass.info/help/base/autotype.html#autoseq "Keepass 2.x codes"
[2]: https://keepass.info/help/base/fieldrefs.html "Keepass field references"
