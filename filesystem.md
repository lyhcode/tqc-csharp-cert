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
using System.Net;
using System.Text;
using System.Threading.Tasks;

class Stock
{
    public string Id { get; set; }
    public string Name { get; set; }
    public double Price { get; set; }
}

class Program
{
    private static List<Stock> stocks = new List<Stock>();

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

                        //if (string.IsNullOrEmpty)
                        if (!string.IsNullOrWhiteSpace(line))
                        {
                            string[] tokens = line.Split(',');

                            string id = tokens[0];
                            string name = tokens[1];

                            Stock stock = new Stock() {
                                Id = id,
                                Name = name,
                                Price = fetchPrice(id)
                            };

                            stocks.Add(stock);
                        }
                    }
                }
            }

            // 只顯示[股價<100]的個股 LINQ

            var query = from s in stocks
                        where s.Price < 100
                        select s;

            foreach (var row in query)
            {
                Console.WriteLine("{0} => {1}, ${2}", row.Id, row.Name, row.Price);
            }

            Console.WriteLine("Total: {0} stocks", stocks.Count);
        }

        Console.ReadKey();
    }

    private static double fetchPrice(string id)
    {
        string url = string.Format("http://finance.google.com/finance/info?client=ig&q=TPE:{0}", id);

        string data = new WebClient().DownloadString(url);

        double price = 0;

        foreach (string line in data.Split('\n')) {
            if (line.StartsWith(",\"l\""))
            {
                string[] tokens = line.Split(':');

                price = double.Parse(tokens[1].Trim().Replace("\"", ""));
            }
        }

        return price;
    }
}

```