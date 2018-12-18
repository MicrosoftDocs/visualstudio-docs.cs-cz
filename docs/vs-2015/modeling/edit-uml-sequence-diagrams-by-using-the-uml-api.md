---
title: Úpravy sekvenčních diagramů UML pomocí rozhraní API UML | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- UML activity diagrams, programming
ms.assetid: 8cdd0203-85ef-4c62-9abc-da4cb26fa504
caps.latest.revision: 27
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: f68cf87a7f45b906c6de43e0a837d49132b7a3e0
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51725563"
---
# <a name="edit-uml-sequence-diagrams-by-using-the-uml-api"></a>Úpravy sekvenčních diagramů UML pomocí rozhraní API UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Interakce je posloupnost zpráv mezi sadu životností. Interakce se zobrazí v sekvenčním diagramu UML.  
  
 Úplné podrobnosti o rozhraní API najdete v části <xref:Microsoft.VisualStudio.Uml.Interactions?displayProperty=fullName>.  
  
 Další obecné Úvod k psaní příkazů a obslužné rutiny gesta pro UML diagramů naleznete v tématu [definování příkazu nabídky v diagramu modelování](../modeling/define-a-menu-command-on-a-modeling-diagram.md).  
  
## <a name="basic-code"></a>Základní kód  
  
### <a name="namespace-imports"></a>Importuje Namespace  
 Musí zahrnovat následující `using` příkazy:  
  
```  
using Microsoft.VisualStudio.Uml.Classes;  
   // for basic UML types such as IPackage  
using Microsoft.VisualStudio.Uml.Interactions;  
   // for interaction types  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;  
   // to create elements and use additional functions  
```  
  
 Pokud vytváříte příkazy a obslužnými rutinami gest, budete také potřebovat:  
  
```  
using System.ComponentModel.Composition;   
   // for Import and Export  
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;  
   // for ICommandExtension  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;  
   // for diagrams and context  
```  
  
 Další informace najdete v tématu [definování příkazu nabídky v diagramu modelování](../modeling/define-a-menu-command-on-a-modeling-diagram.md).  
  
### <a name="getting-the-context"></a>Získání kontextu  
 Pokud upravujete interakce v rámci obslužné rutiny příkazu nebo gesta v sekvenčním diagramu, můžete získat odkaz na kontextu. Příklad:  
  
```  
[SequenceDesignerExtension]  
[Export(typeof(ICommandExtension))]    
public class MySequenceDiagramCommand : ICommandExtension  
{  
    [Import]  
    public IDiagramContext Context { get; set; }  
    public void QueryStatus (IMenuCommand command)  
    {  
      ISequenceDiagram sequenceDiagram =   
          Context.CurrentDiagram as ISequenceDiagram;  
         ...  
```  
  
### <a name="generated-and-uml-sequence-diagrams"></a>Generuje a diagramů UML pořadí  
 Existují dva druhy sekvenční diagramy: ty, které jsou ručně vytvořeny v projektu modelování UML a ty, které byly generovány z programového kódu. Použití `UmlMode` vlastnost ke zjišťování, které sekvence diagramu můžete mít.  
  
> [!NOTE]
>  Tato vlastnost vrátí hodnotu false pouze pro sekvenční diagramy generované z kódu pomocí sady Visual Studio 2013 nebo starší. To zahrnuje kód generovaný pořadí diagramy migrovat z 2013 a starší. Tato verze sady Visual Studio nepodporuje, generuje se nový sekvenční diagramy.  
  
 Například, pokud chcete provést příkaz nabídky, která se zobrazí pouze na sekvenční diagramy UML pak bude `QueryStatus()` metoda může zahrnovat následující příkaz:  
  
```  
command.Enabled = command.Visible =   
      sequenceDiagram != null && sequenceDiagram.UmlMode;  
```  
  
 Na generovaného sekvenčního diagramu, životností, zpráv a další prvky jsou většinou stejné jako v sekvenčním diagramu UML. V modelu UML Model Store má kořenový adresář, který je Model, který vlastní všem ostatním prvkům. Ale v Store svůj vlastní Model, který má hodnotu null kořenové existuje generovaného interakce:  
  
```  
IModel rootModel = sequenceDiagram.ModelStore.Root;  
    // !sequenceDiagram.UmlMode == (rootModel == null)  
```  
  
## <a name="to-create-and-display-an-interaction"></a>Vytvoření a zobrazení interakce  
 Vytvořte interakce jako podřízený objekt balíčku nebo modelu.  
  
 Například pokud vyvíjíte příkaz, který může být proveden na prázdný sekvenční diagram, by měla vždy začnete tak, že zkontrolujete, jestli existuje interakce.  
  
