## Question
I am trying to update the status strip in my Windows Forms application, but nothing is being displayed. Here is my code:

```C#
private void textBox1_TextChanged(object sender, EventArgs e)
{
    lines = Regex.Split(textBox1.Text.Trim(), "\r\n");
    lineCount = lines.Count();
    statusStrip1.Text = "Lines: " + lineCount;
    statusStrip1.Refresh();
}
```

## Answer

![](img/Update-StatusStrip-in-Windows-Forms/StatusStrip.gif?raw=true)

You will need to add a `ToolStripStatusLabel` to the `StatusStrip`.

Then set the text of the label instead (you need to do a `statusstrip.Refresh` as there is no refresh on the status-label).

The `Text` property on the `StatusStrip` comes from the StatusStrip inherits `ToolStrip` (which in turn inherits `Control`), but has no visual effect due to the nature of ToolStrips. It can be a bit confusing.

Example:

```C#
private void textBox1_TextChanged(object sender, EventArgs e)
{
    //...
    lines = Regex.Split(textBox1.Text.Trim(), "\r\n");
    lineCount = lines.Count();

    //this label is added in visual editor using the default name
    ToolStripStatusLabel1.Text = string.Format("Lines: {0}", lineCount);
    StatusStrip1.Refresh();
}
```

## References
1. [How to update StatusStrip in Windows Forms](https://stackoverflow.com/questions/13336290/how-to-update-statusstrip-in-windows-forms)
