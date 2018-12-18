---
title: 'Kurz: Ladění C# a kód jazyka C++ (ve smíšeném režimu)'
description: Zjistěte, jak ladit nativní knihovnu DLL z aplikace .NET Core nebo .NET Framework pro ladění ve smíšeném režimu
ms.custom: seodec18
ms.date: 11/02/2018
ms.technology: vs-ide-debug
ms.topic: tutorial
dev_langs:
- CSharp
- C++
helpviewer_keywords:
- mixed mode debugging
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
- cplusplus
ms.openlocfilehash: 690d607bb62b322cf7fa07e5c45aa59924d29c71
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53051445"
---
# <a name="tutorial-debug-c-and-c-in-the-same-debugging-session"></a>Kurz: Ladění C# a C++ ve stejné relaci ladění

Visual Studio vám umožňuje povolit více než jeden typ ladicího programu v relaci ladění, která se nazývá ladění ve smíšeném režimu. V tomto kurzu zjistíte, jak ladění spravovaného a nativního kódu v jedné relaci ladění. 

Tento kurz ukazuje postupy při ladění nativního kódu ze spravovaných aplikací, ale můžete také [ladění spravovaného kódu z nativní aplikace](../debugger/how-to-debug-in-mixed-mode.md). Ladicí program podporuje také jiné typy ve smíšeném režimu ladění, jako je ladění [Python a nativní kód](../python/debugging-mixed-mode-c-cpp-python-in-visual-studio.md)a pomocí ladicího programu skriptu v typech aplikací, jako je například technologie ASP.NET.

V tomto kurzu se naučíte:

> [!div class="checklist"]
> * Vytvoření jednoduché nativní knihovny DLL
> * Vytvořte jednoduchou aplikaci .NET Core nebo .NET Framework pro volání knihovny DLL
> * Konfigurovat ladění ve smíšeném režimu
> * Spuštění ladicího programu
> * Na zarážku ve spravované aplikaci
> * Krok do nativního kódu

## <a name="prerequisites"></a>Požadavky

Musíte mít Visual Studio nainstalovaný, s následujícími sadami funkcí:
- **Vývoj desktopových aplikací pomocí C++**
- Buď **vývoj desktopových aplikací .NET** nebo **.NET Core pro vývoj napříč platformami**, v závislosti na typu aplikace, který chcete vytvořit.

Pokud nemáte Visual Studio, přejděte [soubory ke stažení Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) stránku a nainstalovat zdarma.

Pokud máte nainstalovanou sadu Visual Studio, ale nemáte úlohy, které potřebujete, vyberte **otevřít instalační program Visual Studio** v levém podokně sady Visual Studio **nový projekt** dialogové okno. Ve Visual Studio Installerem. Vyberte úlohy, které potřebujete a pak vyberte **změnit**.

## <a name="create-a-simple-native-dll"></a>Vytvoření jednoduché nativní knihovny DLL

**Chcete-li vytvořit soubory pro projekt knihovny DLL:**

1. V sadě Visual Studio, vyberte **souboru** > **nový** > **projektu**.

1. V **nový projekt** dialogovém okně **Visual C++** vyberte **jiných**a pak vyberte **prázdný projekt** v prostředním podokně.

1. V **název** zadejte **Mixed_Mode_Debugging**a pak vyberte **OK**.

   Visual Studio vytvoří prázdný projekt a zobrazí ho v **Průzkumníka řešení**.

1. V **Průzkumníka řešení**vyberte **zdrojové soubory**a pak vyberte **projektu** > **přidat novou položku**. Nebo klikněte pravým tlačítkem na **zdrojové soubory** a vyberte **přidat** > **nová položka**. 

1. V **nová položka** dialogového okna, vyberte **soubor C++ (.cpp)**. Typ **Mixed_Mode.cpp** v **název** pole a pak vyberte **přidat**.

    Visual Studio přidá nový soubor C++ **Průzkumníka řešení**.

1. Zkopírujte následující kód do *Mixed_Mode.cpp*:

    ```cpp
    #include "Mixed_Mode.h"
    ```
1. V **Průzkumníka řešení**vyberte **hlavičkové soubory**a pak vyberte **projektu** > **přidat novou položku**. Nebo klikněte pravým tlačítkem na **hlavičkové soubory** a vyberte **přidat** > **nová položka**. 

1. V **nová položka** dialogového okna, vyberte **soubor hlaviček (.h)**. Typ **Mixed_Mode.h** v **název** pole a pak vyberte **přidat**.

   Visual Studio přidá nový soubor záhlaví **Průzkumníka řešení**.

1. Zkopírujte následující kód do *Mixed_Mode.h*:

    ```cpp
    #ifndef MIXED_MODE_MULTIPLY_HPP
    #define MIXED_MODE_MULTIPLY_HPP

    extern "C"
    {
        __declspec(dllexport) int __stdcall mixed_mode_multiply(int a, int b) {
            return a * b;
        }
    }
    #endif
    ```

