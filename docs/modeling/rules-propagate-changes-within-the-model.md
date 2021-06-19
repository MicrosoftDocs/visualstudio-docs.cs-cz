---
title: Pravidla šířící změny v modelu
description: Zjistěte, jak můžete vytvořit pravidlo úložiště pro rozšíření změny z jednoho prvku do druhého v sadě Visualization and Modeling SDK (VMSDK).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, programming domain models
- Domain-Specific Language, rules
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: bde67bd8375e3752370b3b815f8ed155d3123741
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2021
ms.locfileid: "112387590"
---
# <a name="rules-propagate-changes-within-the-model"></a>Pravidla šířící změny v modelu
Můžete vytvořit pravidlo úložiště, které rozšíří změnu z jednoho prvku do druhého v sadě Visualization and Modeling SDK (VMSDK). Pokud dojde ke změně libovolného prvku v obchodě, pravidla jsou naplánována ke spuštění, obvykle při vnější transakce je potvrzena. Existují různé typy pravidel pro různé druhy událostí, například přidání elementu nebo jeho odstranění. Pravidla můžete připojit ke konkrétním typům prvků, tvarů nebo diagramů. Mnoho předdefinovaných funkcí je definováno pravidly: například pravidla zajišťují, že se diagram aktualizuje, když se model změní. Jazyk specifický pro doménu můžete přizpůsobit přidáním vlastních pravidel.

 Pravidla úložiště jsou zvláště užitečná pro šíření změn v rámci úložiště – to znamená změny prvků modelu, relací, obrazců nebo konektorů a jejich vlastností domény. Pravidla se nespouštěly, když uživatel vyvolá příkazy Zpět nebo Znovu. Místo toho správce transakcí zajišťuje, že obsah úložiště jsou obnoveny do správného stavu. Pokud chcete rozšířit změny prostředků mimo úložiště, použijte Store Events (Události úložiště). Další informace najdete v tématu [Obslužné rutiny událostí šíří změny mimo model](../modeling/event-handlers-propagate-changes-outside-the-model.md).

 Předpokládejme například, že chcete určit, že když uživatel (nebo váš kód) vytvoří nový prvek typu ExampleDomainClass, vytvoří se další prvek jiného typu v jiné části modelu. Mohli byste napsat AddRule a přidružit ho k ExampleDomainClass. V pravidle byste napsali kód pro vytvoření dalšího elementu.

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using Microsoft.VisualStudio.Modeling;

