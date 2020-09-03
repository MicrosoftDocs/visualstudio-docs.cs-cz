---
title: Načítají se vlastnosti projektu | Microsoft Docs
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- project properties, displaying in tool window
- tool windows, displaying project properties
ms.assetid: 96ba07ca-0811-4013-8602-12550ac4ba79
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9ddfd48827bc762c9189f9b7600cfe9200e5c866
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80711413"
---
# <a name="get-project-properties"></a>Získat vlastnosti projektu

Tento návod ukazuje, jak zobrazit vlastnosti projektu v okně nástroje.

## <a name="prerequisites"></a>Předpoklady

Od sady Visual Studio 2015 nenainstalujete sadu Visual Studio SDK z webu Stažení softwaru. V instalačním programu sady Visual Studio je zahrnutý jako volitelná funkce. Sadu VS SDK můžete také nainstalovat později. Další informace najdete v tématu [instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

### <a name="to-create-a-vsix-project-and-add-a-tool-window"></a>Chcete-li vytvořit projekt VSIX a přidat okno nástrojů

1. Každé rozšíření sady Visual Studio začíná projektem nasazení VSIX, který bude obsahovat prostředky rozšíření. Vytvořte [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projekt VSIX s názvem `ProjectPropertiesExtension` . Šablonu projektu VSIX můžete najít v dialogovém okně **Nový projekt** hledáním "VSIX".

2. Přidejte okno nástroje přidáním vlastní šablony položky okna nástroje s názvem `ProjectPropertiesToolWindow` . V **Průzkumník řešení**klikněte pravým tlačítkem myši na uzel projektu a vyberte možnost **Přidat**  >  **novou položku**. V **dialogovém okně Přidat novou položku**, přejít na rozšiřitelnost **položek Visual C#**  >  **Extensibility** a vybrat **vlastní panel nástrojů**. V poli **název** v dolní části dialogového okna změňte název souboru na `ProjectPropertiesToolWindow.cs` . Další informace o tom, jak vytvořit vlastní panel nástrojů, najdete v tématu [Vytvoření rozšíření s oknem nástrojů](../extensibility/creating-an-extension-with-a-tool-window.md).

3. Sestavte řešení a ověřte, zda se zkompiluje bez chyb.

### <a name="to-display-project-properties-in-a-tool-window"></a>Zobrazení vlastností projektu v okně nástroje

1. V souboru ProjectPropertiesToolWindowCommand.cs přidejte následující direktivy using.

    ```csharp
    using EnvDTE;
    using System.Windows.Controls;

    ```

2. V souboru *ProjectPropertiesToolWindowControl. XAML*odeberte existující tlačítko a přidejte prvek TreeView z panelu nástrojů. Můžete také odebrat obslužnou rutinu události Click ze souboru *ProjectPropertiesToolWindowControl.XAML.cs* .

3. V *ProjectPropertiesToolWindowCommand.cs*použijte `ShowToolWindow()` metodu k otevření projektu a načtení jeho vlastností a poté přidejte vlastnosti do prvku TreeView. Kód pro ShowToolWindow by měl vypadat takto:

    ```csharp
    private void ShowToolWindow(object sender, EventArgs e)
    {
        ToolWindowPane window = this.package.FindToolWindow(typeof(ProjectPropertiesToolWindow), 0, true);
        if ((null == window) || (null == window.Frame))
        {
            throw new NotSupportedException("Cannot create window.");
        }
        IVsWindowFrame windowFrame = (IVsWindowFrame)window.Frame;
        Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(windowFrame.Show());

        // Get the tree view and populate it if there is a project open.
        ProjectPropertiesToolWindowControl control = (ProjectPropertiesToolWindowControl)window.Content;
        TreeView treeView = control.treeView;

        // Reset the TreeView to 0 items.
        treeView.Items.Clear();

        DTE dte = (DTE)this.ServiceProvider.GetService(typeof(DTE));
        Projects projects = dte.Solution.Projects;
        if (projects.Count == 0)   // no project is open
        {
            TreeViewItem item = new TreeViewItem();
            item.Name = "Projects";
            item.ItemsSource = new string[]{ "no projects are open." };
            item.IsExpanded = true;
            treeView.Items.Add(item);
            return;
        }

        Project project = projects.Item(1);
        TreeViewItem item1 = new TreeViewItem();
        item1.Header = project.Name + "Properties";
        treeView.Items.Add(item1);

        foreach (Property property in project.Properties)
        {
            TreeViewItem item = new TreeViewItem();
            item.ItemsSource = new string[] { property.Name };
            item.IsExpanded = true;
            treeView.Items.Add(item);
        }
    }
    ```

4. Sestavte projekt a spusťte ladění. Měla by se zobrazit experimentální instance.

5. V experimentální instanci otevřete projekt.

6. V **zobrazení**  >  **dalších oken** klikněte na **ProjectPropertiesToolWindow**.

  V okně nástroje byste měli vidět ovládací prvek strom spolu s názvem prvního projektu a všech jeho vlastností projektu.
