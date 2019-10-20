---
title: Úprava sekvenčních diagramů UML pomocí rozhraní API UML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML activity diagrams, programming
ms.assetid: 8cdd0203-85ef-4c62-9abc-da4cb26fa504
caps.latest.revision: 27
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: cbc7a6ce7edede6759c0562df1e524d932f62b91
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72669715"
---
# <a name="edit-uml-sequence-diagrams-by-using-the-uml-api"></a>Úpravy sekvenčních diagramů UML pomocí rozhraní API UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Interakce je posloupnost zpráv mezi sadou životností. Interakce se zobrazí v sekvenčním diagramu UML.

 Úplné podrobnosti o rozhraní API naleznete v tématu [Microsoft. VisualStudio. Uml. interakcí](/previous-versions/dd493373(v=vs.140)).

 Obecnější Úvod do psaní příkazů a obslužných rutin gest pro diagramy UML najdete v tématu věnovaném [Definování příkazu nabídky v diagramu modelování](../modeling/define-a-menu-command-on-a-modeling-diagram.md).

## <a name="basic-code"></a>Základní kód

### <a name="namespace-imports"></a>Importy oboru názvů
 Musíte zahrnout následující příkazy `using`:

```
using Microsoft.VisualStudio.Uml.Classes;
   // for basic UML types such as IPackage
using Microsoft.VisualStudio.Uml.Interactions;
   // for interaction types
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;
   // to create elements and use additional functions
```

 Pokud vytváříte příkazy nabídky a obslužné rutiny gest, budete také potřebovat:

```
using System.ComponentModel.Composition;
   // for Import and Export
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;
   // for ICommandExtension
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;
   // for diagrams and context
```

 Další informace najdete v tématu [Definování příkazu nabídky v diagramu modelování](../modeling/define-a-menu-command-on-a-modeling-diagram.md).

### <a name="getting-the-context"></a>Získání kontextu
 Pokud upravujete interakci jako součást obslužné rutiny příkazu nebo gesta v sekvenčním diagramu, můžete získat odkaz na kontext. Příklad:

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

### <a name="generated-and-uml-sequence-diagrams"></a>Vygenerované a sekvenční diagramy UML
 Existují dva druhy sekvenčních diagramů: ty, které jsou ručně vytvořeny v projektu modelování UML, a ty, které byly generovány z programového kódu. Pomocí vlastnosti `UmlMode` můžete zjistit, který sekvenční diagram máte.

> [!NOTE]
> Tato vlastnost vrátí hodnotu false pouze pro sekvenční diagramy vygenerované z kódu pomocí Visual Studio 2013 a předchozích. To zahrnuje sekvenční diagramy generované kódem z 2013 a starších verzí. Tato verze sady Visual Studio nepodporuje generování nových sekvenčních diagramů.

 Například pokud chcete vytvořit příkaz nabídky, který je viditelný pouze v sekvenčních diagramech UML, může metoda `QueryStatus()` obsahovat následující příkaz:

```
command.Enabled = command.Visible =
      sequenceDiagram != null && sequenceDiagram.UmlMode;
```

 U generovaného sekvenčního diagramu jsou životnosti, zprávy a další prvky většinou stejné jako u sekvenčního diagramu UML. V modelu UML má úložiště modelu kořen, což je model, který je vlastníkem všech ostatních prvků. Ale vytvořená interakce existuje ve vlastním úložišti modelu, které má kořen null:

```
IModel rootModel = sequenceDiagram.ModelStore.Root;
    // !sequenceDiagram.UmlMode == (rootModel == null)
```

## <a name="to-create-and-display-an-interaction"></a>Vytvoření a zobrazení interakce
 Vytvořte interakci jako podřízenou položku balíčku nebo modelu.

 Například při vývoji příkazu, který může být proveden v prázdném sekvenčním diagramu, byste měli vždy začít tím, že zkontrolujete, zda interakce existuje.

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

