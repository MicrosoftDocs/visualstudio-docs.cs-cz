---
title: Získání vlastností projektu | Dokumenty společnosti Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711413"
---
# <a name="get-project-properties"></a>Získat vlastnosti projektu

Tento návod ukazuje, jak se zobrazí vlastnosti projektu v okně nástroje.

## <a name="prerequisites"></a>Požadavky

Počínaje Visual Studio 2015 neinstalujete sady Visual Studio SDK ze služby stažení. Je součástí volitelné funkce v nastavení sady Visual Studio. VS SDK můžete také nainstalovat později. Další informace naleznete [v tématu Instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

### <a name="to-create-a-vsix-project-and-add-a-tool-window"></a>Vytvoření projektu VSIX a přidání okna nástroje

1. Každé rozšíření sady Visual Studio začíná projektem nasazení VSIX, který bude obsahovat prostředky rozšíření. Vytvořte [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projekt VSIX s názvem `ProjectPropertiesExtension`. Šablonu projektu VSIX najdete v dialogovém okně **Nový projekt** vyhledáním "vsix".

2. Přidejte okno nástroje přidáním vlastní šablony `ProjectPropertiesToolWindow`položky okna nástroje s názvem . V **Průzkumníku řešení**klepněte pravým tlačítkem myši na uzel projektu a vyberte **přidat** > **novou položku**. V **dialogovém okně Přidat novou položku**přejděte do části**Rozšiřitelnost** **položek** > Visual C# a vyberte vlastní okno **nástroje**. V poli **Název** v dolní části dialogového okna `ProjectPropertiesToolWindow.cs`změňte název souboru na . Další informace o vytvoření vlastního okna nástroje naleznete v [tématu Vytvoření rozšíření s oknem nástroje](../extensibility/creating-an-extension-with-a-tool-window.md).

3. Sestavení řešení a ověřte, zda se zkompiluje bez chyb.

### <a name="to-display-project-properties-in-a-tool-window"></a>Zobrazení vlastností projektu v okně nástroje

1. V souboru ProjectPropertiesToolWindowCommand.cs přidejte následující pomocí direktiv.

    ```csharp
    using EnvDTE;
    using System.Windows.Controls;

    ```

2. V *aplikaci ProjectPropertiesToolTool.xaml*odeberte existující tlačítko a přidejte treeview z panelu nástrojů. Můžete také odebrat obslužnou rutinu události kliknutí ze souboru *ProjectPropertiesToolWindowControl.xaml.cs.*

3. V *ProjectPropertiesToolWindowCommand.cs*použijte `ShowToolWindow()` metodu k otevření projektu a čtení jeho vlastností a přidejte vlastnosti do treeview. Kód pro ShowToolWindow by měl vypadat takto:

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

4. Sestavení projektu a začít ladění. Experimentální instance by se měla zobrazit.

5. V experimentální instanci otevřete projekt.

6. V **zobrazení** > **jiných oken** klikněte na **ProjectPropertiesToolWindow**.

  Ovládací prvek stromu byste měli vidět v okně nástroje spolu s názvem prvního projektu a všech jeho vlastností projektu.
