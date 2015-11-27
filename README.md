# Atom packages for Oracle Developers

[Atom](https://atom.io/) is a free open source powerful text editor. One of its greatest features is the ability to add packages to enhance its functionality. This document covers recommended packages for Oracle developers that use Atom.


Package                                   | Description
----------------------------------------- | -------------------------
[`project-manager`](#project-manager)     | Allows easy access and quickly switching between projects in Atom
[`language-oracle`](#language-oracle)     | Language specific syntax highlighting for Oracle developers
[`symbols-tree-view`](#symbols-tree-view) | Quick links to procedures and functions in a package (_Note: PL/SQL integration still in development)_
[`minimap`](#minimap)                     | A preview of the full source code and quick scrolling through file
[`file-icons`](#file-icons)               | Adds file specific icons to atom for improved visualization
[`atom-aligntment`](#atom-alignment)      | Aligns multiple lines of assignment operators

## [project-manager](https://atom.io/packages/project-manager)

This allows you to set up a configuration of your active projects so that you can quickly switch between them. The configuration for this is a `cson` file located in your atom user directory - `$HOME/.atom/projects.cson` most typically. You can quickly access it by opening the command palette (`ctrl+shift+p`) and searching for `Edit projects`.

![](https://cloud.githubusercontent.com/assets/1747643/11432340/58a546b2-9500-11e5-8026-d44fa9b0c798.png)

Then, for each project you define properties such as `title`, `paths`, `icon` and `settings` - there are others, which you can read about on the packages README.

To get your project added without manually filling out the properties, you can search for `Save Project` in the command palette and it will prompt you for the name of the project, which adds the entries for `title` and `paths` in the project configuration file.

So for example, I have one project set up for my Atom user directory, as:

```cson
atomConfig:
  title: "Atom user directory"
  paths: [
    "/home/trent/.atom"
  ]
  icon: "icon-tools"
  settings:
    "*":
      "editor.tabLength": 2
```

This means I can quickly open this project by hitting `alt+shift+P` and searching for `atom user directory`.

![](https://cloud.githubusercontent.com/assets/1747643/11432417/1d6b2cd6-9502-11e5-84a1-cd0137508814.png)

### Settings

Any settings you can apply system wide, you can also apply in the project configuration, with `*` being the wild card for all file types. You could alternatively have specific settings for specific language scopes. For instance, in the documentation, it has the example:

```cson
'.source.coffee':
  'editor.tabLength': 2
  'editor.preferredLineLength': 80
```

If you look at the grammar [specification](https://github.com/atom/language-coffee-script/blob/master/grammars/coffeescript.cson) for CoffeeScript, you will see it's defined the `scopeName` as `source.coffee` which is why the above setting is mapped to `.source.coffee`.

## Icon

The icons you can use against your projects are based on [GitHub Octicons](https://octicons.github.com/). For example, on the Atom user directory project I set up earlier, I specified the icon as `icon-tools`. If you look at the grid of icons, you will find that particular icon towards the bottom.

Clicking onto will give you the class name as `octicon-tools`. So in our project settings, we use that same class name, only replacing `octicon` with `icon` - thus becoming `icon-tools`.


![](https://cloud.githubusercontent.com/assets/1747643/11433288/1e8bdaea-950f-11e5-9fec-de144f7ba02a.png)

## [language-oracle](https://atom.io/packages/language-oracle)

This is the grammar for PL/SQL code, and includes all relevant syntax highlights, as well as snippets for common code blocks such as `loops`, `if then else` etc.

Once installed, the language will automatically pickup the grammar when opening files with all the common PL/SQL file extensions. If you have not yet saved your file, or are using a currently un-recognised file extension, you can manually apply the language with the keyboard shortcut `ctrl+shft+L` and searching for PL/SQL

![](https://cloud.githubusercontent.com/assets/1747643/11353907/74f00ca6-929b-11e5-89f1-4a52dca44787.png)

## [symbols-tree-view](https://atom.io/packages/symbols-tree-view)

This package provides a symbols/class view on the right hand side of your text editor. Clicking on any symbol will take you to that position in the code.

![](https://cloud.githubusercontent.com/assets/1747643/11354004/62272df6-929c-11e5-89a4-adc802e6349c.png)

The pane get easily be toggled on and off with the keyboard shortcut `ctrl+alt+o`.

## [minimap](https://atom.io/packages/minimap)

Gives a zoomed out view of the code, on either the left or right hand side of the file that you can drag to scroll to a specific portion of the code.

![](https://cloud.githubusercontent.com/assets/1747643/11354495/f057cc2c-929f-11e5-8d31-d7252f001ec9.png)

## [file-icons](https://atom.io/packages/file-icons)

Adds icons specific to a files extension - just to add a bit of eye candy, and one more visual recognition of the file type. The icons are based on FontAwesome (and derivative(s)) fonts.

As a little example, before using this package:

![](https://cloud.githubusercontent.com/assets/1747643/11354338/d6529614-929e-11e5-9bb9-b7325e5aaaf2.png)

and after:

![](https://cloud.githubusercontent.com/assets/1747643/11354347/e8358f62-929e-11e5-832c-a4b085ec07b6.png)

note: The icon on `foo.pks` in the screenshot above hasn't yet made it into the package - but gives an idea of what is possible

## [atom-alignment](https://atom.io/packages/atom-alignment)

Based on a given selection of text, this will align all assignment operators which can aid in making the code more readable. The key bindings are `ctrl+alt+A` or `ctrl+cmd+A`. Best demonstrated with an example. So first you need to highlight any text where assignment operators occur, then run the aforementioned key bindings.

Example 1: Just the package call

Before:

```plsql
declare
    l_short_field NUMBER;
    l_really_really_long_field NUMBER;
begin

    l_short_field := 1;
    l_really_really_long_field := 999;

    field_updater.get_ready_for_update;

    field_updater.update_details(
        l_short_field => l_short_field
      , l_really_really_long_field => l_really_really_long_field
    );

end;
/
```

After:

```plsql
declare
    l_short_field NUMBER;
    l_really_really_long_field NUMBER;
begin

    l_short_field := 1;
    l_really_really_long_field := 999;

    field_updater.get_ready_for_update;

    field_updater.update_details(
        l_short_field              => l_short_field
      , l_really_really_long_field => l_really_really_long_field
    );

end;
/
```

Example 2: The whole package

```plsql
declare
    l_short_field NUMBER;
    l_really_really_long_field NUMBER;
begin

    l_short_field := 1;
    l_really_really_long_field := 999;

    field_updater.get_ready_for_update;

    field_updater.update_details(
        l_short_field => l_short_field
      , l_really_really_long_field => l_really_really_long_field
    );

end;
/
```

After:

```
declare
    l_short_field NUMBER;
    l_really_really_long_field NUMBER;
begin

    l_short_field              := 1;
    l_really_really_long_field := 999;

    field_updater.get_ready_for_update;

    field_updater.update_details(
        l_short_field              => l_short_field
      , l_really_really_long_field => l_really_really_long_field
    );

end;
/
```

One change I did make, was to clear one of the settings `Add Space Postfix`.

![](https://cloud.githubusercontent.com/assets/1747643/11433471/c894e9da-9511-11e5-94e0-35e06826319d.png)

If that is left enabled, the previous block would have come out as:

```plsql
declare
    l_short_field NUMBER;
    l_really_really_long_field NUMBER;
begin

    l_short_field              := 1;
    l_really_really_long_field := 999;

    field_updater.get_ready_for_update;

    field_updater.update_details(
        l_short_field              = > l_short_field
      , l_really_really_long_field = > l_really_really_long_field
    );

end;
/
```
