---
title: 'Kurz: Rozšíření jednoduché konzolové aplikace v jazyce C#'
description: Naučte se vyvíjet konzolovou aplikaci v jazyce C# Visual Studio krok za krokem.
ms.custom: vs-acquisition, get-started
ms.date: 04/15/2021
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: tutorial
ms.devlang: CSharp
author: ghogen
ms.author: ghogen
manager: jmartens
monikerRange: '>=vs-2019'
dev_langs:
- CSharp
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: c7c38ed40143064090535735b2050dd31904d608
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2021
ms.locfileid: "112390174"
---
# <a name="tutorial-extend-a-simple-c-console-app"></a>Kurz: Rozšíření jednoduché konzolové aplikace v jazyce C#

V tomto kurzu se dozvíte, jak pomocí Visual Studio rozšířit konzolovou aplikaci, kterou jste vytvořili v první části. Seznámíte se s některými funkcemi v Visual Studio, které budete potřebovat pro každodenní vývoj, například správu více projektů a odkazování na balíčky třetích stran.

Pokud jste právě [dokončili první část](tutorial-console.md) této série, už máte konzolovou aplikaci Kalkulačka.  Pokud chcete přeskočit část 1, můžete začít otevřením projektu z úložiště GitHub. Aplikace Kalkulačka jazyka C# je v repo [vs-tutorial-samples,](https://github.com/MicrosoftDocs/vs-tutorial-samples)takže můžete začít podle kroků v [kurzu:](../tutorial-open-project-from-repo.md) Otevření projektu z tohoto místa.

## <a name="add-a-new-project"></a>Přidání nového projektu

Kód z reálného světa zahrnuje mnoho projektů, které spolupracují v řešení. Teď do aplikace Calculator přidáme další projekt. Bude to knihovna tříd, která poskytuje některé funkce kalkulačky.

1. V Visual Studio můžete použít příkaz nabídky nejvyšší úrovně Soubor Přidat nový projekt a přidat nový projekt, ale můžete také kliknout pravým tlačítkem na existující název projektu (nazývaný "uzel projektu") a otevřít místní nabídku projektu (nebo místní  >    >   nabídku). Tato místní nabídka obsahuje mnoho způsobů, jak do projektů přidat funkce. Proto klikněte pravým tlačítkem na uzel projektu v **Průzkumník řešení** a zvolte **Přidat**  >  **nový projekt**.

1. Zvolte knihovnu tříd šablony projektu C# **(.NET Standard).**

   ![Snímek obrazovky s výběrem šablony projektu knihovny tříd](media/vs-2019/calculator2-add-project-dark.png)

1. Zadejte název projektu **CalculatorLibrary** a zvolte **Vytvořit.** Po zobrazení otázky znovu zvolte .NET 3.1. Visual Studio vytvoří nový projekt a přidá ho do řešení.

   ![Snímek obrazovky Průzkumník řešení s přidaným projektem knihovny tříd CalculatorLibrary](media/vs-2019/calculator2-solution-explorer-with-class-library-dark2.png)

1. Místo souboru *Class1.cs* přejmenujte soubor **CalculatorLibrary.cs.** Můžete kliknout na název v **Průzkumník řešení** ho přejmenovat, nebo kliknout pravým tlačítkem a zvolit **Přejmenovat** nebo stisknout **klávesu F2.**

   Může se zobrazit dotaz, jestli chcete v souboru přejmenovat nějaké `Class1` odkazy na . Nezáleží na tom, jak na to odpovíte, protože v dalším kroku nahradíte kód.

1. Teď musíme přidat odkaz na projekt, aby první projekt mohl používat rozhraní API vystavená novou knihovnou tříd.  Klikněte pravým tlačítkem na **uzel Závislosti** v prvním projektu a zvolte **Přidat odkaz na projekt.**

   ![Snímek obrazovky s položkou nabídky Přidat odkaz na projekt](media/vs-2019/calculator2-add-project-reference-dark.png)

   Zobrazí **se dialogové okno Správce** odkazů. Toto dialogové okno umožňuje přidat odkazy na jiné projekty, stejně jako sestavení a knihovny DLL modelu COM, které vaše projekty potřebují.

   ![Snímek obrazovky s dialogem Správce odkazů](media/vs-2019/calculator2-ref-manager-dark.png)

