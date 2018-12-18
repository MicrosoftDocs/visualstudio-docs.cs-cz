---
title: Rozšíření okna výstup | Dokumentace Microsoftu
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
- Output window, about Output window
ms.assetid: b02fa88c-f92a-4ff6-ba5f-2eb4d48a643a
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e4afd91c42eeb60d005b1eb186c30d3896e3101f
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51731389"
---
# <a name="extending-the-output-window"></a>Rozšíření okna Výstup
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Výstup** okna je sada pro čtení a zápis textových podoken. Visual Studio obsahuje tyto předdefinované podokna: **sestavení**, v projektech, které sdělují zprávy o sestavení, a **Obecné**, ve kterém [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] komunikuje zprávy o integrovaném vývojovém prostředí. Projekty získáte odkaz na **sestavení** podokně automaticky až <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> metody rozhraní a sady Visual Studio nabízí přímý přístup k **Obecné** podokna prostřednictvím <xref:Microsoft.VisualStudio.Shell.Interop.SVsGeneralOutputWindowPane> Služba. Kromě předdefinovaných podoken můžete vytvořit a spravovat vlastní vlastní podokna.  
  
 Můžete řídit **výstup** přímo pomocí okna <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> a <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane> rozhraní. <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> Rozhraní, které nabízí <xref:Microsoft.VisualStudio.Shell.Interop.SVsOutputWindow> služeb, definuje metody pro vytváření, načítání a zničení **výstup** podoken. <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> Rozhraní definuje metody pro zobrazení podoken, skrytí podokna a manipulaci s jejich textu. Alternativní způsob řízení **výstup** okno je prostřednictvím <xref:EnvDTE.OutputWindow> a <xref:EnvDTE.OutputWindowPane> objekty v objektovém modelu automatizace sady Visual Studio. Tyto objekty zapouzdřují téměř všechny funkce <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> a <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane> rozhraní. Kromě toho <xref:EnvDTE.OutputWindow> a <xref:EnvDTE.OutputWindowPane> objekty přidat některé funkce vyšší úrovně usnadňují výčet **výstup** podokna a načíst text z podokna.  
  
## <a name="creating-an-extension-that-uses-the-output-pane"></a>Vytvoření rozšíření, která používá podokno výstup  
 Můžete vytvořit rozšíření, která zpracovává různých aspektů podokno výstup.  
  
