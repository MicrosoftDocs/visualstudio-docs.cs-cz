---
title: 'Kurz: Vytvoření jednoduché konzolové aplikace C#'
description: Přečtěte si, jak vytvořit konzolovou aplikaci C# v Sadě Visual Studio krok za krokem.
ms.custom: seodec18, get-started
ms.date: 02/18/2020
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: tutorial
ms.devlang: CSharp
author: ornellaalt
ms.author: ornella
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 528887c477814b7011cf941a9198f83701beee54
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "78215434"
---
# <a name="tutorial-create-a-simple-c-console-app-in-visual-studio"></a>Kurz: Vytvoření jednoduché konzolové aplikace C# v sadě Visual Studio

V tomto kurzu pro C# budete používat Visual Studio k vytvoření a spuštění konzolové aplikace a prozkoumat některé funkce integrovaného vývojového prostředí Visual Studio (IDE), zatímco vy tak učiníte.

::: moniker range="vs-2017"

Pokud jste visual studio ještě nenainstalovali, přejděte na stránku [ke stažení sady Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) a nainstalujte ji zdarma.

::: moniker-end

::: moniker range="vs-2019"

Pokud jste visual studio ještě nenainstalovali, přejděte na stránku [ke stažení sady Visual Studio](https://visualstudio.microsoft.com/downloads) a nainstalujte ji zdarma.

::: moniker-end

## <a name="create-a-project"></a>Vytvoření projektu

Chcete-li začít, vytvoříme projekt aplikace C#. Typ projektu je dodáván se všemi soubory šablon, které budete potřebovat, ještě předtím, než něco přidáte!

::: moniker range="vs-2017"

1. Otevřete sadu Visual Studio 2017.

2. V horním řádku nabídek zvolte **Soubor** > **nového** > **projektu**.
   (Případně stiskněte **kombinaci kláves Ctrl**+**Shift**+**N).**

3. V levém podokně dialogového okna **Nový projekt** rozbalte **položku C#** a pak zvolte **.NET Core**. V prostředním podokně zvolte **Console App (.NET Core)**. Poté pojmenujte soubor ***Kalkulačka***.

   ![Šablona projektu konzolové aplikace (.NET Core) v dialogovém okně Nový projekt v ide sady Visual Studio](./media/new-project-csharp-calculator-console-app.png)

### <a name="add-a-workload-optional"></a>Přidání pracovního vytížení (volitelné)

Pokud nevidíte šablonu projektu **konzolové aplikace (.NET Core),** můžete ji získat přidáním **úlohy pro vývoj napříč platformami .NET Core.** Jak na to:

#### <a name="option-1-use-the-new-project-dialog-box"></a>Možnost 1: Použití dialogového okna Nový projekt

1. V levém podokně dialogového okna Nový **projekt** zvolte odkaz Otevřít instalační program **sady Visual Studio.**

   ![Zvolte odkaz Otevřít instalační program sady Visual Studio v dialogovém okně Nový projekt.](./media/csharp-open-visual-studio-installer-generic-dark.png)

1. Spustí se instalační program pro Visual Studio. Zvolte **úlohu vývoje napříč platformami .NET Core** a pak zvolte **Změnit**.

   ![Úloha vývoje napříč platformami .NET Core v instalačním programu sady Visual Studio](./media/dot-net-core-xplat-dev-workload.png)

#### <a name="option-2-use-the-tools-menu-bar"></a>Možnost 2: Použití panelu nabídek Nástroje

1. Zrušit z dialogového okna **Nový projekt** a v horním řádku nabídek zvolte **Nástroje** > **získat nástroje a funkce**.

1. Spustí se instalační program pro Visual Studio. Zvolte **úlohu vývoje napříč platformami .NET Core** a pak zvolte **Změnit**.

::: moniker-end

::: moniker range="vs-2019"

1. Otevřete Visual Studio 2019.

1. V počátečním okně zvolte **Vytvořit nový projekt**.

   ![Zobrazit okno Vytvořit nový projekt](../../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. V okně **Vytvořit nový projekt** zadejte nebo zadejte *konzolu* do vyhledávacího pole. Dále zvolte **C#** ze seznamu jazyk a pak zvolte **Windows** ze seznamu platformy. 

   Po použití filtrů jazyka a platformy zvolte šablonu **Console App (.NET Core)** a pak zvolte **Další**.

   ![Zvolte šablonu Jazyka C# pro konzolovou aplikaci (.NET Framework)](./media/vs-2019/csharp-create-new-project-search-console-net-core-filtered.png)

   > [!NOTE]
   > Pokud šablonu **Console App (.NET Core)** nevidíte, můžete ji nainstalovat z okna **Vytvořit nový projekt.** Ve zprávě **Install more tools and features** **Nenajít to, co hledáte?**
   >
   > ![Odkaz "Nainstalovat další nástroje a funkce" ze zprávy "Nenajít to, co hledáte" v okně "Vytvořit nový projekt"](../../get-started/media/vs-2019/not-finding-what-looking-for.png) 
   > 
   > Potom v Instalační službě sady Visual Studio zvolte vývojové úlohy **.NET Core napříč platformami.**
   >
   > ![Úloha vývoje napříč platformami .NET Core v instalačním programu sady Visual Studio](./media/dot-net-core-xplat-dev-workload.png)
   >
   > Poté zvolte tlačítko **Změnit** v Instalační službě sady Visual Studio. Můžete být vyzváni k uložení práce. pokud ano, uvažte tak. Dále zvolte **Pokračovat** k instalaci úlohy. Potom se vraťte ke kroku 2 v tomto postupu "[Vytvořit projekt](#create-a-project)".

1. V okně **Konfigurovat nový projekt** zadejte nebo zadejte *kalkulačku* do pole **Název projektu.** Potom zvolte **Vytvořit**.

   ![v okně Konfigurace nového projektu pojmenujte projekt Kalkulačka](./media/vs-2019/csharp-name-your-calculator-project.png)

   Visual Studio otevře nový projekt, který obsahuje výchozí kód "Hello World".
   
::: moniker-end

## <a name="create-the-app"></a>Vytvoření aplikace

Nejprve prozkoumáme některé základní celé číslo matematiky v jazyce C#. Potom přidáme kód k vytvoření základní kalkulačky. Poté aplikaci ladíme, abychom našli a opravili chyby. A nakonec kód zpřesníme, aby byl efektivnější.

### <a name="explore-integer-math"></a>Seznámení s matematikou celých čísel

Začněme s některými základní celé číslo matematiky v jazyce C#.

1. V editoru kódu odstraňte výchozí kód "Hello World".

    ![Odstranění výchozího kódu Hello World z nové aplikace kalkulačky](./media/csharp-console-calculator-deletehelloworld.png)

   Konkrétně odstraňte řádek, `Console.WriteLine("Hello World!");`který říká, .

1. Na jeho místo zadejte následující kód:

    ```csharp
            int a = 42;
            int b = 119;
            int c = a + b;
            Console.WriteLine(c);
            Console.ReadKey();
    ```

    Všimněte si, že když tak učiníte, funkce IntelliSense v sadě Visual Studio nabízí možnost automatického dokončování položky.

    > [!NOTE]
    > Následující animace není určena k duplikaci předchozího kódu. Je určena pouze k zobrazení funkce automatického dokončování.

    ![Animace celého matematického kódu, který zobrazuje funkci automatického dokončování technologie IntelliSense v rozhraní IDE sady Visual Studio](./media/integer-math-intellisense.gif)

1. Chcete-li vytvořit a spustit program, zvolte zelené tlačítko **Start** vedle **tlačítka Kalkulačka** nebo stiskněte **klávesu F5**.

   ![Zvolte tlačítko Kalkulačka pro spuštění aplikace z panelu nástrojů.](./media/csharp-console-calculator-button.png)

   Otevře se okno konzoly, které odhaluje součet 42 + 119, což je **161**.

    ![Okno konzoly zobrazující výsledky celé matematiky](./media/csharp-console-integer-math.png)

1. **(Nepovinné)** Můžete změnit operátor změnit výsledek. Můžete například změnit `+` operátor v `int c = a + b;` řádku kódu `-` na pro `*` odčítání, `/` pro násobení nebo pro dělení. Potom při spuštění programu, výsledek se změní také.

1. Zavřete okno konzoly.

### <a name="add-code-to-create-a-calculator"></a>Přidání kódu pro vytvoření kalkulačky

Pokračujme přidáním složitější sady kódu kalkulačky do projektu.

1. Odstraňte veškerý kód, který vidíte v editoru kódu.

1. Zadejte nebo vložte následující nový kód do editoru kódu:

    ```csharp
    using System;

    namespace Calculator
    {
        class Program
        {
            static void Main(string[] args)
            {
                // Declare variables and then initialize to zero.
                int num1 = 0; int num2 = 0;

                // Display title as the C# console calculator app.
                Console.WriteLine("Console Calculator in C#\r");
                Console.WriteLine("------------------------\n");

                // Ask the user to type the first number.
                Console.WriteLine("Type a number, and then press Enter");
                num1 = Convert.ToInt32(Console.ReadLine());

                // Ask the user to type the second number.
                Console.WriteLine("Type another number, and then press Enter");
                num2 = Convert.ToInt32(Console.ReadLine());

                // Ask the user to choose an option.
                Console.WriteLine("Choose an option from the following list:");
                Console.WriteLine("\ta - Add");
                Console.WriteLine("\ts - Subtract");
                Console.WriteLine("\tm - Multiply");
                Console.WriteLine("\td - Divide");
                Console.Write("Your option? ");

                // Use a switch statement to do the math.
                switch (Console.ReadLine())
                {
                    case "a":
                        Console.WriteLine($"Your result: {num1} + {num2} = " + (num1 + num2));
                        break;
                    case "s":
                        Console.WriteLine($"Your result: {num1} - {num2} = " + (num1 - num2));
                        break;
                    case "m":
                        Console.WriteLine($"Your result: {num1} * {num2} = " + (num1 * num2));
                        break;
                    case "d":
                        Console.WriteLine($"Your result: {num1} / {num2} = " + (num1 / num2));
                        break;
                }
                // Wait for the user to respond before closing.
                Console.Write("Press any key to close the Calculator console app...");
                Console.ReadKey();
            }
        }
    }
    ```

1. Chcete-li spustit program, zvolte **Kalkulačka** nebo stiskněte **klávesu F5**.

   ![Zvolte tlačítko Kalkulačka pro spuštění aplikace z panelu nástrojů.](./media/csharp-console-calculator-button.png)

   Otevře se okno konzoly.

1. Aplikaci si prohlédněte v okně konzoly a podle pokynů přidejte čísla **42** a **119**.

   Vaše aplikace by měla vypadat podobně jako na následujícím snímku obrazovky:

    ![Okno konzoly zobrazující aplikaci Kalkulačka a obsahuje výzvy, které akce mají být podniknu](./media/csharp-console-calculator.png)

### <a name="add-functionality-to-the-calculator"></a>Přidání funkcí do kalkulačky

Pojďme vyladit kód přidat další funkce.

### <a name="add-decimals"></a>Přidání desetinných míst

Aplikace kalkulačky v současné době přijímá a vrací celá čísla. Ale bude přesnější, pokud přidáme kód, který umožňuje desetinná místa.

Stejně jako na následujícím snímku obrazovky, pokud spustíte aplikaci a vydělíte číslo 42 číslem 119, váš výsledek je 0 (nula), což není přesné.

![Okno konzoly zobrazující aplikaci Kalkulačka, která v důsledku toho nevrací desetinnou číslici](./media/csharp-console-calculator-nodecimal.png)

Opravíme kód tak, aby zvládá desetinná místa.

1. Stisknutím **klávesy Ctrl** + **F** otevřete ovládací prvek Najít **a nahradit.**

1. Změňte každou `int` instanci proměnné na `float`.

   Ujistěte se, že jste v ovládacím prvku **Najít a nahradit** přepínali s **případem** Shoda (**Alt**+**C)** a **Spárovat celé slovo** (**Alt**+**W).**

    ![Animace ovládacího prvku Najít a nahradit ukazuje, jak změnit proměnnou int float](./media/find-replace-control-animation.gif)

1. Spusťte aplikaci kalkulačky znovu a vydělte číslo **42** číslem **119**.

   Všimněte si, že aplikace nyní vrátí desetinnou číslici namísto nuly.

    ![Okno konzoly zobrazující aplikaci Kalkulačka, která nyní vrací desetinnou číslici jako výsledek](./media/csharp-console-calculator-decimal.png)

Aplikace však vytváří pouze desetinný výsledek. Udělejme několik dalších vylepšení kódu, aby aplikace mohla také vypočítat desetinná místa.

1. Pomocí ovládacího prvku **Najít a nahradit** (**Ctrl** + **F**) můžete změnit každou `float` instanci proměnné `double`na a změnit každou instanci `Convert.ToInt32` metody na `Convert.ToDouble`.

1. Spusťte aplikaci kalkulačky a vydělte číslo **42.5** číslem **119.75**.

   Všimněte si, že aplikace nyní přijímá desetinné hodnoty a vrátí delší desetinnou číslici jako výsledek.

    ![Okno konzoly zobrazující aplikaci Kalkulačka, která nyní přijímá desetinná čísla a v důsledku toho vrací delší desetinnou číslici.](./media/csharp-console-calculator-usedecimals.png)

    (Počet desetinných míst v části [Revize kódu](#revise-the-code) opravíme.)

## <a name="debug-the-app"></a>Ladění aplikace

Vylepšili jsme naši základní kalkulačku aplikace, ale ještě nemá trezory na místě pro zpracování výjimek, jako jsou chyby vstupu uživatele.

Pokud se například pokusíte vydělit číslo nulou nebo zadáte alfa znak, když aplikace očekává číselný znak (nebo naopak), může aplikace přestat fungovat, vrátit chybu nebo vrátit neočekávaný nečíselný výsledek.

Pojďme projít několik běžných chyb vstupu uživatele, vyhledejte je v ladicím programu, pokud se tam objeví, a opravte je v kódu.

> [!TIP]
> Další informace o ladicím programu a jeho fungování najdete na [stránce První pohled na ladicí program sady Visual Studio.](../../debugger/debugger-feature-tour.md)

### <a name="fix-the-divide-by-zero-error"></a>Oprava chyby "dělení nulou"

Při pokusu o dělení čísla nulou může konzolová aplikace zamrznout a pak vám ukáže, co je v editoru kódu špatně.

   ![Editor kódu sady Visual Studio zobrazuje chybu dělení nulou](./media/csharp-console-calculator-dividebyzero-error.png)

> [!NOTE]
> Někdy aplikace nezamrzne a ladicí program nezobrazí chybu dělení nulou. Místo toho aplikace může vrátit neočekávaný nečíselný výsledek, jako je například symbol nekonečna. Následující oprava kódu stále platí.

Změníme kód pro zpracování této chyby.

1. Odstraňte kód, který `case "d":` se zobrazí `// Wait for the user to respond before closing`přímo mezi a komentář, který říká .

1. Nahraďte jej následujícím kódem:

   ```csharp
            // Ask the user to enter a non-zero divisor until they do so.
                while (num2 == 0)
                {
                    Console.WriteLine("Enter a non-zero divisor: ");
                    num2 = Convert.ToInt32(Console.ReadLine());
                }
                Console.WriteLine($"Your result: {num1} / {num2} = " + (num1 / num2));
                break;
        }
    ```

   Po přidání kódu by měla `switch` vypadat část s příkazem podobně jako následující snímek obrazovky:

   ![Revidovaná část "switch" v editoru kódu sady Visual Studio](./media/csharp-console-calculator-switch-code.png)

Nyní, když vydělíte libovolné číslo nulou, aplikace požádá o další číslo. Ještě lepší: Nepřestane se ptát, dokud neposkytnete jiné číslo než nula.

   ![Editor kódu sady Visual Studio zobrazuje chybu dělení nulou](./media/csharp-console-calculator-dividebyzero.png)

### <a name="fix-the-format-error"></a>Oprava chyby "formát"

Pokud zadáte alfa znak, když aplikace očekává číselný znak (nebo naopak), konzolová aplikace zamrzne. Visual Studio pak ukazuje, co je špatně v editoru kódu.

   ![Editor kódu sady Visual Studio zobrazuje chybu formátu](./media/csharp-console-calculator-format-error.png)

Chcete-li tuto chybu opravit, musíme refaktorovat kód, který jsme dříve zadali.

#### <a name="revise-the-code"></a>Revize kódu

Spíše než spoléhat na třídu `program` pro zpracování všech kódů, `Calculator` rozdělíme naši aplikaci do dvou tříd: a `Program`.

Třída `Calculator` bude zpracovávat většinu práce výpočtu `Program` a třída bude zpracovávat uživatelské rozhraní a zachycování chyb práce.

Pusťme se do toho.

1. Odstraňte vše `Calculator` v oboru názvů mezi jeho otevírací a uzavíracími závorkami:

    ```csharp
    using System;

    namespace Calculator
    {
        
    }
    ```

1. Dále přidejte `Calculator` novou třídu takto:

    ```csharp
    class Calculator
    {
        public static double DoOperation(double num1, double num2, string op)
        {
            double result = double.NaN; // Default value is "not-a-number" which we use if an operation, such as division, could result in an error.

            // Use a switch statement to do the math.
            switch (op)
            {
                case "a":
                    result = num1 + num2;
                    break;
                case "s":
                    result = num1 - num2;
                    break;
                case "m":
                    result = num1 * num2;
                    break;
                case "d":
                    // Ask the user to enter a non-zero divisor.
                    if (num2 != 0)
                    {
                        result = num1 / num2;
                    }
                    break;
                // Return text for an incorrect option entry.
                default:
                    break;
            }
            return result;
        }
    }

    ```

1. Potom přidejte `Program` novou třídu takto:

    ```csharp
    class Program
    {
        static void Main(string[] args)
        {
            bool endApp = false;
            // Display title as the C# console calculator app.
            Console.WriteLine("Console Calculator in C#\r");
            Console.WriteLine("------------------------\n");

            while (!endApp)
            {
                // Declare variables and set to empty.
                string numInput1 = "";
                string numInput2 = "";
                double result = 0;

                // Ask the user to type the first number.
                Console.Write("Type a number, and then press Enter: ");
                numInput1 = Console.ReadLine();

                double cleanNum1 = 0;
                while (!double.TryParse(numInput1, out cleanNum1))
                {
                    Console.Write("This is not valid input. Please enter an integer value: ");
                    numInput1 = Console.ReadLine();
                }

                // Ask the user to type the second number.
                Console.Write("Type another number, and then press Enter: ");
                numInput2 = Console.ReadLine();

                double cleanNum2 = 0;
                while (!double.TryParse(numInput2, out cleanNum2))
                {
                    Console.Write("This is not valid input. Please enter an integer value: ");
                    numInput2 = Console.ReadLine();
                }

                // Ask the user to choose an operator.
                Console.WriteLine("Choose an operator from the following list:");
                Console.WriteLine("\ta - Add");
                Console.WriteLine("\ts - Subtract");
                Console.WriteLine("\tm - Multiply");
                Console.WriteLine("\td - Divide");
                Console.Write("Your option? ");

                string op = Console.ReadLine();

                try
                {
                    result = Calculator.DoOperation(cleanNum1, cleanNum2, op);
                    if (double.IsNaN(result))
                    {
                        Console.WriteLine("This operation will result in a mathematical error.\n");
                    }
                    else Console.WriteLine("Your result: {0:0.##}\n", result);
                }
                catch (Exception e)
                {
                    Console.WriteLine("Oh no! An exception occurred trying to do the math.\n - Details: " + e.Message);
                }

                Console.WriteLine("------------------------\n");

                // Wait for the user to respond before closing.
                Console.Write("Press 'n' and Enter to close the app, or press any other key and Enter to continue: ");
                if (Console.ReadLine() == "n") endApp = true;

                Console.WriteLine("\n"); // Friendly linespacing.
            }
            return;
        }
    }
    ```

1. Chcete-li spustit program, zvolte **Kalkulačka** nebo stiskněte **klávesu F5**.

1. Postupujte podle pokynů a vydělte číslo **42** číslem **119**. Vaše aplikace by měla vypadat podobně jako na následujícím snímku obrazovky:

    ![Okno konzoly zobrazující refaktorovou aplikaci Kalkulačka, která obsahuje výzvy, které mají být akce akce a zpracování chyb pro nesprávné vstupy](./media/csharp-console-calculator-refactored.png)

    Všimněte si, že máte možnost zadat další rovnice, dokud se nerozhodnete zavřít konzolovou aplikaci. A také jsme snížili počet desetinných míst ve výsledku.

## <a name="close-the-app"></a>Zavření aplikace

1. Pokud jste tak ještě neučinili, zavřete aplikaci kalkulačky.

1. Zavřete podokno **Výstup** v sadě Visual Studio.

   ![Zavření podokna Výstup v sadě Visual Studio](./media/csharp-calculator-close-output-pane.png)

1. V Sadě Visual Studio uložte aplikaci stisknutím **klávesctrl**+**s.**

1. Zavřete Visual Studio.

## <a name="code-complete"></a>Kód dokončen

Během tohoto kurzu jsme provedli mnoho změn v aplikaci kalkulačky. Aplikace nyní efektivněji zpracovává výpočetní prostředky a zpracovává většinu chyb vstupu uživatele.

Zde je kompletní kód, vše na jednom místě:

```csharp

using System;

namespace Calculator
{
    class Calculator
    {
        public static double DoOperation(double num1, double num2, string op)
        {
            double result = double.NaN; // Default value is "not-a-number" which we use if an operation, such as division, could result in an error.

            // Use a switch statement to do the math.
            switch (op)
            {
                case "a":
                    result = num1 + num2;
                    break;
                case "s":
                    result = num1 - num2;
                    break;
                case "m":
                    result = num1 * num2;
                    break;
                case "d":
                    // Ask the user to enter a non-zero divisor.
                    if (num2 != 0)
                    {
                        result = num1 / num2;
                    }
                    break;
                // Return text for an incorrect option entry.
                default:
                    break;
            }
            return result;
        }
    }

    class Program
    {
        static void Main(string[] args)
        {
            bool endApp = false;
            // Display title as the C# console calculator app.
            Console.WriteLine("Console Calculator in C#\r");
            Console.WriteLine("------------------------\n");

            while (!endApp)
            {
                // Declare variables and set to empty.
                string numInput1 = "";
                string numInput2 = "";
                double result = 0;

                // Ask the user to type the first number.
                Console.Write("Type a number, and then press Enter: ");
                numInput1 = Console.ReadLine();

                double cleanNum1 = 0;
                while (!double.TryParse(numInput1, out cleanNum1))
                {
                    Console.Write("This is not valid input. Please enter an integer value: ");
                    numInput1 = Console.ReadLine();
                }

                // Ask the user to type the second number.
                Console.Write("Type another number, and then press Enter: ");
                numInput2 = Console.ReadLine();

                double cleanNum2 = 0;
                while (!double.TryParse(numInput2, out cleanNum2))
                {
                    Console.Write("This is not valid input. Please enter an integer value: ");
                    numInput2 = Console.ReadLine();
                }

                // Ask the user to choose an operator.
                Console.WriteLine("Choose an operator from the following list:");
                Console.WriteLine("\ta - Add");
                Console.WriteLine("\ts - Subtract");
                Console.WriteLine("\tm - Multiply");
                Console.WriteLine("\td - Divide");
                Console.Write("Your option? ");

                string op = Console.ReadLine();

                try
                {
                    result = Calculator.DoOperation(cleanNum1, cleanNum2, op);
                    if (double.IsNaN(result))
                    {
                        Console.WriteLine("This operation will result in a mathematical error.\n");
                    }
                    else Console.WriteLine("Your result: {0:0.##}\n", result);
                }
                catch (Exception e)
                {
                    Console.WriteLine("Oh no! An exception occurred trying to do the math.\n - Details: " + e.Message);
                }

                Console.WriteLine("------------------------\n");

                // Wait for the user to respond before closing.
                Console.Write("Press 'n' and Enter to close the app, or press any other key and Enter to continue: ");
                if (Console.ReadLine() == "n") endApp = true;

                Console.WriteLine("\n"); // Friendly linespacing.
            }
            return;
        }
    }
}

```

## <a name="next-steps"></a>Další kroky

Gratulujeme k dokončení tohoto výukového programu! Chcete-li se dozvědět ještě více, pokračujte v následujících kurzech.

> [!div class="nextstepaction"]
> [Pokračovat v dalších kurzech jazyka C#](/dotnet/csharp/tutorials/)

## <a name="see-also"></a>Viz také

* [C# IntelliSense](../../ide/visual-csharp-intellisense.md)
* [Naučte se ladit kód Jazyka C# v sadě Visual Studio](tutorial-debugger.md)
