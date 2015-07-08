# Function

# Overloading

```
class Program
{
    static void Main(string[] args)
    {

        Console.WriteLine(square(15, 25));

        Console.WriteLine(square(1.5, 2.5));

        Console.WriteLine(square("18", "30"));


        int c = 100;

        add(ref c, 1);
        add(ref c, 1);
        add(ref c, 1);

        Console.WriteLine("c = {0}", c);


        string num = "12";
        int result;

        bool r = int.TryParse(num, out result);

        int v;

        add(c, 1, out v);

        Console.WriteLine("v = {0}", v);


        int x, y;

        bool r1 = prompt("請輸入一個整數:", out x);
        bool r2 = prompt("請再輸入一個整數:", out y);

        Console.WriteLine("{0}, {1}", r1, x);
        Console.WriteLine("{0}, {1}", r2, y);

        Console.ReadKey();
    }

    static bool prompt(string msg, out int value)
    {
        Console.Write(msg);
        return int.TryParse(Console.ReadLine(), out value);
    }

    // by Value (傳值)
    // by Reference (傳址)
    static void add(ref int x, int n)
    {
        x += n;
        Console.WriteLine("x = {0}", x);
    }

    static void add(int x, int n, out int z)
    {
        z = x + n;
        Console.WriteLine("z = {0}", z);
    }

    // Function Overloading

    static int square(int w, int h)
    {
        Console.WriteLine("> int <");
        return w * h;
    }

    static double square(double w, double h)
    {
        Console.WriteLine("> double <");
        return w * h;
    }

    static string square(string w, string h)
    {
        Console.WriteLine("> string <");
        return (int.Parse(w) * int.Parse(h)).ToString();
    }
}
```