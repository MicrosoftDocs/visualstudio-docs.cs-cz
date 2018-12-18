---
title: Odběr pro událost | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- running document table (RDT), responding to events
- running document table (RDT), subscribing to events
ms.assetid: e94a4fea-94df-488e-8560-9538413422bc
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 41ed19cb31924e90ef9326aad5c8cad117996793
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2018
ms.locfileid: "31141900"
---
# <a name="subscribing-to-an-event"></a>Odběr pro událost
Tento postup vysvětluje, jak vytvořit okno nástroje, který reaguje na události ve spuštěné tabulce dokumentu (r...). Okno nástroje hostitelem uživatelský ovládací prvek, který implementuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>. <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A> Metoda připojí k událostem rozhraní.  
  
## <a name="prerequisites"></a>Požadavky  
 Od sady Visual Studio 2015 se neinstalovat sadu Visual Studio SDK z webu Stažení softwaru. Je zahrnuta jako volitelná funkce v instalačním programu sady Visual Studio. VS SDK můžete také nainstalovat později. Další informace najdete v tématu [instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="subscribing-to-rdt-events"></a>Přihlášení k odběru událostí r...  
  
#### <a name="to-create-an-extension-with-a-tool-window"></a>Vytváření rozšíření s okno nástroje  
  
1.  Vytvoření projektu s názvem **RDTExplorer** pomocí VSIX šablony a přidat vlastní nástroj šablonu položky okno s názvem **RDTExplorerWindow**.  
  
     Další informace o vytváření rozšíření s okno nástroje najdete v tématu [vytváření rozšíření s okno nástroje](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
#### <a name="to-subscribe-to-rdt-events"></a>Přihlásit k odběru událostí r...  
  
1.  Otevřete soubor RDTExplorerWindowControl.xaml a odstraňte tlačítko s názvem `button1`. Přidat <xref:System.Windows.Forms.ListBox> řízení a přijměte výchozí název. Elementů v mřížce by měl vypadat takto:  
  
    ```xml  
    <Grid>  
        <StackPanel Orientation="Vertical" Margin="-10,10,10,0">  
            <TextBlock Margin="10" HorizontalAlignment="Center">RDTExplorerWindow</TextBlock>  
            <ListBox x:Name="listBox" Height="100" />  
        </StackPanel>  
    </Grid>  
    ```  
  
2.  Otevřete soubor RDTExplorerWindow.cs v zobrazení kódu. Přidejte následující příkazy using na začátek souboru.  
  
    ```csharp  
    using Microsoft.VisualStudio;  
    using Microsoft.VisualStudio.Shell;  
    using Microsoft.VisualStudio.Shell.Interop;  
    ```  
  
3.  Změnit `RDTExplorerWindow` třídy, že kromě odvozování z <xref:Microsoft.VisualStudio.Shell.ToolWindowPane> třída, implementuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents> rozhraní.  
  
    ```csharp  
    public class RDTExplorerWindow : ToolWindowPane, IVsRunningDocTableEvents  
    {. . .}  
    ```  
  
4.  Implementace <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>.  
  
    -   Toto rozhraní implementujte. Umístěte kurzor na název IVsRunningDocTableEvents. Měli byste vidět žárovky na levém okraji. Klikněte na šipku dolů vpravo žárovky a vyberte **implementovat rozhraní**.  
  
5.  V jednotlivých metod v rozhraní, nahraďte řádku `throw new NotImplementedException();` toto:  
  
    ```csharp  
    return VSConstants.S_OK;  
    ```  
  
6.  Přidáte pole soubor cookie k třídě RDTExplorerWindow.  
  
    ```csharp  
    private uint rdtCookie;   
    ```  
  
     To obsahuje souboru cookie, který je vrácený <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A> metoda.  
  
7.  Potlačí metodu Initialize() RDTExplorerWindow k registraci pro r... události. Měli byste obdržet vždy služby metoda inicializaci() ToolWindowPane, není v konstruktoru.  
  
    ```csharp  
    protected override void Initialize()  
    {  
        IVsRunningDocumentTable rdt = (IVsRunningDocumentTable)  
        this.GetService(typeof(SVsRunningDocumentTable));  
        rdt.AdviseRunningDocTableEvents(this, out rdtCookie);  
    }  
    ```  
  
     <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable> Služba se nazývá získat <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable> rozhraní. <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A> Metoda připojí k objektu, který implementuje r... události <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>, v takovém případě RDTExplorer objektu.  
  
8.  Aktualizujte RDTExplorerWindow Dispose() metoda.  
  
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
  
     <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnadviseRunningDocTableEvents%2A> Metoda odstraní připojení mezi `RDTExplorer` a r... oznámení o události.  
  
9. Přidejte následující řádek textu <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnBeforeLastDocumentUnlock%2A> obslužnou rutinu, těsně před `return` příkaz.  
  
    ```csharp  
    public int OnBeforeLastDocumentUnlock(uint docCookie, uint dwRDTLockType, uint dwReadLocksRemaining, uint dwEditLocksRemaining)  
    {  
        ((RDTExplorerWindowControl)this.Content).listBox.Items.Add("Entering OnBeforeLastDocumentUnlock");  
        return VSConstants.S_OK;  
    }  
    ```  
  
10. Přidá řádek podobný do textu <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnAfterFirstDocumentLock%2A> obslužné rutiny a další události, které chcete zobrazit v seznamu.  
  
    ```csharp  
    public int OnAfterFirstDocumentLock(uint docCookie, uint dwRDTLockType, uint dwReadLocksRemaining, uint dwEditLocksRemaining)  
    {  
        ((RDTExplorerWindowControl)this.Content).listBox.Items.Add("Entering OnAfterFirstDocumentLock");  
        return VSConstants.S_OK;  
    }  
    ```  
  
11. Sestavte projekt a spusťte ladění. Zobrazí se experimentální instanci sady Visual Studio.  
  
12. Otevřete **RDTExplorerWindow** (**zobrazení nebo jiných Windows nebo RDTExplorerWindow**).  
  
     **RDTExplorerWindow** otevře se okno s seznamu prázdný událostí.  
  
13. Otevřete nebo vytvořte řešení.  
  
     Jako `OnBeforeLastDocument` a `OnAfterFirstDocument` při vyvolání událostí, oznámení o každé události událostí se zobrazí v seznamu.