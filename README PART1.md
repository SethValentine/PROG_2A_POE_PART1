# PROG_2A_POE_PART1
My POE
Part 1

Project Description
In the Poe they gave us a background on why we have to make the application we are making they gave an example of how sanele was invited to a birthday party and how there was good food. Sanele wants to learn how to cook so we have delveleoped a recipe book on how to start cooking.
Before we can start building anything we have to writing down what the real problem is and create a pseudo code on how we going to solve this problem and how are going to begin coding.
How to Compile and Run the Software.
We started off with creating the program to state Snaneles Recipe Book
When loading the application you will get  6 instructions you can either add, print, scale, reset, clear or quit
Add: Here you add the number of ingredients you would like to the menu. You ony use integers and you put the amount of how much ingreidents you would like to add whether it be 1,2,3, 4 or any amount of ingreidents you would like. 
After adding the number you will be ask the name the ingreident that you want like milk,eggs, flour ect.
You will then enter the quantiy of the ingrdient you would like then the unit of mearsument for the ingrdients
That will be all depending on how much ingreidents you want

You can then print out the entire ingredients and would give out everything you have typed in
You scale the recipe by a factor of 0.5, 2 or 3
In my Code i only have 2 classes 1 would be the Recipe class and the other is the Ingredient Class
The Recipe class has the following properties in them:
NumOfIngrients: here i have an integer showing the amount of ingreidents in the recipe
Ingredients: this is a list of the inredient object which shows all the ingreidents
NumOfSteps: This is an integer that shows all the steos 
Steps: Gives the list of strings that shows the steps

The next class would be the Ingreident Class which has there properties that is:
Name: this is a string that shows the name of the ingrident
Quantity: a double which shows the quantiy of the ingreident 
Unit: the string which gives the unit of measurnemnt 

There is also a main method which is switch statement that has:
add: the user can add an ingredient
print: prints the recipe you are busy with
scale:scales the recipe you are busy with by 0.5,2 or 3
reset: resets everything to how it is in the beginning
clear:clears the whole program
quit: leaves the program
The reason why i used a switch statement is so that it can handle all the different commands. for example when the user enters an invaid command it will display an error message.

class Program
{
    class Recipe 
    /* Use getters and setters the instance
        is the recipe and is a public access modifer
        so they can be accessed from outside the class
    the setter would be the NumOfIngreidents and the getter would be the Ingreidents 
     */
    {
        public int NumOfIngredients { get; set; } //get,set for NumOfIngreidents 
        public List<Ingredient> Ingredients { get; set; } // List the number of Ingreidents
        public int NumOfSteps { get; set; } // List the steps in integers 
        public List<string> Steps { get; set; }

       
    In the start of the program i have class called Recipe which has 2 properties:
    NumOfIngredients and Ingreidents
    I made getters and setters so that i can make my getter private and then it cant be accessed from outside the classs.
    The Setter is public so that it can be accessed from outside the class and make it eassier for me to work from outside the class

    I made the object called Program that contains a Recipe instance variable named recipe which is initialized to null.
    After that is made initialize the recipe instance variable, i used a constructor that takes one argument - an int value representing how many ingredients are in this particular recipe (NumOfIngreidents). The number that is there will  be used as an inital value for NumOfIngreidents property on every new object created using this program's Recipe constructor.
    Here the setter for this varible in this class will be the function numOfIngredients and the getter would be the function ingredients.

     public Recipe()
        {
            Ingredients = new List<Ingredient>();
            Steps = new List<string>();
        }
    The code starts with a class called Recipe.
    It has two properties, Ingredients and Steps.
    The code also contains a constructor that initializes the list of ingredients to an empty list.
    public void Print()
        /*allow the user to print out the recipe which
         * has the ingredients and steps
         */
        {
            Console.WriteLine("Ingredients:"); //No paramaters so does not take input from users
            for (int i = 0; i < NumOfIngredients; i++) //Uses a for loop to print out the  name,quantity and unit of measurment
            {
                Console.WriteLine($"{Ingredients[i].Name}: {Ingredients[i].Quantity} {Ingredients[i].Unit}");
            }
            Console.WriteLine("Steps:");//print out the steps for the user
            for (int i = 0; i < NumOfSteps; i++)
            {
                Console.WriteLine($"{i + 1}.{Steps[i]}"); //for each step it prints out the step number and text of the step
            }
        }
This method is called print and it is here to print out the method is used by the user to print out the recipe which has the ingredients and steps.
This allows the user  print out their recipe by analyzing what they have entered into their program so far (the ingredients and steps).
I first created an instance variable called NumOfSteps which stores how many steps are in total in this particular recipe.
hen it loops through all of its step lists (one for each type) and prints them out one at a time on separate lines using Console's WriteLine function with some formatting information added to make them easier to read on paper or screen depending on where you're running your program from.

 public void Scale(double factor) // Scales the recipe by a factor of 0.5, 2 or 3
        {
            foreach (var ingredient in Ingredients) //uses foreach method to iterate all of the ingredients
            {
                ingredient.Quantity *= factor; //foreach ingredient it multiplies its quantity by the scalling factor
            }
        }
    The Scale method iterates through all of the ingredients, multiplying their quantity by factor which is passed into it as a parameter.
 The code is meant to scale the recipe by a factor of 0.5, 2 or 3.
 The foreach loop iterates through all of the ingredients and multiplies their quantity by the scaling factor.

  public void Clear()// this will remove all the ingredients 
        {
            NumOfIngredients = 0; // sets the value to 0 so NumOfIngreidents will be cleared
            Ingredients.Clear(); // Clears all the content in Ingredients when the user wants to clear it
            NumOfSteps = 0; // sets the value to 0 so steps will be cleared
            Steps.Clear(); //Clears all the content in Steps when the user wants to clear it
        }
    
Here when the user chooses to clear a recipe, the program calls the Clear method of the Recipe class, which removes all the ingredients and steps from the recipe.
 public void Scale() // this scale is to divede the vairable 
        {
            foreach (var ingredient in Ingredients)
            {
                ingredient.Quantity /= 2;
            }
        }
    }
    When the user chooses to reset a recipe, the program calls the Scale method of the Recipe class with no arguments, which divides the quantities of the ingredients by 2 and prints the reset recipe.

