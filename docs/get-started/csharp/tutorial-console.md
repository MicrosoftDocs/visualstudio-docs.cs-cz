---
title: 'Kurz: Vytvoření jednoduché konzolové aplikace v jazyce C# '
description: naučte se, jak vytvořit konzolovou aplikaci v jazyce C# v Visual Studio, krok za krokem.
ms.custom: vs-acquisition, get-started
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
ms.openlocfilehash: 20732b0d7fb09de6079b0c1b7b06d2ae89802a5b
ms.sourcegitcommit: e7629e132a4d2fad6bb5869e4d68d9dbeeae9631
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/12/2021
ms.locfileid: "113649175"
---
# <a name="tutorial-create-a-simple-c-console-app-in-visual-studio-part-1-of-2"></a>kurz: vytvoření jednoduché konzolové aplikace v jazyce C# v Visual Studio (část 1 ze 2)

v tomto kurzu použijete Visual Studio k vytvoření a spuštění konzolové aplikace v jazyce C# a prozkoumání některých funkcí Visual Studio integrovaného vývojového prostředí (IDE). Tento kurz je první částí série kurzů se dvěma částmi.

V tomto kurzu:

> [!div class="checklist"]
> * vytvořte Visual Studio projekt.
> * Vytvořte konzolovou aplikaci v jazyce C#.
> * Ladit aplikaci.
> * Zavřete aplikaci.
> * Zkontrolujte kompletní kód.

[V části 2](tutorial-console-part-2.md)tuto aplikaci rozšíříte pomocí dalších projektů, ladicích štychů a odkazů na balíčky třetích stran.

## <a name="prerequisites"></a>Požadavky

musíte mít nainstalovanou Visual Studio.

::: moniker range="vs-2017"

pokud jste ještě nenainstalovali Visual Studio, pokračujte na stránku [soubory ke stažení Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) a nainstalujte si ji zdarma.

::: moniker-end

::: moniker range="vs-2019"

