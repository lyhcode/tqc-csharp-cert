# 認識 C# 語言與工具

C#（發音 C sharp）

* Microsoft 開發的程式語言
* 用於開發 .NET 平台上運作的元件式程式與服務
* C# 擁有 C/C++ 的強大功能以及 Visual Basic 易寫易用的特性
* 和 C++ 與 Java 一樣亦為物件導向（Object-Oriented）程式語言

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

## 進階的開發工具使用

利用 Command-line 進行 C# 程式碼編譯

先設定 `PATH` 環境變數：

```
set PATH=%PATH%;C:\Windows\Microsoft.NET\Framework\v3.5
```

編譯：

```
csc /t:exe Program.cs
```

執行：

```
Program.exe
```