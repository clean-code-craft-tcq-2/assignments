# Test = Specification

Test | Specification
-----|-------
<pre>alertInCelcius(400.5);<br>alertInCelcius(303.6);<br>assert(alertFailureCount == 2);</pre> | failure counts are updated after all alerts have been done
-----|-----
<pre>alertInCelcius(400.5);<br>assert(alertFailureCount == 1);<br>alertInCelcius(303.6);</pre> | failures are counted right after the send-attempt
-----|-----
<pre>assert(alertFailureCount > 0);</pre> | any non-zero count of failures is ok - even if it's in the 100s
-----|-----
<pre>assert((size(38) == 'S') \|\| (size(38) == 'M'));<br>assert((size(38) != 'L');</pre> | 38 can be S or M, we don't mind. What if XL is added?
-----|-----

## Further examples

[coverage and naming of data-spaces](https://github.com/clean-code-craft-tcq-2/test-failer-in-c-EduardoTapiaC/blob/e747c2ba4e58c5d05129d8895fb82f31f9748c16/tshirts.c)

[remove dependency of production code on stub via injection](https://github.com/clean-code-craft-tcq-2/test-failer-in-c-Bekal-Ramnath-Rao/blob/6299acc32975f0c6f9ffc19b872f882938a56879/alerter.c)

[forming before printing](https://github.com/clean-code-craft-tcq-2/test-failer-in-c-SudeshnaMukherjee94/blob/c5567e7e60fcff6654af158bb755d442eaadca07/misaligned.c)

[test the formatting separately - as spacing logic](https://github.com/clean-code-craft-tcq-2/test-failer-in-cpp-SkandaNarayana/blob/62defc232782332c0a819b776a2ea7c76c8bb711/misaligned.cpp)

[test the formatting - by parsing](https://github.com/clean-code-craft-tcq-2/test-failer-in-py-Yashaswini-Devananda/blob/f705457087f36a834bce23bb3f9682750c90f5c3/misaligned.py)

Test pitfall - [false negatives](https://github.com/clean-code-craft-tcq-2/test-failer-in-py-anilknaidu/runs/4951698222?check_suite_focus=true) in `alerter fail`

[The test as an expression of alignment and numbering](https://github.com/clean-code-craft-tcq-2/test-failer-in-cpp-Subash-Gopal/blob/93accc392c12d9d206c25065ef3b4ceadd9ea8de/misaligned.cpp)
