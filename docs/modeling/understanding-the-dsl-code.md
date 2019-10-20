---
title: Porozumění kódu DSL
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, generated code
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 34ec62310c2c9b9677f682983fc6d87827057151
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663800"
---
# <a name="understanding-the-dsl-code"></a>Porozumění kódu DSL

Řešení DSL (Domain-Specific Language) generuje rozhraní API, které můžete použít ke čtení a aktualizaci instancí DSL v aplikaci Visual Studio. Toto rozhraní API je definováno v kódu, který je generován z definice DSL. Toto téma popisuje vygenerované rozhraní API.

## <a name="the-example-solution-component-diagrams"></a>Ukázkové řešení: diagramy komponent

Chcete-li vytvořit řešení, které je zdrojem většiny příkladů v tomto tématu, vytvořte DSL ze šablony řešení **modelů komponent** . Jedná se o jednu ze standardních šablon, které se zobrazí při vytváření nového řešení DSL.

> [!NOTE]
> Šablona DSL diagramů komponent se nazývá **Návrhář jazyka specifického pro doménu**.

Pokud neznáte tuto šablonu řešení, stiskněte klávesu **F5** a Experimentujte. Všimněte si, že je třeba vytvořit porty přetažením nástroje port do komponenty a zda můžete připojit porty.

![Komponenty a propojené porty](../modeling/media/componentsample.png)

## <a name="the-structure-of-the-dsl-solution"></a>Struktura řešení DSL
 Projekt **DSL** definuje rozhraní API pro vaši DSL. Projekt **DslPackage** definuje způsob, jakým se integruje se sadou Visual Studio. Můžete také přidat vlastní projekty, které mohou také obsahovat kód vygenerovaný z modelu.

### <a name="the-code-directories"></a>Adresáře kódu
 Většina kódu v každém z těchto projektů je vygenerována z **Dsl\DslDefinition.DSL**. Vygenerovaný kód je ve složce **generovaného kódu** . Chcete-li zobrazit vygenerovaný soubor, klikněte na tlačítko **[+]** vedle vygenerovaného souboru **. TT** .

 Doporučujeme, abyste zkontrolovali vygenerovaný kód, který vám pomůže pochopit DSL. Chcete-li zobrazit vygenerované soubory, rozbalte soubory *. TT v Průzkumník řešení.

 Soubory \*. TT obsahují velmi malý kód pro generování kódu. Místo toho používají direktivy `<#include>` pro zahrnutí souborů sdílené šablony. Sdílené soubory najdete ve složce **\Program Files\Microsoft Visual Studio 10.0 \ COMMON7\IDE\EXTENSIONS\MICROSOFT\DSL SDK\DSL Designer\11.0\TextTemplates**

 Když do řešení DSL přidáte vlastní kód programu, přidejte ho do samostatného souboru, mimo složku vygenerovaného kódu. Je možné, že budete chtít vytvořit vlastní složku s **kódem** . (Když přidáte nový soubor kódu do vlastní složky, nezapomeňte opravit obor názvů v úvodní kostrě kódu.)

 Důrazně doporučujeme, abyste generovaný kód neupravili přímo, protože při opětovném sestavování řešení dojde ke ztrátě vašich úprav. Místo toho můžete přizpůsobit DSL:

- Upravte mnoho parametrů v definici DSL.

- Zápis dílčích tříd do samostatných souborů kódu, pro přepsání metod, které jsou definovány v nebo zděděných pomocí, generovaných tříd. V některých případech je nutné nastavit možnost **Generovat dvojitě odvozenou** možnost třídy v definici DSL, aby bylo možné přepsat vygenerovanou metodu.

- Nastavte možnosti v definici DSL, které způsobí, že generovaný kód poskytne "háky" pro vlastní kód.

     Například pokud nastavíte možnost **má vlastní konstruktor** třídy domény a pak sestavíte řešení, zobrazí se chybové zprávy. Když dvakrát kliknete na jednu z těchto chybových zpráv, zobrazí se komentáře ve vygenerovaném kódu, který vysvětluje, co by měl váš vlastní kód poskytovat.

- Zápis vlastních textových šablon pro vygenerování kódu specifického pro vaši aplikaci. Můžete použít vložené soubory ke sdílení částí šablon, které jsou společné pro mnoho projektů, a můžete vytvořit šablony projektů sady Visual Studio pro nastavení projektů, které jsou inicializovány s vlastní strukturou souborů.

