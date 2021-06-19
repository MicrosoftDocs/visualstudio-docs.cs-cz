---
title: Obslužná rutina změny hodnoty vlastnosti domény
description: Přečtěte si o obslužných rutinách změny hodnoty vlastnosti domény, které je možné Visual Studio v jazyce specifickém pro doménu.
ms.custom: SEO-VS-2020
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, overriding event handlers
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 1c6cdb027bafdf4d1fe7689d7dd30d697b539370
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388994"
---
# <a name="domain-property-value-change-handlers"></a>Obslužné rutiny změny hodnoty vlastnosti domény

V Visual Studio jazyka specifickém pro doménu se při změně hodnoty vlastnosti domény v obslužné rutině vlastností domény vyvolá `OnValueChanging()` `OnValueChanged()` metody a . Pokud chcete na změnu reagovat, můžete tyto metody přepsat.

## <a name="override-the-property-handler-methods"></a>Přepsání metod obslužné rutiny vlastností

Každá vlastnost domény jazyka specifického pro doménu je zpracováván třídou, která je vnořena do její nadřazené třídy domény. Jeho název má formát *PropertyName* PropertyHandler. Tuto třídu obslužné rutiny vlastnosti můžete zkontrolovat v souboru **Dsl\Generated Code\DomainClasses.cs**. Ve třídě je volána bezprostředně před změnou hodnoty a je `OnValueChanging()` `OnValueChanged()` volána ihned po změně hodnoty.

Předpokládejme například, že máte třídu domény s názvem , která má vlastnost domény řetězce s názvem `Comment` a `Text` celočíselnou vlastnost s názvem `TextLengthCount` . Pokud chcete, aby vždy obsahoval délku řetězce, můžete do samostatného souboru v projektu Dsl napsat `TextLengthCount` `Text` následující kód:

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

Všimněte si následujících bodů o obslužných rutinách vlastností:

- Metody obslužné rutiny vlastnosti jsou volány jak při změně vlastnosti domény uživatelem, tak v případě, že programový kód přiřadí vlastnosti jinou hodnotu.

- Metody jsou volány pouze v případě, že se hodnota skutečně změní. Obslužná rutina není vyvolána, pokud programový kód přiřadí hodnotu, která se rovná aktuální hodnotě.

- Počítané a vlastní vlastnosti domény úložiště nemají metody OnValueChanged a OnValueChanging.

- K úpravě nové hodnoty nelze použít obslužnou rutinu změn. Pokud chcete například omezit hodnotu na konkrétní rozsah, definujte `ChangeRule` .

- Obslužnou rutinu změny nelze přidat do vlastnosti, která představuje roli vztahu. Místo toho `AddRule` definujte a `DeleteRule` ve třídě relace. Tato pravidla se spustí při vytvoření nebo změně odkazů. Další informace najdete v tématu [Pravidla šíří změny v rámci modelu.](../modeling/rules-propagate-changes-within-the-model.md)

### <a name="changes-in-and-out-of-the-store"></a>Změny v a mimo úložiště

Metody obslužné rutiny vlastností jsou volány uvnitř transakce, která iniciovala změnu. Proto můžete provádět další změny v obchodě bez otevření nové transakce. Vaše změny můžou vést k dalším voláním obslužné rutiny.

Když se transakce vrací zpět, znovu se vrátí nebo se vrátí zpět, neměli byste provádět změny v obchodě, to znamená změny prvků modelu, relací, obrazců, diagramů konektorů nebo jejich vlastností.

Kromě toho byste obvykle ne aktualizací hodnot při načítání modelu ze souboru .

Změny modelu by proto měly být strážené tímto testem:

```csharp
if (!store.InUndoRedoOrRollback && !store. InSerializationTransaction)
{
   this.TextLength = ...; // in-store changes
}
```

Naopak pokud obslužná rutina vlastnosti šíří změny mimo úložiště, například do souboru, databáze nebo neskladových proměnných, měli byste tyto změny vždy provést, aby se externí hodnoty aktualizovaly, když uživatel vyvolá vrácení zpět nebo znovu.

### <a name="cancel-a-change"></a>Zrušení změny

Pokud chcete zabránit změně, můžete vrátit aktuální transakci zpět. Můžete například chtít zajistit, aby vlastnost zůstala v určitém rozsahu.

```csharp
if (newValue > 10)
{
   store.TransactionManager.CurrentTransaction.Rollback();
   System.Windows.Forms.MessageBox.Show("Value must be less than 10");
}
```

### <a name="alternative-technique-calculated-properties"></a>Alternativní technika: Počítané vlastnosti

Předchozí příklad ukazuje, jak lze metodu OnValueChanged() použít k šíření hodnot z jedné vlastnosti domény do druhé. Každá vlastnost má svou vlastní uloženou hodnotu.

Místo toho můžete zvážit definování odvozené vlastnosti jako vlastnosti Calculated. V takovém případě vlastnost nemá vlastní úložiště a definuje funkci, která se vyhodnotí vždy, když je její hodnota požadována. Další informace najdete v tématu [Počítané a vlastní vlastnosti úložiště.](../modeling/calculated-and-custom-storage-properties.md)

Místo předchozího příkladu byste mohli nastavit pole **Druh** pro , `TextLengthCount` aby se **vypočítal** v definici DSL. Pro tuto vlastnost **domény** byste měli zadat vlastní metodu Get. Metoda **Get** vrátí aktuální délku `Text` řetězce.

Potenciální nevýhodou počítaných vlastností je ale to, že se výraz vyhodnocuje při každém použití hodnoty, což může být problém s výkonem. U počítané vlastnosti také nejsou žádné OnValueChanging() a OnValueChanged().

### <a name="alternative-technique-change-rules"></a>Alternativní technika: Změna pravidel

Pokud definujete ChangeRule, provede se na konci transakce, ve které se změní hodnota vlastnosti.  Další informace najdete v tématu [Pravidla šíří změny v rámci modelu.](../modeling/rules-propagate-changes-within-the-model.md)

Pokud je v jedné transakci provedeno několik změn, po dokončení všech se provede pravidlo změny. Naproti tomu onValue... Metody se spustí, když nebyly provedeny některé změny. V závislosti na tom, čeho chcete dosáhnout, může být pravidlo změn vhodnější.

Můžete také použít ChangeRule a upravit novou hodnotu vlastnosti tak, aby byla v určitém rozsahu.

> [!WARNING]
> Pokud pravidlo provede změny obsahu úložiště, můžou se aktivovat další pravidla a obslužné rutiny vlastností. Pokud pravidlo změní vlastnost, která ho aktivoval, bude volána znovu. Musíte zajistit, aby definice pravidel neskončily nekonečnou aktivací.

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

### <a name="description"></a>Description

Následující příklad přepíše obslužnou rutinu vlastnosti vlastnosti domény a upozorní uživatele při změně vlastnosti `ExampleElement` pro třídu domény.

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
