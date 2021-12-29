+++
title = "Advice for emacs newcomers"
author = ["Yuri Ostapchuk"]
date = 2021-12-29T00:55:00-06:00
lastmod = 2021-12-29T00:55:03-06:00
categories = ["emacs"]
draft = false
weight = 2001
[menu.main]
  weight = 2001
  identifier = "advice-for-emacs-newcomers"
+++

Path of Emacs newcomer is long and full of frustration at times. Very often one may run out of will or perseverance, and sometimes even give up and stop trying..

As someone who once decided to push personal productivity to the limit, and had motivation and need to use Emacs for everything from coding and note-taking
to managing whole life in plain-text, and as someone who tried and failed multiple times, I would like to share a short list of tips that I would be happy to knew back in the days:

1.  You will have to borrow ELisp snippets even though you may not understand them - this is the only way to get to the decent experience from vanilla emacs.
    Use use-package and learn how it works - I suggest enabling :demand for all packages for beginning.
    Do not overwhelm your config - the time will come you will have to understand every of those snippets and structure them.

2.  First thing which worth precise learning is how to get help within emacs - all things starting C-h... Especially help on bindings/functions. Reading info manuals is useful as well but you may find yourself googling documentation anyway. You may also try installing help-fns+, helpful.

3.  Do not try to learn ELisp from scratch - do it gradually, build environment that is pleasing to work in then you will be more motivated to learn how to change things.

4.  Make it good-looking - this is a big deal, pick some theme, use doom-modeline, all-the-icons.

5.  Slowly build your own bindings - I suggest you to use hydra, you can borrow some already built hydras but try not to overwhelm and come up with your own bindings that will stick much better to you. Use which-key - this will be game changer at the beginning, especially with some completion engine - ivy or helm, I suggest ivy. You may later review some ivy plugins for other packages (projectile etc.)

6.  i3wm is great, use evil-leader + space - as central dispatcher key for everything.

7.  Try to adopt lsp-mode if you do software development, as well as company, magit (the best git client ever, believe me), projectile (not only for swdev but for navigation in general), smartparens, yasnippet, treemacs (through the time I got used to not having dir-tree on the left as it is in any IDE - and that's freed up a big part of my screen to something more useful, but sometimes treemacs is still helpful), flycheck, eshell.

8.  You can later review some other evil-\* packages available in melpa as well as org-\*. Get comfortable using list-packages interface.

9.  You may give up at some point (temporarily) - try to keep using Emacs at least for note-taking - org-mode headlines and lists in a single org file.


## Good luck! {#good-luck}

[//]: # "Exported with love from a post written in Org mode"
[//]: # "- https://github.com/kaushalmodi/ox-hugo"