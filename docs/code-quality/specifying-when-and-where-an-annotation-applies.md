---
title: Určení, kdy a kde se má poznámka použít
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- _Group_
- _At_
- _When_
- _At_buffer_
ms.assetid: 8e4f4f9c-5dfa-4835-87df-ecd1698fc650
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: 9d99ebce3adc27039763e11ed4882a20199e8469
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
ms.locfileid: "31920612"
---
# <a name="specifying-when-and-where-an-annotation-applies"></a>Určení, kdy a kde se má poznámka použít
Po podmíněného poznámky může požadovat dalších poznámek určíte, že do analyzátoru.  Například pokud má proměnná, která může být synchronní nebo asynchronní funkce, funkce chová následovně: V případě, že synchronní vždy nakonec operace proběhne úspěšně, ale v případě, že asynchronní ho nahlásí chybu, pokud nelze okamžitě úspěšné. Když je tato funkce volána synchronně, kontrolou hodnoty výsledek poskytuje žádnou hodnotu pro analyzátor kódu, protože nebude mít vrátil.  Když je tato funkce volána asynchronně a výsledek funkce není zaškrtnuto, mohlo dojít k závažné chybě. Tento příklad znázorňuje situaci, ve kterém můžete použít `_When_` poznámky – popsané dále v tomto článku – Povolení kontroly.

## <a name="structural-annotations"></a>Strukturální poznámky
 Chcete-li řídit, kdy a kde poznámky použít, použijte následující strukturální poznámky.

|Poznámka|Popis|
|----------------|-----------------|
|`_At_(expr, anno-list)`|`expr` je výraz, který poskytne lvalue. Poznámky v `anno-list` jsou použity pro objekt, který je pojmenován podle `expr`. Pro každý poznámky v `anno-list`, `expr` interpretována v předběžné podmínky, pokud anotace interpretována v předběžné podmínky a v po podmínku Pokud anotace interpretována v po stavu.|
|`_At_buffer_(expr, iter, elem-count, anno-list)`|`expr` je výraz, který poskytne lvalue. Poznámky v `anno-list` jsou použity pro objekt, který je pojmenován podle `expr`. Pro každý poznámky v `anno-list`, `expr` interpretována v předběžné podmínky, pokud anotace interpretována v předběžnou podmínku, a v po podmínku Pokud anotace interpretována v po stavu.<br /><br /> `iter` je název proměnné, která je omezená na anotace (inclusive z `anno-list`). `iter` má implicitní typ `long`. Stejně jako s názvem proměnné v jakékoli vymezeném oboru jsou skryta vyhodnocení.<br /><br /> `elem-count` je výraz, který se vyhodnotí na celé číslo.|
|`_Group_(anno-list)`|Poznámky v `anno-list` jsou zvažovány všechny mít žádné kvalifikátor, která platí pro poznámky skupiny, který se použije pro každý poznámky.|
|`_When_(expr, anno-list)`|`expr` je výraz, který lze převést na `bool`. Když je nulová (`true`), poznámky, které jsou určené v `anno-list` jsou považovány za použít.<br /><br /> Ve výchozím nastavení pro každou poznámky v `anno-list`, `expr` interpretována jako pomocí vstupní hodnoty, pokud je poznámka předběžné podmínky a anotace, protože pomocí hodnot výstupu, pokud je po podmínku. Chcete-li přepsat výchozí nastavení, můžete použít `_Old_` vnitřní při hodnocení po podmínku, která označuje, že vstupní hodnoty má být použita. **Poznámka:** různých poznámek může povolit v důsledku použití `_When_` Pokud hodnotu měnitelný – například `*pLength`– je zahrnuta, protože vyhodnocený výsledek `expr` v předběžnou se můžou lišit od jeho vyhodnotí Výsledkem po podmínku.|

## <a name="see-also"></a>Viz také
 [Použití poznámek SAL k snížení míry výskytu závad kódu C/C++](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md) [porozumění SAL](../code-quality/understanding-sal.md) [zadávání poznámek k parametrům funkcí a návratovým hodnotám](../code-quality/annotating-function-parameters-and-return-values.md) [zadávání poznámek k chování funkcí](../code-quality/annotating-function-behavior.md) [Zadávání poznámek ke strukturám a třídám](../code-quality/annotating-structs-and-classes.md) [zadávání poznámek k chování při zamykání](../code-quality/annotating-locking-behavior.md) [vnitřní funkce](../code-quality/intrinsic-functions.md) [osvědčené postupy a příklady](../code-quality/best-practices-and-examples-sal.md)