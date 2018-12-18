---
title: Porozumění kódu DSL
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, generated code
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 490c9c3fe5724373072b2857eb0ce3da7905b172
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49813315"
---
# <a name="understanding-the-dsl-code"></a>Porozumění kódu DSL
Řešení jazyka specifického pro doménu (DSL), vygeneruje rozhraní API, které můžete použít ke čtení a aktualizovat instance DSL v sadě Visual Studio. Toto rozhraní API je definováno v kódu, který je generován z definici DSL. Toto téma popisuje generovaného rozhraní API.

## <a name="the-example-solution-component-diagrams"></a>Ukázkové řešení: diagramy komponent
 Při vytváření řešení, které je zdrojem většina příkladů v tomto tématu Vytvoření DSL z **komponenty modely** šablonu řešení. Toto je jeden standardní šablony, které se zobrazí, když vytvoříte nové řešení DSL.

> [!NOTE]
>  Šablona DSL diagramy součástí nesouvisí s diagramy komponent UML, které můžete vytvořit pomocí nabídky architektury v sadě Visual Studio. V **nový projekt** dialogového okna rozbalte **jiný projekt Types\Extensibility** a potom klikněte na tlačítko **návrháře jazyka specifického pro doménu**.

 Pokud nejste obeznámeni s touto šablonou řešení, stiskněte klávesu F5 a Experimentujte. Všimněte si zejména vytvořit porty přetažením nástroj portů do komponenty, a zda se můžete připojit porty.

 ![Komponenty a propojených porty](../modeling/media/componentsample.png)

## <a name="the-structure-of-the-dsl-solution"></a>Struktura řešení DSL
 **Dsl** projekt definuje rozhraní API pro vašeho DSL. **DslPackage** projektu definuje, jak se integruje s Visual Studio. Můžete také přidat svoje vlastní projekty, které mohou také obsahovat kód generovaný z modelu.

### <a name="the-code-directories"></a>Adresáře kódu.
 Většinu kódu v každé z těchto projektů se generuje z **Dsl\DslDefinition.dsl**. Generovaný kód je v **kód generovaný** složky. Vygenerovaný soubor zobrazíte kliknutím **[+]** vedle generování **.tt** souboru.

 Doporučujeme vám, že si prohlédnout generovaného kódu, které vám pomůžou porozumět DSL. Pokud chcete zobrazit generované soubory, rozbalte soubory *.tt v Průzkumníku řešení.

 \*Soubory .tt obsahují velmi malé generování kódu. Místo toho použijte `<#include>` direktivy mají zahrnout soubory sdílené šablony. Sdílené soubory lze nalézt v **\Program Files\Microsoft Visual Studio 10.0\Common7\IDE\Extensions\Microsoft\DSL SDK\DSL Designer\11.0\TextTemplates**

 Při přidání vlastního kódu programu k řešení DSL ji přidáte do samostatného souboru mimo složku vygenerovaném kódu. Můžete chtít vytvořit **vlastní kód** složky. (Při přidání nového souboru kódu do vlastní složky, nezapomeňte k odstranění oboru názvů zhruba počáteční kód.)

 Důrazně doporučujeme generovaný kód přímo, neupravujte vzhledem k tomu, že vaše úpravy budou ztraceny, když znovu sestavte řešení. Místo toho k přizpůsobení vašeho DSL:

-   Upravte velký počet parametrů v definici DSL.

-   Částečné třídy zapisovat do souborů samostatného kódu přepsání metody, které jsou definovány v, nebo zdědí generované třídy. V některých případech je nutné nastavit **Generates Double Derived** možnost třídy v definici DSL, aby bylo možné přepsat vygenerovaný metodu.

-   Nastavení možností v definici DSL, která způsobí, že generovaný kód k poskytnutí "zachytávání" pro váš vlastní kód.

     Pokud nastavíte například **má vlastní konstruktor** možnost doménové třídy a začnete vytvářet řešení, zobrazí se chybové zprávy. Když dvakrát kliknete na jednu z těchto chybových zpráv, zobrazí se poznámky v generovaném kódu, které popisují, co by měly poskytnout vlastní kód.

