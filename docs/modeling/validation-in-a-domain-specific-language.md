---
title: Ověřování v jazyce specifickém pro doménu
description: Zjistěte, jak můžete definovat ověřovací omezení, abyste ověřili, že model vytvořený uživatelem má smysl.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, constraints
- Domain-Specific Language, validation
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6de3a8940c845b29d2d0c7454b7c585f4676dba0
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388331"
---
# <a name="validation-in-a-domain-specific-language"></a>Ověřování v jazyce specifickém pro doménu
Jako autor jazyka specifického pro doménu (DSL) můžete definovat ověřovací omezení, abyste ověřili, že model vytvořený uživatelem má smysl. Pokud například váš DSL umožňuje uživatelům vykreslit rodokmen lidí a jejich předchůdců, můžete napsat omezení, které zajistí, že děti budou mít datum narození po svých rodičůch.

 Ověřovací omezení můžete mít spuštěná při uložení modelu, jeho otevření a při explicitním spuštění **příkazu nabídky** Ověřit. Ověřování můžete provést také pod řízením programu. Můžete například provést ověření v reakci na změnu hodnoty vlastnosti nebo relace.

 Ověřování je zvlášť důležité, pokud píšete textové šablony nebo jiné nástroje, které zpracovávají modely vašich uživatelů. Ověření zajišťuje, aby modely splnily podmínky, které tyto nástroje předpokládaly.

> [!WARNING]
> Můžete také povolit, aby ověřovací omezení byla definována v samostatných rozšířeních vašeho DSL spolu s příkazy nabídky rozšíření a obslužných rutin gest. Uživatelé se mohou rozhodnout, že tato rozšíření nainstalují kromě vašeho DSL. Další informace najdete v tématu [Rozšíření DSL pomocí MEF.](../modeling/extend-your-dsl-by-using-mef.md)

## <a name="running-validation"></a>Spuštění ověření
 Když uživatel upravuje model, to znamená instanci jazyka specifického pro doménu, můžete ověření spustit následujícími akcemi:

- Klikněte pravým tlačítkem na diagram a vyberte **Ověřit vše.**

- V průzkumníku DSL klikněte pravým tlačítkem na horní uzel a vyberte **Ověřit vše.**

- Uložte model.

- Otevřete model.

- Kromě toho můžete napsat programový kód, který spouští ověřování, například jako součást příkazu nabídky nebo v reakci na změnu.

  Všechny chyby ověřování se zobrazí v **Seznam chyb** okně. Uživatel může dvakrát kliknout na chybovou zprávu a vybrat prvky modelu, které jsou příčinou chyby.

## <a name="defining-validation-constraints"></a>Definování omezení ověřování
 Omezení ověřování definujete přidáním metod ověřování do tříd domény nebo vztahů vašeho DSL. Při spuštění ověření, ať už uživatelem nebo pod kontrolou programu, se spustí některé nebo všechny metody ověřování. Každá metoda je použita na každou instanci své třídy a v každé třídě může být několik metod ověřování.

 Každá metoda ověřování hlásí všechny nalezené chyby.

