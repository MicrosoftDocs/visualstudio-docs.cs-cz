---
title: Pravidla šířící změny v modelu
description: Přečtěte si, jak můžete vytvořit pravidlo obchodu a rozšířit změnu z jednoho prvku na jiný v rámci vizualizace a modelování SDK (VMSDK).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, programming domain models
- Domain-Specific Language, rules
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 7062feddf00194e4633435655b5e11f5fefd38ee
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99916957"
---
# <a name="rules-propagate-changes-within-the-model"></a>Pravidla šířící změny v modelu
Můžete vytvořit pravidlo obchodu a rozšířit změnu z jednoho prvku na jiný v rámci vizualizace a modelování SDK (VMSDK). Když dojde ke změně jakéhokoli prvku v úložišti, pravidla se naplánují na spouštění, obvykle v případě, kdy je nejvzdálenější transakce potvrzena. Existují různé typy pravidel pro různé druhy událostí, jako je například přidání prvku nebo jeho odstranění. Můžete připojit pravidla ke konkrétním typům prvků, tvarů nebo diagramů. Mnoho vestavěných funkcí je definovaných pravidly: například pravidla zajišťují, že se diagram při změně modelu aktualizuje. Jazyk specifický pro doménu můžete přizpůsobit přidáním vlastních pravidel.

 Pravidla úložišť jsou zvláště užitečná pro rozšiřování změn v obchodě – to znamená změny prvků modelu, vztahů, tvarů a konektorů a jejich vlastností domény. Pravidla se nespustí, když uživatel vyvolá příkazy k vrácení zpět nebo znovu. Místo toho správce transakcí zajistí, že se obsah úložiště obnoví do správného stavu. Pokud chcete rozšířit změny prostředků mimo Store, použijte ukládání událostí. Další informace najdete v tématu [obslužné rutiny událostí rozšiřovat změny mimo model](../modeling/event-handlers-propagate-changes-outside-the-model.md).

 Předpokládejme například, že chcete určit, že pokud uživatel (nebo váš kód) vytvoří nový prvek typu ExampleDomainClass, je v jiné části modelu vytvořen další prvek jiného typu. Můžete napsat AddRule a přidružit ho k ExampleDomainClass. V pravidle byste napsali kód pro vytvoření dalšího elementu.

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
> Kód pravidla by měl změnit pouze stav prvků v rámci úložiště; To znamená, že pravidlo by mělo měnit pouze prvky modelu, relace, obrazce, konektory, diagramy nebo jejich vlastnosti. Pokud chcete rozšířit změny prostředků mimo Store, definujte události úložiště. Další informace najdete v tématu [obslužné rutiny událostí rozšiřovat změny mimo model](../modeling/event-handlers-propagate-changes-outside-the-model.md).

### <a name="to-define-a-rule"></a>Definování pravidla

1. Definujte pravidlo jako třídu s předponou s `RuleOn` atributem. Atribut přidruží pravidlo k jedné z vašich doménových tříd, relací nebo prvků diagramu. Pravidlo bude použito na všechny instance této třídy, což může být abstraktní.

2. Zaregistrujte pravidlo tím, že ho přidáte do sady vrácené `GetCustomDomainModelTypes()` ve vaší třídě doménového modelu.

3. Odvození třídy pravidla z jedné z abstraktních tříd pravidla a zápis kódu metody spuštění.

   Následující části popisují tyto kroky podrobněji.

### <a name="to-define-a-rule-on-a-domain-class"></a>Definování pravidla pro doménovou třídu

- V souboru vlastního kódu Definujte třídu a prefixujte ji <xref:Microsoft.VisualStudio.Modeling.RuleOnAttribute> atributem:

    ```csharp
    [RuleOn(typeof(ExampleElement),
         // Usual value - but required, because it is not the default:
         FireTime = TimeToFire.TopLevelCommit)]
    class MyRule ...

    ```

- Typ subjektu v prvním parametru může být doménová třída, doménová relace, tvar, spojnice nebo diagram. Obvykle použijete pravidla na doménové třídy a vztahy.

     `FireTime`Je obvykle `TopLevelCommit` . Tím se zajistí, že se pravidlo spustí až po provedení všech primárních změn transakce. Alternativy jsou vložené, takže pravidlo se po změně spustí brzo; a LocalCommit, který spouští pravidlo na konci aktuální transakce (což nemusí být nejvzdálenější). Můžete také nastavit prioritu pravidla, aby ovlivnilo jeho pořadí ve frontě, ale toto je nespolehlivější způsob dosažení potřebného výsledku.

- Jako typ subjektu můžete zadat abstraktní třídu.

- Pravidlo se vztahuje na všechny instance třídy Subject.

- Výchozí hodnota pro `FireTime` je TimeToFire. TopLevelCommit. To způsobí, že se pravidlo spustí při potvrzení vnější transakce. Alternativou je TimeToFire. inline. To způsobí, že se pravidlo provede brzo po aktivaci události.

### <a name="to-register-the-rule"></a>Postup při registraci pravidla

- Přidejte třídu pravidel do seznamu typů vrácených `GetCustomDomainModelTypes` v doménovém modelu:

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

- Pokud si nejste jisti názvem vaší třídy doménového modelu, podívejte se do souboru **Dsl\GeneratedCode\DomainModel.cs**

- Tento kód napište do vlastního souboru kódu v projektu DSL.

### <a name="to-write-the-code-of-the-rule"></a>Zápis kódu pravidla

