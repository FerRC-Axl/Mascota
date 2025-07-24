using System;
using System.Collections.Generic;

class Mascota
{
    private string nombre;
    private int edad;
    private string tipo;
    private string sonido;

    public Mascota(string nom, int ed, string ti, string son)
    {
        nombre = nom;
        edad = ed;
        tipo = ti;
        sonido = son;
    }

    public void MostrarInformacion()
    {
        Console.WriteLine("Nombre: " + nombre);
        Console.WriteLine("Edad: " + edad + " años");
        Console.WriteLine("Tipo: " + tipo);
    }

    public void EmitirSonido()
    {
        Console.WriteLine(nombre + " dice: " + sonido);
    }

    public void SetEdad(int nuevaEdad)
    {
        edad = nuevaEdad;
    }

    public int GetEdad()
    {
        return edad;
    }

    private Dictionary<string, int> factoresEdad = new Dictionary<string, int>
    {
        { "perro", 7 },
        { "gato", 7 },
        { "ajolote", 3 }
    };

    public int CalcularEdadHumana()
    {
        if (factoresEdad.ContainsKey(tipo))
            return edad * factoresEdad[tipo];
        else
            return edad;
    }
}

class Program
{
    static void Main(string[] args)
    {
        // Crear mascotas con edad inicial 0 (la pedirá el usuario)
        Mascota m1 = new Mascota("Luka", 0, "perro", "guau");
        Mascota m2 = new Mascota("Mele", 0, "gato", "miau");
        Mascota m3 = new Mascota("Axel", 0, "ajolote", "blub blub");

        Console.WriteLine("¿Qué mascota quieres conocer? (Luka / Mele / Axel)");
        string opcion = Console.ReadLine().ToLower(); // Convertimos a minúsculas para evitar errores

        switch (opcion)
        {
            case "luka":
                MostrarDatosMascota(m1);
                break;

            case "mele":
                MostrarDatosMascota(m2);
                break;

            case "axel":
                MostrarDatosMascota(m3);
                break;

            default:
                Console.WriteLine("Opción no válida. Escribe Luka, Mele o Axel.");
                break;
        }
    }

    static void MostrarDatosMascota(Mascota mascota)
    {
        mascota.MostrarInformacion();
        mascota.EmitirSonido();

        Console.Write("¿Qué edad tiene la mascota? ");
        int edad;
        while (!int.TryParse(Console.ReadLine(), out edad) || edad < 0)
        {
            Console.Write("Por favor, ingresa una edad válida: ");
        }

        mascota.SetEdad(edad);
        Console.WriteLine("Edad humana: " + mascota.CalcularEdadHumana());
    }
}
