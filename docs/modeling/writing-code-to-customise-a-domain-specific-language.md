---
title: Přizpůsobení jazyka specifického pro doménu
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, programming
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3954f271d4bcdc222841bbcb435cdadf115ac263
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72748128"
---
# <a name="write-code-to-customize-a-domain-specific-language"></a>Zápis kódu pro úpravu jazyka specifického pro doménu

V této části se dozvíte, jak používat vlastní kód pro přístup, úpravy nebo vytvoření modelu v jazyce specifickém pro doménu.

Existuje několik kontextů, ve kterých můžete napsat kód, který funguje s DSL:

- **Vlastní příkazy.** Můžete vytvořit příkaz, který mohou uživatelé vyvolat tak, že kliknete pravým tlačítkem myši na diagram a můžete model upravit. Další informace najdete v tématu [Postup: Přidání příkazu do místní nabídky](../modeling/how-to-add-a-command-to-the-shortcut-menu.md).

- **Export.** Můžete napsat kód, který ověří, že je model ve správném stavu. Další informace najdete v tématu [ověření v jazyce specifickém pro doménu](../modeling/validation-in-a-domain-specific-language.md).

- **Přepsání výchozího chování.** Můžete upravit mnoho aspektů kódu, které jsou generovány z DslDefinition. DSL. Další informace naleznete v tématu [přepsání a rozšíření vygenerovaných tříd](../modeling/overriding-and-extending-the-generated-classes.md).

- **Transformace textu** Můžete napsat šablony textu, které obsahují kód, který přistupuje k modelu a generuje textový soubor, například pro generování kódu programu. Další informace najdete v tématu [generování kódu z jazyka specifického pro doménu](../modeling/generating-code-from-a-domain-specific-language.md).

- **Další rozšíření sady Visual Studio.** Můžete napsat samostatná rozšíření VSIX, která čtou a upravují modely. Další informace najdete v tématu [Postup: otevření modelu ze souboru v kódu programu.](../modeling/how-to-open-a-model-from-file-in-program-code.md)

Instance tříd, které definujete v DslDefinition. DSL, jsou uchovávány v datové struktuře označované jako *úložiště pro ukládání do paměti* (IMS) nebo v *úložišti*. Třídy, které definujete v DSL, vždy přebírají úložiště jako argument konstruktoru. Například pokud vaše DSL definuje třídu s názvem příklad:

`Example element = new Example (theStore);`

udržování objektů v úložišti (místo stejně jako běžné objekty) poskytuje několik výhod.

- **Transakce**. Řadu souvisejících změn můžete seskupit do transakce:

     `using (Transaction t = store.TransactionManager.BeginTransaction("updates"))`

     `{`

     `// make several changes to Store elements here`

     `t.Commit();`

     `}`

     Pokud dojde k výjimce během změn, takže se neprovede poslední potvrzení (), uloží se úložiště do předchozího stavu. To vám pomůže zajistit, že chyby nenechávají model v nekonzistentním stavu. Další informace naleznete v tématu [navigace a aktualizace modelu v kódu programu](../modeling/navigating-and-updating-a-model-in-program-code.md).

- **Binární relace**. Definujete-li relaci mezi dvěma třídami, instance na obou koncích mají vlastnost, která přechází na druhý element end. Oba konce jsou vždy synchronizovány. Například pokud definujete relaci parenthood s rolemi s názvem nadřazených a podřízených, můžete napsat:

     `John.Children.Add(Mary)`

     Teď jsou splněné oba následující výrazy:

     `John.Children.Contains(Mary)`

     `Mary.Parents.Contains(John)`

     Stejný efekt můžete dosáhnout i tak, že napíšete:

     `Mary.Parents.Add(John)`

     Další informace naleznete v tématu [navigace a aktualizace modelu v kódu programu](../modeling/navigating-and-updating-a-model-in-program-code.md).

- **Pravidla a události**. Můžete definovat pravidla, která se aktivují při každém provedení zadaných změn. Pravidla se používají například k udržení aktuálního stavu obrazců v diagramu s prvky modelu, které jsou k dispozici. Další informace najdete v tématu [reagování na změny a šíření změn](../modeling/responding-to-and-propagating-changes.md).

- **Serializace**. Úložiště poskytuje standardní způsob, jak serializovat objekty, které obsahuje, do souboru. Můžete přizpůsobit pravidla pro serializaci a deserializaci. Další informace naleznete v tématu [přizpůsobení File Storage a serializace XML](../modeling/customizing-file-storage-and-xml-serialization.md).

## <a name="see-also"></a>Viz také:

- [Přizpůsobení a rozšíření jazyka specifického pro doménu](../modeling/customizing-and-extending-a-domain-specific-language.md)