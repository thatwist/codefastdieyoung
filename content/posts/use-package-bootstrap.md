+++
title = "use-package bootstrap"
author = ["Yuri Ostapchuk"]
date = 2022-02-07T20:37:00-06:00
lastmod = 2022-02-07T20:37:11-06:00
categories = ["emacs"]
draft = false
weight = 2002
[menu.main]
  weight = 2002
  identifier = "use-package-bootstrap"
+++

Most of the guides on `use-package` describe how to start from scratch. If you started your config by copy-pasting various elisp snippets (like I did) you may want to have something like a recipe for how such snippets should be translated into corresponding use-package instructions.
Here are some guidelines from my own experience to "bootstrap" your usage of use-package.
(For the reference - you can find my config [here](https://github.com/thatwist/.emacs.d/blob/master/config.org))

1.  Right now your config is more or less "linear" or imperative so to speak, while use-package will make it more "declarative".
    The simplest would be to wrap all the code related to a specific package into `:config` section of use-package declaration.
    If there is anything in your config that absolutely must be done before `(require '<pkg>)` (this is rare) - you can put that into `:init` section.

2.  Use `:demand t` everywhere at first - lazy loading and dependency handling in use-package can be a little bit of a headache (at first).
    I advise you to be explicit with `:ensure t` in every definition as well (there is an option to enable it globally, but then you may regret later when using something like :quelpa etc.).

3.  So now, this is a wrapper for a configuration for every package:

    ```emacs-lisp
       (use-package <pkg>
         :demand t :ensure t
         :config
         <move all your configs related to <pkg> here>
         )
    ```

4.  There is one trick (not the only) to configure built-in packages with use-package as well - just omit `:ensure t` and use the name of the built-in package (or feature to be more precise, see below), e.g. this is how you can group your `desktop`-related code:

    ```emacs-lisp
       (use-package desktop
         :demand t
         :custom
         ((desktop-files-not-to-save "\\(\\=/[^/:]*:\\|(ftp)\\'\\)")
          (desktop-load-locked-desktop t)
          (desktop-buffers-not-to-save ".*")))
    ```

    This is the way to configure `org` and `org-agenda`. There is some confusion in use-package between package-name and feature-name - actually, name that you put right after `use-package` is the name of the `feature` (most of the time the main feature of the package has the same name), to know exactly the name of the feature you can lookup `(provide '<pkg>)` statements in the code of the package. This is sometimes required to know the name of the built-int features (packages) - e.g. `org` and `org-agenda` are separate features, you can group configs into different use-package declarations.

5.  Use `pp-macroexpand-last-sexp` - this will help you a lot at times when you're confused (especially with lazy loading later) - you should understand that `use-package` just generates plain elisp code, no magic whatsoever.

6.  At this point you are "bootstrapped" so you can do next few steps in any order - this will transition you to doing things more in "use-package"-way.

7.  Use `:custom`, `:custom-face`. This one is easy, most of the `setq` declarations you should probably move into `:custom` (just remove `setq` part) - see the source code of the variable if it's actually a `defcustom`.

8.  Use `:hook`. Whenever you have `(add-hook some-hook (lambda...)` move that into `:hook` removing `-hook` part of the `some-hook` name - e.g. `:hook (some . (lambda))`.

9.  Use :bind. Transform your `global-set-key` into `:bind` and your `define-key` into `:bind (:map ...)`. You will have to keep your `evil-define-key` definitions in `:config` though (or use some 'general' extension).

10. Next step - minor transitions to using `:mode`, `:magic`, maybe `bind-keymap`. Use `:if`, `:unless`  if you have something like `(when (eq system-type 'windows-nt)...)`.

11. As a last big move - handle order of loading and execution and migrate your `with-eval-after-load` statements into using `:after` (removing `:demand t` where appropriate). This is a big step as it will remove dependency on the global order of `use-package` declarations (and make your config really declarative).

    The `:after` might be confusing (look pp-macroexpand-last-sexp if you are confused) but equivalent for `with-eval-after-load <pkg2>` would be combination of `(use-package <pkg1> :after <pkg2> :demand t :config ...)`, if you omit `:demand` the execution won't be triggered eagerly after loading `<pkg2>` as use-package will wrap configuration into another `eval-after-load <pkg1>`. Anyway, once you get here you will learn how to debug and figure it out.

    You may want to use `:defer` in some places but I warn you to use `:defer` as a dependency mechanism - use it only to reduce init time and defer loading a fraction of seconds later (this will still block UI anyway but feels smoother) for some packages e.g. `evil`.

    Also at this point it will make more sense to move all functions and variables definitions (defun and defvar) into `:init` block.

    You won't be able to completely get rid of using `with-eval-after-load` as sometimes it is easier to group some configuration under it,

12. Return to use-package documentation (C-h f 'use-package') from time to time until understanding settles in your brain.

Good luck!

[//]: # "Exported with love from a post written in Org mode"
[//]: # "- https://github.com/kaushalmodi/ox-hugo"