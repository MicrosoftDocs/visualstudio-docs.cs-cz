---
title: Rozšíření okno Výstup | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Output window, about Output window
ms.assetid: b02fa88c-f92a-4ff6-ba5f-2eb4d48a643a
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2788903c60564d501770616fbe3ad2335e60a250
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204423"
---
# <a name="extending-the-output-window"></a>Rozšíření okna Výstup
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Okno **výstup** je sada textových podoken pro čtení a zápis. Visual Studio obsahuje tato Vestavěná podokna: **sestavení**, ve kterém projekty sdělují zprávy o sestaveních a **Obecné**, ve kterých [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] komunikuje se zprávami o integrovaném vývojovém prostředí (IDE). Projekty automaticky získávají odkaz na podokno **sestavení** prostřednictvím <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> metod rozhraní a Visual Studio nabízí přímý přístup k podoknu **Obecné** prostřednictvím <xref:Microsoft.VisualStudio.Shell.Interop.SVsGeneralOutputWindowPane> služby. Kromě integrovaných podoken můžete vytvářet a spravovat vlastní podokna.  
  
 Okno **výstup** můžete řídit přímo prostřednictvím <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane> rozhraní a. <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow>Rozhraní, které <xref:Microsoft.VisualStudio.Shell.Interop.SVsOutputWindow> služba nabízí, definuje metody pro vytváření, načítání a zničení podoken **výstupního** okna. <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow>Rozhraní definuje metody pro zobrazování podoken, skrývání podoken a manipulaci s jejich textem. Alternativní způsob řízení **výstupního** okna je prostřednictvím <xref:EnvDTE.OutputWindow> <xref:EnvDTE.OutputWindowPane> objektů a v modelu automatizačních objektů sady Visual Studio. Tyto objekty zapouzdřují skoro všechny funkce <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane> rozhraní a. Kromě toho <xref:EnvDTE.OutputWindow> <xref:EnvDTE.OutputWindowPane> objekty a přidávají některé funkce vyšší úrovně, které usnadňují zobrazení výčtu podoken **výstupního** okna a načtení textu z podoken.  
  
## <a name="creating-an-extension-that-uses-the-output-pane"></a>Vytvoření rozšíření, které používá podokno výstup  
 Můžete vytvořit rozšíření, které vykonává různé aspekty podokna výstup.  
  
1. Vytvořte projekt VSIX s názvem `TestOutput` s příkazem nabídky s názvem **TestOutput**. Další informace najdete v tématu [Vytvoření rozšíření pomocí příkazu nabídky](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
2. Přidejte následující odkazy:  
  
    1. EnvDTE  
  
    2. EnvDTE80  
  
3. Do TestOutput.cs přidejte následující příkaz using:  
  
    ```f#  
    using EnvDTE;  
    using EnvDTE80;  
    ```  
  
4. V TestOutput.cs odstraňte metodu ShowMessageBox. Přidejte následující zástupnou proceduru následující metody:  
  
    ```csharp  
    private void OutputCommandHandler(object sender, EventArgs e)  
    {  
    }  
    ```  
  
5. V konstruktoru TestOutput Změňte obslužnou rutinu příkazu na OutputCommandHandler. Tady je část, která přidává příkazy:  
  
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
  
6. Následující části obsahují různé metody, které znázorňují různé způsoby práce s podoknem výstup. Tyto metody můžete volat pro tělo metody OutputCommandHandler (). Například následující kód přidá metodu CreatePane () zadanou v další části.  
  
    ```csharp  
    private void OutputCommandHandler(object sender, EventArgs e)  
    {  
        CreatePane(new Guid(), "Created Pane", true, false);  
    }  
    ```  
  
## <a name="creating-an-output-window-with-ivsoutputwindow"></a>Vytvoření okno Výstup pomocí IVsOutputWindow  
 Tento příklad ukazuje, jak vytvořit nové podokno **výstupního** okna pomocí <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> rozhraní.  
  
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
  
 Pokud přidáte tuto metodu do rozšíření uvedeného v předchozí části, po kliknutí na příkaz **vyvolat TestOutput** by se měl zobrazit okno **výstup** s hlavičkou, která říká, že se **zobrazuje výstup z: CreatedPane** a slova **Toto je vytvořeno** v podokně samotné.  
  
## <a name="creating-an-output-window-with-outputwindow"></a>Vytvoření okno Výstup pomocí OutputWindow  
 Tento příklad ukazuje, jak vytvořit podokno **výstupního** okna pomocí <xref:EnvDTE.OutputWindow> objektu.  
  
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
  
 I když <xref:EnvDTE.OutputWindowPanes> kolekce umožňuje načíst podokno **výstupního** okna podle jeho názvu, nadpisy podokna nejsou zaručené jako jedinečné. Pokud si nejste jistí jedinečnost názvu, použijte <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow.GetPane%2A> metodu pro načtení správného podokna podle jeho identifikátoru GUID.  
  
 Pokud přidáte tuto metodu do rozšíření uvedeného v předchozí části, po kliknutí na příkaz **vyvolat TestOutput** by se měl zobrazit okno výstup s hlavičkou, která uvádí, že se **zobrazuje výstup z: DTEPane** a do **podokna DTE v přidaných** slovech v samotném podokně.  
  
## <a name="deleting-an-output-window"></a>Odstranění okno Výstup  
 Tento příklad ukazuje, jak odstranit podokno **výstupního** okna.  
  
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
  
 Pokud přidáte tuto metodu do rozšíření uvedeného v předchozí části, po kliknutí na příkaz **vyvolat TestOutput** by se měl zobrazit okno výstup s hlavičkou, která **ukazuje zobrazit výstup z: nové podokno** a slova **přidáno** v podokně samotné. Pokud znovu kliknete na příkaz **vyvolat TestOutput** , podokno se odstraní.  
  
## <a name="getting-the-general-pane-of-the-output-window"></a>Získání podokna Obecné okno Výstup  
 Tento příklad ukazuje, jak získat předdefinované **Obecné** podokno okna **výstup** .  
  
```csharp  
void GetGeneralPane()  
{  
    return (IVsOutputWindowPane)GetService(  
        typeof(SVsGeneralOutputWindowPane));  
}  
```  
  
 Pokud přidáte tuto metodu do rozšíření uvedeného v předchozí části, po kliknutí na příkaz **vyvolat TestOutput** byste měli vidět, že v okně **výstup** se zobrazí slova, které se nachází v podokně s **obecným** zobrazením.  
  
## <a name="getting-the-build-pane-of-the-output-window"></a>Získání podokna sestavení okno Výstup  
 Tento příklad ukazuje, jak najít podokno sestavení a zapsat do něj. Vzhledem k tomu, že se podokno sestavení ve výchozím nastavení neaktivuje, aktivuje se také.  
  
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
