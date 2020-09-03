---
title: Rozšíření stavového řádku | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- status bars, about status bars
- status bars, overview
ms.assetid: f955115c-4c5f-45ec-b41b-365868c5ec0c
caps.latest.revision: 24
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 28fc1155279ec624cea576b5a70a25800d4ff837
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204410"
---
# <a name="extending-the-status-bar"></a>Rozšíření stavového řádku
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

K zobrazení informací můžete použít stavový řádek sady Visual Studio v dolní části rozhraní IDE.  
  
 Po roztažení stavového řádku můžete zobrazit informace a uživatelské rozhraní ve čtyřech oblastech: oblast zpětné vazby, indikátor průběhu, oblast animace a oblast návrháře. Oblast zpětné vazby umožňuje zobrazit text a zvýraznit zobrazený text. Indikátor průběhu ukazuje přírůstkový průběh pro krátkodobé běžící operace, jako je například ukládání souboru. V oblasti animace se zobrazuje nepřetržitá animace pro dlouhotrvající operace nebo neurčitou délku, jako je například sestavení více projektů v řešení. A oblast návrháře zobrazuje číslo řádku a sloupce umístění kurzoru.  
  
 Stavový řádek můžete získat pomocí <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar> rozhraní (ze <xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar> služby). Kromě toho se každý objekt, který je součástí rámce okna, může zaregistrovat jako objekt klienta stavového řádku implementací <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> rozhraní. Pokaždé, když se aktivuje okno, Visual Studio se dotazuje objektu na daném okně pro dané `IVsStatusbarUser` rozhraní. Pokud je nalezen, volá <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> metodu vráceného rozhraní a objekt může aktualizovat stavový řádek v rámci této metody. Okna dokumentu mohou například použít <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> metodu k aktualizaci informací v oblasti návrháře, když budou aktivní.  
  
 Následující postupy předpokládají, že rozumíte tomu, jak vytvořit projekt VSIX a přidat vlastní příkaz nabídky. Informace najdete v tématu [Vytvoření rozšíření pomocí příkazu nabídky](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
## <a name="modifying-the-status-bar"></a>Úprava stavového řádku  
 Tento postup vám ukáže, jak můžete nastavit a získat text, zobrazit statický text a zvýraznit zobrazený text v oblasti zpětné vazby ve stavovém řádku.  
  
#### <a name="reading-and-writing-to-the-status-bar"></a>Čtení a zápis na stavovém řádku  
  
1. Vytvořte projekt VSIX s názvem **TestStatusBarExtension** a přidejte příkaz nabídky s názvem **TestStatusBarCommand**.  
  
2. V TestStatusBarCommand.cs nahraďte kód metody obslužné rutiny příkazu (MenuItemCallback) následujícím způsobem:  
  
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
  
4. Otevřete nabídku **nástroje** v experimentální instanci aplikace Visual Studio. Klikněte na tlačítko **vyvolat TestStatusBarCommand** .  
  
     Měli byste vidět, že text ve stavovém řádku teď čte **"právě jste napsali na stavovém řádku."** a okno se zprávou, které se zobrazí, má stejný text.  
  
#### <a name="updating-the-progress-bar"></a>Aktualizace indikátoru průběhu  
  
1. V tomto postupu ukážeme, jak se inicializuje a aktualizuje indikátor průběhu.  
  
2. Otevřete soubor TestStatusBarCommand.cs a nahraďte metodu MenuItemCallback následujícím kódem:  
  
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
  
4. Otevřete nabídku **nástroje** v experimentální instanci aplikace Visual Studio. Klikněte na tlačítko **vyvolat TestStatusBarCommand** .  
  
     Měl by se zobrazit, že text ve stavovém řádku nyní čte **"zápis do indikátoru průběhu".** Měli byste také vidět, že se indikátor průběhu aktualizuje každou sekundu na 20 sekund. Poté, co se stavový řádek a indikátor průběhu vymažou.  
  
#### <a name="displaying-an-animation"></a>Zobrazení animace  
  
1. Na stavovém řádku se zobrazuje animace smyčky, která indikuje buď dlouhotrvající operaci (například sestavení více projektů v řešení). Pokud tuto animaci nevidíte, ujistěte se, že máte správné nastavení **nástrojů/možností** :  
  
     Vraťte se na kartu **Nástroje/možnosti/Obecné** a zrušte možnost **automaticky upravit vizuální prostředí na základě výkonu klienta**. Potom zaškrtněte dílčí možnost **Povolit bohatou aplikaci s webovým prostředím**. Nyní byste měli být schopni zobrazit animaci při sestavování projektu v experimentální instanci aplikace Visual Studio.  
  
     V tomto postupu zobrazíme standardní animaci sady Visual Studio, která představuje sestavení projektu nebo řešení.  
  
2. Otevřete soubor TestStatusBarCommand.cs a nahraďte metodu MenuItemCallback následujícím kódem:  
  
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
  
4. Otevřete nabídku **nástroje** v experimentální instanci aplikace Visual Studio a klikněte na **vyvolat TestStatusBarCommand**.  
  
     Když se zobrazí okno se zprávou, měla by se na pravé straně zobrazit také animace na stavovém řádku. Když zavřete okno se zprávou, animace zmizí.
