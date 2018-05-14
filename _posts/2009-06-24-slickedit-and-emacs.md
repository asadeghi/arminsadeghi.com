---
id: 15
title: SlickEdit and Emacs
date: 2009-06-24T14:29:49+00:00
author: armin
layout: post
guid: http://www.arminsadeghi.com/2009/06/slickedit-and-emacs/
permalink: /slickedit-and-emacs/
categories:
  - General
---
<!-- google_ad_section_start -->

Everyone has their favorite code editor. Different editors suit different needs, but I personally like two of them currently: [SlickEdit](http://www.slickedit.com/) and [Emacs](http://www.gnu.org/software/emacs/). Both are extremely flexible and efficient editors offering:

  * Column editing. If you aren't aware of this, you should look into it now. [Here is a good column editing video](http://www.vimeo.com/1168225?pg=embed&sec=1168225). 
  * Macro recording and playback.
  * Tagging.
  * Efficient code viewing/editing (side by side pages, etc), and editing. I.e. mostly keyboard driven and customizable. 
  * Integration with debuggers.
  * Support for many programming languages.

The big difference between SlickEdit and Emacs is that SlickEdit is commercial software and Emacs is open source. If you are on a budget Emacs is a good solution and also lets you run the editor from a console (emacs -nw), which is handy.

<!--more-->

If you go down the Emacs road you will need a little configuration. Below is a minimal set of settings I often use. Pick and choose, and then place these in your .emacs file (in your home directory on Linux, or in your Application Data folder on Windows).
  
```
;; ~/.emacs
;;

(custom-set-variables
  ;; custom-set-variables was added by Custom.
  ;; If you edit it by hand, you could mess it up, so be careful.
  ;; Your init file should contain only one such instance.
  ;; If there is more than one, they won&#039;t work right.
 &#039;(inhibit-startup-screen t)
 &#039;(tool-bar-mode nil)
 &#039;(transient-mark-mode t))

;; Resize window on load
(setq initial-frame-alist
      `((left . 0) (top . 0)
        (width . 100) (height . 60)))

;; Common User Access - Ctrl-X/C/V
(cua-mode)

;; In every buffer, the line which contains the cursor will be fully
;; highlighted
(global-hl-line-mode 1)

;; Prevent Emacs from making backup files
(setq make-backup-files nil) 

;; for emacs to insert spaces instead of tab chars
(setq-default indent-tabs-mode nil);

;; bind macro recording
(global-set-key [f7] &#039;start-kbd-macro)
(global-set-key [f8] &#039;end-kbd-macro)
(global-set-key [f9] &#039;call-last-kbd-macro)

;; scroll two line at a time with mouse scroll wheel, no acceleration
(setq mouse-wheel-scroll-amount &#039;(2 ((shift) . 2) ((control) . nil)))
(setq mouse-wheel-progressive-speed nil)

;; column numbers
(setq column-number-mode t)

;; format title bar to show full path of current file
(setq-default frame-title-format
   (list &#039;((buffer-file-name " %f"
             (dired-directory
              dired-directory
              (revert-buffer-function " %b"
              ("%b - Dir:  " default-directory))))))) 

;; allow use of the x-windows clipboard
(setq x-select-enable-clipboard t)
(setq interprogram-paste-function &#039;x-cut-buffer-or-selection-value)

;; ruby                                                                         
;; based on http://www.rubygarden.org/Ruby
;; /page/show/InstallingEmacsExtensions  
;;                                                                              
(add-to-list &#039;load-path "~/.emacs.d/site-lisp/ruby")

 (autoload &#039;ruby-mode "ruby-mode"
     "Mode for editing ruby source files")
 (add-to-list &#039;auto-mode-alist &#039;("\\.rb$" . ruby-mode))
 (add-to-list &#039;auto-mode-alist &#039;("\\.rhtml$" . html-mode))
 (add-to-list &#039;interpreter-mode-alist &#039;("ruby" . ruby-mode))
 (autoload &#039;run-ruby "inf-ruby"
     "Run an inferior Ruby process")
 (autoload &#039;inf-ruby-keys "inf-ruby"
     "Set local key defs for inf-ruby in ruby-mode")
 (add-hook &#039;ruby-mode-hook
     &#039;(lambda ()
         (inf-ruby-keys)))
 ;; If you have Emacs 19.2x or older, use rubydb2x                              
 (autoload &#039;rubydb "rubydb3x" "Ruby debugger" t)
 ;; uncomment the next line if you want syntax highlighting                     
 (add-hook &#039;ruby-mode-hook &#039;turn-on-font-lock)
``` 

<!-- google_ad_section_end -->
