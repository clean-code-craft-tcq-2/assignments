# Test statements - recap

## Train tickets

Login ... till ... ticket generation should be less than 45s

connect 1000 users to network and verify the latency is less than 1ms for all users for 1Hr. Try with multiple type of devices like mobile phone, laptop etc

Load the portal in 30kbps data speed, Verify that it loads in less than 1 sec.

Submit 500 requests at a time and verify whether it is responded back within 3 secs.

Simulate parallel users of maximum of 10,000 in number. Every user should have page transition time of 4seconds. 

### Hard

Load the server to its maximum capacity and book the ticket and check whether ticket is booked within expected time.

login with user id and password, try to book by filling family members manually and check latency.

Open ticket webpage and verify the time taken to load UI. 

Record the latency before the enhancement. Record latency after the enhancement. Verify the low latency

## Charger reliability

Do a restart and run the system for 23hr. In the end verify whether there is any deviation with its expected behavior.

Check if the current output by the charger remains at 3A with fluctuations not more than 0.2A continuously for 30 mins

Check memory size > 2Mb

After a successful restart of the public car charger, the embedded software should run for 4 hours before another restart.

Verify the charger works for 16 cycles without any restart. (Assuming that charging a car battery takes 1.5hr on an average )

### Hard

Turn on the car charger. Make the car charger work continuously for 30 hours and check if still working.

## Temperature from sensor

### Specific

Temperature check (temperature,accuracy), stateofcharge(soc),chargerate(chargerate) with accuracy 0.02 tolerance

read temperature whether it is storing with sampling rate of 10hz, it should store 10 samples/seconds.

### Hard

Temperature monitoring system should provide _real time data_ with accuracy of 1%

Temperature monitoring system provide _instant alert_ in case temperature is beyond the range of -50°C and 500 °C.

Check the data from sensor is received and stored for every 5s
