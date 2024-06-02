# Custom Typst snippets for use in Vim and Neovim

Typesetting documents, letters, reports, or even books in [Typst] is not as verbose as LaTeX, but certainly error-prone, given the need for strict syntax. A handful of Vim snippets provided in this repository try to reduce this tedium to as low as practicable.

This repository contains the following custom snippets:

| Snippet                   | Inserts            |
| ------------------------- | ------------------ |
| `apdx` + <kbd>tab</kbd>   | appendix block     |
| `bib` + <kbd>tab</kbd>    | bibliography entry |
| `cod` + <kbd>tab</kbd>    | code file          |
| `fig` + <kbd>tab</kbd>    | figure block       |
| `file` + <kbd>tab</kbd>   | file               |
| `hd` + <kbd>tab</kbd>     | set heading number |
| `letter` + <kbd>tab</kbd> | letter block       |
| `lnk` + <kbd>tab</kbd>    | add link           |
| `ltmpl` + <kbd>tab</kbd>  | letter template    |
| `note` + <kbd>tab</kbd>   | note block         |
| `ntmpl` + <kbd>tab</kbd>  | note template      |
| `pb` + <kbd>tab</kbd>     | page break         |
| `ref` + <kbd>tab</kbd>    | bibliography block |
| `tbl` + <kbd>tab</kbd>    | table block        |

## What are snippets and how do they work?

The concept of a snippet is simple. Think of a block of pre-formatted text (i.e., a template) that one needs to use often. One can of-course type or copy-paste such blocks of text repeatedly the hard way, or one could instead assign such common blocks of text with an abbreviated keyword, which in turn calls the entire block of text. To ensure such blocks do not accidentally appear while typing the actual content of the note, paper, or report, a trigger is required. The trigger in this case is a <kbd>tab</kbd> key.

In Vim's insert mode, typing `note` and hitting <kbd>tab</kbd> key on the keyboard inserts the following block, and focuses on the first user input _Title_ in the template. Type the title. To jump to the next placeholder _Author_, hold <kbd>ctrl</kbd> and press <kbd>j</kbd> (`c-j` in Vim parlance). The shortcut to jumping between placeholders can be set in `~/.vimrc` file. 

```typst
#import "${1:template_incl_path}": note
#show note.with(
  title: [${2:title}],
  author: "${3:author}",
  date: [${4:date}],
)
// content hereon
```

## Requirements

To be able to use snippets, the following are required:

1. Vim or Neovim with python3 support.
2. [UltiSnips][us] 
3. [typst-snippets-vim][ck]

## Installation

1. Set up [vim-plug][vp] plug-in manager
2. Set the required UltiSnips plug-in for [typst-snippets-vim][ck] by adding the following to `.vimrc` file:

```vim
call plug#begin('~/.vim/plugged')

" UltiSnips for snippets
Plug 'sirver/ultisnips'

" Typst snippets for Vim using UltiSnips (downloads only tagged releases)
Plug 'ckunte/typst-snippets-vim', { 'tag': '*' }

call plug#end()

let g:UltiSnipsExpandTrigger = '<tab>'
let g:UltiSnipsJumpForwardTrigger = '<c-j>'
let g:UltiSnipsJumpBackwardTrigger = '<c-k>'
```

Reload `.vimrc` and `:PlugInstall` to install plug-ins.

[Typst]: https://typst.app
[us]: https://github.com/SirVer/ultisnips
[vp]: https://github.com/junegunn/vim-plug
[ck]: https://github.com/ckunte/typst-snippets-vim