-   Zápis textové šablony pro generování kódu, které jsou specifické pro vaši aplikaci. Vám může zahrnovat použití souborů sdílet části šablony, které jsou společné pro mnoho projektů, a můžete vytvořit šablony projektů Visual Studio k nastavení projektů, které jsou inicializovány pomocí strukturu souboru.

## <a name="generated-files-in-dsl"></a>Generované soubory v Dsl
 Tyto vygenerované soubory se zobrazí v **Dsl** projektu.

 *YourDsl* `Schema.xsd`

 Schéma pro soubory, které obsahuje instance tohoto kódu DSL. Tento soubor je zkopírován do kompilace (**bin**) adresáře. Při instalaci vašeho DSL tento soubor můžete zkopírovat **\Program Files\Microsoft sady Visual Studio 11.0\Xml\Schemas** tak, aby soubory modelu může být ověřen. Další informace najdete v tématu [nasazení řešení jazyka specifického pro doménu](../modeling/deploying-domain-specific-language-solutions.md).

 Pokud upravíte serializace nastavením možnosti v Průzkumník DSL, schéma odpovídajícím způsobem měnit. Ale pokud píšete kód serializace, tento soubor může být už nepředstavují skutečné schématu. Další informace najdete v tématu [přizpůsobení souborového úložiště a serializace XML](../modeling/customizing-file-storage-and-xml-serialization.md).

 `ConnectionBuilders.cs`

 Tvůrce připojení je třída, která vytvoří vztah. Je kód za nástroj pro připojení. Tento soubor obsahuje pár tříd pro každý nástroj pro připojení. Jejich názvy jsou odvozeny od názvů nástroj relace a připojení k doméně: *vztah*tvůrce, a *ConnectorTool*ConnectAction.

 (V příkladu součást řešení, jedna tvůrci připojení se nazývá Tvůrce propojení, nezdá, důvodem je, že připojení názvem doménového vztahu.)

 Relace je vytvořena v *vztah* `Builder.Connect()` metody. Výchozí verze ověří, zda jsou přijatelné zdrojové a cílové prvky modelu a poté vytvoří instanci relace. Příklad:

 `CommentReferencesSubject(sourceAccepted, targetAccepted);`

 Každá třída Tvůrce generováno v uzlu **tvůrci připojení** části v Průzkumník DSL. Jeden `Connect` metoda můžete vytvářet vztahy mezi jeden nebo více párů doménovými třídami. Každý pár je definována direktivu připojení propojení, které můžete vyhledat v Průzkumníku DSL pod uzlem Tvůrce.

 Můžete třeba přidat do jednoho připojení Tvůrce připojení direktivy odkazu pro všechny tři typy vztahů v ukázce DSL. To by poskytnout uživateli nástroj pro jedno připojení. Typ vztahu vytvořena instance bude záviset na typy prvků zdrojového a cílového vybraný uživatelem.  Přidání připojení direktivy propojení, klikněte pravým tlačítkem na tvůrce v Průzkumník DSL.

 Psát vlastní kód, který se spustí, jakmile se vytvoří konkrétní typ doménového vztahu, vyberte odpovídající odkaz připojení direktiva pod uzlem Tvůrce. V okně Vlastnosti nastavte **používá vlastní připojení**. Znovu sestavte řešení a pak poskytnete kód, chcete-li opravit případné chyby.

 Chcete-li napsat vlastní kód, který se spustí pokaždé, když uživatel používá tento nástroj pro připojení, nastavte **je vlastní** vlastnosti Tvůrce připojení. Můžete zadat kód, který určuje, jestli je povolený zdroj element, zda konkrétní kombinaci zdroje a smí obsahovat cílové a co aktualizuje by měl modelu při vytvoření připojení. Například může povolit připojení pouze v případě, že by vytvořilo smyčku v diagramu. Namísto odkazu na jeden vztah může vytvořit instanci složitější vzor několik mezi souvisejících prvků mezi zdrojem a cílem.

 `Connectors.cs`

 Obsahuje třídy pro konektory, které jsou elementy diagramu, které obvykle představují referenční stavy. Každá třída nevygeneruje jeden konektor v definici DSL. Každý konektor třídy je odvozen z <xref:Microsoft.VisualStudio.Modeling.Diagrams.BinaryLinkShape>

 Chcete-li barvu a některé jiné proměnné stylu funkce v době běhu, klikněte pravým tlačítkem na třídu v diagramem definice DSL a přejděte na **přidat vystavený**.

 Chcete-li proměnná další šablony funkce v době běhu, viz například <xref:Microsoft.VisualStudio.Modeling.Diagrams.TextField> a <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement>.

 `Diagram.cs`

 Obsahuje třídy, která definuje diagramu. Je odvozen z <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram>.

 Chcete-li barvu a některé jiné proměnné stylu funkce v době běhu, klikněte pravým tlačítkem na třídu v diagramem definice DSL a přejděte na **přidat vystavený**.

 Kromě toho tento soubor obsahuje `FixupDiagram` pravidlo, které jsou reaguje, když se přidá nový prvek do modelu. Pravidlo přidá nový tvar a odkazy na obrazec na prvek modelu.

 `DirectiveProcessor.cs`

 Tento procesor direktiv pomáhá uživatelům pro zápis textových šablon, které čtou instance tohoto kódu DSL. Procesor direktiv načte sestavení (knihovny DLL) pro vaše DSL a efektivně vloží `using` příkazy pro váš obor názvů. To umožňuje kód v textové šablony k používání tříd a vztahů, které jste definovali v vašeho DSL.

 Další informace najdete v tématu [generování kódu z jazyka specifického pro doménu](../modeling/generating-code-from-a-domain-specific-language.md) a [vytváření vlastních procesorů textových šablon T4 – direktiva](../modeling/creating-custom-t4-text-template-directive-processors.md).

 `DomainClasses.cs`

 Implementace třídy domény, které jste definovali, včetně abstraktní třídy a kořenová třída modelu. Jsou odvozeny z <xref:Microsoft.VisualStudio.Modeling.ModelElement>.

 Každá doménová třída obsahuje:

