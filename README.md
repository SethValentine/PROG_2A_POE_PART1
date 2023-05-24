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
    
Part 2
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
22; 23; 24 2023
© The Independent Institute of Education (Pty) Ltd 2023
Page 7 of 24
10. You must use generic collections to store the recipes, ingredients, steps, and no longer
arrays.
11. You are required to use a delegate to notify the user when a recipe exceeds 300 calories.
12. You are required to create a unit test to test the total calory calculation. 
