---
title: Přihlášení k odběru události | Dokumenty společnosti Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699684"
---
# <a name="subscribing-to-an-event"></a>Přihlášení k odběru události
Tento návod vysvětluje, jak vytvořit okno nástroje, které reaguje na události v tabulce spuštěného dokumentu (RDT). Okno nástroje je hostitelem uživatelského ovládacího prvku, který implementuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>. Metoda <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A> spojuje rozhraní s událostmi.

## <a name="prerequisites"></a>Požadavky
 Počínaje Visual Studio 2015 neinstalujete sady Visual Studio SDK ze služby stažení. Je součástí volitelné funkce v nastavení sady Visual Studio. VS SDK můžete také nainstalovat později. Další informace naleznete [v tématu Instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="subscribing-to-rdt-events"></a>Přihlášení k odběru událostí RDT

#### <a name="to-create-an-extension-with-a-tool-window"></a>Vytvoření rozšíření s oknem nástroje

1. Vytvořte projekt s názvem **RDTExplorer** pomocí šablony VSIX a přidejte vlastní šablonu položky okna nástroje s názvem **RDTExplorerWindow**.

     Další informace o vytvoření rozšíření pomocí okna nástroje naleznete v [tématu Vytvoření rozšíření s oknem nástroje](../extensibility/creating-an-extension-with-a-tool-window.md).

#### <a name="to-subscribe-to-rdt-events"></a>Chcete-li se přihlásit k odběru událostí RDT

1. Otevřete soubor RDTExplorerWindowControl.xaml a `button1`odstraňte tlačítko s názvem . Přidejte <xref:System.Windows.Forms.ListBox> ovládací prvek a přijměte výchozí název. Prvek Grid by měl vypadat takto:

    ```xml
    <Grid>
        <StackPanel Orientation="Vertical" Margin="-10,10,10,0">
            <TextBlock Margin="10" HorizontalAlignment="Center">RDTExplorerWindow</TextBlock>
            <ListBox x:Name="listBox" Height="100" />
        </StackPanel>
    </Grid>
    ```

2. Otevřete soubor RDTExplorerWindow.cs v zobrazení kódu. Přidejte následující pomocí direktivy na začátek souboru.

    ```csharp
    using Microsoft.VisualStudio;
    using Microsoft.VisualStudio.Shell;
    using Microsoft.VisualStudio.Shell.Interop;
    ```

3. Upravte `RDTExplorerWindow` třídu tak, aby kromě odvození <xref:Microsoft.VisualStudio.Shell.ToolWindowPane> z třídy <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents> implementuje rozhraní.

    ```csharp
    public class RDTExplorerWindow : ToolWindowPane, IVsRunningDocTableEvents
    {. . .}
    ```

4. Implementovat <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>.

    - Implementujte rozhraní. Umístěte kurzor na název IVsRunningDocTableEvents. Měli byste vidět žárovku na levém okraji. Klepněte na šipku dolů vpravo od žárovky a vyberte **implementovat rozhraní**.

5. V každé metodě v rozhraní `throw new NotImplementedException();` nahraďte řádek tímto:

    ```csharp
    return VSConstants.S_OK;
    ```

6. Přidejte pole cookie do třídy RDTExplorerWindow.

    ```csharp
    private uint rdtCookie;
    ```

     To obsahuje soubor cookie, <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A> který je vrácen metodou.

7. Přepsat metodu Initialize() rdtexplorerwindow pro registraci událostí RDT. Vždy byste měli získat služby v Metodě Initialize() nástroje ToolWindowPane, nikoli v konstruktoru.

    ```csharp
    protected override void Initialize()
    {
        IVsRunningDocumentTable rdt = (IVsRunningDocumentTable)
        this.GetService(typeof(SVsRunningDocumentTable));
        rdt.AdviseRunningDocTableEvents(this, out rdtCookie);
    }
    ```

     Služba <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable> je volána <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable> k získání rozhraní. Metoda <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A> spojuje události RDT s objektem, který implementuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>, v tomto případě objekt RDTExplorer.

8. Aktualizujte metodu Dispose() služby RDTExplorerWindow.

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

     Metoda <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnadviseRunningDocTableEvents%2A> odstraní spojení mezi `RDTExplorer` oznámením události RDT.

9. Přidejte následující řádek do <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnBeforeLastDocumentUnlock%2A> těla obslužné rutiny těsně před `return` příkaz.

    ```csharp
    public int OnBeforeLastDocumentUnlock(uint docCookie, uint dwRDTLockType, uint dwReadLocksRemaining, uint dwEditLocksRemaining)
    {
        ((RDTExplorerWindowControl)this.Content).listBox.Items.Add("Entering OnBeforeLastDocumentUnlock");
        return VSConstants.S_OK;
    }
    ```

10. Přidejte podobný řádek do <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnAfterFirstDocumentLock%2A> těla obslužné rutiny a k dalším událostem, které chcete zobrazit v seznamu.

    ```csharp
    public int OnAfterFirstDocumentLock(uint docCookie, uint dwRDTLockType, uint dwReadLocksRemaining, uint dwEditLocksRemaining)
    {
        ((RDTExplorerWindowControl)this.Content).listBox.Items.Add("Entering OnAfterFirstDocumentLock");
        return VSConstants.S_OK;
    }
    ```

11. Sestavení projektu a začít ladění. Zobrazí se experimentální instance sady Visual Studio.

12. Otevřete **okno RDTExplorerWindow** (**Zobrazení / Ostatní Windows / RDTExplorerWindow**).

     Otevře se okno **RDTExplorerWindow** s prázdným seznamem událostí.

13. Otevřete nebo vytvořte řešení.

     Jako `OnBeforeLastDocument` `OnAfterFirstDocument` události jsou aktivována, oznámení o každé události se zobrazí v seznamu událostí.