## <a name="updating-an-interaction-and-its-layout"></a>Aktualizace interakce a jejího rozložení
 Když aktualizujete interakci, vždy ukončete operaci tím, že aktualizujete její rozložení, a to pomocí jedné z následujících metod:

- `ISequenceDiagram.UpdateShapePositions()` upravuje pozice obrazců, které byly v poslední době vloženy nebo přesunuty, a jejich sousední obrazce.

- `ISequenceDiagram.Layout([SequenceDiagramLayoutKinds])` překreslí celý diagram. Parametr můžete použít k určení přemístění životností, zpráv nebo obojího.

  To je obzvláště důležité, pokud vložíte nové prvky nebo přesunete existující prvky. Dokud neprovedete jednu z těchto operací, nebudou ve správném umístění v diagramu. Jednu z těchto operací je třeba volat pouze jednou na konci řady změn.

  Abyste se vyhnuli bemusing uživateli, který po příkazu provede vrácení zpět, použijte `ILinkedUndoTransaction` k uzavření změn a konečných `Layout()` nebo `UpdateShapePositions()` operací. Příklad:

```
using (ILinkedUndoTransaction transaction = LinkedUndoContext.BeginTransaction("create loop"))
{
  Interaction.CreateCombinedFragment(InteractionOperatorKind.Loop, messages);
  Diagram.UpdateShapePositions();
  transaction.Commit();
}
```

 Chcete-li použít `ILinkedUndoTransaction`, je nutné provést tuto deklaraci ve třídě:

```
[Import] ILinkedUndoContext LinkedUndoContext { get; set; }
```

 Další informace najdete v tématu [propojení aktualizací modelů UML pomocí transakcí](../modeling/link-uml-model-updates-by-using-transactions.md).

## <a name="building-an-interaction"></a>Sestavování interakce

### <a name="to-create-lifelines"></a>Vytvoření životností

```
ILifeline lifeline = interaction.CreateLifeline();
```

 Životnost představuje element s připojením, to znamená instance typu. Například pokud je interakce použita k zobrazení, jak komponenta deleguje příchozí zprávy do svých vnitřních částí, životnosti mohou představovat porty a části komponenty:

```
foreach (IConnectableElement part in
            component.Parts
           .Concat<IConnectableElement>(component.OwnedPorts))
{
   ILifeline lifeline = interaction.CreateLifeline();
   lifeline.Represents = part;
}
```

 Případně, pokud interakce zobrazuje libovolnou sadu objektů, můžete vytvořit vlastnost nebo jiné `IConnectableElement` v samotné interakci:

```
ILifeline lifeline = interaction.CreateLifeline();
IProperty property1 = interaction.CreateProperty();
property1.Type = model.CreateInterface();
property1.Type.Name = "Type 1";
lifeline.Represents = property1;
```

 Jako další alternativu můžete nastavit název a typ životnosti bez propojení s připojeným elementem:

```
ILifeline lifeline = interaction.CreateLifeline();
lifeline.Name = "c1";
lifeline.SetInstanceType("Customer");
System.Diagnostics.Debug.Assert(
           lifeline.GetDisplayName() == "c1:Customer"  );
```

### <a name="to-create-messages"></a>Vytvoření zpráv
 Chcete-li vytvořit zprávu, je nutné identifikovat body vložení na zdrojovém a cílovém životnosti. Příklad:

```
interaction.CreateMessage( sourceInsertionPoint,
                           targetInsertionPoint,
                           MessageKind.Complete,
                           MessageSort.ASynchCall)
```

 Chcete-li vytvořit zprávu s nedefinovaným zdrojem nebo nedefinovaným cílem:

```
interaction.CreateLostFoundMessage(MessageKind.Found, insertionPoint);
```

 K dispozici je několik zpráv, které můžete použít k identifikaci bodů vložení všech klíčových bodů na životnosti:

