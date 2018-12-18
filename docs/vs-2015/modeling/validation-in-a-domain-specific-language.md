---
title: Ověřování v jazyka specifického pro doménu | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language, constraints
- Domain-Specific Language, validation
ms.assetid: 65b93df8-af3c-462b-904c-60292f8ed381
caps.latest.revision: 35
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 30a29c9b8921d72f717aea21ed202766f0874389
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49950786"
---
# <a name="validation-in-a-domain-specific-language"></a>Ověřování v jazyce specifickém pro doménu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Jako autoři jazyka specifického pro doménu (DSL) můžete definovat omezení ověření můžete ověřit, že model vytvořený uživatelem smysluplné. Například pokud vaše DSL umožňuje uživatelům nakreslit řady strom osoby a jejich předchůdci, můžete napsat omezení, které zajišťuje, že mají podřízené položky data narození po jejich nadřazených objektů.  
  
 Může mít omezení ověření, spustí při uložení modelu, když se otevře, a když uživatel spustí explicitně **ověřit** příkazu nabídky. Můžete také provést ověření v řízení programu. Například můžete třeba spustit ověření v reakci na změnu hodnoty vlastnosti nebo relace.  
  
 Ověření je zvlášť důležité při psaní textové šablony nebo jiné nástroje, které zpracovávají modely vašich uživatelů. Ověření zajišťuje, že modely splňují předpoklady předpokládá, že pomocí těchto nástrojů.  
  
> [!WARNING]
>  Můžete také povolit omezení ověření je definovat v samostatném rozšíření vašeho DSL, společně s příkazy rozšíření nabídky a obslužné rutiny gesta. Uživatelé mohou nainstalovat tato rozšíření kromě vašeho DSL. Další informace najdete v tématu [rozšíření vašeho DSL pomocí MEF](../modeling/extend-your-dsl-by-using-mef.md).  
  
## <a name="running-validation"></a>Spouštění ověření  
 Když uživatel upravuje model, to znamená, že instance jazyka specifického pro doménu tyto akce můžete spustit ověření:  
  
- V diagramu pravým tlačítkem a vyberte **ověřit všechny**.  
  
- Klikněte pravým tlačítkem na nejvyšší uzel v Průzkumník DSL a vyberte **ověřit všechny**  
  
- Uložte model.  
  
- Otevřete model.  
  
- Kromě toho můžete napsat kód programu, který spustí ověřování, například jako součást příkazu nabídky nebo v reakci na změnu.  
  
  Všechny chyby ověření se zobrazí v **seznam chyb** okna. Uživatel můžete dvakrát kliknout na chybovou zprávu vybrat prvky modelu, které jsou příčinou chyby.  
  
## <a name="defining-validation-constraints"></a>Definování omezení ověření  
 Můžete definovat omezení ověření tak, že přidáte metody ověřování pro doménovými třídami nebo vztahy tohoto kódu DSL. Po spuštění ověření uživatelem nebo v rámci řízení programu, jsou provedeny některé nebo všechny metody ověřování. Každá metoda platí pro každou instanci své třídy a v každé třídě může být několik metod ověření.  
  
 Každá metoda ověřování hlásí chyby, které nalezne.  
  
