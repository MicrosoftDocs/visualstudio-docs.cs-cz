---
title: Rozšíření výstupního okna | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Output window, about Output window
ms.assetid: b02fa88c-f92a-4ff6-ba5f-2eb4d48a643a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 800b443b079111d1d09fffdd900b246a020578f4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711645"
---
# <a name="extend-the-output-window"></a>Rozšíření okna Výstup
Okno **Výstup** je sada textových panelů pro čtení a zápis. Visual Studio má tyto předdefinované podokna: **Sestavení**, ve kterém projekty [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] komunikovat zprávy o sestavení a **obecné**, ve kterém komunikuje zprávy o integrovaném systému. Projekty získat odkaz na **sestavení** <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> podokna automaticky prostřednictvím metod rozhraní a Visual <xref:Microsoft.VisualStudio.Shell.Interop.SVsGeneralOutputWindowPane> Studio nabízí přímý přístup k **obecné** podokno prostřednictvím služby. Kromě předdefinovaných podoken můžete vytvářet a spravovat vlastní podokna.

 Okno **Výstup** můžete ovládat přímo <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane> prostřednictvím rozhraní a. Rozhraní, <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> které nabízí <xref:Microsoft.VisualStudio.Shell.Interop.SVsOutputWindow> služba, definuje metody pro vytváření, načítání a **ničení** výstupní chod oken. Rozhraní <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane> definuje metody pro zobrazení podoken, skrytí podoken a manipulaci s jejich textem. Alternativní způsob ovládání **výstupní** okno je <xref:EnvDTE.OutputWindow> <xref:EnvDTE.OutputWindowPane> prostřednictvím a objekty v objektovém modelu Visual Studio Automation. Tyto objekty zapouzdřují téměř <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane> všechny funkce rozhraní a. Kromě toho <xref:EnvDTE.OutputWindow> a <xref:EnvDTE.OutputWindowPane> objekty přidat některé vyšší úrovně funkce, aby bylo snazší výčet podokna okna **výstup** a načíst text z podoken.

## <a name="create-an-extension-that-uses-the-output-pane"></a>Vytvoření rozšíření, které používá podokno Výstup
 Můžete vytvořit rozšíření, které vykonává různé aspekty podokna Výstup.

1. Vytvořte projekt VSIX s názvem `TestOutput` příkazu nabídky s názvem **TestOutput**. Další informace naleznete [v tématu Vytvoření rozšíření pomocí příkazu nabídky](../extensibility/creating-an-extension-with-a-menu-command.md).

2. Přidejte následující odkazy:

    1. EnvDTE

    2. EnvDTE80

3. V *TestOutput.cs*přidejte následující příkaz using:

    ```f#
    using EnvDTE;
    using EnvDTE80;
    ```

4. V *TestOutput.cs*odstraňte metodu. `ShowMessageBox` Přidejte následující metodu se zakázaným inzerováním:

    ```csharp
    private void OutputCommandHandler(object sender, EventArgs e)
    {
    }
    ```

5. V konstruktoru TestOutput změňte obslužnou rutinu příkazu na OutputCommandHandler. Zde je část, která přidává příkazy:

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

6. Níže uvedené části mají různé metody, které ukazují různé způsoby práce s podoknem Výstup. Tyto metody můžete volat do `OutputCommandHandler()` těla metody. Například následující kód přidá `CreatePane()` metodu uvedenou v další části.

    ```csharp
    private void OutputCommandHandler(object sender, EventArgs e)
    {
        CreatePane(new Guid(), "Created Pane", true, false);
    }
    ```

## <a name="create-an-output-window-with-ivsoutputwindow"></a>Vytvoření výstupního okna s iVsOutputWindow
 Tento příklad ukazuje, jak vytvořit nové podokno okna **Výstup** pomocí <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> rozhraní.

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

 Pokud přidáte tuto metodu do rozšíření uvedeného v předchozím oddílu, po klepnutí na příkaz **Vyvolat testVýstup** se zobrazí okno **Výstup** se záhlavím **Show output from: CreatedPane** a slovy **Toto je podokno Vytvořeno** v samotném podokně.

## <a name="create-an-output-window-with-outputwindow"></a>Vytvoření výstupního okna s oknem OutputWindow
 Tento příklad ukazuje, jak vytvořit **podokno** okna Výstup pomocí objektu. <xref:EnvDTE.OutputWindow>

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
        panes.Add(title);
    }
}
```

 Přestože <xref:EnvDTE.OutputWindowPanes> kolekce umožňuje načíst podokno okna **Výstup** podle názvu, není zaručeno, že názvy podokn a panelu budou jedinečné. Když pochybujete o jedinečnosti názvu, použijte metodu <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow.GetPane%2A> k načtení správného podokna pomocí identifikátoru GUID.

 Pokud přidáte tuto metodu do rozšíření uvedeného v předchozím oddílu, po klepnutí na příkaz **Vyvolat testVýstup** se zobrazí okno Výstup se záhlavím **Show output from: DTEPane** a slovy **Added DTE Pane** v samotném podokně.

## <a name="delete-an-output-window"></a>Odstranit okno Výstup
 Tento příklad ukazuje, jak odstranit podokno okna **Výstup.**

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

 Pokud přidáte tuto metodu do rozšíření uvedeného v předchozím oddílu, po klepnutí na příkaz **Vyvolat testvýstup** se zobrazí okno Výstup se záhlavím **Show output from: New Pane** a slovy Added Created **Pane** v samotném podokně. Pokud znovu klepnete na příkaz **Vyvolat výstup testu,** podokno se odstraní.

## <a name="get-the-general-pane-of-the-output-window"></a>Získání podokna Obecné okna Výstup
 Tento příklad ukazuje, jak získat předdefinované **obecné** podokno okna **Výstup.**

```csharp
IVsOutputWindowPane GetGeneralPane()
{
    return (IVsOutputWindowPane)GetService(
        typeof(SVsGeneralOutputWindowPane));
}
```

 Pokud přidáte tuto metodu do rozšíření uvedeného v předchozím oddílu, po klepnutí na příkaz **Vyvolat testVýstup** byste měli vidět, že v okně **Výstup** se v podokně zobrazují **podokno Nalezené obecné.**

## <a name="get-the-build-pane-of-the-output-window"></a>Získání podokna sestavení okna Výstup
 Tento příklad ukazuje, jak najít podokno **sestavení** a zapisovat do něj. Vzhledem k **tomu, že** podokno sestavení není ve výchozím nastavení aktivováno, aktivuje se také.

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
