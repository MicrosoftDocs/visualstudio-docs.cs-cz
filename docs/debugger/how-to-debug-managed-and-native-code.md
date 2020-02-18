---
title: 'Kurz: Ladění C# a kód jazyka C++ (ve smíšeném režimu)'
description: Zjistěte, jak ladit nativní knihovnu DLL z aplikace .NET Core nebo .NET Framework pro ladění ve smíšeném režimu
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
ms.sourcegitcommit: 6ef52c2030b37ea7a64fddb32f050ecfb77dd918
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/17/2020
ms.locfileid: "77416357"
---
# <a name="tutorial-debug-c-and-c-in-the-same-debugging-session"></a>Kurz: Ladění C# a C++ ve stejné relaci ladění

Visual Studio vám umožňuje povolit více než jeden typ ladicího programu v relaci ladění, která se nazývá ladění ve smíšeném režimu. V tomto kurzu zjistíte, jak ladění spravovaného a nativního kódu v jedné relaci ladění.

V tomto kurzu se dozvíte, jak ladit nativní kód ze spravované aplikace, ale můžete také [ladit spravovaný kód z nativní aplikace](../debugger/how-to-debug-in-mixed-mode.md). Ladicí program také podporuje jiné typy ladění v kombinovaném režimu, jako je ladění [Pythonu a nativního kódu](../python/debugging-mixed-mode-c-cpp-python-in-visual-studio.md), a použití ladicího programu skriptu v typech aplikací, jako je ASP.NET.

V tomto kurzu provedete následující:

> [!div class="checklist"]
> * Vytvoření jednoduché nativní knihovny DLL
> * Vytvořte jednoduchou aplikaci .NET Core nebo .NET Framework pro volání knihovny DLL
> * Konfigurovat ladění ve smíšeném režimu
> * Spuštění ladicího programu
> * Na zarážku ve spravované aplikaci
> * Krok do nativního kódu

## <a name="prerequisites"></a>Předpoklady

Musíte mít Visual Studio nainstalovaný, s následujícími sadami funkcí:
- **Vývoj desktopových aplikací pomocíC++**
- Vývoj **desktopových aplikací .NET** nebo **vývoj pro různé platformy .NET Core**v závislosti na typu aplikace, kterou chcete vytvořit.

