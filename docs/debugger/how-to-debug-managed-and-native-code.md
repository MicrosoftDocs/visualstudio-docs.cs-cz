---
title: 'Kurz: ladění kódu C# a C++ (smíšený režim)'
description: Naučte se ladit nativní knihovnu DLL z aplikace .NET Core nebo .NET Framework pomocí ladění ve smíšeném režimu.
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
ms.openlocfilehash: 0b51a41a2b2df5ac685caebbf08606ae86b4230a
ms.sourcegitcommit: e132a870ec198fdcec289227f1a0c1c48fef070c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/04/2020
ms.locfileid: "93344524"
---
# <a name="tutorial-debug-c-and-c-in-the-same-debugging-session"></a>Kurz: ladění C# a C++ ve stejné relaci ladění

Visual Studio umožňuje povolit v relaci ladění více než jeden typ ladicího programu, který se nazývá ladění v kombinovaném režimu. V tomto kurzu se naučíte ladit spravovaný i nativní kód v jediné relaci ladění.

V tomto kurzu se dozvíte, jak ladit nativní kód ze spravované aplikace, ale můžete také [ladit spravovaný kód z nativní aplikace](../debugger/how-to-debug-in-mixed-mode.md). Ladicí program také podporuje jiné typy ladění v kombinovaném režimu, jako je ladění [Pythonu a nativního kódu](../python/debugging-mixed-mode-c-cpp-python-in-visual-studio.md), a použití ladicího programu skriptu v typech aplikací, jako je ASP.NET.

V tomto kurzu:

> [!div class="checklist"]
> * Vytvoření jednoduché nativní knihovny DLL
> * Vytvoření jednoduché aplikace .NET Core nebo .NET Framework pro volání knihovny DLL
> * Konfigurace ladění ve smíšeném režimu
> * Spustit ladicí program
> * Volání zarážky ve spravované aplikaci
> * Krok do nativního kódu

## <a name="prerequisites"></a>Požadavky

Musíte mít nainstalovanou aplikaci Visual Studio s následujícími úlohami:
- **Vývoj desktopových aplikací v C++**
- Vývoj **desktopových aplikací .NET** nebo **vývoj pro různé platformy .NET Core** v závislosti na typu aplikace, kterou chcete vytvořit.

