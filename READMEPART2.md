# PROG_2A_POE_PART2
My POE
Part 2

Project Description

For this part of the poe we have to use the code we have and update it with the requirments that they ask for.The requirments are:
1. The user shall be able to enter an unlimited number of recipes.
2. The user shall be able to enter a name for each recipe.
3. The software shall display a list of all the recipes to the user in alphabetical order by name.
4. The user can choose which recipe to display from the list.
5. For each ingredient, the user shall additionally be able to enter:
a. The number of calories, and
b. The food group that the ingredient belongs to.
6. The software shall calculate and display the total calories of all the ingredients in a recipe.
7. The software shall notify the user when the total calories of a recipe exceed 300. 
Non-functional requirements:
8. You are required to use internationally acceptable coding standards. Include
comprehensive comments explaining variable names, methods, and the logic of
programming code.
9. You are required to use classes.
10. You must use generic collections to store the recipes, ingredients, steps, and no longer
arrays.
11. You are required to use a delegate to notify the user when a recipe exceeds 300 calories.
12. You are required to create a unit test to test the total calory calculation. 

I have edited my code from part 1 and made to how they want it for part 2 so my code starts out printing the same as how it is for part 1 with Sanales Recipe Book
Difference is now when run the program it will start with 3 instructions where you can add recipe, view recipes or exit.
When you click 1 for adding a recipe it will direct you to add a recipe
Now you can enter the name for the recipe which they ask for in the requirments
Then you enter the number of ingreidents like in part 1
then you can enter the name of that ingredient
then the quantity of the ingredient
then the unit of measurment 
then for part 2 we have to add the calrories and also add the different food groups that people can pick from
at the end you can view the recipe and it will tell you how much calories are there all together in the view recipes
    
How to Compile and Run the Software.   

 When you begen with program it shows the same why i have for part 1 using getters and setters to run the class recipe i have 3 classes which is Recipe, Ingrident and RecipeCalculator.The Recipe class represents a recipe and contains properties such as RecipeName, NumOfIngredients, Ingredients, NumOfSteps, and Steps.The Ingredient class represents an ingredient and contains properties such as Name, Quantity, Unit, Calories, and FoodGroup. The RecipeCalculator class contains a method called CalculateTotalCalories that calculates the total number of calories in a list of ingredients. The Program class represents a recipe book application that allows users to add, view clear and exit recipes. The class contains a Main method that runs the application and a number of other methods that are used to add and view recipes.
