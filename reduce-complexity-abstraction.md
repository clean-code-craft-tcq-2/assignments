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
```