---
title: 'Postupy: přístup a jeho omezení aktuální výběr | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language, accessing the current selection
ms.assetid: 2990981e-dfae-416f-b0d0-7197f1242dfa
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: ec8ff7ae0b0e006528b11604f54dc74170857cf7
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49187569"
---
# <a name="how-to-access-and-constrain-the-current-selection"></a>Postupy: Přístup k aktuálnímu výběru a jeho omezení
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Při napsat obslužnou rutinu příkazu nebo gesta jazyka specifického pro doménu, můžete určit, jaký element klikli pravým tlačítkem myši uživatele. Můžete také zabránit nějaké obrazce nebo pole výběru. Například můžete uspořádat, že když uživatel klikne ikonu dekoratér, na tvar, který ji obsahuje je místo toho se vybere. Omezení výběru tímto způsobem snižuje počet obslužných rutin, které musíte napsat. Také usnadňuje pro uživatele, který můžete kliknout na kdekoli ve tvaru bez nutnosti vyhnout dekoratér.  
  
## <a name="accessing-the-current-selection-from-a-command-handler"></a>Přístup k aktuálním výběru z obslužná rutina příkazu  
 Třída set příkazu jazyka specifického pro doménu obsahuje obslužné rutiny příkazů pro vaše vlastní příkazy. <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> Třída, ze kterého je odvozena třída set příkazu jazyka specifického pro doménu, poskytuje několik členů pro přístup k aktuálnímu výběru.  
  
 V závislosti na příkazu, který může být nutné obslužná rutina příkazu výběru v Návrháři modelů, Průzkumníka modelů nebo aktivní okno.  
  
#### <a name="to-access-selection-information"></a>Přístup k informacím výběr  
  
1.  <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> Třída definuje následující členy, které lze použít pro přístup k aktuálnímu výběru.  
  
    |Člen|Popis|  
    |------------|-----------------|  
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsAnyDocumentSelectionCompartment%2A> – Metoda|Vrátí `true` Pokud některý z prvků vybraných v Návrháři modelů obrazce oddílu; v opačném případě `false`.|  
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsDiagramSelected%2A> – Metoda|Vrátí `true` Pokud diagramu je vybrané v Návrháři modelů; v opačném případě `false`.|  
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsSingleDocumentSelection%2A> – Metoda|Vrátí `true` Pokud právě jeden element je vybrané v Návrháři modelů; v opačném případě `false`.|  
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsSingleSelection%2A> – Metoda|Vrátí `true` Pokud právě jeden element je vybrané v aktivní okno; v opačném případě `false`.|  
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.CurrentDocumentSelection%2A> Vlastnost|Získá kolekci prvků vybraných v Návrháři modelů jen pro čtení.|  
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.CurrentSelection%2A> Vlastnost|Získá kolekci prvků vybraných v aktivní okno jen pro čtení.|  
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.SingleDocumentSelection%2A> Vlastnost|Získá prvek primární výběru v Návrháři modelů.|  
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.SingleSelection%2A> Vlastnost|Získá prvek primární výběru aktivního okna.|  
  
2.  <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet.CurrentDocView%2A> Vlastnost <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> třídě poskytuje přístup k <xref:Microsoft.VisualStudio.Modeling.Shell.DiagramDocView> objekt, který představuje okno návrháře modelů a poskytuje další přístup vybraných elementů v Návrháři modelů.  
  
3.  Kromě toho generovaný kód definuje vlastnost okno Průzkumníka nástroj a na vlastnost výběr explorer v příkazu set – třída jazyka specifického pro doménu.  
  
    -   Vlastnost okno nástroje Průzkumník vrací instanci třídy okna nástroje Průzkumník jazyka specifického pro doménu. Je odvozena z třídy okna Průzkumníka nástroj <xref:Microsoft.VisualStudio.Modeling.Shell.ModelExplorerToolWindow> třídy a představuje Průzkumníka modelů pro jazyka specifického pro doménu.  
  
    -   `ExplorerSelection` Vlastnost vrací vybraného prvku v okně Průzkumníka modelu pro jazyka specifického pro doménu.  
  
## <a name="determining-which-window-is-active"></a>Určení, které okno je aktivní  
 <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService> Obsahuje rozhraní definuje členy, které poskytují přístup k aktuálnímu stavu výběru v prostředí. Můžete získat <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService> objekt z balíčku třídu nebo třídu příkazu set pro jazyka specifického pro doménu prostřednictvím `MonitorSelection` definovanou v základní třídě pro každou z vlastností. Je odvozena z třídy balíčku <xref:Microsoft.VisualStudio.Modeling.Shell.ModelingPackage> třídy a třídy příkazu set je odvozen od <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> třídy.  
  
#### <a name="to-determine-from-a-command-handler-what-type-of-window-is-active"></a>K určení z obslužná rutina příkazu, jaký typ okna je aktivní  
  
1.  <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.MonitorSelection%2A> Vlastnost <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> třídy vrátí <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService> objekt, který poskytuje přístup k aktuální stav výběru v prostředí.  
  
2.  <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService.CurrentSelectionContainer%2A> Vlastnost <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService> rozhraní získá kontejner aktivního výběru, který se může lišit od aktivního okna.  
  
3.  Přidejte že následující vlastnosti pro příkaz set – třída za vás jazyka specifického pro doménu k určení, jaký typ okna je aktivní.  
  
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
  
## <a name="constraining-the-selection"></a>Omezení výběru  
 Přidáním výběr pravidel můžete řídit prvky, které jsou vybrané, když uživatel vybere elementu v modelu. Povolit uživateli považovat za jednu jednotku počet prvků, například můžete použít pravidlo výběru.  
  
#### <a name="to-create-a-selection-rule"></a>Chcete-li vytvořit pravidlo výběru  
  
1.  Vytvořte soubor vlastní kód v projektu DSL  
  
2.  Definice, která je odvozena z třídy pravidlo výběru <xref:Microsoft.VisualStudio.Modeling.Diagrams.DiagramSelectionRules> třídy.  
  
3.  Přepsat <xref:Microsoft.VisualStudio.Modeling.Diagrams.DiagramSelectionRules.GetCompliantSelection%2A> metoda třídy pravidlo výběru použít kritéria pro výběr.  
  
4.  Přidáte definici částečné třídy pro třídu ClassDiagram do souboru vlastního kódu.  
  
     `ClassDiagram` Třída odvozena z <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram> třídy a je definován v generovaném kódu souboru Diagram.cs, v projektu DSL.  
  
5.  Přepsat <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram.SelectionRules%2A> vlastnost `ClassDiagram` třídy k vrácení pravidla vlastního výběru.  
  
     Výchozí implementace <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram.SelectionRules%2A> vlastnost získá objekt výběru pravidel, který neprovede žádné změny výběru.  
  
### <a name="example"></a>Příklad  
 Následující soubor kódu vytvoří pravidlo výběru, který rozbalí výběru zahrnout všechny instance každé domény obrazce, které jste zpočátku vybrali.  
  
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
 <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet>   
 <xref:Microsoft.VisualStudio.Modeling.Shell.ModelingPackage>   
 <xref:Microsoft.VisualStudio.Modeling.Shell.DiagramDocView>   
 <xref:Microsoft.VisualStudio.Modeling.Shell.ModelExplorerToolWindow>   
 <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService>   
 <xref:Microsoft.VisualStudio.Modeling.Diagrams.DiagramSelectionRules>   
 <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram>



