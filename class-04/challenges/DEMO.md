# Ops Challenge - Conditionals in Menu Settings

## Guess Random Number

```bash
#!/bin/bash

# Set a random number between 1 and 100
# target=$RANDOM
# let "target %= 100"
# let "target += 1"

# or set our own target...
target=42

# Loop until the user guesses the correct number
while true; do
    read -p "Guess a number between 1 and 100: " guess

    # Check if the guess is correct
    if [ $guess -eq $target ]; then
        echo "Congratulations! You guessed the number."
        exit 0
    fi

    # Check if the guess is too high or too low
    if [ $guess -gt $target ]; then
        echo "Your guess is too high."
    else
        echo "Your guess is too low."
    fi

done

```

## Menu System Demo

```bash
#!/bin/bash

while true; do
    clear
    echo "Do you like cats or dogs, or something else?"
    echo "1. Cats"
    echo "2. Dogs"
    echo "3. Other"
    echo "4. Exit"
    read choice

    if [[ $choice == 1 ]]; then
        echo "Cats are cool"
        # The -p option is used with the read command to display a prompt to the user and wait for them to enter input.
        read -p "Press Enter to continue"
    elif [[ $choice == 2 ]]; then
        echo "Dogs are great"
        read -p "Press Enter to continue"
    elif [[ $choice == 3 ]]; then
        echo "Oh, you are not a cat or dog person!"
        read -p "What is your pet of choice? " pet
        echo "I like $pet too!"
        read -p "Press Enter to continue"
    elif [[ $choice == 4 ]]; then
        echo "See ya later!"
        exit 0
    else
        echo "Invalid choice"
        read -p "Press Enter to continue"
    fi
done
```