1. Vyberte **souboru** > **Uložit vše** nebo stiskněte klávesu **Ctrl**+**Shift**+**S**  k uložení souborů.

**Ke konfiguraci a sestavte projekt knihovny DLL:**

1. Na panelu nástrojů sady Visual Studio vyberte **ladění** konfigurace a **x86** nebo **x64** platformy. Pokud bude váš volání aplikace .NET Core, který se vždy spouští v 64bitovém režimu, vyberte **x64** jako platformu.

1. V **Průzkumníka řešení**, vyberte **Mixed_Mode_Debugging** uzel projektu a vyberte **vlastnosti** ikonu, nebo klikněte pravým tlačítkem na uzel projektu a vyberte **Vlastnosti**.

1. V horní části **vlastnosti** podokno, ujistěte se, že **konfigurace** je nastavena na **Active(Debug)** a **platformy** je stejný jako co nastavit na panelu nástrojů: **x64**, nebo **Win32** pro x86 platformy. 

   > [!IMPORTANT]
   > Pokud přejdete z platformy **x86** k **x64** nebo naopak, je nutné znovu nakonfigurovat vlastnosti pro nové platformy. 

1. V části **vlastnosti konfigurace** v levém podokně vyberte **Linkeru** > **Upřesnit**a v rozevíracím seznamu vedle **bez vstupního bodu**vyberte **ne**. Pokud jste museli změňte ji na **ne**vyberte **použít**.

1. V části **vlastnosti konfigurace**vyberte **Obecné**a v rozevíracím seznamu vedle **typ konfigurace**vyberte **dynamická knihovna (.dll)**. Vyberte **použít**a pak vyberte **OK**.

   ![Přepnout na nativní knihovnu DLL](../debugger/media/mixed-mode-set-as-native-dll.png)

1. Vyberte projekt v **Průzkumníka řešení** a pak vyberte **sestavení** > **sestavit řešení**, stiskněte klávesu **F7**, nebo klikněte pravým tlačítkem na projekt a vyberte **sestavení**.

   Projekt by se měl sestavit bez chyb.

## <a name="create-a-simple-managed-app-to-call-the-dll"></a>Vytvoření jednoduché spravované aplikace pro volání knihovny DLL

1. V sadě Visual Studio, zvolte **souboru** > **nový** > **projektu**.

   > [!NOTE]
   > I když spravované nového projektu můžete také přidat do existujícího řešení C++, vytvoření nového řešení podporuje další scénáře ladění.

1. V **nový projekt** dialogu **Visual C#** a v prostředním podokně:

   - Aplikace rozhraní .NET Framework, vyberte **Konzolová aplikace (.NET Framework)**.
   
   - Pro aplikace .NET Core, vyberte **Konzolová aplikace (.NET Core)**.

1. V **název** zadejte **Mixed_Mode_Calling_App**a pak vyberte **OK**.

   Visual Studio vytvoří prázdný projekt a zobrazí ho v **Průzkumníka řešení**.

1. Nahraďte kód v *Program.cs* následujícím kódem:

    ```csharp
    using System;
    using System.Runtime.InteropServices;

    namespace Mixed_Mode_Calling_App
    {
        public class Program
        {
            // Replace the file path shown here with the
            // file path on your computer. For .NET Core, the typical (default) path
            // for a 64-bit DLL might look like this:
            // C:\Users\username\source\repos\Mixed_Mode_Debugging\x64\Debug\Mixed_Mode_Debugging.dll
            // Here, we show a typical path for a DLL targeting the **x86** option.
            [DllImport(@"C:\Users\username\source\repos\Mixed_Mode_Debugging\Debug\Mixed_Mode_Debugging.dll", EntryPoint =
            "mixed_mode_multiply", CallingConvention = CallingConvention.StdCall)]
            public static extern int Multiply(int x, int y);
            public static void Main(string[] args)
            {
                int result = Multiply(7, 7);
                Console.WriteLine("The answer is {0}", result);
                Console.ReadKey();
            }
        }
    }
    ```

1. V novém kódu nahraďte cesta k souboru v `[DllImport]` se cesta k souboru *Mixed_Mode_Debugging.dll* jste právě vytvořili. Podívejte se komentář ke kódu pro pomocné parametry. Nezapomeňte nahradit *uživatelské jméno* zástupný symbol.

1. Vyberte **souboru** > **uložit Program.cs** nebo stiskněte klávesu **Ctrl**+**S** k uložení souboru.

## <a name="configure-mixed-mode-debugging"></a>Konfigurovat ladění ve smíšeném režimu 

### <a name="to-configure-mixed-mode-debugging-for-a-net-framework-app"></a>Konfigurovat ladění ve smíšeném režimu pro aplikace rozhraní .NET Framework 

