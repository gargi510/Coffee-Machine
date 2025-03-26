
# Coffee Machine Python Project

## Project Description

Welcome to the **Coffee Machine** Python program! ☕ This interactive simulation allows users to choose from three coffee options: **Espresso**, **Latte**, and **Cappuccino**. Users can insert coins to pay for their coffee and receive change if the payment exceeds the cost. The program ensures there are sufficient resources (water, milk, coffee) before making the coffee.

This project demonstrates basic Python skills, including user input, control flow, and data manipulation.

## How to Use

1. **Start the Program**: Run the Python script in your terminal or IDE:
   ```bash
   python coffee_machine.py
   ```

2. **Select Your Coffee**: Choose one of the following options:
   - Type **`espresso`** for Espresso
   - Type **`latte`** for Latte
   - Type **`cappuccino`** for Cappuccino
   - Type **`report`** to view current resources and money
   - Type **`off`** to turn off the machine

3. **Insert Coins**: The machine will ask how many **quarters**, **dimes**, **nickels**, and **pennies** you'd like to insert. It will then calculate the total.

4. **Wait for Coffee**: If your payment is sufficient, the machine will make your coffee and return any change due.

5. **Check Resources**: You can type **`report`** to check how much water, milk, and coffee is left, as well as how much money has been collected.

6. **Turn Off**: Type **`off`** to stop the machine.

## Example Usage

```
What would you like to have? (espresso/latte/cappuccino): espresso
Please insert coins

How many quarters? 2
How many dimes? 1
How many nickels? 1
How many pennies? 3
Here is $0.56 in change. Here's your espresso. Enjoy!

What would you like to have? (espresso/latte/cappuccino): report
{'water': 300, 'milk': 200, 'coffee': 100}
Money: $1.50

What would you like to have? (espresso/latte/cappuccino): off
Switching off! Goodbye!
```

### Resources

The **resources** dictionary keeps track of the available quantities of water, milk, and coffee. These values decrease as users make coffee:

```python
resources = {
    "water": 300,
    "milk": 200,
    "coffee": 100,
}
```

## Requirements

- Python 3.x

## Conclusion

Enjoy your virtual coffee machine! This project is a great way to practice Python, manage resources, and simulate a simple real-world system. Feel free to fork and modify the code to add more features, like adding more drinks or improving the user interface.

---

**Developed by Gargi Mishra** – Hope you enjoy your coffee! ☕🎉