1. V dialogovém **okně Správce** odkazů zaškrtněte políčko u projektu **CalculatorLibrary** a zvolte **OK.**  Odkaz na projekt se zobrazí v **uzlu Projekty** v **Průzkumník řešení**.

   ![Snímek obrazovky Průzkumník řešení s referenčními odkazy na projekt](media/vs-2019/calculator2-solution-explorer-with-project-reference-dark2.png)

1. V *souboru Program.cs* vyberte třídu a veškerý její kód a stisknutím kombinace kláves `Calculator` **CTRL+X** ji vyjmout ze souboru Program.cs. Potom v **souboru CalculatorLibrary** v *souboru CalculatorLibrary.cs* vložte kód do oboru `CalculatorLibrary` názvů . Potom nastavte třídu Calculator tak, `public` aby ji vystavěla mimo knihovnu. Kód v *souboru CalculatorLibrary.cs* by teď měl vypadat podobně jako následující kód:

   ```csharp
   using System;

    namespace CalculatorLibrary
    {
        public class Calculator
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
    }
   ```

1. První projekt obsahuje odkaz, ale zobrazí se chyba, že se volání Calculator.DoOperation nevyřeší. Je to proto, že Knihovna_kalkulačky se nachází v jiném oboru názvů, proto pro plně kvalifikovaný odkaz přidejte `CalculatorLibrary` obor názvů.

   ```csharp
   result = CalculatorLibrary.Calculator.DoOperation(cleanNum1, cleanNum2, op);
   ```

   Zkuste místo toho na začátek souboru přidat direktivu using:

   ```csharp
   using CalculatorLibrary;
   ```

   Tato změna by vám měla z webu volání odebrat obor názvů CalculatorLibrary, ale teď je tu nejednoznačnost. Je `Calculator` třída v CalculatorLibrary, nebo je obor názvů Kalkulačka?  Pokud chcete vyřešit nejednoznačnost, přejmenujte obor názvů `CalculatorProgram` .

   ```csharp
   namespace CalculatorProgram
   ```

## <a name="reference-net-libraries-write-to-a-log"></a>Referenční knihovny .NET: zápis do protokolu

1. Předpokládejme, že teď chcete přidat protokol všech operací a zapsat ho do textového souboru. Tuto funkci `Trace` poskytuje třída .NET. (Je užitečná také pro základní techniky ladění tisku.)  Třída Trace je v System.Diagnostics a budeme potřebovat System.IO, jako je , takže začněte přidáním direktiv using na začátek `StreamWriter` *souboru CalculatorLibrary.cs:*

   ```csharp
   using System.IO;
   using System.Diagnostics;
   ```

1. Když se podíváme na to, jak se třída Trace používá, musíte uchovat odkaz na třídu , která je přidružena k streamu filestream. To znamená, že kalkulačka by fungovala lépe jako objekt, takže přidáme konstruktor na začátek třídy Calculator v *souboru CalculatorLibrary.cs.*

   ```csharp
   public Calculator()
        {
            StreamWriter logFile = File.CreateText("calculator.log");
            Trace.Listeners.Add(new TextWriterTraceListener(logFile));
            Trace.AutoFlush = true;
            Trace.WriteLine("Starting Calculator Log");
            Trace.WriteLine(String.Format("Started {0}", System.DateTime.Now.ToString()));
        }

    public double DoOperation(double num1, double num2, string op)
        {
   ```

1. A musíme změnit statickou `DoOperation` metodu na členské metody, proto odeberte klíčové `static` slovo .  Pojďme také do každého výpočtu pro protokol přidat výstup, aby DoOperation vypadal jako následující kód:

   ```csharp
   public double DoOperation(double num1, double num2, string op)
   {
        double result = double.NaN; // Default value is "not-a-number" which we use if an operation, such as division, could result in an error.

        // Use a switch statement to do the math.
        switch (op)
        {
            case "a":
                result = num1 + num2;
                Trace.WriteLine(String.Format("{0} + {1} = {2}", num1, num2, result));
                break;
            case "s":
                result = num1 - num2;
                Trace.WriteLine(String.Format("{0} - {1} = {2}", num1, num2, result));
                break;
            case "m":
                result = num1 * num2;
                Trace.WriteLine(String.Format("{0} * {1} = {2}", num1, num2, result));
                break;
            case "d":
                // Ask the user to enter a non-zero divisor.
                if (num2 != 0)
                {
                    result = num1 / num2;
                    Trace.WriteLine(String.Format("{0} / {1} = {2}", num1, num2, result));
                }
                    break;
            // Return text for an incorrect option entry.
            default:
                break;
        }
        return result;
    }
   ```

