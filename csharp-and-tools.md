# 認識 C#

C#（發音 C sharp）

* Microsoft 開發的程式語言
* 用於開發 .NET 平台上運作的元件式程式與服務
* C# 擁有 C/C++ 的強大功能以及 Visual Basic 易寫易用的特性
* 和 C++ 與 Java 一樣亦為物件導向（Object-Oriented）程式語言

問：
C# 與 Visual Studio C# 有何不同？

語言 v.s. 工具

## Common Language Runtime

簡稱 CLR

```
.NET Applications
        \
    Common Language Runtime
            \
        Windows OS
```

問：.NET 支援哪些程式語言呢？

## Microsoft Intermediate Language

簡稱 MSIL

編譯為 Managed 程式碼時，編譯器會將您的原始程式碼轉譯成 Microsoft Intermediate Language (MSIL)，它是可以有效率地轉換為機器碼而與 CPU 無關的指令集。

## 利用指令工具編譯及執行 C# 程式

Using Command-line tools

利用 Command-line 進行 C# 程式碼編譯

透過這個小練習，我們讓同學們瞭解，沒有整合開發工具（IDE Tools）輔助的情況下，如何完成 C# 程式碼的編譯。

打開「命令提示字元」（又稱為終端機、Console 或 Terminal）

先設定 `PATH` 環境變數：

```
set PATH=%PATH%;C:\Windows\Microsoft.NET\Framework\v3.5
```

撰寫程式：

利用記事本或 `edit` 指令，完成一個最簡單的 C# 程式碼，輸出「`Hello, World!`」文字，存檔命名為「`Hello.cs`」。

編譯：

```
csc /t:exe Hello.cs
```

執行：

```
Hello.exe
```

程式碼（一）

```
public class Hello
{
   public static void Main()
   {
      System.Console.WriteLine("Hello, World!");
   }
}
```

程式碼（二）

```
using System;

public class Hello
{
   public static void Main()
   {
      Console.WriteLine("Hello, World!");
   }
}
```

程式碼（三）

```
using System;

public class Hello
{
   public static void Main(string[] args)
   {
      Console.WriteLine("Hello, World!");
      Console.WriteLine("You entered the following {0} command line arguments:",
         args.Length );
      for (int i=0; i < args.Length; i++)
      {
         Console.WriteLine("{0}", args[i]); 
      }
   }
}
```

程式碼（四）

```
using System;

public class Hello
{
   public static int Main(string[] args)
   {
      Console.WriteLine("Hello, World!");
      return 0;
   }
}
```

取得程式執行結果代碼。

`%ERRORLEVEL%`

撰寫 `Hello.bat` 批次檔。

練習：如果沒有參數，輸出「Hello, World!」；否則輸出「Hi {0}, nice to meet you.」

```
@echo off
Hello
Hello John
pause
```