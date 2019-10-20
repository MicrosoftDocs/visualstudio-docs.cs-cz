---
title: Ověřování v jazyce specifickém pro doménu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, constraints
- Domain-Specific Language, validation
ms.assetid: 65b93df8-af3c-462b-904c-60292f8ed381
caps.latest.revision: 35
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9a19ebab7b0c820e336965b4020eff2c2f9726cd
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72659356"
---
# <a name="validation-in-a-domain-specific-language"></a>Ověřování v jazyce specifickém pro doménu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Jako autor jazyka DSL (Domain-Specific Language) můžete definovat ověřovací omezení a ověřit tak, že model vytvořený uživatelem má smysl. Pokud například vaše DSL umožňuje uživatelům nakreslit rodinný strom lidí a jejich předchůdce, mohli byste napsat omezení, které zajistí, že budou mít děti data po jejich rodičůch.

 Omezení ověřování můžete provést, pokud je model uložený, když je otevřený a uživatel explicitně spustí příkaz **ověřit** nabídku. Ověřování můžete provést také v části řízení programu. Můžete například spustit ověřování v reakci na změnu hodnoty vlastnosti nebo vztahu.

 Ověřování je obzvláště důležité, pokud píšete šablony textu nebo jiné nástroje, které zpracovávají modely vašich uživatelů. Ověřování zajišťuje, aby modely splňovaly podmínky, které tyto nástroje předpokládají.

> [!WARNING]
> Můžete taky dovolit, aby se ověřovací omezení definovala v samostatných rozšířeních DSL spolu s příkazy nabídky rozšíření a obslužnými rutinami gest. Uživatelé se můžou rozhodnout nainstalovat tato rozšíření kromě DSL. Další informace najdete v tématu věnovaném [rozšiřování DSL pomocí MEF](../modeling/extend-your-dsl-by-using-mef.md).

## <a name="running-validation"></a>Spouští se ověřování
 Když uživatel upravuje model, to znamená instanci vašeho jazyka specifického pro doménu, můžou ověření spustit následujícími akcemi:

- Klikněte pravým tlačítkem na diagram a vyberte **ověřit vše**.

- Klikněte pravým tlačítkem myši na horní uzel v Průzkumníkovi vaší DSL a vyberte možnost **ověřit vše** .

- Uložte model.

- Otevřete model.

- Kromě toho můžete napsat programový kód, který spouští ověřování, například jako součást příkazu nabídky nebo v reakci na změnu.

  V okně **Seznam chyb** se zobrazí všechny chyby ověřování. Uživatel může dvakrát kliknout na chybovou zprávu a vybrat prvky modelu, které jsou příčinou chyby.

## <a name="defining-validation-constraints"></a>Definování omezení ověřování
 Můžete definovat omezení ověřování přidáním metod ověřování do doménových tříd nebo vztahů vaší DSL. Při spuštění ověřování buď uživatelem, nebo v části řízení programu se spustí některé nebo všechny metody ověřování. Každá metoda je použita na každou instanci své třídy a v každé třídě může být několik metod ověřování.

 Každá metoda ověřování hlásí všechny nalezené chyby.

