## Widening Conversions

|Data type|Widens to data types<sup>1</sup>|
|---|---|
|sbyte|sbyte, short, int, long, decimal, float, double|
|byte|byte, short, ushort, int, uint, long, ulong, decimal, float, double|
|short|short, int, long, decimal, float, double|
|ushort|ushort, int, uint, long, ulong, decimal, float, double|
|int|int, long, decimal, float, double<sup>2</sup>|
|uint|uint, long, ulong, decimal, float, double<sup>2</sup>|
|long|long, decimal, float, double<sup>2</sup>|
|ulong|ulong, decimal, float, double<sup>2</sup>|
|decimal|decimal, float, double<sup>2</sup>|
|float|float, double|
|double|double|
|Any enum|Its underlying integer type and any type to which it widens|
|char|char, string|
|char array|char array, string|
|Any type|object|
|Any derived type|Any base type from which it is derived<sup>3</sup>|
|Any type|Any interface it implements|
|null|Any data or object type|

<sup>1</sup> By definition, every data type widens to itself.

<sup>2</sup> Conversions from int, uint, long, ulong, or decimal to float or double might result in loss of precision, but never in loss of magnitude. In this sense they do not incur information loss.

<sup>3</sup> A type contains all the members of the base type, so it qualifies as an instance of the base type. In the opposite direction, the base type does not contain any new members defined by the derived type.

Widening conversions always succeed at run time and never incur data loss. They are always performed implicitly, even if no cast is used.

## Narrowing Conversions

These are the standard narrowing conversions:
- The reverse directions of the widening conversions in the preceding table (except that every type widens to itself).
- Conversions in either direction between Boolean and any numeric type.
- Conversions from any numeric type to any enumerated type (enum).
- Conversions from a data type or object type to a type derived from it.
- Narrowing conversions do not always succeed at run time, and can fail or incur data loss. An error occurs if the destination data type cannot receive the value being converted. For example, a numeric conversion can result in an overflow.

## References
1. [Widening and Narrowing Conversions](http://condor.depaul.edu/sjost/nwdp/notes/cs1/Widening.htm)