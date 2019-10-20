---
title: Přihlášení k odběru události | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- running document table (RDT), responding to events
- running document table (RDT), subscribing to events
ms.assetid: e94a4fea-94df-488e-8560-9538413422bc
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bd2933ee3e0e162740f0c7eb3f3c2307e17ec46d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72647921"
---
# <a name="subscribing-to-an-event"></a>Přihlášení k odběru události
Tento návod vysvětluje, jak vytvořit okno nástroje, které reaguje na události v běžící tabulce dokumentů (RDT). Okno nástroje je hostitelem uživatelského ovládacího prvku, který implementuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>. Metoda <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A> spojuje rozhraní s událostmi.

## <a name="prerequisites"></a>Požadavky
 Od sady Visual Studio 2015 nenainstalujete sadu Visual Studio SDK z webu Stažení softwaru. V instalačním programu sady Visual Studio je zahrnutý jako volitelná funkce. Sadu VS SDK můžete také nainstalovat později. Další informace najdete v tématu [instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="subscribing-to-rdt-events"></a>Přihlášení k odběru událostí RDT

#### <a name="to-create-an-extension-with-a-tool-window"></a>Vytvoření rozšíření s oknem nástrojů

1. Vytvořte projekt s názvem **RDTExplorer** pomocí šablony VSIX a přidejte šablonu položky vlastního okna nástroje s názvem **RDTExplorerWindow**.

     Další informace o vytváření rozšíření pomocí panelu nástrojů naleznete v tématu [Vytvoření rozšíření s oknem nástrojů](../extensibility/creating-an-extension-with-a-tool-window.md).

#### <a name="to-subscribe-to-rdt-events"></a>Přihlášení k odběru událostí RDT

1. Otevřete soubor RDTExplorerWindowControl. XAML a odstraňte tlačítko s názvem `button1`. Přidejte ovládací prvek <xref:System.Windows.Forms.ListBox> a přijměte výchozí název. Element Grid by měl vypadat takto:

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

3. Upravte třídu `RDTExplorerWindow` tak, aby kromě odvození od <xref:Microsoft.VisualStudio.Shell.ToolWindowPane> třídy implementovala rozhraní <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>.

    ```csharp
    public class RDTExplorerWindow : ToolWindowPane, IVsRunningDocTableEvents
    {. . .}
    ```

4. Implementujte <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>.

    - Implementujte rozhraní. Umístěte kurzor na název IVsRunningDocTableEvents. Na levém okraji by se měla zobrazit žárovka. Klikněte na šipku dolů napravo od žárovky a vyberte **implementovat rozhraní**.

5. V každé metodě v rozhraní nahraďte řádek `throw new NotImplementedException();` tímto:

    ```csharp
    return VSConstants.S_OK;
    ```

6. Přidejte pole cookie do třídy RDTExplorerWindow.

    ```csharp
    private uint rdtCookie;
    ```

     To uchovává soubor cookie vrácený metodou <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A>.

7. Přepište metodu Initialize () RDTExplorerWindow k registraci pro události RDT. Vždy byste měli získat služby v metodě Initialize () třídy ToolWindowPane, nikoli v konstruktoru.

    ```csharp
    protected override void Initialize()
    {
        IVsRunningDocumentTable rdt = (IVsRunningDocumentTable)
        this.GetService(typeof(SVsRunningDocumentTable));
        rdt.AdviseRunningDocTableEvents(this, out rdtCookie);
    }
    ```

     Služba <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable> je volána k získání rozhraní <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable>. Metoda <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A> spojuje události RDT s objektem, který implementuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>, v tomto případě objekt RDTExplorer.

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

     Metoda <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnadviseRunningDocTableEvents%2A> odstraní propojení mezi `RDTExplorer` a oznámení události RDT.

9. Přidejte následující řádek do těla obslužné rutiny <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnBeforeLastDocumentUnlock%2A> těsně před příkazem `return`.

    ```csharp
    public int OnBeforeLastDocumentUnlock(uint docCookie, uint dwRDTLockType, uint dwReadLocksRemaining, uint dwEditLocksRemaining)
    {
        ((RDTExplorerWindowControl)this.Content).listBox.Items.Add("Entering OnBeforeLastDocumentUnlock");
        return VSConstants.S_OK;
    }
    ```

10. Přidejte podobný řádek k textu obslužné rutiny <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnAfterFirstDocumentLock%2A> a dalším událostem, které chcete zobrazit v seznamu.

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

     Při vyvolání `OnBeforeLastDocument` a `OnAfterFirstDocument` události se v seznamu událostí zobrazí oznámení o každé události.
