---
title: 'Postupy: Přístup k aktuálnímu výběru a jeho omezení'
description: Zjistěte, jak můžete určit, ke kterému prvku se uživatel klikne pravým tlačítkem, když napíšete obslužnou rutinu příkazu nebo gesta pro jazyk specifický pro doménu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Domain-Specific Language, accessing the current selection
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0ba656793b630dd55fc2ebc7242e5d45484b0f8e
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/12/2020
ms.locfileid: "97363390"
---
# <a name="how-to-access-and-constrain-the-current-selection"></a>Postupy: Přístup k aktuálnímu výběru a jeho omezení

Při psaní obslužné rutiny příkazu nebo gesta pro jazyk specifický pro doménu můžete určit, na který prvek uživatel klikne pravým tlačítkem myši. Můžete také zabránit výběru některých tvarů nebo polí. Můžete například určit, že když uživatel klikne na ikonu dekoratér, místo toho se vybere obrazec, který ho obsahuje. Omezení výběru tímto způsobem snižuje počet obslužných rutin, které je nutné zapsat. Také usnadňuje uživateli, který může kliknout kamkoli v obrazci bez nutnosti vyhnout se dekoratér.

## <a name="access-the-current-selection-from-a-command-handler"></a>Přístup k aktuálnímu výběru z obslužné rutiny příkazu

Třída sady příkazů pro jazyk specifický pro doménu obsahuje obslužné rutiny příkazu pro vlastní příkazy. <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet>Třída, ze které je odvozena třída sady příkazů pro jazyk specifický pro doménu, poskytuje několik členů pro přístup k aktuálnímu výběru.

V závislosti na příkazu může obslužná rutina příkazu potřebovat výběr v Návrháři modelů, Průzkumníku modelů nebo aktivním okně.

### <a name="to-access-selection-information"></a>Přístup k informacím o výběru

1. <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet>Třída definuje následující členy, které lze použít pro přístup k aktuálnímu výběru.

    |Člen|Popis|
    |-|-|
    |Metoda <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsAnyDocumentSelectionCompartment%2A>|Vrátí, `true` zda kterýkoli prvek vybraný v Návrháři modelů je tvar oddílu, jinak `false` .|
    |Metoda <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsDiagramSelected%2A>|Vrátí `true` , zda je diagram vybrán v Návrháři modelů; v opačném případě `false` .|
    |Metoda <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsSingleDocumentSelection%2A>|Vrátí, `true` zda je v Návrháři modelů vybrán právě jeden prvek; v opačném případě `false` .|
    |Metoda <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsSingleSelection%2A>|Vrátí, `true` zda je v aktivním okně vybrán právě jeden prvek; v opačném případě `false` .|
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.CurrentDocumentSelection%2A> majetek|Získá kolekci prvků, které jsou vybrány v Návrháři modelů, jen pro čtení.|
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.CurrentSelection%2A> majetek|Získá kolekci prvků, které jsou vybrány v aktivním okně, jen pro čtení.|
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.SingleDocumentSelection%2A> majetek|Získá primární prvek výběru v Návrháři modelů.|
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.SingleSelection%2A> majetek|Získá primární prvek výběru v aktivním okně.|

2. <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet.CurrentDocView%2A>Vlastnost <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> třídy poskytuje přístup k <xref:Microsoft.VisualStudio.Modeling.Shell.DiagramDocView> objektu, který představuje okno návrháře modelů a poskytuje další přístup k vybraným prvkům v Návrháři modelů.

3. Kromě toho generovaný kód definuje vlastnost okna Průzkumníka a vlastnost výběr Průzkumníka ve třídě sady příkazů pro jazyk specifický pro doménu.

    - Vlastnost okna nástroje Průzkumník vrací instanci třídy okna nástroje Průzkumník pro jazyk specifický pro doménu. Třída okna nástroje Průzkumník je odvozena z <xref:Microsoft.VisualStudio.Modeling.Shell.ModelExplorerToolWindow> třídy a představuje Průzkumníka modelů pro jazyk specifický pro doménu.

    - `ExplorerSelection`Vlastnost vrací vybraný prvek v okně Průzkumníka modelů pro jazyk specifický pro doménu.

## <a name="determine-which-window-is-active"></a>Určit, které okno je aktivní

<xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService>Rozhraní obsahuje definice členů, kteří poskytují přístup k aktuálnímu stavu výběru v prostředí. Objekt můžete získat <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService> buď z třídy balíčku, nebo z třídy sady příkazů pro jazyk specifický pro doménu prostřednictvím `MonitorSelection` vlastnosti definované v základní třídě každého. Třída balíčku je odvozena z <xref:Microsoft.VisualStudio.Modeling.Shell.ModelingPackage> třídy a třída sady příkazů je odvozena od <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> třídy.

### <a name="to-determine-from-a-command-handler-what-type-of-window-is-active"></a>Určení z obslužné rutiny příkazu, který typ okna je aktivní

1. <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.MonitorSelection%2A>Vlastnost <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> třídy vrátí <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService> objekt, který poskytuje přístup k aktuálnímu stavu výběru v prostředí.

2. <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService.CurrentSelectionContainer%2A>Vlastnost <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService> rozhraní získá aktivní kontejner výběru, který se může lišit od aktivního okna.

