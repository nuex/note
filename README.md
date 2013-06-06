note
====

note is a program for storing, retrieving, and searching for notes. note can accept input from stdin or an editor defined by `$VISUAL`.

## Installation

    curl --silent -G https://raw.github.com/nuex/note/master/note -o ~/bin/note
    chmod +x ~/bin/note

If you do not already have a ~/bin directory and have it in your $PATH (check
using `echo $PATH`) you can
prexifx the preceding commands with the following

    mkdir -p ~/bin
    echo "PATH=\$PATH:~/bin" >> ~/.bashrc

## Usage

    note new -t tag -t tag2
    note new -t tag1 -t tag2 -d ~/.bookmarks
    note show [id]
    note list -t tag
    note edit [id]
    note delete [id]

### Input from STDIN

    echo "this is a note" | note new -t simple -t hello_world

### Examples:

Create notes:

    cat <<EOS | note new -t tag -t tag2 -t anothertag
    This is my note.
    This is another sentence.
    EOS

    VISUAL=vim note new -t tag -t tag2 -t anothertag

Editing notes:

    note edit 1

Listing notes:

    note list
    note list -t nice
    note list -d directory

Show a note:

    note show 2

Deleting:

    note delete 2

### Namespacing

A cool trick is to use bash aliases to make commands for storing notes in different contexts. For example, to store recipes:

    alias recipe="note -d ~/.recipes"
    recipe new -t breakfast -t vegan

Other possibilities:

    alias bookmark="note -d ~/.bookmarks"
    alias password="note -d ~/.passwords"
