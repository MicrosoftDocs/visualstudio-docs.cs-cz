---
title: Rozšíření okna výstup | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Output window, about Output window
ms.assetid: b02fa88c-f92a-4ff6-ba5f-2eb4d48a643a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 33e34a78fc06bc2b7f40129e33b6d2d78ff561c5
ms.sourcegitcommit: 20d1b9a5bf041bb28453501eb63bc0537a8e4f54
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/14/2018
ms.locfileid: "51645208"
---
# <a name="extend-the-output-window"></a>Rozšíření okna výstup
**Výstup** okna je sada pro čtení a zápis textových podoken. Visual Studio obsahuje tyto předdefinované podokna: **sestavení**, v projektech, které sdělují zprávy o sestavení, a **Obecné**, ve kterém [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] komunikuje zprávy o integrovaném vývojovém prostředí. Projekty získáte odkaz na **sestavení** podokně automaticky až <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> metody rozhraní a sady Visual Studio nabízí přímý přístup k **Obecné** podokna prostřednictvím <xref:Microsoft.VisualStudio.Shell.Interop.SVsGeneralOutputWindowPane> Služba. Kromě předdefinovaných podoken můžete vytvořit a spravovat vlastní vlastní podokna.  
  
 Můžete řídit **výstup** přímo pomocí okna <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> a <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane> rozhraní. <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> Rozhraní, které nabízí <xref:Microsoft.VisualStudio.Shell.Interop.SVsOutputWindow> služeb, definuje metody pro vytváření, načítání a zničení **výstup** podoken. <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane> Rozhraní definuje metody pro zobrazení podoken, skrytí podokna a manipulaci s jejich textu. Alternativní způsob řízení **výstup** okno je prostřednictvím <xref:EnvDTE.OutputWindow> a <xref:EnvDTE.OutputWindowPane> objekty v objektovém modelu automatizace sady Visual Studio. Tyto objekty zapouzdřují téměř všechny funkce <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> a <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane> rozhraní. Kromě toho <xref:EnvDTE.OutputWindow> a <xref:EnvDTE.OutputWindowPane> objekty přidat některé funkce vyšší úrovně usnadňují výčet **výstup** podokna a načíst text z podokna.  
  
## <a name="create-an-extension-that-uses-the-output-pane"></a>Vytvoření rozšíření, které se používá v podokně výstupu  
 Můžete vytvořit rozšíření, která zpracovává různých aspektů podokno výstup.  
  
1.  Vytvořte projekt VSIX s názvem `TestOutput` pomocí příkazu nabídky s názvem **TestOutput**. Další informace najdete v tématu [vytváření rozšíření pomocí příkazu nabídky](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
2.  Přidejte následující odkazy:  
  
    1.  EnvDTE  
  
    2.  EnvDTE80  
  
3.  V *TestOutput.cs*, přidejte následující příkaz using:  
  
    ```f#  
    using EnvDTE;  
    using EnvDTE80;  
    ```  
  
4.  V *TestOutput.cs*, odstranit `ShowMessageBox` metody. Přidejte následující pahýl metody:  
  
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
  
6.  Následující části mají různé metody, které ukazují různé způsoby práci s podoknem výstupu. Můžete volat tyto metody pro text `OutputCommandHandler()` metody. Například následující kód přidá `CreatePane()` metody uvedené v další části.  
  
    ```csharp  
    private void OutputCommandHandler(object sender, EventArgs e)  
    {  
        CreatePane(new Guid(), "Created Pane", true, false);  
    }  
    ```  
  
## <a name="create-an-output-window-with-ivsoutputwindow"></a>Vytvořit výstupní okno s IVsOutputWindow  
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
  
## <a name="create-an-output-window-with-outputwindow"></a>Vytvořit výstupní okno s outputwindow –  
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
  
## <a name="delete-an-output-window"></a>Odstranit výstupní okno  
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
  
## <a name="get-the-general-pane-of-the-output-window"></a>Hlavní podokno okna výstup  
 Tento příklad ukazuje, jak získat předdefinované **Obecné** podokně **výstup** okna.  
  
```csharp  
void GetGeneralPane()  
{  
    return (IVsOutputWindowPane)GetService(  
        typeof(SVsGeneralOutputWindowPane));  
}  
```  
  
 Pokud chcete přidat tuto metodu rozšíření uvedený v předchozí části, když kliknete **vyvolat TestOutput** příkazu byste měli vidět, který **výstup** okno zobrazuje slova **nalezen obecné Podokno** v podokně.  
  
## <a name="get-the-build-pane-of-the-output-window"></a>Získat sestavení podokna okna výstupu  
 Tento příklad ukazuje, jak najít **sestavení** podokno a zápis do něj. Vzhledem k tomu, **sestavení** není ve výchozím nastavení aktivuje podokno, aktivuje se také.  
  
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
