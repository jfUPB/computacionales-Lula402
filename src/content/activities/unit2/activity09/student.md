### Traducción a lenguaje de alto nivel
``` C#
namespace PintarPantalla
{
    internal class Program
    {
        static void Main(string[] args)
        {
            int width = 16;          //ancho de la pantalla y lo uso para definir el tamaño del array
            int height = 16;         //ancho de la pantalla y lo uso para definir el tamaño del array
            char[,] screen = new char[height, width]; //array para simular la pantalla


            while (true)
            {
                if (Console.KeyAvailable) // habilita el teclado
                {
                    Console.ReadKey(true); // Verifica si hay una tecla presionada y la captura
                    Console.Clear();
                    for (int row = 0; row < height; row++)
                    {
                        for (int col = 0; col < width; col++)
                        {
                            screen[row, col] = '█'; // Píxel pintado
                        }                        
                    }

                }
                else
                {
                    for (int row = 0; row < height; row++)
                    {
                        for (int col = 0; col < width; col++)
                        {
                            screen[row, col] = ' '; // Píxel limpio                    
                        }
                    }                  
                }

                for (int row = 0; row < height; row++)
                {
                    for (int col = 0; col < width; col++)
                    {
                        Console.Write(screen[row, col]);
                    }
                    Console.WriteLine();          //se salta el renglón para poder imprimir la nueva fila
                }
                Thread.Sleep(50);       // Espera 50 milisegundos para no sobre usar el while
            }
        }
    }
}
```
