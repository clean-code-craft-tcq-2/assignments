# TDD to extend functionality

Test new functionality separately and then integrate

[Use of GENERATE to cover data-space](https://github.com/clean-code-craft-tcq-2/tdd-buckets-Nivedhithya-Sundarasamy/blob/83799c3c0ec20787c1031f432a0654c929e4ce8b/TestInterpretChargingCurrentRangeAndOccurences.cpp)

[Separate testing steps in the workflow](https://github.com/clean-code-craft-tcq-2/tdd-buckets-Ranjeth-Sundaram1/blob/f75469e45314b60f856ac8f2b693b575ede6e28e/.github/workflows/main-workflow.yml)

[BDD in Action](https://github.com/clean-code-craft-tcq-2/tdd-buckets-KiruthighaKMuthusamy/pull/1/files)


# God Class 
```c
class FindRangeReadings
{
public:
    cacheRages m_cacheRange;
    storeConvertedCurrentSamples m_currentSamplesAfterA2D;
    void cacheReadingsFromRanges(std::vector<int> inputRange);
    void printRangeandReadings();
    int convertToAmps(int currentElements);
    bool sortInputRange(std::vector<int> inputRange);
};

```

# Code Duplication
```c
int maxAnalogToDigitalConversion(int ADC_Resolution)
{
	return (pow(2,ADC_Resolution) - 2);
}

int stdAnalogToDigitalConvertedValue(int ADC_Resolution)
{
	return (pow(2,ADC_Resolution) - 1);
}

```

# OCP Violation
```c
def calc_ranges_from_sensor(samples,sensor):
    if sensor == "A2D_12B":
        valid_samples = remove_invalid_data(samples,4094)
        amps_sample = A2D_12BtoAmps_convertor(valid_samples)
    elif sensor == "A2D_10B":
        valid_samples = remove_invalid_data(samples,1022)
        amps_sample = A2D_10BtoAmps_convertor(valid_samples)
    return calc_ranges(amps_sample)
```

