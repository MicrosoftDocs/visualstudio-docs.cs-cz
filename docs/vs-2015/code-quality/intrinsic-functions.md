---
title: Vnitřní funkce | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
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
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: jillfra
ms.openlocfilehash: a0a6cd31cbc8cf73cfa2c7e9ee7c096fa56799b9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "77277958"
---
# <a name="intrinsic-functions"></a>Vnitřní funkce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Výraz v SAL může být výraz jazyka C/C++ za předpokladu, že se jedná o výraz, který nemá vedlejší účinky, například + +,--, a volání funkcí mají v tomto kontextu vedlejší účinky.  SAL však poskytuje některé objekty podobné funkcím a některé vyhrazené symboly, které lze použít ve výrazech SAL. Ty jsou označovány jako *vnitřní funkce*.  
  
## <a name="general-purpose"></a>Pro obecné účely  
 Následující poznámky k funkcím instrinsic poskytují obecný nástroj pro SAL.  
  
|Poznámka|Popis|  
|----------------|-----------------|  
|`_Curr_`|Synonymum pro objekt, který je v současné době opatřen poznámkami.  Když se `_At_` Poznámka používá, `_Curr_` je stejná jako první parametr pro `_At_` .  V opačném případě se jedná o parametr nebo o celou funkci nebo návratovou hodnotu, se kterou je Poznámka lexikální.|  
|`_Inexpressible_(expr)`|Vyjadřuje situaci, kdy velikost vyrovnávací paměti je příliš složitá, aby byla reprezentována pomocí výrazu poznámky, například když je vypočítána kontrolou vstupní datové sady a následným vypočítáním vybraných členů.|  
|`_Nullterm_length_(param)`|`param` je počet prvků ve vyrovnávací paměti až do ne včetně ukončovacího znaku null. Dá se použít na jakoukoli vyrovnávací paměť neagregovaného typu, který není typu void.|  
|`_Old_(expr)`|Pokud je vyhodnocena v předběžné podmínce, `_Old_` vrátí vstupní hodnotu `expr` .  Pokud je vyhodnocena v rámci podmínky post, vrátí hodnotu `expr` , protože by byla vyhodnocena v předběžné podmínce.|  
|`_Param_(n)`|`n`Parametr th pro funkci, který se počítá z 1 na a `n` `n` je literál integrální konstanty. Pokud je parametr pojmenován, je tato poznámka shodná s přístupem k parametru podle názvu. **Poznámka:** `n` může odkazovat na poziční parametry, které jsou definovány třemi tečkami, nebo mohou být použity v prototypech funkce, kde se názvy nepoužívají.  |  
|`return`|Rezervované klíčové slovo C/C++ `return` lze použít ve výrazu SAL k označení návratové hodnoty funkce.  Hodnota je k dispozici pouze ve stavu post; Jedná se o chybu syntaxe, která se má použít v předběžném stavu.|  
  
## <a name="string-specific"></a>Specifické pro řetězec  
 Následující poznámky vnitřní funkce umožňují manipulaci s řetězci. Všechny čtyři tyto funkce mají stejný účel: k vrácení počtu prvků typu, který se nachází před prázdným znakem null. Rozdíly jsou typy dat v prvcích, na které se odkazuje. Všimněte si, že pokud chcete zadat délku vyrovnávací paměti zakončené hodnotou null, která není složena ze znaků, použijte `_Nullterm_length_(param)` poznámku z předchozí části.  
  
|Poznámka|Popis|  
|----------------|-----------------|  
|`_String_length_(param)`|`param` je počet prvků v řetězci až do, ale ne včetně ukončovacího znaku null. Tato poznámka je vyhrazena pro typy řetězcových znaků.|  
|`strlen(param)`|`param` je počet prvků v řetězci až do, ale ne včetně ukončovacího znaku null. Tato poznámka je vyhrazena pro použití v polích znaků a podobá se běhové funkci jazyka C [strlen ()](https://msdn.microsoft.com/library/16462f2a-1e0f-4eb3-be55-bf1c83f374c2).|  
|`wcslen(param)`|`param` je počet prvků v řetězci až do (ale ne včetně) ukončovacího znaku null. Tato poznámka je vyhrazena pro použití v různých polích znaků a podobá se běhové funkci jazyka C [wcslen ()](https://msdn.microsoft.com/library/16462f2a-1e0f-4eb3-be55-bf1c83f374c2).|  
  
## <a name="see-also"></a>Viz také  
 [Použití poznámek SAL k omezení vad kódu C/C++](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [Porozumění SAL](../code-quality/understanding-sal.md)   
 [Zadávání poznámek k parametrům funkcí a návratovým hodnotám](../code-quality/annotating-function-parameters-and-return-values.md)   
 [Zadávání poznámek k chování funkcí](../code-quality/annotating-function-behavior.md)   
 [Přidávání poznámek ke strukturám a třídám](../code-quality/annotating-structs-and-classes.md)   
 [Zadávání poznámek k chování při zamykání](../code-quality/annotating-locking-behavior.md)   
 [Určení, kdy a kde se má Poznámka použít](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [Doporučené postupy a příklady](../code-quality/best-practices-and-examples-sal.md)
