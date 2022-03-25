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


void checkNumberOfReadingsInRange(int* inputStream, int rangeStart, int rangeEnd)
{
	int i, numberOfReadings = 0;
	for(i = 0; i < DATA_STREAM_SIZE; i++)
	{
		if((inputStream[i] >= rangeStart) && (inputStream[i] <= rangeEnd))
		{
			numberOfReadings++;
		}
	}

	sprintf(RangeAndReading, "%d-%d,%d",rangeStart, rangeEnd, numberOfReadings);
}
TEST_CASE("check number of readings in given range from charging session"){
  	int data[DATA_STREAM_SIZE] = {4,5};
	int rangeLow = 4;
	int rangeHigh = 5;
	checkNumberOfReadingsInRange(data, rangeLow, rangeHigh);
	REQUIRE(!strncmp(RangeAndReading, "4-5,2", 5));
}

TEST_CASE("check of no readings found in given range from charging session"){
  	int data[DATA_STREAM_SIZE] = {3,0,-2,10,100};
	int rangeLow = 4;
	int rangeHigh = 7;
	checkNumberOfReadingsInRange(data, rangeLow, rangeHigh);
	REQUIRE(!strncmp(RangeAndReading, "4-7,0", 5));
}
```

### Interesting Test Case
```c
def test_calc_ranges_invalid(self):
      self.assertTrue(current_range_calc.calc_ranges([3,5,7,9]) ==  {})

```
## Solutions

Design concepts

- [Samples in one range](https://github.com/clean-code-craft-tcq-2/tdd-buckets-Ranjeth-Sundaram1/blob/856fd6014bbb2eed21eca8d3fe866d6031ca76fe/validate_samples.test.py)
- [BDD with catch](https://github.com/clean-code-craft-tcq-2/tdd-buckets-MeeraMenon1807/blob/90ccf3bd842233107b2401ec0e1461672d48639c/test-tdd.cpp)
- [Testing lower level funcs, avoid modifying input](https://github.com/clean-code-craft-tcq-2/tdd-buckets-Paul-Ajay/pull/1/files)
- [Good Demonstartion Of TDD Steps](https://github.com/clean-code-craft-tcq-2/tdd-buckets-VishnuNarayanan1/blob/main/testCases.cpp)
- [TDD Kata](https://github.com/clean-code-craft-tcq-2/tdd-buckets-GunaseelanRajamanickam)


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

Change the name of `rfInputValues` to reflect that it must be sorted

```c
unsigned getIndexOfLastElementInContinousRange(unsigned startIndex, const std::vector<int> &rfInputValues, int &count)
```
