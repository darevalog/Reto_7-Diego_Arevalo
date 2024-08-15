# Reto #7 // Diego Arévalo

This repository implement a new Class that creates and iterable with all the items in an order, it should allow looping and contain all item attributes.

```python
import os
os.system("cls")

class menuitem:
    def __init__(self, name, price):
        self.name = name
        self.price = price

class  appetizer(menuitem):
    def __init__(self, name, price, calories):
        super().__init__(name, price)
        self.calories = calories

    def __str__(self):
        return f"{self.name}: ${self.price} ({self.calories} cal)"
    
class main_course(menuitem):
    def __init__(self, name, price, calories, protein):
        super().__init__(name, price)
        self.calories = calories
        self.protein = protein

    def __str__(self):
        return f"{self.name}: ${self.price} ({self.calories} cal, {self.protein} g)"

class beverage(menuitem):
    def __init__(self, name, price, volume):
        super().__init__(name, price)
        self.volume = volume

    def __str__(self):
        return f"{self.name}: ${self.price} ({self.volume} ml)"
    
class order(menuitem):
    def __init__(self):
        self.items = []

    def add_item(self, item):
        self.items.append(item)

    def calculate_total(self):
        total = 0
        for item in self.items:
            total += item.price
        return total

    def apply_discount(self):
        discount = 0.1
        total = self.calculate_total()
        discounted_total = total - (total * discount)
        return discounted_total

# Creación de menú
appetizer1 = appetizer("Guacamole", 5.50, 150)
appetizer2 = appetizer("Nachos", 6.50, 200)
appetizer3 = appetizer("Queso fundido", 7.50, 250)
appetizer4 = appetizer("Tostadas", 4.50, 100)
main_course1 = main_course("Tacos", 12.50, 300, 20)
main_course2 = main_course("Burrito", 10.50, 400, 25)
main_course3 = main_course("Enchiladas", 11.50, 350, 22)
main_course4 = main_course("Quesadillas", 9.50, 250, 18)
beverage1 = beverage("Margarita", 8.50, 250)
beverage2 = beverage("Tequila", 7.50, 200)
beverage3 = beverage("Soda", 2.50, 500)
beverage4 = beverage("Water", 1.50, 500)

a = "MENU"
b = a.center(50, "-")
print(b)
print("\nAppetizers:")
print(appetizer1)
print(appetizer2)
print(appetizer3)
print(appetizer4)
print("\nMain courses:")
print(main_course1)
print(main_course2)
print(main_course3)
print(main_course4)
print("\nBeverages:")
print(beverage1)
print(beverage2)
print(beverage3)
print(beverage4)
print()


# Creación de orden por input del cliente
order1 = order()

while True:
    c = "ORDER"
    d = c.center(50, "-")
    print(d)
    print()
    print("1. Add appetizer")
    print("2. Add main course")
    print("3. Add beverage")
    print("4. Finish order")
    choice = input("\nEnter your choice: ")

    if choice == "1":
        print("\nAppetizers:")
        print("1. Guacamole")
        print("2. Nachos")
        print("3. Queso fundido")
        print("4. Tostadas")
        appetizer_choice = input("\nEnter appetizer choice: ")

        if appetizer_choice == "1":
            order1.add_item(appetizer1)
        elif appetizer_choice == "2":
            order1.add_item(appetizer2)
        elif appetizer_choice == "3":
            order1.add_item(appetizer3)
        elif appetizer_choice == "4":
            order1.add_item(appetizer4)
        else:
            print("\nInvalid choice. Please try again.")

    elif choice == "2":
        print("\nMain courses:")
        print("1. Tacos")
        print("2. Burrito")
        print("3. Enchiladas")
        print("4. Quesadillas")
        main_course_choice = input("\nEnter main course choice: ")

        if main_course_choice == "1":
            order1.add_item(main_course1)
        elif main_course_choice == "2":
            order1.add_item(main_course2)
        elif main_course_choice == "3":
            order1.add_item(main_course3)
        elif main_course_choice == "4":
            order1.add_item(main_course4)
        else:
            print("\nInvalid choice. Please try again.")

    elif choice == "3":
        print("\nBeverages:")
        print("1. Margarita")
        print("2. Tequila")
        print("3. Soda")
        print("4. Water")
        beverage_choice = input("\nEnter beverage choice: ")

        if beverage_choice == "1":
            order1.add_item(beverage1)
        elif beverage_choice == "2":
            order1.add_item(beverage2)
        elif beverage_choice == "3":
            order1.add_item(beverage3)
        elif beverage_choice == "4":
            order1.add_item(beverage4)
        else:
            print("\nInvalid choice. Please try again.")

    elif choice == "4":
        break

    else:
        print("\nInvalid choice. Please try again.")

e = "FINAL ORDER"
f = e.center(50, "-")
print(f)
for item in order1.items:
    print(item)
print(f"\nTotal: ${order1.calculate_total()}")
print(f"Total with discount: ${order1.apply_discount()} (10% of discount)\n")

class OrderIterator:
    def __init__(self, order):
        self.order = order
        self.index = 0

    def __iter__(self):
        return self

    def __next__(self):
        if self.index < len(self.order.items):
            item = self.order.items[self.index]
            self.index += 1
            return item
        else:
            raise StopIteration

order_iterator = OrderIterator(order1)

for item in order_iterator:
    print(f"Item: {item.name}")
    print(f"Price: ${item.price}")
    if isinstance(item, appetizer):
        print(f"Calories: {item.calories} cal")
    elif isinstance(item, main_course):
        print(f"Calories: {item.calories} cal")
        print(f"Protein: {item.protein} g")
    elif isinstance(item, beverage):
        print(f"Volume: {item.volume} ml")
    print()
```
> :shipit: Diego Alejandro Arévalo Guevara. August 14, 2024.
