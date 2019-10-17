---
title: Vnitřní funkce
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- _String_length_
- _Param_
- _Curr_
- _Old_
- _Nullterm_length_
- _Inexpressible_
ms.assetid: adf29f8c-89fd-4a5e-9804-35ac83e1c457
author: mikeblome
ms.author: mblome
manager: markl
ms.workload:
- multiple
ms.openlocfilehash: b9236a5135d1339f46aeb6f2dd1a11658adf01c2
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72445702"
---
# <a name="intrinsic-functions"></a>Vnitřní funkce
Výraz v SAL může být výraz C/C++ , pokud se jedná o výraz, který nemá vedlejší účinky, například + +,--, a volání funkcí mají v tomto kontextu vedlejší účinky.  SAL však poskytuje některé objekty podobné funkcím a některé vyhrazené symboly, které lze použít ve výrazech SAL. Ty jsou označovány jako *vnitřní funkce*.

## <a name="general-purpose"></a>Pro obecné účely
Následující poznámky k funkcím instrinsic poskytují obecný nástroj pro SAL.

|Poznámka|Popis|
|----------------|-----------------|
|`_Curr_`|Synonymum pro objekt, který je v současné době opatřen poznámkami.  Pokud se používá anotace `_At_`, `_Curr_` je stejný jako první parametr pro `_At_`.  V opačném případě se jedná o parametr nebo o celou funkci nebo návratovou hodnotu, se kterou je Poznámka lexikální.|
|`_Inexpressible_(expr)`|Vyjadřuje situaci, kdy velikost vyrovnávací paměti je příliš složitá, aby byla reprezentována pomocí výrazu poznámky, například když je vypočítána kontrolou vstupní datové sady a následným vypočítáním vybraných členů.|
|`_Nullterm_length_(param)`|`param` je počet prvků ve vyrovnávací paměti až do nevčetně ukončovacího znaku null. Dá se použít na jakoukoli vyrovnávací paměť neagregovaného typu, který není typu void.|
|`_Old_(expr)`|Pokud je vyhodnocena v předběžné podmínce, `_Old_` vrátí vstupní hodnotu `expr`.  Když se vyhodnotí v rámci podmínky post, vrátí hodnotu `expr`, protože by byla vyhodnocena v předběžné podmínce.|
|`_Param_(n)`|Parametr `n`th funkce, který se počítá z 1 na `n` a `n` je celočíselná konstanta literálu. Pokud je parametr pojmenován, je tato poznámka shodná s přístupem k parametru podle názvu. **Poznámka:**  `n` se může odkazovat na poziční parametry, které jsou definovány třemi tečkami, nebo mohou být použity v prototypech funkce, kde se názvy nepoužívají.|
|`return`|Klíčové slovo CC++ /rezervované `return` lze použít ve výrazu SAL k označení návratové hodnoty funkce.  Hodnota je k dispozici pouze ve stavu post; Jedná se o chybu syntaxe, která se má použít v předběžném stavu.|

## <a name="string-specific"></a>Specifické pro řetězec
Následující poznámky vnitřní funkce umožňují manipulaci s řetězci. Všechny čtyři tyto funkce mají stejný účel: k vrácení počtu prvků typu, který se nachází před prázdným znakem null. Rozdíly jsou typy dat v prvcích, na které se odkazuje. Všimněte si, že pokud chcete zadat délku vyrovnávací paměti zakončené hodnotou null, která není složena ze znaků, použijte anotaci `_Nullterm_length_(param)` z předchozí části.

|Poznámka|Popis|
|----------------|-----------------|
|`_String_length_(param)`|`param` je počet prvků v řetězci až do, ale ne včetně ukončovacího znaku null. Tato poznámka je vyhrazena pro typy řetězcových znaků.|
|`strlen(param)`|`param` je počet prvků v řetězci až do, ale ne včetně ukončovacího znaku null. Tato poznámka je vyhrazena pro použití v polích znaků a podobá se běhové funkci jazyka C [strlen ()](/cpp/c-runtime-library/reference/strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l).|
|`wcslen(param)`|`param` je počet prvků v řetězci až do (ale ne včetně) ukončovacího znaku null. Tato poznámka je vyhrazena pro použití v různých polích znaků a podobá se běhové funkci jazyka C [wcslen ()](/cpp/c-runtime-library/reference/strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l).|

## <a name="see-also"></a>Viz také

- [Použití poznámek SAL k snížení míry výskytu závad kódu C/C++](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)
- [Porozumění SAL](../code-quality/understanding-sal.md)
- [Zadávání poznámek k parametrům funkcí a návratovým hodnotám](../code-quality/annotating-function-parameters-and-return-values.md)
- [Zadávání poznámek k chování funkcí](../code-quality/annotating-function-behavior.md)
- [Zadávání poznámek ke strukturám a třídám](../code-quality/annotating-structs-and-classes.md)
- [Zadávání poznámek o chování při zamykání](../code-quality/annotating-locking-behavior.md)
- [Určení, kdy a kde se má poznámka použít](../code-quality/specifying-when-and-where-an-annotation-applies.md)
- [Doporučené postupy a příklady](../code-quality/best-practices-and-examples-sal.md)
