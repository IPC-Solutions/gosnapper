# GoSnapper

A Go implementation of the [RedSnapper tool](https://github.com/directededge/redsnapper), designed to run parallel Tarsnap clients for faster extraction of archives with lots of files.

## Overview

GoSnapper speeds up Tarsnap extractions by running multiple clients in parallel. Note that extraction will be slower on small archives since this tool first has to build a list of files to extract. It then runs multiple clients in parallel (default: 10) delivering approximately a 5x speedup in extracting large archives.

## Usage

```
Usage: gosnapper [-d DIR] [-j COUNT] archive [-- [TARSNAP OPTIONS]]
  -d, --directory DIR    Extract files from this directory of the archive
  -j, --jobs COUNT       Number of workers to use
```

## Installation

### From Source

1. Clone the repository
2. Build the binary:
   ```
   cd /path/to/gosnapper
   go build -o gosnapper ./cmd/gosnapper
   ```
3. Move the binary to your PATH

## Requirements

- Go 1.20 or later
- Tarsnap installed and configured on your system

## How It Works

GoSnapper works by:

1. Getting a list of all files in the tarsnap archive
2. Dividing the files into groups based on size for balanced parallel processing
3. Running multiple tarsnap clients in parallel to extract the files
4. Handling errors and output from the tarsnap processes

## License

Copyright (c) 2025. See LICENSE for further details.