pokud jste ještě nenainstalovali Visual Studio, pokračujte na stránku [soubory ke stažení Visual Studio](https://visualstudio.microsoft.com/downloads) a nainstalujte si ji zdarma.

::: moniker-end

::: moniker range="vs-2022"

pokud jste ještě nenainstalovali Visual Studio 2022 preview, můžete si ji nainstalovat zdarma na stránku [Visual Studio 2022 preview](https://visualstudio.microsoft.com/vs/preview/vs2022) .

::: moniker-end

## <a name="create-a-project"></a>Vytvoření projektu

Začněte tím, že vytvoříte projekt aplikace v jazyce C#. Typ projektu se dodává se všemi soubory šablon, které budete potřebovat, než dokonce cokoli přidáte.

::: moniker range="vs-2017"

1. Otevřete sadu Visual Studio 2017.

2. v horním řádku nabídek vyberte **soubor**  >  **nový**  >  **Project**.
   (Případně stiskněte klávesu **CTRL** + **Posun** + **N**).

3. v levém podokně dialogového okna **nový Project** rozbalte položku **C#** a pak zvolte možnost **.net Core**. V prostředním podokně vyberte **aplikace konzoly (.NET Core)**. Pak pojmenujte **_kalkulačku_** souborů.

   ![šablona projektu konzolová aplikace (.net Core) v dialogovém okně nový Project v rozhraní IDE Visual Studio](./media/new-project-csharp-calculator-console-app.png)

### <a name="add-a-workload-optional"></a>Přidat úlohu (volitelné)

Pokud nevidíte šablonu projektu **Konzolová aplikace (.NET Core)** , můžete ji získat přidáním úlohy **vývoje .NET Core pro různé platformy** . Jak na to:

#### <a name="option-1-use-the-new-project-dialog-box"></a>možnost 1: použití dialogového okna nový Project

1. v levém podokně dialogového okna **nový Project** klikněte na odkaz **otevřít Instalační program pro Visual Studio** .

   ![vyberte odkaz otevřít Instalační program pro Visual Studio z dialogového okna nový Project](./media/csharp-open-visual-studio-installer-generic-dark.png)

1. Spustí se instalační program pro Visual Studio. Zvolte úlohu **vývoje .NET Core pro různé platformy** a pak zvolte **změnit**.

   ![úlohy vývoje .net Core pro různé platformy v Instalační program pro Visual Studio](./media/dot-net-core-xplat-dev-workload.png)

#### <a name="option-2-use-the-tools-menu-bar"></a>Možnost 2: použití panelu nabídky nástroje

1. zrušte výběr dialogového okna **nový Project** a v horním řádku nabídky vyberte **nástroje** > **získat nástroje a funkce**.

1. Spustí se instalační program pro Visual Studio. Zvolte úlohu **vývoje .NET Core pro různé platformy** a pak zvolte **změnit**.

::: moniker-end

::: moniker range=">=vs-2019"

1. Otevřete sadu Visual Studio.

1. V okně Start vyberte možnost **vytvořit nový projekt**.

   ![Zobrazit okno vytvořit nový projekt](../../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. V okně **vytvořit nový projekt** vyberte v seznamu jazyk položku **C#** . dále ze seznamu typy projektů vyberte možnost **Windows** ze seznamu platforem a **konzoly** . 

   Po použití filtrů typu jazyk, platforma a typ projektu zvolte šablonu **Konzolová aplikace** a klikněte na tlačítko **Další**.

    :::image type="content" source="./media/vs-2019/csharp-create-new-project-console-net-core.png" alt-text="Zvolit šablonu C# pro konzolovou aplikaci (.NET Framework)":::

   > [!NOTE]
   > Pokud nevidíte šablonu **konzolové aplikace** , můžete ji nainstalovat z okna **vytvořit nový projekt** . V části **nenajít, co hledáte?** klikněte na odkaz **instalovat další nástroje a funkce** .
   >
   > ![Odkaz pro instalaci dalších nástrojů a funkcí v okně vytvořit nový projekt v části nenajít, co hledáte?](../../get-started/media/vs-2019/not-finding-what-looking-for.png) 
   > 
   > pak v Instalační program pro Visual Studio zvolte úlohu **vývoje .net Core pro různé platformy** .
   >
   > ![úlohy vývoje .net Core pro různé platformy v Instalační program pro Visual Studio](./media/dot-net-core-xplat-dev-workload.png)
   >
   > potom klikněte na tlačítko **upravit** v Instalační program pro Visual Studio. Může se zobrazit výzva k uložení práce; Pokud ano, udělejte to. V dalším kroku vyberte **pokračovat** a nainstalujte úlohu. Pak se vraťte ke kroku 2 v tomto postupu "[Vytvoření projektu](#create-a-project)".

1. v okně **konfigurovat nový projekt** zadejte nebo zadejte *kalkulačku* do pole **Project název** . Pak klikněte na tlačítko **Další**.

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

    všimněte si, že když to uděláte, funkce IntelliSense v Visual Studio nabízí možnost automatického dokončování záznamu.

    > [!NOTE]
    > Následující animace není určena k duplikování předchozího kódu. Je určena pouze k zobrazení, jak funguje funkce automatického dokončování.

    ![animace celočíselného matematického kódu, který zobrazuje funkci automatického dokončování IntelliSense v Visual Studio IDE](./media/integer-math-intellisense.gif)

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

Aplikace kalkulačky momentálně přijímá a vrací celá čísla. Pokud ale přidáme kód, který umožňuje desetinná čísla, bude přesnější.

Stejně jako na následujícím snímku obrazovky platí, že pokud spustíte aplikaci a vydělíte číslo 42 číslem 119, výsledek bude 0 (nula), což není přesné.

![Okno konzoly zobrazující aplikaci kalkulačky, která v důsledku toho nevrací desetinná čísla](./media/csharp-console-calculator-nodecimal.png)

Opravme kód tak, aby zpracuje desetinná čísla.

1. Stisknutím **kláves Ctrl**  +  **H** otevřete ovládací prvek Najít **a** nahradit.

1. Změňte každou instanci `int` proměnné na `float` .

   Ujistěte se, že **v** ovládacím prvku Najít a nahradit přepínáte možnost Shoda s velká a malá písmena (**Alt** C ) a Shoda s celým + slovem (**Alt**  + **W**). 

    ![Animace ovládacího prvku Najít a nahradit znázorňující, jak změnit proměnnou int na float](./media/find-replace-control-animation.gif)

1. Znovu spusťte aplikaci kalkulačky a vydělte **číslo 42** číslem **119.**

   Všimněte si, že aplikace teď místo nuly vrací desetinné číslo.

    ![Okno konzoly zobrazující aplikaci Kalkulačka, která teď v důsledku toho vrací desetinná čísla](./media/csharp-console-calculator-decimal.png)

Aplikace ale vytvoří pouze desítkový výsledek. Pojďme kód ještě trochu upravit, aby aplikace také vypočítala desetinná čísla.

1. Pomocí **ovládacího prvku** Najít a nahradit (**Ctrl** H ) změňte jednotlivé instance proměnné na a ke změně  +  jednotlivých instancí metody na `float` `double` `Convert.ToInt32` `Convert.ToDouble` .

1. Spusťte aplikaci kalkulačky a vydělte **číslo 42,5** číslem **119,75**.

   Všimněte si, že aplikace teď přijímá desetinné hodnoty a vrací jako výsledek delší desetinné číslo.

    ![Okno konzoly zobrazující aplikaci Kalkulačka, která teď přijímá desetinná čísla a vrací v důsledku toho delší desetinná čísla](./media/csharp-console-calculator-usedecimals.png)

    (Počet desetinných míst opravíme v části [Revize](#revise-the-code) kódu.)

## <a name="debug-the-app"></a>Ladění aplikace

Vylepšili jsme aplikaci základní kalkulačky, ale zatím nemá k dispozici bezpečnostní opatření pro selhání pro zpracování výjimek, jako jsou chyby uživatelského vstupu.

Pokud se například pokusíte vydělit číslo nulou nebo zadat alfa znak, když aplikace očekává číselný znak (nebo naopak), může aplikace přestat fungovat, vrátit chybu nebo vrátit neočekávaný nečísný výsledek.

Pojďme si projít několik běžných chyb uživatelského vstupu, vyhledat je v ladicím programu, pokud se tam objeví, a opravit je v kódu.

> [!TIP]
> Další informace o ladicím programu a o tom, jak funguje, najdete na stránce První [pohled na Visual Studio ladicího](../../debugger/debugger-feature-tour.md) programu.

### <a name="fix-the-divide-by-zero-error"></a>Oprava chyby "vydělit nulou"

Když se pokusíte číslo vydělit nulou, může se konzolová aplikace zablokovat a pak v editoru kódu zobrazit, co je špatně.

   ![Snímek obrazovky Visual Studio kódu zobrazující řádek zvýrazněný žlutě a chybu Exception Unhandled (Neošetřená výjimka) pro "Attempted to divide by zero" (Pokus o dělení nulou)](./media/csharp-console-calculator-dividebyzero-error.png)

> [!NOTE]
> Někdy se aplikace nezablokuje a ladicí program nebude zobrazovat chybu dělení nulou. Místo toho může aplikace vrátit neočekávaný nečísový výsledek, například symbol nekonečna. Stále platí následující oprava kódu.

Změňte kód tak, aby tuto chybu zvládl.

1. Odstraňte kód, který se zobrazí přímo mezi `case "d":` a komentářem , který říká `// Wait for the user to respond before closing` .

1. Nahraďte ho následujícím kódem:

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

   Po přidání kódu by část s příkazem měla vypadat `switch` podobně jako na následujícím snímku obrazovky:

   ![Upravená část switch v editoru Visual Studio kódu](./media/csharp-console-calculator-switch-code.png)

Když teď jakékoli číslo vydělíte nulou, aplikace vás požádá o další číslo. Ještě lepší: Nepřestane se ptát, dokud nezadáte jiné číslo než nulu.

   ![Snímek obrazovky Visual Studio editoru kódu zobrazující kód pro příkaz switch s přidanou kontrolu pro zadání nenulového dělitele](./media/csharp-console-calculator-dividebyzero.png)

### <a name="fix-the-format-error"></a>Oprava chyby "format"

Pokud zadáte alfanumerický znak, když aplikace očekává číselný znak (nebo naopak), konzolová aplikace se zablokuje. Visual Studio se v editoru kódu zobrazí, co je špatně.

   ![V Visual Studio kódu se zobrazí chyba formátu.](./media/csharp-console-calculator-format-error.png)

Pokud chcete tuto chybu vyřešit, musíme refaktorovat kód, který jsme zadali dříve.

#### <a name="revise-the-code"></a>Revize kódu

Místo toho, abyste ke zpracování veškerého kódu spoléhají na třídu , rozdělíme aplikaci do dvou tříd: a `program` `Calculator` `Program` .

Třída bude zpracovávat většinu výpočtů a třída bude zpracovávat uživatelské rozhraní a `Calculator` `Program` práci zachytávání chyb.

Tak se do toho pusťme.

1. Odstraňte vše v oboru názvů mezi jeho počátečními a `Calculator` uzavíracími složenami závorkami:

    ```csharp
    using System;

    namespace Calculator
    {
        
    }
    ```

1. Dále přidejte novou `Calculator` třídu následujícím způsobem:

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

1. Zvolte **Kalkulačku,** aby se program spouštěl, nebo stiskněte **klávesu F5**.

1. Postupujte podle vý výzvy a vydělte **číslo 42** číslem **119**. Vaše aplikace by měla vypadat podobně jako na následujícím snímku obrazovky:

    ![Okno konzoly zobrazující refaktorované aplikace kalkulačky, která obsahuje výzvy, které akce se mají provádět, a zpracování chyb kvůli nesprávným vstupům](./media/csharp-console-calculator-refactored.png)

    Všimněte si, že máte možnost zadat další rovnice, dokud se rozhodnete zavřít konzolovou aplikaci. Také jsme snížili počet desetinných míst ve výsledku.

## <a name="close-the-app"></a>Zavření aplikace

1. Pokud jste to ještě neudělali, zavřete aplikaci kalkulačky.

1. Zavřete **podokno** Výstup v Visual Studio.

   ![Zavřete podokno Výstup v Visual Studio](./media/csharp-calculator-close-output-pane.png)

1. V Visual Studio stisknutím **Klávesy Ctrl** + **S** aplikaci uložte.

1. Zavřete Visual Studio.

## <a name="review-code-complete"></a>Revize: Dokončení kódu

V tomto kurzu jsme provedli spoustu změn aplikace kalkulačky. Aplikace teď zpracovává výpočetní prostředky efektivněji a zpracovává většinu chyb uživatelského vstupu.

Tady je kompletní kód, vše na jednom místě:

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

Pokračujte v dalších kurzech:

> [!div class="nextstepaction"]
> [Kurzy k jazyku C#](/dotnet/csharp/tutorials)

> [!div class="nextstepaction"]
> [Prohlídka integrovaného vývojového prostředí sady Visual Studio](../visual-studio-ide.md)

:::moniker-end

:::moniker range=">=vs-2019"

Pokračujte druhou částí tohoto kurzu:

> [!div class="nextstepaction"]
> [Kurz 2. část: Použití více projektů a balíčků třetích stran](tutorial-console-part-2.md)
:::moniker-end

Také zajímavé:

- [Pokračujte v dalších kurzech pro jazyk C#.](/dotnet/csharp/tutorials/)
- [Rychlý start: Vytvoření ASP.NET Core aplikace](../../ide/quickstart-aspnet-core.md)
- [Naučte se ladit kód jazyka C# v Visual Studio](tutorial-debugger.md)
- Návod, jak [vytvářet a spouštět testy jednotek](../../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md)
- [Spuštění programu v jazyce C#](run-program.md)
- [C# IntelliSense](../../ide/visual-csharp-intellisense.md)
- [Pokračování s přehledem Visual Studio IDE](/../visual-studio-ide.md)