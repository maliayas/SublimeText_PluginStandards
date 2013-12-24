# Sublime Text Plugin Standards

## Status Bar Items

Status bar pattern:

    [item set by a plugin, ]... Line 7, Column 48
    --------------------------- -----------------
                 |                      |
                 |                      Reserved for Sublime Text. These
                 |                      will always appear _here_.
                 |
                 Items set by plugins.

Some plugins may want to set their status bar item at the beginning of the bar and some not. With the standards defined in this document, it is aimed to separate the plugin space into 2 groups:

    [items set by plugins]
    ---------- -----------
        |           |
        |           End group
        |
        Start group

The guideline for the item key:

    view.set_status("(.0.plugin_name", "text")
                     - - -----------    ----
                     | |      |           |
                     | |      |           Status bar item text.
                     | |      |
                     | |      Snake-case namespace of the plugin.
                     | |
                     | The index for the status bar item in its group (start or
                     | end group). It must be an integer between 0 and 10.
                     | `0` means it will appear at the beginning.
                     | `10` means it will appear at the end.
                     | There may be multiple plugins that want to use the same
                     | index. In this case, `plugin_name` will decide the
                     | final order based on alphabetical order.
                     |
                     This can take 2 values:
                     `(`: Status bar item will be in the "start group"
                     `}`: Status bar item will be in the "end group"
                     The idea behind this: in an alphabetical order, `(` comes
                     before alphanumeric characters and `}` comes after alphanumeric
                     characters.

## License

This document is released under the [MIT License][mit].

[mit]:         http://www.opensource.org/licenses/MIT
