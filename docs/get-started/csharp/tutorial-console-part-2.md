---
title: 'Kurz: roztažení jednoduché konzolové aplikace v jazyce C#'
description: Naučte se vyvíjet konzolovou aplikaci v jazyce C# v aplikaci Visual Studio, krok za krokem.
ms.custom: get-started
ms.date: 07/09/2020
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: tutorial
ms.devlang: CSharp
author: ghogen
ms.author: ghogen
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: fd0d2b3e112a4bf08481fa8f043f70121d827010
ms.sourcegitcommit: cea9e5787ff33e0e18aa1942bf4236748e0ef547
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2020
ms.locfileid: "92197475"
---
# <a name="tutorial-extend-a-simple-c-console-app"></a>Kurz: roztažení jednoduché konzolové aplikace v jazyce C#

V tomto kurzu se naučíte, jak pomocí sady Visual Studio zvětšit konzolovou aplikaci, kterou jste vytvořili v první části. Seznamte se s některými funkcemi v aplikaci Visual Studio, které budete potřebovat pro každodenní vývoj, jako je například Správa více projektů a odkazování na balíčky třetích stran.

Pokud jste právě dokončili [první část](tutorial-console.md) této série, už máte konzolovou aplikaci kalkulačky.  Pokud chcete přeskočit část 1, můžete začít otevřením projektu z úložiště GitHub. Aplikace kalkulačky pro C# je v [úložišti vs-tutorial-Samples](https://github.com/MicrosoftDocs/vs-tutorial-samples), takže můžete postupovat podle kroků v [kurzu: otevření projektu z úložiště](../tutorial-open-project-from-repo.md) a zahájení práce.

## <a name="add-a-new-project"></a>Přidat nový projekt

Real-World Code zahrnuje mnoho projektů pracujících společně v řešení. Teď přidáme do aplikace kalkulačky další projekt. To bude knihovna tříd, která poskytuje některé funkce kalkulačky.

1. V aplikaci Visual Studio můžete použít **soubor**příkazů nabídky nejvyšší úrovně  >  **Add**  >  **New Project** pro přidání nového projektu, ale můžete také kliknout pravým tlačítkem na název existujícího projektu (nazývaný "uzel projektu") a otevřít místní nabídku projektu (nebo místní nabídka). Tato místní nabídka obsahuje mnoho způsobů, jak přidat funkce do projektů. V **Průzkumník řešení**klikněte pravým tlačítkem myši na uzel projektu a vyberte možnost **Přidat**  >  **Nový projekt**.

1. Vyberte knihovnu tříd šablony projektu C# **(.NET Standard)**.

   ![Snímek obrazovky s výběrem šablony projektu knihovny tříd](media/vs-2019/calculator2-add-project-dark.png)

1. Zadejte název projektu **CalculatorLibrary**a klikněte na **vytvořit**. Visual Studio vytvoří nový projekt a přidá ho do řešení.

   ![Snímek obrazovky Průzkumník řešení s přidaným projektem knihovny tříd CalculatorLibrary](media/vs-2019/calculator2-solution-explorer-with-class-library-dark2.png)

1. Místo toho, abyste měli *Class1.cs*, přejmenujte soubor **CalculatorLibrary.cs**. Můžete kliknout na název v **Průzkumník řešení** pro přejmenování, nebo kliknout pravým tlačítkem myši a vybrat **Přejmenovat**nebo stisknout klávesu **F2** .

   Může se zobrazit výzva, pokud chcete přejmenovat všechny odkazy na `Class1` v souboru. Nezáleží na tom, jak jste odpověděli, protože v budoucím kroku nahradíte kód.

1. Nyní je nutné přidat odkaz na projekt, aby první projekt mohl používat rozhraní API vystavené novou knihovnou tříd.  V prvním projektu klikněte pravým tlačítkem myši na uzel **odkazy** a vyberte možnost **Přidat odkaz na projekt**.

   ![Snímek obrazovky s položkou nabídky Přidat odkaz na projekt](media/vs-2019/calculator2-add-project-reference-dark.png)

   Zobrazí se dialogové okno **Správce odkazů** . Toto dialogové okno umožňuje přidat odkazy na jiné projekty, stejně jako sestavení a knihovny DLL modelu COM, které vaše projekty potřebují.

   ![Snímek obrazovky s dialogovým oknem Správce odkazů](media/vs-2019/calculator2-ref-manager-dark.png)

1. V dialogovém okně **Správce odkazů** zaškrtněte políčko u projektu **CalculatorLibrary** a klikněte na **tlačítko OK**.  Odkaz na projekt se zobrazí v uzlu **projekty** v **Průzkumník řešení**.

   ![Snímek obrazovky s Průzkumník řešení s odkazem na projekt](media/vs-2019/calculator2-solution-explorer-with-project-reference-dark2.png)

1. V *program.cs*vyberte `Calculator` třídu a veškerý její kód a stisknutím **kombinace kláves CTRL + X** ji vyjměte z program.cs. Poté v **CalculatorLibrary**v *CalculatorLibrary.cs*vložte kód do `CalculatorLibrary` oboru názvů. Pak vytvořte třídu kalkulačky, `public` aby ji vystavila mimo knihovnu. Kód v *CalculatorLibrary.cs* by teď měl vypadat jako následující kód:

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

