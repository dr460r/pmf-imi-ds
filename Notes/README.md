# Termin 1

## Osnovne razlike

| feature | Java | C# |
|-|-|-|
| Compile target file | `.class` | `.exe`, `.dll` |
| Compile target lang. | Bytecode | Common Intermediate Language (CIL) |
| Runtime | Java Virtual Machine (JVM) | Common Language Runtime (CLR) |
| Grouping | `package`, `import` | `namespace`, `using` |
| Naming | `camelCase` (first letter: lower) | `PascalCase` (first letter: upper) |

## .NET

- Jezici: `C#`, `F#`, `VB`, ...
- _Common Intermediate Language_ (**CIL**)
- _Common Language Runtime_ (**CLR**) - Virtuelna Mašina
- _Base Class Library_ (**BCL**)
- _Assemblies_: **EXE**, **DLL** (sadrže _CIL_ kod)

Kod napisan u jeziku kao što je `C#` se kompajlira u `CIL`, koji se nalazi u **EXE** ili **DLL** fajlu, i izvršava ga **CLR** tako što deo po deo prevodi u mašinski kod, koji se izvršava na procesoru sistema.

## Jezičke konstrukcije

### Čitanje sa konzole
```cs
String linija = Console.ReadLine();
```

### Nasleđivanje: `extends`/`implements` vs. `:`
```java
// Java
class Klasa extends Roditelj implements Interfejs1, Interfejs2 { }
```
```cs
// C#
class Klasa : Roditelj, Interfejs1, Interfejs2 { }
```

### Pozivanje konstruktora nadklase: `super` vs. `base`
```java
// Java
class Klasa extends Roditelj 
{
    Klasa(String p1, String p2) 
    {
        super(p1);
        // ...
    }
}
```
```cs
// C#
class Klasa : Roditelj 
{
    Klasa(String p1, String p2) : base(p1) 
    {
        // ...
    }
}
```

### _Foreach_ petlja: `for` vs. `foreach`
```java
// Java
for (float broj : brojevi) { 
    // ... 
}
```
```cs
// C#
foreach (float broj in brojevi) { 
    // ... 
}
```

### Promenljivi broj argumenata metode: `...` vs. `params`
```java
// Java
int Suma(int ... brojevi) {
    // "brojevi" se koristi kao niz
}
```
```cs
// C#
int Suma(params int[] brojevi) {
    // "brojevi" se koristi kao niz
}
```
```cs
// Poziv metode u oba jezika
Suma(1,2,3,4,5);
```

### Boksovanje (TODO)
```cs

```

### Višelinijski stringovi
```cs
String s = @"Prva linija
Druga linija
    Treca linija
"
```
Rezultat u `s` (postoji newline nakon trece linije):
```
Prva linija
Druga linija
    Treca linija

```

### Svojstva (_property_)
Koriste se kao obični atributi i predstavljaju podatke:
```cs
objekat.Svojstvo = "vrednost";
Console.Write(objekat.Svojstvo);
```
Definišu se na dva načina. Prvi je jednostavan, **bez uvođenja** dodatnog atributa koji čuva podatke:
```cs
int Broj { get; set; }
```
Uz ograničene dozvole:
```cs
public int Broj { get; private set; }
```
Drugi način, dodatni atribut i robusnija kontrola:
```cs
int broj;
int Broj { 
    get { return broj; } 
    set { broj = value; } 
}
```

### Parcijalne klase
fajl 1
```cs
partial class Point2D {
    public float X { get; set; }
    public float Y { get; set; }
}
```
fajl 2
```cs
partial class Point2D {
    public void Move() { /* ... */ }
}
```
Kompajler će pronaći sve delove parcijalne klase i spojiti ih u jednu celinu.

### `ref` i `out` ključne reči
```cs
void Funkcija(ref x, out y) {
    // x - možemo menjati i čitati
    // z - možemo samo menjati
}
```
```cs
// Poziv
int a = 10;
int b;
Funkcija(ref a, out b);
```
Napomene: 
- "a" i "b" ne mogu biti konstante, kako bi mogli da budu promenjeni iz funkcije
- pošto se prosleđuje kao "out", dakle ne može se čitati, "b" ne mora imati postavljenu vrednost

### Imenovani argumenti funkcija
```cs
void Funkcija(int x, int y) { }
```
```cs
// Poziv
Funkcija(1, 2);
Funkcija(x: 1, y: 2);
Funkcija(y: 2, x: 1);
```

### `internal` vidljivost
Vidljivost unutar _Assembly_-ja (EXE/DLL)

### Enumeracije
`int` konstante koje pocinju od 0
```cs
enum Dan { Pon, Uto, Sre, Cet, Pet, Sub, Ned };
```
mogu biti drugog celobrojnog tipa i poceti od nekog drugog broja
```cs
enum Dan: ushort { Pon = 1, Uto, Sre, Cet, Pet, Sub, Ned };
```
Korišćenje:
```cs
Dan x = Dan.Sub;
```

### Automatsko utvrđivanje tipa: `var`

Kompajler često može sam zaključiti tip promenljive
```cs
var x = 15.6F;     // x je float
var y = 15;        // y je int
var s = "hello!";  // s je string
var c = new Car(); // c je tipa klase Car
```

### Anonimni tipovi

```cs
var point3d = new { X = 3.0, Y = 7.0, Z = 1.0 };
Console.Write(point3d.X);
```
Napomena: Članovi objekta anonimne klase mogu biti samo _**property**_, i to _public read-only_ (imaju _**public getter**_). Dakle, `X`, `Y` i `Z` su _property_.


# Termin 2

- Explicit operator
- Implicit operator
- Operator overloading
- Podrška za foreach petlju


# Termin 3

- Delegati
- Događaji
- Dinamičke/anonimne funkcije
- Lambda izrazi
- Predikati

# Termin 4

- Generičke klase i metode
- Ograničenja generičkih tipova
- Generički delegati