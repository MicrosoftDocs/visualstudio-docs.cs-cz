---
title: Načtení vlastností projektu | Dokumentace Microsoftu
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
- project properties, displaying in tool window
- tool windows, displaying project properties
ms.assetid: 96ba07ca-0811-4013-8602-12550ac4ba79
caps.latest.revision: 30
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d7137012fb5b1a562257134ae7f87b19068db165
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51749232"
---
# <a name="getting-project-properties"></a>Načtení vlastností projektu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tento návod ukazuje, jak vlastnosti projektu zobrazí v panelu nástrojů.  
  
## <a name="prerequisites"></a>Požadavky  
 Spouští se v sadě Visual Studio 2015, nenainstalujete sadu Visual Studio SDK ze služby Stažení softwaru. Je zahrnut jako volitelná funkce v instalačním programu sady Visual Studio. VS SDK můžete také nainstalovat později. Další informace najdete v tématu [instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
### <a name="to-create-a-vsix-project-and-add-a-tool-window"></a>Vytvořte projekt VSIX a přidání panelu nástrojů  
  
1.  Každé rozšíření sady Visual Studio spustí nasazení projektu VSIX, který bude obsahovat rozšíření prostředků. Vytvoření [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] VSIX projekt s názvem `ProjectPropertiesExtension`. Můžete najít šablonu projektu VSIX v **nový projekt** dialogového okna v části **Visual C# / rozšíření**.  
  
2.  Přidání panelu nástrojů přidejte šablonu vlastního panelu nástrojů položku s názvem `ProjectPropertiesToolWindow`. V **Průzkumníka řešení**, klikněte pravým tlačítkem na uzel projektu a vyberte **Add / nová položka**. V **dialogového okna Přidat novou položku**, přejděte na stránku **položky Visual C# / rozšíření** a vyberte **vlastního panelu nástrojů**. V **název** pole v dolní části dialogového okna, změňte název souboru, aby `ProjectPropertiesToolWindow.cs`. Další informace o tom, jak vytvořit vlastního okna nástroje najdete v tématu [vytváření rozšíření pomocí panelu nástrojů](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
3.  Sestavte řešení a ověřte, že se zkompiluje bez chyb.  
  
### <a name="to-display-project-properties-in-a-tool-window"></a>Chcete-li zobrazit vlastnosti projektu v panelu nástrojů  
  
1.  V souboru ProjectPropertiesToolWindowCommand.cs přidejte následující příkazy using.  
  
    ```csharp  
    using EnvDTE;  
    using System.Windows.Controls;  
  
    ```  
  
2.  V ProjectPropertiesToolWindowControl.xaml odeberte existující tlačítko a přidejte ovládací prvek TreeView z panelu nástrojů. Můžete také odebrat obslužnou rutinu události kliknutí ze souboru ProjectPropertiesToolWindowControl.xaml.cs.  
  
3.  V ProjectPropertiesToolWindowCommand.cs použijte metodu ShowToolWindow() projekt otevřít a číst jejich vlastnosti a pak přidejte vlastnosti na ovládacím prvku TreeView. Kód pro ShowToolWindow by měl vypadat nějak takto:  
  
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
  
4.  Sestavte projekt a spusťte ladění. Experimentální instanci aplikace by se zobrazit.  
  
5.  V experimentální instanci otevřete projekt.  
  
6.  V **zobrazení / ostatní Windows** klikněte na tlačítko **ProjectPropertiesToolWindow**.  
  
     Měli byste vidět ovládací prvek stromové struktury v panelu nástrojů spolu s názvem první projekt a všechny jeho vlastnosti projektu.