1. První projekt obsahuje odkaz, ale zobrazí se chyba, že volání kalkulačky. DoOperation nebude vyřešeno. To je způsobeno tím, že CalculatorLibrary je v oboru názvů rozdíl, proto přidejte `CalculatorLibrary` obor názvů pro plně kvalifikovaný odkaz.

   ```csharp
   result = CalculatorLibrary.Calculator.DoOperation(cleanNum1, cleanNum2, op);
   ```

   Zkuste místo toho přidat direktivu using na začátek souboru:

   ```csharp
   using CalculatorLibrary;
   ```

   Tato změna by měla umožnit odebrat obor názvů CalculatorLibrary z webu volání, ale nyní je nejednoznačnost. Je `Calculator` Třída v CalculatorLibrary nebo je Kalkulačka oboru názvů?  Chcete-li vyřešit nejednoznačnost, přejmenujte obor názvů `CalculatorProgram` .

   ```csharp
   namespace CalculatorProgram
   ```

## <a name="reference-net-libraries-write-to-a-log"></a>Odkazy na knihovny .NET: zápis do protokolu

1. Předpokládejme, že teď chcete přidat protokol všech operací a zapsat ho do textového souboru. `Trace`Tato funkce poskytuje třídu .NET. (Je užitečné také pro základní techniky tisku a ladění.)  Třída Trace je v System. Diagnostics a budeme potřebovat třídy System.IO `StreamWriter` , jako tak začít přidáním direktiv using:

   ```csharp
   using System.IO;
   using System.Diagnostics;
   ```

1. Prohlížíte-li se, jak je třída trasování používána, je nutné umístit na odkaz pro třídu, která je přidružena k FileStream. To znamená, že Kalkulačka bude lépe fungovat jako objekt, takže přidáváme konstruktor.

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

1. A musíme změnit statickou `DoOperation` metodu na členskou metodu.  Pojďme také do každého výpočtu protokolu přidat výstup, aby DoOperation vypadal jako následující kód:

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

1. Nyní je v Program.cs statické volání označeno červenou vlnovkou. Pokud ho chcete opravit, vytvořte `calculator` proměnnou přidáním následujícího řádku těsně před smyčkou while:

   ```csharp
   Calculator calculator = new Calculator();
   ```

   A upravte web volání `DoOperation` následujícím způsobem:

   ```csharp
   result = calculator.DoOperation(cleanNum1, cleanNum2, op);
   ```

1. Spusťte program znovu a po dokončení klikněte pravým tlačítkem myši na uzel projektu a zvolte možnost **Otevřít složku v Průzkumníku souborů**a pak přejděte dolů v Průzkumníkovi souborů do výstupní složky. Může to být *bin/Debug/netcoreapp 3.1*a otevře se soubor *kalkulačky. log* .

    ```output
    Starting Calculator Log
    Started 7/9/2020 1:58:19 PM
    1 + 2 = 3
    3 * 3 = 9
    ```

## <a name="add-a-nuget-package-write-to-a-json-file"></a>Přidat balíček NuGet: zapsat do souboru JSON

1. Nyní předpokládejme, že chceme výstupovat operace ve formátu JSON, což je oblíbený a přenosný formát pro ukládání dat objektů. Pro implementaci této funkce budeme muset odkazovat na balíček NuGet Newtonsoft.Jsna. Balíčky NuGet představují primární vozidlo pro distribuci knihoven tříd .NET. V **Průzkumník řešení**klikněte pravým tlačítkem myši na uzel **odkazy** pro projekt CalculatorLibrary a vyberte možnost **Spravovat balíčky NuGet**.

   ![Snímek obrazovky s možností spravovat balíčky NuGet v místní nabídce](media/vs-2019/calculator2-manage-nuget-packages-dark2.png)

   Otevře se správce balíčků NuGet.

   ![Snímek správce balíčků NuGet](media/vs-2019/calculator2-nuget-package-manager-dark.png)

1. Vyhledejte Newtonsoft.Jsna balíčku a vyberte **nainstalovat**.

   ![Snímek obrazovky s informacemi o balíčku NuGet Newtonsoft](media/vs-2019/calculator2-nuget-newtonsoft-json-dark2.png)

   Balíček je stažen a přidán do projektu a nová položka se zobrazí v uzlu odkazy v **Průzkumník řešení**.

1. Přidejte direktivu using pro System.IO a Newtonsoft.Jsna balíčku na začátku *CalculatorLibrary.cs*.

   ```csharp
   using Newtonsoft.Json;
   ```

1. Nyní nahraďte konstruktor pro kalkulačku následujícím kódem a vytvořte objekt členské JsonWriter:

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

1. Upravte `DoOperation` metodu pro přidání kódu zapisovače JSON:

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

1. Jakmile se uživatel stane vstupem do data operace, budete muset přidat metodu pro dokončení syntaxe JSON.

   ```csharp
    public void Finish()
    {
        writer.WriteEndArray();
        writer.WriteEndObject();
        writer.Close();
    }
   ```

1. A v *program.cs*přidejte volání pro dokončení na konci.

   ```csharp
            // And call to close the JSON writer before return
            calculator.Finish();
            return;
        }
   ```

1. Sestavte a spusťte aplikaci a po dokončení zadávání několika operací aplikaci zavřete správně pomocí příkazu n.  Nyní otevřete calculatorlog.jsv souboru a měli byste vidět podobný následujícímu:

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

## <a name="next-steps"></a>Další kroky

Blahopřejeme k dokončení tohoto kurzu! Pokud se chcete dozvědět ještě víc, pokračujte v následujících kurzech.

> [!div class="nextstepaction"]
> [Pokračovat s dalšími kurzy C#](/dotnet/csharp/tutorials/)

> [!div class="nextstepaction"]
> [Pokračovat s přehledem integrovaného vývojového prostředí sady Visual Studio](/../visual-studio-ide.md)

## <a name="see-also"></a>Viz také

* [C# IntelliSense](../../ide/visual-csharp-intellisense.md)
* [Naučte se ladit kód C# v aplikaci Visual Studio.](tutorial-debugger.md)