```  
public void Execute (IMenuCommand command)  
{  
    ISequenceDiagram sequenceDiagram =   
         Context.CurrentDiagram as ISequenceDiagram;  
    if (sequenceDiagram == null) return;  
    // Get the diagram's interaction:  
    IInteraction interaction = sequenceDiagram.Interaction;  
    // A new sequence diagram might have no interaction:  
    if (interaction == null)  
    {  
       // Get the home package or model of the diagram:  
       IPackage parentPackage = sequenceDiagram.GetObject<IPackage>();  
       interaction = parentPackage.CreateInteraction();  
       // Display the interaction on the sequence diagram:  
       sequenceDiagram.Bind(interaction);  
    }   
```  
  
## <a name="updating-an-interaction-and-its-layout"></a>Aktualizuje se interakce a její rozložení  
 Při aktualizaci interakci vždy ukončit operaci aktualizací rozložení pomocí jedné z následujících metod:  
  
- `ISequenceDiagram.UpdateShapePositions()` Upraví pozice tvary, které nedávno bylo vloženo nebo přesunout a jejich sousedních tvarů.  
  
- `ISequenceDiagram.Layout([SequenceDiagramLayoutKinds])` Překreslí celý diagram. Parametr slouží k určení přemístění životnosti nebo zprávy.  
  
  To je zvlášť důležité při vložení nových elementů nebo přesunout existující prvky. Nebudou do správné polohy v diagramu, dokud jste provedli jednu z těchto operací. Potřebujete pouze volání jednoho z těchto operací jednou na konci řady změn.  
  
  Chcete-li zabránit bemusing uživatel, který provádí vrácení zpět po příkazu, použijte `ILinkedUndoTransaction` uzavřete změny a finální `Layout()` nebo `UpdateShapePositions()` operace. Příklad:  
  
```  
using (ILinkedUndoTransaction transaction = LinkedUndoContext.BeginTransaction("create loop"))  
{  
  Interaction.CreateCombinedFragment(InteractionOperatorKind.Loop, messages);  
  Diagram.UpdateShapePositions();  
  transaction.Commit();  
}  
```  
  
 Použití `ILinkedUndoTransaction`, je třeba tuto deklaraci ve své třídě:  
  
```  
[Import] ILinkedUndoContext LinkedUndoContext { get; set; }  
```  
  
 Další informace najdete v tématu [UML propojení aktualizací modelů pomocí transakcí](../modeling/link-uml-model-updates-by-using-transactions.md).  
  
## <a name="building-an-interaction"></a>Vytváření interakce  
  
### <a name="to-create-lifelines"></a>Chcete-li vytvořit životnosti  
  
```  
ILifeline lifeline = interaction.CreateLifeline();  
```  
  
 Životnost představuje umožňující připojení k elementu, to znamená, že instance typu. Například pokud interakce se používá k zobrazení, jak komponenty deleguje příchozí zprávy do jeho vnitřních částí, životnosti může představovat portů a součást:  
  
```  
foreach (IConnectableElement part in   
            component.Parts  
           .Concat<IConnectableElement>(component.OwnedPorts))  
{  
   ILifeline lifeline = interaction.CreateLifeline();  
   lifeline.Represents = part;  
}  
```  
  
 Případně, pokud interakce ukazuje libovolného sadu objektů, můžete vytvořit vlastnost nebo jiné `IConnectableElement` interakce sama:  
  
```  
ILifeline lifeline = interaction.CreateLifeline();  
IProperty property1 = interaction.CreateProperty();  
property1.Type = model.CreateInterface();  
property1.Type.Name = "Type 1";  
lifeline.Represents = property1;  
```  
  
 Jako další alternativu můžete nastavit název a typ životnosti bez odkazu na prvek umožňující připojení k:  
  
```  
ILifeline lifeline = interaction.CreateLifeline();  
lifeline.Name = "c1";  
lifeline.SetInstanceType("Customer");  
System.Diagnostics.Debug.Assert(  
           lifeline.GetDisplayName() == "c1:Customer"  );  
```  
  
### <a name="to-create-messages"></a>Chcete-li vytvořit zprávy  
 K vytvoření zprávy, musí identifikovat body vložení v rámci životnosti zdroj a cíl. Příklad:  
  
