---
title: Obslužná rutina změny hodnoty vlastnosti domény
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, overriding event handlers
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2f23984d6c4723b020b361e1da30363442966ea7
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75594705"
---
# <a name="domain-property-value-change-handlers"></a>Obslužná rutina změny hodnoty vlastnosti domény

V jazyce Visual Studio specifického pro doménu, při změně hodnoty vlastnosti domény `OnValueChanging()` a `OnValueChanged()` jsou metody vyvolány v obslužné rutině vlastnost domény. Reakce na změny, můžete přepsat tyto metody.

## <a name="override-the-property-handler-methods"></a>Přepište metody obslužné rutiny vlastnosti

Každá doménová vlastnost jazyka specifického pro doménu je zpracována třídou, která je vnořená do své nadřazené třídy domény. Formát názvu *PropertyName*PropertyHandler. Tato třída obslužné rutiny vlastnosti v souboru si můžete prohlédnout **Dsl\Generated Code\DomainClasses.cs**. Ve třídě `OnValueChanging()` je volána bezprostředně před provedením změny hodnot a `OnValueChanged()` volat bezprostředně po změně hodnoty.

Předpokládejme například, že máte doménovou třídu s názvem `Comment` , který má řetězec doménovou vlastnost s názvem `Text` a celočíselnou vlastnost s názvem `TextLengthCount`. Způsobí `TextLengthCount` vždy tak, aby obsahovala délka `Text` řetězec, můžete napsat následující kód v samostatném souboru v projektu Dsl:

```csharp
// Domain Class "Comment":
public partial class Comment
{
  // Domain Property "Text":
  partial class TextPropertyHandler
  {
    protected override void OnValueChanging(CommentBase element, string oldValue, string newValue)
    {
      base.OnValueChanging(element, oldValue, newValue);

      // To update values outside the Store, write code here.

      // Let the transaction manager handle undo:
      Store store = element.Store;
      if (store.InUndoRedoOrRollback || store.InSerializationTransaction) return;

      // Update values in the Store:
      this.TextLengthCount = newValue.Length;
    }
  }
}
```

Všimněte si následujících o vlastnost obslužné rutiny:

- Když uživatel provede změny na doménovou vlastnost i při programovém kódu přiřadí jinou hodnotu pro vlastnost volání těchto metod obslužné rutiny vlastnosti.

- Pouze při změně hodnoty ve skutečnosti volání těchto metod. Obslužná rutina není vyvolána, pokud kód programu přiřadí hodnotu, která se rovná aktuální hodnotu.

- Vypočtené a vlastní domény vlastnosti úložiště nemusí metod OnValueChanged a OnValueChanging.

- Obslužná rutina změny nelze použít k úpravě novou hodnotu. Pokud chcete udělat, například k omezení hodnoty na konkrétní rozsah, definování `ChangeRule`.

- Nelze přidat obsluhu změnu vlastnosti, která představuje roli relace. Místo toho definujte `AddRule` a `DeleteRule` na třídu vztahu. Tato pravidla se aktivují v případě odkazů jsou vytvořené nebo změněné. Další informace najdete v tématu [pravidla šíření změn v rámci the Model](../modeling/rules-propagate-changes-within-the-model.md).

### <a name="changes-in-and-out-of-the-store"></a>Změny do a z úložiště

Vlastnost obslužnou rutinu metody jsou volány v transakci, která iniciovala změny. Proto můžete provést další změny v úložišti bez otevření nové transakce. Změny může mít za výsledek volání další obslužné rutiny.

Když se vrací zpět transakci, znovu, nebo vrátit zpět, by neměla provést změny v úložišti, to znamená, změní na prvky modelu, relace, tvary, konektory diagramů nebo jejich vlastností.

Kromě toho by obvykle aktualizujete hodnoty při načítání modelu ze souboru.

Změny v modelu by měly mít ochranu proto testem takto:

```csharp
if (!store.InUndoRedoOrRollback && !store. InSerializationTransaction)
{
   this.TextLength = ...; // in-store changes
}
```

Naopak pokud obslužné rutiny vlastnosti šíří změny mimo úložiště, například soubor, databáze nebo proměnné bez úložiště, pak můžete by měl vždy proveďte tyto změny tak, aby se aktualizují externí hodnoty, když uživatel vyvolá vrácení zpět nebo znovu.

### <a name="cancel-a-change"></a>Zrušit změnu

