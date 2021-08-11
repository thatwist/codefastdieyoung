+++
title = "advice for emacs newcomers"
author = ["Yurii Ostapchuk"]
lastmod = 2021-07-23T10:29:14-04:00
categories = ["emacs"]
draft = true
weight = 2003
[menu.main]
  weight = 2003
  identifier = "advice-for-emacs-newcomers"
+++

As someone who once had the same motivation and needs and picked the same route I can give some advice from the experience, at least what worked for me:

-   you will have to borrow elisp snippets even though you may not understand them - this is the only way to get to the decent experience from vanilla emacs. Use use-package and learn how it works - I suggest enabling :demand for all for beginning. But do not overwhelm your config - the time will come you will have to understand every of those snippets and structure them
-   first thing which worth precise learning - is how to get help within emacs - all things starting C-h... Especially help on bindings/functions. Reading info manuals is useful as well but I find myself googling documentation anyway. You may also try installing help-fns+, helpful.
-   do not try to learn elisp from scratch - do it gradually, build environment that is pleasing to work in then you will be more motivated to learn how to change things
-   make it good looking - this is a big deal, pick some theme, use doom-modeline, all-the-icons
-   slowly build your own bindings - I advice using hydras, you can borrow some already built hydras but try not to overwhelm and come up with your own bindings that stick. Use which-key - this will be game changer as the beginning, especially with some completion engine - ivy or helm, I suggest ivy. You may later review some ivy plugins for other packages (projectile etc.)
-   i3wm is great, use evil-leader + space - as central dispatcher key for everything
-   try to adopt lsp-mode for sw dev, as well as company, magit (the best git client ever, believe me), projectile (not only for swdev but for navigation in general), smartparens, yasnippet, treemacs (through the time I got used to not having dir-tree on the left as it is in any IDE - and that's freed up a big part of my screen to something more useful, but sometimes treemacs is still helpful), flycheck, eshell
-   you can later review some other evil-\* packages available in melpa as well as org-\*. Get comfortable using list-packages interface
-   you may give up at some point (temporarily) - try to keep using emacs at least for some things e.g. org-mode

Good luck!

[//]: # "Exported with love from a post written in Org mode"
[//]: # "- https://github.com/kaushalmodi/ox-hugo"
