---
title: 'Postupy: používání transakcí k aktualizaci modelu | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e24436a5-7f97-401b-bc83-20d188d10d5b
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 50f9d491ed52098edb8a8ccd1a7b2f9c8834447e
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49236857"
---
# <a name="how-to-use-transactions-to-update-the-model"></a>Postupy: Používání transakcí k aktualizaci modelu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Transakce, ujistěte se, že změny, které byly provedeny do úložiště jsou považovány za skupinu. Změny, které jsou seskupeny může být potvrzena nebo vrácena zpět jako jednu jednotku.  
  
 Vždy, když váš program kód upraví, přidá nebo odstraní libovolný prvek v Store v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Visualization and Modeling SDK, je nutné provést v transakci. Musí být aktivní instance <xref:Microsoft.VisualStudio.Modeling.Transaction> přidružené Store, když se stane, změny. To platí pro všechny prvky modelu, relace, tvary, diagramy a jejich vlastnosti.  
  
 Transakce mechanismus umožňuje vyhnout se nekonzistentní stavy. Pokud dojde k chybě během transakce, všechny změny se vrátí zpět. Pokud uživatel provede příkaz zpět, je považován za jeden krok každý posledních transakcí. Uživatel se nedá vrátit zpátky části ke změnám, pokud je explicitně umístíte v samostatných transakcích.  
  
## <a name="opening-a-transaction"></a>Otevírání transakce  
 Je nejpohodlnější způsob správy transakce s `using` ohraničeno příkaz `try...catch` – příkaz:  
  
```  
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
  
 Pokud výjimka, která brání finální `Commit()` spadá změn, resetuje Store do předchozího stavu. To vám pomůže zajistit, že chyby nenechala modelu v nekonzistentním stavu.  
  
 Můžete vytvořit libovolný počet změn v jedné transakci. Můžete otevřít nové transakce v aktivní transakci. Vnořené transakce musí potvrzení nebo vrátit zpět před ukončením obsahující transakce. Další informace, podívejte se na příklad pro <xref:Microsoft.VisualStudio.Modeling.Transaction.TransactionDepth%2A> vlastnost.  
  
 Aby byly provedené změny trvalé, měli byste `Commit` transakce před jejich likvidace. Pokud dojde k výjimce, která není zachycena uvnitř transakce, Store obnoví do stavu před změny.  
  
## <a name="rolling-back-a-transaction"></a>Vrácení transakce zpět  
 Aby se zajistilo, že Store zůstává ve nebo se vrátí do stavu před transakce, můžete použít některý z těchto taktika:  
  
1.  Vyvolat výjimku, která není zachycena uvnitř oboru transakce.  
  
2.  Explicitně navrátit transakci:  
  
    ```  
    this.Store.TransactionManager.CurrentTransaction.Rollback();  
    ```  
  
## <a name="transactions-do-not-affect-non-store-objects"></a>Transakce nemají vliv na objekty bez Store  
 Transakce řízení pouze stav Store. Nelze vrátit zpět změny provedené na externí položky, jako jsou soubory, databáze nebo objekty, které je deklarován pomocí běžných typů mimo definici DSL.  
  
 Pokud výjimka může nechat tuto změnu konzistentní s Store, by měl řešit pomocí této možnosti v obslužné rutině výjimky. Jedním ze způsobů, abyste měli jistotu, že externí prostředky budou synchronizovány s objekty Store je spojte každý externí objekt na element v obchodě s použitím obslužné rutiny událostí. Další informace najdete v tématu [obslužné rutiny rozšíření změny mimo the Model událostí](../modeling/event-handlers-propagate-changes-outside-the-model.md).  
  
## <a name="rules-fire-at-the-end-of-a-transaction"></a>Pravidla Fire na konci transakce  
 Na konci transakce jsou předtím, než je transakce vyřazena, aktivuje pravidla připojená k prvkům v úložišti. Každé pravidlo je metoda, která se použije k prvku modelu, který se změnil. Například "Opravit" pravidla, které aktualizují stavu obrazce, když došlo ke změně jeho prvek modelu a obrazec vytvořit při prvku modelu. Neexistuje žádné zadané pořadí. Změny provedené pravidlo můžete vyvolat jiné pravidlo.  
  
 Můžete definovat vlastní pravidla. Další informace o pravidlech najdete v tématu [šířící změny a reakce na](../modeling/responding-to-and-propagating-changes.md).  
  
 Pravidla neaktivuje po vrácení zpět, znovu nebo příkaz vrátit zpět.  
  
## <a name="transaction-context"></a>Kontext transakce  
 Každá transakce obsahuje slovník, ve kterém můžete uložit všechny informace, které chcete, aby:  
  
 `store.TransactionManager`  
  
 `.CurrentTransaction.TopLevelTransaction`  
  
 `.Context.Add(aKey, aValue);`  
  
 To je užitečné zejména pro přenos informací mezi pravidly.  
  
## <a name="transaction-state"></a>Stav transakce  
 V některých případech, které potřebujete, aby se zabránilo šíření změnu, je-li změnu rušení nebo znovu provedení transakce. To může nastat, například když napsat obslužnou rutinu hodnotu vlastnosti, která můžete aktualizovat jinou hodnotu v Store. Vzhledem k tomu, že operaci vrácení zpět obnoví všechny hodnoty Store na předchozím stavům, není nutné pro výpočet aktualizovanými hodnotami. Pomocí tohoto kódu:  
  
```  
if (!this.Store.InUndoRedoOrRollback) {...}  
```  
  
 Pravidla můžete vyvolat při úložišti zpočátku načítání ze souboru. Aby se zabránilo reakce na tyto změny, použijte:  
  
```  
if (!this.Store.InSerializationTransaction) {...}  
  
```



