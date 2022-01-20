# Daily naming habits

## Printing

```c
for (int i = 0; i < 25; i++)
```
Avoid hard-coding numbers like 25. A maintainer may forget to change it when a color gets added.

---
Any possibility to check some aspects of the reference manual through Asserts?

---

[Separation of concerns-1](https://github.com/clean-code-craft-tcq-2/well-named-in-py-SanjaySaatyaki/pull/1/files#diff-d1f84ac1f330f233a01340afdac4eaa9c67c5eb90498557a3935a855f70361fc)

[Separation of concerns-2](https://github.com/clean-code-craft-tcq-2/well-named-in-c-Nivedhithya-Sundarasamy/pull/1/files#diff-5bfba68bcb5b26e165cf995cbfde5a44efb838b90a245995729748884df4d8ff)

Do you think Printing is appropriate inside a TelCoColor**Coder** file / class? Or should it be in its own 'Printer' class?

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

## Naming

Try naming by purpose, not content.

instead of `UserDefFunctions`, consider `ColorMapper`

This looks very similar to the next for loop. Is there a possibility to extract the common functionality to a function with a 'good' name?

---

## Testing

Every aspect of the Reference Manual has to be checked manually, including alignment, content, etc.
E.g., when we translate the output to a different language, all these aspects need to be tested again.
Can you think of asserting some aspects of the manual, to reduce the burden on a human tester?

Hint: First step is to separate the forming of the manual from its printing

## Norming

```c
const int MAX_COLORPAIR_NAME_CHARS = 16;
```
Would this work even with other languages?
