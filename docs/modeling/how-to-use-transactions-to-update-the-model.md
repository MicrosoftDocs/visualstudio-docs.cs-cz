---
title: 'Postupy: Používání transakcí k aktualizaci modelu'
ms.date: 11/04/2016
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 33d6c249845c72e25b7201bed5e640ff523c5d81
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75594601"
---
# <a name="how-to-use-transactions-to-update-the-model"></a>Postupy: Používání transakcí k aktualizaci modelu
Transakce zajistí, že se změny provedené v úložišti považují za skupinu. Změny, které jsou seskupeny, lze potvrdit nebo vrátit zpět jako jednu jednotku.

 Pokaždé, když kód programu upraví, přidá nebo odstraní libovolný prvek v úložišti v sadě Visual Studio vizualizace and modeling SDK, musí to dělat v rámci transakce. Pokud dojde ke změně, musí být k úložišti přidružena aktivní instance <xref:Microsoft.VisualStudio.Modeling.Transaction>. To platí pro všechny prvky modelu, vztahy, obrazce, diagramy a jejich vlastnosti.

 Mechanismus transakce pomáhá vyhnout se nekonzistenci stavů. Pokud během transakce dojde k chybě, všechny změny se vrátí zpět. Pokud uživatel provede příkaz k vrácení zpět, každá poslední transakce je považována za jeden krok. Uživatel nemůže vrátit části Nedávné změny, pokud je explicitně neumístíte do samostatných transakcí.

## <a name="opening-a-transaction"></a>Otevření transakce
 Nejpohodlnější způsob správy transakce je příkaz `using` uzavřený v příkazu `try...catch`:

```csharp
Store store; ...
try
{
  using (Transaction transaction =
    store.TransactionManager.BeginTransaction("update model"))
    // Outermost transaction must always have a name.
  {
    // Make several changes in Store:
    Person p = new Person(store);
    p.FamilyTreeModel = familyTree;
    p.Name = "Edward VI";
    // end of changes to Store

    transaction.Commit(); // Don't forget this!
  } // transaction disposed here
}
catch (Exception ex)
{
  // If an exception occurs, the Store will be
  // rolled back to its previous state.
}
```

 Pokud dojde k výjimce, která brání závěrečnému `Commit()` v průběhu změn, uloží se do předchozího stavu. To vám pomůže zajistit, že chyby nenechávají model v nekonzistentním stavu.

 V rámci jedné transakce můžete provést libovolný počet změn. Můžete otevřít nové transakce v aktivní transakci. Vnořené transakce musí být potvrzeny nebo vráceny zpět před ukončením obsahující transakce. Další informace naleznete v příkladu pro vlastnost <xref:Microsoft.VisualStudio.Modeling.Transaction.TransactionDepth%2A>.

 Chcete-li provést trvalé změny, měli byste `Commit` transakce před jejím vyřazením. Pokud dojde k výjimce, která není zachycena v rámci transakce, úložiště bude před změnami obnoveno do svého stavu.

## <a name="rolling-back-a-transaction"></a>Vrácení transakce zpět
 Aby se zajistilo, že obchod zůstane v nebo se vrátí do stavu před transakcí, můžete použít některý z těchto taktiku:

1. Vyvolejte výjimku, která není zachycena v rámci oboru transakce.

2. Explicitně vraťte transakci zpět:

    ```csharp
    this.Store.TransactionManager.CurrentTransaction.Rollback();
    ```

## <a name="transactions-do-not-affect-non-store-objects"></a>Transakce neovlivňují objekty, které nejsou v úložišti.
 Transakce řídí pouze stav úložiště. Nemůžou vrátit zpět částečné změny provedené u externích položek, jako jsou soubory, databáze nebo objekty, které jste deklarovali s běžnými typy mimo definici DSL.

 Pokud by výjimka mohla opustit takovou změnu, která je nekonzistentní s úložištěm, měli byste se vypořádat s touto možností v obslužné rutině výjimky. Jedním ze způsobů, jak zajistit, aby externí prostředky zůstaly synchronizované s objekty úložiště, je spojit každý externí objekt s elementem in-Store pomocí obslužných rutin událostí. Další informace najdete v tématu [obslužné rutiny událostí rozšiřovat změny mimo model](../modeling/event-handlers-propagate-changes-outside-the-model.md).

## <a name="rules-fire-at-the-end-of-a-transaction"></a>Pravidla se aktivují na konci transakce.
 Na konci transakce před uvolněním transakce jsou vyvolána pravidla připojená k elementům ve Storu. Každé pravidlo je metoda, která je použita na prvek modelu, který se změnil. Například existují pravidla "opravit", která aktualizují stav tvaru při změně jeho elementu modelu a který vytvoří tvar při vytvoření prvku modelu. Neexistuje žádný konkrétní způsob vypálení. Změna vytvořená pravidlem může aktivovat jiné pravidlo.

 Můžete definovat vlastní pravidla. Další informace o pravidlech najdete v tématu věnovaném [reagování na změny a šíření změn](../modeling/responding-to-and-propagating-changes.md).

 Pravidla se neaktivují po příkazu zpět, znovu nebo vrácení zpět.

## <a name="transaction-context"></a>Kontext transakce
 Každá transakce má slovník, ve kterém můžete ukládat libovolné informace, které chcete:

 `store.TransactionManager`

 `.CurrentTransaction.TopLevelTransaction`

 `.Context.Add(aKey, aValue);`

 To je zvlášť užitečné pro přenos informací mezi pravidly.

## <a name="transaction-state"></a>Stav transakce
 V některých případech je třeba zabránit rozšiřování změny, pokud je změna způsobena zrušením nebo opakováním transakce. K tomu může dojít například při psaní obslužné rutiny hodnoty vlastnosti, která může aktualizovat jinou hodnotu v úložišti. Vzhledem k tomu, že operace vrácení zpět obnoví všechny hodnoty v úložišti do jejich předchozích stavů, není nutné počítat aktualizované hodnoty. Použít tento kód:

```csharp
if (!this.Store.InUndoRedoOrRollback) {...}
```

 Pravidla se můžou aktivovat při počátečním načtení úložiště ze souboru. Abyste se vyhnuli reakci na tyto změny, použijte:

```csharp
if (!this.Store.InSerializationTransaction) {...}
```
