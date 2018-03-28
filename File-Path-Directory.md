## File

| Method Name | Description |
| --- | --- |
| Copy(String, String) | Copies an existing file to a new file. Overwriting a file of the same name is not allowed. |
| Copy(String, String, Boolean) | Copies an existing file to a new file. Overwriting a file of the same name is allowed. |
| Delete(String) | Deletes the specified file. |
| Move(String, String) | Moves a specified file to a new location, providing the option to specify a new file name. |


## Path

| Method Name | Description |
| --- | --- |
| Combine(String, String) | Combines two strings into a path. |
| GetDirectoryName(String) | Returns the directory information for the specified path string. |
| GetFileName(String) | Returns the file name and extension of the specified path string. |
| GetFileNameWithoutExtension(String) | Returns the file name of the specified path string without the extension. |
<!--stackedit_data:
eyJoaXN0b3J5IjpbMzE1ODAyNDBdfQ==
-->
## Directory

| Method Name | Description |
| --- | --- |
| CreateDirectory(String) | Creates all directories and subdirectories in the specified path unless they already exist. |
| Exists(String) | Determines whether the given path refers to an existing directory on disk. |
<!--stackedit_data:
eyJoaXN0b3J5IjpbNzE2NTE1Mjk0XX0=
-->