- Definice vlastnosti a třída vnořené obslužné rutiny pro každou vlastnost domény. Můžete přepsat OnValueChanging() a OnValueChanged(). Další informace najdete v tématu [obslužné rutiny změny hodnoty vlastnosti domény](../modeling/domain-property-value-change-handlers.md).

   V příkladu DSL `Comment` třída obsahuje vlastnosti `Text` a třídu obslužné rutiny `TextPropertyHandler`.

- Přistupující objekt vlastnosti relace, ve kterých se účastní této doménové třídě. (Neexistuje žádné vnořené třídy pro vlastnosti role.)

   V příkladu DSL `Comment` třída nemá přistupující objekty, které přistupují k její nadřazené modelu prostřednictvím vztah obsažení `ComponentModelHasComments`.

- Konstruktory. Pokud chcete tyto přepsat, nastavte **má vlastní konstruktor** na doménové třídy.

- Element metody obslužné rutiny skupiny prototypu (EGP). To je nezbytné, pokud uživatel může *sloučení* (Přidat) jiný element do instance této třídy. Obvykle uživatel to dělá přetažením z nástroj element nebo jiný tvar nebo vložením.

   V příkladu DSL, Port vstupní nebo výstupní Port sloučit do komponenty. Navíc komponenty a komentáře lze sloučit do modelu. Rozhraní

   Metody obslužné rutiny EGP ve třídě součást povolit komponentu tak, aby přijímal porty, ale ne komentáře. Obslužná rutina EGP ve třídě kořenové model přijímá komentáře a komponenty, ale ne porty.

  `DomainModel.cs`

  Třída, která představuje model domény. Je odvozen z <xref:Microsoft.VisualStudio.Modeling.DomainModel>.

