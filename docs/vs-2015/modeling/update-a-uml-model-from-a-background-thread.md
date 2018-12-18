---
title: Aktualizace modelu UML z vlákna na pozadí | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 42c06b0b-b681-4e19-b5f3-6116dd2a4072
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 4173b70cda9df39ce8a4500817fff199ed1a2996
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51750008"
---
# <a name="update-a-uml-model-from-a-background-thread"></a>Aktualizace modelu UML z vlákna na pozadí
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V některých případech může být užitečné provést změny modelu ve vlákně na pozadí. Například pokud načítáte informace z pomalého externího zdroje, můžete použít vlákno na pozadí k dohledu nad aktualizacemi. To umožňuje uživatelům zobrazit každou aktualizaci ihned poté, co se stane.  
  
 Však musí být vědomi, že úložiště UML není bezpečné pro vlákna. Důležitá jsou následující opatření:  
  
-   Všechny aktualizace modelu nebo diagramu se musí provádět ve vlákně uživatelského rozhraní (UI). Vlákno na pozadí musí používat <xref:System.Windows.Forms.Control.Invoke%2A> nebo `Dispatcher.` <xref:System.Windows.Threading.Dispatcher.Invoke%2A> mít vlákno uživatelského rozhraní provedlo skutečné aktualizace.  
  
-   Pokud seskupíte řady změn do jediné transakce, doporučujeme zabránit uživateli v úpravě modelu, když transakce probíhá. V opačném případě se veškeré úpravy provedené uživatelem stanou součástí stejné transakce. Uživatel můžete zabránit v provádění změn tím zobrazením modálního dialogového okna. Pokud chcete, můžete zadat tlačítko Storno v dialogovém okně. Uživatel můžete zobrazit změny při jejich provádění.  
  
## <a name="example"></a>Příklad  
 Tento příklad používá vlákna na pozadí pro provedení několika změn do modelu. Dialogové okno se používá k vyloučení uživatele, když je spuštěn podproces. V tomto jednoduchém příkladu je k dispozici žádné tlačítko Storno v dialogovém okně. Ale bylo by snadno přidat funkci.  
  
#### <a name="to-run-the-example"></a>Chcete-li spustit příklad  
  
1. Vytvořte obslužnou rutinu příkazu v projektu v jazyce C#, jak je popsáno v [definování příkazu nabídky v diagramu modelování](../modeling/define-a-menu-command-on-a-modeling-diagram.md).  
  
2. Ujistěte se, že projekt obsahuje odkazy na tato sestavení:  
  
   -   Microsoft.VisualStudio.ArchitectureTools.Extensibility  
  
   -   Microsoft.VisualStudio.Modeling.Sdk.[version]  
  
   -   Microsoft.VisualStudio.Modeling.Sdk.Diagrams.[version]  
  
   -   Microsoft.VisualStudio.Uml.Interfaces  
  
   -   System.ComponentModel.Composition  
  
   -   System.Windows.Forms  
  
3. Přidejte do projektu formuláře Windows s názvem **ProgressForm**. By se zobrazit zpráva s oznámením, probíhají aktualizace. Nemusí mít další ovládací prvky.  
  
4. Přidejte soubor jazyka C#, která obsahuje kód, který se zobrazí po provedení kroku 7.  
  
5. Sestavte a spusťte projekt.  
  
    Novou instanci třídy [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] začne v experimentálním režimu.  
  
