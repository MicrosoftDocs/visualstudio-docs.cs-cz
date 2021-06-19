---
title: 'Postupy: Přístup k aktuálnímu výběru a jeho omezení'
description: Zjistěte, jak můžete určit, na který prvek uživatel klikl pravým tlačítkem při psaní obslužné rutiny příkazů nebo gest pro jazyk specifický pro vaši doménu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Domain-Specific Language, accessing the current selection
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 28d0f99743535965b3cf203d461fac5d0193607c
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2021
ms.locfileid: "112386602"
---
# <a name="how-to-access-and-constrain-the-current-selection"></a>Postupy: Přístup k aktuálnímu výběru a jeho omezení

Když píšete obslužnou rutinu příkazů nebo gest pro jazyk specifický pro doménu, můžete určit, na který prvek uživatel klikl pravým tlačítkem. Můžete také zabránit výběru některých tvarů nebo polí. Můžete například uspořádat, že když uživatel klikne na dekorátor ikon, místo toho se vybere tvar, který ho obsahuje. Omezením výběru tímto způsobem se sníží počet obslužných rutin, které musíte napsat. Usnadňuje to také uživateli, který může kliknout na libovolné místo ve tvaru, aniž by se museli vyhnout dekoratéru.

## <a name="access-the-current-selection-from-a-command-handler"></a>Přístup k aktuálnímu výběru z obslužné rutiny příkazu

Třída sady příkazů pro jazyk specifický pro doménu obsahuje obslužné rutiny příkazů pro vaše vlastní příkazy. Třída, ze které je odvozena třída sady příkazů pro jazyk specifický pro doménu, poskytuje několik členů pro přístup <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> k aktuálnímu výběru.

V závislosti na příkazu může obslužná rutina příkazu potřebovat výběr v návrháři modelů, v průzkumníku modelů nebo v aktivním okně.

### <a name="to-access-selection-information"></a>Přístup k informacím o výběru

1. Třída <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> definuje následující členy, které lze použít pro přístup k aktuálnímu výběru.

    |Člen|Description|
    |-|-|
    |Metoda <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsAnyDocumentSelectionCompartment%2A>|Vrátí hodnotu , pokud některý z `true` prvků vybraných v návrháři modelů má tvar přihrádky. V opačném případě `false` vrátí hodnotu .|
    |Metoda <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsDiagramSelected%2A>|Vrátí `true` hodnotu , pokud je diagram vybraný v návrháři modelů. V opačném případě vrátí hodnotu `false` .|
    |Metoda <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsSingleDocumentSelection%2A>|Vrátí hodnotu , pokud je v návrháři modelů vybrán právě `true` jeden prvek. V opačném případě `false` vrátí hodnotu .|
    |Metoda <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsSingleSelection%2A>|Vrátí hodnotu , pokud je v aktivním okně vybrán právě jeden prvek. V opačném případě vrátí hodnotu `true` `false` .|
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.CurrentDocumentSelection%2A> Vlastnost|Získá kolekci prvků vybraných v návrháři modelů jen pro čtení.|
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.CurrentSelection%2A> Vlastnost|Získá kolekci prvků vybraných v aktivním okně jen pro čtení.|
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.SingleDocumentSelection%2A> Vlastnost|Získá primární prvek výběru v návrháři modelů.|
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.SingleSelection%2A> Vlastnost|Získá primární prvek výběru v aktivním okně.|

2. Vlastnost třídy poskytuje přístup k objektu, který představuje okno návrháře modelů a poskytuje další přístup k vybraným <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet.CurrentDocView%2A> <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> <xref:Microsoft.VisualStudio.Modeling.Shell.DiagramDocView> prvkům v návrháři modelů.

3. Kromě toho vygenerovaný kód definuje vlastnost okna nástroje průzkumníka a vlastnost výběru průzkumníka ve třídě sady příkazů pro jazyk specifický pro doménu.

    - Vlastnost okna nástroje průzkumníka vrátí instanci třídy okna nástroje průzkumníka pro jazyk specifický pro doménu. Třída okna nástroje průzkumníka je odvozená z třídy a představuje průzkumníka modelů pro jazyk <xref:Microsoft.VisualStudio.Modeling.Shell.ModelExplorerToolWindow> specifický pro doménu.

    - Vlastnost `ExplorerSelection` vrátí vybraný prvek v okně Průzkumníka modelů pro jazyk specifický pro doménu.

## <a name="determine-which-window-is-active"></a>Určení, které okno je aktivní

Rozhraní <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService> obsahuje členy, které poskytují přístup k aktuálnímu stavu výběru v prostředí. Objekt můžete získat z třídy balíčku nebo třídy sady příkazů pro jazyk specifický pro doménu prostřednictvím vlastnosti definované v každé <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService> `MonitorSelection` základní třídě. Třída balíčku je odvozena z <xref:Microsoft.VisualStudio.Modeling.Shell.ModelingPackage> třídy a třída sady příkazů je odvozena z třídy <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> .

### <a name="to-determine-from-a-command-handler-what-type-of-window-is-active"></a>Určení typu okna, který je aktivní, z obslužné rutiny příkazu

1. Vlastnost třídy vrací objekt, který poskytuje přístup k <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.MonitorSelection%2A> <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService> aktuálnímu stavu výběru v prostředí.

2. Vlastnost rozhraní získá aktivní kontejner výběru, který se může <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService.CurrentSelectionContainer%2A> <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService> lišit od aktivního okna.

3. Přidejte následující vlastnosti do třídy sady příkazů pro jazyk specifický pro doménu, abyste zjistili, jaký typ okna je aktivní.

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

## <a name="constrain-the-selection"></a>Omezení výběru

Přidáním pravidel výběru můžete řídit, které prvky se vyberou, když uživatel vybere prvek v modelu. Pokud například chcete uživateli umožnit, aby s několika prvky zacloučil jednu jednotku, můžete použít pravidlo výběru.

### <a name="to-create-a-selection-rule"></a>Vytvoření pravidla výběru

1. Vytvoření vlastního souboru kódu v projektu DSL

2. Definujte třídu pravidla výběru odvozenou z <xref:Microsoft.VisualStudio.Modeling.Diagrams.DiagramSelectionRules> třídy .

3. Přepsáním <xref:Microsoft.VisualStudio.Modeling.Diagrams.DiagramSelectionRules.GetCompliantSelection%2A> metody třídy pravidla výběru použijte kritéria výběru.

4. Do souboru vlastního kódu přidejte částečnou definici třídy ClassDiagram.

     Třída je odvozena z třídy a je definována ve vygenerované souboru kódu `ClassDiagram` <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram> Diagram.cs v projektu DSL.

5. Přepište <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram.SelectionRules%2A> vlastnost třídy `ClassDiagram` tak, aby vracel vlastní pravidlo výběru.

     Výchozí implementace vlastnosti získá objekt pravidla <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram.SelectionRules%2A> výběru, který neupravuje výběr.

### <a name="example"></a>Příklad

Následující soubor kódu vytvoří pravidlo výběru, které rozbalí výběr tak, aby zahrnoval všechny instance jednotlivých tvarů domény, které byly původně vybrány.

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

## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet>
- <xref:Microsoft.VisualStudio.Modeling.Shell.ModelingPackage>
- <xref:Microsoft.VisualStudio.Modeling.Shell.DiagramDocView>
- <xref:Microsoft.VisualStudio.Modeling.Shell.ModelExplorerToolWindow>
- <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService>
- <xref:Microsoft.VisualStudio.Modeling.Diagrams.DiagramSelectionRules>
- <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram>