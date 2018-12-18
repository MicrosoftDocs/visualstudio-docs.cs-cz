---
title: Vnitřní funkce
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: 0e58f84a48104553e5517d24f746769e6f0959e5
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
ms.locfileid: "31920945"
---
# <a name="intrinsic-functions"></a>Vnitřní funkce
Výraz v SAL může být výraz C/C++, za předpokladu, že je výraz, který nemá vedlejší účinky – například ++,--a volání funkce v tomto kontextu jsou vybavené vedlejší účinky.  SAL však poskytuje některé funkce jako objekty a některé vyhrazené znaky, které můžete použít ve výrazech SAL. Tyto jsou označovány jako *vnitřní funkce*.

## <a name="general-purpose"></a>Obecné účely
 Následující poznámky funkce instrinsic poskytují obecné nástroj pro SAL.

|Poznámka|Popis|
|----------------|-----------------|
|`_Curr_`|Synonymum pro objekt, který je aktuálně poznámkou.  Když `_At_` poznámky se používá, `_Curr_` je stejný jako první parametr `_At_`.  Jinak je parametr nebo celý funkce/návratová hodnota, ke kterému je poznámka lexikálně přiřazeno.|
|`_Inexpressible_(expr)`|Nevyjadřuje situaci, kde velikost vyrovnávací paměti je příliš složité pomocí výrazu poznámky – například když je počítaný prohledáním vstupní datové sady a pak počítání vybrané členy.|
|`_Nullterm_length_(param)`|`param` je počet elementů ve vyrovnávací paměti než, ale není včetně zakončením hodnotu null. Lze ji použít na všechny vyrovnávací paměti typu neagregačními, není void.|
|`_Old_(expr)`|Vyhodnocena v předběžnou podmínku, `_Old_` vrátí vstupní hodnotu `expr`.  Při vyhodnocování v po podmínka, vrátí hodnotu `expr` jako jeho by byly vyhodnoceny v předběžnou podmínku.|
|`_Param_(n)`|`n`Tý parametr funkce, počítáno od 1 do `n`, a `n` literálu integrální konstanta. Pokud je parametr, tato anotace je stejný jako při přístupu ke parametr podle názvu. **Poznámka:** `n` mohou odkazovat na poziční parametry, které jsou definované za tři tečky nebo mohou být použity v prototypy funkcí nejsou-li použity názvy.  |
|`return`|C/C++ vyhrazené – klíčové slovo `return` lze použít ve výrazu SAL k označení návratovou hodnotu funkce.  Hodnota je k dispozici pouze ve stavu post; je chyba syntaxe pro použití v předběžné stavu.|

## <a name="string-specific"></a>Konkrétní řetězec
 Následující poznámky vnitřní funkce povolit zpracování řetězce. Všechny čtyři tyto funkce mají stejné účely: vrátit počet elementů typ, který se nachází před zakončením hodnotu null. Rozdíly jsou typů dat v elementech, které jsou uvedené. Všimněte si, že pokud chcete zadat délku ukončené hodnotou null vyrovnávací paměti, která není tvořený znaky, použijte `_Nullterm_length_(param)` poznámky z předchozí části.

|Poznámka|Popis|
|----------------|-----------------|
|`_String_length_(param)`|`param` je počet elementů v řetězec, který se má ale není včetně zakončením hodnotu null. Tato anotace je vyhrazený pro typy řetězec znaků.|
|`strlen(param)`|`param` je počet elementů v řetězec, který se má ale není včetně zakončením hodnotu null. Tato anotace je vyhrazený pro použití na znak polí a vypadá takto: funkce C Runtime [strlen()](/cpp/c-runtime-library/reference/strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l).|
|`wcslen(param)`|`param` je počet elementů v řetězci až do (s výjimkou) zakončením hodnotu null. Tato anotace je vyhrazený pro použití na široká znaková polí a vypadá takto: funkce C Runtime [wcslen()](/cpp/c-runtime-library/reference/strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l).|

## <a name="see-also"></a>Viz také
 [Použití poznámek SAL k snížení míry výskytu závad kódu C/C++](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md) [porozumění SAL](../code-quality/understanding-sal.md) [zadávání poznámek k parametrům funkcí a návratovým hodnotám](../code-quality/annotating-function-parameters-and-return-values.md) [zadávání poznámek k chování funkcí](../code-quality/annotating-function-behavior.md) [Zadávání poznámek ke strukturám a třídám](../code-quality/annotating-structs-and-classes.md) [zadávání poznámek k chování při zamykání](../code-quality/annotating-locking-behavior.md) [určující, kdy a kde se má poznámka použít](../code-quality/specifying-when-and-where-an-annotation-applies.md) [osvědčené postupy a příklady](../code-quality/best-practices-and-examples-sal.md)