This is the first class 
class Recipe
    /* Use getters and setters the instance
    is the recipe and is a public access modifer
    so they can be accessed from outside the class
    the setter would be the NumOfIngreidents and the getter
    would be the Ingreidents 
    */
    {
        public string RecipeName { get; set; } // get,set to enter name of the recipe
        public int NumOfIngredients { get; set; } //get,set for NumOfIngreidents 
        public List<Ingredient> Ingredients { get; set; }// List the number of Ingreidents
        public int NumOfSteps { get; set; } // List the steps in integers 
        public List<string> Steps { get; set; }

        public Recipe(string name)
        {
            RecipeName = name;
            Ingredients = new List<Ingredient>();
            Steps = new List<string>();
        }

        public void Print()
        {
            Console.WriteLine($"Recipe: {RecipeName}");//output to ask the name of the recipe
            Console.WriteLine("Ingredients:");
            for (int i = 0; i < NumOfIngredients; i++)
            {
                Console.WriteLine($"{Ingredients[i].Name}: {Ingredients[i].Quantity} {Ingredients[i].Unit} ({Ingredients[i].FoodGroup})");
            }
            Console.WriteLine("Steps:");
            for (int i = 0; i < NumOfSteps; i++)
            {
                Console.WriteLine($"{i + 1}. {Steps[i]}");
            }
        }
       
      
       

        public delegate void RecipeCalorieNotification(); // using delagate feature for calorie notifcation

        public RecipeCalorieNotification NotifyCalorieExceedance;


        public void ExplainCalorieRange()
        {
            RecipeCalculator calculator =  new RecipeCalculator();
            double totalCalories = calculator.CalculateTotalCalories(Ingredients);

            Console.WriteLine($"Total Calories: {totalCalories}");

            if (totalCalories < 100)
            {
                Console.ForegroundColor = ConsoleColor.Green; // shows a green colour when its low in calroies
                Console.WriteLine("This recipe is low in calories.");
                Console.ResetColor();
            }
            else if (totalCalories >= 100 && totalCalories <= 300) // will show that the calories are moderate amount in calroies
            {
                Console.ForegroundColor = ConsoleColor.Yellow; // shows a yellow colour when its moderate in calroies
                Console.WriteLine("This recipe has a moderate amount of calories.");
                Console.ResetColor();
            }
            else
            {
                Console.ForegroundColor = ConsoleColor.Red;  // shows a red colour when the user has 
                Console.WriteLine("This recipe is high in calories.");
                Console.ResetColor();

                NotifyCalorieExceedance?.Invoke();
            }
        }
    }
    The Recipe class also includes a delegate RecipeCalorieNotification and an event NotifyCalorieExceedance. The ExplainCalorieRange method calculates the total calories of the recipe and displays whether it is low, moderate, or high in calories. If the recipe is high in calories, it invokes the NotifyCalorieExceedance event. When the user chooses to view recipes, the method displays a list of all the recipes in alphabetical order. The user can then select a recipe to view. The method displays the name of the recipe, the ingredients, and the steps. It also uses the RecipeCalculator class to calculate the total number of calories in the recipe and displays a message indicating whether the recipe is low, moderate, or high in calories. If the recipe is high in calories, the method also invokes a delegate called NotifyCalorieExceedance.

     class RecipeCalculator
    {
        public double CalculateTotalCalories(List<Ingredient> ingredients)
        {
            double totalCalories = 0;
            foreach (var ingredient in ingredients)
            {
                totalCalories += ingredient.Calories;
            }
            return totalCalories;
        }
    }
    This class is own its own because we had to run unit test on it to check if the calculation is correct. The ExplainCalorieRange method calculates the total calories of the recipe and displays whether it is low, moderate, or high in calories. If the recipe is high in calories, it invokes the NotifyCalorieExceedance event

   class Ingredient
    {
        public string Name { get; set; } // get, set to get the recipe name
        public double Quantity { get; set; } // get, set to get the quanity
        public string Unit { get; set; } // get, set to get unit of measurment
        public double Calories { get; set; } // get, set to get the calories
        public string FoodGroup { get; set; } // get,set to add the food group its in
    }
 private static readonly List<string> AvailableFoodGroups = new List<string> { "Starchy foods", "Vegetables and fruits", "Dry beans, peas, lentils and soya", "Chicken, fish, meat and eggs", "Milk and dairy products", "Fats and Oils", "Water" }; 


    public static void DisplayFoodGroupOptions()
    {
        Console.WriteLine("Available Food Groups:");
        for (int i = 0; i < AvailableFoodGroups.Count; i++)
        {
            Console.WriteLine($"{i + 1}. {AvailableFoodGroups[i]}");
        }
    }

    static void Main(string[] args)
    {
        List<Recipe> recipes = new List<Recipe>();
        /* 
       Used to store the recipe which grows
       dynamically and can store unlimited recipes 
       */


        while (true)
        {
            Console.WriteLine("Sanele's Recipe Book");
            Console.WriteLine();
            Console.WriteLine("Pick the command you would like to use:");
            Console.WriteLine("1. Add Recipe");
            Console.WriteLine("2. View Recipes");
            Console.WriteLine("3. Clear");
            Console.WriteLine("4. Exit");
            Console.Write("Enter your choice: ");

            string choice = Console.ReadLine();

            switch (choice)
            {
                case "1":
                    // allows the user to enter the name of the recipe
                    Console.WriteLine("Enter the name of the recipe:");
                    string recipeName = Console.ReadLine();
                    Recipe newRecipe = new Recipe(recipeName);

                    // shows the number of ingreidents
                    Console.WriteLine("Enter the number of ingredients you would like to add:");

                    //use exception when a user enters an invalid input like a non-numeric value
                    if (!int.TryParse(Console.ReadLine(), out int numOfIngredients))
                    {
                        Console.WriteLine("Invalid input. Please enter a valid number.");
                        break;
                    }
                    newRecipe.NumOfIngredients = numOfIngredients;

                    for (int i = 0; i < newRecipe.NumOfIngredients; i++)
                    {
                        Console.WriteLine($"Please enter the name of ingredient {i + 1}:");
                        string name = Console.ReadLine();

                        Console.WriteLine($"Please enter the quantity of ingredient {i + 1}:");

                        //use exception when a user enters an invalid input like a non-numeric value
                        if (!double.TryParse(Console.ReadLine(), out double quantity))
                        {
                            Console.WriteLine("Invalid input. Please enter a valid number.");
                            break;
                        }

                        Console.WriteLine($"Please enter the unit of measurment for the ingredient {i + 1}:");
                        string unit = Console.ReadLine();

                        Console.WriteLine($"Please enter the number of calories for ingredient {i + 1}:");
                        //use exception when a user enters an invalid input like a non-numeric value
                        if (!double.TryParse(Console.ReadLine(), out double calories))
                        {
                            Console.WriteLine("Invalid input. Please enter a valid number.");
                            break;
                        }


                        Console.WriteLine($"Please select the food group for ingredient {i + 1}:");
                        DisplayFoodGroupOptions();

                        //use exception when a user enters an invalid input like a non-numeric value
                        if (!int.TryParse(Console.ReadLine(), out int foodGroupIndex) || foodGroupIndex < 1 || foodGroupIndex > AvailableFoodGroups.Count)
                        {
                            Console.WriteLine("Invalid input. Please enter a valid number.");
                            break;
                        }

                        string foodGroup = AvailableFoodGroups[foodGroupIndex];

                        newRecipe.Ingredients.Add(new Ingredient { Name = name, Quantity = quantity, Unit = unit, Calories = calories, FoodGroup = foodGroup });
                    }

                    Console.WriteLine("Please enter the number of steps:");

                    //use exception when a user enters an invalid input like a non-numeric value
                    if (!int.TryParse(Console.ReadLine(), out int numOfSteps))
                    {
                        Console.WriteLine("Invalid input. Please enter a valid number.");
                        break;
                    }
                    newRecipe.NumOfSteps = numOfSteps;

                    for (int i = 0; i < newRecipe.NumOfSteps; i++)
                    {
                        Console.WriteLine($"Please enter step {i + 1}:");
                        string step = Console.ReadLine();
                        newRecipe.Steps.Add(step);
                    }

                    recipes.Add(newRecipe);
                    break;

                // display no recipes found if recipe is not there
                case "2":
                    if (recipes.Count == 0)
                    {
                        Console.WriteLine("No recipes found.");
                    }
                    else
                    {
                        recipes = recipes.OrderBy(r => r.RecipeName).ToList();
                        //OrderBy method stores the recipes in Alphabetical

                        Console.WriteLine("Recipes:");
                        for (int i = 0; i < recipes.Count; i++)
                        {
                            Console.WriteLine($"{i + 1}. {recipes[i].RecipeName}");
                        }

                        Console.WriteLine("Enter the number of the recipe you want to view:");

                        //use exception when a user enters an invalid input like a non-numeric value
                        if (!int.TryParse(Console.ReadLine(), out int recipeIndex) || recipeIndex < 1 || recipeIndex > recipes.Count)
                        {
                            Console.WriteLine("Invalid recipe number.");
                            break;
                        }
                        Recipe selectedRecipe = recipes[recipeIndex - 1];
                        selectedRecipe.Print();
                        selectedRecipe.ExplainCalorieRange();
                    }
                    break;

                case "3":
                    // clear recipe
                    recipes.Clear();
                    Console.WriteLine("Recipes Cleared.");
                    return;
                case "4":
                    // Exit
                    return;

                default:
                    Console.WriteLine("Invalid choice. Please enter a valid choice.");
                    break;
            }

            Console.WriteLine();
        }
    }


 This is the Ingreident class which  represents an ingredient and has properties such as Name, Quantity, Unit, Calories, and FoodGroup all in get and set methods. The DisplayFoodGroupOptions method displays the available food groups to choose from.The Main method is the entry point of the program. It starts an infinite loop that displays a menu of options for the user to choose from.

Inside the loop, the user can choose to add a recipe, view existing recipes, clear the recipes, or exit the program.
When adding a recipe, the user is prompted to enter the recipe's name, number of ingredients, and details of each ingredient (name, quantity, unit, calories, and food group), as well as the number of steps and the steps themselves.
When viewing recipes, the existing recipes are displayed in alphabetical order, and the user can choose a recipe to view its details and calorie range.
If the recipe is high in calories, it triggers the NotifyCalorieExceedance event.
The program continues to loop until the user chooses to exit.
 Possible bugs
If the user enters an invalid input, such as a non-numeric value, the program will throw an error.
If the user enters a recipe name that already exists, the program will not handle it and may cause issues.
If the user enters an ingredient with a negative quantity or calories, the program will not handle it and may cause issues.
 This is a detailed discription how to complile and run the software

 My GitHub Repository
  https://github.com/SethValentine/PROG_2A_POE_PART1