## <a name="generated-files-in-dsl"></a>Vygenerované soubory v DSL
 V projektu **DSL** se zobrazí následující vygenerované soubory.

 *YourDsl* `Schema.xsd`

 Schéma pro soubory, které obsahují instance vaší DSL. Tento soubor je zkopírován do adresáře Compilation (**bin**). Když nainstalujete DSL, můžete tento soubor zkopírovat do **složky \Program Files\Microsoft Visual Studio 11.0 \ Xml\Schemas** , aby bylo možné ověřit soubory modelů. Další informace najdete v tématu [nasazení řešení jazyka specifického pro doménu](msi-and-vsix-deployment-of-a-dsl.md).

 Pokud přizpůsobíte serializaci nastavením možností v Průzkumníku DSL, schéma se odpovídajícím způsobem změní. Nicméně pokud zapíšete vlastní Serializační kód, tento soubor pravděpodobně nebude reprezentovat skutečné schéma. Další informace naleznete v tématu [přizpůsobení File Storage a serializace XML](../modeling/customizing-file-storage-and-xml-serialization.md).

 `ConnectionBuilders.cs`

 Tvůrce připojení je třída, která vytváří relace. Jedná se o kód za nástrojem pro připojení. Tento soubor obsahuje dvojici tříd pro každý nástroj pro připojení. Jejich názvy jsou odvozeny z názvů doménového vztahu a nástroje připojení: Tvůrce *vztahů*a *ConnectorTool*ConnectAction.

 (V příkladu řešení komponenty se jeden ze tvůrců připojení nazývá tvůrci propojení, jedná se o spoludopad, protože doménový vztah se nazývá připojení.)

 Relace je vytvořena v metodě `Builder.Connect()` *vztahu* . Výchozí verze ověří, zda jsou prvky zdrojového a cílového modelu přijatelné, a poté vytvoří instanci vztahu. Příklad:

 `CommentReferencesSubject(sourceAccepted, targetAccepted);`

 Každá třída tvůrce je vygenerována z uzlu v části **tvůrci připojení** v Průzkumníku DSL. Jedna `Connect` metoda může vytvářet relace mezi jednou nebo více páry doménových tříd. Každý pár je definovaný direktivou Connect Link, kterou můžete najít v Průzkumníkovi DSL pod uzlem tvůrce.

 Můžete například přidat do jedné direktivy propojení odkazů Tvůrce připojení pro každý ze tří typů vztahů v ukázce DSL. To uživateli poskytne Nástroj pro jeden připojení. Typ vytvořeného vztahu by měl záviset na typech zdrojového a cílového prvku vybraného uživatelem.  Chcete-li přidat direktivy propojení odkazů, klikněte pravým tlačítkem myši na tvůrce v Průzkumníku DSL.

 Chcete-li napsat vlastní kód, který se spustí při vytvoření konkrétního typu doménového vztahu, vyberte odpovídající direktivu Connect Link v uzlu Tvůrce. V okno Vlastnosti nastavení **používá vlastní připojení**. Znovu sestavte řešení a pak Dodejte kód pro opravu výsledných chyb.

 Chcete-li napsat vlastní kód, který se spustí pokaždé, když uživatel používá tento nástroj pro připojení, nastavte vlastnost **je vlastní** vlastnosti Tvůrce připojení. Můžete dodat kód, který rozhoduje, jestli je zdrojový prvek povolený, jestli je povolená konkrétní kombinace zdroje a cíle, a jaké aktualizace se mají provést v modelu, když se nastavilo připojení. Připojení můžete například dovolit pouze v případě, že by v diagramu nevytvořila smyčku. Místo propojení jedna relace můžete vytvořit instanci složitějšího vzoru několika vzájemně souvisejících prvků mezi zdrojem a cílem.

 `Connectors.cs`

 Obsahuje třídy pro konektory, které jsou prvky diagramu, které typicky představují referenční vztahy. Každá třída je vygenerována z jednoho konektoru v definici DSL. Každá třída konektoru je odvozena z <xref:Microsoft.VisualStudio.Modeling.Diagrams.BinaryLinkShape>

 Chcete-li nastavit barvu a některé jiné funkce stylu v době běhu, klikněte pravým tlačítkem myši na třídu v diagramu definice DSL a přejděte na **Přidat vystaveno**.

 Chcete-li nastavit další funkce stylu za běhu, přečtěte si například <xref:Microsoft.VisualStudio.Modeling.Diagrams.TextField> a <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement>.

 `Diagram.cs`

 Obsahuje třídu, která definuje diagram. Je odvozen z <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram>.

 Chcete-li nastavit barvu a některé jiné funkce stylu v době běhu, klikněte pravým tlačítkem myši na třídu v diagramu definice DSL a přejděte na **Přidat vystaveno**.

 Kromě toho tento soubor obsahuje pravidlo `FixupDiagram`, které reaguje na přidání nového prvku do modelu. Pravidlo přidá nový tvar a propojí obrazec s prvkem modelu.

 `DirectiveProcessor.cs`

 Tento procesor direktiv pomáhá uživatelům psát textové šablony, které čtou instanci vaší DSL. Procesor direktiv načte sestavení (knihovny DLL) pro vaši DSL a efektivně vloží `using` příkazy pro váš obor názvů. To umožňuje, aby kód v textových šablonách používal třídy a vztahy, které jste definovali v DSL.

 Další informace najdete v tématu [generování kódu z jazyka specifického pro doménu](../modeling/generating-code-from-a-domain-specific-language.md) a [vytváření vlastních procesorů pro direktivy textových šablon T4](../modeling/creating-custom-t4-text-template-directive-processors.md).

 `DomainClasses.cs`

 Implementace tříd domény, které jste definovali, včetně abstraktních tříd a kořenové třídy modelu. Jsou odvozeny z <xref:Microsoft.VisualStudio.Modeling.ModelElement>.

 Každá doménová třída obsahuje:

