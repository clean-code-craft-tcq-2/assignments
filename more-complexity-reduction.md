
## Complex conditions

```python
 return_value = not(temperatureNotOk or socNotOk or charge_rateNotOk)
```

```c
    TR = Temp_Range(temperature);
    SR = State_Range(soc);
    CR = Charge_Range(chargeRate);
    Battery_status = LogicalAND(TR , SR) ;
    Battery_status = LogicalAND(Battery_status , CR);
```

```c
batteryTemperatureIsOk(temperature) && batterySOCIsOk(soc) && batterychargeRateIsOk(chargeRate)
```

testing...
```c
status = (temperature_range(temperature)) && (soc_range(soc)) && (chargerate_range(chargeRate)) ;
...
  assert(batteryIsOk(25, 70, 0.7));
  assert(!batteryIsOk(50, 85, 0));
  assert(!batteryIsOk(55, 30, 0.9));
  assert(!batteryIsOk(90, 65, 0.5));
```

## Close to requirement

[Concise](https://github.com/clean-code-craft-tcq-2/simple-monitor-in-py-GunaseelanRajamanickam/blob/69735f9fc8105d86c37c7bf42d2c1b6b598916a4/check_limits.py)

[Explicit types](https://github.com/clean-code-craft-tcq-2/simple-monitor-in-c-EduardoTapiaC/blob/e7b957ec1eb0782fef352db561083bae88bf4158/checker.c)

## Data coverage

[Enumerating by literals](https://github.com/clean-code-craft-tcq-2/simple-monitor-in-py-anilknaidu/blob/645c0108eca15c9bcce22a898913462863cf0dc8/check_limits.py)

[Enumerating by iteration](https://github.com/clean-code-craft-tcq-2/simple-monitor-in-py-Yashaswini-Devananda/blob/ca5f18eef55f91d025bdefb5bcd91d0091ca1420/check_limits.py)
