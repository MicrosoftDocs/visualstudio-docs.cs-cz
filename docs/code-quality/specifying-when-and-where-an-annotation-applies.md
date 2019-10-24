---
title: Určení, kdy a kde se má poznámka použít
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- _Group_
- _At_
- _When_
- _At_buffer_
ms.assetid: 8e4f4f9c-5dfa-4835-87df-ecd1698fc650
author: mikeblome
ms.author: mblome
manager: markl
ms.workload:
- multiple
ms.openlocfilehash: 8ccf20ab4348a8abed4b052f512477c8b2a8cd0b
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745903"
---
# <a name="specifying-when-and-where-an-annotation-applies"></a>Určení, kdy a kde se má poznámka použít
Pokud je Poznámka podmíněná, může vyžadovat další poznámky k určení tohoto analyzátoru.  Například pokud má funkce proměnnou, která může být buď synchronní, nebo asynchronní, funkce se chová takto: v synchronním případě je vždy úspěšné, ale v asynchronním případě hlásí chybu, pokud nemůže být okamžitě úspěšná. Pokud je funkce volána synchronně, kontrola hodnoty výsledku neposkytne analyzátoru kódu žádnou hodnotu, protože by nebyla vrácena.  Nicméně pokud je funkce volána asynchronně a výsledek funkce není kontrolován, může dojít k závažné chybě. Tento příklad znázorňuje situaci, ve které můžete použít `_When_` anotaci, popsanou dále v tomto článku, a povolit tak kontrolu.

## <a name="structural-annotations"></a>Strukturální poznámky
Chcete-li určit, kdy a kde se poznámky vztahují, použijte následující strukturální poznámky.

|Poznámka|Popis|
|----------------|-----------------|
|`_At_(expr, anno-list)`|`expr` je výraz, který vrací hodnotu lvalue. Poznámky v `anno-list` jsou aplikovány na objekt, který je pojmenován `expr`. Pro každou anotaci v `anno-list` je `expr` interpretována v předběžném stavu, pokud je Poznámka interpretována v předběžné podmínce a v případě, že je Poznámka interpretována v podmínkách post.|
|`_At_buffer_(expr, iter, elem-count, anno-list)`|`expr` je výraz, který vrací hodnotu lvalue. Poznámky v `anno-list` jsou aplikovány na objekt, který je pojmenován `expr`. U každé poznámky v `anno-list` je `expr` interpretována v předběžném stavu, pokud je Poznámka interpretována v předběžné podmínce, a v případě, že je Poznámka interpretována v podmínkách post.<br /><br /> `iter` je název proměnné, která je vymezena pro anotaci (včetně `anno-list`). `iter` má implicitní typ `long`. Identicky pojmenované proměnné v jakémkoli ohraničujícím oboru jsou ze hodnocení skryté.<br /><br /> `elem-count` je výraz, který je vyhodnocen jako celé číslo.|
|`_Group_(anno-list)`|Poznámky v `anno-list` jsou považovány za všechny kvalifikátory, které se vztahují na anotaci skupiny, která je použita u každé poznámky.|
|`_When_(expr, anno-list)`|`expr` je výraz, který lze převést na `bool`. Pokud je hodnota nenulová (`true`), považují se za použitelné poznámky uvedené v `anno-list`.<br /><br /> Ve výchozím nastavení se pro každou anotaci v `anno-list` `expr` interpretuje jako použití vstupních hodnot, pokud je Poznámka podmínkou, a při použití výstupních hodnot, pokud je Poznámka podmínkou. Chcete-li přepsat výchozí hodnotu, můžete použít vnitřní `_Old_` při vyhodnocení podmínky post, aby označovala, že by měly být použity vstupní hodnoty. **Poznámka:**  Jiné poznámky mohou být povoleny jako důsledek použití `_When_`, pokud se jedná o proměnlivou hodnotu (například `*pLength`), protože vyhodnocený výsledek `expr` v předběžné podmínce se může lišit od vyhodnoceného výsledku v podmínkách post.|

## <a name="see-also"></a>Viz také:

- [Použití poznámek SAL k snížení míry výskytu závad kódu C/C++](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)
- [Porozumění SAL](../code-quality/understanding-sal.md)
- [Zadávání poznámek k parametrům funkcí a návratovým hodnotám](../code-quality/annotating-function-parameters-and-return-values.md)
- [Zadávání poznámek k chování funkcí](../code-quality/annotating-function-behavior.md)
- [Zadávání poznámek ke strukturám a třídám](../code-quality/annotating-structs-and-classes.md)
- [Zadávání poznámek o chování při zamykání](../code-quality/annotating-locking-behavior.md)
- [Vnitřní funkce](../code-quality/intrinsic-functions.md)
- [Doporučené postupy a příklady](../code-quality/best-practices-and-examples-sal.md)
