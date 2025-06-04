# TP2 - Calculadora de Triángulos

## Estudiante
**Juan Pablo Agüero Fajardo**

## Carnet
**FI22026174**

---

## Comandos utilizados
```bash
dotnet new mvc -f net8.0 -n TP2
cd TP2
dotnet run
```

---

## Páginas web consultadas
- [Operaciones básicas en C#](https://learn.microsoft.com/es-es/dotnet/csharp/language-reference/operators/arithmetic-operators)
- [Operadores de igualdad en C#](https://learn.microsoft.com/es-es/dotnet/csharp/language-reference/operators/equality-operators)
- [Math en C#](https://oregoom.com/c-sharp/math/)
- Videos:
  - [Video 1](https://youtu.be/JjLI-lU2dsw)
  - [Video 2](https://youtu.be/w2vWAywu8rA)
  - [Video 3](https://www.youtube.com/watch?v=UShz5cJNhss)

---
Tambien utilicé recursos del curso anterior donde teníamos formularios y tareas que eran similares en estructura

## Búsqueda en Google, primera respuesta que aparece de gemini

> Para calcular el perímetro de un triángulo en C#, necesitas sumar las longitudes de sus tres lados. Puedes utilizar una función para encapsular este cálculo y reutilizarla en diferentes contextos. 
> Código de ejemplo:

```csharp
using System;

public class Triangulo
{
    public double lado1;
    public double lado2;
    public double lado3;

    public Triangulo(double lado1, double lado2, double lado3)
    {
        this.lado1 = lado1;
        this.lado2 = lado2;
        this.lado3 = lado3;
    }

    public double CalcularPerimetro()
    {
        return lado1 + lado2 + lado3;
    }
}

public class Programa
{
    public static void Main(string[] args)
    {
        // Ejemplo de uso
        Triangulo triangulo1 = new Triangulo(5, 6, 7);
        double perimetro = triangulo1.CalcularPerimetro();
        Console.WriteLine($"El perímetro del triángulo es: {perimetro}"); // Output: El perímetro del triángulo es: 18
    }
}
```

---

## Consulta a deepseek de fórmula a mano

Prompt:

```
dame el codigo para calcular esto porfa
A = √[S ● (S - a) ● (S - b) ● (S - c)]
```

Resultado:

```csharp
 public double CalcularArea()
    {
        double S = (LadoA + LadoB + LadoC) / 2;
        double area = Math.Sqrt(S * (S - LadoA) * (S - LadoB) * (S - LadoC));
        return area;
    }
```

####
Prompt:

```
dame la formula de ley de cosenos en codigo tambien
```

Resultado:

```csharp
// Calcula el lado 'a' usando b, c y α (en grados)
    public double CalcularLadoA()
    {
        return Math.Sqrt(
            Math.Pow(LadoB, 2) + Math.Pow(LadoC, 2) - 
            2 * LadoB * LadoC * Math.Cos(GradosARadianes(AnguloAlpha))
        );
    }

    // Calcula el lado 'b' usando a, c y β (en grados)
    public double CalcularLadoB()
    {
        return Math.Sqrt(
            Math.Pow(LadoA, 2) + Math.Pow(LadoC, 2) - 
            2 * LadoA * LadoC * Math.Cos(GradosARadianes(AnguloBeta))
        );
    }

    // Calcula el lado 'c' usando a, b y γ (en grados)
    public double CalcularLadoC()
    {
        return Math.Sqrt(
            Math.Pow(LadoA, 2) + Math.Pow(LadoB, 2) - 
            2 * LadoA * LadoB * Math.Cos(GradosARadianes(AnguloGamma))
        );
    }

    // Convierte grados a radianes (Math.Cos usa radianes)
    private double GradosARadianes(double grados)
    {
        return grados * Math.PI / 180;
    }
```

####
Prompt:

```
tambien la de los angulos cos(α), cos(β), cos(γ)
```

Resultado:

```csharp
     // Calcula un lado (ejemplo: LadoA)
    public double CalcularLadoA() => Math.Sqrt(
        Math.Pow(LadoB, 2) + Math.Pow(LadoC, 2) - 
        2 * LadoB * LadoC * Math.Cos(GradosARadianes(AnguloAlpha))
    );

    // Calcula ángulos si se conocen los tres lados
    public void CalcularAngulos()
    {
        if (LadoA > 0 && LadoB > 0 && LadoC > 0)
        {
            AnguloAlpha = RadianesAGrados(
                Math.Acos((Math.Pow(LadoB, 2) + Math.Pow(LadoC, 2) - Math.Pow(LadoA, 2)) / (2 * LadoB * LadoC))
            );
            AnguloBeta = RadianesAGrados(
                Math.Acos((Math.Pow(LadoA, 2) + Math.Pow(LadoC, 2) - Math.Pow(LadoB, 2)) / (2 * LadoA * LadoC))
            );
            AnguloGamma = 180 - AnguloAlpha - AnguloBeta; // Suma de ángulos = 180°
        }
    }

    private double GradosARadianes(double grados) => grados * Math.PI / 180;
    private double RadianesAGrados(double radianes) => radianes * 180 / Math.PI;
```
Prompt a copilot: formatea mejor el readme.md porfa para que quede con el markdown bien hecho
```
Resultado: este doc
```
