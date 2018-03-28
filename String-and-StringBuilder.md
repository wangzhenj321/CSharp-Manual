## Tips for Using String and StringBuilder

1. Use  `**StringBuilder**`  when you’re concatenating  `string`s in a very long loop or in a loop within an unknown size – especially if you don’t know for sure (at compile time) how many iterations you’ll make through the loop. For example, reading a file a character at a time, building up a  `string`  as you go.

2. Use  **String Concatenation operator**  when you can specify everything which needs to be concatenated in one statement. (If you have an array of things to concatenate, consider calling  `String.Concat`  explicitly – or  `String.Join`  if you need a delimiter.), avoid using the (`+=`) or the normal (`+`) for  `string`s concatenation.

3. If you need the  **intermediate results of the concatenation**  for something other than feeding the next iteration of concatenation,  `StringBuilder`  isn’t going to help you. For instance, if you build up a full name from a first name and a last name, and then add a third piece of information (the nickname, maybe) to the end, you’ll only benefit from using  `StringBuilder`  if you don’t need the (first name + last name)  `string`  for other purpose (as we do in the example which creates a  `Person`  object).

## Methods of String

| Method | 
| --- | --- |
| AppendLine() | Appends the default line terminator to the end of the current StringBuilder object.|

## Methods of StringBuilder
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTIyOTAxODA1OF19
-->