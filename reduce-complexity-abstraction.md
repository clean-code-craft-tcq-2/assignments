### Art of Separation
```c
breachAndValue checkLowerLimit(float input, float lowLimit);
breachAndValue checkHigherLimit(float input, float highLimit);
void printStatus(breachAndValue lowerResult , breachAndValue higherResult , int parameter);
void limitCheck(float value, float *limit, int parameter);
void temperatureIsOk(float temperature, float *limitArray);
void SOCIsOk(float soc, float *limitArray);
void chargeRateIsOk(float chargeRate, float *limitArray);
int batteryIsOk(float temperature, float soc, float chargeRate, float *limitArray);
void resultCheck(float *testTempList, float *testSOCList,float *testChargeRateList, batteryCondition *testResultArray,float *limitArray, int *resultBattStatus);
```

### pure functions are predictable and testable
---
```c 
//Is this a valid name for a function?
int rangeBasedConditionCheck(float parameterValue, float min_threshold, float max_threshold) {
	if (parameterValue < min_threshold || parameterValue > max_threshold) {
		return 0;
	}
	return 1;
}
//Is this a valid name for a function?
int limitBasedConditionCheck(float parameterValue, float max_limit) {
	if (parameterValue  > max_limit) {
		return 0;
	}
	return 1;
}
//What is the issue with this code?
int statusCheck(int status, const char* parameter) {
	char statement[100];
	strcpy(statement, alertString);
	if (status == 0) {
		strcat(statement, parameter);
		(*fpPrintOnConsole)(statement);
	}
	return status;
}

public class RangeChecker {

  static boolean isInRange(final float value, final float lowerLimit, final float upperLimit) {
    return checkIfValueIsLesser(value, upperLimit) && checkIfValueIsGreater(value, lowerLimit);
  }

  static boolean checkIfValueIsGreater(final float value, final float lowerLimit) {
    return Float.compare(lowerLimit, value) < 0;
  }

  static boolean checkIfValueIsLesser(final float value, final float upperLimit) {
    return Float.compare(value, upperLimit) < 0;
  }

}
```
### Multiple Responsibilities
```c
breachAndValue checkHigherLimit(float input, float highLimit)        // Avioding Duplication
{
	breachAndValue result= {0,0.0};
	if (input  > highLimit)
	{
	result.status = HIGH;
	result.breachedValue = input - highLimit ;	 // Calculate the breached value
	}
	return result;
}
```

### How to test these functions?
```c
void temperatureIsOk(float temperature, float *tempLimitArray)
void SOCIsOk(float soc, float *SOCLimitArray)
void chargeRateIsOk(float chargeRate, float *chargeRateLimitArray)
```
### 
```c
//What is the issue with this class definition?

class Battery
{
    public:
    bool isBatteryOK(float temperature, float soc, float chargeRate);

    private:
    bool checkTemperatureRange(float temperatue, void(*fnprint)(string));
    bool checkStateOfCharegeRange( float soc, void(*fnprint)(string));
    bool checkChargeRateRange(float rate, void(*fnprint)(string));
    static void printWarning(string output);
};
```

### Are these names  verbose?
```c
int ValidateIfBatteryParameterValueIsLessThanMinOperatingLimit(float minOperatingLimitOfBatteryParameter,  float batteryParameterValue, void (*Fn_Ptr)(char[],float))
int ValidateIfBatteryParameterValueIsGreaterThanMaxOperatingLimit(float maxOperatingLimitOfBatteryParameter,  float batteryParameterValue, void (*Fn_Ptr)(char[],float))
```
### Intersting Design!
```c
#define OK 		        true
#define NOT_OK 	        false
#define IS              ==
#define IS_NOT          !=
#define ERROR           -1
#define AND 	        &&
#define OR              ||
#define IS_LESS_THAN    <
#define IS_GREATER_THAN >
#define AND 	        &&
#define OR              ||
#define LESS_THAN(x)    (x - 0.1f)
#define GREATER_THAN(x) (x + 0.1f)

bool batteryTemperature(float temperature)
{
    
	if( (temperature IS_LESS_THAN MINIMUM_TEMPERATURE) OR (temperature IS_GREATER_THAN MAXIMUM_TEMPERATURE) ) 
	{
    	printOutofRange("Temperature");
    	return NOT_OK;
	}
	else 
		return OK;
  
}
```