namespace ExampleNamespace
{
 // Attribute associates the rule with a domain class:
 [RuleOn(typeof(ExampleDomainClass), FireTime=TimeToFire.TopLevelCommit)]
 // The rule is a class derived from one of the abstract rules:
 class MyAddRule : AddRule
 {
  // Override the abstract method:
  public override void ElementAdded(ElementAddedEventArgs e)
  {
    base.ElementAdded(e);
    ExampleDomainClass element = e.ModelElement;
    Store store = element.Store;
    // Ignore this call if we're currently loading a model:
    if (store.TransactionManager.CurrentTransaction.IsSerializing)
       return;

    // Code here propagates change as required - for example:
      AnotherDomainClass echo = new AnotherDomainClass(element.Partition);
      echo.Name = element.Name;
      echo.Parent = element.Parent;
    }
  }
 // The rule must be registered:
 public partial class ExampleDomainModel
 {
   protected override Type[] GetCustomDomainModelTypes()
   {
     List<Type> types = new List<Type>(base.GetCustomDomainModelTypes());
     types.Add(typeof(MyAddRule));
     // If you add more rules, list them here.
     return types.ToArray();
   }
 }
}
```

> [!NOTE]
> Kód pravidla by měl změnit stav jenom prvků uvnitř Store. To znamená, že pravidlo by mělo měnit pouze prvky modelu, relace, tvary, konektory, diagramy nebo jejich vlastnosti. Pokud chcete rozšířit změny prostředků mimo úložiště, definujte Store Events (Události úložiště). Další informace najdete v tématu [Obslužné rutiny událostí šíří změny mimo model](../modeling/event-handlers-propagate-changes-outside-the-model.md).

### <a name="to-define-a-rule"></a>Definování pravidla

1. Definujte pravidlo jako třídu s předponou `RuleOn` atributu . Atribut přidruží pravidlo k jedné z doménových tříd, relací nebo prvků diagramu. Pravidlo se použije pro každou instanci této třídy, která může být abstraktní.

2. Zaregistrujte pravidlo tak, že ho přidáte do sady vrácené ve `GetCustomDomainModelTypes()` třídě doménového modelu.

3. Odvození třídy pravidla z jedné z abstraktních tříd Rule a zápis kódu metody provádění.

   Následující části popisují tyto kroky podrobněji.

### <a name="to-define-a-rule-on-a-domain-class"></a>Definování pravidla pro třídu domény

- V souboru vlastního kódu definujte třídu a před ní zadejte předponu <xref:Microsoft.VisualStudio.Modeling.RuleOnAttribute> atributu :

    ```csharp
    [RuleOn(typeof(ExampleElement),
         // Usual value - but required, because it is not the default:
         FireTime = TimeToFire.TopLevelCommit)]
    class MyRule ...

    ```

- Typ předmětu v prvním parametru může být třída domény, vztah domény, tvar, konektor nebo diagram. Obvykle se pravidla aplikují na třídy domén a relace.

     je `FireTime` obvykle `TopLevelCommit` . Tím se zajistí, že se pravidlo spustí až po provedení všech primárních změn transakce. Alternativy jsou Vložené, které spustí pravidlo krátce po změně. a LocalCommit, které spustí pravidlo na konci aktuální transakce (která nemusí být nejvzdálenější). Můžete také nastavit prioritu pravidla, která ovlivní jeho řazení ve frontě, ale toto je nespolehlivá metoda, jak dosáhnout požadovaného výsledku.

- Jako typ předmětu můžete zadat abstraktní třídu.

- Pravidlo platí pro všechny instance třídy předmětu.

- Výchozí hodnota pro je `FireTime` TimeToFire.TopLevelCommit. To způsobí, že pravidlo se spustí, když je potvrzena vnější transakce. Alternativou je TimeToFire.Inline. To způsobí, že se pravidlo spustí brzy po aktivační události.

### <a name="to-register-the-rule"></a>Registrace pravidla

- Přidejte třídu pravidla do seznamu typů vrácených `GetCustomDomainModelTypes` v doménovém modelu:

    ```csharp
    public partial class ExampleDomainModel
     {
       protected override Type[] GetCustomDomainModelTypes()
       {
         List<Type> types = new List<Type>(base.GetCustomDomainModelTypes());
         types.Add(typeof(MyAddRule));
         // If you add more rules, list them here.
         return types.ToArray();
       }
     }

    ```

- Pokud si nejste jistí názvem vaší třídy modelu domény, nahlédněte do souboru **Dsl\GeneratedCode\DomainModel.cs.**

- Napište tento kód do souboru vlastního kódu v projektu DSL.

### <a name="to-write-the-code-of-the-rule"></a>Napsání kódu pravidla

- Odvození třídy pravidla z jedné z následujících základních tříd:

  | Základní třída | Trigger |
  |-|-|
  | <xref:Microsoft.VisualStudio.Modeling.AddRule> | Přidá se prvek, propojení nebo tvar.<br /><br /> Pomocí této funkce můžete kromě nových prvků detekovat i nové relace. |
  | <xref:Microsoft.VisualStudio.Modeling.ChangeRule> | Hodnota vlastnosti domény se změní. Argument metody poskytuje staré a nové hodnoty.<br /><br /> U tvarů se toto pravidlo aktivuje při změně `AbsoluteBounds` předdefinované vlastnosti, pokud se tvar přesune.<br /><br /> V mnoha případech je pohodlnější přepsat `OnValueChanged` nebo v `OnValueChanging` obslužné rutině vlastnosti. Tyto metody jsou volány bezprostředně před změnou a po nich. Naopak pravidlo se obvykle spouští na konci transakce. Další informace najdete v tématu [Obslužné rutiny změn vlastností domény.](../modeling/domain-property-value-change-handlers.md) **Poznámka:**  Toto pravidlo se nespouští při vytvoření nebo odstranění odkazu. Místo toho pro `AddRule` vztah domény zapište a `DeleteRule` . |
  | <xref:Microsoft.VisualStudio.Modeling.DeletingRule> | Aktivuje se, když se má odstranit prvek nebo odkaz. Vlastnost ModelElement.IsDeleting je true až do konce transakce. |
  | <xref:Microsoft.VisualStudio.Modeling.DeleteRule> | Provede se při odstranění elementu nebo propojení. Pravidlo se spustí po spuštění všech ostatních pravidel, včetně odstranění pravidel. ModelElement.IsDeleting má hodnotu false a ModelElement.IsDeleted má hodnotu true. Aby bylo možné následné vrácení zpět, není prvek ve skutečnosti odebrán z paměti, ale je odebrán z Store.ElementDirectory. |
  | <xref:Microsoft.VisualStudio.Modeling.MoveRule> | Prvek je přesunut z jednoho oddílu úložiště do jiného.<br /><br /> (Všimněte si, že to s grafickým umístěním obrazce souvisí.) |
  | <xref:Microsoft.VisualStudio.Modeling.RolePlayerChangeRule> | Toto pravidlo se vztahuje pouze na vztahy mezi doménami. Aktivuje se, pokud explicitně přiřadíte prvek modelu k jednomu konci propojení. |
  | <xref:Microsoft.VisualStudio.Modeling.RolePlayerPositionChangeRule> | Aktivuje se při změně pořadí odkazů na prvek nebo z elementu pomocí metod MoveBefore nebo MoveToIndex u odkazu. |
  | <xref:Microsoft.VisualStudio.Modeling.TransactionBeginningRule> | Provede se při vytvoření transakce. |
  | <xref:Microsoft.VisualStudio.Modeling.TransactionCommittingRule> | Spuštěno, když se transakce má být potvrzena. |
  | <xref:Microsoft.VisualStudio.Modeling.TransactionRollingBackRule> | Provede se, když se transakce vrátí zpět. |

- Každá třída má metodu, kterou přepíšete. Zadejte `override` do třídy , abyste ji zjistili. Parametr této metody identifikuje prvek, který se mění.

  Všimněte si následujících bodů o pravidlech:

1. Sada změn v transakci může aktivovat mnoho pravidel. Pravidla se obvykle spustí, když je potvrzena vnější transakce. Provádějí se v neurčeném pořadí.

2. Pravidlo se vždy provádí v rámci transakce. Proto není nutné vytvářet novou transakci, aby bylo možné provádět změny.

3. Pravidla se nespouštěly při vrácení transakce zpět nebo provádění operací Vrácení zpět nebo Znovu. Tyto operace obnoví veškerý obsah úložiště do předchozího stavu. Proto pokud vaše pravidlo změní stav cokoli mimo Store, nemusí být synchronizované s obsahem Store. Pokud chcete aktualizovat stav mimo Store, je lepší použít Události. Další informace najdete v tématu [Obslužné rutiny událostí šíří změny mimo model](../modeling/event-handlers-propagate-changes-outside-the-model.md).

4. Některá pravidla se spustí při načtení modelu ze souboru . Pokud chcete zjistit, jestli probíhá načítání nebo ukládání, použijte `store.TransactionManager.CurrentTransaction.IsSerializing` .

5. Pokud kód vašeho pravidla vytvoří další triggery pravidla, přičtou se na konec seznamu aktivací a spustí se před dokončením transakce. Pravidla DeletedRule se spouští po všech ostatních pravidlech. Jedno pravidlo může v transakci spustit mnohokrát, jednou pro každou změnu.

6. Pokud chcete předávat informace do a z pravidel, můžete ukládat informace v `TransactionContext` . Toto je pouze slovník, který se udržuje během transakce. Je uvolněna, když transakce skončí. Argumenty události v každém pravidle k ní poskytují přístup. Mějte na paměti, že pravidla nejsou spouštěna v předvídatelném pořadí.

7. Po zvážení dalších alternativ používejte pravidla. Pokud například chcete aktualizovat vlastnost při změně hodnoty, zvažte použití počítané vlastnosti. Pokud chcete omezit velikost nebo umístění tvaru, použijte `BoundsRule` . Pokud chcete reagovat na změnu v hodnotě vlastnosti, přidejte `OnValueChanged` obslužnou rutinu do vlastnosti. Další informace najdete v tématu [reagování na změny a šíření změn](../modeling/responding-to-and-propagating-changes.md).

## <a name="example"></a>Příklad
 Následující příklad aktualizuje vlastnost při vytvoření instance doménového vztahu pro propojení dvou prvků. Pravidlo se aktivuje nejen v případě, že uživatel vytvoří odkaz na diagram, ale také v případě, že kód programu vytvoří odkaz.

 Tento příklad otestujete tak, že vytvoříte DSL pomocí šablony řešení Flow úlohy a do souboru v projektu DSL vložíte následující kód. Sestavte a spusťte řešení a otevřete vzorový soubor v projektu ladění. Nakreslete odkaz na komentář mezi obrazcem komentáře a prvkem toku. Text v komentáři se změní na sestavu s posledním prvkem, ke kterému jste ho připojili.

 V praxi byste obvykle napsali DeleteRule pro každou AddRule.

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using Microsoft.VisualStudio.Modeling;

namespace Company.TaskRuleExample
{

  [RuleOn(typeof(CommentReferencesSubjects))]
  public class RoleRule : AddRule
  {

    public override void ElementAdded(ElementAddedEventArgs e)
    {
      base.ElementAdded(e);
      CommentReferencesSubjects link = e.ModelElement as CommentReferencesSubjects;
      Comment comment = link.Comment;
      FlowElement subject = link.Subject;
      Transaction current = link.Store.TransactionManager.CurrentTransaction;
      // Don't want to run when we're just loading from file:
      if (current.IsSerializing) return;
      comment.Text = "Flow has " + subject.FlowTo.Count + " outgoing connections";
    }

  }

  public partial class TaskRuleExampleDomainModel
  {
    protected override Type[] GetCustomDomainModelTypes()
    {
      List<Type> types = new List<Type>(base.GetCustomDomainModelTypes());
      types.Add(typeof(RoleRule));
      return types.ToArray();
    }
  }

}
```

## <a name="see-also"></a>Viz také

- [Obslužné rutiny události šířící změny mimo model](../modeling/event-handlers-propagate-changes-outside-the-model.md)