## Installation

1. Copy `resize-font` to where URxvt looks for Perl extensions, e.g:
   `$HOME/.urxvt/ext/`. For the exact path, see the urxvt(1) manual page on
   perl-lib.

2. In your `~/.Xresources` file, add `resize-font` to the
   `urxvt.perl-ext-common` setting so URxvt loads the extension, e.g:

        urxvt.perl-ext-common: default,matcher,resize-font

## Functionality

Two different functionalities are possible with this extension: a
normal font resizing which also alters the text size _and_ window size,
and a static font resizing, which alters _only_ the size size.

In both cases, the terminal window's location will be maintained, with the
x and y coordinates of the terminal's top-left corner being retained. In the
normal font resizing case, the terminal will only grow down and to the right.
In the static font resizing case, the terminal's size will never change: only
the text will change size.

## Configuration

All configuration of `resize-font` is done in `~/.Xresources`.

__Note that if the `urxvt.font` property is not set, this extension assumes
a default of `xft:monospace:size=8`.__

### keybindings

The default keybindings look like this:

    URxvt.keysym.C-0:          resize-font:reset
    URxvt.keysym.C-minus:      resize-font:smaller
    URxvt.keysym.C-equal:      resize-font:bigger
    URxvt.keysym.C-underscore: resize-font:smaller-static
    URxvt.keysym.C-plus:       resize-font:bigger-static
    URxvt.keysym.C-question:   resize-font:show

Keybindings can be modified using the above syntax. For more information on how
to specify keys, see the description of the `keysym` resource in the urxvt(1)
manual page.

### Resize interval

You can also configure the number of steps to take when changing the font size:

    URxvt.resize-font.step: 2

And even fractions like 0.2 are supported.

### Fonts

Default font sizes can be specified in pixels, using the `pixelsize` attribute,
e.g.:

    urxvt.font: xft:Inconsolata:pixelsize=12

Or they can be given in points, using the `size` attribute, e.g.: 

    urxvt.font: xft:Inconsolata:size=12

Fixed fonts are also supported, for example:

    urxvt.font: 7x14

And, finally, XLFD/X logical font description is supported as well, e.g.:

    urxvt.font: -*-inconsolata-medium-*-normal-*-14-*-*-*-*-*-iso8859-*

### Notes

This extension has been tested on FreeBSD-13.3 with i3/X11.
