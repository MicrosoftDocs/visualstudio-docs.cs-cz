---
title: Aktualizace modelu UML z vlákna na pozadí | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 42c06b0b-b681-4e19-b5f3-6116dd2a4072
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9e6626faa09f1e38506c2d205d13caa9a3707fc0
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72659469"
---
# <a name="update-a-uml-model-from-a-background-thread"></a>Aktualizace modelu UML z vlákna na pozadí
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V některých případech může být užitečné provést změny modelu ve vlákně na pozadí. Například pokud načítáte informace z pomalého externího prostředku, můžete použít vlákno na pozadí pro dohled nad aktualizacemi. To uživateli umožňuje zobrazit každou aktualizaci hned, jak se stane.

 Je však nutné si uvědomit, že úložiště UML není bezpečné pro přístup z více vláken. Důležitá jsou následující opatření:

- Každá aktualizace modelu nebo diagramu se musí provádět ve vlákně uživatelského rozhraní (UI). Vlákno na pozadí musí použít <xref:System.Windows.Forms.Control.Invoke%2A> nebo `Dispatcher.` <xref:System.Windows.Threading.Dispatcher.Invoke%2A>, aby vlákno uživatelského rozhraní provádělo skutečné aktualizace.

- Pokud seskupete řadu změn do jediné transakce, doporučujeme, abyste uživatelům zabránili v úpravách modelu v době, kdy transakce probíhá. V opačném případě všechny úpravy provedené uživatelem se stanou součástí stejné transakce. Uživateli můžete zabránit v provádění změn zobrazením modálního dialogového okna. Pokud chcete, můžete v dialogovém okně zadat tlačítko zrušit. Uživatel uvidí změny, když k nim dojde.

## <a name="example"></a>Příklad
 Tento příklad používá vlákno na pozadí k provedení několika změn modelu. Dialogové okno se používá k vyloučení uživatele v době, kdy je vlákno spuštěno. V tomto jednoduchém příkladu není v dialogovém okně k dispozici žádné tlačítko Storno. Tuto funkci byste ale mohli snadno přidat.

#### <a name="to-run-the-example"></a>Chcete-li spustit příklad

1. Vytvořte obslužnou rutinu příkazu v C# projektu, jak je popsáno v tématu [Definování příkazu nabídky v diagramu modelování](../modeling/define-a-menu-command-on-a-modeling-diagram.md).

2. Ujistěte se, že projekt obsahuje odkazy na tato sestavení:

   - Microsoft. VisualStudio. ArchitectureTools. rozšiřitelnost

   - Microsoft. VisualStudio. Modeling. SDK. znění

   - Microsoft. VisualStudio. Modeling. SDK. Diagrams. znění

   - Microsoft. VisualStudio. Uml. Interfaces

   - System. ComponentModel. složení

   - System. Windows. Forms

3. Přidejte do projektu formulář Windows s názvem **ProgressForm**. Měla by se zobrazit zpráva s oznámením, že probíhá aktualizace. Nemusí mít žádné další ovládací prvky.

4. Přidejte C# soubor, který obsahuje kód, který se zobrazí po kroku 7.

5. Sestavte a spusťte projekt.

    Nová instance [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] začne v experimentálním režimu.

6. Vytvořte nebo otevřete diagram tříd UML v experimentální instanci [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

7. Klikněte pravým tlačítkem myši kdekoli v diagramu tříd UML a pak klikněte na **přidat několik tříd UML**.

   Několik nových polí třídy se zobrazí v diagramu, jeden po druhém v intervalech po půl sekundách.

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

#### <a name="to-allow-the-user-to-cancel-the-thread-in-the-example"></a>Umožnění uživateli zrušit vlákno v příkladu

1. Přidejte tlačítko Storno do dialogového okna průběhu.

2. Do dialogového okna průběh přidejte následující kód:

     `public event MethodInvoker Cancel;`

     `private void CancelButton_Click(object sender, EventArgs e)`

     `{`

     `Cancel();`

     `}`

3. V metodě Execute () vložte tento řádek po konstrukci formuláře:

     `form.Cancel += delegate() { worker.CancelAsync(); };`

### <a name="other-methods-of-accessing-the-ui-thread"></a>Další metody přístupu ke vláknu uživatelského rozhraní
 Pokud nechcete vytvořit dialogové okno, můžete získat přístup k ovládacímu prvku, který zobrazí diagram:

 `DiagramView uiThreadHolder = context.CurrentDiagram.GetObject<Diagram>().ActiveDiagramView;`

 Můžete použít `uiThreadHolder.Invoke()` k provádění operací ve vlákně uživatelského rozhraní.

## <a name="see-also"></a>Viz také
 [Definování příkazu nabídky v diagramu modelování](../modeling/define-a-menu-command-on-a-modeling-diagram.md) [Definování obslužné rutiny gesta v diagramu modelování](../modeling/define-a-gesture-handler-on-a-modeling-diagram.md)
