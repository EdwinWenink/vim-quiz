# vim-quiz.vim

This is a small Vimscript plugin for extracting quiz questions from your notes.
When studying a topic, I typically make notes and intersperse the notes with questions that I can later ask myself to review the material.
This small plugin contains a command to collect all these "quiz" questions from your note.
A second command allows you to paste all collected questions in a file if you want to print them or produce a nice pdf.

## Installation

It is recommended to use a package manager such as [Plug](https://github.com/junegunn/vim-plug).
When using Plug, place the following in your `vimrc`:

```
Plug 'EdwinWenink/vim-quiz'
```

## Usage

By default, questions in your notes are expected to start with `*Q*`, which will pick up questions in lines with `*Q*` and `**Q**` (markdown syntax).
Note: it is assumed that each question is written on a new line.

This plugin offers two commands:

- `:SearchQuestions` will find all questions in the current buffer and collects them in the quickfix list.
- `:PasteQuestions` will paste the contents of the quickfix list on the next line in the current buffer.

Because this plugin uses Vim's quickfix list, you can navigate to the previous and next question with `:cprev` and `:cnext`.
If you use T. Pope's [unimpaired](https://github.com/tpope/vim-unimpaired) plugin, these functions have the shortcuts `[q` and `]q` which you can coincidentally remember as "previous question" and "next question".

This plugin defines default bindings (note that leader is the backslash by default):

- `<leader>sq` invokes `SearchQuestions`
- `<leader>pq` invokes `PasteQuestions`

You can override these defaults, as well as set your preferred "quiz marker" in your `vimrc` as follows:

```vim
nmap <leader>sq <Plug>(SearchQuestions)
nmap <leader>pq <Plug>(PasteQuestions)
let g:quiz_marker = '*Q*'
```