> [!NOTE]
>  Metody ověřování zprávy o chybách, ale neměňte modelu. Pokud chcete upravit nebo zakázat některé změny, přečtěte si [alternativy k ověření](#alternatives).  
  
#### <a name="to-define-a-validation-constraint"></a>Chcete-li definovat omezení ověření  
  
1. Povolení ověřování v **Editor\Validation** uzlu:  
  
   1.  Otevřít **Dsl\DslDefinition.dsl**.  
  
   2.  V okně Průzkumník DSL, rozbalte **Editor** uzel a vyberte možnost **ověření**.  
  
   3.  V okně Vlastnosti nastavte **používá** vlastností `true`. Je nejvhodnější pro nastavení těchto vlastností.  
  
   4.  Klikněte na tlačítko **Transformovat všechny šablony** v panelu nástrojů Průzkumníka řešení.  
  
2. Zápis definicí částečné třídy pro jeden nebo více doménovými třídami nebo vztahy domén. Zapsat tyto definice do nového souboru v kódu **Dsl** projektu.  
  
3. Předpona každou třídu se tento atribut:  
  
   ```csharp  
   [ValidationState(ValidationState.Enabled)]  
   ```  
  
   -   Ve výchozím nastavení tento atribut taky povolí ověřování pro odvozené třídy. Pokud chcete zakázat ověřování pro konkrétní odvozenou třídu, můžete použít `ValidationState.Disabled`.  
  
4. Přidání metody ověřování na třídy. Každá metoda ověřování můžete mít libovolný název, ale mít jeden parametr typu <xref:Microsoft.VisualStudio.Modeling.Validation.ValidationContext>.  
  
    Musí mít předponu s jedním nebo více `ValidationMethod` atributy:  
  
   ```csharp  
   [ValidationMethod (ValidationCategories.Open | ValidationCategories.Save | ValidationCategories.Menu ) ]  
   ```  
  
    ValidationCategories zadat při provádění metody.  
  
   Příklad:  
  
```csharp  
using Microsoft.VisualStudio.Modeling;  
using Microsoft.VisualStudio.Modeling.Validation;  
  
// Allow validation methods in this class:  
[ValidationState(ValidationState.Enabled)]  
// In this DSL, ParentsHaveChildren is a domain relationship  
// from Person to Person:  
public partial class ParentsHaveChildren  
{  
  // Identify the method as a validation method:  
  [ValidationMethod  
  ( // Specify which events cause the method to be invoked:  
    ValidationCategories.Open // On file load.  
  | ValidationCategories.Save // On save to file.  
  | ValidationCategories.Menu // On user menu command.  
  )]  
  // This method is applied to each instance of the   
  // type (and its subtypes) in a model:   
  private void ValidateParentBirth(ValidationContext context)     
  {  
    // In this DSL, the role names of this relationship  
    // are "Child" and "Parent":   
     if (this.Child.BirthYear < this.Parent.BirthYear   
        // Allow user to leave the year unset:  
        && this.Child.BirthYear != 0)  
      {  
        context.LogError(  
             // Description:  
                       "Child must be born after Parent",  
             // Unique code for this error:  
                       "FAB001ParentBirthError",   
              // Objects to select when user double-clicks error:  
                       this.Child,   
                       this.Parent);  
    }  
  }  
```  
  
 Všimněte si, že o tomto kódu následující body:  
  
- Metody ověřování můžete přidat doménovými třídami nebo vztahy domén. Kód pro tyto typy je v **Dsl\Generated Code\Domain\*.cs**.  
  
- Každá metoda ověřování platí pro každou instanci své třídy a jejích podtřídách. V případě doménového vztahu každá instance je propojení mezi dvěma prvky modelu.  
  
- Metody ověřování nejsou použity v libovolném zadané pořadí a každá metoda neplatí pro instance své třídy v libovolném pořadí předvídatelné.  
  
- Je obvykle chybná pro metodu ověřování pro aktualizaci obsahu úložiště, protože by to vést k nekonzistentním výsledkům. Místo toho nahlásit všechny chyby pomocí volání metody `context.LogError`, `LogWarning` nebo `LogInfo`.  
  
- Při volání LogError můžete zadat seznam prvků modelu nebo vztah odkazy, které bude vybrána, když uživatel poklepe chybová zpráva.  
  
- Informace o tom, jak čtení modelu v programovém kódu najdete v tématu [navigace a aktualizace modelu v programovém kódu](../modeling/navigating-and-updating-a-model-in-program-code.md).  
  
  V příkladu platí pro následující doménový model. U tohoto vztahu ParentsHaveChildren je role, které jsou pojmenovány podřízenými a nadřazenými.  
  
  ![Diagramem definice DSL &#45; řady stromu modelu](../modeling/media/familyt-person.png "FamilyT_Person")  
  
## <a name="validation-categories"></a>Ověření kategorie  
 V <xref:Microsoft.VisualStudio.Modeling.Validation.ValidationMethodAttribute> atribut určíte, když metoda ověření by měl být spuštěn.  
  
|Kategorie|Spuštění|  
|--------------|---------------|  
|<xref:Microsoft.VisualStudio.Modeling.Validation.ValidationCategories>|Pokud uživatel vyvolá příkaz nabídky ověření.|  
|<xref:Microsoft.VisualStudio.Modeling.Validation.ValidationCategories>|Při otevření souboru modelu.|  
|<xref:Microsoft.VisualStudio.Modeling.Validation.ValidationCategories>|Když je soubor uložen. Pokud jsou chyby ověření, uživateli se přihlašovací možnost uložení zrušení operace.|  
|<xref:Microsoft.VisualStudio.Modeling.Validation.ValidationCategories>|Když je soubor uložen. Pokud nejsou chyby z metody v této kategorii, uživatel bude upozorněn, že nemusí být možné znovuotevření daného souboru.<br /><br /> Tato kategorie se používá pro metody ověřování, které testují duplicitních názvů nebo ID nebo jinými podmínkami, které by mohly způsobit chyby načtení.|  
|<xref:Microsoft.VisualStudio.Modeling.Validation.ValidationCategories>|Když je volána metoda ValidateCustom. Ověření v této kategorii lze volat pouze z programového kódu.<br /><br /> Další informace najdete v tématu [vlastní ověření kategorie](#custom).|  
  
## <a name="where-to-place-validation-methods"></a>Kam umístit metody ověřování  
 Umístěním ověřovací metodu na jiný typ lze často dosáhnout stejného efektu. Může například přidejte metodu do třídy osoba místo ParentsHaveChildren vztah a jeho iteraci v rámci odkazy:  
  
```  
[ValidationState(ValidationState.Enabled)]  
public partial class Person  
{[ValidationMethod  
 ( ValidationCategories.Open   
 | ValidationCategories.Save  
 | ValidationCategories.Menu  
 )  
]  
  private void ValidateParentBirth(ValidationContext context)     
  {  
    // Iterate through ParentHasChildren links:  
    foreach (Person parent in this.Parents)  
    {  
        if (this.BirthYear <= parent.BirthYear)  
        { ...  
  
```  
  
 **Agregování omezení ověření.** Použití ověřovacích předvídatelné popořadě, definujte jeden ověřovací metodu na třídu vlastníka takových kořenový prvek modelu. Tato technika také umožňuje agregovat více zpráv o chybách do jedné zprávy.  
  
 Nevýhody jsou, kombinované metoda je méně usnadňuje správu a že omezení musí všechny mají stejnou `ValidationCategories`. Proto doporučujeme, pokud je to možné ponechat každé omezení v samostatné metodě.  
  
 **Předávání hodnot v místní mezipaměti.** Kontextový parametr je slovník, do kterého můžete umístit libovolné hodnoty. Adresář se uchovávají po dobu trvání spuštění ověření. Konkrétní ověřovací metoda může například zachovat počet chyb v rámci a použití mají předejít zahlcení okna chyby s opakované zprávy. Příklad:  
  
```csharp  
List<ParentsHaveChildren> erroneousLinks;  
if (!context.TryGetCacheValue("erroneousLinks", out erroneousLinks))  
erroneousLinks = new List<ParentsHaveChildren>();  
erroneousLinks.Add(this);  
context.SetCacheValue("erroneousLinks", erroneousLinks);  
if (erroneousLinks.Count < 5) { context.LogError( ... ); }  
  
```  
  
## <a name="validation-of-multiplicities"></a>Ověření násobnosti  
 Metody ověřování pro kontrolu minimální násobností jsou automaticky generovány pro vašeho DSL. Kód je zapsán do **Dsl\Generated Code\MultiplicityValidation.cs**. Tyto metody se projeví, když povolíte ověření v **Editor\Validation** uzel v Průzkumník DSL.  
  
 Pokud nastavíte násobnost role doménového vztahu musí být 1.. * nebo 1..1, ale uživatel nevytváří odkaz tento vztah se zobrazí chybovou zprávu ověření.  
  
 Například pokud má vaše DSL třídy osoby a města a relace PersonLivesInTown se vztahem **1..\\** * na roli města, pak pro každou osobu, která nemá žádné města, chybová zpráva se zobrazí.  
  
## <a name="running-validation-from-program-code"></a>Spuštění ověření v kódu programu  
 Přístup k nebo vytvořením ValidationController můžete spustit ověření. Pokud chcete chyby, který se má zobrazit uživatelům v okně chyb, použijte ValidationController, který je připojen k DocData do diagramu. Například, pokud při psaní příkazu nabídky `CurrentDocData.ValidationController` je k dispozici ve třídě set příkazu:  
  
```csharp  
using Microsoft.VisualStudio.Modeling;  
using Microsoft.VisualStudio.Modeling.Validation;  
using Microsoft.VisualStudio.Modeling.Shell;  
...  
partial class MyLanguageCommandSet   
{  
  private void OnMenuMyContextMenuCommand(object sender, EventArgs e)   
  {   
   ValidationController controller = this.CurrentDocData.ValidationController;   
...  
  
```  
  
 Další informace najdete v tématu [postupy: přidání příkazu do místní nabídky](../modeling/how-to-add-a-command-to-the-shortcut-menu.md).  
  
 Můžete také vytvořit samostatné ověření řadič a chyby spravovat sami. Příklad:  
  
```csharp  
using Microsoft.VisualStudio.Modeling;  
using Microsoft.VisualStudio.Modeling.Validation;  
using Microsoft.VisualStudio.Modeling.Shell;  
...  
Store store = ...;  
VsValidationController validator = new VsValidationController(s);  
// Validate all elements in the Store:  
if (!validator.Validate(store, ValidationCategories.Save))  
{  
  // Deal with errors:  
  foreach (ValidationMessage message in validator.ValidationMessages) { ... }  
}  
  
```  
  
## <a name="running-validation-when-a-change-occurs"></a>Spuštění ověření v případě, že dojde ke změně  
 Pokud chcete, aby se zajistilo, že uživatel je-li modelu stává neplatným okamžitě upozornění, můžete definovat událost úložiště, která spustí ověřování. Další informace o události v úložišti, najdete v části [obslužné rutiny rozšíření změny mimo the Model událostí](../modeling/event-handlers-propagate-changes-outside-the-model.md).  
  
 Kromě kód pro ověření, přidejte soubor vlastní kód na vaši **DslPackage** projektu s obsahem, podobně jako v následujícím příkladu. Tento kód používá `ValidationController` , který je připojený k tomuto dokumentu. Tento řadič se zobrazí chyby ověření v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] seznamu chyb.  
  
```csharp  
using System;  
using System.Linq;  
using Microsoft.VisualStudio.Modeling;  
using Microsoft.VisualStudio.Modeling.Validation;  
namespace Company.FamilyTree  
{  
  partial class FamilyTreeDocData // Change name to your DocData.  
  {  
    // Register the store event handler:   
    protected override void OnDocumentLoaded()  
    {  
      base.OnDocumentLoaded();  
      DomainClassInfo observedLinkInfo = this.Store.DomainDataDirectory  
         .FindDomainClass(typeof(ParentsHaveChildren));  
      DomainClassInfo observedClassInfo = this.Store.DomainDataDirectory  
         .FindDomainClass(typeof(Person));  
      EventManagerDirectory events = this.Store.EventManagerDirectory;  
      events.ElementAdded  
         .Add(observedLinkInfo, new EventHandler<ElementAddedEventArgs>(ParentLinkAddedHandler));  
      events.ElementDeleted.Add(observedLinkInfo, new EventHandler<ElementDeletedEventArgs>(ParentLinkDeletedHandler));  
      events.ElementPropertyChanged.Add(observedClassInfo, new EventHandler<ElementPropertyChangedEventArgs>(BirthDateChangedHandler));  
    }  
    // Handler will be called after transaction that creates a link:  
    private void ParentLinkAddedHandler(object sender,  
                                ElementAddedEventArgs e)  
    {  
      this.ValidationController.Validate(e.ModelElement,  
           ValidationCategories.Save);  
    }  
    // Called when a link is deleted:  
    private void ParentLinkDeletedHandler(object sender,   
                                ElementDeletedEventArgs e)  
    {  
      // Don't apply validation to a deleted item!   
      // - Validate store to refresh the error list.  
      this.ValidationController.Validate(this.Store,  
           ValidationCategories.Save);  
    }  
    // Called when any property of a Person element changes:  
    private void BirthDateChangedHandler(object sender,  
                      ElementPropertyChangedEventArgs e)  
    {  
      Person person = e.ModelElement as Person;  
      // Not interested in changes in other properties:  
      if (e.DomainProperty.Id != Person.BirthYearDomainPropertyId)  
          return;  
  
      // Validate all parent links to and from the person:  
      this.ValidationController.Validate(  
        ParentsHaveChildren.GetLinksToParents(person)  
        .Concat(ParentsHaveChildren.GetLinksToChildren(person))  
        , ValidationCategories.Save);  
    }  
  }  
}  
  
```  
  
 Obslužné rutiny se také označují jako po vrácení zpět nebo opakování operace, které ovlivňují odkazy nebo elementy.  
  
##  <a name="custom"></a> Vlastní ověřovací kategorie  
 Kromě standardní ověřovací kategorie, jako je například nabídka a otevřít můžete definovat vlastní kategorie. Můžete vyvolat tyto kategorie z programového kódu. Uživatel nemůže je vyvolat přímo.  
  
 Typické použití pro vlastní kategorie je definovat kategorie, která ověřuje, zda model splňuje předpoklady konkrétní nástroj.  
  
 Přidání metody ověření pro určité kategorie, předpona s atributem takto:  
  
```csharp  
[ValidationMethod(CustomCategory = "PreconditionsForGeneratePartsList")]  
[ValidationMethod(ValidationCategory.Menu)]   
private void TestForCircularLinks(ValidationContext context)   
{...}  
  
```  
  
> [!NOTE]
>  Můžete před metodu s tolika `[ValidationMethod()]` atributy, jak chcete. Přidejte metodu pro standardní i vlastní kategorie.  
  
 Chcete-li vyvolat vlastní ověřování:  
  
```csharp  
  
// Invoke all validation methods in a custom category:   
validationController.ValidateCustom  
  (store, // or a list of model elements  
   "PreconditionsForGeneratePartsList");  
```  
  
##  <a name="alternatives"></a> Alternativy k ověření  
 Omezení ověření zprávy o chybách, ale neměňte modelu. Pokud místo toho chcete zabránit modelu stává neplatný, můžete použít jiné techniky.  
  
 Tyto postupy se však nedoporučuje. Je obvykle vhodnější nechat uživatele rozhodnout, jak chybu opravit modelu je neplatný.  
  
 **Upravte Změna modelu obnovení platnosti.** Například pokud uživatel nastaví vlastnost vyšší než povolené maximum, může resetovat vlastnost na maximální hodnotu. K tomuto účelu definice pravidla. Další informace najdete v tématu [pravidla šíření změn v rámci the Model](../modeling/rules-propagate-changes-within-the-model.md).  
  
 **Při pokusu o neplatný změnu vrátit zpět transakci.** Můžete také definovat pravidla pro tento účel, ale v některých případech je možné přepsat obslužné rutiny vlastnosti **OnValueChanging()**, nebo o přepsání metody, jako `OnDeleted().` vrácení zpět transakcí, použití `this.Store.TransactionManager.CurrentTransaction.Rollback().` Další informace informace najdete v tématu [obslužné rutiny změny hodnoty vlastnosti domény](../modeling/domain-property-value-change-handlers.md).  
  
> [!WARNING]
>  Ujistěte se, že uživatel zná, že změna byla upravena nebo vrácena zpět. Například použít `System.Windows.Forms.MessageBox.Show("message").`  
  
## <a name="see-also"></a>Viz také  
 [Procházení a aktualizace modelu v programovém kódu](../modeling/navigating-and-updating-a-model-in-program-code.md)   
 [Obslužné rutiny události šířící změny mimo model](../modeling/event-handlers-propagate-changes-outside-the-model.md)



