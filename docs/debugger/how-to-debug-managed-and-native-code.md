---
title: 'Kurz: Ladění kódu Jazyka C# a Jazyka C++ (smíšený režim)'
description: Zjistěte, jak ladit nativní dll z aplikace .NET Core nebo .NET Framework pomocí ladění ve smíšeném režimu
ms.custom: seodec18
ms.date: 11/02/2018
ms.topic: tutorial
dev_langs:
- CSharp
- C++
helpviewer_keywords:
- mixed mode debugging
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
- cplusplus
ms.openlocfilehash: 06f68962eb7cdb6e4fc0290ee5c6559721afb52b
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "77416357"
---
# <a name="tutorial-debug-c-and-c-in-the-same-debugging-session"></a>Kurz: Ladění C# a C++ ve stejné relaci ladění

Visual Studio umožňuje povolit více než jeden typ ladicího programu v relaci ladění, která se nazývá ladění v smíšeném režimu. V tomto kurzu se naučíte ladit spravovaný i nativní kód v jedné relaci ladění.

Tento kurz ukazuje, jak ladit nativní kód ze spravované aplikace, ale můžete také [ladit spravovaný kód z nativní aplikace](../debugger/how-to-debug-in-mixed-mode.md). Ladicí program také podporuje jiné typy ladění ve smíšeném režimu, jako je ladění [Pythonu a nativního kódu](../python/debugging-mixed-mode-c-cpp-python-in-visual-studio.md)a použití ladicího programu skriptu v typech aplikací, jako je ASP.NET.

V tomto kurzu provedete následující:

> [!div class="checklist"]
> * Vytvoření jednoduché nativní dll.
> * Vytvoření jednoduché aplikace .NET Core nebo .NET Framework pro volání dll.
> * Konfigurace ladění ve smíšeném režimu
> * Spuštění ladicího programu
> * Přístup k zarážky ve spravované aplikaci
> * Krok do nativního kódu

## <a name="prerequisites"></a>Požadavky

Musíte mít nainstalovanou Visual Studio s následujícími úlohami:
- **Vývoj plochy s C++**
- Vývoj **plochy .NET** nebo **vývoj napříč platformami .NET Core**v závislosti na typu aplikace, kterou chcete vytvořit.

