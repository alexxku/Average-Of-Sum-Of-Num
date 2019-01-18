# Average-Of-Sum-Of-Num
Using C# console application, enter ten test scores and average them.

using System;

namespace SumNumAverage
{
    class Program
    {
        static void Main(string[] args)
        {
            //Variable Declarations
            double totalSum, totalAverage;
            Console.WriteLine("Enter ten test scores from 0 to 100.");
            //Assign and call method
            totalSum = sumValue();
            //Divide total sum with 10 to get average
            totalAverage = totalSum / 10;
            Console.WriteLine($"\nTotal Test Scores: {totalAverage}");
            //Average conditions to get letter grade
            letterGrade(totalAverage);
            Console.ReadLine();
        }




        //Add values 
        static double sumValue()
        {
            //Variables declaration and assignment for sumValue()
            double sum;
            double total = 0;

            //Repeat value entry 10 times
            for (int count = 0; count < 10; count++)
            {
                //Label reference
                Start:

                Console.Write($"\nTest Score {count + 1}: ");

                //Exception handler. Going to try the following block of code.
                try
                {
                    //Ask user for input and convert to double
                    sum = Convert.ToDouble(Console.ReadLine());
                    //Sum assignment with user input and sum arguements.
                    sum = repeatV(sum, count);
                    //total assignment with increasing input sum for every loop
                    total += sum;
                }
                //Catches error
                catch (Exception error)
                {
                    Console.WriteLine($"\n{error.Message.ToString()}");

                    //Goes to reference label
                    goto Start;
                }
            }
            //Return total
            return total;
        }

        //Looping negative and large numbers with two parameters for sum and count
        static double repeatV(double x, int y)
        {
            //Loop conditions
            while (x < 0 || x > 100)
            {
                Console.WriteLine("\nInvalid Test Score.");
                Console.Write($"\nTest Score {y + 1}: ");
                x = Convert.ToDouble(Console.ReadLine());
            }

            //Return x
            return x;
        }

        //Conditions for letter grade
        static void letterGrade (double average)
        {
            if (average < 60)
            {
                Console.WriteLine("\nGrade: F");
            }
            else if (average < 70)
            {
                Console.WriteLine("\nGrade: D");
            }
            else if (average < 80)
            {
                Console.WriteLine("\nGrade: C");
            }
            else if (average < 90)
            {
                Console.WriteLine("\nGrade: B");
            }
            else if (average <= 100)
            {
                Console.WriteLine("\nGrade: A");
            }

        }
    }
}
