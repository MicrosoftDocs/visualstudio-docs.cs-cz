---
title: Vnitřní funkce | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- _String_length_
- _Param_
- _Curr_
- _Old_
- _Nullterm_length_
- _Inexpressible_
ms.assetid: adf29f8c-89fd-4a5e-9804-35ac83e1c457
caps.latest.revision: 9
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 7258092b79ca0c10079a986e2a80b34c25660054
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51788105"
---
# <a name="intrinsic-functions"></a>Vnitřní funkce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Výraz v SAL může být výraz jazyka C/C++, za předpokladu, že je výraz, který nemá žádné vedlejší účinky, například ++,--a všechny vedlejší účinky mají v tomto kontextu volání funkce.  Poznámky SAL však poskytuje některé funkce jako objekty a některé rezervované symboly, které můžete použít ve výrazech SAL. Tyto jsou označovány jako *vnitřní funkce*.  
  
## <a name="general-purpose"></a>Obecné účely  
 Následující poznámky instrinsic funkce poskytují obecné nástroje pro poznámky SAL.  
  
|Poznámka|Popis|  
|----------------|-----------------|  
|`_Curr_`|Synonymum pro objekt, který je aktuálně poznámkou.  Když `_At_` poznámky se používá, `_Curr_` je stejný jako první parametr `_At_`.  V opačném případě je parametr nebo celé funkce/návratová hodnota, ke kterému je poznámka lexikálně přidružena.|  
|`_Inexpressible_(expr)`|Vyjadřuje situaci, kde velikost vyrovnávací paměti je příliš složité pomocí výrazu anotace – například když je vypočítán prohledáním vstupní datové sady a potom počítání Vybraní členové.|  
|`_Nullterm_length_(param)`|`param` je počet elementů ve vyrovnávací paměti až, ale nezahrnuje ukončovací znak null. Lze ji použít na všechny vyrovnávací paměti typu neagregované, jiný než void.|  
|`_Old_(expr)`|Když je vyhodnocen v předběžné podmínce, `_Old_` vrátí vstupní hodnoty `expr`.  Když je vyhodnocen v po podmínka, vrátí hodnotu `expr` jako jeho by se vyhodnotily v předběžné podmínce.|  
|`_Param_(n)`|`n`Th parametr funkce, počítáno od 1 do `n`, a `n` je literál integrální konstanta. Pokud je parametr pojmenovaný, tato poznámka se shoduje s přístupem k parametru podle názvu. **Poznámka:** `n` mohou odkazovat na poziční parametry, které jsou definovány pomocí tři teček nebo mohou být použity v prototypech funkcí nejsou-li použity názvy.|  
|`return`|Vyhrazené klíčové slovo jazyka C/C++ `return` lze použít ve výrazu poznámky SAL k označení návratovou hodnotu funkce.  Hodnota je k dispozici pouze ve stavu příspěvku; Jedná se chybu syntaxe jeho použití v předem stavu.|  
  
## <a name="string-specific"></a>Konkrétní řetězec  
 Následující poznámky pro vnitřní funkce povolit manipulaci s řetězci. Všechny čtyři z těchto funkcí slouží stejnému účelu: k vrácení počtu prvků typu, který se nachází před ukončovací znak null. Rozdíly jsou typy dat v prvky, které jsou uvedené. Všimněte si, že pokud chcete zadat délku zakončený hodnotou null vyrovnávací paměti, který není tvořený znaky, použijte `_Nullterm_length_(param)` poznámky z předchozí části.  
  
|Poznámka|Popis|  
|----------------|-----------------|  
|`_String_length_(param)`|`param` je počet elementů v řetězec, který se má ale nezahrnuje ukončovací znak null. Tato poznámka je vyhrazený pro typy řetězce znaků.|  
|`strlen(param)`|`param` je počet elementů v řetězec, který se má ale nezahrnuje ukončovací znak null. Tato poznámka je vyhrazený pro použití na znak pole a podobá se funkci C Runtime [strlen()](http://msdn.microsoft.com/library/16462f2a-1e0f-4eb3-be55-bf1c83f374c2).|  
|`wcslen(param)`|`param` počet prvků v řetězci nahoru (ale nikoli včetně), které je ukončovacího znaku null. Tato poznámka je vyhrazený pro použití na široké znaky pole a podobá se funkci C Runtime [wcslen()](http://msdn.microsoft.com/library/16462f2a-1e0f-4eb3-be55-bf1c83f374c2).|  
  
## <a name="see-also"></a>Viz také  
 [Použití poznámek SAL k omezení defektů kódu C/C++](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [Porozumění SAL](../code-quality/understanding-sal.md)   
 [Zadávání poznámek k parametrům funkcí a návratovým hodnotám](../code-quality/annotating-function-parameters-and-return-values.md)   
 [Zadávání poznámek k chování funkcí](../code-quality/annotating-function-behavior.md)   
 [Zadávání poznámek ke strukturám a třídám](../code-quality/annotating-structs-and-classes.md)   
 [Zadávání poznámek o chování při zamykání](../code-quality/annotating-locking-behavior.md)   
 [Určení, kdy a kde se má poznámka použít](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [Doporučené postupy a příklady](../code-quality/best-practices-and-examples-sal.md)



