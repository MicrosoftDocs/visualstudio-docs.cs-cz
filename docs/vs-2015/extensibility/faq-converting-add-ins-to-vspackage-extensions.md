---
title: 'Nejčastější dotazy: převod doplňků na rozšíření VSPackage | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 3a01d333-6e31-423f-ae06-5091a4fcb7a9
caps.latest.revision: 23
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: bc6ed31f96fc2021d0d9e104692f0440cfb78a5e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64821274"
---
# <a name="faq-converting-add-ins-to-vspackage-extensions"></a>Časté otázky: Převádění doplňků na rozšíření VSPackage
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Doplňky jsou nyní zastaralé. Chcete-li vytvořit nové rozšíření sady Visual Studio, je nutné vytvořit rozšíření VSIX. Tady jsou odpovědi na některé nejčastější dotazy týkající se převodu doplňku sady Visual Studio na rozšíření VSIX.  
  
> [!WARNING]
> Od sady Visual Studio 2015 pro projekty C# a Visual Basic můžete použít projekt VSIX a přidat šablony položek pro příkazy nabídky, okna nástrojů a VSPackage. Další informace najdete v tématu [co je nového v sadě Visual Studio 2015 SDK](../extensibility/what-s-new-in-the-visual-studio-2015-sdk.md).  
  
