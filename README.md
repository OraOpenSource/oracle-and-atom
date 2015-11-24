# Atom packages for Oracle Developers

[Atom](atom.io) is a free open source powerful text editor. One of its greatest features is the ability to add packages to enhance its functionality. This document covers recommended packages for Oracle developers that use Atom.


Package                                                           | Description
----------------------------------------------------------------- | -------------------------
[`language-oracle`](https://atom.io/packages/language-oracle)     | Language specific syntax highlighting for Oracle developers
[`symbols-tree-view`](https://atom.io/packages/symbols-tree-view) | Quick links to procedures and functions in a package (_Note: PL/SQL integration still in development)_
[`minimap`](https://atom.io/packages/minimap)                     | A preview of the full source code and quick scrolling through file
[`file-icons`](https://atom.io/packages/file-icons)               | Adds file specific icons to atom for improved visualization

## language-oracle

This is the grammar for PL/SQL code, and includes all relevant syntax highlights, as well as snippets for common code blocks such as `loops`, `if then else` etc.

Once installed, the language will automatically pickup the grammar when opening files with all the common PL/SQL file extensions. If you have not yet saved your file, or are using a currently un-recognised file extension, you can manually apply the language with the keyboard shortcut `ctrl+shft+L` and searching for PL/SQL

![](https://cloud.githubusercontent.com/assets/1747643/11353907/74f00ca6-929b-11e5-89f1-4a52dca44787.png)

## symbols-tree-view

This package provides a symbols/class view on the right hand side of your text editor. Clicking on any symbol will take you to that position in the code.

![](https://cloud.githubusercontent.com/assets/1747643/11354004/62272df6-929c-11e5-89a4-adc802e6349c.png)
