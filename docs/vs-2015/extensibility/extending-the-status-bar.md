---
title: Rozšíření stavového řádku | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- status bars, about status bars
- status bars, overview
ms.assetid: f955115c-4c5f-45ec-b41b-365868c5ec0c
caps.latest.revision: 24
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ea1ed437a58069039be144bbc5153f7596a6ac95
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51733896"
---
# <a name="extending-the-status-bar"></a>Rozšíření stavového řádku
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Stavový řádek sady Visual Studio můžete v dolní části rozhraní IDE zobrazíte informace.  
  
 Když rozšíříte stavového řádku, můžete zobrazit informace a uživatelské rozhraní ve čtyřech oblastech: oblast zpětnou vazbu, indikátor průběhu, animace oblasti a oblasti návrháře. Oblast zpětné vazby umožňuje zobrazit text a zvýraznit zobrazovaného textu. Indikátor průběhu vám ukáže přírůstkového pokroku krátce běžící operací, jako je například ukládání souboru. Animace oblasti zobrazí animace průběžně opakuje pro dlouho běžící operace nebo operace neurčeném délky, jako je například sestavování více projektů v řešení. A návrháře oblasti zobrazuje spojnicový a sloupcový počet umístění kurzoru.  
  
 Stavový řádek můžete získat pomocí <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar> rozhraní (z <xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar> služby). Kromě toho můžete zaregistrovat libovolného objektu umístěn na rámec okna jako stavového řádku objektu klienta implementací <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> rozhraní. Při každé aktivaci okno Visual Studio dotaz se týká objektu umístěn tohoto okna pro `IVsStatusbarUser` rozhraní. Pokud se najde, zavolá <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> metodu na vrácené rozhraní a objekt můžete aktualizovat stavový řádek z v rámci této metody. Windows, například dokument, můžete použít <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> metoda k aktualizaci informací v oblasti návrháře po své aktivaci.  
  
 V následující postupech se předpokládá, že vám pochopit, jak vytvořit projekt VSIX a přidejte vlastní příkaz. Informace najdete v tématu [vytváření rozšíření pomocí příkazu nabídky](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
## <a name="modifying-the-status-bar"></a>Úprava stavového řádku  
 Tento postup ukazuje, jak nastavit a získat text, zobrazit statický text a zvýraznit zobrazeného textu v oblasti zpětnou vazbu ve stavovém řádku.  
  
#### <a name="reading-and-writing-to-the-status-bar"></a>Čtení a zápis do stavového řádku  
  
1.  Vytvořte projekt VSIX s názvem **TestStatusBarExtension** a přidání příkazu nabídky s názvem **TestStatusBarCommand**.  
  
2.  V TestStatusBarCommand.cs nahraďte kód metody obslužné rutiny příkazu (MenuItemCallback) s následujícími možnostmi:  
  
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
  
3.  Zkompilování kódu a spuštění ladění.  
  
4.  Otevřít **nástroje** nabídky v experimentální instanci sady Visual Studio. Klikněte na tlačítko **vyvolat TestStatusBarCommand** tlačítko.  
  
     Měli byste vidět, který text ve stavovém řádku nyní čtení **"Jsme teď napsali na stavový řádek."** a, který se zobrazí okno se zprávou nemá stejný text.  
  
#### <a name="updating-the-progress-bar"></a>Aktualizuje se indikátor průběhu  
  
1.  V tomto postupu vám ukážeme, jak inicializovat a aktualizovat indikátor průběhu.  
  
2.  Otevřete soubor TestStatusBarCommand.cs a metodu MenuItemCallback nahraďte následujícím kódem:  
  
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
  
3.  Zkompilování kódu a spuštění ladění.  
  
4.  Otevřít **nástroje** nabídky v experimentální instanci sady Visual Studio. Klikněte na tlačítko **vyvolat TestStatusBarCommand** tlačítko.  
  
     Měli byste vidět, který text ve stavovém řádku nyní čtení **"Zápis do indikátor průběhu."** Také byste měli vidět indikátor průběhu aktualizovat každou sekundu po dobu 20 sekund. Následně se vymažou stavový řádek a indikátor průběhu.  
  
#### <a name="displaying-an-animation"></a>Zobrazení animace  
  
1.  Stavový řádek zobrazuje opakování animace, která označuje dlouhotrvající operace (například sestavování více projektů v řešení). Pokud nevidíte tuto animaci, ujistěte se, že máte správnou **Nástroje / možnosti** nastavení:  
  
     Přejděte **Nástroje/možnosti / Obecné** kartu a zrušte zaškrtnutí políčka **automaticky upravit vzhled na základě výkonu klienta**. Zaškrtněte možnost dílčí **povolit vzhled plně funkčního klienta**. Teď by měl být vidět animace při sestavování projektu v experimentální instanci sady Visual Studio.  
  
     V tomto postupu zobrazují standardní sady Visual Studio animace, která představuje sestavování projektu nebo řešení.  
  
2.  Otevřete soubor TestStatusBarCommand.cs a metodu MenuItemCallback nahraďte následujícím kódem:  
  
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
  
3.  Zkompilování kódu a spuštění ladění.  
  
4.  Otevřít **nástroje** nabídky v experimentální instanci sady Visual Studio a klikněte na tlačítko **vyvolat TestStatusBarCommand**.  
  
     Když se zobrazí okno se zprávou, měli byste také vidět animace ve stavovém řádku úplně vpravo. Při zavírání okna se zprávou, animace zmizí.