- Odvodit třídu pravidla z jedné z následujících základních tříd:

  | Základní třída | Trigger |
  |-|-|
  | <xref:Microsoft.VisualStudio.Modeling.AddRule> | Přidá se element, odkaz nebo tvar.<br /><br /> Tuto kombinaci použijte k detekci nových vztahů kromě nových prvků. |
  | <xref:Microsoft.VisualStudio.Modeling.ChangeRule> | Hodnota vlastnosti domény se změnila. Argument metody poskytuje staré a nové hodnoty.<br /><br /> U obrazců je toto pravidlo aktivováno, když se `AbsoluteBounds` změní integrovaná vlastnost, pokud je obrazec přesunut.<br /><br /> V mnoha případech je pohodlnější přepsat `OnValueChanged` nebo `OnValueChanging` v obslužné rutině vlastnosti. Tyto metody jsou volány bezprostředně před a po změně. Naproti tomu se pravidlo obvykle spouští na konci transakce. Další informace najdete v tématu [obslužné rutiny změny hodnoty vlastnosti domény](../modeling/domain-property-value-change-handlers.md). **Poznámka:**  Toto pravidlo se neaktivuje, když se vytvoří nebo odstraní odkaz. Místo toho napište `AddRule` a `DeleteRule` pro doménový vztah. |
  | <xref:Microsoft.VisualStudio.Modeling.DeletingRule> | Aktivuje se, když se chystá odstranění elementu nebo odkazu. Vlastnost ModelElement. má hodnotu true do konce transakce. |
  | <xref:Microsoft.VisualStudio.Modeling.DeleteRule> | Provede se při odstranění elementu nebo odkazu. Pravidlo je spuštěno po provedení všech ostatních pravidel, včetně DeletingRules. ModelElement. IsDeleted je false a ModelElement. IsDeleted má hodnotu true. Aby bylo možné provést následné zrušení, prvek není ve skutečnosti odebrán z paměti, ale je odebrán z Store. ElementDirectory. |
  | <xref:Microsoft.VisualStudio.Modeling.MoveRule> | Prvek je přesunut z jednoho oddílu úložiště do jiného.<br /><br /> (Všimněte si, že to nesouvisí s grafickým umístěním tvaru.) |
  | <xref:Microsoft.VisualStudio.Modeling.RolePlayerChangeRule> | Toto pravidlo se vztahuje pouze na doménové vztahy. Je aktivována, pokud explicitně přiřadíte prvek modelu ke konci propojení. |
  | <xref:Microsoft.VisualStudio.Modeling.RolePlayerPositionChangeRule> | Aktivováno, když je řazení odkazů na prvek nebo z prvku změněno pomocí metod MoveBefore nebo MoveToIndex na odkazu. |
  | <xref:Microsoft.VisualStudio.Modeling.TransactionBeginningRule> | Provede se při vytvoření transakce. |
  | <xref:Microsoft.VisualStudio.Modeling.TransactionCommittingRule> | Provedeno v případě, že transakce bude potvrzena. |
  | <xref:Microsoft.VisualStudio.Modeling.TransactionRollingBackRule> | Provedeno v případě, že transakce bude vrácena zpět. |

- Každá třída má metodu, kterou přepíšete. Zadejte `override` svou třídu a zjistěte ji. Parametr této metody identifikuje prvek, který se mění.

  Všimněte si následujících bodů pravidel:

1. Sada změn v transakci může aktivovat mnoho pravidel. Pravidla jsou obvykle spouštěna při potvrzení vnější transakce. Jsou spouštěny v nespecifikovaném pořadí.

2. Pravidlo je vždy spuštěno v rámci transakce. Proto není nutné vytvářet novou transakci, aby bylo možné provádět změny.

3. Pravidla nejsou provedena, pokud je transakce vrácena zpět nebo když jsou provedeny operace vrácení zpět nebo opakování. Tyto operace obnoví veškerý obsah úložiště do předchozího stavu. Proto pokud vaše pravidlo změní stav všeho, co je mimo obchod, nemusí v synchronism s obsahem úložiště zůstat. Chcete-li aktualizovat stav mimo úložiště, je lepší používat události. Další informace najdete v tématu [obslužné rutiny událostí rozšiřovat změny mimo model](../modeling/event-handlers-propagate-changes-outside-the-model.md).

4. Některá pravidla se spustí, když je model načten ze souboru. Chcete-li zjistit, zda probíhá načítání nebo ukládání, použijte `store.TransactionManager.CurrentTransaction.IsSerializing` .

5. Pokud kód pravidla vytvoří další aktivační procedury pravidel, budou přidány na konec seznamu pro vypálení a spustí se před dokončením transakce. DeletedRules se spustí po všech ostatních pravidlech. Jedno pravidlo může běžet mnohokrát v transakci, a to jednou při každé změně.

6. Chcete-li předat informace do a z pravidel, můžete ukládat informace v části `TransactionContext` . Toto je pouze slovník, který je udržován během transakce. Je uvolněna v případě, že transakce skončí. Argumenty události v každém pravidle poskytují přístup k ní. Mějte na paměti, že pravidla se nespouštějí v předvídatelném pořadí.

7. Pravidla použijte po zvážení dalších možností. Například pokud chcete aktualizovat vlastnost při změně hodnoty, zvažte použití počítané vlastnosti. Pokud chcete omezit velikost nebo umístění tvaru, použijte `BoundsRule` . Pokud chcete reagovat na změnu v hodnotě vlastnosti, přidejte `OnValueChanged` obslužnou rutinu do vlastnosti. Další informace najdete v tématu [reagování na změny a šíření změn](../modeling/responding-to-and-propagating-changes.md).

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