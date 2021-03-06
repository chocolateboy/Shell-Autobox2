# Shell::Autobox

[![Build Status](https://github.com/chocolateboy/Shell-Autobox/workflows/test/badge.svg)](https://github.com/chocolateboy/Shell-Autobox/actions?query=workflow%3Atest)
[![CPAN Version](https://badge.fury.io/pl/Shell-Autobox.svg)](https://badge.fury.io/pl/Shell-Autobox)

<!-- TOC -->

- [NAME](#name)
- [SYNOPSIS](#synopsis)
- [DESCRIPTION](#description)
- [EXPORTS](#exports)
- [VERSION](#version)
- [SEE ALSO](#see-also)
- [AUTHOR](#author)
- [COPYRIGHT AND LICENSE](#copyright-and-license)

<!-- TOC END -->

# NAME

Shell::Autobox - pipe Perl values through shell commands

# SYNOPSIS

```perl
use Shell::Autobox qw(xmllint);

my $xml = '<foo bar="baz"><bar /><baz /></foo>';
my $pretty = $xml->xmllint('--format -');
```

# DESCRIPTION

Shell::Autobox provides an easy way to pipe Perl values through shell commands.
Commands passed as arguments to the `use Shell::Autobox` statement are
installed as subroutines in the calling package, and that package is then
registered as the handler for methods called on strings, numbers or arrayrefs.

When a registered command is called as a method, the value is passed as the
command's standard input, additional arguments are passed to the command, and —
if no error occurs — the command's standard output is returned. This can then
be piped into other commands.

The registered methods can also be called as regular functions, e.g.:

```perl
use Shell::Autobox qw(cut);

my $bar = cut('foo:bar:baz', '-d:', '-f2');
```

# EXPORTS

None by default.

# VERSION

2.0.1

# SEE ALSO

- [autobox](https://metacpan.org/pod/autobox)
- [autobox::Core](https://metacpan.org/pod/autobox::Core)
- [IPC::Run3::Shell](https://metacpan.org/pod/IPC::Run3::Shell)
- [System::Sub](https://metacpan.org/pod/System::Sub)
- [Shell](https://metacpan.org/pod/Shell)

# AUTHOR

[chocolateboy](mailto:chocolate@cpan.org)

# COPYRIGHT AND LICENSE

Copyright © 2005-2021 by chocolateboy.

This is free software; you can redistribute it and/or modify it under the terms of the
[Artistic License 2.0](https://www.opensource.org/licenses/artistic-license-2.0.php).
