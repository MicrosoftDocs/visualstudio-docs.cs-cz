---
title: 'Nejčastější dotazy: Převádění doplňků na rozšíření VSPackage | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 3a01d333-6e31-423f-ae06-5091a4fcb7a9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 56088e45af5ed45b3a303ffc99679e77b51f56ae
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49826511"
---
# <a name="faq-converting-add-ins-to-vspackage-extensions"></a>Nejčastější dotazy: Převádění doplňků na rozšíření VSPackage
Nyní jsou zastaralé doplňky. Chcete-li nové rozšíření sady Visual Studio, je potřeba vytvořit rozšíření VSIX. Tady najdete odpovědi na některé nejčastější dotazy o tom, jak převést doplněk Visual Studio k rozšíření VSIX.  
  
> [!WARNING]
>  Spouští se v sadě Visual Studio 2015 pro projekty jazyka C# a Visual Basic, můžete použít projekt VSIX a přidat položku šablony pro příkazy nabídky, panely nástrojů a rozšíření VSPackages. Další informace najdete v tématu [co je nového ve Visual Studio 2015 SDK](../extensibility/what-s-new-in-the-visual-studio-2015-sdk.md).  
  
> [!IMPORTANT]
>  V mnoha případech můžete jednoduše převést kód doplňku do projektu VSIX s položkou projektu VSPackage. Můžete získat automatizační objekt DTE zavoláním <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> v <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> metody.  
>   
>  `DTE2 dte = (DTE2)GetService(typeof(DTE));`  
>   
>  Další informace najdete v tématu [jak mohu spustit kód doplňku v sadě VSPackage?](../extensibility/faq-converting-add-ins-to-vspackage-extensions.md#BKMK_RunAddin) níže.  
  
## <a name="what-software-do-i-need-to-develop-vsix-extensions"></a>Jaký software potřebujete pro vývoj rozšíření VSIX?  
 Spouští se v sadě Visual Studio 2015, nenainstalujete sadu Visual Studio SDK ze služby Stažení softwaru. Je zahrnut jako volitelná funkce v instalačním programu sady Visual Studio. VS SDK můžete také nainstalovat později. Další informace najdete v tématu [instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="wheres-the-extension-documentation"></a>Kde je dokumentace rozšíření?  
 Začněte s [začít vyvíjet rozšíření aplikace Visual Studio](../extensibility/starting-to-develop-visual-studio-extensions.md). Další články o vývoji VSSDK rozšíření na webu MSDN jsou uvedené níže, že jedna.  
  
## <a name="can-i-convert-my-add-in-project-to-a-vsix-project"></a>Můžete převést projekt doplňku do projektu VSIX  
 Projekt doplňku nelze převést přímo do projektu VSIX, protože mechanismus používaný v projektů VSIX není stejné jako ty v projektech doplňků. Šablonou projektu VSIX šablony položek projektu správný a máte velké množství kódu, který usnadňuje relativně ke zprovoznění a spuštěné jako rozšíření VSIX.  
  
##  <a name="BKMK_StartDeveloping"></a> Jak můžu začít vyvíjet rozšíření VSIX?  
 Zde je, jak vytvořit rozšíření VSIX, který obsahuje příkaz nabídky:  
  
#### <a name="to-make-a-vsix-extension-that-has-a-menu-command"></a>Aby bylo rozšíření VSIX, který obsahuje příkaz nabídky  
  
1.  Vytvořte projekt VSIX. (**Souboru** > **nový** > **projektu**, nebo typ **projektu** v **snadnéhospuštění** okno). V **nový projekt** dialogového okna rozbalte **Visual C#** > **rozšiřitelnost** nebo **jazyka Visual Basic**  >   **Rozšiřitelnost** a vyberte **projekt VSIX**.) Pojmenujte projekt **TestExtension** a zadejte umístění pro něj.  
  
2.  Přidat **vlastního příkazu** šablony položky projektu. (Klikněte pravým tlačítkem na uzel projektu v **Průzkumníka řešení** a vyberte **přidat** > **nová položka**. V **nový projekt** dialogové okno pro Visual C# nebo Visual Basic, vyberte **rozšiřitelnost** uzel a vyberte možnost **vlastního příkazu**.)  
  
3.  Stisknutím klávesy **F5** sestavte a spusťte projekt v režimu ladění.  
  
     Zobrazí se druhé instanci aplikace Visual Studio. Této druhé instance se nazývá experimentální instanci a nemusí mít stejné nastavení jako instanci aplikace Visual Studio, které používáte k psaní kódu. Při prvním spuštění experimentální instance, zobrazí se výzva k přihlášení k VS Online a určit motivu a profilu.  
  
     Na **nástroje** nabídky (v experimentální instanci) byste měli vidět tlačítko s názvem **název mé příkazu**. Když vyberete toto tlačítko, by měla zobrazit zpráva: **uvnitř TestVSPackagePackage.MenuItemCallback()**.  
  
##  <a name="BKMK_RunAddin"></a> Jak mohu spustit kód doplňku v sadě VSPackage?  
 Přidejte kód se obvykle běží v jednom ze dvou způsobů:  
  
- Aktivované pomocí příkazu nabídky (kód je v `IDTCommandTarget.Exec` metoda.)  
  
- Automaticky při spuštění (kód je v `OnConnection` obslužné rutiny události.)  
  
  Můžete provádět stejné akce v sadě VSPackage. Tady je postup pro přidání kódu doplňku v metodě zpětného volání:  
  
### <a name="to-implement-a-menu-command-in-a-vspackage"></a>Implementace příkazu nabídky v sadě VSPackage  
  
1. Vytvoření balíčku VSPackage, která obsahuje příkaz nabídky. (Další informace najdete v tématu [vytváření rozšíření pomocí příkazu nabídky](../extensibility/creating-an-extension-with-a-menu-command.md).)  
  
2. Otevřete soubor, který obsahuje definici sady VSPackage. (V projektu jazyka C#, má  *\<název projektu > Package.cs*.)  
  
3. Přidejte následující `using` příkazy do souboru:  
  
   ```csharp  
   using EnvDTE;  
   using EnvDTE80;  
   ```  
  
4. Najít `MenuItemCallback` metody. Přidejte volání do <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> zobrazíte <xref:EnvDTE80.DTE2> objektu:  
  
   ```csharp  
   DTE2 dte = (DTE2)GetService(typeof(DTE));  
   ```  
  
5. Přidejte kód, který doplněk došlo v jeho `IDTCommandTarget.Exec` metoda. Například tady je kód, který přidává nové podokno, které má **výstup** okno a vypíše "Některé Text" v novém podokně.  
  
   ```csharp  
   private void MenuItemCallback(object sender, EventArgs e)  
   {  
       DTE2 dte = (DTE2) GetService(typeof(DTE));  
       OutputWindow outputWindow = dte.ToolWindows.OutputWindow;  
  
       OutputWindowPane outputWindowPane = outputWindow.OutputWindowPanes.Add("A New Pane");  
       outputWindowPane.OutputString("Some Text");  
   }  
  
   ```  
  
6. Sestavte a spusťte tento projekt. Stisknutím klávesy **F5** nebo vyberte **Start** na **ladění** nástrojů. V experimentální instanci sady Visual Studio **nástroje** nabídka má tlačítko s názvem **název mé příkazu**. Pokud zvolíte toto tlačítko, slova **některé Text** by se měla objevit v **výstup** podokno okna. (Možná budete muset otevřít **výstup** okna.)  
  
   Je také možné váš kód spustit při spuštění. Tento postup se obecně nedoporučuje pro rozšíření VSPackage. Pokud příliš mnoho přípon se pokusí načíst při spuštění sady Visual Studio, může být výrazně delší čas spuštění. Je doporučeno automaticky načíst sady VSPackage jenom v případě, že se nesplní nějaká podmínka (např. řešení otevírané).  
  
   Tento postup ukazuje, jak spustit kód doplňku v sadě VSPackage, která načte automaticky při otevření řešení:  
  
### <a name="to-autoload-a-vspackage"></a>K autoload VSPackage  
  
1. Vytvořte projekt VSIX s položkou projektu balíček Visual Studio. (Pokyny k tomu najdete v článku [Jak můžu začít vyvíjet rozšíření VSIX?](../extensibility/faq-converting-add-ins-to-vspackage-extensions.md#BKMK_StartDeveloping). Stačí přidat elementy **balíček Visual Studio** místo položky projektu.) Pojmenujte projekt VSIX **TestAutoload**.  
  
2. Otevřít *TestAutoloadPackage.cs*. Vyhledejte řádek, ve kterém je deklarována třída balíčku:  
  
   ```csharp  
   public sealed class <name of your package>Package : Package  
   ```  
  
3. Nad tímto řádkem se sadu atributů. Přidejte tento atribut:  
  
   ```csharp  
   [ProvideAutoLoad(UIContextGuids80.SolutionExists)]  
   ```  
  
4. Nastavit zarážku `Initialize()` metoda a spuštění ladění (**F5**).  
  
5. V experimentální instanci aplikace otevřete projekt. By se měly načíst sady VSPackage, a musí být vaše zarážka dosažena.  
  
   Můžete zadat jiných kontextech, ve kterých se mají načíst vaše VSPackage pomocí pole <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80>. Další informace najdete v tématu [načtení rozšíření VSPackages](../extensibility/loading-vspackages.md).  
  
## <a name="how-can-i-get-the-dte-object"></a>Jak získat objekt DTE  
 Pokud se váš doplněk nezobrazí uživatelského rozhraní – například příkazy nabídek, tlačítek panelu nástrojů nebo okna nástrojů – je možné využít kód jako-je tak dlouho, jak získat objekt DTE automation z sady VSPackage. Tady je způsob:  
  
### <a name="to-get-the-dte-object-from-a-vspackage"></a>Chcete-li získat objekt DTE z VSPackage  
  
1. V projektu VSIX pomocí šablony položky balíčku Visual Studio, vyhledejte  *\<název projektu > Package.cs* souboru. Toto je třída, která je odvozena z <xref:Microsoft.VisualStudio.Shell.Package>; může pomoci při práci s aplikací Visual Studio. V takovém případě použijte jeho <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> zobrazíte <xref:EnvDTE80.DTE2> objektu.  
  
2. Přidejte tyto `using` příkazy:  
  
   ```csharp  
   using EnvDTE;  
   using EnvDTE80;  
   ```  
  
3. Najít `Initialize` metody. Tato metoda zpracovává příkaz, který jste zadali v Průvodci balíčkem. Přidejte volání do <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> získat objekt DTE:  
  
   ```csharp  
   DTE dte = (DTE)GetService(typeof(DTE));  
   ```  
  
   Až budete mít <xref:EnvDTE.DTE> objektu automatizace, zbytek kódu doplňku můžete přidat do projektu. Pokud potřebujete <xref:EnvDTE80.DTE2> objektu, můžete provést totéž.  
  
## <a name="how-do-i-change-menu-commands-and-toolbar-buttons-in-my-add-in-to-the-vspackage-style"></a>Jak změním příkazů nabídky a tlačítka panelu nástrojů v mé doplňku na VSPackage styl?  
 Použití rozšíření VSPackage *.vsct* souboru se má vytvořit většinu příkazů nabídky, panely nástrojů, tlačítka na panelu nástrojů a dalších uživatelského rozhraní. **Vlastního příkazu** šablony položky projektu poskytuje možnost vytvořit příkaz na **nástroje** nabídky. Další informace najdete v tématu [vytváření rozšíření pomocí příkazu nabídky](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
 Další informace o *.vsct* soubory, naleznete v tématu [jak balíčky VSPackages přidávají prvky uživatelského rozhraní](../extensibility/internals/how-vspackages-add-user-interface-elements.md). Pro návody, které ukazují, jak používat *.vsct* soubor pro přidání položek nabídky, panely nástrojů a tlačítka panelu nástrojů, viz [rozšířit nabídek a příkazů](../extensibility/extending-menus-and-commands.md).  
  
## <a name="how-do-i-add-custom-tool-windows-in-the-vspackage-way"></a>Jak přidat vlastní okna nástrojů tak, jak VSPackage  
 Šablony položky projektu vlastního panelu nástrojů poskytuje možnost vytvořit okno nástroje. Další informace o této šablony položky projektu, naleznete v tématu [vytváření rozšíření pomocí panelu nástrojů](../extensibility/creating-an-extension-with-a-tool-window.md). Informace týkající se oken nástrojů najdete v tématu [rozšířit a přizpůsobit okna nástrojů](../extensibility/extending-and-customizing-tool-windows.md) a články, které je pod ním, zejména [přidat panel nástrojů](../extensibility/adding-a-tool-window.md).  
  
## <a name="how-do-i-manage-visual-studio-windows-in-the-vspackage-way"></a>Jak můžu spravovat okna sady Visual Studio tak, jak VSPackage?  
 Pokud váš doplněk spravuje okna sady Visual Studio, měl by kód doplňku fungovat v sadě VSPackage. Například tento postup ukazuje, jak přidat kód, který spravuje **seznamu úkolů** k `MenuItemCallback` metoda sady VSPackage.  
  
#### <a name="to-insert-window-management-code-from-an-add-in-into-a-vspackage"></a>Vložit kód pro správu okna z doplňku na VSPackage  
  
1.  Vytvoření balíčku VSPackage, která obsahuje příkaz nabídky, stejně jako [Jak můžu začít vyvíjet rozšíření VSIX?](../extensibility/faq-converting-add-ins-to-vspackage-extensions.md#BKMK_StartDeveloping) části.  
  
2.  Otevřete soubor, který obsahuje definici sady VSPackage. (V projektu jazyka C#, má  *\<název projektu > Package.cs*.)  
  
3.  Přidejte tyto `using` příkazy:  
  
    ```csharp  
    using EnvDTE;  
    using EnvDTE80;  
    ```  
  
4.  Najít `MenuItemCallback` metody. Přidejte volání do <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> zobrazíte <xref:EnvDTE80.DTE2> objektu:  
  
    ```csharp  
    DTE2 dte = (DTE2)GetService(typeof(DTE));  
    ```  
  
5.  Přidejte kód z tohoto doplňku. Například tady je kód, který přidá nový úkol **seznamu úkolů**uvádí počet úloh a odstraní jeden úkol.  
  
    ```csharp  
    private void MenuItemCallback(object sender, EventArgs e)   
    {  
        DTE2 dte = (DTE2) GetService(typeof(DTE));   
  
        TaskList tl = (TaskList)dte.ToolWindows.TaskList;   
        askItem tlItem;   
  
        // Add a couple of tasks to the Task List.   
        tlItem = tl.TaskItems.Add(" ", " ", "Test task 1.",    
            vsTaskPriority.vsTaskPriorityHigh, vsTaskIcon.vsTaskIconUser,   
            true, "", 10, true, true);  
        tlItem = tl.TaskItems.Add(" ", " ", "Test task 2.",   
            vsTaskPriority.vsTaskPriorityLow, vsTaskIcon.vsTaskIconComment, true, "", 20, true,true);  
  
        // List the total number of task list items after adding the new task items.  
        System.Windows.Forms.MessageBox.Show("Task Item 1 description: "+tl.TaskItems.Item(2).Description);  
        System.Windows.Forms.MessageBox.Show("Total number of task items: "+tl.TaskItems.Count);   
  
        // Remove the second task item. The items list in reverse numeric order.   
        System.Windows.Forms.MessageBox.Show("Deleting the second task item");  
        tl.TaskItems.Item(2).Delete();  
        System.Windows.Forms.MessageBox.Show("Total number of task items: "+tl.TaskItems.Count);   
    }  
    ```  
  
## <a name="how-do-i-manage-projects-and-solutions-in-a-vspackage"></a>Jak můžu spravovat projekty a řešení v sadě VSPackage?  
 Pokud váš doplněk spravuje projekty a řešení, měl by kód doplňku fungovat v sadě VSPackage. Například tento postup ukazuje, jak přidat kód, který získá spouštěný projekt.  
  
1.  Vytvoření balíčku VSPackage, která obsahuje příkaz nabídky, stejně jako [Jak můžu začít vyvíjet rozšíření VSIX?](../extensibility/faq-converting-add-ins-to-vspackage-extensions.md#BKMK_StartDeveloping) části.  
  
2.  Otevřete soubor, který obsahuje definici sady VSPackage. (V projektu jazyka C#, má  *\<název projektu > Package.cs*.)  
  
3.  Přidejte tyto `using` příkazy:  
  
    ```csharp  
    using EnvDTE;  
    using EnvDTE80;  
    ```  
  
4.  Najít `MenuItemCallback` metody. Přidejte volání do <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> zobrazíte <xref:EnvDTE80.DTE2> objektu:  
  
    ```csharp  
    DTE2 dte = (DTE2)GetService(typeof(DTE));  
    ```  
  
5.  Přidejte kód z tohoto doplňku. Například následující kód získá název projektu při spuštění v řešení. (Řešení vícenásobného projektu musí být otevřený po spuštění tohoto balíčku.)  
  
    ```csharp  
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        DTE2 dte = (DTE2) GetService(typeof(DTE));   
  
        SolutionBuild2 sb = (SolutionBuild2)dte.Solution.SolutionBuild;   
        Project startupProj;   
        string msg = "";  
  
        foreach (String item in (Array)sb.StartupProjects)   
        {  
            msg += item;   
        }  
        System.Windows.Forms.MessageBox.Show("Solution startup Project: "+msg);   
        startupProj = dte.Solution.Item(msg);   
        System.Windows.Forms.MessageBox.Show("Full name of solution's startup project: "+"/n"+startupProj.FullName);   
    }  
    ```  
  
## <a name="how-do-i-set-keyboard-shortcuts-in-a-vspackage"></a>Nastavení klávesové zkratky v sadě VSPackage  
 Můžete použít `<KeyBindings>` elementu *.vsct* souboru. V následujícím příkladu, klávesové zkratky pro příkaz `idCommand1` je **Alt**+**A**a klávesovou zkratku pro příkaz `idCommand2` je **Alt**  + **Ctrl**+**A**. Všimněte si, že syntaxe pro názvy klíčů.  
  
```xml  
<KeyBindings>  
    <KeyBinding guid="MyProjectCmdSet" id="idCommand1" editor="guidVSStd97" key1="A" mod1="ALT" />  
    <KeyBinding guid="MyProjectCmdSet" id="idCommand2" editor="guidVSStd97" key1="A" mod1="CONTROL" mod2="ALT" />  
</KeyBindings>  
```  
  
## <a name="how-do-i-handle-automation-events-in-a-vspackage"></a>Jak mám postupovat při události automatizace v sadě VSPackage?  
 Můžete zpracovávat události automatizace v sadě VSPackage stejným způsobem jako doplněk. Následující kód ukazuje, jak naložit `OnItemRenamed` událostí. (Tento příklad předpokládá, že jste už získali objekt DTE.)  
  
```csharp  
Events2 dteEvents = (Events2)dte.Events;  
dteEvents.ProjectItemsEvents.ItemRenamed += listener1.OnItemRenamed;   
. . .  
public void OnItemRenamed(EnvDTE.ProjectItem projItem, string oldName)   
{  
    string s = "[Event] Renamed " + oldName + " to " + Path.GetFileName(projItem.get_FileNames(1) + " in project " + projItem.ContainingProject.Name;   
}  
```