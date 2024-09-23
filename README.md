# Fuel-your-Fitness
# Food database with calories and nutritional values per 100g or per unit or per 100ml
food_data = {
    'apple': {'calories_per_100g': 52, 'protein_per_100g': 0.3, 'fat_per_100g': 0.2, 'carbohydrates_per_100g': 14, 'sodium_per_100g': 1, 'fiber_per_100g': 2.4, 'sugar_per_100g': 10.4},
    'banana': {'calories_per_unit': 89, 'protein_per_unit': 1.1, 'fat_per_unit': 0.3, 'carbohydrates_per_unit': 23, 'sodium_per_unit': 1, 'fiber_per_unit': 2.6, 'sugar_per_unit': 12.2},
    'chicken breast': {'calories_per_100g': 165, 'protein_per_100g': 31, 'fat_per_100g': 3.6, 'carbohydrates_per_100g': 0, 'sodium_per_100g': 74, 'fiber_per_100g': 0, 'sugar_per_100g': 0},
    # Add more food items as needed
}

def calculate_nutrition(food_items):
    total_calories = 0
    total_protein = 0
    total_fat = 0
    total_carbohydrates = 0
    total_sodium = 0
    total_fiber = 0
    total_sugar = 0
    
    for food, quantity in food_items.items():
        if food in food_data:
            if 'calories_per_100g' in food_data[food]:
                # If the food is measured in grams
                item_calories = (food_data[food]['calories_per_100g'] / 100) * quantity
                item_protein = (food_data[food]['protein_per_100g'] / 100) * quantity
                item_fat = (food_data[food]['fat_per_100g'] / 100) * quantity
                item_carbohydrates = (food_data[food]['carbohydrates_per_100g'] / 100) * quantity
                item_sodium = (food_data[food]['sodium_per_100g'] / 100) * quantity
                item_fiber = (food_data[food]['fiber_per_100g'] / 100) * quantity
                item_sugar = (food_data[food]['sugar_per_100g'] / 100) * quantity
            elif 'calories_per_unit' in food_data[food]:
                # If the food is measured by units
                item_calories = food_data[food]['calories_per_unit'] * quantity
                item_protein = food_data[food]['protein_per_unit'] * quantity
                item_fat = food_data[food]['fat_per_unit'] * quantity
                item_carbohydrates = food_data[food]['carbohydrates_per_unit'] * quantity
                item_sodium = food_data[food]['sodium_per_unit'] * quantity
                item_fiber = food_data[food]['fiber_per_unit'] * quantity
                item_sugar = food_data[food]['sugar_per_unit'] * quantity

            # Print the individual item's nutritional values
            print(f"{food.capitalize()}:")
            print(f"  Calories: {item_calories:.2f} kcal")
            print(f"  Protein: {item_protein:.2f} g")
            print(f"  Fat: {item_fat:.2f} g")
            print(f"  Carbohydrates: {item_carbohydrates:.2f} g")
            print(f"  Sodium: {item_sodium:.2f} mg")
            print(f"  Fiber: {item_fiber:.2f} g")
            print(f"  Sugar: {item_sugar:.2f} g\n")

            total_calories += item_calories
            total_protein += item_protein
            total_fat += item_fat
            total_carbohydrates += item_carbohydrates
            total_sodium += item_sodium
            total_fiber += item_fiber
            total_sugar += item_sugar
        else:
            print(f"{food} is not in the database.")

    return total_calories, total_protein, total_fat, total_carbohydrates, total_sodium, total_fiber, total_sugar

# Taking user input
food_items = {}
while True:
    food = input("Enter food item (or 'done' to finish): ").lower()
    if food == 'done':
        break
    quantity = float(input(f"Enter quantity for {food}: "))
    food_items[food] = quantity

# Calculate and display nutrition for each item
calories, protein, fat, carbohydrates, sodium, fiber, sugar = calculate_nutrition(food_items)

# Print total nutritional values
print("Total Nutritional Values:")
print(f"Total Calories: {calories:.2f} kcal")
print(f"Total Protein: {protein:.2f} g")
print(f"Total Fat: {fat:.2f} g")
print(f"Total Carbohydrates: {carbohydrates:.2f} g")
print(f"Total Sodium: {sodium:.2f} mg")
print(f"Total Fiber: {fiber:.2f} g")
print(f"Total Sugar: {sugar:.2f} g")