> [!NOTE]
>  To však není stejný jako kořenová třída modelu.

 Kopírování a odstranit uzávěry definovat další prvky, které je třeba zahrnout při elementu zkopíruje nebo odstranit. Toto chování můžete ovládat nastavením **šíří kopírování** a **šíří odstranit** Vlastnosti rolí na každé straně všech relací. Pokud chcete hodnoty, které mají být dynamicky rozlišit, můžete napsat kód k přepsání metod třídy uzavření.

 `DomainModelResx.resx`

 Tato položka obsahuje řetězce, jako jsou popisy doménové třídy a vlastnosti, názvy vlastností, panel nástrojů popisky, standardní chybové zprávy a jiných řetězců, které se může zobrazovat uživateli. Obsahuje taky nástroje ikonami a obrázky, obrazce obrázku.

 Tento soubor je vázán na sestavení a poskytuje výchozí hodnoty těchto prostředků. Vytvořením satelitní sestavení, která obsahuje lokalizované verzi prostředky je možné lokalizovat vašeho DSL. Tato verze se použije při instalaci DSL v jazykové verzi odpovídající lokalizované prostředky. Další informace najdete v tématu [nasazení řešení jazyka specifického pro doménu](../modeling/deploying-domain-specific-language-solutions.md).

 `DomainRelationships.cs`

 Každé propojení mezi dvěma prvky v modelu je reprezentován instance třída doménového vztahu. Všechny relace třídy jsou odvozeny z <xref:Microsoft.VisualStudio.Modeling.ElementLink>, který je zase odvozen z <xref:Microsoft.VisualStudio.Modeling.ModelElement>. Protože se jedná ModelElement, instance vztahu může mít vlastnosti a může být zdroj nebo cíl relace.

 `HelpKeywordHelper.cs`

 Poskytuje funkce, které se používají, když uživatel stiskne klávesu F1.

 `MultiplicityValidation.cs`

 V části role vztahu zadávat násobnost 1..1 nebo 1.. *, uživatel by měl být upozornění na tento alespoň jednu instanci relace je povinný. Tento soubor obsahuje omezení ověření, které implementují těchto upozornění. 1..1 propojení s nadřazenou položkou vkládání není ověřený.

 K těmto omezením, který se spustí, musíte mít nastavit jednu z **používá...**  možnosti **Editor\Validation** uzel v Průzkumník DSL. Další informace najdete v tématu [ověřování v jazyka specifického pro doménu](../modeling/validation-in-a-domain-specific-language.md).

 `PropertiesGrid.cs`

 Tento soubor obsahuje kód, pouze v případě, že jste přiřadili popisovači vlastního typu na doménovou vlastnost. Další informace najdete v tématu [přizpůsobení okna vlastnosti](../modeling/customizing-the-properties-window.md).

 `SerializationHelper.cs`

- Metoda ověření k zajištění, že žádné dva prvky je odkazováno dle stejného moniker. Další informace najdete v tématu [přizpůsobení souborového úložiště a serializace XML](../modeling/customizing-file-storage-and-xml-serialization.md).

