
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

## Code Structure

### 1. **Main Logic**
The program continuously asks the user for their coffee choice, handles payments, checks resources, and dispenses coffee or shows reports.

### 2. **Code Snippets**

Here’s the core script of the coffee machine program:

```python
from data import MENU
from data import resources

switch = 'on'
money = 0

def amount_payed():
    print("Please insert coins
")
    quarter = int(input("How many quarters? "))
    dime = int(input("How many dimes? "))
    nickle = int(input("How many nickels? "))
    penny = int(input("How many pennies? "))
    total = ((25 * quarter) + (10 * dime) + (5 * nickle) + penny) / 100
    return total

def change_calculation(variety):
    total = amount_payed()
    global price
    if total > price:
        change = total - MENU[variety]["cost"]
        print(f"Here is ${change} in change. Here's your {variety}. Enjoy!")
    elif total < price:
        print("Not enough money. Money refunded.")
        exit()

def report_generation(MENU, resources):
    global variety
    global switch
    if variety == 'report':
        return resources
    else:
        if resources['water'] >= MENU[variety]['ingredients']['water']:
            resources['water'] = resources['water'] - MENU[variety]['ingredients']['water']
        else:
            print("Not sufficient water")
            switch = 'off'
            exit()
        if variety != 'espresso':
            if resources['milk'] >= MENU[variety]['ingredients']['milk']:
                resources['milk'] = resources['milk'] - MENU[variety]['ingredients']['milk']
            else:
                print("Not sufficient milk")
        if resources['coffee'] >= MENU[variety]['ingredients']['coffee']:
            resources['coffee'] = resources['coffee'] - MENU[variety]['ingredients']['coffee']
        else:
            print("Not sufficient coffee")
            switch = 'off'
            exit()

        return resources

while switch == 'on':
    variety = input("What would you like to have? (espresso/latte/cappuccino)").lower()
    if variety == 'report':
        for key in report_generation(MENU, resources).items():
            print(key)
        print(f"Money: ${money}")
    elif variety == 'espresso' or variety == 'latte' or variety == 'cappuccino':
        price = MENU[variety]["cost"]
        report_generation(MENU, resources)
        change_calculation(variety)
        money = money + price
    elif variety == 'off':
        switch = 'off'
        print("Switching off! Goodbye!")
    else:
        print("Invalid input")
```

## Data Structure (From `data.py`)

### MENU

The **MENU** dictionary contains the available drinks with their ingredients and costs:

```python
MENU = {
    "espresso": {
        "ingredients": {
            "water": 50,
            "coffee": 18,
        },
        "cost": 1.5,
    },
    "latte": {
        "ingredients": {
            "water": 200,
            "milk": 150,
            "coffee": 24,
        },
        "cost": 2.5,
    },
    "cappuccino": {
        "ingredients": {
            "water": 250,
            "milk": 100,
            "coffee": 24,
        },
        "cost": 3.0,
    }
}
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