3. Přidejte následující vlastnosti do třídy sady příkazů pro jazyk specifický pro doménu, abyste určili, jaký typ okna je aktivní.

    ```csharp
    // using Microsoft.VisualStudio.Modeling.Shell;

    // Returns true if the model designer is the active selection container;
    // otherwise, false.
    protected bool IsDesignerActive
    {
        get
        {
            return (this.MonitorSelection.CurrentSelectionContainer
                is DiagramDocView);
        }
    }

    // Returns true if the model explorer is the active selection container;
    // otherwise, false.
    protected bool IsExplorerActive
    {
        get
        {
            return (this.MonitorSelection.CurrentSelectionContainer
                is ModelExplorerToolWindow);
        }
    }
    ```

## <a name="constrain-the-selection"></a>Omezit výběr

Přidáním pravidel výběru můžete řídit, které prvky jsou vybrány, když uživatel vybere prvek v modelu. Pokud například chcete, aby uživatel mohl zacházet s několika prvky jako s jednou jednotkou, můžete použít pravidlo výběru.

### <a name="to-create-a-selection-rule"></a>Vytvoření pravidla výběru

1. Vytvoření vlastního souboru kódu v projektu DSL

2. Definujte třídu pravidla výběru, která je odvozena od <xref:Microsoft.VisualStudio.Modeling.Diagrams.DiagramSelectionRules> třídy.

3. Přepsat <xref:Microsoft.VisualStudio.Modeling.Diagrams.DiagramSelectionRules.GetCompliantSelection%2A> metodu třídy pravidla výběru, aby bylo možné použít kritéria výběru.

4. Přidejte do vlastního souboru kódu definici částečné třídy pro třídu ClassDiagram.

     `ClassDiagram`Třída je odvozena z <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram> třídy a je definována v souboru generovaného kódu diagram.cs v projektu DSL.

5. Přepište <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram.SelectionRules%2A> vlastnost `ClassDiagram` třídy tak, aby vracela vlastní pravidlo výběru.

     Výchozí implementace <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram.SelectionRules%2A> vlastnosti získá objekt pravidla výběru, který neupravuje výběr.

### <a name="example"></a>Příklad

Následující soubor kódu vytvoří pravidlo výběru, které rozšíří výběr tak, aby zahrnoval všechny instance všech původně vybraných obrazců domény.

```csharp
using System;
using System.Collections.Generic;
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;

namespace CompanyName.ProductName.GroupingDsl
{
    public class CustomSelectionRules : DiagramSelectionRules
    {
        protected Diagram diagram;
        protected IElementDirectory elementDirectory;

        public CustomSelectionRules(Diagram diagram)
        {
            if (diagram == null) throw new ArgumentNullException();

            this.diagram = diagram;
            this.elementDirectory = diagram.Store.ElementDirectory;
        }

        /// <summary>Called by the design surface to allow selection filtering.
        /// </summary>
        /// <param name="currentSelection">[in] The current selection before any
        /// ShapeElements are added or removed.</param>
        /// <param name="proposedItemsToAdd">[in/out] The proposed DiagramItems to
        /// be added to the selection.</param>
        /// <param name="proposedItemsToRemove">[in/out] The proposed DiagramItems
        /// to be removed from the selection.</param>
        /// <param name="primaryItem">[in/out] The proposed DiagramItem to become
        /// the primary DiagramItem of the selection. A null value signifies that
        /// the last DiagramItem in the resultant selection should be assumed as
        /// the primary DiagramItem.</param>
        /// <returns>true if some or all of the selection was accepted; false if
        /// the entire selection proposal was rejected. If false, appropriate
        /// feedback will be given to the user to indicate that the selection was
        /// rejected.</returns>
        public override bool GetCompliantSelection(
            SelectedShapesCollection currentSelection,
            DiagramItemCollection proposedItemsToAdd,
            DiagramItemCollection proposedItemsToRemove,
            DiagramItem primaryItem)
        {
            if (currentSelection.Count == 0 && proposedItemsToAdd.Count == 0) return true;

            HashSet<DomainClassInfo> itemsToAdd = new HashSet<DomainClassInfo>();

            foreach (DiagramItem item in proposedItemsToAdd)
            {
                if (item.Shape != null)
                    itemsToAdd.Add(item.Shape.GetDomainClass());
            }
            proposedItemsToAdd.Clear();
            foreach (DomainClassInfo classInfo in itemsToAdd)
            {
                foreach (ModelElement element
                    in this.elementDirectory.FindElements(classInfo, false))
                {
                    if (element is ShapeElement)
                    {
                        proposedItemsToAdd.Add(
                            new DiagramItem((ShapeElement)element));
                    }
                }
            }

            return true;
        }
    }

    public partial class ClassDiagram
    {
        protected CustomSelectionRules customSelectionRules = null;

        protected bool multipleSelectionMode = true;

        public override DiagramSelectionRules SelectionRules
        {
            get
            {
                if (multipleSelectionMode)
                {
                    if (customSelectionRules == null)
                    {
                        customSelectionRules = new CustomSelectionRules(this);
                    }
                    return customSelectionRules;
                }
                else
                {
                    return base.SelectionRules;
                }
            }
        }
    }
}
```

## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet>
- <xref:Microsoft.VisualStudio.Modeling.Shell.ModelingPackage>
- <xref:Microsoft.VisualStudio.Modeling.Shell.DiagramDocView>
- <xref:Microsoft.VisualStudio.Modeling.Shell.ModelExplorerToolWindow>
- <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService>
- <xref:Microsoft.VisualStudio.Modeling.Diagrams.DiagramSelectionRules>
- <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram>