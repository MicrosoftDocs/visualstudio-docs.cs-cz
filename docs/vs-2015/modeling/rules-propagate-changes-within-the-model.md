---
title: Pravidla šířící změny v modelu | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language, programming domain models
- Domain-Specific Language, rules
ms.assetid: 1690a38a-c8f5-4bc6-aab9-015771ec6647
caps.latest.revision: 32
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 265d04306b4747a4e5bc04b879b9635e81ed8102
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49831195"
---
# <a name="rules-propagate-changes-within-the-model"></a>Pravidla šířící změny v modelu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete vytvořit pravidlo úložiště, které rozšíří změnu z jednoho elementu do druhého v produktu Visualization and Modeling SDK (vmsdk následující položky). Když dojde ke změně k libovolnému prvku v Store, jsou naplánovány pravidla má být spuštěna, většinou když nejkrajnější transakce se potvrzeny. Existují různé typy pravidel pro různé druhy událostí, jako je například přidání elementu nebo jejím odstranění. Pravidla můžete připojit na konkrétní typy prvků, tvary nebo diagramů. Mnoho integrovaných funkcí, které jsou definovány pomocí pravidel: například pravidla ujistěte se, že diagramu se aktualizuje při změně modelu. Doménově specifického jazyka můžete přizpůsobit tak, že přidáte vlastní pravidla.  

 Pravidla Store jsou vhodné pro šíření změn v úložišti – to znamená, že se změní na prvky modelu, relace, tvary nebo konektory a jejich domény vlastnosti. Pravidla nelze spustit, když uživatel spustí příkaz zpět nebo znovu. Místo toho správce transakcí zajišťuje, že obsah úložiště jsou obnovena do správného stavu. Pokud chcete změny na prostředky mimo úložiště, použijte Store události. Další informace najdete v tématu [obslužné rutiny rozšíření změny mimo the Model událostí](../modeling/event-handlers-propagate-changes-outside-the-model.md).  

 Předpokládejme například, že chcete určit, že pokaždé, když se uživatel (nebo váš kód) vytvoří nový prvek typu ExampleDomainClass, další prvek jiného typu je vytvořen v jiné části modelu. Může zapisovat AddRule a přidružte jej k ExampleDomainClass. Měli byste napsat kód v pravidlo můžete vytvořit další prvek.  

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

    // Code here propagates change as required – for example:  
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
>  Kód pravidlo by měl změnit stav pouze prvky uvnitř Store; To znamená pravidlo by měl změnit pouze prvky modelu, relace, tvary, konektory, diagramů nebo jejich vlastností. Pokud chcete změny na prostředky mimo úložišti, definujte Store události. Další informace najdete v tématu [obslužné rutiny rozšíření změny mimo the Model událostí](../modeling/event-handlers-propagate-changes-outside-the-model.md)  

### <a name="to-define-a-rule"></a>Chcete definovat pravidlo  

1. Definovat pravidlo, protože třídy s předponou `RuleOn` atribut. Atribut přidruží pravidlo doménovými třídami, relací nebo elementů diagramu. Pravidla se použijí na každou instanci této třídy, které mohou být abstraktní.  

2. Registrovat pravidla tak, že přidáte do sady vrácené `GetCustomDomainModelTypes()` v třídě modelu domény.  

3. Třídy pravidla odvození od některého z abstraktní třídy pravidla a napsat kód metoda spuštění.  

   Následující části popisují postup podrobněji.  

### <a name="to-define-a-rule-on-a-domain-class"></a>Chcete-li definovat pravidla na doménovou třídu  

-   V souboru vlastního kódu, definovat třídu a prefix <xref:Microsoft.VisualStudio.Modeling.RuleOnAttribute> atribut:  

    ```  
    [RuleOn(typeof(ExampleElement),   
         // Usual value – but required, because it is not the default:  
         FireTime = TimeToFire.TopLevelCommit)]   
    class MyRule ...  

    ```  

-   Typ subjektu v prvním parametru může být doménovou třídou, doménového vztahu, tvaru, konektoru nebo diagramu. Obvykle použít pravidla pro doménovými třídami a vztahy.  

     `FireTime` Je obvykle `TopLevelCommit`. Tím se zajistí, že se provede pouze po provedení všech primární změny transakce. Alternativ jsou vložené, která spustí pravidlo brzy po provedení změny; a LocalCommit, která spustí pravidlo na konci aktuální transakce (která nemusí být nejkrajnější). Můžete také nastavit prioritu pravidlo, které ovlivňují pořadí řazení ve frontě, ale jedná o metodu nespolehlivé dosažení výsledků podle svých požadavků.  

-   Abstraktní třídy můžete zadat jako typy předmětů.  

-   Toto pravidlo se vztahuje na všechny instance třídy předmět.  

-   Výchozí hodnota pro `FireTime` je TimeToFire.TopLevelCommit. To způsobí, že pravidlo se spustí při nejkrajnější transakce se potvrzeny. Alternativou je TimeToFire.Inline. To způsobí, že pravidlo se spustí ihned po aktivační událost.  

### <a name="to-register-the-rule"></a>Pravidla registrace  

-   Přidat třídu pravidlo do seznamu typů vrácených `GetCustomDomainModelTypes` v doménovém modelu:  

    ```  
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

-   Pokud si nejste jisti názvem třídy modelu domény, vyhledejte v souboru **Dsl\GeneratedCode\DomainModel.cs**  

-   Tento kód napište vlastní kód souboru ve vašem projektu DSL.  

### <a name="to-write-the-code-of-the-rule"></a>Psaní kódu pravidla  

- Třída pravidla odvození od některého z následujících základních tříd:  


  |                             Základní třída                              |                                                                                                                                                                                                                                                                                                                                                                              Aktivační událost                                                                                                                                                                                                                                                                                                                                                                              |
  |---------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
  |           <xref:Microsoft.VisualStudio.Modeling.AddRule>            |                                                                                                                                                                                                                                                                                                                        Přidání elementu, odkaz nebo tvar.<br /><br /> To lze použijte k detekci nové relace, kromě nových elementů.                                                                                                                                                                                                                                                                                                                        |
  |          <xref:Microsoft.VisualStudio.Modeling.ChangeRule>          | Hodnota vlastnosti domény se změní. Argument metody obsahuje staré a nové hodnoty.<br /><br /> Obrazce, toto pravidlo aktivováno, když předdefinované `AbsoluteBounds` změny vlastností, pokud se přesune na obrazec.<br /><br /> V mnoha případech je snazší přepsat `OnValueChanged` nebo `OnValueChanging` v obslužné rutině vlastnost. Tyto metody jsou volány bezprostředně před a po provedení změny. Naopak se pravidlo spustí obvykle na konci transakce. Další informace najdete v tématu [obslužné rutiny změny hodnoty vlastnosti domény](../modeling/domain-property-value-change-handlers.md). **Poznámka:** toto pravidlo není aktivováno, když vytvoříte nebo odstraníte odkaz. Místo toho zápis `AddRule` a `DeleteRule` pro doménový vztah. |
  |         <xref:Microsoft.VisualStudio.Modeling.DeletingRule>         |                                                                                                                                                                                                                                                                                                             Aktivováno, když elementu nebo propojení je odstranit. Vlastnost ModelElement.IsDeleting platí až do konce transakce.                                                                                                                                                                                                                                                                                                              |
  |          <xref:Microsoft.VisualStudio.Modeling.DeleteRule>          |                                                                                                                                                                                                       Provádí při elementu nebo propojení se odstranil. Toto pravidlo se spustí po byly provedeny všechny ostatní pravidla, včetně DeletingRules. ModelElement.IsDeleting má hodnotu false a ModelElement.IsDeleted má hodnotu true. Povolit pro následné vrácení zpět, se ve skutečnosti neodebere element z paměti, ale je odebrán z Store.ElementDirectory.                                                                                                                                                                                                       |
  |           <xref:Microsoft.VisualStudio.Modeling.MoveRule>           |                                                                                                                                                                                                                                                                                                           Element je přesouvat z jednoho úložiště pro oddíl do druhého.<br /><br /> (Všimněte si, že to se nevztahuje na pozici grafické obrazce.)                                                                                                                                                                                                                                                                                                            |
  |     <xref:Microsoft.VisualStudio.Modeling.RolePlayerChangeRule>     |                                                                                                                                                                                                                                                                                                                 Toto pravidlo platí pouze pro vztahy domén. Se aktivuje, pokud přiřadíte prvek modelu explicitně na oba konce tohoto odkazu.                                                                                                                                                                                                                                                                                                                 |
  | <xref:Microsoft.VisualStudio.Modeling.RolePlayerPositionChangeRule> |                                                                                                                                                                                                                                                                                                                   Aktivováno, když odkazů do nebo z elementu není řazení změněno pomocí metody MoveBefore nebo MoveToIndex na odkaz.                                                                                                                                                                                                                                                                                                                    |
  |   <xref:Microsoft.VisualStudio.Modeling.TransactionBeginningRule>   |                                                                                                                                                                                                                                                                                                                                                              Spustit při transakci.                                                                                                                                                                                                                                                                                                                                                              |
  |  <xref:Microsoft.VisualStudio.Modeling.TransactionCommittingRule>   |                                                                                                                                                                                                                                                                                                                                                      Spustit transakci blížící se odešlou.                                                                                                                                                                                                                                                                                                                                                      |
  |  <xref:Microsoft.VisualStudio.Modeling.TransactionRollingBackRule>  |                                                                                                                                                                                                                                                                                                                                                     Spustit, když transakce je vrácena zpět.                                                                                                                                                                                                                                                                                                                                                     |


- Každá třída má metodu, která je přepsat. Typ `override` ve své třídě jej zjistit. Parametr této metody určuje prvek, který mění.  

  Všimněte si následujících o pravidlech:  

1.  Sadu změn v rámci transakce, které může aktivovat více pravidel. Pravidla jsou obvykle spouštěny, když nejkrajnější transakce se potvrzeny. Jsou prováděna v nespecifikovaném pořadí.  

2.  Pravidlo je vždy spuštěn v transakci. Proto není muset vytvořit novou transakci provést změny.  

3.  Pravidla nejsou provedeny, když transakce je vrácena zpět, nebo když se provádí operace vrácení zpět nebo znovu. Tyto operace obnovit veškerý obsah Store do předchozího stavu. Proto pokud vaše pravidlo změní stav něco mimo Store, se nemusí mějte synchronism s Store obsahu. Pokud chcete aktualizovat stav mimo Store, je vhodnější použít události. Další informace najdete v tématu [obslužné rutiny rozšíření změny mimo the Model událostí](../modeling/event-handlers-propagate-changes-outside-the-model.md).  

4.  Některá pravidla jsou spouštěny, když je model načtenou ze souboru. Chcete-li zjistit, jestli je v průběhu načítání nebo ukládání, použijte `store.TransactionManager.CurrentTransaction.IsSerializing`.  

5.  Pokud vaše pravidlo vytvoří další pravidlo aktivuje, se přidá na konec seznamu jeho spuštění a budou spuštěny před dokončením transakce. DeletedRules jsou spuštěny za všemi ostatními pravidly. Jedno pravidlo můžete spustit v mnoha případech v transakci, jednou pro každou změnu.  

6.  K předávání informací do a z pravidel, můžete ukládat informace `TransactionContext`. Toto je jenom slovník, který je udržován během transakce. To je uvolněna při transakci skončí. Argumenty události z každé pravidlo poskytnutí přístupu k němu. Mějte na paměti, že pravidla nejsou provedeny v předvídatelné pořadí.  

7.  Použijte pravidla po zvážení další možnosti. Pokud chcete aktualizovat při změně hodnoty vlastnosti, představte si třeba použití počítané vlastnosti. Pokud chcete omezit velikost nebo umístění obrazce, použijte `BoundsRule`. Pokud chcete reagovat na změnu v hodnotě vlastnosti, přidejte `OnValueChanged` obslužné rutiny vlastnosti. Další informace najdete v tématu [šířící změny a reakce na](../modeling/responding-to-and-propagating-changes.md).  

## <a name="example"></a>Příklad  
 Následující příklad aktualizuje vlastnosti při vytváření instance vztah domény propojení dvou prvků. Toto pravidlo se aktivuje, nikoli pouze v případě, že uživatel vytvoří odkaz v diagramu, ale i pokud programového kódu vytvoří odkaz.  

 K otestování v tomto příkladu, vytvoření DSL pomocí šablony toku úkolů řešení a vložte následující kód do souboru v projektu Dsl. Sestavení a spuštění řešení a otevřít ukázkový soubor v ladění projektu. Odkaz na komentář nakreslete mezi obrazec komentáře a prvku toku. V komentáři, změní se na sestavu na nejnovější elementu, který umožňuje připojení.  

 V praxi měli byste obvykle napsat DeletRule pro každý AddRule.  

```  
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
 [Obslužné rutiny události šířící změny mimo Model](../modeling/event-handlers-propagate-changes-outside-the-model.md)   
 [Umístění a velikost obrazce omezení BoundsRules](../modeling/boundsrules-constrain-shape-location-and-size.md)



