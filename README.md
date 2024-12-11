[![Actions Status](https://github.com/raku-community-modules/Docker-File/actions/workflows/linux.yml/badge.svg)](https://github.com/raku-community-modules/Docker-File/actions) [![Actions Status](https://github.com/raku-community-modules/Docker-File/actions/workflows/macos.yml/badge.svg)](https://github.com/raku-community-modules/Docker-File/actions) [![Actions Status](https://github.com/raku-community-modules/Docker-File/actions/workflows/windows.yml/badge.svg)](https://github.com/raku-community-modules/Docker-File/actions)

NAME
====

Docker::File - Parsing and generation of Dockerfiles

SYNOPSIS
========

```raku
use Docker::File;

# Parse a Dockerfile into a bunch of objects.
my $parsed-df = Docker::File.parse($docker-file);
unless $parsed-df.instructions.grep(Docker::File::Maintainer) {
    note "This Dockerfile has no maintainer! :-("
}

# Generate a Dockerfile.
my $new-df = Docker::File.new(
  images => [
    Docker::File::Image.new(
      from-short => 'ubuntu',
      from-tag => 'latest'
      entries => [
        Docker::File::RunShell.new(
          command => 'sudo apt-get install raku'
        )
      ]
    )
  ]
);
say ~$new-df;
```

DESCRIPTION
===========

A Raku module to read/write docker files.

AUTHOR
======

Jonathan Worthington

COPYRIGHT AND LICENSE
=====================

Copyright 2016 - 2017 Jonathan Worthington

Copyright 2024 Raku Community

This library is free software; you can redistribute it and/or modify it under the Artistic License 2.0.

