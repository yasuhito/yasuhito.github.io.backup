---
title: Emacs 24.4 のインストール
date: 2014-10-24 00:24 UTC
tags: emacs, emacs_reboot
---

僕はメインマシンが Mac なので, [Homebrew](http://brew.sh/) でインストー
ルします. `brew install` 一発でインストールできるのでほんと便利. 今回
はとりあえず全部入りでインストールしてみました.

```
% brew install emacs --cocoa --keep-ctags --with-d-bus --with-gnutls --with-imagemagick --with-librsvg --with-mailutils
```

ちなみに, どういうコンパイルオプションがあるかは `brew info emacs` で確認できます.

```
brew info emacs                                                                                                                                         rvm:ruby-2.0.0-p576
emacs: stable 24.4 (bottled), HEAD
https://www.gnu.org/software/emacs/
/usr/local/Cellar/emacs/24.3 (3911 files, 116M)
  Built from source with: --keep-ctags, --cocoa, --srgb
/usr/local/Cellar/emacs/24.4 (3924 files, 118M) *
  Built from source with: --cocoa, --keep-ctags, --with-d-bus, --with-gnutls, --with-imagemagick, --with-librsvg, --with-mailutils
From: https://github.com/Homebrew/homebrew/blob/master/Library/Formula/emacs.rb
==> Dependencies
Build: xz ✔, pkg-config ✔
Optional: d-bus ✔, gnutls ✔, librsvg ✔, imagemagick ✔, mailutils ✔, glib ✔
==> Options
--cocoa
        Build a Cocoa version of emacs
--keep-ctags
        Don't remove the ctags executable that emacs provides
--use-git-head
        Use Savannah (faster) git mirror for HEAD builds
--with-d-bus
        Build with d-bus support
--with-glib
        Build with glib support
--with-gnutls
        Build with gnutls support
--with-imagemagick
        Build with imagemagick support
--with-librsvg
        Build with librsvg support
--with-mailutils
        Build with mailutils support
--with-x
        Include X11 support
--HEAD
        install HEAD version
==> Caveats
To have launchd start emacs at login:
    ln -sfv /usr/local/opt/emacs/*.plist ~/Library/LaunchAgents
Then to load emacs now:
    launchctl load ~/Library/LaunchAgents/homebrew.mxcl.emacs.plist

WARNING: launchctl will fail when run under tmux.
.app bundles were installed.
Run `brew linkapps` to symlink these to /Applications.
```

コンパイルオプションがわりとたくさんありますが, 次のように選びました.

- 最新版の追っかけ (`--HEAD` と `--use-git-head`) もしてません. 普通に
  よく落ちるし, アップデートしてコンパイルする時間がもったいないからです.


インストールが終わったら, /Applications/Emacs.app を作ります.

```
% brew linkapps
```
