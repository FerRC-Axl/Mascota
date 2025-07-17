using System;

namespace MascotasApp
{
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

        public int CalcularEdadHumana()
        {
            if (tipo == "perro" || tipo == "gato")
                return edad * 7;
            else if (tipo == "ajolote")
                return edad * 3;
            else
                return edad;
        }
    }

    class Program
    {
        static void Main(string[] args)
        {
            Mascota m1 = new Mascota("Firulais", 4, "perro", "guau");
            Mascota m2 = new Mascota("Michi", 2, "gato", "miau");
            Mascota m3 = new Mascota("Axel", 1, "ajolote", "blub blub");

            // Perro
            m1.MostrarInformacion();
            m1.EmitirSonido();
            Console.WriteLine("Edad humana: " + m1.CalcularEdadHumana());
            m1.SetEdad(5);
            Console.WriteLine("Nueva edad: " + m1.GetEdad());
            Console.WriteLine("Nueva edad humana: " + m1.CalcularEdadHumana());
            Console.WriteLine();

            // Gato
            m2.MostrarInformacion();
            m2.EmitirSonido();
            Console.WriteLine("Edad humana: " + m2.CalcularEdadHumana());
            m2.SetEdad(3);
            Console.WriteLine("Nueva edad: " + m2.GetEdad());
            Console.WriteLine("Nueva edad humana: " + m2.CalcularEdadHumana());
            Console.WriteLine();

            // Ajolote
            m3.MostrarInformacion();
            m3.EmitirSonido();
            Console.WriteLine("Edad humana: " + m3.CalcularEdadHumana());
            m3.SetEdad(2);
            Console.WriteLine("Nueva edad: " + m3.GetEdad());
            Console.WriteLine("Nueva edad humana: " + m3.CalcularEdadHumana());
        }
    }
}
