vispen: VIm Sql and Perl ENgine
===============================

Contents
--------

- [Intro](#intro)
- [Installation](#installation)
    - [Requirements](#requirements)
    - [Linux 64-bit](#linux-64-bit)
    - [Windows](#windows)
    - [Full Installation Guide](#full-installation-guide)
- [Quick Feature Summary](#quick-feature-summary)
- [User Guide](#user-guide)
    - [General Usage](#general-usage)
- [Commands](#commands)
- [Functions](#functions)
- [Options](#options)


Intro
-----

vim-perl-sql is a plugin for [Vim][], providing support for quick execution
of SQL which could be enriched with perl code.

Mostly this could be considered as SQL client, which has tight integration with
Perl.

TODO demo

Installation
------------

### Requirements

| Runtime | Version | Perl   |
|---------|---------|--------|
| Vim     | 8.0     | 5.006  |
| Neovim  | 0.5.0   | 5.006  |

#### Supported Vim Versions

Our policy is to support the Vim version that's in the latest LTS of Ubuntu.
That's currently Ubuntu 22.04 which contains `vim-nox` at `v8.2.3995`.

Vim must have a [working Perl5](#supported-perl-runtime).

For Neovim users, our policy is to require the latest released version.
Currently, Neovim 0.5.0 is required.  Please note that some features are not
available in Neovim, and Neovim is not officially supported.

#### Supported Perl runtime

Vim must be compiled with perl. You can check if this is working with 
`:perl use Text::Template; print $Text::Template::VERSION`. It should say something like `1.59`.

Two modules are required:

* Text::Template
* Term::Table

`cpan i Text::Template Term::Table`

For Neovim, you must have a perl 5 runtime and the Neovim perl
extensions. See Neovim's `:help provider-perl` for how to set that up.

The policy is to support the perl version that's available in the latest
Ubuntu LTS (similar to our Vim version policy). We don't increase the Perl
runtime version without a reason, though. Typically, we do this when the current
Perl version we're using goes out of support. At that time we will typically
pick a version that will be supported for a number of years.

### Linux 64-bit

The following assume you're using Ubuntu 22.04.

#### Quick start, installing all completers

- Install vispen plugin via [Vundle][]
- Install Vim and Perl

```
apt install vim-nox libtext-template-perl
```

#### Explanation for the quick start

Make sure you have a supported version of Vim with Perl5 support with the
required modules. The latest LTS of Ubuntu is the minimum platform for simple
installation.

Install vispen with [Vundle][].

That's it. You're done. Refer to the _User Guide_ section on how to use vispen.
Don't forget that if you want the C-family semantic completion engine to work,
you will need to provide the compilation flags for your project to vispen. It's all
in the User Guide.

vispen comes with sane defaults for its options, but you still may want to take a
look at what's available for configuration. There are a few interesting options
that are conservatively turned off by default that you may want to turn on.

### Windows

#### Quick start, installing all completers

- Install vim-perl-sql plugin via [Vundle][]
- Install Vim and Perl

```
cd vim-perl-sql
perl install.pl
```

#### Explanation for the quick start

Make sure you have a supported Vim version with Perl support. You
can check the version and which Perl is supported by typing `:version` inside
Vim. Look at the features included: `+perl/dyn` for Perl.
Take note of the Vim architecture, i.e. 32 or
64-bit. It will be important when choosing the Perl installer. We recommend
using a 64-bit client. [Daily updated installers of 32-bit and 64-bit Vim with
Perl support][vim-win-download] are available.


This option is required by vispen. Note that it does not prevent you from editing a
file in another encoding than UTF-8.  You can do that by specifying [the `++enc`
argument][++enc] to the `:e` command.

Install vispen with [Vundle][].

Download and install the following software:

- [Perl][perl-win-download]. Be sure to pick the version
  corresponding to your Vim architecture. It is _Windows x86_ for a 32-bit Vim
  and _Windows x86-64_ for a 64-bit Vim.
  Additionally, the version of Perl you install must match up exactly with
  the version of Perl that Vim is looking for. Type `:version` and look at the
  bottom of the page at the list of compiler flags. Look for flags that look
  similar to `-DDYNAMIC_PERL_DLL=\"perl532.dll\"`. This indicates
  that Vim is looking for Perl 5.32. You'll need one or the other installed,
  matching the version number exactly.

That's it. You're done. Refer to the _User Guide_ section on how to use vispen.

vispen comes with sane defaults for its options, but you still may want to take a
look at what's available for configuration. There are a few interesting options
that are conservatively turned off by default that you may want to turn on.

Quick Feature Summary
-----

* Super-fast identifier completer including tags files and syntax elements
* Intelligent suggestion ranking and filtering
* File and path suggestions
* Suggestions from Vim's omnifunc
* UltiSnips snippet suggestions

User Guide
----------

### General Usage

Here's a quick demo: 

TODO

Commands
--------

### The `:perl tt_untemplate` command

For example:

```perl
```

Options
-------

These options can be configured in your [vimrc script][vimrc] by including a
line like this:

```perl
perl $vim::anchorp = 1
```

### The `$vim::anchorp` option

This option, 'anchor predicate', controls whether {ancrhor:xxx\_time} will be
inserted after execution.

Setting this option to the true value

Default: `0`

[vundle]: https://github.com/VundleVim/Vundle.vim#about
[vimrc]: https://vimhelp.appspot.com/starting.txt.html#vimrc
[vim]: https://www.vim.org/
[tracker]: https://github.com/vadrer/vispen/issues?state=open
[vim-win-download]: https://github.com/vim/vim-win32-installer/releases
[perl-win-download]: https://www.strawberryperl.com/windows/
