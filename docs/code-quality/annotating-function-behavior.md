---
title: Zadávání poznámek k chování funkcí
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- _On_failure_
- _Return_type_success_
- _Always_
- _Maybe_raises_SEH_exception_
- _Raises_SEH_exception_
- _Called_from_function_class_
- _Function_class_
- _Must_inspect_result_
- _Success_
- _Check_return_
- _Use_decl_annotations_
ms.assetid: c0aa268d-6fa3-4ced-a8c6-f7652b152e61
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: 7ee46c277574b9ceec2c4b0a26685570d305990f
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
ms.locfileid: "31899352"
---
# <a name="annotating-function-behavior"></a>Zadávání poznámek k chování funkcí
Kromě zadávání poznámek k [funkce parametry a návratové hodnoty](../code-quality/annotating-function-parameters-and-return-values.md), může opatřit poznámkami celou funkci.

## <a name="function-annotations"></a>Funkce poznámek
 Následující poznámky platí pro funkce jako celek a popisují, jak se chová nebo co se očekává, že na hodnotu true.

|Poznámka|Popis|
|----------------|-----------------|
|`_Called_from_function_class_(name)`|Není určena pro samostatná; Místo toho je predikát pro použití s `_When_` poznámky. Další informace najdete v tématu [zadání při a kde poznámky platí](../code-quality/specifying-when-and-where-an-annotation-applies.md).<br /><br /> `name` Parametr je libovolný řetězec, který se zobrazí také v `_Function_class_` poznámky v deklaraci některé funkce.  `_Called_from_function_class_` Vrátí nenulové hodnoty, pokud je funkce, která je aktuálně analyzován poznámkou pomocí `_Function_class_` který má stejnou hodnotu `name`, jinak vrátí hodnotu nula.|
|`_Check_return_`|Označí návratovou hodnotu a stanoví, že volající by měl zkontrolovat. Nástroj pro kontrolu nahlásí chybu, pokud je tato funkce volána v kontextu void.|
|`_Function_class_(name)`|`name` Parametr je libovolný řetězec, který je určený uživatel.  Existuje v oboru názvů, který se liší od jiných oborech názvů. Funkce, – ukazatel na funkci, nebo – nejvíce úspěšně – ukazatel typu funkce může být určen jako náležící do jedné nebo více tříd funkce.|
|`_Raises_SEH_exception_`|Označí funkci, která vždy vyvolá obslužnou rutinu (SEH) výjimka strukturovaného výjimek, podléhají `_When_` a `_On_failure_` podmínky. Další informace najdete v tématu [zadání při a kde poznámky platí](../code-quality/specifying-when-and-where-an-annotation-applies.md).|
|`_Maybe_raises_SEH_exception_`|Označí funkci, která může volitelně vyvolat výjimku SEH podléhají `_When_` a `_On_failure_` podmínky.|
|`_Must_inspect_result_`|Označí jakákoli hodnota výstupu, včetně návratovou hodnotu, parametry a globální prvky.  Analyzátoru nahlásí chybu, pokud hodnoty v poznámkou objektu není prověřovány následně. "Kontroly" zahrnuje, jestli se používá v podmíněným výrazem, je přiřazená k výstupní parametr, globální nebo se předá jako parametr.  Návratové hodnoty `_Must_inspect_result_` znamená `_Check_return_`.|
|`_Use_decl_annotations_`|Může být použít v definici funkce (také označované jako tělo funkce) místo seznam poznámky v záhlaví.  Když `_Use_decl_annotations_` se používá, poznámky, které se zobrazují na hlavičku v oboru pro stejnou funkci slouží jako, když jsou i obsažené v definici, který má `_Use_decl_annotations_` poznámky.|

## <a name="successfailure-annotations"></a>Úspěch nebo selhání poznámky
 Funkce může selhat, a pokud ano, své výsledky mohou být neúplné nebo se liší od výsledky, pokud je funkce úspěšná.  Poznámky v následujícím seznamu poskytují způsoby, jak express chování selhání.  Pokud chcete použít tyto poznámky, musíte povolit k určení úspěšnosti; Proto `_Success_` poznámky se vyžaduje.  Všimněte si, že `NTSTATUS` a `HRESULT` už máte `_Success_` poznámky součástí je; ale pokud zadáte vlastní `_Success_` poznámky na `NTSTATUS` nebo `HRESULT`, přepíše předdefinované poznámky.

|Poznámka|Popis|
|----------------|-----------------|
|`_Always_(anno_list)`|Ekvivalentní `anno_list _On_failure_(anno_list)`; to znamená, poznámky v `anno_list` použít zda funkce úspěšné.|
|`_On_failure_(anno_list)`|Má být použit pouze tehdy, když `_Success_` je také používaná k anotaci funkce – buď explicitně nebo implicitně prostřednictvím `_Return_type_success_` v definici typu. Když `_On_failure_` poznámky se nachází na funkce, nebo parametr návratové hodnotě, každý poznámky v `anno_list` (anno) se chová jako kdyby byly programového jako `_When_(!expr, anno)`, kde `expr` je parametr k požadovaným `_Success_` poznámky. To znamená, že předpokládané použití `_Success_` všechny po podmínky nevztahuje na `_On_failure_`.|
|`_Return_type_success_(expr)`|Může použít k definici typu. Označuje, že všechny funkce tohoto vrátit, zadejte a není nutné explicitně `_Success_` jsou opatřeny poznámkami, jako by měly `_Success_(expr)`. `_Return_type_success_` nelze použít na funkci nebo funkce pointer – typedef.|
|`_Success_(expr)`|`expr` je výraz, který poskytne rvalue. Když `_Success_` je přítomen v deklaraci funkce nebo definice, každý Poznámka Poznámka (`anno`) u funkce a v po stavu se chová, jako by byly programového jako `_When_(expr, anno)`. `_Success_` Poznámky může použít pouze na funkce, ne na jeho parametry nebo návratovým typem. Může být maximálně jedna `_Success_` poznámky na funkce ale nemůže být v některém `_When_`, `_At_`, nebo `_Group_`. Další informace najdete v tématu [zadání při a kde poznámky platí](../code-quality/specifying-when-and-where-an-annotation-applies.md).|

## <a name="see-also"></a>Viz také
 [Použití poznámek SAL k snížení míry výskytu závad kódu C/C++](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md) [porozumění SAL](../code-quality/understanding-sal.md) [zadávání poznámek k parametrům funkcí a návratovým hodnotám](../code-quality/annotating-function-parameters-and-return-values.md) [zadávání poznámek ke strukturám a třídám](../code-quality/annotating-structs-and-classes.md) [Zadávání poznámek k chování při zamykání](../code-quality/annotating-locking-behavior.md) [určující, kdy a kde se má poznámka použít](../code-quality/specifying-when-and-where-an-annotation-applies.md) [vnitřní funkce](../code-quality/intrinsic-functions.md) [osvědčené postupy a Příklady](../code-quality/best-practices-and-examples-sal.md)