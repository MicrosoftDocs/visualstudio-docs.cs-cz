---
title: Definování omezení ověření pro modely UML | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- UML model, validation constraints
ms.assetid: 87b3b0da-122d-4121-9318-200c38ff49d0
caps.latest.revision: 49
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 6647d37636ed0e79d817113e388ae5df23a88a29
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51782411"
---
# <a name="define-validation-constraints-for-uml-models"></a>Definování omezení ověřování pro modely UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete definovat omezení ověření, které testují, zda model splňuje podmínku, kterou zadáte. Můžete například definovat omezení a ujistit se, že uživatel nevytvoří smyčku vztahů dědičnosti. Omezení je vyvoláno, když se uživatel pokusí otevřít nebo uložit model a může být vyvoláno také ručně. Pokud omezení selže, chybová zpráva, která definujete se přidá do okna chyby. Můžete zabalit tato omezení do rozšíření integrace Visual Studio ([VSIX](http://go.microsoft.com/fwlink/?LinkId=160780)) a distribuovat ho ostatním uživatelům aplikace Visual Studio.  
  
 Můžete také definovat omezení, která ověřují model proti externím prostředkům, jako jsou databáze. Pokud chcete ověřit kód programu proti diagramu vrstev, přečtěte si téma [přidání ověřování vlastní architektury do diagramů vrstev](../modeling/add-custom-architecture-validation-to-layer-diagrams.md).  
  
 Pokud chcete zobrazit, které verze sady Visual Studio podporují modelech UML, naleznete v tématu [podporované verze pro nástroje architektury a modelování](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
## <a name="requirements"></a>Požadavky  
 Zobrazit [požadavky](../modeling/extend-uml-models-and-diagrams.md#Requirements).  
  
 Tuto funkci podporovat kterou verzí sady Visual Studio najdete v tématu [podporované verze pro nástroje architektury a modelování](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
## <a name="applying-validation-constraints"></a>Použití omezení ověření  
 Omezení ověření jsou použita ve třech případech: při uložení modelu; Při otevření modelu; a po kliknutí na **ověřit Model UML** na **architektura** nabídky. V každém případě pouze ta omezení, které byly definovány pro tento případ se použijí, i když obvykle definujete každé omezení, které chcete použít ve více než jeden případ.  
  
 Chyby ověření jsou hlášeny v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] chyby a poklepáním na chybu můžete vybrat prvky modelu, které jsou chybné.  
  
 Další informace o použití ověřování najdete v tématu [ověření modelu UML](../modeling/validate-your-uml-model.md).  
  
## <a name="defining-a-validation-extension"></a>Definování ověřování rozšíření  
 Chcete-li vytvořit rozšíření ověření pro UML designer, musíte vytvořit třídu, která definuje omezení ověření a vložit tuto třídu v Visual Studio integrace rozšíření (VSIX). VSIX funguje jako kontejner, který může omezení nainstalovat. Existují dva alternativní způsoby definování rozšíření ověření:  
  
-   **Vytvoření rozšíření ověření ve vlastním souboru VSIX pomocí šablony projektu.** Toto je rychlejší metoda. Pokud nechcete vaše omezení ověření kombinovat s jinými typy rozšíření například příkazy nabídek, vlastními položkami panelu nástrojů nebo obslužnými rutinami gest, použijte ji. V jedné třídě lze definovat několik omezení.  
  
-   **Vytvoření samostatné třídy ověření a projektů VSIX.** Tuto metodu použijte, pokud chcete sloučit několik typů rozšíření do stejného VSIX. Například pokud váš příkaz nabídky očekává, že model bude dodržovat zvláštní omezení, můžete ho vložit do stejného VSIX jako metodu ověřování.  
  
#### <a name="to-create-a-validation-extension-in-its-own-vsix"></a>Chcete-li vytvořit rozšíření ověření ve vlastním souboru VSIX  
  
1. V **nový projekt** dialogovém okně **projekty modelování**vyberte **rozšíření ověřování**.  
  
2. Otevřít **.cs** souboru v novém projektu a upravte třídu pro implementaci omezení ověření.  
  
    Další informace najdete v tématu [vyhodnocování omezení ověření](#Implementing).  
  
   > [!IMPORTANT]
   >  Ujistěte se, že vaše **.cs** soubory obsahují následující `using` – příkaz:  
   >   
   >  `using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;`  
  
3. Definováním nových metod můžete přidat další omezení. K identifikaci metody jako metodu ověřování, musí být označena s atributy stejným způsobem jako původní ověřovací metoda.  
  
4. Otestujte omezení stisknutím klávesy F5. Další informace najdete v tématu [provádění ověření omezení](#Executing).  
  
5. Nainstalujte příkaz nabídky v jiném počítači zkopírováním souboru **bin\\\*\\\*VSIX** , který je sestaven projektem. Další informace najdete v tématu [instalace a odinstalace rozšíření](#Installing).  
  
   Když přidáte další **.cs** soubory, bude obvykle vyžadovat následující `using` příkazy:  
  
```csharp  
using System.Collections.Generic;  
using System.ComponentModel.Composition;  
using System.Linq;  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;  
using Microsoft.VisualStudio.Modeling.Validation;  
using Microsoft.VisualStudio.Uml.Classes;  
  
```  
  
 Tady je alternativní postup:  
  
#### <a name="to-create-a-separate-validation-constraint-in-a-class-library-project"></a>K vytvoření zvláštního omezení ověření v projektu knihovny tříd  
  
1.  Vytvořte projekt knihovny tříd, jeho přidání do existujícího VSIX řešení nebo vytvoření nového řešení.  
  
    1.  Na **souboru** nabídce zvolte **nový**, **projektu**.  
  
    2.  V části **nainstalované šablony**, rozbalte **Visual C#** nebo **jazyka Visual Basic**a potom v prostředním sloupci zvolte možnost **knihovny tříd**.  
  
2.  Pokud ho vaše řešení již neobsahuje, vytvořte projekt VSIX:  
  
    1.  V **Průzkumníka řešení**, v místní nabídce řešení zvolte **přidat**, **nový projekt**.  
  
    2.  V části **nainstalované šablony**, rozbalte **Visual C#** nebo **jazyka Visual Basic**, klikněte na tlačítko **rozšiřitelnost**. V prostředním sloupci klikněte na tlačítko **projekt VSIX**.  
  
3.  Nastavte projekt VSIX jako projekt po spuštění řešení.  
  
    -   V Průzkumníku řešení v místní nabídce projektu VSIX zvolte **nastavit jako spouštěný projekt**.  
  
4.  V **source.extension.vsixmanifest**v části **obsahu**, přidejte projekt knihovny tříd jako komponentu MEF:  
  
    1.  Na **metadat** kartu, nastavte název souboru VSIX.  
  
    2.  Na **cíle instalace** kartu, nastavte verze sady Visual Studio jako cíle.  
  
    3.  Na **prostředky** kartě **nový**a v dialogovém okně nastavte:  
  
         **Typ** = **Komponenta MEF**  
  
         **Zdroj** = **projekt v aktuálním řešení**  
  
         **Projekt** = *váš projekt knihovny tříd*  
  
#### <a name="to-define-the-validation-class"></a>Do definice třídy validace  
  
1.  Tento postup není nutné, pokud jste vytvořili třídu ověřování s vlastním souborem VSIX z šablony projektu ověřování.  
  
2.  V ověření projektu třídy přidejte odkazy na následující [!INCLUDE[TLA2#tla_net](../includes/tla2sharptla-net-md.md)] sestavení:  
  
     `Microsoft.VisualStudio.Modeling.Sdk.[version]`  
  
     `Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml`  
  
     `Microsoft.VisualStudio.Uml.Interfaces`  
  
     `System.ComponentModel.Composition`  
  
3.  Přidejte soubor do projektu knihovny tříd obsahujícího kód, který se podobá následujícímu příkladu.  
  
    -   Každé omezení ověření je součástí metody, která je označena určitým atributem. Metoda přijímá parametr typu prvku modelu. Při vyvolání ověření, rozhraní ověřování použije každou metodu ověřování na každý prvek modelu, který odpovídá jeho typu parametru.  
  
    -   Tyto metody můžete umístit do libovolných tříd a obory názvů. Změňte je dle požadavků.  
  
    ```  
    using System.Collections.Generic;  
    using System.ComponentModel.Composition;  
    using System.Linq;  
    using Microsoft.VisualStudio.Modeling.Validation;  
    using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;  
    using Microsoft.VisualStudio.Uml.Classes;  
    // You might also need the other Microsoft.VisualStudio.Uml namespaces.  
  
    namespace Validation  
    {  
      public class MyValidationExtensions  
      {  
        // SAMPLE VALIDATION METHOD.  
        // All validation methods have the following attributes.  
        [Export(typeof(System.Action<ValidationContext, object>))]  
        [ValidationMethod(  
           ValidationCategories.Save  
         | ValidationCategories.Open  
         | ValidationCategories.Menu)]  
        public void ValidateClassNames  
          (ValidationContext context,   
           // This type determines what elements   
           // will be validated by this method:  
           IClass elementToValidate)  
        {  
          // A validation method should not change the model.  
  
          List<string> attributeNames = new List<string>();  
          foreach (IProperty attribute in elementToValidate.OwnedAttributes)  
          {  
            string name = attribute.Name;  
            if (!string.IsNullOrEmpty(name) && attributeNames.Contains(name))  
            {  
              context.LogError(  
                string.Format("Duplicate attribute name '{0}' in class {1}", name, elementToValidate.Name),  
                "001", elementToValidate);  
            }  
            attributeNames.Add(name);  
          }  
  
        }  
        // Add more validation methods for different element types.  
      }  
    }  
    ```  
  
##  <a name="Executing"></a> Provádění ověření omezení  
 Pro účely testování spusťte metodu ověřování v režimu ladění.  
  
#### <a name="to-test-the-validation-constraint"></a>Testování omezení ověření  
  
1.  Stisknutím klávesy **F5**, nebo **ladění** nabídce zvolte **spustit ladění**.  
  
     Experimentální instanci [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] spustí.  
  
     **Řešení potíží s**: Pokud se nová [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] nespustí:  
  
    -   Pokud máte více než jeden projekt, ujistěte se, že projekt VSIX je nastaven jako projekt po spuštění řešení.  
  
    -   V Průzkumníku řešení zvolte v místní nabídce startupu nebo projektu, **vlastnosti**. V editoru vlastností projektu, vyberte **ladění** kartu. Ujistěte se, že řetězec v **externí program Start** pole je úplný název cesty [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], obvykle:  
  
         `C:\Program Files\Microsoft Visual Studio [version]\Common7\IDE\devenv.exe`  
  
2.  V experimentální instanci [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]otevřete nebo vytvořte projekt modelování a otevřete nebo vytvořte diagram modelování.  
  
3.  Nastavení testu pro testovací omezení uvedené v předchozí části:  
  
    1.  Otevřete diagram třídy.  
  
    2.  Vytvořte třídu a přidejte dva atributy, které mají stejný název.  
  
4.  V místní nabídce kdekoli v diagramu zvolte **ověřit**.  
  
5.  Všechny chyby v modelu budou hlášeny v okně chyb.  
  
6.  Klikněte dvakrát na zprávy o chybách. Pokud jsou prvky uvedené v sestavě zobrazeny na obrazovce, budou zvýrazněny.  
  
     **Řešení potíží s**: Pokud **ověřit** příkaz nezobrazí v nabídce, ujistěte se, že:  
  
    -   Projekt ověření nabídky je uveden jako Komponenta MEF na **prostředky** kartu **source.extensions.manifest** v projektu VSIX.  
  
    -   Správné `Export` a `ValidationMethod` jsou přiřazeny k ověřovacím metodám.  
  
    -   `ValidationCategories.Menu` je součástí argumentu pro `ValidationMethod` atribut který je tvořena jinými hodnotami pomocí logického OR (&#124;).  
  
    -   Parametry všech vlastností `Import` a `Export` jsou platné.  
  
##  <a name="Implementing"></a> Vyhodnocování omezení  
 Metoda ověření by měl určit, zda je omezení ověření, které chcete použít hodnotu true nebo false. Při hodnotě true by se neměla provádět žádnou akci. Pokud false, měli byste nahlásit chybu pomocí metod poskytovaných parametrem `ValidationContext` parametru.  
  
> [!NOTE]
>  Metody ověřování by neměly měnit model. Neexistuje žádná záruka při nebo v jakém že se spustí omezení pořadí. Pokud musíte předat informace mezi po sobě jdoucích spuštěních metody ověřování v rámci ověřovacího běhu, můžete použít kontext mezipaměti popsaný v části [koordinace více ověření](#ContextCache).  
  
 Například pokud chcete zajistit, že každý typ (třída, rozhraní nebo výčet) má název, který je dlouhý alespoň tři znaky, můžete použít tuto metodu:  
  
```  
public void ValidateTypeName(ValidationContext context, IType type)  
{  
  if (!string.IsNullOrEmpty(type.Name) && type.Name.Length < 3)  
  {  
    context.LogError(  
      string.Format("Type name {0} is too short", type.Name),  
               "001", type);  
   }  
 }  
```  
  
 Zobrazit [programování s rozhraním API UML](../modeling/programming-with-the-uml-api.md) informace o metody a typy, které můžete použít k procházení a čtení modelu.  
  
### <a name="about-validation-constraint-methods"></a>Informace o metodách omezení ověřování  
 Každé omezení ověření je definováno metodou v následujícím formátu:  
  
```  
[Export(typeof(System.Action<ValidationContext, object>))]  
 [ValidationMethod(ValidationCategories.Save   
  | ValidationCategories.Menu   
  | ValidationCategories.Open)]  
public void ValidateSomething  
  (ValidationContext context, IClassifier elementToValidate)  
{...}  
```  
  
 Atributy a parametry každé metody ověření jsou následující:  
  
|||  
|-|-|  
|`[Export(typeof(System.Action <ValidationContext, object>))]`|Definuje metodu jako omezení ověřování pomocí Managed Extensibility Framework (MEF).|  
|`[ValidationMethod (ValidationCategories.Menu)]`|Určuje, kdy bude ověření provedeno. Použijte bitový operátor OR (&#124;) Pokud chcete zkombinovat více než jednu možnost.<br /><br /> `Menu` = vyvolána nabídkou ověřit.<br /><br /> `Save` = vyvolána při uložení modelu.<br /><br /> `Open` = vyvolána při otevření modelu. `Load` = vyvolána při uložení modelu, ale preventivně uživatele upozorní, že nemusí být možné model znovu otevřít. Také voláno při načítání před analýzou modelu.|  
|`public void ValidateSomething`<br /><br /> `(ValidationContext context,`<br /><br /> `IElement element)`|Nahraďte druhý parametr `IElement` typem elementu, ke kterému chcete, aby omezení platilo. Metoda omezení bude vyvolána na všechny prvky v zadaném typu.<br /><br /> Název metody není důležitý.|  
  
 Můžete definovat, kolik ověřovacích metod chcete s různými typy ve druhém parametru. Při vyvolání ověření každá metoda ověřování bude volána na každý prvek modelu, který odpovídá typu parametru.  
  
### <a name="reporting-validation-errors"></a>Oznamování chyb ověřování  
 Chcete-li vytvořit zprávu o chybách, použijte metody poskytované `ValidationContext`:  
  
 `context.LogError("error string", errorCode, elementsWithError);`  
  
- `"error string"` Zobrazí se v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] seznam chyb  
  
- `errorCode` řetězec, který by měl být jedinečným identifikátorem chyby  
  
- `elementsWithError` identifikuje prvky v modelu. Když uživatel poklepe na sestavu chyby, bude vybrán obrazec představující tento prvek.  
  
  `LogError(),` `LogWarning()` a `LogMessage()` umísťují zprávy v různých částech seznamu chyb.  
  
## <a name="how-validation-methods-are-applied"></a>Jak jsou použity metody ověřování  
 Ověření se aplikuje na každý prvek v modelu, včetně vztahů a částí větších prvků, jako jsou atributy třídy a parametry operace.  
  
 Každá metoda ověřování se aplikuje na každý prvek, který odpovídá typu v jejím druhém parametru. To znamená, že například pokud definujete metodu ověření s druhým parametrem `IUseCase` a jinou s jeho nadtypem `IElement`, pak obě tyto metody se použijí pro každý případ použití v modelu.  
  
 Hierarchie typů je shrnuto v [typy prvků modelu UML](../modeling/uml-model-element-types.md).  
  
 Můžete také přístup k prvků následujícími vztahy. Například, pokud chcete definovat ověřovací metodu na `IClass`, mohli byste projít jeho vlastněnými vlastnostmi:  
  
```  
public void ValidateTypeName(ValidationContext context, IClass c)  
{  
   foreach (IProperty property in c.OwnedAttributes)  
   {  
       if (property.Name.Length < 3)  
       {  
            context.LogError(  
                 string.Format(  
                        "Property name {0} is too short",   
                        property.Name),   
                 "001", property);  
        }  
   }  
}  
```  
  
### <a name="creating-a-validation-method-on-the-model"></a>Vytváření ověřovací metody na modelu  
 Pokud chcete mít jistotu, že metoda ověření je volána přesně jednou při každém spuštění ověřování, můžete ověřit `IModel`:  
  
```  
using Microsoft.VisualStudio.Uml.AuxiliaryConstructs; ...  
[Export(typeof(System.Action<ValidationContext, object>))]  
[ValidationMethod(ValidationCategories.Menu)]  
public void ValidateModel(ValidationContext context, IModel model)  
{  foreach (IElement element in model.OwnedElements)  
   { ...  
```  
  
### <a name="validating-shapes-and-diagrams"></a>Ověřování tvarů a diagramů  
 Metody ověřování nejsou vyvolány na prvky zobrazení jako diagramy a tvary, protože primárním účelem metod ověření je ověřovat model. Ale můžete přístup k aktuálnímu diagramu pomocí kontextu diagramu.  
  
 Ve vaší třídě ověření deklarujte `DiagramContext` jako importovanou vlastnost:  
  
```  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;   
...  
[Import]  
public IDiagramContext DiagramContext { get; set; }  
```  
  
 V metodě ověření, můžete použít `DiagramContext` pro přístup k aktuálnímu diagramu fokusu, pokud existuje:  
  
```  
[Export(typeof(System.Action<ValidationContext, object>))]  
[ValidationMethod(ValidationCategories.Menu)]  
public void ValidateModel(ValidationContext context, IModel model)  
{  
  IDiagram focusDiagram = DiagramContext.CurrentDiagram;  
  if (focusDiagram != null)  
  {  
    foreach (IShape<IUseCase> useCaseShape in  
              focusDiagram.GetChildShapes<IUseCase>())  
    { ...  
```  
  
 Chcete-li zaprotokolovat chybu, musíte získat prvek modelu, který tvar představuje, protože nemůžete předat tvar do `LogError`:  
  
```  
IUseCase useCase = useCaseShape.Element;  
context.LogError(... , usecase);  
```  
  
###  <a name="ContextCache"></a> Koordinace více ověřování  
 Při vyvolání ověření, například uživatelem v nabídce diagramu, každá metoda ověřování platí pro každý prvek modelu. To znamená, že v jednom vyvolání rozhraní ověření stejnou metodu může použít mnohokrát na různé prvky.  
  
 To představuje problém pro ověření, které se zabývají vztahy mezi elementy. Například můžete například napsat ověření, které začíná od, Řekněme, případu použití a překračuje **zahrnují** vztahy k ověření, že neexistují žádné smyčky. Ale když metoda platí pro každý případ použití v modelu, který má mnoho **zahrnují** odkazy, je pravděpodobné, že opakovaně zpracuje stejné oblasti modelu.  
  
 Abyste předešli této situaci, existuje mezipaměť kontextu, ve které se uchovají informace během procesu ověřování. Můžete ho použít k předávání informací mezi různými běhy metod ověřování. Může například uložit seznam prvků, které již byly zpracovány v tomto spuštění ověřování. Mezipaměť je vytvořena na začátku každého běhu ověřování a nelze použít k předávání informací mezi různými běhy ověřování.  
  
|||  
|-|-|  
|`context.SetCacheValue<T> (name, value)`|Store hodnotu|  
|`context.TryGetCacheValue<T> (name, out value)`|Získáte hodnotu. Vrátí hodnotu true v případě úspěšného ověření.|  
|`context.GetValue<T>(name)`|Získáte hodnotu.|  
|`Context.GetValue<T>()`|Získáte hodnotu zadaného typu.|  
  
##  <a name="Installing"></a> Instalace a odinstalace rozšíření  
 Můžete nainstalovat [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] rozšíření ve vašem počítači i v jiných počítačích.  
  
#### <a name="to-install-an-extension"></a>Instalace rozšíření  
  
1.  V počítači, vyhledejte **VSIX** soubor, který byl vytvořen vaším projektem VSIX.  
  
    1.  V **Průzkumníka řešení**, v místní nabídce projektu VSIX zvolte **otevřít složku v Průzkumníku Windows**.  
  
    2.  Vyhledejte soubor **bin\\\*\\**_YourProject_**VSIX.**  
  
2.  Kopírovat **VSIX** souboru k cílovému počítači, na kterém chcete nainstalovat rozšíření. To může být vlastní počítač nebo jiný.  
  
    -   Cílový počítač musí mít některou z edicí systému [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] , který jste zadali v **source.extension.vsixmanifest**.  
  
3.  V cílovém počítači, otevřete **VSIX** souboru.  
  
     **Instalační program rozšíření sady Visual Studio** otevře a nainstaluje rozšíření.  
  
4.  Spusťte nebo restartujte [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)].  
  
#### <a name="to-uninstall-an-extension"></a>Odinstalace rozšíření  
  
1. Na **nástroje** nabídce zvolte **rozšíření a aktualizace**.  
  
2. Rozbalte **nainstalovaná rozšíření**.  
  
3. Vyberte požadované rozšíření a klikněte na tlačítko **odinstalovat**.  
  
   Jen zřídka se chybné rozšíření se nepodaří načíst a vytvoří sestavu v okně chyb, ale nezobrazí ve Správci rozšíření. V takovém případě můžete odebrat rozšíření odstraněním souboru z následujícího umístění kde *% LocalAppData %* je obvykle *DriveName*: \Users\\*uživatelskéjméno*\AppData\Local:  
  
   *% LocalAppData %* **\Microsoft\VisualStudio\\\Extensions [verze]**  
  
##  <a name="Example"></a> Příklad  
 Tento příklad vyhledá smyčky ve vztahu závislosti mezi prvky.  
  
 Ověří i na Uložit a v příkazu nabídky ověřit.  
  
```  
/// <summary>  
/// Verify that there are no loops in the dependency relationsips.  
/// In our project, no element should be a dependent of itself.  
/// </summary>  
/// <param name="context">Validation context for logs.</param>  
/// <param name="element">Element to start validation from.</param>  
[Export(typeof(System.Action<ValidationContext, object>))]  
[ValidationMethod(ValidationCategories.Menu   
     | ValidationCategories.Save | ValidationCategories.Open)]  
public void NoDependencyLoops(ValidationContext context, INamedElement element)  
{  
    // The validation framework will call this method  
    // for every element in the model. But when we follow  
    // the dependencies from one element, we will validate others.  
    // So we keep a list of the elements that we don't need to validate again.   
    // The list is kept in the context cache so that it is passed  
    // from one execution of this method to another.  
    List<INamedElement> alreadySeen = null;  
    if (!context.TryGetCacheValue("No dependency loops", out alreadySeen))  
    {  
       alreadySeen = new List<INamedElement>();  
       context.SetCacheValue("No dependency loops", alreadySeen);  
    }  
  
    NoDependencyLoops(context, element,   
                new INamedElement[0], alreadySeen);      
}  
  
/// <summary>  
/// Log an error if there is any loop in the dependency relationship.  
/// </summary>  
/// <param name="context">Validation context for logs.</param>  
/// <param name="element">The element to be validated.</param>  
/// <param name="dependants">Elements we've followed in this recursion.</param>  
/// <param name="alreadySeen">Elements that have already been validated.</param>  
/// <returns>true if no error was detected</returns>  
private bool NoDependencyLoops(ValidationContext context,   
    INamedElement element, INamedElement[] dependants,   
    List<INamedElement> alreadySeen)  
{  
    if (dependants.Contains(element))  
    {  
        context.LogError(string.Format("{0} should not depend on itself", element.Name),   
        "Fabrikam.UML.NoGenLoops", // unique code for this error  
        dependants.SkipWhile(e => e != element).ToArray());   
            // highlight elements that are in the loop  
        return false;  
    }  
    INamedElement[] dependantsPlusElement =   
        new INamedElement[dependants.Length + 1];  
    dependants.CopyTo(dependantsPlusElement, 0);  
    dependantsPlusElement[dependantsPlusElement.Length - 1] = element;  
  
    if (alreadySeen.Contains(element))  
    {  
        // We have already validated this when we started   
        // from another element during this validation run.  
        return true;  
    }  
    alreadySeen.Add(element);  
  
    foreach (INamedElement supplier in element.GetDependencySuppliers())  
    {  
        if (!NoDependencyLoops(context, supplier,  
             dependantsPlusElement, alreadySeen))  
        return false;  
    }  
    return true;  
}  
```  
  
## <a name="see-also"></a>Viz také  
 [Definování a instalace rozšíření modelování](../modeling/define-and-install-a-modeling-extension.md)   
 [Programování pomocí rozhraní API UML](../modeling/programming-with-the-uml-api.md)