> [!NOTE]
> Metody ověřování hlásí chyby, ale nemění model. Pokud chcete upravit nebo zabránit určitým změnám, přečtěte si téma [alternativy ověřování](#alternatives).

#### <a name="to-define-a-validation-constraint"></a>Definování omezení ověřování

1. Povolit ověřování v uzlu **Editor\Validation** :

   1. Otevřete **Dsl\DslDefinition.DSL**.

   2. V Průzkumníku DSL rozbalte uzel **Editor** a vyberte **ověřování**.

   3. V okno Vlastnosti nastavte **pomocí** vlastnosti `true`. Nastavení všech těchto vlastností je nejpohodlnější.

   4. Na panelu nástrojů Průzkumník řešení klikněte na **transformovat všechny šablony** .

2. Pište částečné definice tříd pro jednu nebo více doménových tříd nebo doménových vztahů. Zapište tyto definice do nového souboru kódu v projektu **DSL** .

3. Každou třídu nasměrujte pomocí tohoto atributu:

   ```csharp
   [ValidationState(ValidationState.Enabled)]
   ```

   - Ve výchozím nastavení bude tento atribut také umožňovat ověřování pro odvozené třídy. Pokud chcete zakázat ověřování pro specifickou odvozenou třídu, můžete použít `ValidationState.Disabled`.

4. Přidejte do tříd metody ověřování. Každá metoda ověřování může mít libovolný název, ale má jeden parametr typu <xref:Microsoft.VisualStudio.Modeling.Validation.ValidationContext>.

    Musí být předpona s jedním nebo více `ValidationMethod` atributy:

   ```csharp
   [ValidationMethod (ValidationCategories.Open | ValidationCategories.Save | ValidationCategories.Menu ) ]
   ```

    ValidationCategories určuje, kdy se má metoda provést.

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

 Všimněte si následujících bodů tohoto kódu:

- Do doménových tříd nebo doménových vztahů můžete přidat metody ověřování. Kód pro tyto typy je v **Dsl\Generated Code\Domain \*. cs**.

- Každá metoda ověřování je použita na všechny instance své třídy a jejích podtříd. V případě doménového vztahu je každá instance propojení mezi dvěma prvky modelu.

- Metody ověřování nejsou aplikovány v žádném specifikovaném pořadí a jednotlivé metody nejsou aplikovány na instance své třídy v jakémkoli předvídatelném pořadí.

- Obvykle se jedná o špatný postup pro metodu ověřování, která aktualizuje obsah úložiště, protože by to vedlo k nekonzistentním výsledkům. Místo toho by měla metoda nahlásit jakoukoli chybu voláním `context.LogError`, `LogWarning` nebo `LogInfo`.

- V volání LogError můžete zadat seznam elementů modelu nebo propojení vztahů, které budou vybrány, když uživatel dvakrát klikne na chybovou zprávu.

- Informace o tom, jak číst model v programovém kódu, naleznete v tématu [navigace a aktualizace modelu v kódu programu](../modeling/navigating-and-updating-a-model-in-program-code.md).

  Příklad platí pro následující doménový model. Vztah ParentsHaveChildren má role pojmenované jako podřízené a nadřazené.

  ![Model stromu řady &#45; diagram definice DSL](../modeling/media/familyt-person.png "FamilyT_Person")

## <a name="validation-categories"></a>Kategorie ověřování
 V atributu <xref:Microsoft.VisualStudio.Modeling.Validation.ValidationMethodAttribute> určíte, kdy se má spustit metoda ověřování.

|Kategorie|Spuštění|
|--------------|---------------|
|<xref:Microsoft.VisualStudio.Modeling.Validation.ValidationCategories>|Když uživatel vyvolá příkaz pro ověření nabídky.|
|<xref:Microsoft.VisualStudio.Modeling.Validation.ValidationCategories>|Při otevření souboru modelu.|
|<xref:Microsoft.VisualStudio.Modeling.Validation.ValidationCategories>|Při uložení souboru. Pokud dojde k chybám ověření, uživateli bude dána možnost zrušit operaci uložení.|
|<xref:Microsoft.VisualStudio.Modeling.Validation.ValidationCategories>|Při uložení souboru. Pokud v této kategorii dojde k chybám, uživateli se zobrazí upozornění, že nemusí být možné soubor znovu otevřít.<br /><br /> Tuto kategorii použijte k ověřování metod, které testuje duplicitní názvy nebo ID, nebo jiné podmínky, které mohou způsobit chyby při načítání.|
|<xref:Microsoft.VisualStudio.Modeling.Validation.ValidationCategories>|Když je volána metoda ValidateCustom. Ověření v této kategorii lze vyvolat pouze z kódu programu.<br /><br /> Další informace najdete v tématu [vlastní kategorie ověření](#custom).|

## <a name="where-to-place-validation-methods"></a>Kam umístit metody ověřování
 Stejný účinek lze často dosáhnout umístěním metody ověřování na jiný typ. Například můžete přidat metodu do třídy Person namísto vztahu ParentsHaveChildren a nechat ji iterovat prostřednictvím odkazů:

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

 **Agregace omezení ověřování.** Chcete-li použít ověřování v předvídatelném pořadí, definujte jedinou metodu ověření pro třídu Owner, například kořenový prvek modelu. Tato technika také umožňuje agregovat více zpráv o chybách do jedné zprávy.

 Nevýhodami je, že kombinovaná metoda je méně jednoduchá ke správě a že omezení musí mít všechny stejné `ValidationCategories`. Proto doporučujeme, abyste každé omezení zachovali v samostatné metodě, pokud je to možné.

 **Předávání hodnot v mezipaměti kontextu.** Kontextový parametr obsahuje slovník, do kterého lze umístit libovolné hodnoty. Slovník přetrvává po dobu životnosti běhu ověřování. Konkrétní metoda ověřování může například v kontextu zachovat počet chyb a použít ho k tomu, abyste zabránili zahlcení okna chyb opakovanými zprávami. Příklad:

```csharp
List<ParentsHaveChildren> erroneousLinks;
if (!context.TryGetCacheValue("erroneousLinks", out erroneousLinks))
erroneousLinks = new List<ParentsHaveChildren>();
erroneousLinks.Add(this);
context.SetCacheValue("erroneousLinks", erroneousLinks);
if (erroneousLinks.Count < 5) { context.LogError( ... ); }

```

## <a name="validation-of-multiplicities"></a>Ověřování násobnosti
 Metody ověřování pro kontrolu minimální násobnosti jsou automaticky generovány pro vaši DSL. Kód je zapsán do **Dsl\Generated Code\MultiplicityValidation.cs**. Tyto metody se projeví, když povolíte ověřování v uzlu **Editor\Validation** v Průzkumníku DSL.

 Pokud nastavíte násobnost role relace domény na hodnotu 1.. * nebo 1.. 1, ale uživatel nevytvoří odkaz na tento vztah, zobrazí se chybová zpráva ověření.

 Pokud například vaše DSL má třídy Person a město a relace PersonLivesInTown se vztahem **1.. \\** * v roli města, pak se zobrazí chybová zpráva pro každou osobu, která nemá město.

## <a name="running-validation-from-program-code"></a>Spuštění ověřování z kódu programu
 Ověřování můžete spustit přístupem k ValidationController nebo jeho vytvořením. Chcete-li, aby se chyby zobrazily uživateli v okně chyby, použijte ValidationController, který je připojen k DocData vašeho diagramu. Například při psaní příkazu nabídky je `CurrentDocData.ValidationController` k dispozici ve třídě sady příkazů:

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

 Další informace najdete v tématu [Postup: Přidání příkazu do místní nabídky](../modeling/how-to-add-a-command-to-the-shortcut-menu.md).

 Můžete také vytvořit samostatný kontroler ověřování a chyby spravovat sami. Příklad:

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

## <a name="running-validation-when-a-change-occurs"></a>Spuštění ověřování, když dojde ke změně
 Pokud se chcete ujistit, že uživatel bude upozorněn okamžitě, pokud je model neplatný, můžete definovat událost úložiště, která spouští ověřování. Další informace o událostech úložiště najdete v tématu [obslužné rutiny událostí rozšiřují změny mimo model](../modeling/event-handlers-propagate-changes-outside-the-model.md).

 Kromě ověřovacího kódu přidejte do projektu **DslPackage** vlastní soubor kódu s podobným obsahem jako v následujícím příkladu. Tento kód používá `ValidationController`, který je připojen k dokumentu. Tento kontroler zobrazuje chyby ověřování v seznamu chyb [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

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

## <a name="custom"></a>Vlastní kategorie ověřování
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
> Můžete vytvořit předponu metody s libovolným počtem atributů `[ValidationMethod()]`, kolik chcete. Můžete přidat metodu do vlastních i standardních kategorií.

 Postup při volání vlastního ověření:

```csharp

// Invoke all validation methods in a custom category:
validationController.ValidateCustom
  (store, // or a list of model elements
   "PreconditionsForGeneratePartsList");
```

## <a name="alternatives"></a>Alternativy k ověřování
 Omezení ověřování hlásí chyby, ale nemění model. Pokud místo toho chcete zabránit tomu, aby se model stal neplatným, můžete použít jiné techniky.

 Tyto techniky se ale nedoporučují. Je obvykle lepší umožnit uživateli rozhodnout, jak opravit neplatný model.

 **Úpravou změny obnovte platnost modelu.** Pokud uživatel například nastaví vlastnost nad povolené maximum, mohli byste obnovit vlastnost na maximální hodnotu. Uděláte to tak, že definujete pravidlo. Další informace najdete v tématu [pravidla šířící změny v modelu](../modeling/rules-propagate-changes-within-the-model.md).

 **Pokud se pokusíte o neplatnou změnu, vraťte transakci zpět.** Můžete také definovat pravidlo pro tento účel, ale v některých případech je možné přepsat obslužnou rutinu vlastnosti **OnValueChanging ()** nebo přepsat metodu, například `OnDeleted().` pro vrácení transakce zpět, použití `this.Store.TransactionManager.CurrentTransaction.Rollback().` pro další informace najdete v tématu [doménová vlastnost. Obslužné rutiny změn hodnot](../modeling/domain-property-value-change-handlers.md)

> [!WARNING]
> Ujistěte se, že uživatel ví, že změna byla upravena nebo vrácena zpět. Použijte například `System.Windows.Forms.MessageBox.Show("message").`

## <a name="see-also"></a>Viz také
 [Navigace v modelu a aktualizace modelu v](../modeling/navigating-and-updating-a-model-in-program-code.md) [obslužných rutinách událostí kódu programu šíří změny mimo model](../modeling/event-handlers-propagate-changes-outside-the-model.md)
