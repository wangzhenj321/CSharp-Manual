#### 1. Displays a message box with specified text

```C#
MessageBox.Show(
    "Cancel this operation?");
```

![](img/Usage-of-MessageBox/StatusStrip.gi?raw=true)

#### 2. Displays a message box with specified text and caption

```C#
MessageBox.Show(
    "Cancel this operation?",
    "Error Detected in Input");
```

[[]]

#### 3. Displays a message box with specified text, caption, and buttons

```C#
MessageBox.Show(
    "Cancel this operation?",
    "Error Detected in Input",
    MessageBoxButtons.YesNo);
```

[[]]

#### 4. Displays a message box with specified text, caption, buttons, and icon

```C#
MessageBox.Show(
    "Cancel this operation?",
    "Error Detected in Input",
    MessageBoxButtons.YesNo,
    MessageBoxIcon.Question);
```

[[]]

#### 5. Displays a message box with the specified text, caption, buttons, icon, and default button

```C#
MessageBox.Show(
    "Cancel this operation?",
    "Error Detected in Input",
    MessageBoxButtons.YesNo,
    MessageBoxIcon.Question,
    MessageBoxDefaultButton.Button1);
```

[[]]

#### 6. Displays a message box with the specified text, caption, buttons, icon, default button, and options

```C#
MessageBox.Show(
    "Cancel this operation?",
    "Error Detected in Input",
    MessageBoxButtons.YesNo,
    MessageBoxIcon.Question,
    MessageBoxDefaultButton.Button1,
    MessageBoxOptions.RightAlign);
```

[[]]

#### 7. Displays a message box with the specified text, caption, buttons, icon, default button, options, and Help button

```C#
MessageBox.Show(
    "Cancel this operation?",
    "Error Detected in Input",
    MessageBoxButtons.YesNo,
    MessageBoxIcon.Question,
    MessageBoxDefaultButton.Button1,
    MessageBoxOptions.RightAlign,
    true);
```

[[]]

#### 8. Displays a message box with the specified text, caption, buttons, icon, default button, options, and Help button, using the specified Help file

```C#
MessageBox.Show(
    "Cancel this operation?",
    "Error Detected in Input",
    MessageBoxButtons.YesNo,
    MessageBoxIcon.Question,
    MessageBoxDefaultButton.Button1,
    MessageBoxOptions.RightAlign,
    "mspaint.chm");
```

#### 9. Displays a message box with the specified text, caption, buttons, icon, default button, options, and Help button, using the specified Help file and HelpNavigator

```C#
MessageBox.Show(
    "Cancel this operation?",
    "Error Detected in Input",
    MessageBoxButtons.YesNo,
    MessageBoxIcon.Question,
    MessageBoxDefaultButton.Button1,
    MessageBoxOptions.RightAlign,
    "mspaint.chm",
    HelpNavigator.Index);
```

## References
1. [C#中MessageBox用法大全（附效果图）](http://www.cnblogs.com/rainman/archive/2013/06/03/3116283.html)
2. [MessageBox Class](https://msdn.microsoft.com/en-us/library/system.windows.forms.messagebox(v=vs.110).aspx)
<!--stackedit_data:
eyJoaXN0b3J5IjpbOTQwODAwNDUyXX0=
-->