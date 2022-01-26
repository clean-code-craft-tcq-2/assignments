
# Art of Separation and Use of Pure Function

ex:-
```c
//pure function
float convertFarenheitToCelcius(float farenheit) {
    float celcius = (farenheit - 32) * 5 / 9;
    return celcius;
}

void printColorMap(int pairNumber, const char *majorColor, const char *minorColor ) {
	printf("%d | %s | %s\n", pairNumber, majorColor, minorColor);
}
```
# Don't assert on stub
```c
    assert(networkAlertStub(200) == 1 );
    assert(networkAlertStub(500) == 1 )
```
> The stub ensures that the test runs smoothly. explore difference b/w stub and mock (TestDouble)

## assert on expected value 
```c
// Is this a vald assertion?
 assert(alertFailureCount!=0);
//One assert with multiple condition vs multiple assert ?
  assert((size(0) != 'S') && (size(0) != 'M') && (size(0) != 'L'));
```
# Code pollution and Multiple responsibilities
```c
void alertInCelcius(float farenheit , TESTENV testParameter) {
    
    }
//Allow your production code to be free from information about the test environment.
```