Pokud nemáte Visual Studio, navštivte stránku pro stažení sady [Visual studio](https://visualstudio.microsoft.com/downloads/) a nainstalujte ji zdarma.

Pokud máte nainstalovanou sadu Visual Studio, ale nemáte potřebné úlohy, vyberte **otevřít instalační program pro Visual Studio** v levém podokně dialogového okna **Nový projekt** aplikace Visual Studio. V Instalační program pro Visual Studio vyberte úlohy, které potřebujete, a pak vyberte **Upravit**.

## <a name="create-a-simple-native-dll"></a>Vytvoření jednoduché nativní knihovny DLL

**Chcete-li vytvořit soubory pro projekt knihovny DLL:**

1. Otevřete Visual Studio a vytvořte projekt.

    ::: moniker range=">=vs-2019"
    Stisknutím klávesy **ESC** zavřete okno Start. Zadáním **CTRL + Q** otevřete vyhledávací pole, zadejte **prázdný projekt**, zvolte **šablony**a pak zvolte **prázdný projekt** pro C++. V dialogovém okně, které se zobrazí, vyberte **vytvořit**. Pak zadejte název podobný **Mixed_Mode_Debugging** a klikněte na **vytvořit**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    V horním řádku nabídek zvolte **Soubor** > **Nový** > **Projekt**. V levém podokně dialogového okna **Nový projekt** , v části **vizuál C++** zvolte možnost **jiné**a potom v prostředním podokně vyberte **prázdný projekt**. Pak zadejte název podobný **Mixed_Mode_Debugging** a klikněte na **OK**.
    ::: moniker-end

    Pokud nevidíte šablonu projektu **prázdného projektu** , přejděte do části **nástroje** > **získat nástroje a funkce...** , který otevře instalační program pro Visual Studio. Spustí se instalační program pro Visual Studio. Zvolte **desktopový vývoj s C++**  úlohou a pak zvolte **Upravit**.

    Visual Studio vytvoří projekt.

1. V **Průzkumník řešení**vyberte **zdrojové soubory**a pak vyberte **projekt** > **Přidat novou položku**. Nebo klikněte pravým tlačítkem na **zdrojové soubory** a vyberte **Přidat** > **Nová položka**.

1. V dialogovém okně **Nová položka** vyberte  **C++ soubor (. cpp)** . Do pole **název** zadejte **Mixed_Mode. cpp** a pak vyberte **Přidat**.

    Visual Studio přidá nový C++ soubor do **Průzkumník řešení**.

1. Zkopírujte následující kód do *Mixed_Mode. cpp*:

    ```cpp
    #include "Mixed_Mode.h"
    ```

1. V **Průzkumník řešení**vyberte **hlavičkové soubory**a pak vyberte **projekt** > **Přidat novou položku**. Nebo klikněte pravým tlačítkem na **hlavičkové soubory** a vyberte **Přidat** > **Nová položka**.

1. V dialogovém okně **Nová položka** vyberte **hlavičkový soubor (. h)** . Do pole **název** zadejte **Mixed_Mode. h** a pak vyberte **Přidat**.

   Visual Studio přidá nový soubor hlaviček do **Průzkumník řešení**.

1. Zkopírujte následující kód do *Mixed_Mode. h*:

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

1. Vyberte **soubor** > **Uložit vše** nebo stiskněte klávesovou **zkratku CTRL**+**SHIFT**+**s** a soubory uložte.

**Konfigurace a sestavení projektu knihovny DLL:**

1. Na panelu nástrojů sady Visual Studio vyberte konfigurace **ladění** a platforma **x86** nebo **x64** . Pokud bude vaše volání aplikace .NET Core, která vždy běží v 64ovém režimu, jako platformu vyberte **x64** .

1. V **Průzkumník řešení**vyberte uzel projektu **Mixed_Mode_Debugging** a vyberte ikonu **vlastnosti** , nebo klikněte pravým tlačítkem myši na uzel projektu a vyberte **vlastnosti**.

1. V horní části podokna **vlastností** se ujistěte, že je **Konfigurace** nastavená na **aktivní (ladění)** a že **platforma** je stejná jako ta, kterou jste nastavili na panelu nástrojů: **x64**nebo **Win32** pro platformu x86.

   > [!IMPORTANT]
   > Pokud přepnete platformu z **platformy x86** na **x64** nebo naopak, je nutné překonfigurovat vlastnosti pro novou platformu.

1. V části **Vlastnosti konfigurace** v levém podokně vyberte **linker** > **Upřesnit**a v rozevírací nabídce vedle **položky bez vstupního bodu**vyberte **ne**. Pokud jste ho museli změnit na **ne**, vyberte **použít**.

1. V části **Vlastnosti konfigurace**vyberte možnost **Obecné**a v rozevírací nabídce vedle položky **typ konfigurace**vyberte **dynamická knihovna (. dll)** . Vyberte **Apply** (Použít) a pak vyberte **OK**.

   ![Přepnout na nativní knihovnu DLL](../debugger/media/mixed-mode-set-as-native-dll.png)

1. Vyberte projekt v **Průzkumník řešení** a pak vyberte **sestavit** > **sestavení řešení**, stiskněte **F7**nebo klikněte pravým tlačítkem na projekt a vyberte **sestavit**.

   Projekt by se měl sestavit bez chyb.

## <a name="create-a-simple-managed-app-to-call-the-dll"></a>Vytvoření jednoduché spravované aplikace pro volání knihovny DLL

1. Otevřete Visual Studio a vytvořte nový projekt.

    ::: moniker range=">=vs-2019"
    Stisknutím klávesy **ESC** zavřete okno Start. Zadáním **CTRL + Q** otevřete vyhledávací pole, zadejte příkaz **Konzola**, zvolte **šablony**a pak zvolte **Konzolová aplikace (.net Core)** nebo **aplikace konzoly (.NET Framework)** pro C#. V dialogovém okně, které se zobrazí, vyberte **vytvořit**.

    Pak zadejte název podobný **Mixed_Mode_Calling_App** a klikněte na **vytvořit**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    V horním řádku nabídek zvolte **Soubor** > **Nový** > **Projekt**. V levém podokně dialogového okna **Nový projekt** , v části **C#vizuál**zvolte možnost **plocha systému Windows**a potom v prostředním podokně zvolte **Konzolová aplikace (.NET Framework)** nebo **aplikace konzoly (.NET Core)** .

    Pak zadejte název podobný **Mixed_Mode_Calling_App** a klikněte na **OK**.
    ::: moniker-end

    Pokud nevidíte šablonu projektu **konzolové aplikace** , přejděte do části **nástroje** > **získat nástroje a funkce...** , který otevře instalační program pro Visual Studio. Zvolte úlohu **vývoj desktopových** aplikací pro .NET a pak zvolte **Upravit**.

    > [!NOTE]
    > I když spravované nového projektu můžete také přidat do existujícího řešení C++, vytvoření nového řešení podporuje další scénáře ladění.

   Visual Studio vytvoří prázdný projekt a zobrazí ho v **Průzkumník řešení**.

1. Nahraďte veškerý kód v *program.cs* následujícím kódem:

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

1. V novém kódu Nahraďte cestu k souboru v `[DllImport]` cestou k souboru pro soubor *Mixed_Mode_Debugging. dll* , který jste právě vytvořili. Podívejte se komentář ke kódu pro pomocné parametry. Ujistěte se, že jste zástupný symbol *uživatelského jména* nahradili.

1. Vyberte **soubor** > **Uložit program.cs** nebo stiskněte klávesovou **zkratku CTRL**+**S** a soubor uložte.

## <a name="configure-mixed-mode-debugging"></a>Konfigurovat ladění ve smíšeném režimu

### <a name="to-configure-mixed-mode-debugging-for-a-net-framework-app"></a>Konfigurovat ladění ve smíšeném režimu pro aplikace rozhraní .NET Framework

1. V **Průzkumník řešení**vyberte uzel projektu **Mixed_Mode_Calling_App** a vyberte ikonu **vlastnosti** , nebo klikněte pravým tlačítkem myši na uzel projektu a vyberte **vlastnosti**.

1. V levém podokně vyberte **ladit** , zaškrtněte políčko **Povolit ladění nativního kódu** a pak zavřete stránku Properties (vlastnosti), aby se změny uložily.

    ![Povolit ladění ve smíšeném režimu](../debugger/media/mixed-mode-enable-native-code-debugging.png)

### <a name="to-configure-mixed-mode-debugging-for-a-net-core-app"></a>Konfigurovat ladění ve smíšeném režimu pro aplikace .NET Core

Ve většině verzí sady Visual Studio počínaje verzí Visual Studio 2017 je nutné použít soubor *launchSettings. JSON* namísto vlastností projektu pro povolení ladění ve smíšeném režimu pro nativní kód v aplikaci .NET Core. Pokud chcete sledovat aktualizace uživatelského rozhraní pro tuto funkci, přečtěte si tento [problém GitHub](https://github.com/dotnet/project-system/issues/1125).

1. V **Průzkumník řešení**rozbalte položku **vlastnosti**a otevřete soubor *launchSettings. JSON* .

   >[!NOTE]
   >Ve výchozím nastavení je *launchSettings. JSON* v *c:\users\username\source\repos\ Mixed_Mode_Calling_App \properties*. Pokud *launchSettings. JSON* neexistuje, vyberte projekt **Mixed_Mode_Calling_App** v **Průzkumník řešení** a pak vyberte ikonu **vlastnosti** , nebo klikněte pravým tlačítkem na projekt a vyberte **vlastnosti**. Proveďte dočasnou změnu na kartě **ladění** a sestavte projekt. Tím se vytvoří soubor *launchSettings. JSON* . Vraťte změny, které jste provedli na kartě **ladění** .

1. Do souboru *launchsettings. JSON* přidejte následující řádek:

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

1. V C# projektu otevřete *program.cs*. Nastavte zarážku na následujícím řádku kódu kliknutím na levý levý okraj, výběrem řádku a stisknutím klávesy **F9**nebo kliknutím pravým tlačítkem myši na řádek a výběrem **zarážky** > **Vložit zarážku**.

    ```csharp
    int result = Multiply(7, 7);
    ```

    Do levého okraje, kde nastavit zarážky se zobrazí červený kruh.

1. Stiskněte klávesu **F5**, vyberte zelenou šipku na panelu nástrojů sady Visual Studio nebo vyberte **ladit** > **Spustit ladění** a spusťte ladění.

   Ladicí program pozastavení na zarážce, kterou jste nastavili. Žlutá šipka označuje, kde je nyní pozastavena ladicím programu.

## <a name="step-in-and-out-of-native-code"></a>Krok dovnitř a ven z nativního kódu

1. Když je ladění pozastavené ve spravované aplikaci, stiskněte klávesu **F11**nebo vyberte **ladit** > **Krokovat**s vnořením.

   Otevře se soubor s nativní hlavičkou *Mixed_Mode. h* a zobrazí se žlutá šipka, kde je ladicí program pozastaven.

   ![Krok do nativního kódu](../debugger/media/mixed-mode-step-into-native-code.png)

1. Teď můžete nastavit a dosažení zarážky a zkontrolovat proměnné v nativním nebo spravovaným kódem.

   - Najeďte myší proměnné ve zdrojovém kódu zobrazíte jejich hodnoty.

   - Podívejte se na proměnnou a jejich hodnoty v oknech **Automatické** hodnoty a **místní** hodnoty.

   - Při pozastavení v ladicím programu můžete také použít okna **kukátka** a **zásobník volání** .

1. Stiskněte klávesu **F11** znovu pro posunutí ladicího programu o jeden řádek.

1. Stiskněte **Shift**+**F11** nebo vyberte **ladění** > **Krok ven** , abyste mohli pokračovat v provádění a znovu ho pozastavit ve spravované aplikaci.

1. Stiskněte klávesu **F5** nebo vyberte zelenou šipku pro pokračování v ladění aplikace.

Blahopřejeme! Dokončili jste kurz ladění ve smíšeném režimu.

## <a name="next-step"></a>Další krok

V tomto kurzu jste zjistili, jak k ladění nativního kódu ze spravovaných aplikací tím, že ladění ve smíšeném režimu. Přehled dalších funkcí ladicího programu naleznete v tématu:

> [!div class="nextstepaction"]
> [První seznámení s ladicím programem](../debugger/debugger-feature-tour.md)
