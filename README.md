# VuelingBoxingUnboxing

This repository is the sample code developed to test: boxing, unboxing and extension methods on a simple console application.


### Extension Methods Included

*	Generate a number of elements and fill a list with them
    ```C#
	public static void FillListWithRandomValues(this List<object> list, int lengthOfList)
	{
		Random rnd = new Random();
		for (int i = 0; i < lengthOfList - 1; i++)
		{
			list.Add(rnd.Next(-50,200)); // boxing?
		}
	}
	```
	the method can be invoked this way:
	```C#
	exampleList.FillListWithRandomValues(40);
	```
*   Calcualtes the total sum of the values in a `List<object>`
	```C#
	public static int SumValuesOfList(this List<object> list)
	{
		int sum = 0;
		foreach (var i in list)
		{
			sum += (int)i; // unboxing
		}
		return sum;
	}
    ```
    in this case, also implement the unboxing of the values in the list to add them to `sum`
	and can be invoked like:
	```C#
	int exampleListSum = list.SumValuesOfList();
	```
*   The last extension method is used to calculate de average of the values in a list:
    ```C#
    public static int AverageListCalculator (this List<object> list)
	{
		int exampleListSum = list.SumValuesOfList();
		int exampleListAverage = exampleListSum / list.Count();
		return exampleListAverage;
	}
    ```
    I implement de method in the Main
    ```C#
    int listAverage = exampleList.AverageListCalculator();
    ```

    The last boxing case is:
    ```C#
	Console.WriteLine(string.Concat("The average value of the generated list of values is: ", listAverage)); // boxing
    ```