6. Vytvořte nebo otevřete diagram tříd UML v experimentální instanci [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
7. Klikněte pravým tlačítkem kamkoli v diagramu tříd UML a potom klikněte na tlačítko **přidat několik tříd UML**.  
  
   Několik nových polí tříd se zobrazí v diagramu, jeden po druhém v intervalech půl sekundy.  
  
```csharp  
using System;  
using System.ComponentModel;  
using System.ComponentModel.Composition;  
using System.Threading;  
using System.Windows.Forms;  
  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;  
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;  
using Microsoft.VisualStudio.Uml.Classes;  
  
namespace BackgroundThreadProgressUI // CHANGE TO YOUR NAMESPACE  
{  
  [Export(typeof(ICommandExtension))]  
  [ClassDesignerExtension]  
  class UmlClassAdderCommand : ICommandExtension  
  {  
  
    [Import]  
    IDiagramContext context { get; set; }  
  
    [Import]  
    ILinkedUndoContext linkedUndoContext { get; set; }  
  
    // Called when the user runs the command.  
    public void Execute(IMenuCommand command)  
    {  
      // The form that will exclude the user.  
      ProgressForm form = new ProgressForm();  
  
      // System.ComponentModel.BackgroundWorker is a  
      // convenient way to run a background thread.  
      BackgroundWorker worker = new BackgroundWorker();  
      worker.WorkerSupportsCancellation = true;  
  
      worker.DoWork += delegate(object sender, DoWorkEventArgs args)  
      {  
        // This block will be executed in a background thread.  
  
        IClassDiagram diagram = context.CurrentDiagram as IClassDiagram;  
        IModelStore store = diagram.ModelStore;  
        const int CLASSES_TO_CREATE = 15;  
  
        // Group all the changes together.  
        using (ILinkedUndoTransaction transaction = linkedUndoContext.BeginTransaction("Background Updates"))  
        {  
          for (int i = 1; i < CLASSES_TO_CREATE; i++)  
          {  
            if (worker.CancellationPending)   
               return; // No commit - undo all.  
  
            // Create model elements using the UI thread by using  
            // the Invoke method on the progress form. Always   
            // modify the model and diagrams from a UI thread.  
            form.Invoke((MethodInvoker)(delegate  
            {  
              IClass newClass = store.Root.CreateClass();  
              newClass.Name = string.Format("NewClass{0}", i);  
              diagram.Display(newClass);  
            }));  
  
            // Sleep briefly so that we can watch the updates.  
            Thread.Sleep(500);  
          }  
  
          // Commit the transaction or it will be rolled back.  
          transaction.Commit();  
        }  
      };  
  
      // Close the form when the thread completes.  
      worker.RunWorkerCompleted += delegate(object sender, RunWorkerCompletedEventArgs args)  
      {  
        form.Close();  
      };  
  
      // Start the thread before showing the modal progress dialog.  
      worker.RunWorkerAsync();  
  
      // Show the form modally, parented on VS.  
      // Prevents the user from making changes while in progress.  
      form.ShowDialog();  
    }  
  
    public void QueryStatus(IMenuCommand command)  
    {  
      command.Enabled = command.Visible = true;  
    }  
  
    public string Text  
    {  
      get { return "Add several classes"; }  
    }  
  }  
}  
```  
  
#### <a name="to-allow-the-user-to-cancel-the-thread-in-the-example"></a>Umožnění uživateli zrušit vlákno v tomto příkladu  
  
1.  Přidejte tlačítko Storno do dialogového okna průběhu.  
  
2.  Přidejte následující kód do dialogového okna průběhu:  
  
     `public event MethodInvoker Cancel;`  
  
     `private void CancelButton_Click(object sender, EventArgs e)`  
  
     `{`  
  
     `Cancel();`  
  
     `}`  
  
3.  Metoda Execute() vloží tento řádek po konstrukci formuláře:  
  
     `form.Cancel += delegate() { worker.CancelAsync(); };`  
  
### <a name="other-methods-of-accessing-the-ui-thread"></a>Jiné metody přístupu k vláknu uživatelského rozhraní  
 Pokud nechcete vytvořit dialogové okno, se můžete dostat ovládací prvek, který zobrazuje diagram:  
  
 `DiagramView uiThreadHolder = context.CurrentDiagram.GetObject<Diagram>().ActiveDiagramView;`  
  
 Můžete použít `uiThreadHolder.Invoke()` k provádění operací ve vlákně uživatelského rozhraní.  
  
## <a name="see-also"></a>Viz také  
 [Definování příkazu nabídky v diagramu modelování](../modeling/define-a-menu-command-on-a-modeling-diagram.md)   
 [Definování obslužné rutiny gest v diagramu modelování](../modeling/define-a-gesture-handler-on-a-modeling-diagram.md)



