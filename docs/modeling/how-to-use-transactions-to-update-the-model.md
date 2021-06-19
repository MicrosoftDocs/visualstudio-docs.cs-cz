---
title: 'Postupy: Používání transakcí k aktualizaci modelu'
description: Zjistěte, že transakce se ujistěte, že se změny provedené v obchodě zachází jako se skupinou a jak používat transakce k aktualizaci modelu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e91e569573076d1614a9fa946b67f3bda01e6fba
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2021
ms.locfileid: "112390539"
---
# <a name="how-to-use-transactions-to-update-the-model"></a>Postupy: Používání transakcí k aktualizaci modelu
Transakce se ujistěte, že se změny provedené v obchodě budou považovat za skupinu. Změny, které jsou seskupené, je možné posouvaly nebo vrátit zpět jako jednu jednotku.

 Kdykoli kód programu upraví, přidá nebo odstraní jakýkoli prvek v obchodě v sadě Visual Studio Visualization and Modeling SDK, musí to udělat uvnitř transakce. Když dojde ke změně, musí být k Store přidružená <xref:Microsoft.VisualStudio.Modeling.Transaction> aktivní instance . To platí pro všechny prvky modelu, relace, tvary, diagramy a jejich vlastnosti.

 Mechanismus transakcí pomáhá vyhnout nekonzistentní stavy. Pokud během transakce dojde k chybě, všechny změny se vrátí zpět. Pokud uživatel provede příkaz Zpět, každá nedávná transakce se bude považovat za jeden krok. Uživatel nemůže vrátit zpět části nedávné změny, pokud je explicitně nezadáte do samostatných transakcí.

## <a name="opening-a-transaction"></a>Otevření transakce
 Nejpohodlnější způsob správy transakce je s `using` příkazem uzavřeným v `try...catch` příkazu :

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

 Pokud během změn dojde k výjimce, která brání dokončení, store `Commit()` se resetuje do předchozího stavu. To vám pomůže zajistit, že chyby nezanechá model v nekonzistentním stavu.

 V rámci jedné transakce můžete provést libovolný počet změn. Nové transakce můžete otevřít v rámci aktivní transakce. Vnořené transakce musí potvrdit nebo vrátit zpět před ukončením obsahující transakce. Další informace najdete v příkladu vlastnosti <xref:Microsoft.VisualStudio.Modeling.Transaction.TransactionDepth%2A> .

 Pokud chcete, aby vaše změny byly trvalé, měli `Commit` byste transakci před vyřazení. Pokud dojde k výjimce, která není zachycena v rámci transakce, úložiště se resetuje do jeho stavu před změnami.

## <a name="rolling-back-a-transaction"></a>Vrácení transakce zpět
 Pokud chcete zajistit, že Store zůstane ve stavu před transakcí nebo se vrátí do původního stavu, můžete použít některou z těchto taktik:

1. Vyvolání výjimky, která není zachycena v rámci oboru transakce.

2. Explicitně transakci vraťte zpět:

    ```csharp
    this.Store.TransactionManager.CurrentTransaction.Rollback();
    ```

## <a name="transactions-do-not-affect-non-store-objects"></a>Transakce nemají vliv na neukládané objekty.
 Transakce řídí pouze stav úložiště. Nemohou vrátit zpět částečné změny provedené u externích položek, jako jsou soubory, databáze nebo objekty deklarované s běžnými typy mimo definici DSL.

 Pokud může výjimka ponechat takovou změnu nekonzistentní s úložištěm, měli byste tuto možnost řešte v obslužné rutině výjimky. Jedním ze zdrojů, jak zajistit, aby externí prostředky zůstaly synchronizované s objekty Store, je s využitím obslužných rutin událostí smět každý externí objekt s prvkem v obchodě. Další informace najdete v tématu [Obslužné rutiny událostí šíří změny mimo model](../modeling/event-handlers-propagate-changes-outside-the-model.md).

## <a name="rules-fire-at-the-end-of-a-transaction"></a>Pravidla se shodí na konci transakce.
 Na konci transakce před uvolněním transakce jsou aktivována pravidla připojená k prvkům v obchodě. Každé pravidlo je metoda, která se použije na změněný prvek modelu. Existují například pravidla oprav, která aktualizují stav prvku Shape při změně jeho prvku modelu a která vytvoří tvar při vytvoření prvku modelu. Není zadáno pořadí aktivace. Změna provedená pravidlem může zahodí jiné pravidlo.

 Můžete definovat vlastní pravidla. Další informace o pravidlech najdete v tématu [Reakce na změny a šíření změn](../modeling/responding-to-and-propagating-changes.md).

 Pravidla se po vrácení zpět, příkazu pro vrácení zpět neschová.

## <a name="transaction-context"></a>Kontext transakce
 Každá transakce má slovník, ve kterém můžete ukládat libovolné informace:

 `store.TransactionManager`

 `.CurrentTransaction.TopLevelTransaction`

 `.Context.Add(aKey, aValue);`

 To je užitečné hlavně při přenosu informací mezi pravidly.

## <a name="transaction-state"></a>Stav transakce
 V některých případech se musíte vyhnout šíření změny, pokud je změna způsobena vrácením zpět nebo znovu transakcí. K tomu může dojít například v případě, že napíšete obslužnou rutinu hodnoty vlastnosti, která může aktualizovat jinou hodnotu v Store. Vzhledem k tomu, že operace vrácení zpět obnoví všechny hodnoty ve Storu do jejich předchozích stavů, není nutné počítat aktualizované hodnoty. Použijte tento kód:

```csharp
if (!this.Store.InUndoRedoOrRollback) {...}
```

 Pravidla se mohou otevřít, když se úložiště načítá ze souboru. Pokud se chcete vyhnout reagování na tyto změny, použijte:

```csharp
if (!this.Store.InSerializationTransaction) {...}
```
