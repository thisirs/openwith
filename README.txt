Openwith is a simple but very useful package to make Emacs associate various file types with external applications.  For example, Emacs can open PDFs, but you may want to open them with a dedicated PDF viewer instead.  With openwith, you can do this seamlessly when you use C-x C-f.  It also works with recentf and ido.

Here's an example configuration for your init.el:

    (when (require 'openwith nil 'noerror)
      (setq openwith-associations
            (list
             (list (openwith-make-extension-regexp
                    '("mpg" "mpeg" "mp3" "mp4"
                      "avi" "wmv" "wav" "mov" "flv"
                      "ogm" "ogg" "mkv"))
                   "vlc"
                   '(file))
             (list (openwith-make-extension-regexp
                    '("xbm" "pbm" "pgm" "ppm" "pnm"
                      "png" "gif" "bmp" "tif" "jpeg" "jpg"))
                   "geeqie"
                   '(file))
             (list (openwith-make-extension-regexp
                    '("doc" "xls" "ppt" "odt" "ods" "odg" "odp"))
                   "libreoffice"
                   '(file))
             '("\\.lyx" "lyx" (file))
             '("\\.chm" "kchmviewer" (file))
             (list (openwith-make-extension-regexp
                    '("pdf" "ps" "ps.gz" "dvi"))
                   "okular"
                   '(file))
             ))
      (openwith-mode 1))

See also http://www.emacswiki.org/emacs/OpenWith.

I have attempted to contact the author, but he hasn't responded.
