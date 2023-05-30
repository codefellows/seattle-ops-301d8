# Ops Challenge - Python Conditionals

## Demo Code

The demo code below introduces concepts necessary to complete the challenge.

```python
#!/usr/bin/env python3
# Script:                       Op Challenge 10
# Author:                       Hexx King
# Date of latest revision:      05/18/2023
# Purpose:                      Python Conditionals

# Variable Declarations
forecast = "rain"
sky = "cloudy"
temperature = 25
wind = "strong"
pollen_count = 80
humidity = 60

# Main

# if statement
if forecast == "rain":
  print("It is raining! Don't forget your umbrella!")

# if-else statement
if sky == "cloudy":
  print("The sky is cloudy.")
else:
  print("The sky is clear.")

# if-elif-else statement
if temperature < 40:
  print("It's chilly outside.")
elif temperature > 75:
  print("It's warm outside.")
else:
  print("The temperature is pretty moderate.")

# Nested if statement
if wind == "strong":
  print("It's a windy day.")
  if pollen_count > 70:
    print("It's windy and a high pollen count! Ah-choo!")
  elif pollen_count <= 70 and pollen_count > 30:
    print("Careful out there, it's windy with a moderate pollen count.")
  else:
    print("No worries, it may be windy but there is a low pollen count today.")
elif wind == "weak":
  print("The wind is calm today.")
else:
  print("Wind conditions are unknown.")

# Complex logical conditions
if forecast == "rain" or wind == "strong":
  print("The weather is too severe to be outside today!")
elif temperature > 75 and humidity > 70:
  print("It's hot and humid! Yuck!'")
elif not forecast == "rain" and temperature <= 50:
  print("This sounds like a perfect day.")
else:
  print("Weather conditions are unknown.")

# End

```
