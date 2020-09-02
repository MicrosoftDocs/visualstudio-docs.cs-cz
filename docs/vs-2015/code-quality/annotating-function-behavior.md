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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "77277866"
---
# <a name="annotating-function-behavior"></a>Zadávání poznámek k chování funkcí
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kromě zadávání poznámek k [parametrům funkcí a návratovým hodnotám](../code-quality/annotating-function-parameters-and-return-values.md)můžete opatřit poznámkami vlastnosti celé funkce.  
  
## <a name="function-annotations"></a>Poznámky k funkcím  
 Následující poznámky se vztahují na funkci jako celek a popisují, jak se chovají nebo co očekává jako true.  
  
|Poznámka|Popis|  
|----------------|-----------------|  
|`_Called_from_function_class_(name)`|Neurčeno k samostatnému; místo toho je predikát pro použití s `_When_` poznámkou. Další informace najdete v tématu [určení, kdy a kde se Poznámka vztahuje](../code-quality/specifying-when-and-where-an-annotation-applies.md).<br /><br /> `name`Parametr je libovolný řetězec, který se také zobrazí v `_Function_class_` anotaci v deklaraci některých funkcí.  `_Called_from_function_class_` vrátí nenulovou hodnotu, pokud je funkce, která je právě analyzována, opatřena poznámkami pomocí `_Function_class_` , který má stejnou hodnotu `name` ; v opačném případě vrátí hodnotu nula.|  
|`_Check_return_`|Označí návratovou hodnotu a určí, že ji volající má zkontrolovat. Nástroj Checker hlásí chybu, pokud je funkce volána v kontextu void.|  
|`_Function_class_(name)`|`name`Parametr je libovolný řetězec, který je určen uživatelem.  Existuje v oboru názvů, který se liší od jiných oborů názvů. Funkce, ukazatel na funkci nebo – nejužitečnější – typ ukazatele na funkci může být určen jako patřící do jedné nebo více tříd Functions.|  
|`_Raises_SEH_exception_`|Doznámí funkci, která vždy vyvolá výjimku strukturované obslužné rutiny výjimek (SEH), `_When_` podléhá `_On_failure_` podmínkám a. Další informace najdete v tématu [určení, kdy a kde se Poznámka vztahuje](../code-quality/specifying-when-and-where-an-annotation-applies.md).|  
|`_Maybe_raises_SEH_exception_`|Doznámí funkci, která může volitelně vyvolat výjimku SEH, podléhá `_When_` podmínkám a `_On_failure_` .|  
|`_Must_inspect_result_`|Označí jakoukoli výstupní hodnotu, včetně návratové hodnoty, parametrů a Globals.  Analyzátor ohlásí chybu, pokud hodnota v objektu s poznámkou není následně kontrolována. "Kontrola" zahrnuje, zda je použit v podmíněném výrazu, je přiřazen výstupnímu parametru nebo globálnímu nebo je předán jako parametr.  Pro návratové hodnoty `_Must_inspect_result_` implikuje `_Check_return_` .|  
|`_Use_decl_annotations_`|Dá se použít v definici funkce (označované také jako tělo funkce) místo seznamu poznámek v hlavičce.  Při `_Use_decl_annotations_` použití se použijí poznámky, které se zobrazí v záhlaví v oboru pro stejnou funkci, jako kdyby byly také přítomny v definici, která má `_Use_decl_annotations_` anotaci.|  
  
## <a name="successfailure-annotations"></a>Poznámky k úspěchu/neúspěchu  
 Funkce může selhat a když je, její výsledky mohou být neúplné nebo se liší od výsledků, pokud je funkce úspěšná.  Poznámky v následujícím seznamu poskytují způsoby, jak vyjádřit chování při selhání.  Chcete-li použít tyto poznámky, je nutné jim povolit, aby určily úspěch. Proto `_Success_` je vyžadována Poznámka.  Všimněte si, že `NTSTATUS` a `HRESULT` již `_Success_` do nich máte zabudovanou poznámku. Pokud však zadáte vlastní `_Success_` poznámku na `NTSTATUS` nebo `HRESULT` , přepíše vestavěnou poznámku.  
  
|Poznámka|Popis|  
|----------------|-----------------|  
|`_Always_(anno_list)`|Ekvivalent `anno_list _On_failure_(anno_list)` ; to znamená, že poznámky v aplikaci `anno_list` platí bez ohledu na to, zda funkce proběhne úspěšně.|  
|`_On_failure_(anno_list)`|Má být použit pouze `_Success_` v případě, že se používá také k přidání poznámky k funkci – buď explicitně, nebo implicitně prostřednictvím `_Return_type_success_` typu typedef. Pokud `_On_failure_` je Poznámka přítomna v parametru funkce nebo návratové hodnotě, každá Poznámka v `anno_list` (Anno) se chová, jako by byla kódována jako `_When_(!expr, anno)` , kde `expr` je parametr pro požadovanou `_Success_` poznámku. To znamená, že předpokládaná aplikace pro `_Success_` všechny podmínky odeslání neplatí pro `_On_failure_` .|  
|`_Return_type_success_(expr)`|Může být použito pro typedef. Označuje, že všechny funkce, které vracejí tento typ a explicitně nejsou `_Success_` opatřeny poznámkami, jako by měly `_Success_(expr)` . `_Return_type_success_` nelze použít pro funkci nebo typedef s ukazatelem na funkci.|  
|`_Success_(expr)`|`expr` je výraz, který poskytuje rvalue. Pokud `_Success_` je Poznámka přítomna v deklaraci nebo definici funkce, každé anotace ( `anno` ) funkce a v podmínkách post se chová, jako by byla kódována jako `_When_(expr, anno)` . `_Success_`Anotace lze použít pouze pro funkci, nikoli pro její parametry nebo návratový typ. U funkce může existovat maximálně jedno `_Success_` Anotace a nemůže být v žádném `_When_` , `_At_` nebo `_Group_` . Další informace najdete v tématu [určení, kdy a kde se Poznámka vztahuje](../code-quality/specifying-when-and-where-an-annotation-applies.md).|  
  
## <a name="see-also"></a>Viz také  
 [Použití poznámek SAL k omezení vad kódu C/C++](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [Porozumění SAL](../code-quality/understanding-sal.md)   
 [Zadávání poznámek k parametrům funkcí a návratovým hodnotám](../code-quality/annotating-function-parameters-and-return-values.md)   
 [Přidávání poznámek ke strukturám a třídám](../code-quality/annotating-structs-and-classes.md)   
 [Zadávání poznámek k chování při zamykání](../code-quality/annotating-locking-behavior.md)   
 [Určení, kdy a kde se má Poznámka použít](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [Vnitřní funkce](../code-quality/intrinsic-functions.md)   
 [Doporučené postupy a příklady](../code-quality/best-practices-and-examples-sal.md)
