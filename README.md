# MP3 Tag Reader

A command-line MP3 tag reader and editor written in C. It parses the ID3v2.3 header and frames of an MP3 file to display its metadata, and lets you edit individual tags such as title, artist, album, year, genre, and comments.

Built to practice file handling, binary data parsing, and modular C programming.

## Features

- View ID3v2.3 tag information of an MP3 file
- Edit individual tags (title, artist, album, year, genre, comment)
- Built-in help menu listing all options
- Input validation and error messages for invalid files or arguments
- Modular code split into view, edit, and help modules

## Project Structure

```
MP3-Tag-Reader/
├── main.c          # Entry point and argument handling
├── view.c / view.h # Reads and displays tag data
├── edit.c / edit.h # Edits tag data
├── help.c / help.h # Help menu
├── operations.h    # Shared declarations
├── sample1.mp3     # Sample files for testing
├── sample2.mp3
└── mp3_tag_reader_srs.pdf  # Software requirements specification
```

## Getting Started

### Requirements

- GCC (or any C compiler)
- Linux, macOS, or Windows with MinGW/WSL

### Clone and Build

```bash
git clone https://github.com/almishamsudheen-ops/mp3-tag-reader.git
cd mp3-tag-reader
gcc *.c -o mp3tag
```

### Usage

```bash
# Show help
./mp3tag --help

# View tags
./mp3tag -v sample1.mp3

# Edit a tag
./mp3tag -e -t "New Title" sample1.mp3
```

| Option | Description |
|--------|-------------|
| `-v`   | View tags |
| `-e`   | Edit tags |
| `-t`   | Title |
| `-a`   | Artist |
| `-A`   | Album |
| `-y`   | Year |
| `-g`   | Genre |
| `-c`   | Comment |
| `--help` | Show help |

## How It Works

An MP3 file with ID3v2.3 starts with a 10-byte header containing the `ID3` identifier, version, flags, and tag size (stored as a synchsafe integer). After the header come frames, each with a 4-character ID (such as `TIT2` for title or `TPE1` for artist), a size, flags, and the data. The program reads these frames, converts sizes between big-endian and little-endian, and prints or rewrites the requested fields.

## What I Learned

- Parsing a binary file format from a specification
- Endianness conversion and synchsafe integers
- File I/O with `fopen`, `fread`, `fseek`, and `fwrite`
- Structuring a C project into multiple modules with header files
- Handling command-line arguments and errors

## Reference

- [ID3v2.3 Tag Specification](https://id3.org/id3v2.3.0)

## Author

**[Almi Shamsudheen](https://www.linkedin.com/in/almi-shamsudheen-67b4592b2)**

Feedback and suggestions are welcome. Feel free to open an issue or connect with me on LinkedIn.

## License

Released under the MIT License.
