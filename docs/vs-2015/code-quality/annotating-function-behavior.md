---
title: Zadávání poznámek k chování funkcí | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
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
caps.latest.revision: 13
author: corob-msft
ms.author: corob
manager: jillfra
ms.openlocfilehash: 7ebda5933f73e2511932f8968104327a56ee7606
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/15/2020
ms.locfileid: "77277866"
---
# <a name="annotating-function-behavior"></a>Zadávání poznámek k chování funkcí
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kromě zadávání poznámek k [parametrům funkcí a návratovým hodnotám](../code-quality/annotating-function-parameters-and-return-values.md)můžete opatřit poznámkami vlastnosti celé funkce.  
  
## <a name="function-annotations"></a>Poznámky k funkcím  
 Následující poznámky se vztahují na funkci jako celek a popisují, jak se chovají nebo co očekává jako true.  
  
|Poznámka|Popis|  
|----------------|-----------------|  
|`_Called_from_function_class_(name)`|Neurčeno k samostatnému; místo toho je predikát pro použití s anotací `_When_`. Další informace najdete v tématu [určení, kdy a kde se Poznámka vztahuje](../code-quality/specifying-when-and-where-an-annotation-applies.md).<br /><br /> Parametr `name` je libovolný řetězec, který se také zobrazí v poznámce `_Function_class_` v deklaraci některých funkcí.  `_Called_from_function_class_` vrátí nenulovou hodnotu, pokud je funkce, která je právě analyzována, opatřena poznámkou pomocí `_Function_class_`, která má stejnou hodnotu `name`; v opačném případě vrátí hodnotu nula.|  
|`_Check_return_`|Označí návratovou hodnotu a určí, že ji volající má zkontrolovat. Nástroj Checker hlásí chybu, pokud je funkce volána v kontextu void.|  
|`_Function_class_(name)`|Parametr `name` je libovolný řetězec, který je určen uživatelem.  Existuje v oboru názvů, který se liší od jiných oborů názvů. Funkce, ukazatel na funkci nebo – nejužitečnější – typ ukazatele na funkci může být určen jako patřící do jedné nebo více tříd Functions.|  
|`_Raises_SEH_exception_`|Doznámí funkci, která vždy vyvolává výjimku strukturované obslužné rutiny výjimek (SEH), podléhá `_When_` a `_On_failure_` podmínek. Další informace najdete v tématu [určení, kdy a kde se Poznámka vztahuje](../code-quality/specifying-when-and-where-an-annotation-applies.md).|  
|`_Maybe_raises_SEH_exception_`|Doznámí funkci, která může volitelně vyvolat výjimku SEH, v souladu s podmínkami `_When_` a `_On_failure_`.|  
|`_Must_inspect_result_`|Označí jakoukoli výstupní hodnotu, včetně návratové hodnoty, parametrů a Globals.  Analyzátor ohlásí chybu, pokud hodnota v objektu s poznámkou není následně kontrolována. "Kontrola" zahrnuje, zda je použit v podmíněném výrazu, je přiřazen výstupnímu parametru nebo globálnímu nebo je předán jako parametr.  Pro návratové hodnoty `_Must_inspect_result_` implikuje `_Check_return_`.|  
|`_Use_decl_annotations_`|Dá se použít v definici funkce (označované také jako tělo funkce) místo seznamu poznámek v hlavičce.  Při použití `_Use_decl_annotations_` se používají poznámky, které se zobrazí v záhlaví v oboru pro stejnou funkci, jako kdyby byly také přítomny v definici, která má `_Use_decl_annotations_` anotace.|  
  
## <a name="successfailure-annotations"></a>Poznámky k úspěchu/neúspěchu  
 Funkce může selhat a když je, její výsledky mohou být neúplné nebo se liší od výsledků, pokud je funkce úspěšná.  Poznámky v následujícím seznamu poskytují způsoby, jak vyjádřit chování při selhání.  Chcete-li použít tyto poznámky, je nutné jim povolit, aby určily úspěch. Proto je potřeba anotace `_Success_`.  Všimněte si, že `NTSTATUS` a `HRESULT` již mají do nich zabudovanou `_Success_` anotaci. Pokud však zadáte vlastní `_Success_` anotace v `NTSTATUS` nebo `HRESULT`, přepíše vestavěnou poznámku.  
  
|Poznámka|Popis|  
|----------------|-----------------|  
|`_Always_(anno_list)`|Ekvivalent `anno_list _On_failure_(anno_list)`; To znamená, že poznámky v `anno_list` použijí, zda je funkce úspěšná.|  
|`_On_failure_(anno_list)`|Dá se použít jenom v případě, že se k této funkci používá taky `_Success_`, a to buď explicitně, nebo implicitně prostřednictvím `_Return_type_success_` na typedef. Když je `_On_failure_` anotace přítomna v parametru funkce nebo v návratové hodnotě, každá Poznámka v `anno_list` (Anno) se chová, jako by byla kódována jako `_When_(!expr, anno)`, kde `expr` je parametrem požadované `_Success_` poznámky. To znamená, že předpokládaná aplikace `_Success_` pro všechny podmínky odeslání neplatí pro `_On_failure_`.|  
|`_Return_type_success_(expr)`|Může být použito pro typedef. Označuje, že všechny funkce, které vracejí tento typ a nejsou explicitně `_Success_`, jsou opatřeny poznámkami, jako by měly `_Success_(expr)`. `_Return_type_success_` nelze použít pro funkci nebo typedef s ukazatelem na funkci.|  
|`_Success_(expr)`|`expr` je výraz, který poskytuje rvalue. Když je `_Success_` anotace přítomna v deklaraci nebo definici funkce, každá anotace (`anno`) na funkci a v podmínkách post se chová, jako by byla kódována jako `_When_(expr, anno)`. Anotace `_Success_` lze použít pouze pro funkci, nikoli pro její parametry nebo návratový typ. U funkce může existovat maximálně jedno `_Success_` anotace a nemůže být v žádném `_When_`, `_At_`ani `_Group_`. Další informace najdete v tématu [určení, kdy a kde se Poznámka vztahuje](../code-quality/specifying-when-and-where-an-annotation-applies.md).|  
  
## <a name="see-also"></a>Viz také  
 [Použití poznámek SAL ke snížení vad CC++ /kódu](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [Princip  Sal](../code-quality/understanding-sal.md)  
 Zadávání [poznámek k parametrům funkcí a návratovým hodnotám](../code-quality/annotating-function-parameters-and-return-values.md)   
 [Přidávání poznámek ke strukturám a třídám](../code-quality/annotating-structs-and-classes.md)   
 Zadávání [poznámek o chování při zamykání](../code-quality/annotating-locking-behavior.md)   
 [Určení, kdy a kde se má Poznámka použít](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
   [vnitřních funkcí](../code-quality/intrinsic-functions.md)  
 [Doporučené postupy a příklady](../code-quality/best-practices-and-examples-sal.md)
