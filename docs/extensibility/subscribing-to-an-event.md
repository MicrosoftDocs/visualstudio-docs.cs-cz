---
title: Přihlášení k odběru události | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- running document table (RDT), responding to events
- running document table (RDT), subscribing to events
ms.assetid: e94a4fea-94df-488e-8560-9538413422bc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6aefe2efce897aefc26f63835844b0cc705fb5b1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80699684"
---
# <a name="subscribing-to-an-event"></a>Přihlášení k odběru události
Tento návod vysvětluje, jak vytvořit okno nástroje, které reaguje na události v běžící tabulce dokumentů (RDT). Okno nástroje je hostitelem uživatelského ovládacího prvku, který implementuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents> . <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A>Metoda připojuje rozhraní k událostem.

## <a name="prerequisites"></a>Předpoklady
 Od sady Visual Studio 2015 nenainstalujete sadu Visual Studio SDK z webu Stažení softwaru. V instalačním programu sady Visual Studio je zahrnutý jako volitelná funkce. Sadu VS SDK můžete také nainstalovat později. Další informace najdete v tématu [instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="subscribing-to-rdt-events"></a>Přihlášení k odběru událostí RDT

#### <a name="to-create-an-extension-with-a-tool-window"></a>Vytvoření rozšíření s oknem nástrojů

1. Vytvořte projekt s názvem **RDTExplorer** pomocí šablony VSIX a přidejte šablonu položky vlastního okna nástroje s názvem **RDTExplorerWindow**.

     Další informace o vytváření rozšíření pomocí panelu nástrojů naleznete v tématu [Vytvoření rozšíření s oknem nástrojů](../extensibility/creating-an-extension-with-a-tool-window.md).

#### <a name="to-subscribe-to-rdt-events"></a>Přihlášení k odběru událostí RDT

1. Otevřete soubor RDTExplorerWindowControl. XAML a odstraňte tlačítko s názvem `button1` . Přidejte <xref:System.Windows.Forms.ListBox> ovládací prvek a přijměte výchozí název. Element Grid by měl vypadat takto:

    ```xml
    <Grid>
        <StackPanel Orientation="Vertical" Margin="-10,10,10,0">
            <TextBlock Margin="10" HorizontalAlignment="Center">RDTExplorerWindow</TextBlock>
            <ListBox x:Name="listBox" Height="100" />
        </StackPanel>
    </Grid>
    ```

2. Otevřete soubor RDTExplorerWindow.cs v zobrazení kódu. Na začátek souboru přidejte následující direktivy using.

    ```csharp
    using Microsoft.VisualStudio;
    using Microsoft.VisualStudio.Shell;
    using Microsoft.VisualStudio.Shell.Interop;
    ```

3. Upravte `RDTExplorerWindow` třídu tak, aby kromě odvození od <xref:Microsoft.VisualStudio.Shell.ToolWindowPane> třídy implementovala <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents> rozhraní.

    ```csharp
    public class RDTExplorerWindow : ToolWindowPane, IVsRunningDocTableEvents
    {. . .}
    ```

4. Implementujte <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents> .

    - Implementujte rozhraní. Umístěte kurzor na název IVsRunningDocTableEvents. Na levém okraji by se měla zobrazit žárovka. Klikněte na šipku dolů napravo od žárovky a vyberte **implementovat rozhraní**.

5. V každé metodě v rozhraní nahraďte řádek `throw new NotImplementedException();` tímto:

    ```csharp
    return VSConstants.S_OK;
    ```

6. Přidejte pole cookie do třídy RDTExplorerWindow.

    ```csharp
    private uint rdtCookie;
    ```

     To uchovává soubor cookie vrácený <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A> metodou.

7. Přepište metodu Initialize () RDTExplorerWindow k registraci pro události RDT. Vždy byste měli získat služby v metodě Initialize () třídy ToolWindowPane, nikoli v konstruktoru.

    ```csharp
    protected override void Initialize()
    {
        IVsRunningDocumentTable rdt = (IVsRunningDocumentTable)
        this.GetService(typeof(SVsRunningDocumentTable));
        rdt.AdviseRunningDocTableEvents(this, out rdtCookie);
    }
    ```

     <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>Služba se volá za účelem získání <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable> rozhraní. <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A>Metoda propojuje události RDT s objektem, který implementuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents> , v tomto případě objekt RDTExplorer.

8. Aktualizujte metodu Dispose () RDTExplorerWindow.

    ```csharp
    protected override void Dispose(bool disposing)
    {
        // Release the RDT cookie.
        IVsRunningDocumentTable rdt = (IVsRunningDocumentTable)
            Package.GetGlobalService(typeof(SVsRunningDocumentTable));
        rdt.UnadviseRunningDocTableEvents(rdtCookie);

        base.Dispose(disposing);
    }
    ```

     <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnadviseRunningDocTableEvents%2A>Metoda odstraní propojení mezi `RDTExplorer` a RDT oznámení události.

9. Přidejte následující řádek do těla <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnBeforeLastDocumentUnlock%2A> obslužné rutiny těsně před `return` příkaz.

    ```csharp
    public int OnBeforeLastDocumentUnlock(uint docCookie, uint dwRDTLockType, uint dwReadLocksRemaining, uint dwEditLocksRemaining)
    {
        ((RDTExplorerWindowControl)this.Content).listBox.Items.Add("Entering OnBeforeLastDocumentUnlock");
        return VSConstants.S_OK;
    }
    ```

10. Přidejte podobný řádek do těla <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnAfterFirstDocumentLock%2A> obslužné rutiny a dalším událostem, které chcete zobrazit v seznamu.

    ```csharp
    public int OnAfterFirstDocumentLock(uint docCookie, uint dwRDTLockType, uint dwReadLocksRemaining, uint dwEditLocksRemaining)
    {
        ((RDTExplorerWindowControl)this.Content).listBox.Items.Add("Entering OnAfterFirstDocumentLock");
        return VSConstants.S_OK;
    }
    ```

11. Sestavte projekt a spusťte ladění. Zobrazí se experimentální instance sady Visual Studio.

12. Otevřete **RDTExplorerWindow** (**Zobrazit/další Windows/RDTExplorerWindow**).

     Otevře se okno **RDTExplorerWindow** s prázdným seznamem událostí.

13. Otevřete nebo vytvořte řešení.

     `OnBeforeLastDocument`Události a `OnAfterFirstDocument` jsou aktivovány, oznámení o každé události se zobrazí v seznamu událostí.
