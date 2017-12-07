## Question

A simple question: is it possible to customize the tab-to-space conversion factor when using VSCode? For instance, right now in HTML it appears to produce 2 spaces per press of `TAB`, but in Typescript it produces 4.

## Answer

By default, VS Code will try to guess your indentation options depending on the file you open.

You can turn off indentation guessing via `"editor.detectIndentation": false`

You can customize this easily via these 3 settings in *File > Preferences > User Settings*:

```
// The number of spaces a tab is equal to. This setting is overriden
// based on the file contents when `editor.detectIndentation` is true.
"editor.tabSize": 4,

// Insert spaces when pressing Tab. This setting is overriden
// based on the file contents when `editor.detectIndentation` is true.
"editor.insertSpaces": true,

// When opening a file, `editor.tabSize` and `editor.insertSpaces`
// will be detected based on the file contents.
"editor.detectIndentation": true
```

## References

1. [How to set tab-space style?](https://stackoverflow.com/questions/29972396/how-to-set-tab-space-style)