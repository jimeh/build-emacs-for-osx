# build-emacs-for-osx

Use this script at your own risk. It currently works for me on my own machine,
which as of writing runs:

* Mac OS X Lion 10.7.2 (11C74)
* Xcode 4.2 (4D199)

Your luck might vary. Do note that it does not build a universal application.
The CPU architecture of the built application will be that of the machine it
was built on.

## Why?

I've been using [Homebrew](http://mxcl.github.com/homebrew/) the past few
months to build from HEAD. Homebrew comes with the [ns-toogle-fullscreen][fs]
and [sRGB][] patches which I use.

Homebrew does not build a self-contained application though, which caused
issues for me when I needed to rollback to a specific build. I found the
easiest way to build a completely self-contained Emacs.app nightly from a
specific date with custom patches was to do it manually.

So I decided to quickly hack together a script to automate that manual
process. The code is a horrible hack, but it (seemingly) works as I'm writing
this in Emacs built with it.

## Internals

I decided to pull Emacs' source from the GitHub mirror rather than the
official Bzr repo cause I'm not familiar with Bzr, and GitHub lets you easily
download tarballs of any commit.

The only option passed in `./configure` is `--with-ns`, meaning the resulting
application only supports the CPU architecture of the system is was built on.
There might be more side-effects to.


[fs]: https://gist.github.com/1012927
[srgb]: http://debbugs.gnu.org/cgi/bugreport.cgi?bug=8402