- Třída SerializationHelper, která poskytuje funkce, které se používají v běžných třídami serializace.

  `Serializer.cs`

  Třída serializátoru pro každou doménovou třídu, relace, tvar, konektor, diagramu a modelu.

  Řadu funkcí, které z těchto tříd mohou být řízena nastavení v Průzkumník DSL pod **chování serializace Xml**.

  `Shapes.cs`

  Třídy pro každou třídu tvar v definici DSL. Tvary jsou odvozeny z <xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape>. Další informace najdete v tématu [přizpůsobení souborového úložiště a serializace XML](../modeling/customizing-file-storage-and-xml-serialization.md).

  Chcete-li přepsat metody generované vašimi vlastními metodami v dílčí třídě, nastavte **Generates Double Derived** pro konektor v definici DSL. Chcete-li nahradit konstruktor s vlastním kódem, nastavte **má vlastní konstruktor**.

  Chcete-li barvu a některé jiné proměnné stylu funkce v době běhu, klikněte pravým tlačítkem na třídu v diagramem definice DSL a přejděte na **přidat vystavený**.

  Chcete-li proměnná další šablony funkce v době běhu, viz například <xref:Microsoft.VisualStudio.Modeling.Diagrams.TextField> a <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement>

  `ToolboxHelper.cs`

  Nastaví panelu nainstalováním prvek skupiny prototypy do nástrojů elementu. Kopie těchto prototypů jsou sloučeny s cílových elementů, když uživatel spustí nástroj.

  Může přepsat `CreateElementPrototype()` definovat položku sady nástrojů, který vytvoří skupiny několika objektů. Můžete například definovat položku k reprezentaci objektů, které mají dílčí komponenty. Po změně kódu, resetujte experimentální instanci sady Visual Studio a vymažte mezipaměť sady nástrojů.

## <a name="generated-files-in-the-dslpackage-project"></a>Generované soubory v projektu DslPackage
 DslPackage páry v odstupu modelu DSL do prostředí nástroje Visual Studio, Správa oken, nástrojů a nabídky příkazů. Většina tříd jsou double odvozena, tak, aby jejich metod můžete přepsat.

 `CommandSet.cs`

 Příkazy místní nabídky, které jsou viditelné v diagramu. Můžete upravit nebo přidat do této sady. Tento soubor obsahuje kód pro příkazy. Určuje umístění příkazů v nabídkách Commands.vsct souboru. Další informace najdete v tématu [zápis uživatelských příkazů a akcí](../modeling/writing-user-commands-and-actions.md).

 `Constants.cs`

 Identifikátory GUID.

 `DocData.cs`

 *YourDsl* `DocData` spravuje načítání a ukládání modelu do souboru a vytvoří instanci Store.

 Například pokud chcete uložit vašeho DSL v databázi místo souboru, je může přepsat `Load` a `Save` metody.

 `DocView.cs`

 *YourDsl* `DocView` spravuje okno, ve kterém se zobrazí v diagramu. Například můžete vložit do diagramu do formuláře windows:

 Přidáte uživatelský ovládací prvek souboru do projektu DslPackage. Přidání panelu, ve kterém lze zobrazit v diagramu. Přidáte tlačítka a další ovládací prvky. V zobrazení kódu formuláře přidejte následující kód, úprava názvů do vašeho DSL:

```csharp
using System;
using System.Collections.Generic;
using System.ComponentModel;
using System.Drawing;
using System.Data;
using System.Linq;
using System.Text;
using System.Windows.Forms;
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Shell;

namespace Company.EmbedInForm
{
  public partial class UserControl1 : UserControl
  {
    public UserControl1()
    {
      InitializeComponent();
    }

    private DiagramDocView docView;

    public UserControl1(DiagramDocView docView, Control content)
      : this()
    {
      this.docView = docView;
      panel1.Controls.Add(content);
    }

    private void button1_Click(object sender, EventArgs e)
    {
      ExampleModel modelRoot = this.docView.CurrentDiagram.ModelElement as ExampleModel;
      foreach (ExampleElement element in modelRoot.Elements)
      {
       listBox1.Items.Add(element.Name);
      }
    }
  }
  internal partial class EmbedInFormDocView
  {

    private ContainerControl container;

    /// <summary>
    /// Return a User Control instead of the DSL window.
    /// The user control will contain the DSL window.
    /// </summary>

    public override System.Windows.Forms.IWin32Window Window
    {
      get
      {
        if (container == null)
        {
          // Put the normal DSL Window inside our control
          container = new UserControl1(this, (Control)base.Window);
        }
        return container;
      }
    }
  }

}
```

 `EditorFactory.cs`

 Vytvoří instanci `DocData` a `DocView`. Vyřizuje standardní rozhraní, které Visual Studio používá k otevření editoru při spuštění balíčku DSL. Je odkazováno v `ProvideEditorFactory` atribut v Package.cs

 `GeneratedVSCT.vsct`

 Vyhledá standardní příkazy v nabídkách, jako je například místní nabídky diagramu **upravit** nabídky a tak dále. Kód pro příkazy je v CommandSet.cs. Můžete přemístit nebo standardní příkazy upravit, a můžete přidat vlastní příkazy. Další informace najdete v tématu [zápis uživatelských příkazů a akcí](../modeling/writing-user-commands-and-actions.md).

 `ModelExplorer.cs`

 Definuje Průzkumníka modelů pro vaše DSL. Toto je stromové zobrazení modelu, který se uživateli zobrazí vedle diagramu.

 Je třeba přepsat `InsertTreeView()` Chcete-li změnit pořadí, ve kterém se elementy zobrazí v Průzkumníku modelů.

 Pokud chcete výběr v Průzkumníku modelů udržovat synchronizované s výběrem diagramu, můžete použít následující kód:

