# Conditionals
Conditionals is a string-condition parser.<br>
It works by grabbing a string which it assumes is a valid conditional<br>
This is useful for plugin customizability by only executing if the condition is met.
<br><br>
# Example
```java
	String[] conditions = [
		"true == true || false == 0", // returns true
		"false == true", // returns false
		"5*3+5 == 20", // returns true
		"\"dINg\" == \"dINg\" && (53/2 == 1 || 3*3 == 9)", // returns false because 53/2 != 1
		"ping == ping", // returns false because it doesnt know what ping is. Strings need to be surrounded by quotes
		"\"ping\" == \"ping\"", // returns true because they are equal
		"\"ping\" != \"pong\"", // returns true
		"5 > 6" // returns false
	];
	
	for(String condition: conditions) {
		Conditional conditional = Conditional.parse(condition);
		System.out.print(conditional.getResults());
	}
```

# Where this would be useful
Conditional would be useful for developers that want their plugins to be fully customizable.
By using PlaceholderAPI or any other placeholder plugins to parse placeholders before the condition is parsed.
<br>Click [here](https://github.com/iStudLion/RunicCore/blob/master/custom_items.yml#L18) to see how I used it inside my config.

```java
	String condition = "\"%player_name%\" == \"Notch\""; // this would be a string from your config
	String finalCondition = PlaceholderAPI.setPlaceholders(player, condition);
	boolean result = Conditional.parse(finalCondition).getResults();
	if(result) {
		// if the player's name is "Notch" this would be executed
	} else {
		// if the player's name is not "Notch" this would be executed
	}
```
