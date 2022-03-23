# TDD recap

## First step

### Watch out for coverage

Code has a bug, coverage is 100% but tests aren't catching

```c
size_t FindNumberOfSamples(int* chargingCurrentSamples) {
	size_t numberOfSamples;
	numberOfSamples = sizeof(chargingCurrentSamples) / sizeof(chargingCurrentSamples[0]);
	return numberOfSamples;
}

TEST_CASE("Check the size of given charging current samples") {
	int chargingCurrentSamples[] = {4,5};
	size_t expectedSize = 2;
	size_t numberOfSamples = FindNumberOfSamples(chargingCurrentSamples);
	REQUIRE(numberOfSamples == expectedSize);
}
```

### Minimal code

[Just enough-1](https://github.com/clean-code-craft-tcq-2/tdd-buckets-VaishakhGurumurthy-Mehendale/pull/1/files)

[Just enough-2](https://github.com/clean-code-craft-tcq-2/tdd-buckets-Nallasamy-Muthupavithra/pull/1/files)

[Just enough-3](https://github.com/clean-code-craft-tcq-2/tdd-buckets-Velayutha-Perumal-Trichy-Rajendran/blob/main/test-alerts.cpp)

### More code

[Get readings for a range](https://github.com/clean-code-craft-tcq-2/tdd-buckets-Subash-Gopal/pull/1/files)

[Generate and detect ranges](https://github.com/clean-code-craft-tcq-2/tdd-buckets-anilknaidu/pull/1/files)

## Second step

Design concepts

- [Samples in one range](https://github.com/clean-code-craft-tcq-2/tdd-buckets-Ranjeth-Sundaram1/blob/856fd6014bbb2eed21eca8d3fe866d6031ca76fe/validate_samples.test.py)
- [BDD with catch](https://github.com/clean-code-craft-tcq-2/tdd-buckets-MeeraMenon1807/blob/90ccf3bd842233107b2401ec0e1461672d48639c/test-tdd.cpp)
- [Testing lower level funcs, avoid modifying input](https://github.com/clean-code-craft-tcq-2/tdd-buckets-Paul-Ajay/pull/1/files)

Algorithms

- [Count in slots, one counter per current-value](https://github.com/clean-code-craft-tcq-2/tdd-buckets-TharaniDevendran/blob/2481a04ddafd17a9b0081964fa930eb3ae3d16b5/CheckNoOfSequenceSamples.c)
- [Subtract from a set of all possible current values](https://github.com/clean-code-craft-tcq-2/tdd-buckets-Sathyapriyan-Kannan/blob/0d5c9590dd93438218c04cbe64913b28968d379a/test_driven_ranges.py)

Allocating memory

```c
/* Returns an array with Count of Elements provided in input array*/
int* provideCountOfDistinctElementsInArray(int *ArrayElements, int sizeOfArray) {
    int *arrayToStoreCount;
    arrayToStoreCount = (int*)calloc(MAX_NUMBER_OF_READINGS, sizeof(int));
    
    for(int i=0; i<sizeOfArray; i++)
    {
        int index = ArrayElements[i];
        arrayToStoreCount[index]++;
    }
    return arrayToStoreCount;
}
```

Parameter naming

```c
unsigned getIndexOfLastElementInContinousRange(unsigned startIndex, const std::vector<int> &rfInputValues, int &count)
```

Test-driven discovery of domain:
Write a test for handling negative numbers in the domain of charging/discharging currents.

```c
// Function to validate if the charging samples are non empty non negative
int negativeNumberInArray(int *chargingSamples, int numSamples){
    if(numSamples > 0){
      for (int i = 0; i < numSamples; i++) {
          if (chargingSamples[i] < 0)
              return 0;
      }
      return 1;
    }
    return 0;
}
```