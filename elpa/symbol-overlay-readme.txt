Highlighting symbols with overlays while providing a keymap for various
operations about highlighted symbols.  It was originally inspired by the
package `highlight-symbol'.  The fundamental difference is that in
`symbol-overlay' every symbol is highlighted by the Emacs built-in function
`overlay-put' rather than the `font-lock' mechanism used in
`highlight-symbol'.

Advantages

When highlighting symbols in a buffer of regular size and language,
`overlay-put' behaves as fast as the traditional Highlighting method
`font-lock'.  However, for a buffer of major-mode with complicated keywords
syntax, like haskell-mode, `font-lock' is quite slow even the buffer is less
than 100 lines.  Besides, when counting the number of highlighted
occurrences, `highlight-symbol' will call the function `how-many' twice,
which could also result in an unpleasant delay in a large buffer.  Those
problems don't exist in `symbol-overlay'.

When putting overlays on symbols, an auto-activated overlay-inside keymap
will enable you to call various useful commands with a single keystroke.

Toggle all overlays of symbol at point: `symbol-overlay-put'
Copy symbol at point: `symbol-overlay-save-symbol'
Jump back to the position before a recent jump: `symbol-overlay-echo-mark'
Remove all highlighted symbols in the buffer: `symbol-overlay-remove-all'
Jump between locations of symbol at point: `symbol-overlay-jump-next' &
`symbol-overlay-jump-prev'
Jump to the definition of symbol at point: `symbol-overlay-jump-to-definition'
Switch to the closest symbol highlighted nearby:
`symbol-overlay-switch-forward' & `symbol-overlay-switch-backward'
Toggle overlays to be showed in buffer or only in scope:
`symbol-overlay-toggle-in-scope'
Query replace symbol at point: `symbol-overlay-query-replace'
Rename symbol at point on all its occurrences: `symbol-overlay-rename'

Usage

To use `symbol-overlay' in your Emacs, you need only to bind three keys:
(require 'symbol-overlay)
(global-set-key (kbd "M-i") 'symbol-overlay-put)
(global-set-key (kbd "M-u") 'symbol-overlay-switch-backward)
(global-set-key (kbd "M-o") 'symbol-overlay-switch-forward)

Default key-bindings are defined in `symbol-overlay-map'.
You can re-bind the commands to any keys you prefer by simply writing
(define-key symbol-overlay-map (kbd "your-prefer-key") 'any-command)
