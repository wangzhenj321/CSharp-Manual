## Tips for Using String and StringBuilder

1. Use  `**StringBuilder**`  when you’re concatenating  `string`s in a very long loop or in a loop within an unknown size – especially if you don’t know for sure (at compile time) how many iterations you’ll make through the loop. For example, reading a file a character at a time, building up a  `string`  as you go.

2. Use  **String Concatenation operator**  when you can specify everything which needs to be concatenated in one statement. (If you have an array of things to concatenate, consider calling  `String.Concat`  explicitly – or  `String.Join`  if you need a delimiter.), avoid using the (`+=`) or the normal (`+`) for  `string`s concatenation.

3. If you need the  **intermediate results of the concatenation**  for something other than feeding the next iteration of concatenation,  `StringBuilder`  isn’t going to help you. For instance, if you build up a full name from a first name and a last name, and then add a third piece of information (the nickname, maybe) to the end, you’ll only benefit from using  `StringBuilder`  if you don’t need the (first name + last name)  `string`  for other purpose (as we do in the example which creates a  `Person`  object).

## Methods of String


## Methods of StringBuilder

| Method Name | Description |
| --- | --- |
| `Append(UInt32)` | Appends the string representation of a specified 32-bit unsigned integer to this instance. |
| `AppendLine()` | Appends the default line terminator to the end of the current StringBuilder object.|
| `AppendLine(String)` | Appends a copy of the specified string followed by the default line terminator to the end of the current StringBuilder object. |
| `ToString()` | Converts the value of this instance to a String. |

#### Remarks

You must call the `ToString` method to convert the `StringBuilder` object to a `String` object before you can pass the string represented by the `StringBuilder` object to a method that has a `String` parameter or display it in the user interface.
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE0NDc1MzYwOTFdfQ==
-->