Pokud visual studio nemáte, přejděte na stránku ke stažení sady Visual [Studio](https://visualstudio.microsoft.com/downloads/)a nainstalujte ho zdarma.

Pokud máte nainstalovaný Visual Studio, ale nemáte potřebné úlohy, vyberte **otevřít instalační program sady Visual Studio** v levém podokně dialogového okna Nový **projekt** sady Visual Studio. V Instalační službě sady Visual Studio vyberte potřebné úlohy a pak vyberte **Změnit**.

## <a name="create-a-simple-native-dll"></a>Vytvoření jednoduché nativní dll.

**Vytvoření souborů pro projekt DLL:**

1. Otevřete Visual Studio a vytvořte projekt.

    ::: moniker range=">=vs-2019"
    Stisknutím **klávesy Esc** zavřete počáteční okno. Zadáním **kombinace kláves Ctrl + Q** otevřete vyhledávací pole, zadejte Prázdný **projekt**, zvolte **Šablony**a pak zvolte **Prázdný projekt** pro C++. V zobrazeném dialogovém okně zvolte **Vytvořit**. Potom zadejte název, **jako je Mixed_Mode_Debugging,** a klepněte na **tlačítko Vytvořit**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    V horním řádku nabídek zvolte **Soubor** > **nového** > **projektu**. V levém podokně dialogového okna **Nový projekt** v části **Visual C++** zvolte **Jiné**a potom v prostředním podokně zvolte **Prázdný projekt**. Potom zadejte název, **například Mixed_Mode_Debugging** a klepněte na tlačítko **OK**.
    ::: moniker-end

    Pokud šablonu projektu **Prázdný projekt** nevidíte, přejděte na **nástrojové** > **nástroje a nástroje...**, která otevře Instalační program sady Visual Studio. Spustí se instalační program pro Visual Studio. Zvolte vývoj plochy s úlohami **C++** a pak zvolte **Změnit**.

    Visual Studio vytvoří projekt.

1. V **Průzkumníku řešení**vyberte **Zdrojové soubory**a pak vyberte Přidat novou**položku** **projektu** > . Nebo klepněte pravým tlačítkem myši na **položku Zdrojové soubory** a vyberte **přidat** > **novou položku**.

1. V dialogovém okně **Nová položka** vyberte **soubor C++ (.cpp)**. Do pole **Název** zadejte **Mixed_Mode.cpp** a pak vyberte **Přidat**.

    Visual Studio přidá nový soubor C++ do **Průzkumníka řešení**.

1. Zkopírujte následující kód do *Mixed_Mode.cpp*:

    ```cpp
    #include "Mixed_Mode.h"
    ```

1. V **Průzkumníku řešení**vyberte **Soubory záhlaví**a pak vyberte Přidat**novou položku** **projektu** > . Nebo klepněte pravým tlačítkem myši na **položku Soubory záhlaví** a vyberte **přidat** > **novou položku**.

1. V dialogovém okně **Nová položka** vyberte soubor **záhlaví (.h)**. Do pole **Název** zadejte **Mixed_Mode.h** a pak vyberte **Přidat**.

   Visual Studio přidá nový soubor záhlaví do **Průzkumníka řešení**.

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

1. Vyberte **Uložit** > **vše** nebo stisknutím **klávesy Ctrl**+**Shift**+**S** soubory uložte.

**Konfigurace a sestavení projektu DLL:**

1. Na panelu nástrojů Sady Visual Studio vyberte **konfigurace ladění** a platforma **x86** nebo **x64.** Pokud vaše volající aplikace bude .NET Core, který vždy běží v 64bitovém režimu, vyberte **x64** jako platformu.

1. V **Průzkumníku řešení**vyberte **uzel Mixed_Mode_Debugging** projektu a vyberte ikonu **Vlastnosti** nebo klepněte pravým tlačítkem myši na uzel projektu a vyberte **vlastnosti**.

1. V horní části **podokna Vlastnosti** zkontrolujte, zda je **konfigurace** nastavena na **Active(Debug)** a **platforma** je stejná jako to, co jste nastavili v panelu nástrojů: **x64**nebo **Win32** pro platformu x86.

   > [!IMPORTANT]
   > Pokud přepnete platformu z **x86** na **x64** nebo naopak, je nutné překonfigurovat vlastnosti pro novou platformu.

1. V části **Vlastnosti konfigurace** v levém podokně vyberte **Linker** > **Advanced**a v rozevíracím seznamu vedle **položky Žádný vstupní bod**vyberte **Ne**. Pokud jste ji museli změnit na **Ne**, vyberte **Použít**.

1. V části **Vlastnosti konfigurace**vyberte **Obecné**a v rozevíracím souboru vedle **položky Typ konfigurace**vyberte **Dynamická knihovna (.dll).** Vyberte **Apply** (Použít) a pak vyberte **OK**.

   ![Přepnutí na nativní dll.](../debugger/media/mixed-mode-set-as-native-dll.png)

1. Vprůzkumníka **řešení** vyberte projekt a pak vyberte **Build** > **Build Build Solution**, stiskněte **klávesu F7**nebo klikněte pravým tlačítkem myši na projekt a vyberte **Build**.

   Projekt by se měl sestavit bez chyb.

## <a name="create-a-simple-managed-app-to-call-the-dll"></a>Vytvoření jednoduché spravované aplikace pro volání dll.

1. Otevřete Visual Studio a vytvořte nový projekt.

    ::: moniker range=">=vs-2019"
    Stisknutím **klávesy Esc** zavřete počáteční okno. Zadejte **Ctrl + Q,** chcete-li otevřít vyhledávací pole, zadat **konzolu**, zvolit **šablony**a pak zvolte Console **App (.NET Core)** nebo **Console App (.NET Framework)** pro C#. V zobrazeném dialogovém okně zvolte **Vytvořit**.

    Potom zadejte název, **jako je Mixed_Mode_Calling_App,** a klepněte na **tlačítko Vytvořit**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    V horním řádku nabídek zvolte **Soubor** > **nového** > **projektu**. V levém podokně dialogového okna **Nový projekt** v části **Visual C#** zvolte **Plochu systému Windows**a potom v prostředním podokně zvolte Console App **(.NET Framework)** nebo **Console App (.NET Core)**.

    Potom zadejte název, **jako je Mixed_Mode_Calling_App,** a klepněte na tlačítko **OK**.
    ::: moniker-end

    Pokud šablonu projektu **konzolové aplikace** nevidíte, přejděte na **nástrojové** > **nástroje a nástroje...**, který otevře Instalační službu sady Visual Studio. Zvolte **úlohu vývoje plochy .NET** a pak zvolte **Změnit**.

    > [!NOTE]
    > I když můžete také přidat nový spravovaný projekt do existujícího řešení C++, vytvoření nového řešení podporuje další scénáře ladění.

   Visual Studio vytvoří prázdný projekt a zobrazí jej v **Průzkumníku řešení**.

1. Nahraďte veškerý kód v *Program.cs* následujícím kódem:

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

1. V novém kódu nahraďte `[DllImport]` cestu k souboru cestou k *Mixed_Mode_Debugging.dll,* kterou jste právě vytvořili. Podívejte se na komentář kódu pro rady. Nezapomeňte nahradit zástupný symbol *uživatelského jména.*

1. Vyberte**Uložit Program.cs** **soubor** > nebo stisknutím **ctrl**+**s** souboru uložte.

## <a name="configure-mixed-mode-debugging"></a>Konfigurace ladění ve smíšeném režimu

### <a name="to-configure-mixed-mode-debugging-for-a-net-framework-app"></a>Konfigurace ladění v kombinovaném režimu pro aplikaci rozhraní .NET Framework

1. V **Průzkumníku řešení**vyberte **uzel projektu Mixed_Mode_Calling_App** a vyberte ikonu **Vlastnosti** nebo klepněte pravým tlačítkem myši na uzel projektu a vyberte **vlastnosti**.

1. V levém podokně vyberte **Ladění,** zaškrtněte políčko **Povolit ladění nativního kódu** a zavřete stránku vlastností, chcete-li změny uložit.

    ![Povolit ladění ve smíšeném režimu](../debugger/media/mixed-mode-enable-native-code-debugging.png)

### <a name="to-configure-mixed-mode-debugging-for-a-net-core-app"></a>Konfigurace ladění ve smíšeném režimu pro aplikaci .NET Core

Ve většině verzí sady Visual Studio začínajících v sadě Visual Studio 2017 je nutné použít soubor *launchSettings.json* namísto vlastností projektu, abyste povolili ladění pro nativní kód v aplikaci .NET Core ve smíšeném režimu. Chcete-li sledovat aktualizace rozhraní pro tuto funkci, podívejte se na tento [problém GitHub](https://github.com/dotnet/project-system/issues/1125).

1. V **Průzkumníku řešení**rozbalte **příkaz Vlastnosti**a otevřete soubor *launchSettings.json.*

   >[!NOTE]
   >Ve výchozím nastavení je *soubor launchSettings.json* v *souboru C:\Users\username\source\repos\Mixed_Mode_Calling_App\Properties*. Pokud *soubor launchSettings.json* neexistuje, vyberte **Mixed_Mode_Calling_App** projektu v **Průzkumníku řešení** a pak vyberte ikonu **Vlastnosti** nebo klepněte pravým tlačítkem myši na projekt a vyberte **příkaz Vlastnosti**. Proveďte dočasnou změnu na kartě **Ladění** a vytvořte projekt. Tím se vytvoří soubor *launchSettings.json.* Vrátit změnu, kterou jste provedli na kartě **Ladění.**

1. Do souboru *launchsettings.json* přidejte následující řádek:

    ```csharp
    "nativeDebugging": true
    ```

    Celý soubor bude vypadat jako následující příklad:

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

## <a name="set-a-breakpoint-and-start-debugging"></a>Nastavení zarážky a zahájení ladění

1. V projektu C# otevřete *Program.cs*. Nastavte zarážku na následujícím řádku kódu klepnutím na zcela levý okraj, výběrem řádku a stisknutím **klávesy F9**nebo klepnutím pravým tlačítkem myši na řádek a výběrem **zarážky** > **vložení zarážky**.

    ```csharp
    int result = Multiply(7, 7);
    ```

    Na levém okraji, kde nastavíte zarážku, se zobrazí červený kruh.

1. Stiskněte **klávesu F5**, vyberte zelenou šipku na panelu nástrojů sady Visual Studio nebo vyberte **možnost Ladění** > **začít ladění** a spusťte ladění.

   Ladicí program se pozastaví na zarážky, kterou nastavíte. Žlutá šipka označuje, kde je ladicí program aktuálně pozastaven.

## <a name="step-in-and-out-of-native-code"></a>Krok dovnitř a ven z nativního kódu

1. Při ladění je pozastaveno ve spravované aplikaci, stiskněte **klávesu F11**nebo vyberte **ladění** > **krok do**.

   Otevře se nativní soubor záhlaví *Mixed_Mode.h* a zobrazí se žlutá šipka, kde je ladicí program pozastaven.

   ![Krok do nativního kódu](../debugger/media/mixed-mode-step-into-native-code.png)

1. Nyní můžete nastavit a zasáhnout zarážky a zkontrolovat proměnné v nativním nebo spravovaném kódu.

   - Najeďte nad proměnnými ve zdrojovém kódu, abyste viděli jejich hodnoty.

   - Podívejte se na proměnné a jejich hodnoty v **autos** a **locals** okna.

   - Při pozastavení v ladicím programu můžete také použít okna **kukátka** a okno **Zásobník volání.**

1. Dalším stisknutím **klávesy F11** převezte ladicí program o jeden řádek.

1. Stisknutím **klávesy Shift**+**F11** nebo vyberte **možnost Ladění** > krok**ven** pokračovat v provádění a pozastavit znovu ve spravované aplikaci.

1. Stisknutím **klávesy F5** nebo vyberte zelenou šipku a pokračujte v ladění aplikace.

Blahopřejeme! Dokončili jste kurz ladění ve smíšeném režimu.

## <a name="next-step"></a>Další krok

V tomto kurzu jste se naučili ladit nativní kód ze spravované aplikace povolením ladění ve smíšeném režimu. Přehled dalších funkcí ladicího programu najdete v těchto tématech:

> [!div class="nextstepaction"]
> [První seznámení s ladicím programem](../debugger/debugger-feature-tour.md)
