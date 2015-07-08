# File System

`C:\stock.txt`

```
2317,鴻海
2330,台積電
3008,大立光

```


```
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

class Program
{
    static void Main(string[] args)
    {
        string file = @"C:\stock.txt";

        FileInfo info = new FileInfo(file);

        if (info.Exists)
        {
            Console.WriteLine("File Size: {0} bytes", info.Length);

            using (FileStream stream = new FileStream(file, FileMode.Open, FileAccess.Read))
            {
                using(StreamReader reader = new StreamReader(stream, Encoding.UTF8))
                {
                    while (!reader.EndOfStream)
                    {
                        string line = reader.ReadLine();

                        if (!string.IsNullOrWhiteSpace(line))
                        {
                            Console.WriteLine(line);
                        }
                        //if (string.IsNullOrEmpty)
                    }
                }
            }
        }

        Console.ReadKey();
    }
}
```