> [!IMPORTANT]
> V mnoha případech můžete jednoduše přenést kód doplňku do projektu VSIX pomocí položky projektu VSPackage. Automatizační objekt DTE můžete získat voláním <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> metody.  
>   
> `DTE2 dte = (DTE2)GetService(typeof(DTE));`  
>   
> Další informace najdete v tématu [Jak mohu spustit můj kód doplňku ve VSPackage?](../extensibility/faq-converting-add-ins-to-vspackage-extensions.md#BKMK_RunAddin) níže.  
  
## <a name="what-software-do-i-need-to-develop-vsix-extensions"></a>Jaký software potřebuji k vývoji rozšíření VSIX?  
 Od sady Visual Studio 2015 nenainstalujete sadu Visual Studio SDK z webu Stažení softwaru. V instalačním programu sady Visual Studio je zahrnutý jako volitelná funkce. Sadu VS SDK můžete také nainstalovat později. Další informace najdete v tématu [instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="wheres-the-extension-documentation"></a>Kde se nachází dokumentace k rozšíření?  
 Začněte s [zahájením vývoje rozšíření sady Visual Studio](../extensibility/starting-to-develop-visual-studio-extensions.md). Další články o vývoji rozšíření VSSDK na webu MSDN najdete pod tím, co je tu.  
  
## <a name="can-i-convert-my-add-in-project-to-a-vsix-project"></a>Můžu převést projekt doplňku na projekt VSIX?  
 Projekt doplňku nelze převést přímo na projekt VSIX, protože mechanismy používané v projektech VSIX nejsou stejné jako ty v projektech doplňku. Šablona projektu VSIX, spolu se správnými šablonami položek projektu, mají velký kód, který je poměrně snadný, aby bylo možné ho získat a spustit jako rozšíření VSIX.  
  
## <a name="how-do-i-start-developing-vsix-extensions"></a><a name="BKMK_StartDeveloping"></a> Návody začít vyvíjet rozšíření VSIX?  
 Tady je postup, jak vytvořit VSIX, který obsahuje příkaz nabídky:  
  
#### <a name="to-make-a-vsix-extension-that-has-a-menu-command"></a>Chcete-li vytvořit rozšíření VSIX, které má příkaz nabídky  
  
1. Vytvořte projekt VSIX. (**Soubor**, **Nový**, **projekt**nebo typ **projektu** v okně **Snadné spuštění** ). V dialogovém okně **Nový projekt** rozbalte položku **Visual C#/rozšiřitelnost** nebo **Visual Basic/rozšiřitelnost** a vyberte **projekt VSIX**.) Pojmenujte projekt **TestExtension** a zadejte jeho umístění.  
  
2. Přidejte šablonu položky projektu **vlastního příkazu** . (V **Průzkumník řešení** klikněte pravým tlačítkem myši na uzel projektu a vyberte **přidat/nová položka**. V dialogovém okně **Nový projekt** pro jazyk Visual C# nebo Visual Basic vyberte uzel **rozšiřitelnost** a vyberte **vlastní příkaz**.)  
  
3. Stisknutím klávesy F5 Sestavte a spusťte projekt v režimu ladění.  
  
     Zobrazí se druhá instance aplikace Visual Studio. Tato druhá instance se nazývá experimentální instance a nemusí mít stejné nastavení jako instance sady Visual Studio, kterou používáte k psaní kódu. Při prvním spuštění experimentální instance se zobrazí výzva, abyste se přihlásili do prostředí VS Online a určili svůj motiv a profil.  
  
     V nabídce **nástroje** (v experimentální instanci) by se mělo zobrazit tlačítko s názvem **Můj název příkazu**. Když vyberete toto tlačítko, zobrazí se zpráva: **uvnitř TestVSPackagePackage. MenuItemCallback ()**.  
  
## <a name="how-can-i-run-my-add-in-code-in-a-vspackage"></a><a name="BKMK_RunAddin"></a> Jak mohu spustit můj kód doplňku v VSPackage?  
 Kód doplňku se obvykle spouští jedním ze dvou způsobů:  
  
- Aktivováno příkazem nabídky (kód je v `IDTCommandTarget.Exec` metodě)  
  
- Automaticky při spuštění (kód je v `OnConnection` obslužné rutině události)  
  
  Stejné věci můžete provádět v VSPackage. Zde je uveden postup přidání kódu doplňku v metodě zpětného volání:  
  
#### <a name="to-implement-a-menu-command-in-a-vspackage"></a>Implementace příkazu nabídky v VSPackage  
  
1. Vytvořte VSPackage, který obsahuje příkaz nabídky. (Další informace najdete v tématu [Vytvoření rozšíření pomocí příkazu nabídky](../extensibility/creating-an-extension-with-a-menu-command.md).)  
  
2. Otevřete soubor, který obsahuje definici sady VSPackage. (V projektu C# je to <em>\<your project name></em> Package.cs.)  
  
3. Přidejte `using` do souboru následující příkazy:  
  
   ```csharp  
   using EnvDTE;  
   using EnvDTE80;  
   ```  
  
4. Vyhledejte `MenuItemCallback` metodu. Přidejte volání pro <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> k získání <xref:EnvDTE80.DTE2> objektu:  
  
   ```csharp  
   DTE2 dte = (DTE2)GetService(typeof(DTE));  
   ```  
  
5. Přidejte kód, který byl doplňkem v `IDTCommandTarget.Exec` metodě. Například zde je nějaký kód, který přidá nové podokno do okna **výstup** a vytiskne "nějaký text" v novém podokně.  
  
   ```csharp  
   private void MenuItemCallback(object sender, EventArgs e)  
   {  
       DTE2 dte = (DTE2) GetService(typeof(DTE));  
       OutputWindow outputWindow = dte.ToolWindows.OutputWindow;  
  
       OutputWindowPane outputWindowPane = outputWindow.OutputWindowPanes.Add("A New Pane");  
       outputWindowPane.OutputString("Some Text");  
   }  
  
   ```  
  
6. Sestavte a spusťte tento projekt. Stiskněte klávesu F5 nebo vyberte **Spustit** na panelu nástrojů **ladění** . V experimentální instanci aplikace Visual Studio by měla mít nabídka **nástroje** tlačítko s názvem **Můj název příkazu**. Když vyberete toto tlačítko, slova v podokně **výstup** by se měla zobrazit jako **text** . (Možná budete muset otevřít okno **výstup** .)  
  
   Můžete také spustit kód při spuštění. Tento přístup se ale obecně nedoporučuje pro rozšíření VSPackage. Pokud se při spuštění sady Visual Studio pokusí načíst příliš mnoho rozšíření, čas spuštění se může projevit již pozorně. Lepším postupem je načíst VSPackage automaticky pouze v případě, že je splněna nějaká podmínka (například otevření řešení).  
  
   Tento postup ukazuje, jak spustit kód doplňku ve VSPackage, který se automaticky načte při otevření řešení:  
  
#### <a name="to-autoload-a-vspackage"></a>Automatické načtení VSPackage  
  
1. Vytvoří projekt VSIX s položkou projektu balíčku sady Visual Studio. (Návod k tomu, jak to provést, najdete v tématu [návody zahájení vývoje rozšíření VSIX?](../extensibility/faq-converting-add-ins-to-vspackage-extensions.md#BKMK_StartDeveloping). Stačí místo toho přidat položku projektu **balíčku sady Visual Studio** .) Pojmenujte projekt VSIX **TestAutoload**.  
  
2. Otevřete TestAutoloadPackage.cs. Vyhledejte řádek, ve kterém je deklarována Třída balíčku:  
  
   ```csharp  
   public sealed class <name of your package>Package : Package  
   ```  
  
3. Nad tímto řádkem je sada atributů. Přidat tento atribut:  
  
   ```csharp  
   [ProvideAutoLoad(UIContextGuids80.SolutionExists)]  
   ```  
  
4. Nastavte zarážku v `Initialize()` metodě a spusťte ladění (F5).  
  
5. V experimentální instanci otevřete projekt. Rozhraní VSPackage by mělo být načteno a měla by být vybrána vaše zarážka.  
  
   Můžete určit další kontexty, ve kterých chcete načíst VSPackage pomocí polí <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> . Další informace najdete v tématu [načítání VSPackage](../extensibility/loading-vspackages.md).  
  
## <a name="how-can-i-get-the-dte-object"></a>Jak získám objekt DTE?  
 Pokud váš doplněk nezobrazuje uživatelské rozhraní, například příkazy nabídky, tlačítka panelu nástrojů nebo okna nástrojů – můžete použít váš kód tak, jak je, tak dlouho, dokud získáte automatizační objekt DTE ze sady VSPackage. Zde je uveden postup:  
  
#### <a name="to-get-the-dte-object-from-a-vspackage"></a>Získání objektu DTE ze sady VSPackage  
  
1. V projektu VSIX se šablonou položky balíčku sady Visual Studio vyhledejte <em>\<project name></em> soubor Package.cs. Toto je třída, která je odvozena z <xref:Microsoft.VisualStudio.Shell.Package> . může vám usnadnit interakci se sadou Visual Studio. V takovém případě použijete svůj <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> objekt k získání <xref:EnvDTE80.DTE2> objektu.  
  
2. Přidejte tyto `using` příkazy:  
  
   ```csharp  
   using EnvDTE;  
   using EnvDTE80;  
   ```  
  
3. Vyhledejte `Initialize` metodu. Tato metoda zpracovává příkaz, který jste zadali v průvodci balíčkem. Přidejte volání pro <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> získání objektu DTE:  
  
   ```csharp  
   DTE dte = (DTE)GetService(typeof(DTE));  
   ```  
  
   Po tom, co máte <xref:EnvDTE.DTE> automatizační objekt, můžete do projektu přidat zbytek kódu doplňku. Pokud <xref:EnvDTE80.DTE2> objekt potřebujete, můžete to samé udělat.  
  
## <a name="how-do-i-change-menu-commands-and-toolbar-buttons-in-my-add-in-to-the-vspackage-style"></a>Návody příkazy nabídky změnit a tlačítka panelu nástrojů v mém doplňku na styl VSPackage?  
 Rozšíření VSPackage používají soubor. vsct k vytvoření většiny příkazů nabídky, panelů nástrojů, tlačítek panelu nástrojů a jiného uživatelského rozhraní. Šablona položky projektu **vlastního příkazu** vám nabídne možnost vytvořit příkaz v nabídce **nástroje** . Další informace najdete v tématu [Vytvoření rozšíření pomocí příkazu nabídky](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
 Další informace o souborech. vsct naleznete v tématu [jak rozhraní VSPackage přidávají prvky uživatelského rozhraní](../extensibility/internals/how-vspackages-add-user-interface-elements.md). Návody, které ukazují, jak pomocí souboru. vsct přidat položky nabídky, panely nástrojů a tlačítka panelu nástrojů, najdete v tématu [rozšíření nabídek a příkazů](../extensibility/extending-menus-and-commands.md).  
  
## <a name="how-do-i-add-custom-tool-windows-in-the-vspackage-way"></a>Návody přidat vlastní okna nástrojů do sady VSPackage?  
 Šablona položky projektu vlastního nástroje nabízí možnost vytvořit okno nástroje. Další informace o této šabloně položky projektu naleznete v tématu [Vytvoření rozšíření s oknem nástrojů](../extensibility/creating-an-extension-with-a-tool-window.md). Informace o oknech nástrojů naleznete v tématu [rozšíření a přizpůsobení oken nástrojů](../extensibility/extending-and-customizing-tool-windows.md) a článků pod ním, zejména [Přidání okna nástroje](../extensibility/adding-a-tool-window.md).  
  
## <a name="how-do-i-manage-visual-studio-windows-in-the-vspackage-way"></a>Návody spravovat Visual Studio Windows ve VSPackage?  
 Pokud váš doplněk spravuje aplikace Visual Studio, kód doplňku by měl fungovat ve VSPackage. Například tento postup ukazuje, jak přidat kód, který spravuje **seznam úkolů** do `MenuItemCallback` metody VSPackage.  
  
#### <a name="to-insert-window-management-code-from-an-add-in-into-a-vspackage"></a>Vložení kódu správy okna z doplňku do VSPackage  
  
1. Vytvořte VSPackage, který obsahuje příkaz nabídky, jako v části [návody zahájení vývoje rozšíření VSIX?](../extensibility/faq-converting-add-ins-to-vspackage-extensions.md#BKMK_StartDeveloping) .  
  
2. Otevřete soubor, který obsahuje definici sady VSPackage. (V projektu C# je to <em>\<your project name></em> Package.cs.)  
  
3. Přidejte tyto `using` příkazy:  
  
   ```csharp  
   using EnvDTE;  
   using EnvDTE80;  
   ```  
  
4. Vyhledejte `MenuItemCallback` metodu. Přidejte volání pro <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> k získání <xref:EnvDTE80.DTE2> objektu:  
  
   ```csharp  
   DTE2 dte = (DTE2)GetService(typeof(DTE));  
   ```  
  
5. Přidejte kód z vašeho doplňku. Tady je například nějaký kód, který přidá nové úlohy do **seznam úkolů**, vypíše počet úkolů a pak odstraní jednu úlohu.  
  
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
  
## <a name="how-do-i-manage-projects-and-solutions-in-a-vspackage"></a>Návody spravovat projekty a řešení v VSPackage?  
 Pokud váš doplněk spravuje projekty a řešení, kód doplňku by měl fungovat ve VSPackage. Například tento postup ukazuje, jak přidat kód, který získá spouštěný projekt.  
  
1. Vytvořte VSPackage, který obsahuje příkaz nabídky, jako v části [návody zahájení vývoje rozšíření VSIX?](../extensibility/faq-converting-add-ins-to-vspackage-extensions.md#BKMK_StartDeveloping) .  
  
2. Otevřete soubor, který obsahuje definici sady VSPackage. (V projektu C# je to <em>\<your project name></em> Package.cs.)  
  
3. Přidejte tyto `using` příkazy:  
  
   ```csharp  
   using EnvDTE;  
   using EnvDTE80;  
   ```  
  
4. Vyhledejte `MenuItemCallback` metodu. Přidejte volání pro <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> k získání <xref:EnvDTE80.DTE2> objektu:  
  
   ```csharp  
   DTE2 dte = (DTE2)GetService(typeof(DTE));  
   ```  
  
5. Přidejte kód z vašeho doplňku. Například následující kód Získá název spouštěného projektu v řešení. (Řešení s více projekty musí být otevřené při spuštění tohoto balíčku.)  
  
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
  
## <a name="how-do-i-set-keyboard-shortcuts-in-a-vspackage"></a>Návody nastavit klávesové zkratky v sadě VSPackage?  
 Použijete `<KeyBindings>` element souboru. vsct. V následujícím příkladu je klávesová zkratka pro příkaz `idCommand1` ALT + a a klávesová zkratka pro příkaz `idCommand2` je Alt + Ctrl + a. Všimněte si syntaxe názvů klíčů.  
  
```xml  
<KeyBindings>  
    <KeyBinding guid="MyProjectCmdSet" id="idCommand1" editor="guidVSStd97" key1="A" mod1="ALT" />  
    <KeyBinding guid="MyProjectCmdSet" id="idCommand2" editor="guidVSStd97" key1="A" mod1="CONTROL" mod2="ALT" />  
</KeyBindings>  
```  
  
## <a name="how-do-i-handle-automation-events-in-a-vspackage"></a>Návody zpracovávat události automatizace v VSPackage?  
 Události automatizace můžete zpracovávat v VSPackage stejným způsobem jako v doplňku. Následující kód ukazuje, jak zpracovat `OnItemRenamed` událost. (V tomto příkladu se předpokládá, že už jste se dopracovali s objektem DTE.)  
  
```csharp  
Events2 dteEvents = (Events2)dte.Events;  
dteEvents.ProjectItemsEvents.ItemRenamed += listener1.OnItemRenamed;   
. . .  
public void OnItemRenamed(EnvDTE.ProjectItem projItem, string oldName)   
{  
    string s = "[Event] Renamed " + oldName + " to " + Path.GetFileName(projItem.get_FileNames(1) + " in project " + projItem.ContainingProject.Name;   
}  
```