1.  Vytvořte projekt VSIX s názvem `TestOutput` pomocí příkazu nabídky s názvem **TestOutput**. Další informace najdete v tématu [vytváření rozšíření pomocí příkazu nabídky](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
2.  Přidejte následující odkazy:  
  
    1.  EnvDTE  
  
    2.  EnvDTE80  
  
3.  V souboru TestOutput.cs, přidejte následující příkaz using:  
  
    ```f#  
    using EnvDTE;  
    using EnvDTE80;  
    ```  
  
4.  V TestOutput.cs odstraňte ShowMessageBox metody. Přidejte následující pahýl metody:  
  
    ```csharp  
    private void OutputCommandHandler(object sender, EventArgs e)  
    {  
    }  
    ```  
  
5.  V konstruktoru TestOutput změňte na OutputCommandHandler obslužná rutina příkazu. Tady je část, která přidá příkazy:  
  
    ```csharp  
    OleMenuCommandService commandService = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;  
    if (commandService != null)  
    {  
        CommandID menuCommandID = new CommandID(MenuGroup, CommandId);  
        EventHandler eventHandler = OutputCommandHandler;  
        MenuCommand menuItem = new MenuCommand(eventHandler, menuCommandID);  
        commandService.AddCommand(menuItem);  
    }  
    ```  
  
6.  Následující části mají různé metody, které ukazují různé způsoby práci s podoknem výstupu. Můžete volat tyto metody pro tělo metody OutputCommandHandler(). Například následující kód přidá metodu CreatePane() uvedené v další části.  
  
    ```csharp  
    private void OutputCommandHandler(object sender, EventArgs e)  
    {  
        CreatePane(new Guid(), "Created Pane", true, false);  
    }  
    ```  
  
## <a name="creating-an-output-window-with-ivsoutputwindow"></a>Vytvoření výstupní okno s IVsOutputWindow  
 Tento příklad ukazuje, jak vytvořit nový **výstup** podokno okna s použitím <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> rozhraní.  
  
```csharp  
void CreatePane(Guid paneGuid, string title,   
    bool visible, bool clearWithSolution)  
{  
    IVsOutputWindow output =   
        (IVsOutputWindow)GetService(typeof(SVsOutputWindow));  
    IVsOutputWindowPane pane;  
  
    // Create a new pane.  
    output.CreatePane(  
        ref paneGuid,   
        title,   
        Convert.ToInt32(visible),   
        Convert.ToInt32(clearWithSolution));  
  
    // Retrieve the new pane.  
    output.GetPane(ref paneGuid, out pane);  
  
     pane.OutputString("This is the Created Pane \n");  
}  
```  
  
 Pokud chcete přidat tuto metodu rozšíření uvedený v předchozí části, když kliknete **vyvolat TestOutput** příkazu byste měli vidět **výstup** okno s hlavičku, která uvádí, že **zobrazit výstup z: CreatedPane** a slova **jde v podokně vytvoření** v podokně samotný.  
  
## <a name="creating-an-output-window-with-outputwindow"></a>Vytvoření výstupní okno s outputwindow –  
 Tento příklad ukazuje, jak vytvořit **výstup** podokno okna s použitím <xref:EnvDTE.OutputWindow> objektu.  
  
```csharp  
void CreatePane(string title)  
{  
    DTE2 dte = (DTE2)GetService(typeof(DTE));  
    OutputWindowPanes panes =  
        dte.ToolWindows.OutputWindow.OutputWindowPanes;  
  
    try  
    {  
        // If the pane exists already, write to it.  
        panes.Item(title);  
    }  
    catch (ArgumentException)  
    {  
        // Create a new pane and write to it.  
        return panes.Add(title);  
    }  
}  
```  
  
 I když <xref:EnvDTE.OutputWindowPanes> kolekce umožňuje načíst **výstup** podokno okna podle jeho názvu, podokno názvy nemusí být jedinečný. Pokud jste pochybovat jedinečnost názvu, použijte <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow.GetPane%2A> metody k získání správné podokně podle její identifikátor GUID.  
  
 Pokud chcete přidat tuto metodu rozšíření uvedený v předchozí části, když kliknete **vyvolat TestOutput** příkaz, zobrazí se v okně výstupu se, že **zobrazit výstup z:: DTEPane** a slova **přidá podokno DTE** v podokně samotný.  
  
## <a name="deleting-an-output-window"></a>Odstranění výstupní okno  
 Tento příklad ukazuje, jak odstranit **výstup** podokno okna.  
  
```csharp  
void DeletePane(Guid paneGuid)  
{  
    IVsOutputWindow output =  
    (IVsOutputWindow)ServiceProvider.GetService(typeof(SVsOutputWindow));  
  
    IVsOutputWindowPane pane;  
    output.GetPane(ref paneGuid, out pane);  
  
    if (pane == null)  
    {  
        CreatePane(paneGuid, "New Pane\n", true, true);  
    }  
     else  
    {  
        output.DeletePane(ref paneGuid);  
    }  
}  
```  
  
 Pokud chcete přidat tuto metodu rozšíření uvedený v předchozí části, když kliknete **vyvolat TestOutput** příkaz, zobrazí se v okně výstupu se, že **zobrazit výstup z:: nové podokno** a slova **přidá podokno vytvořili** v podokně samotný. Pokud kliknete **vyvolat TestOutput** příkaz znovu, v podokně se odstraní.  
  
## <a name="getting-the-general-pane-of-the-output-window"></a>Získávání podokně Obecné v okně Výstup  
 Tento příklad ukazuje, jak získat předdefinované **Obecné** podokně **výstup** okna.  
  
```csharp  
void GetGeneralPane()  
{  
    return (IVsOutputWindowPane)GetService(  
        typeof(SVsGeneralOutputWindowPane));  
}  
```  
  
 Pokud chcete přidat tuto metodu rozšíření uvedený v předchozí části, když kliknete **vyvolat TestOutput** příkazu byste měli vidět, který **výstup** okno zobrazuje slova **nalezen obecné Podokno** v podokně.  
  
## <a name="getting-the-build-pane-of-the-output-window"></a>Načtení sestavení podokna okna výstupu  
 Tento příklad ukazuje, jak najít podokně sestavení a do ní zapisovat. Vzhledem k tomu, že v podokně sestavení aktivováno ve výchozím nastavení, aktivuje jej také.  
  
```csharp  
void OutputTaskItemStringExExample(string buildMessage)  
{  
    EnvDTE80.DTE2 dte = (EnvDTE80.DTE2)ServiceProvider.GetService(typeof(EnvDTE.DTE));  
  
    EnvDTE.OutputWindowPanes panes =  
        dte.ToolWindows.OutputWindow.OutputWindowPanes;  
    foreach (EnvDTE.OutputWindowPane pane in panes)  
        {  
            if (pane.Name.Contains("Build"))  
            {  
                pane.OutputString(buildMessage + "\n");  
                pane.Activate();  
                return;  
             }  
        }  
}  
```

