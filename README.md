# 9. String & char

**String in C#:**

- **Class:** String is a reference type and a class in the .NET framework.
- **Immutable:** Once a String object is created, its value cannot be changed. Any modification to a String results in the creation of a new String object.
- **Unicode support:** A String in C# is a sequence of Unicode characters, allowing it to store text in various languages.
- **Operations:** C# provides a rich set of methods for manipulating strings, including concatenation, comparison, searching, and more.
- **Nullability:** Since String is a reference type, it can be null.

**Char in c#:**

- **Structure:** Char (or char) is a value type and a structure in the .NET framework.
- **Mutable:** Unlike String, individual Char values are not immutable by nature, but because they are value types, they do not support methods to change the value of an existing instance.
- **Single character:** A Char represents a single 16-bit Unicode character.
  Operations: The Char structure provides methods for working with individual characters, like checking if a character is a digit, letter, or white space, and converting characters to their upper or lower case forms.
- **No Nullability:** By default, Char cannot be null. However, you can use Nullable<Char> or char? to allow null values.

## Strings

```csharp
string name = "Peter";
string lastname = new String("Peter");

// Funny thing
string stares = new String('*',10); // Generate => **********
```

### Strings - Static methods

As String is a class, this class have static class, so that means that we can call without instanciate the class.

Let us see some of them.

```csharp
string[] countries = { "Belgium", "France", "USA" };
string result = string.Join(", ", countries);
Console.WriteLine(result);

string name = "John ";
string lastname = "Doe";
Console.WriteLine($"Here is the full name: {string.Concat(name, lastname)}");
```

### String - Instance methods

```csharp
 string name = "I love C# so much";
 string[]? strings = [];

 strings = name.Split(' ');
 Console.WriteLine(re[2]); // => C#
```

Check the doc for more instance or class methods

## String to int, float, double ...

```csharp
string? x string.Empty;
string? y string.Empty;
int? sum = null;

x = Console.ReadLine();
y = Console.ReadLine();

sum = int.Parse(x) + int.Parse(y);

Console.WriteLine(sum);
```

## Int, float, double ... to string

```csharp
float money = 23.5f;
int age = 34;

Console.WriteLine($"I have {money.ToString()} and I have {age.ToString()}");
```

![](assets/var-string-char.png)

## Interpolation

```csharp
// Simple Interpolation
string name = "John";
Console.WriteLine($"{name}");
```

It is right but we have two contraints like:

- Escape special "caracters",
- Escape the double quote

```csharp
Console.WriteLine("Complete \"path\": C:\\Temp\\readme.md");
```

So, we can use **Verbatim** instead of interpolation:

```csharp
Console.WriteLine(@"Complete ""path"": C:\Temp\readme.md");
```

- But we need to double the quotes

We can use both together:

```csharp
string s4 = "Complete \"path\": C:\\Temp\\readme.md";
string name = "John";

string print = $@"{name} : - {s4}";
Console.WriteLine(print);
```

But we have something that can be used:

```csharp
 string text = """
     Dans un literal de chaine brut:
     - pas besoin d'échaper les caractères spéciaux y compris les "guillemets",
     - on peut indenter la chaine comme le reste du code
     """;
 Console.WriteLine(text);
```

## Go deeper with int/float/decimal.ToString() method

```csharp
int age = 23;

string result = age.ToString(); // "23"
string result2 = age.ToString("N3"); // 23,000
string result3 = age.ToString("D3"); // 023

// We need to add this line, to "activate" the unicode in the terminal
Console.OutputEncoding = Encoding.Unicode;

float price = 23.4f;
string priceEuro = price.ToString("c2"); // 23.40€
string priceUSA = price.ToString("c2", CultureInfo.GetCultureInfo("us-US")); // $23.4

// Personnal formats

 long phone = 487324542;
 const string PREFIX_PHONE_BE = "+32";
 string result = phone.ToString($"{PREFIX_PHONE_BE} ### ## ## ##"); // +32 487 32 45 42
```

So, let's resume, we can pass some parameters in the static method **ToString()** like:

- Nn : Add n digits after the string
- Dn: Add (n-number) digits before the string
- Cn : Add the "currency" before / after the string, n-number add digit after the string
- CultureInfo : A provider which Changing the localization `CultureInfo.GetCultureInfo("us-US")`

## Exercices
