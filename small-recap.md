# Daily naming habits

Try naming by purpose, not content.

instead of `UserDefFunctions`, consider `ColorMapper`

ex:-
```c
void PrintColorCodingReferenceManual()
	{
		....
	}
```

Functions returning boolean - reflect their purpose to the caller, not what they are 'checking'

instead of `checkPairNumber`, consider `pairNumberIsValid`

---

```c
for (int i = 0; i < 25; i++) 
  // print all colors
```
Avoid hard-coding numbers like `25`. A maintainer may forget to change it when a color gets added.

---

[Separation of concerns-1](https://github.com/clean-code-craft-tcq-2/well-named-in-py-SanjaySaatyaki/pull/1/files#diff-d1f84ac1f330f233a01340afdac4eaa9c67c5eb90498557a3935a855f70361fc)

[Separation of concerns-2](https://github.com/clean-code-craft-tcq-2/well-named-in-c-Nivedhithya-Sundarasamy/pull/1/files#diff-5bfba68bcb5b26e165cf995cbfde5a44efb838b90a245995729748884df4d8ff)

Do you think Printing is appropriate inside a TelCoColor**Coder** file / class? Or should it be in its own 'Printer' class?

## Testing

Any possibility to check some aspects of the reference manual through Asserts?

Every aspect of the Reference Manual has to be checked manually, including alignment, content, etc. Can we reduce the burden on a human tester?

Hint: First step is to separate the forming of the manual from its printing

[Testing ColorCodePairMannual Print Functionality](https://github.com/clean-code-craft-tcq-2/well-named-in-py-TalhaKhatib/pull/1/commits/025c04c680c41ca546e71798f6ade3738c8ef641)

## Duplication

Consider - these pieces of code are copy-pasted for their 'minor' counterparts.
Do you think this duplication is significant?

```c
// Find the major color in the array and get the index
int majorIndex = -1;
for (int i = 0; i < colorMapMajor.Length; i++)
    // code to match and break...
```

```java
  public static MajorColor fromIndex(final int index) {
    for (MajorColor color : MajorColor.values()) {
      if (color.getIndex() == index) {
        return color;
      }
    }
    return null;
  }
```