Pokud nemáte Visual Studio, navštivte stránku [ke stažení pro Visual Studio](https://visualstudio.microsoft.com/downloads/) a nainstalujte si ji zdarma.

Pokud máte nainstalovanou sadu Visual Studio, ale nemáte potřebné úlohy, vyberte **otevřít instalační program pro Visual Studio** v levém podokně dialogového okna **Nový projekt** aplikace Visual Studio. V Instalační program pro Visual Studio vyberte úlohy, které potřebujete, a pak vyberte **Upravit**.

## <a name="create-a-simple-native-dll"></a>Vytvoření jednoduché nativní knihovny DLL

**Chcete-li vytvořit soubory pro projekt knihovny DLL:**

1. Otevřete Visual Studio a vytvořte projekt.

    ::: moniker range=">=vs-2019"
    Stisknutím klávesy **ESC** zavřete okno Start. Zadáním **CTRL + Q** otevřete vyhledávací pole, zadejte **prázdný projekt** , zvolte **šablony** a pak zvolte **prázdný projekt** pro C++. V dialogovém okně, které se zobrazí, vyberte **vytvořit**. Pak zadejte název podobný **Mixed_Mode_Debugging** a klikněte na **vytvořit**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    V horním řádku nabídek vyberte **soubor**  >  **Nový**  >  **projekt**. V levém podokně dialogového okna **Nový projekt** , v části **Visual C++** zvolte možnost **jiné** a potom v prostředním podokně vyberte **prázdný projekt**. Pak zadejte název podobný **Mixed_Mode_Debugging** a klikněte na **OK**.
    ::: moniker-end

    Pokud nevidíte prázdnou šablonu projektu **projektu** , přejděte do části **nástroje**  >  **získat nástroje a funkce...** , které otevře instalační program pro Visual Studio. Spustí se instalační program pro Visual Studio. Zvolte **vývoj desktopových aplikací pomocí C++** a pak zvolte **Upravit**.

    Visual Studio vytvoří projekt.

1. V **Průzkumník řešení** vyberte **zdrojové soubory** a pak vyberte **projekt**  >  **Přidat novou položku**. Nebo klikněte pravým tlačítkem na položku **zdrojové soubory** a vyberte možnost **Přidat**  >  **novou položku**.

1. V dialogovém okně **Nová položka** vyberte **soubor C++ (. cpp)**. Do pole **název** zadejte **Mixed_Mode. cpp** a pak vyberte **Přidat**.

    Visual Studio přidá nový soubor C++ pro **Průzkumník řešení**.

1. Zkopírujte následující kód do *Mixed_Mode. cpp* :

    ```cpp
    #include "Mixed_Mode.h"
    ```

1. V **Průzkumník řešení** vyberte **hlavičkové soubory** a pak vyberte **projekt**  >  **Přidat novou položku**. Nebo klikněte pravým tlačítkem na **hlavičkové soubory** a vyberte **Přidat**  >  **novou položku**.

1. V dialogovém okně **Nová položka** vyberte **hlavičkový soubor (. h)**. Do pole **název** zadejte **Mixed_Mode. h** a pak vyberte **Přidat**.

   Visual Studio přidá nový soubor hlaviček do **Průzkumník řešení**.

1. Zkopírujte následující kód do *Mixed_Mode. h* :

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

1. Vyberte **soubor**  >  **Uložit vše** nebo stiskněte **kombinaci kláves CTRL** + **+ SHIFT** + **s** a soubory uložte.

**Konfigurace a sestavení projektu knihovny DLL:**

1. Na panelu nástrojů sady Visual Studio vyberte konfigurace **ladění** a platforma **x86** nebo **x64** . Pokud bude vaše volání aplikace .NET Core, která vždy běží v 64ovém režimu, jako platformu vyberte **x64** .

1. V **Průzkumník řešení** vyberte uzel projektu **Mixed_Mode_Debugging** a vyberte ikonu **vlastnosti** , nebo klikněte pravým tlačítkem myši na uzel projektu a vyberte **vlastnosti**.

1. V horní části podokna **vlastností** se ujistěte, že je **Konfigurace** nastavená na **aktivní (ladění)** a že **platforma** je stejná jako ta, kterou jste nastavili na panelu nástrojů: **x64** nebo **Win32** pro platformu x86.

   > [!IMPORTANT]
   > Pokud přepnete platformu z **platformy x86** na **x64** nebo naopak, je nutné překonfigurovat vlastnosti pro novou platformu.

1. V části **Vlastnosti konfigurace** v levém podokně vyberte **linker**  >  **Upřesnit** a v rozevírací nabídce vedle **položky bez vstupního bodu** vyberte **ne**. Pokud jste ho museli změnit na **ne** , vyberte **použít**.

1. V části **Vlastnosti konfigurace** vyberte možnost **Obecné** a v rozevírací nabídce vedle položky **typ konfigurace** vyberte **dynamická knihovna (. dll)**. Vyberte **Apply** (Použít) a pak vyberte **OK**.

   ![Přepnout na nativní knihovnu DLL](../debugger/media/mixed-mode-set-as-native-dll.png)

1. Vyberte projekt v **Průzkumník řešení** a pak vyberte **sestavení**  >  **sestavení** , stiskněte **F7** nebo klikněte pravým tlačítkem na projekt a vyberte **sestavit**.

   Projekt by se měl sestavit bez chyb.

## <a name="create-a-simple-managed-app-to-call-the-dll"></a>Vytvoření jednoduché spravované aplikace pro volání knihovny DLL

1. Otevřete Visual Studio a vytvořte nový projekt.

    ::: moniker range=">=vs-2019"
    Stisknutím klávesy **ESC** zavřete okno Start. Zadáním **CTRL + Q** otevřete vyhledávací pole, zadejte příkaz **Konzola** , zvolte **šablony** a pak zvolte **Konzolová aplikace (.net Core)** nebo **aplikace konzoly (.NET Framework)** pro C#. V dialogovém okně, které se zobrazí, vyberte **vytvořit**.

    Pak zadejte název podobný **Mixed_Mode_Calling_App** a klikněte na **vytvořit**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    V horním řádku nabídek vyberte **soubor**  >  **Nový**  >  **projekt**. V levém podokně dialogového okna **Nový projekt** , v části **Visual C#** zvolte možnost **plocha systému Windows** a potom v prostředním podokně zvolte **Konzolová aplikace (.NET Framework)** nebo  **aplikace konzoly (.NET Core)**.

    Pak zadejte název podobný **Mixed_Mode_Calling_App** a klikněte na **OK**.
    ::: moniker-end

    Pokud nevidíte šablonu projektu **konzolové aplikace** , přejděte do části **nástroje**  >  **získat nástroje a funkce...** , které otevře instalační program pro Visual Studio. Zvolte úlohu **vývoj desktopových** aplikací pro .NET a pak zvolte **Upravit**.

    > [!NOTE]
    > Můžete také přidat nový spravovaný projekt do stávajícího řešení jazyka C++. Vytváříme projekt v novém řešení, aby se úloha ladění v kombinovaném režimu obtížnější povedla.

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

1. V novém kódu Nahraďte cestu k souboru `[DllImport]` pomocí cesty k souboru *Mixed_Mode_Debugging.dll* , kterou jste právě vytvořili. Přečtěte si komentář ke kódu pro nápovědu. Ujistěte se, že jste zástupný symbol *uživatelského jména* nahradili.

1. Vyberte **soubor**  >  **Uložit program.cs** nebo stiskněte **klávesu CTRL** + **S** a soubor uložte.

## <a name="configure-mixed-mode-debugging"></a>Konfigurace ladění ve smíšeném režimu

1. V **Průzkumník řešení** vyberte uzel projektu **Mixed_Mode_Calling_App** a vyberte ikonu **vlastnosti** , nebo klikněte pravým tlačítkem myši na uzel projektu a vyberte **vlastnosti**.

1. V levém podokně vyberte **ladit** , zaškrtněte políčko **Povolit ladění nativního kódu** a pak zavřete stránku Properties (vlastnosti), aby se změny uložily.

    ![Povolit ladění ve smíšeném režimu](../debugger/media/mixed-mode-enable-native-code-debugging.png)

## <a name="set-a-breakpoint-and-start-debugging"></a>Nastavit zarážku a spustit ladění

1. V projektu C# otevřete *program.cs*. Nastavte zarážku na následujícím řádku kódu kliknutím do levého levého okraje, vybráním čáry a stisknutím klávesy **F9** nebo kliknutím pravým tlačítkem myši na řádek a výběrem **zarážky**  >  **Vložit** zarážku.

    ```csharp
    int result = Multiply(7, 7);
    ```

    Na levém okraji, kde nastavíte zarážku, se zobrazí červený kroužek.

1. Stiskněte klávesu **F5** , vyberte zelenou šipku na panelu nástrojů sady Visual Studio **nebo vyberte ladění**  >  **Spustit ladění** a spusťte ladění.

   Ladicí program se zastaví na zarážce, kterou jste nastavili. Žlutá šipka indikuje, kde je ladicí program aktuálně pozastaven.

## <a name="step-in-and-out-of-native-code"></a>Krokovat a ven z nativního kódu

1. Když je ladění pozastavené ve spravované aplikaci, stiskněte klávesu **F11** nebo vyberte **ladit**  >  **Krok do**.

   Otevře se soubor s nativní hlavičkou *Mixed_Mode. h* a zobrazí se žlutá šipka, kde je ladicí program pozastaven.

   ![Krokovat s vnořením do nativního kódu](../debugger/media/mixed-mode-step-into-native-code.png)

1. Nyní můžete nastavit a spustit zarážky a zkontrolovat proměnné v nativním nebo spravovaném kódu.

   - Pokud chcete zobrazit jejich hodnoty, najeďte myší na proměnné ve zdrojovém kódu.

   - Podívejte se na proměnnou a jejich hodnoty v oknech **Automatické** hodnoty a **místní** hodnoty.

   - Při pozastavení v ladicím programu můžete také použít okna **kukátka** a **zásobník volání** .

1. Stiskněte klávesu **F11** znovu pro posunutí ladicího programu o jeden řádek.

1. Stiskněte **SHIFT** + **F11** nebo vyberte **ladit**  >  **Krok ven** a pokračujte v provádění a pak znovu pozastavte ve spravované aplikaci.

1. Stiskněte klávesu **F5** nebo vyberte zelenou šipku pro pokračování v ladění aplikace.

Blahopřejeme vám. Dokončili jste kurz ladění ve smíšeném režimu.

## <a name="next-step"></a>Další krok

V tomto kurzu jste zjistili, jak ladit nativní kód ze spravované aplikace povolením ladění ve smíšeném režimu. Přehled dalších funkcí ladicího programu najdete v těchto tématech:

> [!div class="nextstepaction"]
> [První seznámení s ladicím programem](../debugger/debugger-feature-tour.md)
