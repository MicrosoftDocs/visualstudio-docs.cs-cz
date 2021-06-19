---
title: Navigace v modelu a aktualizace modelu v kódu programu
description: Zjistěte, jak můžete napsat kód pro vytváření a odstraňování prvků modelu, nastavení jejich vlastností a vytváření a odstraňování propojení mezi prvky.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, programming domain models
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: be19b34c51744c6bab1c6021a006f7ec9b4da0f4
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2021
ms.locfileid: "112390968"
---
# <a name="navigate-and-update-a-model-in-program-code"></a>Procházení a aktualizace modelu v programovém kódu

Můžete napsat kód pro vytvoření a odstranění prvků modelu, nastavení jejich vlastností a vytvoření a odstranění propojení mezi prvky. Všechny změny musí být provedeny v rámci transakce. Pokud jsou prvky zobrazeny v diagramu, diagram bude automaticky "opraven" na konci transakce.

## <a name="an-example-dsl-definition"></a><a name="example"></a> Příklad definice DSL
 Toto je hlavní část dslDefinition.dsl pro příklady v tomto tématu:

 ![Diagram definice DSL &#45; modelu stromové struktury rodiny](../modeling/media/familyt_person.png)

 Tento model je instancí tohoto DSL:

 ![Tudor Family Tree Model](../modeling/media/tudor_familytreemodel.png)

### <a name="references-and-namespaces"></a>Odkazy a obory názvů
 Pokud chcete spustit kód v tomto tématu, měli byste odkazovat na:

 `Microsoft.VisualStudio.Modeling.Sdk.11.0.dll`

 Váš kód bude používat tento obor názvů:

 `using Microsoft.VisualStudio.Modeling;`

 Kromě toho, pokud píšete kód v jiném projektu než ten, ve kterém je definován váš DSL, měli byste importovat sestavení, které je sestaveno projektem Dsl.

## <a name="navigating-the-model"></a><a name="navigation"></a> Navigace v modelu

### <a name="properties"></a>Vlastnosti
 Vlastnosti domény, které definujete v definici DSL, se stanou vlastnostmi, ke které máte přístup v kódu programu:

 `Person henry = ...;`

 `if (henry.BirthDate < 1500) ...`

 `if (henry.Name.EndsWith("VIII")) ...`

 Pokud chcete nastavit vlastnost, musíte to provést uvnitř [transakce](#transaction):

 `henry.Name = "Henry VIII";`

 Pokud je v definici DSL vlastnost **Kind** **vypočtena,** nelze ji nastavit. Další informace najdete v tématu [Počítané a vlastní vlastnosti úložiště.](../modeling/calculated-and-custom-storage-properties.md)

### <a name="relationships"></a>Relace
 Vztahy domény, které definujete v definici DSL, se stanou dvojicemi vlastností, jednu ve třídě na každém konci relace. Názvy vlastností se zobrazují v diagramu DslDefinition jako popisky na rolích na každé straně relace. V závislosti na násobnosti role je typem vlastnosti buď třída na druhém konci relace, nebo kolekce této třídy.

 `foreach (Person child in henry.Children) { ... }`

 `FamilyTreeModel ftree = henry.FamilyTreeModel;`

 Vlastnosti na opačných koncích relace jsou vždy reciproční. Při vytvoření nebo odstranění odkazu se aktualizují vlastnosti role u obou prvků. Následující výraz (který používá rozšíření ) je vždy pravdivý pro relaci `System.Linq` Parents Nespravovatelé v příkladu:

 `(Person p) => p.Children.All(child => child.Parents.Contains(p))`

 `&& p.Parents.All(parent => parent.Children.Contains(p));`

 **ElementLinks**. Relace je také reprezentována prvkem modelu *nazývaným odkaz*, což je instance typu vztahu domény. Propojení má vždy jeden zdrojový prvek a jeden cílový prvek. Zdrojový prvek a cílový prvek mohou být stejné.

 Můžete získat přístup k odkazu a jeho vlastnostem:

 `ParentsHaveChildren link = ParentsHaveChildren.GetLink(henry, edward);`

 `// This is now true:`

 `link == null || link.Parent == henry && link.Child == edward`

 Ve výchozím nastavení nesmí propojit jakoukoli dvojici prvků modelu více než jedna instance relace. Pokud je ale v definici DSL příznak pro relaci true, pak může být více než jedno propojení a `Allow Duplicates` musíte použít `GetLinks` :

 `foreach (ParentsHaveChildren link in ParentsHaveChildren.GetLinks(henry, edward)) { ... }`

 Existují také další metody pro přístup k odkazům. Příklad:

 `foreach (ParentsHaveChildren link in     ParentsHaveChildren.GetLinksToChildren(henry)) { ... }`

 **Skryté role.** Pokud je v definici DSL vlastnost **Generated** pro konkrétní roli **false,** pak se negeneruje žádná vlastnost, která odpovídá této roli. Stále ale máte přístup k odkazům a můžete je procházet pomocí metod relace:

 `foreach (Person p in ParentsHaveChildren.GetChildren(henry)) { ... }`

 Nejčastěji používaným příkladem je relace, která propojuje prvek modelu s tvarem, který <xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationViewsSubject> ho zobrazuje v diagramu:

 `PresentationViewsSubject.GetPresentation(henry)[0] as PersonShape`

### <a name="the-element-directory"></a>Adresář elementu
 Ke všem prvkům v obchodě můžete přistupovat pomocí adresáře elementu :

 `store.ElementDirectory.AllElements`

 Existují také metody pro vyhledání elementů, například:

 `store.ElementDirectory.FindElements(Person.DomainClassId);`

 `store.ElementDirectory.GetElement(elementId);`

## <a name="accessing-class-information"></a><a name="metadata"></a> Přístup k informacím o třídě
 Můžete získat informace o třídách, relacích a dalších aspektech definice DSL. Příklad:

 `DomainClassInfo personClass = henry.GetDomainClass();`

 `DomainPropertyInfo birthProperty =`

 `personClass.FindDomainProperty("BirthDate")`

 `DomainRelationshipInfo relationship =`

 `link.GetDomainRelationship();`

 `DomainRoleInfo sourceRole = relationship.DomainRole[0];`

 Třídy předchůdce prvků modelu jsou následující:

- ModelElement – všechny prvky a relace jsou ModelElements

- ElementLink – všechny relace jsou ElementLinks

## <a name="perform-changes-inside-a-transaction"></a><a name="transaction"></a> Provádění změn uvnitř transakce
 Kdykoli programový kód změní cokoli ve Storu, musí to udělat uvnitř transakce. To platí pro všechny prvky modelu, relace, tvary, diagramy a jejich vlastnosti. Další informace naleznete v tématu <xref:Microsoft.VisualStudio.Modeling.Transaction>.

 Nejpohodlnější způsob správy transakce je s `using` příkazem uzavřeným v `try...catch` příkazu :

```
Store store; ...
try
{
  using (Transaction transaction =
    store.TransactionManager.BeginTransaction("update model"))
    // Outermost transaction must always have a name.
  {
    // Make several changes in Store:
    Person p = new Person(store);
    p.FamilyTreeModel = familyTree;
    p.Name = "Edward VI";
    // end of changes to Store

    transaction.Commit(); // Don't forget this!
  } // transaction disposed here
}
catch (Exception ex)
{
  // If an exception occurs, the Store will be
  // rolled back to its previous state.
}
```

 V rámci jedné transakce můžete provést libovolný počet změn. Nové transakce můžete otevřít v rámci aktivní transakce.

 Pokud chcete, aby vaše změny byly trvalé, měli `Commit` byste transakci před vyřazení. Pokud dojde k výjimce, která není zachycena v rámci transakce, úložiště se resetuje do jeho stavu před změnami.

## <a name="creating-model-elements"></a><a name="elements"></a> Vytváření elementů modelu
 Tento příklad přidá prvek do existujícího modelu:

```csharp
FamilyTreeModel familyTree = ...; // The root of the model.
using (Transaction t =
    familyTree.Store.TransactionManager
    .BeginTransaction("update model"))
{
  // Create a new model element
  // in the same partition as the model root:
  Person edward = new Person(familyTree.Partition);
  // Set its embedding relationship:
  edward.FamilyTreeModel = familyTree;
          // same as: familyTree.People.Add(edward);
  // Set its properties:
  edward.Name = "Edward VII";
  t.Commit(); // Don't forget this!
}
```

 Tento příklad znázorňuje tyto základní body týkající se vytvoření elementu:

- Vytvořte nový prvek v konkrétním oddílu úložiště. U prvků modelu a relací, ale nikoli tvarů, se obvykle jedná o výchozí oddíl.

- Načtou se jako cíl vztahu vkládání. V dsldefinition tohoto příkladu musí být cílem vkládaní relace FamilyTreeHasPeople každá osoba. K tomu můžeme buď nastavit vlastnost role FamilyTreeModel objektu Person, nebo přidat Person do vlastnosti role People objektu FamilyTreeModel.

- Nastavte vlastnosti nového prvku, zejména vlastnost, pro kterou `IsName` je true v DslDefinition. Tento příznak označuje vlastnost, která slouží k jednoznačné identifikaci elementu v rámci jeho vlastníka. V tomto případě má vlastnost Name tento příznak.

- Definice DSL tohoto DSL musí být načtena do úložiště. Pokud píšete rozšíření, jako je příkaz nabídky, bude to obvykle již true. V ostatních případech můžete model explicitně načíst do Storu nebo ho načíst pomocí [služby ModelBus.](/previous-versions/ee904639(v=vs.140)) Další informace najdete v tématu [Postupy: Otevření modelu ze souboru v programovém kódu](../modeling/how-to-open-a-model-from-file-in-program-code.md).

  Když vytvoříte prvek tímto způsobem, vytvoří se tvar automaticky (pokud DSL obsahuje diagram). Zobrazuje se v automaticky přiřazeném umístění s výchozím tvarem, barvou a dalšími funkcemi. Pokud chcete řídit, kde a jak se přidružený obrazec zobrazí, podívejte se na vytvoření [elementu a jeho tvaru](#merge).

## <a name="creating-relationship-links"></a><a name="links"></a> Vytváření odkazů na relace
 V příkladu definice DSL jsou definované dvě relace. Každý vztah definuje *vlastnost role* ve třídě na každém konci relace.

 Existují tři způsoby, jak vytvořit instanci relace. Každá z těchto tří metod má stejný účinek:

- Nastavte vlastnost zdrojového přehrávače role. Příklad:

  - `familyTree.People.Add(edward);`

  - `edward.Parents.Add(henry);`

- Nastavte vlastnost cílového hráče role. Příklad:

  - `edward.familyTreeModel = familyTree;`

       Násobnost této role je `1..1` , takže přiřadíme hodnotu .

  - `henry.Children.Add(edward);`

       Násobnost této role je `0..*` , takže do kolekce přidáme .

- Vytvořte instanci relace explicitně. Příklad:

  - `FamilyTreeHasPeople edwardLink = new FamilyTreeHasPeople(familyTreeModel, edward);`

  - `ParentsHaveChildren edwardHenryLink = new ParentsHaveChildren(henry, edward);`

  Poslední metoda je užitečná, pokud chcete nastavit vlastnosti pro samotnou relaci.

  Když vytvoříte prvek tímto způsobem, konektor v diagramu se automaticky vytvoří, ale má výchozí tvar, barvu a další funkce. Pokud chcete řídit, jak se přidružený konektor vytvoří, podívejte se na vytvoření [elementu a jeho tvaru.](#merge)

## <a name="deleting-elements"></a><a name="deleteelements"></a> Odstranění elementů

Odstranění elementu voláním `Delete()` :

`henry.Delete();`

Tato operace také odstraní:

- Relace odkazuje na a z elementu . Například už `edward.Parents` nebude obsahovat `henry` .

- Prvky v rolích, pro `PropagatesDelete` které má příznak hodnotu true. Například tvar, který zobrazuje prvek, bude odstraněn.

Ve výchozím nastavení má každá relace vložení `PropagatesDelete` na cílovou roli hodnotu true. Odstraněním se `henry` neodstraní `familyTree` , ale `familyTree.Delete()` odstraní všechny `Persons` .

Ve výchozím nastavení `PropagatesDelete` není hodnota true pro role referenčních vztahů.

Můžete způsobit, že pravidla odstraňování budou při odstraňování objektu vynechat specifická rozšíření. To je užitečné, Pokud nahrazujete jeden prvek pro jiný. Zadejte identifikátor GUID jedné nebo více rolí, pro které by odstranění nemělo být šířeno. Identifikátor GUID lze získat z třídy Relationship:

`henry.Delete(ParentsHaveChildren.SourceDomainRoleId);`

(Tento konkrétní příklad by neměl mít žádný účinek, protože `PropagatesDelete` je `false` pro role `ParentsHaveChildren` vztahu.)

V některých případech je odstranění znemožněno existence zámku, buď na elementu, nebo na elementu, který by byl odstraněn pomocí šíření. Můžete použít `element.CanDelete()` ke kontrole, zda lze prvek odstranit.

## <a name="deleting-relationship-links"></a><a name="deletelinks"></a> Odstraňují se odkazy na relace.
 Odkaz na relaci můžete odstranit odebráním elementu z vlastnosti role:

 `henry.Children.Remove(edward); // or:`

 `edward.Parents.Remove(henry);  // or:`

 Propojení můžete také explicitně odstranit:

 `edwardHenryLink.Delete();`

 Všechny tyto tři metody mají stejný účinek. Musíte použít jenom jeden z nich.

 Pokud má role 0.. 1 nebo 1.. 1 násobnost, můžete ji nastavit na `null` nebo jinou hodnotu:

 `edward.FamilyTreeModel = null;` ani

 `edward.FamilyTreeModel = anotherFamilyTree;`

## <a name="re-ordering-the-links-of-a-relationship"></a><a name="reorder"></a> Změna pořadí propojení vztahu
 Odkazy konkrétního vztahu, které jsou zdrojové nebo cílové na konkrétním prvku modelu, mají konkrétní sekvenci. Zobrazují se v pořadí, ve kterém byly přidány. Například tento příkaz bude vždy vracet podřízené objekty ve stejném pořadí:

 `foreach (Person child in henry.Children) ...`

 Můžete změnit pořadí odkazů:

 `ParentsHaveChildren link = GetLink(henry,edward);`

 `ParentsHaveChildren nextLink = GetLink(henry, elizabeth);`

 `DomainRoleInfo role =`

 `link.GetDomainRelationship().DomainRoles[0];`

 `link.MoveBefore(role, nextLink);`

## <a name="locks"></a><a name="locks"></a> Počtu
 Je možné, že se vaše změny zabrání zámkům. Zámky je možné nastavit u jednotlivých prvků, v oddílech a na úložišti. Pokud má kterákoli z těchto úrovní zámek, který brání druhu změny, kterou chcete provést, může být výjimka vyvolána při pokusu. Můžete zjistit, zda jsou zámky nastaveny pomocí elementu. GetLocks (), což je rozšiřující metoda, která je definována v oboru názvů <xref:Microsoft.VisualStudio.Modeling.Immutability> .

 Další informace najdete v tématu [Definování zásady zamykání pro vytváření Read-Onlych segmentů](../modeling/defining-a-locking-policy-to-create-read-only-segments.md).

## <a name="copy-and-paste"></a><a name="copy"></a> Kopírovat a vložit
 Prvky nebo skupiny prvků můžete kopírovat do <xref:System.Windows.Forms.IDataObject> :

```csharp
Person person = personShape.ModelElement as Person;
Person adopter = adopterShape.ModelElement as Person;
IDataObject data = new DataObject();
personShape.Diagram.ElementOperations
      .Copy(data, person.Children.ToList<ModelElement>());
```

 Prvky jsou uloženy jako serializovaná skupina elementů.

 Prvky můžete sloučit z IDataObject do modelu:

```csharp
using (Transaction t = targetDiagram.Store.
        TransactionManager.BeginTransaction("paste"))
{
  adopterShape.Diagram.ElementOperations.Merge(adopter, data);
}
```

 `Merge ()` může přijmout buď `PresentationElement` nebo `ModelElement` . Pokud mu udělíte a `PresentationElement` , můžete také určit pozici v cílovém diagramu jako třetí parametr.

## <a name="navigating-and-updating-diagrams"></a><a name="diagrams"></a> Navigace a aktualizace diagramů
 V rámci DSL je prvek doménového modelu, který představuje koncept, jako je například person nebo song, oddělený od prvku Shape, který představuje to, co vidíte v diagramu. Element Domain model ukládá důležité vlastnosti a vztahy konceptu. Element Shape ukládá velikost, umístění a barvu zobrazení objektu v diagramu a rozložení jeho částí.

### <a name="presentation-elements"></a>Prvky prezentace
 ![Diagram tříd základních obrazců a typů elementů](../modeling/media/dslshapesandelements.png)

 V definici DSL každý element, který zadáte, vytvoří třídu, která je odvozena z jedné z následujících standardních tříd.

|Druh elementu|Základní třída|
|-|-|
|Domain – třída|<xref:Microsoft.VisualStudio.Modeling.ModelElement>|
|Doménový vztah|<xref:Microsoft.VisualStudio.Modeling.ElementLink>|
|Tvar|<xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape>|
|Konektor|<xref:Microsoft.VisualStudio.Modeling.Diagrams.BinaryLinkShape>|
|Diagram|<xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram>|

 Prvek v diagramu obvykle představuje prvek modelu. Obvykle (ale ne vždy) <xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape> představuje instanci doménové třídy a <xref:Microsoft.VisualStudio.Modeling.Diagrams.BinaryLinkShape> představuje instanci doménového vztahu. <xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationViewsSubject>Vztah odkazuje na uzel nebo propojení obrazce k prvku modelu, který představuje.

 Každý obrazec uzlu nebo propojení patří do jednoho diagramu. Obrazec binárního propojení spojuje dva obrazce uzlů.

 Obrazce mohou mít podřízené obrazce ve dvou sadách. Tvar v `NestedChildShapes` sadě je omezen na ohraničující rámeček své nadřazené položky. Tvar v `RelativeChildShapes` seznamu se může objevit mimo nebo částečně mimo hranice nadřazeného objektu, například popisku nebo portu. Diagram nemá žádné `RelativeChildShapes` a žádné `Parent` .

### <a name="navigating-between-shapes-and-elements"></a><a name="views"></a> Navigace mezi tvary a prvky
 Prvky doménového modelu a prvky obrazce souvisejí s <xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationViewsSubject> relací.

```csharp
// using Microsoft.VisualStudio.Modeling;
// using Microsoft.VisualStudio.Modeling.Diagrams;
// using System.Linq;
Person henry = ...;
PersonShape henryShape =
  PresentationViewsSubject.GetPresentation(henry)
    .FirstOrDefault() as PersonShape;
```

 Stejné vztahy odkazují na spojnice v diagramu:

```
Descendants link = Descendants.GetLink(henry, edward);
DescendantConnector dc =
   PresentationViewsSubject.GetPresentation(link)
     .FirstOrDefault() as DescendantConnector;
// dc.FromShape == henryShape && dc.ToShape == edwardShape
```

 Tento vztah také propojuje kořen modelu s diagramem:

```
FamilyTreeDiagram diagram =
   PresentationViewsSubject.GetPresentation(familyTree)
      .FirstOrDefault() as FamilyTreeDiagram;
```

 Chcete-li získat prvek modelu reprezentovaný obrazcem, použijte:

 `henryShape.ModelElement as Person`

 `diagram.ModelElement as FamilyTreeModel`

### <a name="navigating-around-the-diagram"></a>Navigace okolo diagramu
 Obecně není vhodné přecházet mezi tvary a spojnicemi v diagramu. Je lepší procházet vztahy v modelu a přesouvat je mezi obrazci a spojnicemi pouze v případě, že je nutné pracovat na vzhledu diagramu. Tyto metody propojí konektory s tvary na každém konci:

 `personShape.FromRoleLinkShapes, personShape.ToRoleLinkShapes`

 `connector.FromShape, connector.ToShape`

 Mnoho tvarů je složených. jsou tvořeny nadřazeným obrazcem a jednou nebo více vrstvami podřízených objektů. Obrazce, které jsou umístěny vzhledem k jinému obrazci, jsou označeny jako *podřízené*. Po přesunutí nadřazeného obrazce se s ním přesunou podřízené objekty.

 *Relativní podřízené objekty* se mohou objevit mimo ohraničující rámeček nadřazeného obrazce. *Vnořené* podřízené objekty jsou přesně uvnitř hranic nadřazeného objektu.

 Chcete-li získat nejvyšší sadu obrazců v diagramu, použijte:

 `Diagram.NestedChildShapes`

 Nadřazené třídy obrazců a konektorů jsou:

 <xref:Microsoft.VisualStudio.Modeling.ModelElement>

 -- <xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationElement>

 -- <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement>

 ----- <xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape>

 ------- <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram>

 ------- *YourShape*

 ----- <xref:Microsoft.VisualStudio.Modeling.Diagrams.LinkShape>

 ------- <xref:Microsoft.VisualStudio.Modeling.Diagrams.BinaryLinkShape>

 --------- *YourConnector*

### <a name="properties-of-shapes-and-connectors"></a><a name="shapeProperties"></a> Vlastnosti obrazců a konektorů
 Ve většině případů není nutné provádět explicitní změny tvarů. Pokud jste změnili prvky modelu, pravidla "opravit" aktualizují tvary a konektory. Další informace najdete v tématu [reagování na změny a šíření změn](../modeling/responding-to-and-propagating-changes.md).

 Je však vhodné provést některé explicitní změny tvarů ve vlastnostech, které jsou nezávisle na prvcích modelu. Můžete například změnit tyto vlastnosti:

- <xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape.Size%2A> – Určuje výšku a šířku obrazce.

- <xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape.Location%2A> -pozice relativní vzhledem k nadřazenému obrazci nebo diagramu

- <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.StyleSet%2A> -sada per a štětců používané pro kreslení tvaru nebo spojnice

- <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.Hide%2A> – změní tvar na neviditelný.

- <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.Show%2A> – Nastaví obrazec jako viditelný po `Hide()`

### <a name="creating-an-element-and-its-shape"></a><a name="merge"></a> Vytvoření elementu a jeho tvaru

Když vytvoříte element a propojíte ho se stromem vkládání vztahů, vytvoří se obrazec automaticky a přidruží se k němu. Tuto akci provádí pravidla "opravit", která se spouštějí na konci transakce. Tvar se ale zobrazí v automaticky přiřazeném umístění a jeho tvar, barva a další funkce budou mít výchozí hodnoty. Chcete-li řídit, jak je tvar vytvořen, můžete použít funkci Merge. Nejprve musíte přidat prvky, které chcete přidat do skupiny prvků, a poté skupinu sloučit do diagramu.

Tato metoda:

- Nastaví název, pokud jste přiřadili vlastnost jako název elementu.

- Sleduje všechny direktivy sloučení elementů, které jste zadali v definici DSL.

Tento příklad vytvoří tvar na pozici myši, když uživatel dvakrát klikne na diagram. V definici DSL pro tuto ukázku byla vlastnost k `FillColor` `ExampleShape` dispozici.

```csharp
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;
partial class MyDiagram
{
  public override void OnDoubleClick(DiagramPointEventArgs e)
  {
    base.OnDoubleClick(e);

    using (Transaction t = this.Store.TransactionManager
        .BeginTransaction("double click"))
    {
      ExampleElement element = new ExampleElement(this.Store);
      ElementGroup group = new ElementGroup(element);

      { // To use a shape of a default size and color, omit this block.
        ExampleShape shape = new ExampleShape(this.Partition);
        shape.ModelElement = element;
        shape.AbsoluteBounds = new RectangleD(0, 0, 1.5, 1.0);
        shape.FillColor = System.Drawing.Color.Azure;
        group.Add(shape);
      }

      this.ElementOperations.MergeElementGroupPrototype(
        this,
        group.CreatePrototype(),
        PointD.ToPointF(e.MousePosition));
      t.Commit();
    }
  }
}
```

 Pokud zadáte více než jeden obrazec, nastavte jejich relativní umístění pomocí `AbsoluteBounds` .

 Pomocí této metody můžete také nastavit barvu a další vystavené vlastnosti konektorů.

### <a name="use-transactions"></a>Použití transakcí
 Obrazce, konektory a diagramy jsou podtypy <xref:Microsoft.VisualStudio.Modeling.ModelElement> a živé v úložišti. Proto je nutné provést změny pouze v rámci transakce. Další informace naleznete v tématu [How to: use Transactions to Update a model](../modeling/how-to-use-transactions-to-update-the-model.md).

## <a name="document-view-and-document-data"></a><a name="docdata"></a> Zobrazení dokumentu a data dokumentu
 ![Diagram tříd standardních typů diagramů](../modeling/media/dsldiagramsanddocs.png)

## <a name="store-partitions"></a>Ukládat oddíly
 Při načtení modelu se načte i doprovodný diagram. Model je obvykle načten do úložiště. DefaultPartition a obsah diagramu je načten do jiného oddílu. Obvykle se obsah každého oddílu načte a uloží do samostatného souboru.

## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualStudio.Modeling.ModelElement>
- [Ověřování v jazyce specifickém pro doménu](../modeling/validation-in-a-domain-specific-language.md)
- [Vytváření kódu z jazyka specifického pro doménu](../modeling/generating-code-from-a-domain-specific-language.md)
- [Postupy: Používání transakcí k aktualizaci modelu](../modeling/how-to-use-transactions-to-update-the-model.md)
- [Integrace modelů pomocí Visual Studio Modelbus](../modeling/integrating-models-by-using-visual-studio-modelbus.md)
- [Reagování na změny a šíření změn](../modeling/responding-to-and-propagating-changes.md)
