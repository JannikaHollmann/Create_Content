# Structuring Content using the Table of Contents

The structure of your book is based on a `YAML` file called `_toc.yml`, which defines the Table of Contents.
In the simplest form, the _toc.yml looks like this:

```format: jb-book
root: index`
chapters:
- file: path/to/chapter1
- file: path/to/chapter2
  sections:
  - file: path/to/chapter2/section1
```
___
Below you'll find a short desription of the regarding key:

`format:`
*Format* defines how the ToC will be interpreted. For many cases, `jb-book` will be the appropiate option. (other options and their usecases will be  described later.)
`root:`
*Root* defines the landing (aka first) page of your book. Paths that you define will be relative to the root.
`chapters:`
Contains a list of files.
`file:`
Path to the files that you want to include in your book. All the paths are relative to the root.
Can also be a url. 
`sections:`
Defines sections of a chapter.
___
## Organizing chapters into parts

```format: jb-book
root: index
parts:
  - caption: Name of Part 1
    chapters:
    - file: path/to/part1/chapter1
    - file: path/to/part1/chapter2
      sections:
      - file: path/to/part1/chapter2/section1
  - caption: Name of Part 2
    chapters:
    - file: path/to/part2/chapter1
    - file: path/to/part2/chapter2
      sections:
      - file: path/to/part2/chapter2/section1
```
`parts:`
Parts can further subdivide and group chapters and, thus, consist of a list of chapters. 
___
## Autogenerate the Table of Contents from a list of files
Instead of configuring the ToC yourself, Jupyter Book also has a built-in function that generates the Table of Content based on filenames of your content using the following command:
<code>jupyter-book toc from-project path/to/book -f [jb-book/jb-article]

```{note} Note
To use this command, open your OS-respective Terminal, and copy the path to where your files are as an argument (here displayed as "path/to/book")
```
This function will search your respective path for content files and generate the `_toc.yml` based on the content files. Keep in mind, that:
* Each sub-folder must have at least one content file inside it
* The ordering of files in _toc.yml will depend on the alphanumeric order of the filenames (e.g., folder_01 comes before folder_02, and apage comes before b_page)
* If there is a file called index.md in any folder, it will be listed first.

In addition to that, there are a few arguments you can add to the command to control the generation, that are outlined below:

```Usage: jupyter-book toc from-project [OPTIONS] SITE_DIR

  Create a ToC file from a project directory.

Options:
  -e, --extension TEXT            File extensions to consider as documents
                                  (use multiple times)  [default: .rst, .md]
  -i, --index TEXT                File name (without suffix) considered as the
                                  index file in a folder  [default: index]
  -s, --skip-match TEXT           File/Folder names which match will be
                                  ignored (use multiple times)  [default: .*]
  -t, --guess-titles              Guess titles of documents from path names
  -f, --file-format [default|jb-book|jb-article]
                                  The key-mappings to use.  [default: default]
  -h, --help                      Show this message and exit.
  ````