- Definice vlastnosti a vnořená třída obslužné rutiny pro každou doménovou vlastnost. Můžete přepsat OnValueChanging () a OnValueChanged (). Další informace najdete v tématu [obslužné rutiny změny hodnoty vlastnosti domény](../modeling/domain-property-value-change-handlers.md).

   V příkladu DSL obsahuje Třída `Comment` vlastnost `Text` a `TextPropertyHandler` třídy obslužné rutiny.

- Vlastnosti přístupového objektu pro vztahy, ve kterých se tato doménová třída podílí. (Pro vlastnosti role neexistuje žádná vnořená třída.)

   V příkladu DSL má třída `Comment` přistupující objekty, které přistupují k nadřazenému modelu pomocí `ComponentModelHasComments` relace vložení.

- Konstruktory. Pokud je chcete přepsat, nastavte u třídy doména **vlastní konstruktor** .

- Metody obslužné rutiny prototypu skupiny elementů (EGP). Ty jsou nezbytné, pokud uživatel může *Sloučit* (Přidat) jiný prvek do instancí této třídy. Uživatel to obvykle provede přetažením z nástroje prvku nebo jiného tvaru nebo vložením.

   V příkladu DSL je možné do komponenty sloučit vstupní port nebo výstupní port. Součásti a komentáře lze také sloučit do modelu. Rozhraní

   Metody obslužné rutiny EGP ve třídě Component umožňují komponentě přijímat porty, ale ne komentáře. Obslužná rutina EGP v kořenové třídě modelu akceptuje komentáře a komponenty, ale ne porty.

  `DomainModel.cs`

  Třída, která představuje doménový model. Je odvozen z <xref:Microsoft.VisualStudio.Modeling.DomainModel>.

