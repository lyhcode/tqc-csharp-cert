# 認識 C# 語言與工具

C# 與 Visual Studio C# 有何不同？

語言 v.s. 工具

## CLR, Common Language Runtime


```
.NET Applications
        \
    Common Language Runtime
            \
        Windows OS
```

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