    class Ingredient 
    /*this getter and setter class calls a string witch
     * is the name the quantity which is a double and
     * the unit which is a string 
     */
    {
        public string Name { get; set; }
        public double Quantity { get; set; }
        public string Unit { get; set; }
    }
    The Ingredient class represents an ingredient and has properties for the name, quantity, and unit of measurement calling  the getters and setters

    static void Main(string[] args)
    {
        /* This main  method will open up a menu to add a new recipe,
         * entering a name,printing it or scaling it
         *When the user enters an  invalid comment an error is inserted on the console
         */
        Recipe recipe = new Recipe(); 
        while (true)
        {
            Console.WriteLine("Sanele's Recipe Book");
            Console.WriteLine();
            Console.WriteLine("Pick the command you would like to use (add, print, scale, reset, clear, or quit):");
            string command = Console.ReadLine();

            switch (command) // using a swtich
            {
                case "add": // allows the user to add ingredients 
                    Console.WriteLine("Enter the number of ingredients you would like to add:");
                    recipe.NumOfIngredients = int.Parse(Console.ReadLine());
                    /* This for loop presents the user with a menu of 
                     * optionns to interact with the recipe NumOfIngridents Class      
                    */


                    for (int i = 0; i < recipe.NumOfIngredients; i++)
                    {
                        Console.WriteLine($"Please enter the name of ingredient you would like to insert {i + 1}:");
                        string name = Console.ReadLine();

                        Console.WriteLine($"Please enter the quantity of ingredient you would like to insert {i + 1}:");
                        double quantity = double.Parse(Console.ReadLine());

                        Console.WriteLine($"Please enter the unit of ingredient you would like to insert {i + 1}:");
                        string unit = Console.ReadLine();
                        //Here the user can enter the details for the recipe(name,quantity,UnitOfMeasurnment
                        recipe.Ingredients.Add(new Ingredient { Name = name, Quantity = quantity, Unit = unit });
                    }
                   
                    Console.WriteLine("Please enter the number of steps:");
                    recipe.NumOfSteps = int.Parse(Console.ReadLine());

                    for (int i = 0; i < recipe.NumOfSteps; i++)
                    {
                        Console.WriteLine($"Please enter step {i + 1}:");
                        string step = Console.ReadLine();
                        recipe.Steps.Add(step);
                    }

                    break;
                    //Use a switch statement
                case "print":
                    recipe.Print();
                    break;

                case "scale":
                    Console.WriteLine("Enter the scaling factor (0.5, 2, or 3):");
                    double factor = double.Parse(Console.ReadLine());
                    recipe.Scale(factor);
                    recipe.Print();
                    break;

                case "reset":
                    recipe.Scale();
                    recipe.Print();
                    break;

                case "clear":
                    recipe.Clear();
                    break;

                case "quit":
                    return;
                    //The program exists when the choses the quit option
                default:
                    Console.WriteLine("Invalid choice. Please enter a valid choice.");
                    break;
            }
        }

    }
}

Finally we have the main method which is the entry point of the program and contains a loop that displays a menu of options to the user. The user can choose to add a new recipe, print a recipe, scale a recipe, reset a recipe, clear a recipe, or quit the program.
When the user chooses to add a new recipe, the program prompts the user to enter the number of ingredients and the details of each ingredient. The program then prompts the user to enter the number of steps and the details of each step.

There are possible bugs that the code might have for example:
If the user enters an invalid input, such as a non-numeric value for the number of ingredients or steps, the program will throw an error.
If the user enters an invalid scaling factor, such as a non-numeric value or a value that is not 0.5, 2, or 3, the program will throw an error.
If the user enters an invalid command, the program will display an error message but will not prompt the user to enter a valid command.

My GitHub Repository
https://github.com/SethValentine/PROG_2A_POE_PART1
    
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
 
 This is a detailed discription how to complile and run the software

 My GitHub Repository
  https://github.com/SethValentine/PROG_2A_POE_PART1