> [!NOTE]
> Metody ověřování hlásí chyby, ale nemění model. Pokud chcete upravit nebo zabránit určitým změnám, podívejte se [na stránku Alternativy k ověřování](#alternatives).

#### <a name="to-define-a-validation-constraint"></a>Definování omezení ověřování

1. Povolte ověřování v **uzlu Editor\Validation:**

   1. Otevřete **Dsl\DslDefinition.dsl**.

   2. V Průzkumníku DSL rozbalte **uzel Editor** a vyberte **Ověření.**

   3. V okno Vlastnosti nastavte vlastnosti **Uses**  na `true` . Nejpohodlnější je nastavit všechny tyto vlastnosti.

   4. Na **panelu nástrojů klikněte na** Transformovat **Průzkumník řešení** šablony.

2. Zápis částečných definic tříd pro jednu nebo více tříd domény nebo vztahů domény. Tyto definice zapište do nového souboru kódu v **projektu Dsl.**

3. Ke každé třídě zadejte předponu tohoto atributu:

   ```csharp
   [ValidationState(ValidationState.Enabled)]
   ```

   - Ve výchozím nastavení tento atribut také povolí ověřování pro odvozené třídy. Pokud chcete zakázat ověřování pro konkrétní odvozenou třídu, můžete použít `ValidationState.Disabled` .

4. Přidejte metody ověřování do tříd. Každá metoda ověřování může mít libovolný název, ale má jeden parametr typu <xref:Microsoft.VisualStudio.Modeling.Validation.ValidationContext> .

    Musí mít předponu s jedním nebo více `ValidationMethod` atributy:

   ```csharp
   [ValidationMethod (ValidationCategories.Open | ValidationCategories.Save | ValidationCategories.Menu ) ]
   ```

    Kategorie ValidationCategories určují, kdy je metoda spuštěna.

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

 Všimněte si následujících bodů o tomto kódu:

- Metody ověřování můžete přidat do tříd domén nebo vztahů mezi doménami. Kód pro tyto typy je v **Dsl\Generated Code\Domain \* .cs**.

- Každá metoda ověřování se použije na každou instanci své třídy a jejích podtříd. V případě relace domény je každá instance propojením mezi dvěma prvky modelu.

- Metody ověřování nejsou použity v žádném zadaném pořadí a každá metoda není použita na instance své třídy v předvídatelných pořadích.

- Pro metodu ověřování je obvykle chybný postup aktualizace obsahu úložiště, protože by to vedlo k nekonzistentním výsledkům. Místo toho by měla metoda nahlásit jakoukoli chybu voláním `context.LogError` nebo `LogWarning` `LogInfo` .

- Ve volání LogError můžete zadat seznam prvků modelu nebo odkazů na relace, které budou vybrány, když uživatel dvakrát klikne na chybovou zprávu.

- Informace o tom, jak číst model v programovém kódu, najdete v tématu Navigace a aktualizace [modelu v programovém kódu](../modeling/navigating-and-updating-a-model-in-program-code.md).

  Příklad se týká následujícího doménového modelu. Vztah Parents Nespravované Prvky má role, které mají název Child a Parent.

  ![Diagram definice DSL &#45; modelu stromové struktury rodiny](../modeling/media/familyt_person.png)

## <a name="validation-categories"></a>Kategorie ověření
 V <xref:Microsoft.VisualStudio.Modeling.Validation.ValidationMethodAttribute> atributu určíte, kdy se má metoda ověřování spustit.

|Kategorie|Spuštění|
|-|-|
|<xref:Microsoft.VisualStudio.Modeling.Validation.ValidationCategories>|Když uživatel vyvolá příkaz nabídky Ověřit.|
|<xref:Microsoft.VisualStudio.Modeling.Validation.ValidationCategories>|Při otevření souboru modelu.|
|<xref:Microsoft.VisualStudio.Modeling.Validation.ValidationCategories>|Při uložení souboru. Pokud dojde k chybám ověřování, uživateli se zobrazí možnost zrušení operace uložení.|
|<xref:Microsoft.VisualStudio.Modeling.Validation.ValidationCategories>|Při uložení souboru. Pokud v této kategorii dojde k chybám z metod, uživatel bude upozorněn, že soubor nemusí být možné znovu otevřít.<br /><br /> Tuto kategorii použijte pro metody ověřování, které testuje duplicitní názvy nebo ID nebo jiné podmínky, které můžou způsobovat chyby načítání.|
|<xref:Microsoft.VisualStudio.Modeling.Validation.ValidationCategories>|Při volání metody ValidateCustom. Ověření v této kategorii je možné vyvolat pouze z kódu programu.<br /><br /> Další informace najdete v tématu [Vlastní kategorie ověření.](#custom)|

## <a name="where-to-place-validation-methods"></a>Kam umístit metody ověřování
 Stejný účinek můžete často dosáhnout umístěním metody ověřování na jiný typ. Můžete například přidat metodu do třídy Person místo vztahu Parents Vychytátka A iterovat pomocí odkazů:

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

 **Agregování ověřovacích omezení** Pokud chcete použít ověřování v předvídatelných pořadích, definujte jednu metodu ověřování ve třídě vlastníka, jako je například kořenový prvek modelu. Tato technika také umožňuje agregovat více zpráv o chybách do jedné zprávy.

 Nevýhodou je, že kombinovaná metoda je méně snadná a omezení musí mít stejnou metodu `ValidationCategories` . Proto doporučujeme ponechat každé omezení v samostatné metodě, pokud je to možné.

 **Předávání hodnot v mezipaměti kontextu.** Parametr context má slovník, do kterého můžete umístit libovolné hodnoty. Slovník se zachová po dobu běhu ověření. Konkrétní metoda ověřování může například ponechat počet chyb v kontextu a použít ji, aby se zabránilo zahlcení chybového okna opakovanými zprávami. Příklad:

```csharp
List<ParentsHaveChildren> erroneousLinks;
if (!context.TryGetCacheValue("erroneousLinks", out erroneousLinks))
erroneousLinks = new List<ParentsHaveChildren>();
erroneousLinks.Add(this);
context.SetCacheValue("erroneousLinks", erroneousLinks);
if (erroneousLinks.Count < 5) { context.LogError( ... ); }
```

## <a name="validation-of-multiplicities"></a>Ověření násobení
 Metody ověřování pro kontrolu minimální násobnosti se automaticky generují pro váš DSL. Kód je zapsán do **souboru Dsl\Generated Code\MultiplicityValidation.cs**. Tyto metody se projeví, když povolíte ověřování v uzlu **Editor\Validation** v průzkumníku DSL.

 Pokud nastavíte násobnost role relace domény na 1..* nebo 1..1, ale uživatel nevytváří odkaz na tento vztah, zobrazí se chybová zpráva ověření.

 Například pokud váš DSL má třídy Person (Osoba) a Town (Město) a vztah PersonLivesIn Přístup s vztahem **1. \\** * v roli města a pak se pro každou osobu, která nemá žádné město, zobrazí chybová zpráva.

## <a name="running-validation-from-program-code"></a>Spuštění ověření z kódu programu
 Ověření můžete spustit tak, že se k ověřovacímu řadiči přistupujete nebo vytvoříte. Pokud chcete, aby se chyby v chybovém okně uživateli zobrazují, použijte ValidationController, který je připojený k DocData vašeho diagramu. Pokud například píšete příkaz nabídky, je `CurrentDocData.ValidationController` k dispozici ve třídě command set:

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

 Další informace najdete v [tématu Postupy: Přidání příkazu do místní nabídky](../modeling/how-to-add-a-command-to-the-shortcut-menu.md).

 Můžete také vytvořit samostatný kontroler ověřování a spravovat chyby sami. Příklad:

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

## <a name="running-validation-when-a-change-occurs"></a>Spuštění ověření, když dojde ke změně
 Pokud se chcete ujistit, že uživatel bude upozorněn okamžitě, pokud je model neplatný, můžete definovat událost úložiště, která spouští ověřování. Další informace o událostech úložiště najdete v tématu [obslužné rutiny událostí rozšiřují změny mimo model](../modeling/event-handlers-propagate-changes-outside-the-model.md).

 Kromě ověřovacího kódu přidejte do projektu **DslPackage** vlastní soubor kódu s podobným obsahem jako v následujícím příkladu. Tento kód používá `ValidationController` , který je připojen k dokumentu. Tento kontroler zobrazuje chyby ověřování v seznamu chyb sady Visual Studio.

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

 Obslužné rutiny jsou také volány po operaci zpět nebo znovu, které ovlivňují odkazy nebo prvky.

## <a name="custom-validation-categories"></a><a name="custom"></a> Vlastní kategorie ověřování
 Kromě standardních kategorií ověřování, jako je například nabídka a otevřít, můžete definovat vlastní kategorie. Tyto kategorie můžete vyvolat z programového kódu. Uživatel je nemůže vyvolat přímo.

 Typickým použitím vlastních kategorií je definování kategorie, která testuje, zda model splňuje podmínky pro konkrétní nástroj.

 Chcete-li přidat metodu ověřování do konkrétní kategorie, použijte ji jako předponu atributu:

```csharp
[ValidationMethod(CustomCategory = "PreconditionsForGeneratePartsList")]
[ValidationMethod(ValidationCategory.Menu)]
private void TestForCircularLinks(ValidationContext context)
{...}
```

> [!NOTE]
> Můžete vytvořit předponu metody s libovolným počtem `[ValidationMethod()]` atributů, kolik chcete. Můžete přidat metodu do vlastních i standardních kategorií.

 Postup při volání vlastního ověření:

```csharp

// Invoke all validation methods in a custom category:
validationController.ValidateCustom
  (store, // or a list of model elements
   "PreconditionsForGeneratePartsList");
```

## <a name="alternatives-to-validation"></a><a name="alternatives"></a> Alternativy k ověřování
 Omezení ověřování hlásí chyby, ale nemění model. Pokud místo toho chcete zabránit tomu, aby se model stal neplatným, můžete použít jiné techniky.

 Tyto techniky se ale nedoporučují. Je obvykle lepší umožnit uživateli rozhodnout, jak opravit neplatný model.

 **Úpravou změny obnovte platnost modelu.** Pokud uživatel například nastaví vlastnost nad povolené maximum, mohli byste obnovit vlastnost na maximální hodnotu. Uděláte to tak, že definujete pravidlo. Další informace najdete v tématu [pravidla šířící změny v modelu](../modeling/rules-propagate-changes-within-the-model.md).

 **Pokud se pokusíte o neplatnou změnu, vraťte transakci zpět.** Můžete také definovat pravidlo pro tento účel, ale v některých případech je možné přepsat obslužnou rutinu vlastnosti **OnValueChanging ()** nebo přepsat metodu, například chcete-li `OnDeleted().` vrátit transakci, použijte `this.Store.TransactionManager.CurrentTransaction.Rollback().` Další informace v tématu [obslužné rutiny změny hodnoty vlastnosti domény](../modeling/domain-property-value-change-handlers.md).

> [!WARNING]
> Ujistěte se, že uživatel ví, že změna byla upravena nebo vrácena zpět. Například použijte `System.Windows.Forms.MessageBox.Show("message").`

## <a name="see-also"></a>Viz také

- [Navigace v modelu a aktualizace modelu v kódu programu](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [Obslužné rutiny události šířící změny mimo model](../modeling/event-handlers-propagate-changes-outside-the-model.md)