Pokud chcete, aby změnu, je aktuální transakce vrátit zpět. Například můžete chtít zajistit, aby zůstal vlastnost do určitého rozsahu.

```csharp
if (newValue > 10)
{
   store.TransactionManager.CurrentTransaction.Rollback();
   System.Windows.Forms.MessageBox.Show("Value must be less than 10");
}
```

### <a name="alternative-technique-calculated-properties"></a>Alternativní postup: počítá vlastností

Předchozí příklad ukazuje, jak lze pomocí OnValueChanged() šíření hodnoty z jedné doménové vlastnosti. Každá vlastnost má svůj vlastní uloženou hodnotu.

Zvažte místo toho definuje odvozená vlastnost jako vlastnost vypočítaná. Případ, vlastnost nemá žádné úložiště, a jedná o definici funkce je vyhodnocen vždy, když jeho hodnota je povinná. Další informace najdete v tématu [vypočtené a vlastní vlastnosti úložiště](../modeling/calculated-and-custom-storage-properties.md).

Místo v předchozím příkladu můžete nastavit **druh** pole `TextLengthCount` bude **vypočtené** v definici DSL. Bude poskytovat vlastní **získat** metody pro tuto vlastnost domény. **Získat** metoda vrátí aktuální délka `Text` řetězec.

Potenciální nevýhodou vypočítané vlastnosti je však, že tento výraz je vyhodnocen vždy, když je použita hodnota, které mohou představovat problém s výkonem. Navíc není žádná OnValueChanging() a OnValueChanged() u počítané vlastnosti.

### <a name="alternative-technique-change-rules"></a>Alternativní postup: změnit pravidla

Pokud definujete ChangeRule, provede se na konci transakce, ve kterém se změní hodnota vlastnosti.  Další informace najdete v tématu [pravidla šíření změn v rámci the Model](../modeling/rules-propagate-changes-within-the-model.md).

Pokud se provede několik změn v rámci jedné transakce ChangeRule spustí, pokud jsou všechny dokončené. Naopak OnValue... metody jsou spouštěny, když se některé změny nebyly provedeny. V závislosti na tom, co chcete dosáhnout to může mít ChangeRule vhodnější.

Také vám pomůže ChangeRule upravit novou hodnotu vlastnosti zajistit jeho do určitého rozsahu.

> [!WARNING]
> Pravidlo provede změny k uložení obsahu, může další pravidla a obslužné rutiny vlastnosti aktivuje. Pokud se pravidlo změní vlastnost, která se aktivuje, zavolá se znovu. Ujistěte se, že vaše definice pravidla za následek nekonečnou aktivace.

```csharp
using Microsoft.VisualStudio.Modeling;
...
// Change rule on the domain class Comment:
[RuleOn(typeof(Comment), FireTime = TimeToFire.TopLevelCommit)]
class MyCommentTrimRule : ChangeRule
{
  public override void
    ElementPropertyChanged(ElementPropertyChangedEventArgs e)
  {
    base.ElementPropertyChanged(e);
    Comment comment = e.ModelElement as Comment;

    if (comment.Text.StartsWith(" ") || comment.Text.EndsWith(" "))
      comment.Text = comment.Text.Trim();
    // If changed, rule will trigger again.
  }
}

// Register the rule:
public partial class MyDomainModel
{
 protected override Type[] GetCustomDomainModelTypes()
 { return new Type[] { typeof(MyCommentTrimRule) };
 }
}
```

## <a name="example"></a>Příklad

### <a name="description"></a>Popis

Následující příklad přepisuje vlastnost rutiny doménová vlastnost, která a upozorní uživatele, pokud vlastnost `ExampleElement` došlo ke změně třídy domény.

### <a name="code"></a>Kód

```csharp
using DslModeling = global::Microsoft.VisualStudio.Modeling;
using DslDesign = global::Microsoft.VisualStudio.Modeling.Design;

namespace msft.FieldChangeSample
{
  public partial class ExampleElement
  {
    internal sealed partial class NamePropertyHandler
    {
      protected override void OnValueChanged(ExampleElement element,
         string oldValue, string newValue)
      {
        if (!this.Store.InUndoRedoOrRollback)
        {
           // make in-store changes here...
        }
        // This part is called even in undo:
        System.Windows.Forms.MessageBox.Show("Value Has Changed");
        base.OnValueChanged(element, oldValue, newValue);
      }
    }
  }
}
```
