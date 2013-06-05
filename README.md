note
====

`note` is a program for storing, retrieving, and searching for notes. `note` can accept input from stdin or the editor defined in `$VISUAL`.

## Usage

    note new -t tag -t tag2
    note new -t tag1 -t tag2 -d ~/.bookmarks
    note show [id]
    note list -t tag
    note edit [id]
    note delete [id]

### Input from STDIN

    echo "this is a note" | note new -t simple -t hello_world

### Namespacing

Use the `-d` option to set a custom directory for notes. You can create an alias that prepends the directory to the note command to split notes with different contexts:

    alias bmark="note -d ~/.bmark"

## DESCRIPTION:


## EXAMPLES:

    # create a new note with three different tags
    cat <<! | note new -t tag -t tag2 -t anothertag
    This is my note.
    This is another sentence.
    !

    # create a new note in an editor
    note new -t tag -t tag2 -t anothertag

    # update note 1
    cat <<! | note update 1
    This is my updated note.
    !

    # edit note 1
    note edit 1

    # get notes matching the tag "nice"
    note all nice

    # get all notes
    note all

    # get all notes in a different directory
    note all -d directory

    # get a note by its ID
    note get 2

    # delete note 2
    note delete 2

### Namespacing

For example, to use note to store bookmarks, use the following alias:

    alias bmark="note -d ~/.bmark -validate"

Add a bookmark:

    echo "http://nu-ex.com" | bmark -t nerd