```  
interaction.CreateMessage( sourceInsertionPoint,   
                           targetInsertionPoint,   
                           MessageKind.Complete,   
                           MessageSort.ASynchCall)  
```  
  
 K vytvoření zprávy, která má Nedefinovaný zdroj nebo cíl nedefinované:  
  
```  
interaction.CreateLostFoundMessage(MessageKind.Found, insertionPoint);  
```  
  
 Existuje několik zpráv, které vám umožní identifikovat body vložení vůbec klíčové body na životnost:  
  
|Metoda ILifeline|Použijte ho k vložení v tomto okamžiku|  
|-------------------------|------------------------------------|  
|`FindInsertionPointAtTop()`|Horní životnost.|  
|`FindInsertionPointAtBottom()`|Konec životnosti.|  
|`FindInsertionPointAfterMessage`<br /><br /> `(IMessage previous)`|Bod okamžitě po určenou zprávu.|  
|`FindInsertionPointAfterExecutionSpecification`<br /><br /> `(IExecutionSpecification previous)`|Bod může být na životnost, nebo na nadřazený blok specifikace spuštění.|  
|`FindInsertionPointAfterInteractionUse`<br /><br /> `(IInteractionUse previous)`|Bod, následující použitím interakce.|  
|`FindInsertionPointAfterCombinedFragment`<br /><br /> `(ICombinedFragment previous)`|Bod, následující Fragment kombinovat.|  
|`FindInsertionPoint(IExecutionSpecification block)`|Na začátek bloku spuštění.|  
|`FindInsertionPoint(IInteractionOperand fragment)`|Horní operand kombinovaného fragmentu.|  
  
 Při vytváření zprávy, pečlivě Vyhněte se definování zprávu, která by překřížila další zprávu.  
  
### <a name="to-create-combined-fragments-and-interaction-uses"></a>Vytvoření kombinované fragmenty a interakce používá  
 Kombinované fragmenty a interakce používá můžete vytvořit tak, že určíte bod vložení na každé životnosti, musí být pokryté komponentami elementu. Snažte se vyhnout zadávání sadu body, které by překřížila existující zprávu nebo fragment.  
  
```  
Interaction.CreateCombinedFragment(InteractionOperatorKind.Loop,   
  Interaction.Lifelines.Select(lifeline => lifeline.FindInsertionPointAtTop()));  
Interaction.CreateInteractionUse(  
  Interaction.Lifelines.Select(lifeline => lifeline.FindInsertionPointAtTop()));  
```  
  
 Můžete také vytvořit kombinovaného fragmentu, která zahrnuje existující sadu zpráv. Všechny zprávy musí zdroj na stejné životnosti nebo provedení bloku.  
  
```  
ICombinedFragment cf = Interaction.CreateCombinedFragment(  
  InteractionOperatorKind.Loop,  
  Interaction.Lifelines.First().GetAllOutgoingMessages());  
```  
  
 Do kombinovaného fragmentu je vytvořen vždy pomocí jediného operandu. K vytvoření nové operandu, je nutné zadat existující operand, který chcete vložit před nebo po a zda chcete vložit za něj nebo před ní:  
  
```  
// Create an additional operand before the first  
cf.CreateInteractionOperand(cf.Operands.First(), false);  
// Create an additional operand after the last:  
cf.CreateInteractionOperand(cf.Operands.Last(), true);  
```  
  
## <a name="troubleshooting"></a>Poradce při potížích  
 Obrazce se zobrazí v nesprávné pozici v případě změny nebyly dokončeny s `UpdateShapePositions()` nebo `Layout()` operace.  
  
 Většina jiných problémy jsou způsobené právě chybně zarovnaných, tak, aby nové zprávy nebo fragmenty byste museli překřížila ostatní body vložení. Příznaky může být, že je provedena žádná změna, nebo dojde k výjimce. Nemusí být vyvolána výjimka, dokud `UpdateShapePositions()` nebo `Layout()` proběhlo.  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualStudio.Uml.Interactions?displayProperty=fullName>   
 [Rozšíření modelů a diagramů UML](../modeling/extend-uml-models-and-diagrams.md)   
 [Definování příkazu nabídky v diagramu modelování](../modeling/define-a-menu-command-on-a-modeling-diagram.md)   
 [Definování vlastní položky sady nástrojů pro modelování](../modeling/define-a-custom-modeling-toolbox-item.md)   
 [Definování omezení ověření pro modely UML](../modeling/define-validation-constraints-for-uml-models.md)   
 [Programování pomocí rozhraní API UML](../modeling/programming-with-the-uml-api.md)