1. V souboru *Program.cs je teď* statické volání označeno červenouquiggly. Pokud ji chcete opravit, vytvořte `calculator` proměnnou přidáním následujícího řádku těsně před `while (!endApp)` smyčku:

   ```csharp
   Calculator calculator = new Calculator();
   ```

   A upravte lokalitu volání pro následujícím způsobem tak, aby odkaz na objekt s názvem malými písmeny, čímž se z tohoto volání členu místo volání statické `DoOperation` `calculator` metody odkazuje:

   ```csharp
   result = calculator.DoOperation(cleanNum1, cleanNum2, op);
   ```

1. Spusťte program znovu a až to bude hotové, klikněte pravým tlačítkem na uzel projektu, zvolte Otevřít složku v **Průzkumník souborů** a pak přejděte dolů Průzkumník souborů výstupní složce. Může to být *bin/Debug/netcoreapp3.1* a otevřete soubor *calculator.log.*

    ```output
    Starting Calculator Log
    Started 7/9/2020 1:58:19 PM
    1 + 2 = 3
    3 * 3 = 9
    ```

V tuto chvíli by *soubor CalculatorLibrary.cs* měl vypadat nějak takhle:

```csharp
using System;
using System.IO;
using System.Diagnostics;


namespace CalculatorLibrary
{
    public class Calculator
    {

        public Calculator()
        {
            StreamWriter logFile = File.CreateText("calculator.log");
            Trace.Listeners.Add(new TextWriterTraceListener(logFile));
            Trace.AutoFlush = true;
            Trace.WriteLine("Starting Calculator Log");
            Trace.WriteLine(String.Format("Started {0}", System.DateTime.Now.ToString()));
        }

        public double DoOperation(double num1, double num2, string op)
        {
            double result = double.NaN; // Default value is "not-a-number" which we use if an operation, such as division, could result in an error.

            // Use a switch statement to do the math.
            switch (op)
            {
                case "a":
                    result = num1 + num2;
                    Trace.WriteLine(String.Format("{0} + {1} = {2}", num1, num2, result));
                    break;
                case "s":
                    result = num1 - num2;
                    Trace.WriteLine(String.Format("{0} - {1} = {2}", num1, num2, result));
                    break;
                case "m":
                    result = num1 * num2;
                    Trace.WriteLine(String.Format("{0} * {1} = {2}", num1, num2, result));
                    break;
                case "d":
                    // Ask the user to enter a non-zero divisor.
                    if (num2 != 0)
                    {
                        result = num1 / num2;
                        Trace.WriteLine(String.Format("{0} / {1} = {2}", num1, num2, result));
                    }
                    break;
                // Return text for an incorrect option entry.
                default:
                    break;
            }
            return result;
        }
    }
}
```

Soubor *Program.cs* by měl vypadat takto:

