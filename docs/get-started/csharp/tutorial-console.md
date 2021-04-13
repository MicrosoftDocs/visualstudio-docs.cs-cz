---
title: 'Kurz: Vytvoření jednoduché konzolové aplikace v jazyce C#'
description: Naučte se, jak vytvořit konzolovou aplikaci v jazyce C# v aplikaci Visual Studio, krok za krokem.
ms.custom: seodec18, get-started
ms.date: 02/10/2021
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: tutorial
ms.devlang: CSharp
author: j-martens
ms.author: jmartens
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 12f00bedba6078fc5c471d02b92630b49dd35afa
ms.sourcegitcommit: 6d88913a8b5a9e5eda01d3f95205b4d138f440f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/13/2021
ms.locfileid: "107295621"
---
# <a name="tutorial-create-a-simple-c-console-app-in-visual-studio"></a>Kurz: Vytvoření jednoduché konzolové aplikace v jazyce C# v aplikaci Visual Studio

V tomto kurzu pro C# použijete Visual Studio k vytvoření a spuštění konzolové aplikace a Prozkoumejte některé funkce integrovaného vývojového prostředí (IDE) sady Visual Studio.

::: moniker range="vs-2017"

Pokud jste ještě nenainstalovali Visual Studio, navštivte stránku [ke stažení pro Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) a nainstalujte si ji zdarma.

::: moniker-end

::: moniker range="vs-2019"