> [!NOTE]
> Nejedná se o shodu s kořenovou třídou modelu.

 Kopírovat a odstranit uzávěry definují, jaké další prvky by měly být zahrnuty při kopírování nebo odstranění prvku. Toto chování můžete řídit nastavením **šířit kopírování** a **rozšířením odstranit** vlastnosti rolí na každé straně každé relace. Pokud chcete, aby byly hodnoty určovány dynamicky, můžete napsat kód pro přepsání metod třídy uzávěry.

 `DomainModelResx.resx`

 To obsahuje řetězce, jako jsou popisy tříd domény a vlastností, názvy vlastností, popisky panelu nástrojů, standardní chybové zprávy a další řetězce, které by se mohly zobrazit uživateli. Obsahuje také ikony a obrázky nástrojů pro obrazové tvary.

 Tento soubor je svázán s sestaveným sestavením a poskytuje výchozí hodnoty těchto prostředků. Můžete lokalizovat DSL vytvořením satelitního sestavení, které obsahuje lokalizovanou verzi prostředků. Tato verze se použije, když je DSL nainstalovaná v jazykové verzi odpovídající lokalizovaným prostředkům. Další informace najdete v tématu [nasazení řešení jazyka specifického pro doménu](msi-and-vsix-deployment-of-a-dsl.md).

 `DomainRelationships.cs`

 Každé propojení mezi dvěma prvky v modelu je reprezentované instancí třídy doménového vztahu. Všechny třídy vztahů jsou odvozeny od <xref:Microsoft.VisualStudio.Modeling.ElementLink>, které jsou zase odvozeny od <xref:Microsoft.VisualStudio.Modeling.ModelElement>. Vzhledem k tomu, že se jedná o ModelElement, může mít instance relace vlastnosti a může být zdrojem nebo cílem vztahu.

 `HelpKeywordHelper.cs`

 Poskytuje funkce, které se používají, když uživatel stiskne klávesu F1.

 `MultiplicityValidation.cs`

 V rolích vztahů, kde zadáte násobnost 1.. 1 nebo 1.. *, by měl uživatel být upozorněn na to, že je požadována alespoň jedna instance relace. Tento soubor poskytuje omezení ověřování, která implementují tato upozornění. Odkaz 1.. 1 na nadřazený objekt pro vložení není ověřen.

 Aby tato omezení byla provedena, je nutné nastavit jednu z možností **použití..** . v uzlu **EDITOR\VALIDATION** v Průzkumníku DSL. Další informace najdete v tématu [ověření v jazyce specifickém pro doménu](../modeling/validation-in-a-domain-specific-language.md).

 `PropertiesGrid.cs`

 Tento soubor obsahuje kód pouze v případě, že jste připojili vlastní popisovač typu k doménové vlastnosti. Další informace najdete v tématu [přizpůsobení okna vlastností](../modeling/customizing-the-properties-window.md).

 `SerializationHelper.cs`

- Metoda ověření, která zajistí, že žádný ze dvou prvků není odkazován stejným monikerem. Další informace naleznete v tématu [přizpůsobení File Storage a serializace XML](../modeling/customizing-file-storage-and-xml-serialization.md).

- Třída SerializationHelper, která poskytuje funkce, které jsou používány společnými třídami serializace.

  `Serializer.cs`

  Třída serializátoru pro každou doménovou třídu, vztah, obrazec, spojnici, diagram a model.

  Mnohé z funkcí těchto tříd lze ovládat pomocí nastavení v Průzkumníku DSL v části **chování serializace XML**.

  `Shapes.cs`

  Třída pro každou třídu Shape v definici DSL Tvary jsou odvozeny z <xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape>. Další informace naleznete v tématu [přizpůsobení File Storage a serializace XML](../modeling/customizing-file-storage-and-xml-serialization.md).

  Chcete-li vygenerované metody přepsat vlastními metodami v částečné třídě, sada pro konektor v definici DSL **vygeneruje dvojitou odvozenou** hodnotu. Chcete-li nahradit konstruktor vlastním kódem, nastavte **má vlastní konstruktor**.

  Chcete-li nastavit barvu a některé jiné funkce stylu v době běhu, klikněte pravým tlačítkem myši na třídu v diagramu definice DSL a přejděte na **Přidat vystaveno**.

  Chcete-li nastavit další funkce stylu v době běhu, přejděte například <xref:Microsoft.VisualStudio.Modeling.Diagrams.TextField> a <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement>

  `ToolboxHelper.cs`

  Nastaví sadu nástrojů tak, že do nástrojů prvku nainstaluje prototypy skupiny prvků. Kopie těchto prototypů jsou sloučeny s cílovými prvky, když uživatel spustí nástroj.

  Můžete přepsat `CreateElementPrototype()` pro definování položky sady nástrojů, která vytvoří skupinu několika objektů. Například můžete definovat položku pro reprezentaci objektů, které mají dílčí komponenty. Po změně kódu obnovte experimentální instanci sady Visual Studio, čímž vymažete mezipaměť sady nástrojů.