```csharp
using System;
using CalculatorLibrary;

namespace CalculatorProgram
{
   
    class Program
    {
        static void Main(string[] args)
        {
            bool endApp = false;
            // Display title as the C# console calculator app.
            Console.WriteLine("Console Calculator in C#\r");
            Console.WriteLine("------------------------\n");

            Calculator calculator = new Calculator();
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
                    result = calculator.DoOperation(cleanNum1, cleanNum2, op); 
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

## <a name="add-a-nuget-package-write-to-a-json-file"></a>Přidání balíčku NuGet: zápis do souboru JSON

1. Teď předpokládejme, že chceme výstup operací ve formátu JSON, oblíbeném a přenosném formátu pro ukládání dat objektů. K implementaci této funkce budeme muset odkazovat na balíček NuGet, Newtonsoft.Json. Balíčky NuGet jsou primárním vozidla pro distribuci knihoven tříd .NET. V **Průzkumník řešení** klikněte pravým tlačítkem na **uzel** Závislosti pro projekt CalculatorLibrary a zvolte **Spravovat balíčky NuGet.**

   ![Snímek obrazovky se spravou balíčků NuGet v místní nabídce](media/vs-2019/calculator2-manage-nuget-packages-dark2.png)

   Otevře se Správce balíčků NuGet.

   ![Snímek obrazovky s Správce balíčků](media/vs-2019/calculator2-nuget-package-manager-dark.png)

1. Vyhledejte Newtonsoft.Jsbalíčku a zvolte **Nainstalovat.**

   ![Snímek obrazovky s informacemi o balíčku Installersoft NuGet](media/vs-2019/calculator2-nuget-newtonsoft-json-dark2.png)

   Balíček se stáhne a přidá se do projektu a v uzlu Odkazy v souboru se zobrazí **Průzkumník řešení**.

1. Přidejte direktivu using pro System.IO a Newtonsoft.Jsna začátek souboru *CalculatorLibrary.cs*.

   ```csharp
   using Newtonsoft.Json;
   ```

1. Teď nahraďte konstruktor pro Calculator následujícím kódem a vytvořte objekt člena JsonWriter:

   ```csharp
        JsonWriter writer;

        public Calculator()
        {
            StreamWriter logFile = File.CreateText("calculatorlog.json");
            logFile.AutoFlush = true;
            writer = new JsonTextWriter(logFile);
            writer.Formatting = Formatting.Indented;
            writer.WriteStartObject();
            writer.WritePropertyName("Operations");
            writer.WriteStartArray();
        }
   ```

1. Upravte `DoOperation` metodu a přidejte kód JSON pro zápis:

   ```csharp
        public double DoOperation(double num1, double num2, string op)
        {
            double result = double.NaN; // Default value is "not-a-number" which we use if an operation, such as division, could result in an error.
            writer.WriteStartObject();
            writer.WritePropertyName("Operand1");
            writer.WriteValue(num1);
            writer.WritePropertyName("Operand2");
            writer.WriteValue(num2);
            writer.WritePropertyName("Operation");
            // Use a switch statement to do the math.
            switch (op)
            {
                case "a":
                    result = num1 + num2;
                    writer.WriteValue("Add");
                    break;
                case "s":
                    result = num1 - num2;
                    writer.WriteValue("Subtract");
                    break;
                case "m":
                    result = num1 * num2;
                    writer.WriteValue("Multiply");
                    break;
                case "d":
                    // Ask the user to enter a non-zero divisor.
                    if (num2 != 0)
                    {
                        result = num1 / num2;
                        writer.WriteValue("Divide");
                    }
                    break;
                // Return text for an incorrect option entry.
                default:
                    break;
            }
            writer.WritePropertyName("Result");
            writer.WriteValue(result);
            writer.WriteEndObject();

            return result;
        }
   ```

1. Jakmile uživatel dokončí zadávání provozních dat, budete muset přidat metodu , která dokončí syntaxi JSON.

   ```csharp
    public void Finish()
    {
        writer.WriteEndArray();
        writer.WriteEndObject();
        writer.Close();
    }
   ```

1. V *souboru Program.cs* přidejte na konec volání Finish (Dokončit).

   ```csharp
            // And call to close the JSON writer before return
            calculator.Finish();
            return;
        }
   ```

1. Sestavte a spusťte aplikaci. Až budete hotovi se zadáváním několika operací, pomocí příkazu n aplikaci správně zavřete.  Teď otevřete soubor calculatorlog.jsa měli byste vidět něco podobného:

   ```json
   {
    "Operations": [
        {
        "Operand1": 2.0,
        "Operand2": 3.0,
        "Operation": "Add",
        "Result": 5.0
        },
        {
        "Operand1": 3.0,
        "Operand2": 4.0,
        "Operation": "Multiply",
        "Result": 12.0
        }
    ]
   }
   ```

## <a name="debug-set-and-hit-a-breakpoint"></a>Ladění: nastavení zarážky a přístup k zarážce

Ladicí Visual Studio je výkonný nástroj, který umožňuje krok za krokem spouštět kód a najít přesný bod, ve kterém jste udělali programovací chybu. Pak pochopíte, jaké opravy je potřeba provést v kódu. Visual Studio umožňuje provádět dočasné změny, abyste mohli program dále spustit.

1. V *souboru Program.cs* klikněte na okraj nalevo od následujícího kódu (nebo otevřete místní nabídku a zvolte **Breakpoint**  >  **Insert Breakpoint**(Vložit zarážku) nebo stiskněte klávesu **F9**):

   ```csharp
   result = calculator.DoOperation(cleanNum1, cleanNum2, op);
   ```

   Červený kruh, který se zobrazí, označuje zarážku. Zarážky můžete použít k pozastavení aplikace a kontrole kódu. Zarážku můžete nastavit na libovolném spustitelném řádku kódu.

   ![Snímek obrazovky s nastavením zarážky](media/vs-2019/calculator-2-debug-set-breakpoint.png)

1. Sestavte a spusťte aplikaci.

1. Ve spuštěné aplikaci zadejte pro výpočet některé hodnoty:

   - Jako první číslo zadejte **8** a zadejte ho.
   - Pro druhé číslo zadejte **0** a zadejte ho.
   - Pro operátor se bavte. zadejte **d** a zadejte ho.

   Aplikace pozastaví místo, kde jste vytvořili zarážku, což je označeno žlutým ukazatelem vlevo a zvýrazněný kód. Zvýrazněný kód se ještě nespouštěl.

   ![Snímek obrazovky s zarážkou](media/vs-2019/calculator-2-debug-hit-breakpoint.png)

   Teď, když je aplikace pozastavená, můžete zkontrolovat stav aplikace.

## <a name="debug-view-variables"></a>Ladění: zobrazení proměnných

1. Ve zvýrazněných kódech najeďte myší na proměnné, jako je a `cleanNum1` `op` . Zobrazí se aktuální hodnoty pro tyto proměnné ( a , v `8` `d` uvedeném pořadí), které se zobrazují v datových tipech.

   ![Snímek obrazovky se zobrazením popisu dat](media/vs-2019/calculator-2-debug-view-datatip.png)

   Při ladění je kontrola, jestli proměnné udržují hodnoty, které očekáváte, že jsou v nich hodnoty, často zásadní pro opravu problémů.

2. V dolním podokně se podívejte na okno **Místní** hodnoty. (Pokud je zavřená, zvolte **Ladit.**  >  **Windows**  >  **Místní** hodnoty, které ho otevřou.)

   V okně Místní hodnoty se zobrazí každá proměnná, která je aktuálně v oboru, spolu s její hodnotou a typem.

   ![Snímek obrazovky s oknem Místních hodnoty](media/vs-2019/calculator-2-debug-locals-window.png)

3. Podívejte se na **okno Automatické** funkce.

   Okno Automatické hodnoty se  podobá oknu Místní hodnoty, ale zobrazuje proměnné bezprostředně předcházející aktuálnímu řádku kódu, na kterém je aplikace pozastavená.

   V dalším kroku spustíte kód v ladicím programu po jednom příkazu, který se nazývá *krokování*.

## <a name="debug-step-through-code"></a>Ladění: krok přes kód

1. Stiskněte **klávesu F11** (nebo **Ladit**  >  **krok do**).

   Pomocí příkazu Step Into aplikace spustí aktuální příkaz a přejde k dalšímu spustitelnému příkazu (obvykle dalšímu řádku kódu). Žlutý ukazatel vlevo vždy označuje aktuální příkaz.

   ![Snímek obrazovky s příkazem step into](media/vs-2019/calculator-2-debug-step-into.png)

   Právě jste do metody ve `DoOperation` třídě zašla. `Calculator`

1. Pokud chcete získat hierarchický pohled na tok programu, podívejte se do **okna Zásobník** volání. (Pokud je zavřená, zvolte **Ladit.**  >  **Windows**  >  **Zásobník volání**.)

   ![Snímek obrazovky se zásobníkem volání](media/vs-2019/calculator-2-debug-call-stack.png)

   Toto zobrazení ukazuje aktuální metodu označenou žlutým ukazatelem a druhý řádek ukazuje funkci, která ji volala, z metody `Calculator.DoOperation` `Main` v souboru *Program.cs*. V **okně Zásobník** volání se zobrazuje pořadí, ve kterém se volají metody a funkce. Kromě toho poskytuje přístup k mnoha funkcím ladicího programu, jako je **například Přejít na zdrojový** kód , z místní nabídky.

1. Několikrát **stiskněte klávesu F10** (nebo **Ladit** krok přes ), dokud  >  se aplikace na příkazu nepozastaví. `switch`

   ```csharp
   switch (op)
   {
   ```

   Příkaz Step Over se podobá příkazu Step Into s tím rozdílem, že pokud aktuální příkaz volá funkci, ladicí program spustí kód ve vvané funkci a nepozastaví provádění, dokud se funkce nevrátí. Krok přes je rychlejší způsob, jak procházet kód, pokud vás konkrétní funkce nezajímá.

1. Ještě **jednou stiskněte klávesu F10,** aby se aplikace pozastavila na následujícím řádku kódu.

   ```csharp
   if (num2 != 0)
   {
   ```

   Tento kód vyhledá případ dělení nulou. Pokud aplikace pokračuje, vyvolá obecnou výjimku (chybu), ale řekněme, že to považujete za chybu a chcete udělat něco jiného, například zobrazit skutečnou vrácenou hodnotu v konzole. Jednou z možností je použít funkci ladicího programu Edit-and-continue k provedení změn kódu a pak pokračovat v ladění. Ukážeme vám ale jiný trik pro dočasné úpravy toku provádění.

## <a name="debug-test-a-temporary-change"></a>Ladění: otestování dočasné změny

1. Vyberte žlutý ukazatel, který je aktuálně pozastavený u `if (num2 != 0)` příkazu , a přetáhněte ho na následující příkaz.

   ```csharp
   result = num1 / num2;
   ```

   Aplikace tak příkaz úplně přeskočí, takže uvidíte, co se stane, když vydělíte `if` nulou.

1. Stisknutím **klávesy F10** spusťte řádek kódu.

1. Najeďte `result` myší na proměnnou a zobrazí se v ní uložená hodnota `Infinity` .

   V jazyce C# `Infinity` je výsledkem dělení nulou.

1. Stiskněte **klávesu F5** (nebo **ladění pokračovat** v  >  **ladění).**

   Symbol nekonečna se zobrazí v konzole jako výsledek matematické operace.

1. Pomocí příkazu "n" aplikaci správně zavřete.

## <a name="code-complete"></a>Dokončení kódu

Tady je úplný kód souboru *CalculatorLibrary.cs* po dokončení všech kroků:

```csharp
using System;
using System.IO;
using System.Diagnostics;
using Newtonsoft.Json;

namespace CalculatorLibrary
{
    public class Calculator
    {

        JsonWriter writer;

        public Calculator()
        {
            StreamWriter logFile = File.CreateText("calculatorlog.json");
            logFile.AutoFlush = true;
            writer = new JsonTextWriter(logFile);
            writer.Formatting = Formatting.Indented;
            writer.WriteStartObject();
            writer.WritePropertyName("Operations");
            writer.WriteStartArray();
        }

        public double DoOperation(double num1, double num2, string op)
        {
            double result = double.NaN; // Default value is "not-a-number" which we use if an operation, such as division, could result in an error.
            writer.WriteStartObject();
            writer.WritePropertyName("Operand1");
            writer.WriteValue(num1);
            writer.WritePropertyName("Operand2");
            writer.WriteValue(num2);
            writer.WritePropertyName("Operation");
            // Use a switch statement to do the math.
            switch (op)
            {
                case "a":
                    result = num1 + num2;
                    writer.WriteValue("Add");
                    break;
                case "s":
                    result = num1 - num2;
                    writer.WriteValue("Subtract");
                    break;
                case "m":
                    result = num1 * num2;
                    writer.WriteValue("Multiply");
                    break;
                case "d":
                    // Ask the user to enter a non-zero divisor.
                    if (num2 != 0)
                    {
                        result = num1 / num2;
                        writer.WriteValue("Divide");
                    }
                    break;
                // Return text for an incorrect option entry.
                default:
                    break;
            }
            writer.WritePropertyName("Result");
            writer.WriteValue(result);
            writer.WriteEndObject();

            return result;
        }

        public void Finish()
        {
            writer.WriteEndArray();
            writer.WriteEndObject();
            writer.Close();
        }
    }
}
```

A tady je kód pro *Program.cs:* 

```csharp
using System;
using CalculatorLibrary;

namespace CalculatorProgram
{
   
    class Program
    {
        static void Main(string[] args)
        {
            bool endApp = false;
            // Display title as the C# console calculator app.
            Console.WriteLine("Console Calculator in C#\r");
            Console.WriteLine("------------------------\n");

            Calculator calculator = new Calculator();
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
                    result = calculator.DoOperation(cleanNum1, cleanNum2, op); 
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
            calculator.Finish();
            return;
        }
    }
}
```

## <a name="next-steps"></a>Další kroky

Blahopřejeme k dokončení tohoto kurzu! Další informace najdete v následujících kurzech.

> [!div class="nextstepaction"]
> [Pokračujte v dalších kurzech pro jazyk C#.](/dotnet/csharp/tutorials/)

> [!div class="nextstepaction"]
> [Pokračování s přehledem Visual Studio IDE](/../visual-studio-ide.md)

## <a name="see-also"></a>Viz také

- [C# IntelliSense](../../ide/visual-csharp-intellisense.md)
- [Naučte se ladit kód C# v Visual Studio](tutorial-debugger.md)