Pokud jste ještě nenainstalovali Visual Studio, navštivte stránku [ke stažení pro Visual Studio](https://visualstudio.microsoft.com/downloads) a nainstalujte si ji zdarma.

::: moniker-end

## <a name="create-a-project"></a>Vytvoření projektu

Začněte tím, že vytvoříte projekt aplikace v jazyce C#. Typ projektu se dodává se všemi soubory šablon, které budete potřebovat, než dokonce cokoli přidáte.

::: moniker range="vs-2017"

1. Otevřete sadu Visual Studio 2017.

2. V horním řádku nabídek vyberte **soubor**  >  **Nový**  >  **projekt**.
   (Případně stiskněte klávesu **CTRL** + **Posun** + **N**).

3. V levém podokně dialogového okna **Nový projekt** rozbalte položku **C#** a pak zvolte možnost **.NET Core**. V prostředním podokně vyberte **aplikace konzoly (.NET Core)**. Pak pojmenujte **_kalkulačku_** souborů.

   ![Šablona projektu Konzolová aplikace (.NET Core) v dialogovém okně Nový projekt v integrovaném vývojovém prostředí sady Visual Studio](./media/new-project-csharp-calculator-console-app.png)

### <a name="add-a-workload-optional"></a>Přidat úlohu (volitelné)

Pokud nevidíte šablonu projektu **Konzolová aplikace (.NET Core)** , můžete ji získat přidáním úlohy **vývoje .NET Core pro různé platformy** . Jak na to:

#### <a name="option-1-use-the-new-project-dialog-box"></a>Možnost 1: použití dialogového okna Nový projekt

1. V levém podokně dialogového okna **Nový projekt** vyberte odkaz **otevřít instalační program pro Visual Studio** .

   ![Vyberte odkaz otevřít Instalační program pro Visual Studio z dialogového okna Nový projekt.](./media/csharp-open-visual-studio-installer-generic-dark.png)

1. Spustí se instalační program pro Visual Studio. Zvolte úlohu **vývoje .NET Core pro různé platformy** a pak zvolte **změnit**.

   ![Úlohy vývoje .NET Core pro různé platformy v Instalační program pro Visual Studio](./media/dot-net-core-xplat-dev-workload.png)

#### <a name="option-2-use-the-tools-menu-bar"></a>Možnost 2: použití panelu nabídky nástroje

1. Zrušte z dialogového okna **Nový projekt** a v horním řádku nabídky vyberte **nástroje** > **získat nástroje a funkce**.

1. Spustí se instalační program pro Visual Studio. Zvolte úlohu **vývoje .NET Core pro různé platformy** a pak zvolte **změnit**.

::: moniker-end

::: moniker range="vs-2019"

1. Otevřete Visual Studio 2019.

1. V okně Start vyberte možnost **vytvořit nový projekt**.

   ![Zobrazit okno vytvořit nový projekt](../../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. V okně **vytvořit nový projekt** vyberte v seznamu jazyk položku **C#** . Dále ze seznamu typy projektů vyberte možnost **Windows** ze seznamu platforem a **konzole** . 

   Po použití filtrů typu jazyk, platforma a typ projektu zvolte šablonu **Konzolová aplikace** a klikněte na tlačítko **Další**.

    :::image type="content" source="./media/vs-2019/csharp-create-new-project-console-net-core.png" alt-text="Zvolit šablonu C# pro konzolovou aplikaci (.NET Framework)":::

   > [!NOTE]
   > Pokud nevidíte šablonu **konzolové aplikace** , můžete ji nainstalovat z okna **vytvořit nový projekt** . V části **nenajít, co hledáte?** klikněte na odkaz **instalovat další nástroje a funkce** .
   >
   > ![Odkaz pro instalaci dalších nástrojů a funkcí v okně vytvořit nový projekt v části nenajít, co hledáte?](../../get-started/media/vs-2019/not-finding-what-looking-for.png) 
   > 
   > Pak v Instalační program pro Visual Studio zvolte úlohu **vývoje .NET Core pro různé platformy** .
   >
   > ![Úlohy vývoje .NET Core pro různé platformy v Instalační program pro Visual Studio](./media/dot-net-core-xplat-dev-workload.png)
   >
   > Potom klikněte na tlačítko **Upravit** v instalační program pro Visual Studio. Může se zobrazit výzva k uložení práce; Pokud ano, udělejte to. V dalším kroku vyberte **pokračovat** a nainstalujte úlohu. Pak se vraťte ke kroku 2 v tomto postupu "[Vytvoření projektu](#create-a-project)".

1. V okně **Konfigurovat nový projekt** zadejte nebo zadejte *kalkulačku* do pole **název projektu** . Pak klikněte na tlačítko **Další**.

    :::image type="content" source="./media/vs-2019/csharp-name-your-calculator-project.png" alt-text="v okně Konfigurovat nový projekt pojmenujte svůj projekt Kalkulačka.":::
   
1. V okně **Další informace** by měl být **.NET Core 3,1** již vybraný pro vaši cílovou architekturu. Pokud ne, vyberte **.NET Core 3,1**. Pak zvolte **vytvořit**.

    :::image type="content" source="./media/vs-2019/csharp-target-framework.png" alt-text="v okně Další informace se ujistěte, že je vybraná možnost .NET Core 3,1.":::

   Visual Studio otevře nový projekt, který obsahuje výchozí kód "Hello World".

::: moniker-end

## <a name="create-the-app"></a>Vytvoření aplikace

Nejprve prozkoumáme některé základní celočíselné matematické hodnoty v jazyce C#. Pak přidáme kód pro vytvoření základní kalkulačky. Potom budeme ladit aplikaci, abychom našli a opravili chyby. A nakonec kód Vylepšete, aby bylo efektivnější.

### <a name="explore-integer-math"></a>Seznámení s matematikou celých čísel

Pojďme v C# začít s některým z celých čísel Basic Integer Math.

1. V editoru kódu odstraňte výchozí kód "Hello World".

    ![Odstranění výchozího Hello World kódu z nové aplikace kalkulačky](./media/csharp-console-calculator-deletehelloworld.png)

   Konkrétně odstraňte řádek, který říká, `Console.WriteLine("Hello World!");` .

1. Do svého umístění zadejte následující kód:

    ```csharp
            int a = 42;
            int b = 119;
            int c = a + b;
            Console.WriteLine(c);
            Console.ReadKey();
    ```

    Všimněte si, že když to uděláte, funkce IntelliSense v aplikaci Visual Studio vám nabídne možnost automatického dokončování záznamu.

    > [!NOTE]
    > Následující animace není určena k duplikování předchozího kódu. Je určena pouze k zobrazení, jak funguje funkce automatického dokončování.

    ![Animace celočíselného matematického kódu, který zobrazuje funkci automatického dokončování IntelliSense v integrovaném vývojovém prostředí sady Visual Studio](./media/integer-math-intellisense.gif)

1. Zvolte zelené tlačítko **Start** vedle **kalkulačky** a sestavte a spusťte program, nebo stiskněte klávesu **F5**.

   ![Kliknutím na tlačítko kalkulačky spusťte aplikaci z panelu nástrojů.](./media/csharp-console-calculator-button.png)

   Otevře se okno konzoly, které odhalí součet 42 + 119, což je **161**.

    ![Okno konzoly zobrazující výsledky typu Integer Math](./media/csharp-console-integer-math.png)

1. **(Volitelné)** Chcete-li změnit výsledek, můžete změnit operátor. Například můžete změnit `+` operátor v `int c = a + b;` řádku kódu na `-` pro odčítání, `*` pro násobení nebo `/` pro dělení. Pak se při spuštění programu změní i výsledek.

1. Zavřete okno konzoly.

### <a name="add-code-to-create-a-calculator"></a>Přidání kódu pro vytvoření kalkulačky

Pojďme pokračovat přidáním komplexnější sady kódu kalkulačky do vašeho projektu.

1. Odstraňte veškerý kód, který se zobrazí v editoru kódu.

1. Do editoru kódu zadejte nebo vložte následující nový kód:

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

1. Zvolte **kalkulačku** pro spuštění programu nebo stiskněte klávesu **F5**.

   ![Kliknutím na tlačítko kalkulačky spusťte aplikaci z panelu nástrojů.](./media/csharp-console-calculator-button.png)

   Otevře se okno konzoly.

1. Zobrazte aplikaci v okně konzoly a podle pokynů přidejte čísla **42** a **119**.

   Vaše aplikace by měla vypadat podobně jako na následujícím snímku obrazovky:

    ![Okno konzoly zobrazující aplikaci kalkulačky a obsahuje výzvy, které akce se mají provést](./media/csharp-console-calculator.png)

### <a name="add-functionality-to-the-calculator"></a>Přidání funkcí do kalkulačky

Pojďme upravit kód pro přidání dalších funkcí.

### <a name="add-decimals"></a>Přidat desetinná místa

Aplikace kalkulačky aktuálně přijímá a vrací celá čísla. Ale bude přesnější, pokud přidáme kód, který umožňuje desetinných míst.

Jak je znázorněno na následujícím snímku obrazovky, pokud aplikaci spouštíte a číslo 42 vydělíte číslem 119, výsledek je 0 (nula), což není přesné.

![Okno konzoly zobrazující aplikaci kalkulačky, která nevrací desítkové číslo jako výsledek](./media/csharp-console-calculator-nodecimal.png)

Pojďme kód opravit tak, aby zpracovává desetinná místa.

1. Stisknutím **kombinace kláves CTRL**  +  **H** otevřete ovládací prvek **Najít a nahradit** .

1. Změňte všechny instance `int` proměnné na `float` .

   Ujistěte se, že jste přepnuli rozlišovat **velikost písmen** (**ALT** + **C**) a **odpovídá celému slovu** (**ALT** + **W**) v ovládacím prvku **Najít a nahradit** .

    ![Animace ovládacího prvku Find a Replace ukazující, jak změnit proměnnou int na float](./media/find-replace-control-animation.gif)

1. Spusťte znovu aplikaci kalkulačky a vydělte číslo **42** číslem **119**.

   Všimněte si, že aplikace teď vrací desítkové číslo místo nuly.

    ![Okno konzoly zobrazující aplikaci kalkulačky, která teď jako výsledek vrátí desítkovou číslici](./media/csharp-console-calculator-decimal.png)

Aplikace ale produkuje jenom desítkový výsledek. Pojďme udělat ještě několik vylepšení kódu, aby mohla aplikace vypočítat desetinná místa.

1. Použijte ovládací prvek **Najít a nahradit** (**CTRL**  +  **H**) ke změně každé instance `float` proměnné na a `double` ke změně každé instance `Convert.ToInt32` metody na `Convert.ToDouble` .

1. Spusťte aplikaci kalkulačky a číslo **42,5** vydělte číslem **119,75**.

   Všimněte si, že aplikace teď přijímá desítkové hodnoty a jako svůj výsledek vrátí delší desetinné číslo.

    ![Okno konzoly zobrazující aplikaci kalkulačky, která teď přijímá desítková čísla a jako výsledek vrátí delší desetinné číslo](./media/csharp-console-calculator-usedecimals.png)

    (Počet desetinných míst vyřešíme v části [Revize kódu](#revise-the-code) .)

## <a name="debug-the-app"></a>Ladění aplikace

Vylepšili jsme základní aplikaci kalkulačky, ale ještě nedošlo k jejich bezpečnému selhání, aby bylo možné zpracovávat výjimky, například chyby vstupu uživatele.

Například pokud se pokusíte dělit číslo nulou nebo zadat alfa znak, když aplikace očekává číselný znak (nebo naopak), může aplikace přestat pracovat, vracet chybu nebo vracet neočekávaný nečíselný výsledek.

Pojďme si projít několik běžných chyb vstupu uživatele, vyhledat je v ladicím programu, pokud se tam objeví, a opravit je v kódu.

> [!TIP]
> Další informace o ladicím programu a jeho fungování najdete na stránce [ladicího programu sady Visual Studio na první pohled](../../debugger/debugger-feature-tour.md) .

### <a name="fix-the-divide-by-zero-error"></a>Opravit chybu dělení nulou

Když se pokusíte dělit číslo nulou, aplikace konzoly se může ukotvit a pak se zobrazí informace o tom, co je v editoru kódu chybné.

   ![Snímek obrazovky editoru kódu sady Visual Studio ukazující žlutě zvýrazněný řádek a Neošetřená chyba pro ' pokus o dělení nulou '.](./media/csharp-console-calculator-dividebyzero-error.png)

> [!NOTE]
> V některých případech se aplikace neblokuje a ladicí program nebude zobrazovat chybu s dělením nulou. Místo toho může aplikace vracet neočekávaný nenumerický výsledek, jako je například symbol nekonečno. Následující oprava kódu se pořád používá.

Pojďme změnit kód pro zpracování této chyby.

1. Odstraňte kód, který se zobrazí přímo mezi `case "d":` a komentář, který říká `// Wait for the user to respond before closing` .

1. Nahraďte ji následujícím kódem:

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

   Po přidání kódu by část s `switch` příkazem měla vypadat podobně jako na následujícím snímku obrazovky:

   ![Revidovaný oddíl Switch v editoru kódu sady Visual Studio](./media/csharp-console-calculator-switch-code.png)

Když teď číslo vydělíte nulou, aplikace si vyžádá další číslo. Ještě lepší: přestane zobrazovat výzvy, dokud nezadáte číslo jiné než nula.

   ![Snímek obrazovky editoru kódu sady Visual Studio zobrazující kód pro příkaz switch s kontrolou pro položku, která je přidána nenulovému děliteli.](./media/csharp-console-calculator-dividebyzero.png)

### <a name="fix-the-format-error"></a>Opravit chybu "formát"

Pokud zadáte alfanumerický znak, když aplikace očekává číselný znak (nebo naopak), aplikace konzoly se zablokuje. Visual Studio potom ukáže, co je v editoru kódu chybné.

   ![V editoru kódu sady Visual Studio se zobrazuje chyba formátu](./media/csharp-console-calculator-format-error.png)

Abychom mohli tuto chybu opravit, musíme kód, který jsme předtím zadali, Refaktorovat.

#### <a name="revise-the-code"></a>Revize kódu

Místo toho `program` , aby se při zpracování veškerého kódu spoléhá na třídu, rozdělíme naši aplikaci na dvě třídy: `Calculator` a `Program` .

`Calculator`Třída zpracuje hromadnou práci výpočtu a `Program` Třída zpracuje uživatelské rozhraní a zachytávání chyb.

Tak se do toho pusťme.

1. Odstranit vše v `Calculator` oboru názvů mezi otevírací a pravou závorkou:

    ```csharp
    using System;

    namespace Calculator
    {
        
    }
    ```

1. Dále přidejte novou třídu následujícím `Calculator` způsobem:

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

1. Pak přidejte novou  `Program` třídu následujícím způsobem:

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

1. Zvolte **kalkulačku** pro spuštění programu nebo stiskněte klávesu **F5**.

1. Postupujte podle výzev a vydělte číslo **42** číslem **119**. Vaše aplikace by měla vypadat podobně jako na následujícím snímku obrazovky:

    ![Okno konzoly zobrazující refaktorované aplikace kalkulačky, které obsahují výzvy, které akce při zpracování a zpracování chyb budou mít nesprávné vstupy](./media/csharp-console-calculator-refactored.png)

    Všimněte si, že máte možnost zadat další rovnice, dokud se nerozhodnete zavřít konzolovou aplikaci. A také jsme snížili počet desetinných míst ve výsledku.

## <a name="close-the-app"></a>Zavřít aplikaci

1. Pokud jste to ještě neudělali, zavřete aplikaci Kalkulačka.

1. Zavřete podokno **výstup** v aplikaci Visual Studio.

   ![Zavření podokna výstup v aplikaci Visual Studio](./media/csharp-calculator-close-output-pane.png)

1. V aplikaci Visual Studio uložte aplikaci stisknutím **kombinace kláves CTRL +** +  .

1. Zavřete Visual Studio.

## <a name="code-complete"></a>Kód je kompletní

V tomto kurzu jsme udělali spoustu změn v aplikaci kalkulačky. Aplikace nyní zpracovává výpočetní prostředky efektivněji a zpracovává většinu chyb vstupu uživatele.

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

:::moniker range="vs-2017"

Pokračovat s dalšími kurzy:

> [!div class="nextstepaction"]
> [Kurzy C#](/dotnet/csharp/tutorials)

> [!div class="nextstepaction"]
> [Prohlídka integrovaného vývojového prostředí sady Visual Studio](../visual-studio-ide.md)

:::moniker-end

:::moniker range="vs-2019"

Pokračujte v druhé části tohoto kurzu:

> [!div class="nextstepaction"]
> [Pokračovat s částí 2](tutorial-console-part-2.md)
:::moniker-end

## <a name="see-also"></a>Viz také

* [C# IntelliSense](../../ide/visual-csharp-intellisense.md)
* [Naučte se ladit kód C# v aplikaci Visual Studio.](tutorial-debugger.md)
