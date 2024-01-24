# Na-kartk

using System;

class Program
{
    static void Main()
    {
        Console.WriteLine("Wybierz rodzaj przesyłki:");
        Console.WriteLine("1. Pocztówka");
        Console.WriteLine("2. List");
        Console.WriteLine("3. Paczka");

        int wyborTypuPrzesylki = WybierzOpcje(1, 3);

        string obraz = "";
        string cena = "";

        switch (wyborTypuPrzesylki)
        {
            case 1:
                obraz = "pocztowka.png";
                cena = "Cena: 1 zł";
                break;
            case 2:
                obraz = "list.png";
                cena = "Cena: 1,5 zł";
                break;
            case 3:
                obraz = "paczka.png";
                cena = "Cena: 10 zł";
                break;
        }

        Console.WriteLine($"Wybrano {Enum.GetName(typeof(RodzajPrzesylki), wyborTypuPrzesylki)}");
        Console.WriteLine($"Obraz: {obraz}");
        Console.WriteLine($"Cena: {cena}");

        Console.WriteLine("Podaj kod pocztowy (5 cyfr):");
        string kodPocztowy = Console.ReadLine();

        if (WalidujKodPocztowy(kodPocztowy))
        {
            Console.WriteLine("Dane przesyłki zostały wprowadzone");
        }
        else
        {
            Console.WriteLine("Nieprawidłowa liczba cyfr w kodzie pocztowym");
        }
    }

    static int WybierzOpcje(int min, int max)
    {
        int wybor;
        while (!int.TryParse(Console.ReadLine(), out wybor) || wybor < min || wybor > max)
        {
            Console.WriteLine($"Wprowadź poprawną wartość od {min} do {max}");
        }
        return wybor;
    }

    static bool WalidujKodPocztowy(string kodPocztowy)
    {
        return kodPocztowy.Length == 5 && int.TryParse(kodPocztowy, out _);
    }

    enum RodzajPrzesylki
    {
        Pocztówka = 1,
        List = 2,
        Paczka = 3
    }
}
