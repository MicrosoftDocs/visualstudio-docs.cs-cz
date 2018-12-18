---
title: Psaní kódu pro úpravu jazyka specifického pro doménu specifického | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language, programming
ms.assetid: a4a17f5b-9c97-4575-b2d1-3182c1896b72
caps.latest.revision: 31
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: affa3db292ed23ca52b0cca810daf5ca70ad0fd1
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49866321"
---
# <a name="writing-code-to-customise-a-domain-specific-language"></a>Zápis kódu pro úpravu jazyka specifického pro doménu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tato část ukazuje, jak použít vlastní kód pro přístup, upravit nebo vytvořit model v jazyka specifického pro doménu.  
  
 Existuje několik kontextech, ve kterých můžete napsat kód, který funguje s DSL:  
  
- **Vlastní příkazy.** Můžete vytvořit příkaz, že uživatelé můžete vyvolat kliknutím pravým tlačítkem myši v diagramu a které můžete měnit model. Další informace najdete v tématu [postupy: přidání příkazu do místní nabídky](../modeling/how-to-add-a-command-to-the-shortcut-menu.md).  
  
- **Ověření.** Můžete napsat kód, který ověřuje, že model je ve správném stavu. Další informace najdete v tématu [ověřování v jazyka specifického pro doménu](../modeling/validation-in-a-domain-specific-language.md).  
  
- **Přepisování výchozího chování.** Můžete upravit mnoho aspektů kód, který je generován z DslDefinition.dsl. Další informace najdete v tématu [přepisování a rozšiřování třídy generované v](../modeling/overriding-and-extending-the-generated-classes.md).  
  
- **Transformace textu.** Můžete napsat textových šablon, které obsahují kód, který má přístup k modelu a vytváří textový soubor, třeba když chcete generovat kód programu. Další informace najdete v tématu [generování kódu z jazyka specifického pro doménu](../modeling/generating-code-from-a-domain-specific-language.md).  
  
- **Další rozšíření sady Visual Studio.** Můžete napsat samostatné rozšíření VSIX, které čtení a úpravy modelů. Další informace najdete v tématu [postupy: otevření modelu ze souboru v kódu programu](../modeling/how-to-open-a-model-from-file-in-program-code.md)  
  
  Instance tříd, které definujete v DslDefinition.dsl uchovávají do datové struktury, volá se, *Store v paměti* (IMS) nebo *Store*. Třídy, které definujete DSL, vždy provést Store jako argument konstruktoru. Pokud například vaše DSL definuje třídu s názvem příkladu:  
  
  `Example element = new Example (theStore);`  
  
  uchování objektů v Store (namísto stejně jako normální objekty) poskytuje několik výhod.  
  
- **Transakce**. Můžete seskupit řadu souvisejících změn do transakce:  
  
   `using (Transaction t = store.TransactionManager.BeginTransaction("updates"))`  
  
   `{`  
  
   `// make several changes to Store elements here`  
  
   `t.Commit();`  
  
   `}`  
  
   Pokud dojde k výjimce během změny, tak, aby konečná Commit() neprovádí, Store se resetuje do předchozího stavu. Díky tomu můžete zajistit, že chyby nenechala modelu v nekonzistentním stavu. Další informace najdete v tématu [navigace a aktualizace modelu v programovém kódu](../modeling/navigating-and-updating-a-model-in-program-code.md).  
  
- **Binární vztahy**. Při definování vztahu mezi dvěma třídami, instance na obou koncích mají vlastnost, která přejde na druhém konci. Dva elementy jsou vždy synchronizované. Například pokud definujete rodičovství vztah s rolí s názvem nadřazené a podřízené položky, můžete napsat:  
  
   `John.Children.Add(Mary)`  
  
   Obě tyto výrazy jsou teď true:  
  
   `John.Children.Contains(Mary)`  
  
   `Mary.Parents.Contains(John)`  
  
   Můžete také dosáhnout stejný účinek pomocí zápisu:  
  
   `Mary.Parents.Add(John)`  
  
   Další informace najdete v tématu [navigace a aktualizace modelu v programovém kódu](../modeling/navigating-and-updating-a-model-in-program-code.md).  
  
- **Pravidla a události**. Můžete definovat pravidla, která se aktivuje vždy, když dojde ke změně zadané. Se používají pravidla, třeba udržovat tvary v diagramu stavu s prvky modelu, které jsou k dispozici. Další informace najdete v tématu [šířící změny a reakce na](../modeling/responding-to-and-propagating-changes.md).  
  
- **Serializace**. Store poskytuje standardní způsob, jak serializovat objekty, které obsahuje do souboru. Můžete přizpůsobit pravidla pro serializaci a deserializaci. Další informace najdete v tématu [přizpůsobení souborového úložiště a serializace XML](../modeling/customizing-file-storage-and-xml-serialization.md).  
  
## <a name="see-also"></a>Viz také  
 [Přizpůsobení a rozšíření jazyka specifického pro doménu](../modeling/customizing-and-extending-a-domain-specific-language.md)