## <a name="generated-files-in-the-dslpackage-project"></a>Generované soubory v projektu DslPackage
 DslPackage Couples model DSL do prostředí sady Visual Studio a spravuje příkazy okna, panelu nástrojů a nabídky. Většina tříd je dvojitě odvozena, takže můžete přepsat jakoukoli z jejich metod.

 `CommandSet.cs`

 Příkazy nabídky po kliknutí pravým tlačítkem, které jsou viditelné v diagramu. Tuto sadu můžete přizpůsobovat nebo přidat. Tento soubor obsahuje kód pro příkazy. Umístění příkazů v nabídkách je určeno souborem Commands. vsct. Další informace najdete v tématu [zápis uživatelských příkazů a akcí](../modeling/writing-user-commands-and-actions.md).

 `Constants.cs`

 Identifikátory GUID.

 `DocData.cs`

 *YourDsl* `DocData` spravuje načítání a ukládání modelu do souboru a vytváří instanci úložiště.

 Pokud například chcete uložit DSL v databázi místo souboru, můžete přepsat `Load` a `Save` metody.

 `DocView.cs`

 *YourDsl* `DocView` spravuje okno, ve kterém se diagram zobrazuje. Diagram můžete například vložit do formuláře Windows:

 Přidejte do projektu DslPackage soubor uživatelského ovládacího prvku. Přidejte panel, ve kterém lze diagram zobrazit. Přidejte tlačítka a další ovládací prvky. V zobrazení kódu formuláře přidejte následující kód, kterým upravíte názvy DSL:

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

 Vytvoří instanci `DocData` a `DocView`. Splňuje standardní rozhraní, které sada Visual Studio používá k otevření editoru při spuštění vašeho balíčku DSL. Je odkazováno v atributu `ProvideEditorFactory` v Package.cs

 `GeneratedVSCT.vsct`

 Vyhledá standardní příkazy nabídky v nabídkách, například v diagramu klikněte pravým tlačítkem myši na nabídku (kontext), nabídce **Upravit** a tak dále. Kód pro příkazy je v CommandSet.cs. Můžete přemístit nebo upravit standardní příkazy a můžete přidat vlastní příkazy. Další informace najdete v tématu [zápis uživatelských příkazů a akcí](../modeling/writing-user-commands-and-actions.md).

 `ModelExplorer.cs`

 Definuje Průzkumníka modelů pro vaši DSL. Toto je stromové zobrazení modelu, který uživatel vidí vedle diagramu.

 Můžete například přepsat `InsertTreeView()` pro změnu pořadí, ve kterém se prvky zobrazí v Průzkumníku modelů.

 Pokud chcete, aby výběr v Průzkumníkovi modelů udržoval synchronizaci s výběrem diagramu, můžete použít následující kód:

```csharp
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

 Definuje okno, ve kterém se Průzkumník modelů zobrazuje. Zpracovává výběr položek v Průzkumníkovi.

 `Package.cs`

 Tento soubor definuje, jak se DSL integruje do sady Visual Studio. Atributy třídy Package registrují DSL jako obslužnou rutinu pro soubory, které mají příponu souboru, definují její sadu nástrojů a definují, jak otevřít nové okno. Metoda Initialize () je volána jednou, když je první DSL načtena do instance sady Visual Studio.

 `Source.extension.vsixmanifest`

 Chcete-li tento soubor přizpůsobit, upravte soubor `.tt`.

> [!WARNING]
> Pokud upravujete soubor. TT tak, aby zahrnoval prostředky, jako jsou ikony nebo obrázky, ujistěte se, že je prostředek součástí sestavení VSIX. V Průzkumník řešení vyberte soubor a ujistěte se, že je `True` **zahrnout do vlastnosti VSIX** .

 Tento soubor určuje, jak se DSL zabalí do rozšíření integrace sady Visual Studio (VSIX). Další informace najdete v tématu [nasazení řešení jazyka specifického pro doménu](msi-and-vsix-deployment-of-a-dsl.md).

## <a name="see-also"></a>Viz také

- [Jak se definuje jazyk specifický pro doménu](../modeling/how-to-define-a-domain-specific-language.md)
- [Porozumění modelům, třídám a vztahům](../modeling/understanding-models-classes-and-relationships.md)
- [Přizpůsobení a rozšíření jazyka specifického pro doménu](../modeling/customizing-and-extending-a-domain-specific-language.md)
- [Psaní kódu pro přizpůsobení jazyka specifického pro doménu](../modeling/writing-code-to-customise-a-domain-specific-language.md)