|Metoda na ILifeline|Použít ho k vložení do tohoto bodu|
|-------------------------|------------------------------------|
|`FindInsertionPointAtTop()`|Horní část životnosti.|
|`FindInsertionPointAtBottom()`|Dolní část životnosti.|
|`FindInsertionPointAfterMessage`<br /><br /> `(IMessage previous)`|Bod hned za určenou zprávou.|
|`FindInsertionPointAfterExecutionSpecification`<br /><br /> `(IExecutionSpecification previous)`|Bod může být buď na životnosti, nebo v nadřazeném bloku specifikace spuštění.|
|`FindInsertionPointAfterInteractionUse`<br /><br /> `(IInteractionUse previous)`|Bod následující po použití interakce.|
|`FindInsertionPointAfterCombinedFragment`<br /><br /> `(ICombinedFragment previous)`|Bod následující po kombinovaném fragmentu.|
|`FindInsertionPoint(IExecutionSpecification block)`|Horní část bloku spuštění.|
|`FindInsertionPoint(IInteractionOperand fragment)`|Horní část operandu kombinovaného fragmentu.|

 Při vytváření zpráv se ujistěte, že nedefinujete zprávu, která by převzala jiné zprávy.

### <a name="to-create-combined-fragments-and-interaction-uses"></a>Vytvoření kombinovaných fragmentů a použití interakce
 Můžete vytvořit kombinované fragmenty a použití interakce zadáním kurzoru na každou životnost, která musí být pokryta elementem. Je nutné se vyhnout zadání množiny bodů, které by přebraly existující zprávu nebo fragment.

```
Interaction.CreateCombinedFragment(InteractionOperatorKind.Loop,
  Interaction.Lifelines.Select(lifeline => lifeline.FindInsertionPointAtTop()));
Interaction.CreateInteractionUse(
  Interaction.Lifelines.Select(lifeline => lifeline.FindInsertionPointAtTop()));
```

 Můžete také vytvořit Kombinovaný fragment, který pokrývá existující sadu zpráv. Zprávy musí být všechny nasource ve stejném životnosti nebo bloku spuštění.

```
ICombinedFragment cf = Interaction.CreateCombinedFragment(
  InteractionOperatorKind.Loop,
  Interaction.Lifelines.First().GetAllOutgoingMessages());
```

 Kombinovaný fragment je vždy vytvořen s jedním operandem. Chcete-li vytvořit nový operand, je nutné zadat existující operand, který chcete vložit před nebo po, a zda chcete vložit po něm nebo před ním:

```
// Create an additional operand before the first
cf.CreateInteractionOperand(cf.Operands.First(), false);
// Create an additional operand after the last:
cf.CreateInteractionOperand(cf.Operands.Last(), true);
```

## <a name="troubleshooting"></a>Poradce při potížích
 Pokud se operace `UpdateShapePositions()` nebo `Layout()` nedokončily, zobrazí se obrazce v nesprávných pozicích.

 Většina ostatních problémů je způsobena chybně zarovnanými body vložení, takže nové zprávy nebo fragmenty by musely překračovat jiné. Je možné, že se neprovádí žádná změna nebo je vyvolána výjimka. Výjimka nemusí být vyvolána, dokud nebude provedena operace `UpdateShapePositions()` nebo `Layout()`.

## <a name="see-also"></a>Viz také:

- [Microsoft. VisualStudio. Uml. interakcí](/previous-versions/dd493373(v=vs.140))
- [Rozšíření modelů a diagramů UML](../modeling/extend-uml-models-and-diagrams.md)
- [Definování příkazu nabídky v diagramu modelování](../modeling/define-a-menu-command-on-a-modeling-diagram.md)
- [Definování vlastní položky sady nástrojů pro modelování](../modeling/define-a-custom-modeling-toolbox-item.md)
- [Definování omezení ověřování pro modely UML](../modeling/define-validation-constraints-for-uml-models.md)
- [Programování pomocí rozhraní API UML](../modeling/programming-with-the-uml-api.md)
