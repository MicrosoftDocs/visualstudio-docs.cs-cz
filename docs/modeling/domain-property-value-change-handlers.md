---
title: Obslužná rutina změny hodnoty vlastnosti domény
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, overriding event handlers
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 46bf3d8a188899e27e7a83d875cf970583858ba8
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72653783"
---
# <a name="domain-property-value-change-handlers"></a>Obslužné rutiny změny hodnoty vlastnosti domény

V jazyce specifickém pro doménu sady Visual Studio se při změně hodnoty vlastnosti domény vyvolají metody `OnValueChanging()` a `OnValueChanged()` v obslužné rutině vlastnosti domény. Pro reakci na změnu můžete tyto metody přepsat.

## <a name="override-the-property-handler-methods"></a>Přepsat metody obslužné rutiny vlastností

Každá doménová vlastnost jazyka specifického pro doménu je zpracována třídou, která je vnořena do své nadřazené třídy domény. Jeho název následuje po formátu *PropertyName*PropertyHandler. Tuto třídu obslužné rutiny vlastnosti můžete zkontrolovat v souboru **Dsl\Generated Code\DomainClasses.cs**. Ve třídě je `OnValueChanging()` volána bezprostředně před změnou hodnoty a `OnValueChanged()` je volána ihned po změně hodnoty.

Předpokládejme například, že máte doménovou třídu s názvem `Comment`, která má řetězcovou vlastnost domény s názvem `Text` a vlastnost Integer s názvem `TextLengthCount`. Chcete-li, aby `TextLengthCount` vždy obsahovala délku `Text` řetězce, mohli byste zapsat následující kód do samostatného souboru v projektu DSL:

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

Všimněte si následujících bodů obslužných rutin vlastností:

- Metody obslužné rutiny vlastností jsou volány v případě, že uživatel provede změny v doménové vlastnosti a když kód programu přiřadí k vlastnosti jinou hodnotu.

- Metody jsou volány pouze v případě, že se hodnota skutečně změní. Obslužná rutina není vyvolána, pokud kód programu přiřadí hodnotu, která je rovna aktuální hodnotě.

- Vypočítané a vlastní vlastnosti domény úložiště nemají metody OnValueChanged a OnValueChanging.

- Nelze použít obslužnou rutinu změn pro úpravu nové hodnoty. Chcete-li to provést, například pro omezení hodnoty na určitý rozsah, definujte `ChangeRule`.

- Do vlastnosti, která představuje roli vztahu, nelze přidat obslužnou rutinu změn. Místo toho definujte `AddRule` a `DeleteRule` na třídě Relationship. Tato pravidla se aktivují při vytváření nebo změně propojení. Další informace najdete v tématu [pravidla šířící změny v modelu](../modeling/rules-propagate-changes-within-the-model.md).

### <a name="changes-in-and-out-of-the-store"></a>Změny v úložišti a ven z něj

Metody obslužné rutiny vlastností jsou volány uvnitř transakce, která iniciovala změnu. Proto můžete v úložišti dělat další změny bez otevření nové transakce. Vaše změny můžou mít za následek další volání obslužných rutin.

V případě vrácení transakce zpět, opětovného dokončení nebo vrácení změn byste neměli provádět změny v úložišti, tedy změny prvků modelu, relací, tvarů, spojnicových diagramů nebo jejich vlastností.

Kromě toho byste obvykle neaktualizovali hodnoty při načítání modelu ze souboru.

Změny modelu by proto měly být chráněny následujícím testem:

```csharp
if (!store.InUndoRedoOrRollback && !store. InSerializationTransaction)
{
   this.TextLength = ...; // in-store changes
}
```

Naopak, pokud vaše obslužná rutina vlastnosti šíří změny mimo úložiště, například do souboru, databáze nebo proměnných neuloženého, pak byste tyto změny měli vždycky dělat, aby se tyto změny aktualizovaly, když uživatel vyvolá vrácení akce zpět nebo znovu.

### <a name="cancel-a-change"></a>Zrušit změnu

Pokud chcete zabránit změně, můžete aktuální transakci vrátit zpět. Například může být vhodné zajistit, aby vlastnost zůstala v určitém rozsahu.

```csharp
if (newValue > 10)
{
   store.TransactionManager.CurrentTransaction.Rollback();
   System.Windows.Forms.MessageBox.Show("Value must be less than 10");
}
```

### <a name="alternative-technique-calculated-properties"></a>Alternativní postup: vypočtené vlastnosti

Předchozí příklad ukazuje, jak lze pomocí OnValueChanged () rozšířit hodnoty z jedné doménové vlastnosti do jiné. Každá vlastnost má svou vlastní uloženou hodnotu.

Místo toho můžete zvážit definování odvozené vlastnosti jako počítané vlastnosti. V takovém případě vlastnost nemá žádné vlastní úložiště a je vyhodnocena funkcí, pokud je požadována její hodnota. Další informace najdete v tématu věnovaném [vypočítaným a vlastním vlastnostem úložiště](../modeling/calculated-and-custom-storage-properties.md).

Místo předchozího příkladu jste mohli nastavit pole **druh** `TextLengthCount`, které se má v definici DSL **Vypočítat** . Pro tuto doménovou vlastnost byste zadali vlastní metodu **Get** . Metoda **Get** vrátí aktuální délku řetězce `Text`.

Potenciální nevýhodou počítaných vlastností však je, že výraz je vyhodnocován při každém použití hodnoty, což může představovat problém s výkonem. Pro počítanou vlastnost nejsou k dispozici žádné OnValueChanging () a OnValueChanged ().

### <a name="alternative-technique-change-rules"></a>Alternativní postupy: Změna pravidel

Definujete-li ChangeRule, je proveden na konci transakce, ve které se změní hodnota vlastnosti.  Další informace najdete v tématu [pravidla šířící změny v modelu](../modeling/rules-propagate-changes-within-the-model.md).

Pokud se v jedné transakci provede několik změn, ChangeRule se spustí, až budou dokončená. Naproti tomu hodnota-... metody jsou spouštěny, pokud nebyly provedeny některé změny. V závislosti na tom, co chcete dosáhnout, může to ChangeRule být vhodnější.

Pomocí ChangeRule můžete také upravit novou hodnotu vlastnosti tak, aby se zachovala v konkrétním rozsahu.

> [!WARNING]
> Pokud pravidlo provede změny v obsahu úložiště, mohou se aktivovat další pravidla a obslužné rutiny vlastností. Pokud pravidlo změní vlastnost, která ji aktivovala, bude volána znovu. Je nutné zajistit, aby definice pravidel nezpůsobily nekonečné spouštění.

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

Následující příklad přepisuje obslužnou rutinu vlastnosti domény a upozorní uživatele, když se změní vlastnost pro třídu `ExampleElement` domény.

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