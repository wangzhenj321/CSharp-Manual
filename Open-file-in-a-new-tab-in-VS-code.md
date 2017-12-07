## Question

I am using vscode 1.3.1 with the newly introduced tabs. When I click on files, the first file will open in a tab. If I do not make any changes to this file, the second clicked file will open in the same tab. How can I avoid this and make vscode always open a new tab?

## Answer

I assume you're using the file browser located within the sidebar in Visual Studio Code to open files. If you're not, this answer will likely not be of any use to you.

When you [single-]click a file in the sidebar, Visual Studio Code opens it in what's called "Preview Mode", which allows you to quickly view files.

Preview Mode tabs are not kept open. As soon as you go to open another file from the sidebar, the existing Preview Mode tab (if one exists) is used. You can determine if a tab is in Preview Mode, by looking at its title in the tab bar. If the title is italic, the tab is in preview mode.

To open a file for editing (i.e. don't open in Preview Mode), double-click on the file in the sidebar.

If you want to disable Preview Mode all together, you can do so by setting the `"workbench.editor.enablePreview"` property to false in your settings file. Also make note of the `"workbench.editor.enablePreviewFromQuickOpen"` option, in case you're looking to disable this only from quick open menu.

Before you can disable Preview Mode, you'll need to open your Settings File.

**Pro Tip**: You can use the Command Palette to open your settings file, just enter `"Preferences: Open User Settings"`!

Once you've opened your settings file (your settings file should be located on the right), add the `"workbench.editor.enablePreview"` property, and set it's value to false.

You can learn more about Visual Studio Code's "Preview Mode", [here](https://code.visualstudio.com/docs/getstarted/userinterface#_preview-mode).

## References

1. [How to config vscode to open files always in a new tab?](https://stackoverflow.com/questions/38713405/how-to-config-vscode-to-open-files-always-in-a-new-tab)