1. V **Průzkumníka řešení**, vyberte **Mixed_Mode_Calling_App** uzel projektu a vyberte **vlastnosti** ikonu, nebo klikněte pravým tlačítkem na uzel projektu a vyberte **Vlastnosti**.

1. Vyberte **ladění** v levém podokně, vyberte **povolit ladění nativního kódu** zaškrtněte políčko a pak zavřete stránku vlastností a uložte změny.

    ![Povolit ladění ve smíšeném režimu](../debugger/media/mixed-mode-enable-native-code-debugging.png)

### <a name="to-configure-mixed-mode-debugging-for-a-net-core-app"></a>Konfigurovat ladění ve smíšeném režimu pro aplikace .NET Core 

Ve většině verzí sady Visual Studio 2017, je nutné použít *launchSettings.json* souboru místo vlastnosti projektu pro povolení ladění ve smíšeném režimu pro nativní kód v aplikaci .NET Core. Pokud chcete sledovat aktualizace uživatelského rozhraní pro tuto funkci, najdete v tomto [problém Githubu](https://github.com/dotnet/project-system/issues/1125).

1. V **Průzkumníka řešení**, rozbalte **vlastnosti**a otevřete *launchSettings.json* souboru. 

   >[!NOTE]
   >Ve výchozím nastavení *launchSettings.json* probíhá *C:\Users\username\source\repos\Mixed_Mode_Calling_App\Properties*. Pokud *launchSettings.json* neexistuje, vyberte **Mixed_Mode_Calling_App** projekt **Průzkumníka řešení** a pak vyberte **vlastnosti** ikonu, nebo klikněte pravým tlačítkem na projekt a vyberte **vlastnosti**. Změňte dočasné v **ladění** kartu a sestavte projekt. Tím se vytvoří *launchSettings.json* souboru. Vrátit zpět změny, které jste provedli v **ladění** kartu.

1. V *lauchsettings.json* přidejte následující řádek:

    ```csharp
    "nativeDebugging": true
    ```

    Úplný soubor bude vypadat jako v následujícím příkladu:

    ```csharp
    {
      "profiles": {
        "Mixed_Mode_Calling_App": {
          "commandName": "Project",
          "nativeDebugging": true
        }
      }
    }
    ```

## <a name="set-a-breakpoint-and-start-debugging"></a>Nastavte zarážku a spustit ladění

1. V C# projekt, otevřete *Program.cs*. Nastavit zarážku na řádek kódu kliknutím v levém okraji, výběrem řádku a stisknutím klávesy **F9**, nebo kliknete pravým tlačítkem na řádku a vyberete **zarážku**  >  **Vložit zarážku**.

    ```csharp
    int result = Multiply(7, 7);
    ```

    Do levého okraje, kde nastavit zarážky se zobrazí červený kruh.

1. Stisknutím klávesy **F5**vyberte zelenou šipku na panelu nástrojů sady Visual Studio, nebo vyberte **ladění** > **spustit ladění** pro spuštění ladění.

   Ladicí program pozastavení na zarážce, kterou jste nastavili. Žlutá šipka označuje, kde je nyní pozastavena ladicím programu.

## <a name="step-in-and-out-of-native-code"></a>Krok dovnitř a ven z nativního kódu

1. Při ladění je pozastavený ve spravované aplikaci, stiskněte klávesu **F11**, nebo vyberte **ladění** > **Krokovat s vnořením**.

   *Mixed_Mode.h* nativní hlavičkový soubor se otevře a zobrazí žlutá šipka, kde je pozastavena ladicím programu.

   ![Krok do nativního kódu](../debugger/media/mixed-mode-step-into-native-code.png)

1. Teď můžete nastavit a dosažení zarážky a zkontrolovat proměnné v nativním nebo spravovaným kódem.

   - Najeďte myší proměnné ve zdrojovém kódu zobrazíte jejich hodnoty.

   - Podívejte se na proměnné a jejich hodnoty v **automatické hodnoty** a **lokální** systému windows.

   - Během pozastavení v ladicím programu, můžete použít také **Watch** windows a **zásobník volání** okna.

1. Stisknutím klávesy **F11** znovu, aby ladicí program jeden řádek záloh.

1. Stisknutím klávesy **Shift**+**F11** nebo vyberte **ladění** > **Krokovat s Vystoupením** znovu v pozastavit a pokračovat v provádění spravované aplikace.

1. Stisknutím klávesy **F5** nebo vyberte zelenou šipku pro pokračování v ladění aplikace.

Blahopřejeme! Dokončili jste kurz ladění ve smíšeném režimu.

## <a name="next-step"></a>Další krok

V tomto kurzu jste zjistili, jak k ladění nativního kódu ze spravovaných aplikací tím, že ladění ve smíšeném režimu. Přehled dalších funkcí ladicího programu naleznete v tématu:

> [!div class="nextstepaction"]
> [První seznámení s ladicím programem](../debugger/debugger-feature-tour.md)