```
protected override void OnSelectionChanged(global::System.EventArgs e)
{
base.OnSelectionChanged(e);
// get the selected element
DslModeling::ModelElement selectedElement =
this.PrimarySelection as DslModeling::ModelElement;
// Select in the model explorer
SelectInModelExplorer<YOURLANGUAGEExplorerToolWindow>(selectedElement);
}
private void SelectInModelExplorer<T>(DslModeling::ModelElement modelElement)
where T : DslShell.ModelExplorerToolWindow
{
DslShell::ModelingPackage package =
this.GetService(typeof(VSShell.Package)) as DslShell::ModelingPackage;

if (package != null)
{
// find the model explorer window
T explorerWindow = package.GetToolWindow(typeof(T), true) as T;
if (explorerWindow != null)
{
// get the tree container
DslShell.ModelExplorerTreeContainer treeContainer =
explorerWindow.TreeContainer;
// find the tree node
DslShell.ExplorerTreeNode treeNode =
treeContainer.FindNodeForElement(modelElement);
// select the node
explorerWindow.TreeContainer.ObjectModelBrowser.SelectedNode = treeNode;
}
}
}
```

 `ModelExplorerToolWindow.cs`

 Definuje okno, ve kterém se zobrazí v Průzkumníku modelu. Výběr položek v Průzkumníku zpracovává.

 `Package.cs`

 Tento soubor definuje, jak se integruje do sady Visual Studio DSL. Atributy ve třídě balíčku zaregistrujte DSL jako popisovač pro soubory, které vaše rozšíření souboru, definovat jeho nástrojů a definovat, jak otevřít nové okno. Metoda Initialize() se volá jednou při prvním DSL je načten do instance sady Visual Studio.

 `Source.extension.vsixmanifest`

 Chcete-li tento soubor upravit, upravit `.tt` souboru.

> [!WARNING]
>  Při úpravě souboru .tt prostředky, jako jsou ikony nebo obrázky, ujistěte se, že prostředek je zahrnuta v sestavení VSIX. V Průzkumníku řešení, vyberte ho a ujistěte se, že **zahrnout do VSIX** vlastnost `True`.

 Tento soubor řídí, jak DSL je zabalená do Visual Studio integrace rozšíření (VSIX). Další informace najdete v tématu [nasazení řešení jazyka specifického pro doménu](../modeling/deploying-domain-specific-language-solutions.md).

## <a name="see-also"></a>Viz také

- [Jak se definuje jazyk specifický pro doménu](../modeling/how-to-define-a-domain-specific-language.md)
- [Porozumění modelům, třídám a vztahům](../modeling/understanding-models-classes-and-relationships.md)
- [Přizpůsobení a rozšíření jazyka specifického pro doménu](../modeling/customizing-and-extending-a-domain-specific-language.md)
- [Zápis kódu pro úpravu jazyka specifického pro doménu](../modeling/writing-code-to-customise-a-domain-specific-language.md)
