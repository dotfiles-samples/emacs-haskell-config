# emacs-haskell-config (stack-mode version)

A quick and easy pre-configured Emacs for developing with Haskell. You
can use this to try out the Emacs support for Haskell, or use it as a
base or to crib Elisp from, or whatever. The motivating use-case is
that newbies tend to want something that just works that they can
customize later. This aims to be that repo.

At least, an opinionated version of it. Most of it is using my
tooling, so it's very me-ish. I pretty much copied my own Emacs
configuration into a repo.

Dependencies are included or explicitly stated.

### License

This program is free software: you can redistribute it and/or modify
it under the terms of the GNU General Public License as published by
the Free Software Foundation, either version 3 of the License, or
(at your option) any later version.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU General Public License for more details.

You should have received a copy of the GNU General Public License
along with this program. If not, see <http://www.gnu.org/licenses/>.

## Prerequisites

It's easier if you're running Linux or OS X. If you're on Windows,
there is no guarantee whether anything described will work.

You need GHC version 7.8.2, 7.8.3, or 7.8.4. Check that with:

    $ ghc --version
    The Glorious Glasgow Haskell Compilation System, version 7.8.2

You need `stack` installed, fairly recent:

    $ stack --version
    Version 0.1.2.7, Git revision 68e194622b3c52be3d386b2e9b807ec1ac288828

## Download

Run the following to clone this repo and its dependencies:

    $ git clone https://github.com/chrisdone/emacs-haskell-config.git -b stack-mode --recursive

That should take about a minute or two.

## Build

Build the haskell-mode Elisp:

    $ cd packages/haskell-mode/
    $ make compile haskell-mode-autoloads.el

## Running

In the repo directory, run this:

    $ emacs -Q -l init.el

The `-Q` is short for "quick" and means it will not use any existing
Emacs configuration that you already have.

The `-l init.el` will load this repo's init configuration.

If you decide you want to use this configuration as-is or as a base,
you can put the following in your `~/.emacs` file:

    (load "/path/to/emacs-haskell-config/init.el")

Then run Emacs from the terminal as simply:

    $ emacs & disown

You need to run it from the terminal to ensure that your `PATH` is
configured, otherwise it's more difficult to setup.

## Using

You need a Stack project. Open a .hs file.

## Type checking

Type checking is done through flycheck, it should happen
automatically.

## Type information

Once you've loaded your module in, you can go to any identifier and
run `C-c C-t`. E.g. if you go to `n` and run `C-c C-t` you'll see this
in the minibuffer:

``` haskell
n :: Integer
```

If you select the `n - 1` and hit `C-c C-t` you'll see this:

``` haskell
n - 1 :: Integer
```

## Go to definition

If you go to the `n` in `n - 2` and run `M-.` it will jump to the `n`
in `fib n`.
