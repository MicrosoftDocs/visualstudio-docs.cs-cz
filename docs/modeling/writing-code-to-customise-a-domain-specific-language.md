---
title: Přizpůsobení jazyka domény
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, programming
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: f7fd63546f7d85ddbcc7661ac600a56bd340e6ec
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
ms.locfileid: "31965223"
---
# <a name="write-code-to-customize-a-domain-specific-language"></a>Napsat kód pro přizpůsobení jazyka domény

V této části se dozvíte, jak použít vlastní kód pro přístup, upravit nebo vytvořit model v jazyce specifické pro doménu.

Existuje několik kontexty, ve kterých můžete napsat kód, který funguje s DSL:

-   **Vlastní příkazy.** Můžete vytvořit příkaz uživatelů můžete vyvolat kliknutím pravým tlačítkem myši v diagramu, a který můžete upravit modelu. Další informace najdete v tématu [postupy: přidání příkazu do místní nabídky](../modeling/how-to-add-a-command-to-the-shortcut-menu.md).

-   **Ověření.** Můžete napsat kód, který ověřuje, že model je ve správném stavu. Další informace najdete v tématu [ověření v jazyce specifické pro doménu](../modeling/validation-in-a-domain-specific-language.md).

-   **Přepsání výchozího nastavení.** Mnoho aspektů kód, který se generují z DslDefinition.dsl, můžete upravit. Další informace najdete v tématu [přepsání a rozšíření třídy generované](../modeling/overriding-and-extending-the-generated-classes.md).

-   **Transformace textu.** Můžete napsat textové šablony, které obsahovat kód, který přistupuje k modelu a generuje textového souboru, například ke generování kódu programu. Další informace najdete v tématu [generování kódu z jazyka domény](../modeling/generating-code-from-a-domain-specific-language.md).

-   **Další rozšíření sady Visual Studio.** Můžete napsat samostatné VSIX rozšíření, která číst a upravovat modely. Další informace najdete v tématu [postupy: otevření modelu ze souboru v programovém kódu](../modeling/how-to-open-a-model-from-file-in-program-code.md)

Instance třídy, které definujete v DslDefinition.dsl udržovaly v strukturu dat s názvem *úložiště v paměti* (IMS) nebo *úložiště*. Třídy, které definujete DSL, vždy trvat úložiště jako argument konstruktoru. Například pokud vaše DSL definuje třídu s názvem příklad:

`Example element = new Example (theStore);`

uchování objektů v úložišti (namísto stejně jako obyčejnou objekty) poskytuje několik výhod.

-   **Transakce**. Můžete seskupit řadu související změny do transakce:

     `using (Transaction t = store.TransactionManager.BeginTransaction("updates"))`

     `{`

     `// make several changes to Store elements here`

     `t.Commit();`

     `}`

     Pokud dojde k výjimce během změny, tak, aby konečné Commit() neprovádí, úložišti se resetuje do předchozího stavu. Díky tomu můžete zajistit, že chyby nenechávejte modelu v nekonzistentním stavu. Další informace najdete v tématu [navigace a aktualizace modelu v programovém kódu](../modeling/navigating-and-updating-a-model-in-program-code.md).

-   **Binární vztahy**. Při definování vztahu mezi dvěma třídami, instance na obou koncích mají vlastnost, která přejde na druhém konci. Vždy se synchronizují dva elementy end. Například pokud definujete rodičovství vztah s rolí s názvem nadřazené a podřízené položky, můžete napsat:

     `John.Children.Add(Mary)`

     Z těchto výrazů platí obě nyní:

     `John.Children.Contains(Mary)`

     `Mary.Parents.Contains(John)`

     Stejného efektu můžete také dosáhnout vytvořením:

     `Mary.Parents.Add(John)`

     Další informace najdete v tématu [navigace a aktualizace modelu v programovém kódu](../modeling/navigating-and-updating-a-model-in-program-code.md).

-   **Pravidla a události**. Můžete definovat pravidla, které budou spuštěny při každé zadané změně. Pravidla jsou například použít k udržování tvarů diagram stavu pomocí modelu prvky, které budou k dispozici. Další informace najdete v tématu [reakce na a šíření změny](../modeling/responding-to-and-propagating-changes.md).

-   **Serializace**. Úložiště poskytuje standardní způsob, jak serializovat objekty, které obsahuje do souboru. Můžete upravit pravidla pro serializaci a deserializaci. Další informace najdete v tématu [přizpůsobení File Storage a serializace XML](../modeling/customizing-file-storage-and-xml-serialization.md).

## <a name="see-also"></a>Viz také

- [Přizpůsobení a rozšíření jazyka specifického pro doménu](../modeling/customizing-and-extending-a-domain-specific-language.md)