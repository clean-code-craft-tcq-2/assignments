### What is the issue with this code? ?
```c

float convertTempIfInFarenheit(float temperature, string unit)
{
    if(unit == "F")
        return ((temperature - 32.0)/1.8);
    else 
        return temperature;
}
```

### God Class Design
```c
class BatteryStatusChecker {
public:
  BatteryStatusChecker(float lower_temperature, 
                        float upper_temperature, 
                        float lower_soc,
                        float upper_soc, 
                        float minimum_charge_rate, 
                        float temperature_tolerance = 0,
                        float soc_tolerance = 0,
                        float charge_rate_tolerance = 0,
                        float max_temperature = 0,
                        LanguagesSupported language = LanguagesSupported::ENGLISH) {
    this->temperature_lower_limit = lower_temperature;
    this->temperature_upper_limit = upper_temperature;
    this->soc_lower_limit = lower_soc;
    this->soc_upper_limit = upper_soc;
    this->minimum_charge_rate = minimum_charge_rate;
    this->temperature_tolerance = temperature_tolerance;
    this->soc_tolerance = soc_tolerance;
    this->charge_rate_tolerance = charge_rate_tolerance;
    this->max_temperature = max_temperature;
    this->selected_language = language;
  }

  bool isTemperatureOK(float temperature) {
    BoundaryRangeWithTolerance range_label_value;
    range_label_value = getPropertyStatus(temperature, {temperature_lower_limit, temperature_upper_limit, temperature_tolerance}, max_temperature, checkInLimits);
    consolePrint("Temperature",status_message_list[selected_language][range_label_value]);
    if(range_label_value != BoundaryRangeWithTolerance::NORMAL)
      return false;
    else
      return true;
  }

  bool isSocOk(float soc){
    BoundaryRangeWithTolerance range_label_value;
    range_label_value = getPropertyStatus(soc, {soc_lower_limit, soc_upper_limit, soc_tolerance}, static_cast<float>(100.0), checkInLimits);
    consolePrint("SOC", status_message_list[selected_language][range_label_value]);
    if(range_label_value != BoundaryRangeWithTolerance::NORMAL)
      return false;
    else
      return true;
  }
  bool isChargeRateOk(float charge_rate) {
    BoundaryRangeWithTolerance range_label_value;
    range_label_value = getPropertyStatus(charge_rate, {0, minimum_charge_rate, charge_rate_tolerance}, static_cast<float>(1.0), checkInLimits);
    consolePrint("Charge Rate", status_message_list[selected_language][range_label_value]);
    if(range_label_value != BoundaryRangeWithTolerance::NORMAL)
      return false;
    else
      return true;    
  }

  bool batteryIsOk(float temperature, float soc, float charge_rate) {
    temperature_ok = isTemperatureOK(temperature);
    soc_ok = isSocOk(soc);
    charge_rate_ok = isChargeRateOk(charge_rate);
    return temperature_ok && soc_ok && charge_rate_ok;
  }

private:
  float temperature_lower_limit, temperature_upper_limit, soc_lower_limit, soc_upper_limit, minimum_charge_rate;
  float temperature_tolerance, soc_tolerance, charge_rate_tolerance;
  float max_temperature;
  bool temperature_ok, soc_ok, charge_rate_ok;
  void consolePrint(string property, string message) {
    cout <<property <<" : "<< message <<std::endl;
  }
  LanguagesSupported selected_language;
};

```
#### Closure
```java
 static boolean batteryIsOk(final String temperature, final String soc, final String chargeRate) {

    Temperature tempObject = (value, lowerLimit, upperLimit) -> checkIfBatteryConditionOk("Temperature", value,
        lowerLimit, upperLimit, true);

    StateOfCharge stateOfChargeObject = (value, lowerLimit, upperLimit) -> checkIfBatteryConditionOk("State Of Charge",
        value, lowerLimit, upperLimit, true);

    ChargeRate chargeRateObject = (value, upperLimit) -> checkIfChargeRateOk("Charge Rate", value, upperLimit, true);

    float tempInCelcius = getTemperatureInCelcius(temperature);
    float socInPercent = getSocInPercent(soc);
    float chargeRateInCRate = getChargeRateInCRate(chargeRate);

    return tempObject.conditionIsOk(tempInCelcius, 0, 45) && stateOfChargeObject.conditionIsOk(socInPercent, 20, 80) &&
        chargeRateObject.conditionIsOk(chargeRateInCRate, 0.8f);
  }
```
### OCP Violation
```c
float convert_temp_unitbased(char temp_unit , float temperature)
{
	float temp_celcius;
		switch(temp_unit)
	{/* convert any unit to celcius*/

		case 'k':
			temp_celcius = kelvin_to_celcius(temperature);
			break;
		case 'f':
			temp_celcius = farenhiet_to_celcius(temperature);
			break;
		default:
			temp_celcius = temperature;
		break;
			
	}
	return temp_celcius;
	
}
```
[See more](extend-refactor-more-recap.md)
