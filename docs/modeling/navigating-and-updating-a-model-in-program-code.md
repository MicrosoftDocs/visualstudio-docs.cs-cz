---
title: Navigace v modelu a aktualizace modelu v kódu programu
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, programming domain models
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 930d7ededf4a54aaf75516c59001eaccf38c210c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49896763"
---
# <a name="navigate-and-update-a-model-in-program-code"></a>Procházení a aktualizace modelu v programovém kódu

Můžete napsat kód, vytvářet a odstraňovat prvky modelu, nastavit jejich vlastnosti a vytvářet a odstraňovat vazeb mezi prvky. Všechny změny se musí provádět v rámci transakce. Pokud prvky jsou zobrazeny v diagramu, diagram bude je "Opravit" automaticky na konci transakce.

##  <a name="example"></a> Příklad definice DSL
 Toto je hlavní část DslDefinition.dsl příklady v tomto tématu:

 ![Diagramem definice DSL &#45; řady stromu modelu](../modeling/media/familyt_person.png)

 Tento model je instance tento DSL:

 ![Tudor řady stromu modelu](../modeling/media/tudor_familytreemodel.png)

### <a name="references-and-namespaces"></a>Odkazy a obory názvů
 Chcete-li spustit kód v tomto tématu, by měly odkazovat:

 `Microsoft.VisualStudio.Modeling.Sdk.11.0.dll`

 Váš kód bude používat tento obor názvů:

 `using Microsoft.VisualStudio.Modeling;`

 Kromě toho pokud píšete kód v jiném projektu než ten, ve kterém je definována vašeho DSL, importujte sestavení, který je sestaven projektem Dsl.

##  <a name="navigation"></a> Navigace modelu

### <a name="properties"></a>Vlastnosti
 Vlastnosti domény, které definujete v definici DSL stát vlastnosti, ke kterým můžete přistupovat v programovém kódu:

 `Person henry = ...;`

 `if (henry.BirthDate < 1500) ...`

 `if (henry.Name.EndsWith("VIII")) ...`

 Pokud chcete nastavit vlastnost, musíte to udělat uvnitř [transakce](#transaction):

 `henry.Name = "Henry VIII";`

 Při použití ve definici DSL, vlastnost **druh** je **vypočtené**, nelze ji nastavit. Další informace najdete v tématu [vypočtené a vlastní vlastnosti úložiště](../modeling/calculated-and-custom-storage-properties.md).

### <a name="relationships"></a>Relace
 Dvojice vlastností, jeden ve třídě na každém konci vztahu se stanou vztahy domén, které definujete v definici DSL. Názvy vlastností se zobrazí v diagramu DslDefinition jako popisky na rolích na každé straně vztahu. V závislosti na násobnost role je typ vlastnosti třídy na druhém konci vztahu nebo kolekci této třídy.

 `foreach (Person child in henry.Children) { ... }`

 `FamilyTreeModel ftree = henry.FamilyTreeModel;`

 Vlastnosti na opačnou elementy end vztahu jsou vždy převrácenou hodnotu. Po vytvoření nebo odstranění odkazu jsou aktualizovány vlastnosti role na oba prvky. Následující výraz (využívající rozšíření `System.Linq`) je vždycky true. u vztahu ParentsHaveChildren v příkladu:

 `(Person p) => p.Children.All(child => child.Parents.Contains(p))`

 `&& p.Parents.All(parent => parent.Children.Contains(p));`

 **ElementLinks**. Relace je představováno také prvek modelu s názvem *odkaz*, což je instance typu vztah domény. Odkaz vždy obsahuje jeden zdrojový element a element jeden cíl. Element zdrojový a cílový element může být stejný.

 Přístupné odkaz a jeho vlastnosti:

 `ParentsHaveChildren link = ParentsHaveChildren.GetLink(henry, edward);`

 `// This is now true:`

 `link == null || link.Parent == henry && link.Child == edward`

 Ve výchozím nastavení více než jednu instanci relace může propojit nějaká dvojice prvků modelu. Ale pokud se v definici DSL `Allow Duplicates` příznak má hodnotu true pro relaci, pak může existovat více než jedno propojení a je nutné použít `GetLinks`:

 `foreach (ParentsHaveChildren link in ParentsHaveChildren.GetLinks(henry, edward)) { ... }`

 Existují také další metody pro přístup k propojení. Příklad:

 `foreach (ParentsHaveChildren link in     ParentsHaveChildren.GetLinksToChildren(henry)) { ... }`

 **Skryté role.** Pokud v definici DSL **se vygeneruje vlastnost** je **false** pro určité role, pak žádná vlastnost není vygenerován, která odpovídá této role. Můžete však stále přistupovat k propojení a procházení odkazů pomocí metod relace:

 `foreach (Person p in ParentsHaveChildren.GetChildren(henry)) { ... }`

 Nejčastěji používané příkladem je <xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationViewsSubject> vztah, který propojí prvek modelu na tvar, který se zobrazí v diagramu:

 `PresentationViewsSubject.GetPresentation(henry)[0] as PersonShape`

### <a name="the-element-directory"></a>Adresáři elementů
 Všechny prvky v úložišti pomocí adresáři elementů se můžete dostat:

 `store.ElementDirectory.AllElements`

 Existují také metody pro hledání elementů, jako je následující:

 `store.ElementDirectory.FindElements(Person.DomainClassId);`

 `store.ElementDirectory.GetElement(elementId);`

##  <a name="metadata"></a> Přístup k informacím o třídě
 Můžete získat informace o třídách, relace a další aspekty definici DSL. Příklad:

 `DomainClassInfo personClass = henry.GetDomainClass();`

 `DomainPropertyInfo birthProperty =`

 `personClass.FindDomainProperty("BirthDate")`

 `DomainRelationshipInfo relationship =`

 `link.GetDomainRelationship();`

 `DomainRoleInfo sourceRole = relationship.DomainRole[0];`

 Třídy předchůdce prvků modelu jsou následující:

-   ModelElement – všechny prvky a vztahy jsou ModelElements

-   ElementLink – všechny vztahy jsou ElementLinks

##  <a name="transaction"></a> Proveďte změny v transakci
 Pokaždé, když se změní váš kód programu cokoli Store, se musí provést v transakci. To platí pro všechny prvky modelu, relace, tvary, diagramy a jejich vlastnosti. Další informace naleznete v tématu <xref:Microsoft.VisualStudio.Modeling.Transaction>.

 Je nejpohodlnější způsob správy transakce s `using` ohraničeno příkaz `try...catch` – příkaz:

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

 Můžete vytvořit libovolný počet změn v jedné transakci. Můžete otevřít nové transakce v aktivní transakci.

 Aby byly provedené změny trvalé, měli byste `Commit` transakce před jejich likvidace. Pokud dojde k výjimce, která není zachycena uvnitř transakce, Store obnoví do stavu před změny.

##  <a name="elements"></a> Vytváření elementů modelu
 Tento příklad přidá prvek na existující model:

```
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

 Tento příklad znázorňuje tyto základní body vytváření elementu:

- Vytvořte nový prvek do konkrétního oddílu Store. Pro prvky modelu a vztahů, ale ne tvary Toto je obvykle výchozí oddíl.

- Zkontrolujte cílové vztah obsažení. V DslDefinition v tomto příkladu každý uživatel, který musí být cílem vztah FamilyTreeHasPeople vložení. K dosažení tohoto cíle, jsme můžete nastavit vlastnost FamilyTreeModel role objektu osoba, nebo přidat uživatele do FamilyTreeModel objektu role vlastnictví.

- Nastavení vlastností nového elementu, zejména vlastnost, pro kterou `IsName` DslDefinition platí. Tento příznak označí vlastnost, která slouží k identifikaci elementu jedinečné v rámci jeho vlastníka. V tomto případě vlastnost Name má tento příznak.

- Definice DSL tento DSL musí byla načtena do Store. Pokud píšete rozšíření například příkaz nabídky, bude obvykle jednat již hodnotu true. V ostatních případech můžete explicitně načíst model do Store, nebo použít <xref:Microsoft.VisualStudio.Modeling.Integration.ModelBus> se jej načíst. Další informace najdete v tématu [postupy: otevření modelu ze souboru v kódu programu](../modeling/how-to-open-a-model-from-file-in-program-code.md).

  Při vytváření elementu tímto způsobem obrazce se automaticky vytvoří (Pokud DSL neobsahuje diagram). Zobrazí se v umístění služby automaticky přiřazený, výchozí tvar, barvu a další funkce. Pokud chcete určit, kde a jak se zobrazí související tvar, přečtěte si téma [vytváření elementu a jeho tvar](#merge).

##  <a name="links"></a> Vytváření vztahů propojení
 Existují dva vztahy definované v příkladu definici DSL. Definuje každou relaci *vlastnosti role* ve třídě na každém konci vztahu.

 Existují tři způsoby, ve kterých můžete vytvořit instanci relace. Každá z těchto tří metod má stejný účinek:

- Nastavte vlastnost aktéra zdrojové role. Příklad:

  -   `familyTree.People.Add(edward);`

  -   `edward.Parents.Add(henry);`

- Nastavte vlastnost Aktér cílové role. Příklad:

  -   `edward.familyTreeModel = familyTree;`

       Násobnost tato role je `1..1`, takže můžeme přiřadit hodnotu.

  -   `henry.Children.Add(edward);`

       Násobnost tato role je `0..*`, takže můžeme přidat do kolekce.

- Explicitně vytvořte instanci relace. Příklad:

  -   `FamilyTreeHasPeople edwardLink = new FamilyTreeHasPeople(familyTreeModel, edward);`

  -   `ParentsHaveChildren edwardHenryLink = new ParentsHaveChildren(henry, edward);`

  Poslední metoda je užitečná, pokud chcete nastavit vlastnosti v relaci sama.

  Při vytváření elementu tímto způsobem je automaticky vytvořen konektor v diagramu, ale má výchozí tvar, barvu a další funkce. Pokud chcete řídit způsob vytvoření konektoru přidružené, naleznete v tématu [vytváření elementu a jeho tvar](#merge).

##  <a name="deleteelements"></a> Odstranění prvků
 Odstranit element voláním `Delete()`:

 `henry.Delete();`

 Tato operace odstraní také:

- Vztah odkazy na a z elementu. Například `edward.Parents` bude již obsahovat `henry`.

- Prvky v rolí, pro které `PropagatesDelete` příznak má hodnotu true. Například na tvar, který se zobrazí element se odstraní.

  Ve výchozím nastavení, má každý vztah obsažení `PropagatesDelete` hodnotu true na cílová role. Odstraňuje se `henry` nedojde k odstranění `familyTree`, ale `familyTree.Delete()` by odstranit všechny `Persons`. Další informace najdete v tématu [přizpůsobení chování odstranění](../modeling/customizing-deletion-behavior.md).

  Ve výchozím nastavení `PropagatesDelete` neplatí pro role referenční stavy.

  Může způsobit odstranění pravidla chcete vynechat, nechte konkrétní šíření při odstranění objektu. To je užitečné, pokud jeden element jsou nahrazování pro jiné. Můžete zadat identifikátor GUID jednu nebo víc rolí, u kterých by neměly rozšířit odstranění. Identifikátor GUID můžete získat z třídy vztahu:

  `henry.Delete(ParentsHaveChildren.SourceDomainRoleId);`

  (V tomto konkrétním příkladu by neměl žádný vliv, protože `PropagatesDelete` je `false` pro role `ParentsHaveChildren` vztah.)

  V některých případech je odstranění bráněno existenci zámek, který je v elementu nebo na element, který se odstraní podle šíření. Můžete použít `element.CanDelete()` ke kontrole, jestli je možné odstranit prvek.

##  <a name="deletelinks"></a> Odstranění vztahů propojení
 Vztah odkazu můžete odstranit tak, že odeberete element z vlastnosti role:

 `henry.Children.Remove(edward); // or:`

 `edward.Parents.Remove(henry);  // or:`

 Můžete také odstranit odkaz explicitně:

 `edwardHenryLink.Delete();`

 Tyto tři metody všechny mají stejný účinek. Stačí použít jeden z nich.

 Pokud roli násobnosti 0.. 1 nebo 1..1, můžete ho nastavit `null`, nebo na jinou hodnotu:

 `edward.FamilyTreeModel = null;` nebo:

 `edward.FamilyTreeModel = anotherFamilyTree;`

##  <a name="reorder"></a> Změna řazení odkazy tohoto vztahu
 Odkazy konkrétního vztahu, které jsou zdrojem nebo zaměřený na konkrétním modelu element mají konkrétní pořadí. Zobrazí se v pořadí, ve kterém byly přidány. Tento příkaz například budou vždy poskytovat podřízené objekty ve stejném pořadí:

 `foreach (Person child in henry.Children) ...`

 Můžete změnit pořadí odkazů:

 `ParentsHaveChildren link = GetLink(henry,edward);`

 `ParentsHaveChildren nextLink = GetLink(henry, elizabeth);`

 `DomainRoleInfo role =`

 `link.GetDomainRelationship().DomainRoles[0];`

 `link.MoveBefore(role, nextLink);`

##  <a name="locks"></a> Zámky
 Provedené změny mohou být bráněno zámek. Zámky můžete nastavit na jednotlivé prvky, oddíly a úložišti. Pokud některé z těchto úrovní má zámek, který brání druh změn, které nechcete se ujistit, může při pokusu o je vyvolána výjimka. Můžete zjistit, jestli jsou nastavené zámky pomocí elementu. GetLocks(), což je rozšiřující metodu, která je definována v oboru názvů <xref:Microsoft.VisualStudio.Modeling.Immutability>.

 Další informace najdete v tématu [definování zásady zamykání pro vytváření segmentů jen pro čtení](../modeling/defining-a-locking-policy-to-create-read-only-segments.md).

##  <a name="copy"></a> Kopírování a vkládání
 Můžete zkopírovat elementy nebo skupiny prvků, které se <xref:System.Windows.Forms.IDataObject>:

```
Person person = personShape.ModelElement as Person;
Person adopter = adopterShape.ModelElement as Person;
IDataObject data = new DataObject();
personShape.Diagram.ElementOperations
      .Copy(data, person.Children.ToList<ModelElement>());
```

 Prvky jsou uloženy jako serializovaný prvek skupiny.

 Sloučit elementy ze objekt IDataObject do modelu:

```
using (Transaction t = targetDiagram.Store.
        TransactionManager.BeginTransaction("paste"))
{
  adopterShape.Diagram.ElementOperations.Merge(adopter, data);
}
```

 `Merge ()` Můžete buď přijmout `PresentationElement` nebo `ModelElement`. Pokud je jí `PresentationElement`, můžete také určit pozici v diagramu cíl jako třetí parametr.

##  <a name="diagrams"></a> Procházení a aktualizace diagramů
 V DSL doménový element modelu, který představuje koncept jako osoba nebo skladby, je oddělený od elementu obrazce, který reprezentuje, co se zobrazí v diagramu. Prvek modelu domény ukládá důležité vlastnosti a vztahy koncepty. Prvek tvaru ukládá velikost, umístění a barvy zobrazení objektu v diagramu a rozložení jeho součásti.

### <a name="presentation-elements"></a>Elementy prezentace
 ![Diagram tříd základní obrazec a element typů](../modeling/media/dslshapesandelements.png)

 Každý prvek, který zadáte v definici DSL, vytvoří třídu, která je odvozena z jednoho z následujících standardní třídy.

|Typ prvku|Základní třída|
|-|-|
|Doménová třída|<xref:Microsoft.VisualStudio.Modeling.ModelElement>|
|Doménový vztah|<xref:Microsoft.VisualStudio.Modeling.ElementLink>|
|Obrazec|<xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape>|
|Konektor|<xref:Microsoft.VisualStudio.Modeling.Diagrams.BinaryLinkShape>|
|diagram|<xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram>|

 Element diagramu obvykle představuje prvek modelu. Obvykle (ale ne vždy) <xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape> představuje instanci třídy domény a <xref:Microsoft.VisualStudio.Modeling.Diagrams.BinaryLinkShape> představuje instanci vztah domény. <xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationViewsSubject> Vztah propojuje tvar uzlu nebo propojení s prvkem modelu, který představuje.

 Každý uzel nebo propojení tvar patří do jednoho diagramu. Obrazec propojení připojí dva tvary uzlu.

 Obrazce mohou mít podřízené obrazce ve dvou sad. Tvar v `NestedChildShapes` sada je omezena na ohraničující rámeček svého nadřazeného objektu. Tvar v `RelativeChildShapes` seznamu mohou vyskytovat mimo nebo částečně mimo hranice nadřazený – například popisku nebo port. Diagram nemá žádné `RelativeChildShapes` a ne `Parent`.

###  <a name="views"></a> Přecházení mezi tvary a elementy
 Elementy modelu domény a elementy obrazce se vztahují <xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationViewsSubject> vztah.

```csharp
// using Microsoft.VisualStudio.Modeling;
// using Microsoft.VisualStudio.Modeling.Diagrams;
// using System.Linq;
Person henry = ...;
PersonShape henryShape =
  PresentationViewsSubject.GetPresentation(henry)
    .FirstOrDefault() as PersonShape;
```

 Stejný vztah odkazuje na konektory na diagram vztahů:

```
Descendants link = Descendants.GetLink(henry, edward);
DescendantConnector dc =
   PresentationViewsSubject.GetPresentation(link)
     .FirstOrDefault() as DescendantConnector;
// dc.FromShape == henryShape && dc.ToShape == edwardShape
```

 Tento vztah taky obsahuje odkazy kořen modelu do diagramu:

```
FamilyTreeDiagram diagram =
   PresentationViewsSubject.GetPresentation(familyTree)
      .FirstOrDefault() as FamilyTreeDiagram;
```

 Pokud chcete získat prvek modelu, který je reprezentovaný obrazec, použijte:

 `henryShape.ModelElement as Person`

 `diagram.ModelElement as FamilyTreeModel`

### <a name="navigating-around-the-diagram"></a>Navigace z diagramu
 Obecně není vhodné přecházet mezi obrazců a konektorů v diagramu. Je lepší procházení vztahů v modelu, přesouvání mezi obrazců a konektorů, pouze pokud je to nutné pro fungování na výskyt diagramu. Tyto metody propojit obrazce na každém konci konektory:

 `personShape.FromRoleLinkShapes, personShape.ToRoleLinkShapes`

 `connector.FromShape, connector.ToShape`

 Mnoho tvary jsou složené; se skládá z nadřazeného obrazce a vrstvy jeden nebo více podřízených prvků. Tvary, které jsou umístěny vzhledem k obrazci se označují jako jeho *podřízené*. Pokud se přesune do nadřazeného obrazce, podřízené objekty přesune s ním.

 *Relativní podřízené* může objevit mimo ohraničovací rámeček nadřazeného obrazce. *Vnořené* podřízené položky se zobrazí striktně uvnitř hranic nadřazeného prvku.

 Pokud chcete získat nejvyšší sadu tvarů v diagramu, použijte:

 `Diagram.NestedChildShapes`

 Třídy předchůdce obrazců a konektorů jsou:

 <xref:Microsoft.VisualStudio.Modeling.ModelElement>

 -- <xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationElement>

 -- <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement>

 ----- <xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape>

 ------- <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram>

 ------- *YourShape*

 ----- <xref:Microsoft.VisualStudio.Modeling.Diagrams.LinkShape>

 ------- <xref:Microsoft.VisualStudio.Modeling.Diagrams.BinaryLinkShape>

 --------- *YourConnector*

###  <a name="shapeProperties"></a> Vlastnosti obrazců a konektorů
 Ve většině případů není nutné provést explicitní změny obrazce. Pokud jste změnili prvky modelu, pravidla "Opravit" aktualizace obrazců a konektorů. Další informace najdete v tématu [šířící změny a reakce na](../modeling/responding-to-and-propagating-changes.md).

 Je však vhodné udělat nějaké změny explicitní obrazce ve vlastnosti, které jsou nezávislé na prvky modelu. Můžete například změnit tyto vlastnosti:

-   <xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape.Size%2A> -Určuje výšku a šířku tvaru.

-   <xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape.Location%2A> -pozice relativně vzhledem k nadřazený obrazec ani diagram

-   <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.StyleSet%2A> -sadu pera a použité pro kreslení obrazec nebo spojnici štětce

-   <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.Hide%2A> -je neviditelné tvar

-   <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.Show%2A> – Po zviditelní obrazec `Hide()`

###  <a name="merge"></a> Vytvoření elementu a jeho tvar

Při vytváření elementu a připojit ho do stromu relace vkládání, je automaticky vytvořen a přidružen obrazce. To se provádí pomocí pravidel "opravy", které jsou spouštěny na konci transakce. Ale tvar se zobrazí v automaticky přiřazená umístění a jeho tvar, barvu a další funkce budou mít výchozí hodnoty. K řízení, jak vytvořit tvar, můžete použít funkci sloučení. Musíte nejprve přidat prvky, které chcete přidat do skupina ElementGroup a pak sloučit skupiny do diagramu.

Tuto metodu:

-   Nastaví název, pokud jste přiřadili vlastnost jako název elementu.

-   Dodržuje všechny direktivy sloučení elementů, který jste zadali v definici DSL.

Tento příklad vytvoří obrazec pod kurzor myši, když uživatel pokliká na diagramu. V definici DSL v tomto příkladu `FillColor` vlastnost `ExampleShape` byl zpřístupněn.

```
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

 Pokud zadáte více než jeden tvar, nastavit jejich relativní pozice pomocí `AbsoluteBounds`.

 Můžete také nastavit barvu a další vlastnosti zveřejněné konektorů pomocí této metody.

### <a name="use-transactions"></a>Použití transakcí
 Tvary, konektory a diagramy jsou podtypy <xref:Microsoft.VisualStudio.Modeling.ModelElement> tak pro živé v Store. Proto je třeba provést změny k nim jen v transakci. Další informace najdete v tématu [postupy: používání transakcí k aktualizaci modelu](../modeling/how-to-use-transactions-to-update-the-model.md).

##  <a name="docdata"></a> Zobrazení dokumentů a dat dokumentu
 ![Diagram tříd typů standardní diagramu](../modeling/media/dsldiagramsanddocs.png)

## <a name="store-partitions"></a>Oddíly Store
 Při načítání modelu doprovodné diagram načtení ve stejnou dobu. Obvykle model je načtený do Store.DefaultPartition a diagram obsahu se načtou do jiného oddílu. Obsah jednotlivých oddílů je obvykle načtení a uložit do samostatného souboru.

## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualStudio.Modeling.ModelElement>
- [Ověřování v jazyce specifickém pro doménu](../modeling/validation-in-a-domain-specific-language.md)
- [Vytváření kódu z jazyka specifického pro doménu](../modeling/generating-code-from-a-domain-specific-language.md)
- [Postupy: Používání transakcí k aktualizaci modelu](../modeling/how-to-use-transactions-to-update-the-model.md)
- [Integrace modelů pomocí Visual Studio Modelbus](../modeling/integrating-models-by-using-visual-studio-modelbus.md)
- [Reagování na změny a šíření změn](../modeling/responding-to-and-propagating-changes.md)
