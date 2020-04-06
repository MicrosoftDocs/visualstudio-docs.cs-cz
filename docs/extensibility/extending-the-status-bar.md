---
title: Rozšíření stavového řádku | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- status bars, about status bars
- status bars, overview
ms.assetid: f955115c-4c5f-45ec-b41b-365868c5ec0c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aa62326d82d81f7ee4d10a838209364355cc488e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711543"
---
# <a name="extend-the-status-bar"></a>Rozšíření stavového řádku
K zobrazení informací můžete použít stavový řádek sady Visual Studio v dolní části ide.

 Při rozšíření stavového řádku můžete zobrazit informace a uživatelské rozhraní ve čtyřech oblastech: oblast zpětné vazby, indikátor průběhu, oblast animace a oblast návrháře. Oblast zpětné vazby umožňuje zobrazit text a zvýraznit zobrazený text. Indikátor průběhu zobrazuje přírůstkový průběh pro krátkodobé operace, jako je například uložení souboru. Oblast animace zobrazuje nepřetržitě smyčkovou animaci pro dlouhotrvající operace nebo operace neurčené délky, jako je například vytváření více projektů v řešení. A oblast návrháře zobrazuje číslo řádku a sloupce umístění kurzoru.

 Stavový řádek můžete získat <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar> pomocí rozhraní <xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar> (ze služby). Kromě toho libovolný objekt umístěn na okenní houštinu může <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> zaregistrovat jako objekt klienta stavového řádku implementací rozhraní. Při každé aktivaci okna visual studio dotazuje objekt `IVsStatusbarUser` umístěn na tomto okně pro rozhraní. Pokud je nalezen, <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> volá metodu na vrácené rozhraní a objekt můžete aktualizovat stavový řádek z v rámci této metody. Okna dokumentu, například můžete <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> použít metodu k aktualizaci informací v oblasti návrháře, když se stanou aktivními.

 Následující postupy předpokládají, že rozumíte způsobu vytvoření projektu VSIX a přidání vlastního příkazu nabídky. Další informace naleznete [v tématu Vytvoření rozšíření pomocí příkazu nabídky](../extensibility/creating-an-extension-with-a-menu-command.md).

## <a name="modify-the-status-bar"></a>Změna stavového řádku
 Tento postup ukazuje, jak nastavit a získat text, zobrazit statický text a zvýraznit zobrazený text v oblasti zpětné vazby stavového řádku.

### <a name="read-and-write-to-the-status-bar"></a>Čtení a zápis na stavový řádek

1. Vytvořte projekt VSIX s názvem **TestStatusBarExtension** a přidejte příkaz nabídky s názvem **TestStatusBarCommand**.

2. V *TestStatusBarCommand.cs*nahraďte kód`MenuItemCallback`metody obslužné rutiny příkazu ( ) následujícím:

    ```csharp
    private void MenuItemCallback(object sender, EventArgs e)
    {
        IVsStatusbar statusBar = (IVsStatusbar)ServiceProvider.GetService(typeof(SVsStatusbar));

        // Make sure the status bar is not frozen
        int frozen;

        statusBar.IsFrozen(out frozen);

        if (frozen != 0)
        {
            statusBar.FreezeOutput(0);
        }

        // Set the status bar text and make its display static.
        statusBar.SetText("We just wrote to the status bar.");

        // Freeze the status bar.
        statusBar.FreezeOutput(1);

        // Get the status bar text.
        string text;
        statusBar.GetText(out text);
        System.Windows.Forms.MessageBox.Show(text);

        // Clear the status bar text.
        statusBar.FreezeOutput(0);
        statusBar.Clear();
    }
    ```

3. Zkompilujte kód a spusťte ladění.

4. Otevřete nabídku **Nástroje** v experimentální instanci sady Visual Studio. Klepněte na tlačítko **Vyvolat příkaz TestStatusBarCommand.**

     Měli byste vidět, že text ve stavovém řádku nyní čte **Právě jsme napsali na stavový řádek.** a okno se zprávou, které se zobrazí, má stejný text.

### <a name="update-the-progress-bar"></a>Aktualizace indikátoru průběhu

1. V tomto postupu ukážeme, jak inicializovat a aktualizovat indikátor průběhu.

2. Otevřete soubor *TestStatusBarCommand.cs* `MenuItemCallback` a nahraďte metodu následujícím kódem:

    ```csharp
    private void MenuItemCallback(object sender, EventArgs e)
    {
        IVsStatusbar statusBar = (IVsStatusbar)ServiceProvider.GetService(typeof(SVsStatusbar));
        uint cookie = 0;
        string label = "Writing to the progress bar";

        // Initialize the progress bar.
        statusBar.Progress(ref cookie, 1, "", 0, 0);

        for (uint i = 0, total = 20; i <= total; i++)
        {
            // Display progress every second.
            statusBar.Progress(ref cookie, 1, label, i, total);
            System.Threading.Thread.Sleep(1000);
        }

        // Clear the progress bar.
        statusBar.Progress(ref cookie, 0, "", 0, 0);
    }
    ```

3. Zkompilujte kód a spusťte ladění.

4. Otevřete nabídku **Nástroje** v experimentální instanci sady Visual Studio. Klepněte na tlačítko **Vyvolat příkaz TestStatusBarCommand.**

     Měli byste vidět, že text ve stavovém řádku nyní čte **Zápis do indikátoru průběhu.** Měli byste také vidět indikátor průběhu aktualizovat každou sekundu po dobu 20 sekund. Poté se vymaže stavový řádek a indikátor průběhu.

### <a name="display-an-animation"></a>Zobrazení animace

1. Stavový řádek zobrazuje animaci opakování, která označuje dlouhodobou operaci (například vytváření více projektů v řešení). Pokud tuto animaci nevidíte, ujistěte se, že máte správné nastavení**možností** **nástrojů:** > 

     Přejděte na kartu**Obecné** **možnosti** >  **nástrojů** > a zaškrtněte políčko **Automaticky upravit vizuální prostředí na základě výkonu klienta**. Potom zaškrtněte dílčí možnost **Povolit vizuální prostředí rozšířeného klienta**. Nyní byste měli být schopni zobrazit animaci při vytváření projektu v experimentální instanci sady Visual Studio.

     V tomto postupu zobrazíme standardní animaci sady Visual Studio, která představuje vytváření projektu nebo řešení.

2. Otevřete soubor *TestStatusBarCommand.cs* `MenuItemCallback` a nahraďte metodu následujícím kódem:

    ```csharp
    private void MenuItemCallback(object sender, EventArgs e)
    {
        IVsStatusbar statusBar =(IVsStatusbar)ServiceProvider.GetService(typeof(SVsStatusbar));

        // Use the standard Visual Studio icon for building.
        object icon = (short)Microsoft.VisualStudio.Shell.Interop.Constants.SBAI_Build;

        // Display the icon in the Animation region.
        statusBar.Animation(1, ref icon);

        // The message box pauses execution for you to look at the animation.
        System.Windows.Forms.MessageBox.Show("showing?");

        // Stop the animation.
        statusBar.Animation(0, ref icon);
    }
    ```

3. Zkompilujte kód a spusťte ladění.

4. Otevřete nabídku **Nástroje** v experimentální instanci sady Visual Studio a klepněte na **příkaz Vyvolat příkaz TestStatusBarCommand**.

     Když se zobrazí okno se zprávou, měli byste také vidět animace ve stavovém řádku zcela vpravo. Když zavřete okno se zprávou, animace zmizí.
