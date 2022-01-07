### Art of Readable Code

---

#### Pack Information into your names

- Use Specific words  - for example , instead of Get, words like Fetch or Download might be better , depending on the context.

- Avoid Generic Names - like **tmp** and **retval**, unless there's specific reason to use them

- Use concrete names that describe things in more detail—the name ServerCanStart() is vague compared to CanListenOnPort().

  ```C++
  // Here’s an example from the codebase at Google. In C++, if you don’t define a copy constructor
  or assignment operator for your class, a default is provided. Although handy, these methods can easily lead to memory leaks and other mishaps because they’re executed “behind the scenes” in places you might not have realized. As a result, Google has a convention to disallow these “evil” constructors, using a macro:
  class ClassName {
  private:
  DISALLOW_EVIL_CONSTRUCTORS(ClassName);
  public:
  ...
  };
  
  //This macro was defined as:
  #define DISALLOW_EVIL_CONSTRUCTORS(ClassName) \
  ClassName(const ClassName&); \
  void operator=(const ClassName&);
  
  
  The name DISALLOW_EVIL_CONSTRUCTORS isn’t very good, though. The use of the word “evil”
  conveys an overly strong stance on a debatable issue. More important, it isn’t clear what that
  macro is disallowing. It disallows the operator=() method, and that isn’t even a “constructor”!
  The name was used for years but was eventually replaced with something less provocative and
  more concrete:
  
  #define DISALLOW_COPY_AND_ASSIGN(ClassName) ...
  ```

  

- Attach important details to variable names—for example, append _ms to a variable whose value is in milliseconds or prepend raw_ to an unprocessed variable that needs escaping.

| Function parameter            | Renaming parameter to encode units |
| ----------------------------- | ---------------------------------- |
| Start(int delay )             | delay → delay_secs                 |
| CreateCache(int size )        | size → size_mb                     |
| ThrottleDownload(float limit) | limit → max_kbps                   |
| Rotate(float angle)           | angle → degrees_cw                 |



-  Use longer names for larger scopes—don’t use cryptic one- or two-letter names for variables that span multiple screens; shorter names are better for variables that span only a few lines.

-  Use capitalization, underscores, and so on in a meaningful way—for example, you can append “_” to class members to distinguish them from local variables.

- Encoding Other Important Attributes

  

  | Situation                                                    | Variable Name | Better Name        |
  | ------------------------------------------------------------ | ------------- | ------------------ |
  | A password is in “plaintext” and should be encrypted before further processing | password      | plaintext_password |
  | A user-provided comment that needs escaping before being displayed | comment       | unescaped_comment  |
  | Bytes of html have been converted to UTF-8                   | html          | html_utf8          |
  | Incoming data has been “url encoded”                         | data          | data_urlenc        |

- HUNGARIAN NOTATION?

- | Name      | Meaning                                                      |
  | --------- | ------------------------------------------------------------ |
  | pLast     | A pointer (p) to the last element in some data structure     |
  | pszBuffer | A pointer (p) to a zero-terminated (z) string (s) buffer     |
  | cch       | A count (c) of characters (ch)                               |
  | mpcopx    | A map (m) from a pointer to a color (pco) to a pointer to an x-axis length (px) |



### Simplifying Loops and Logic

---

Make all your conditionals, loops, and other changes to control flow as “natural” as possible—written in a way that doesn’t make the reader stop and reread your code.



#### The Order of Arguments in Conditionals

When writing a comparison (while (bytes_expected > bytes_received)), it’s better to put the changing value on the left and the more stable value on the right (while (bytes_received < bytes_expected)).

| Left-hand side                                               | Right-hand side                                              |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| The expression “being interrogated,” whose value is more in flux. | The expression being compared against, whose value is more constant. |

This guideline matches English usage—it’s pretty natural to say, “if you make at least $100K/year” or “if you are at least 18 years old.” It’s unnatural to say, “if 18 years is less than or equal to your age.”



