---
title: Zadávání poznámek k chování funkcí | Dokumentace Microsoftu
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
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 88213e1cd8112aecac527f7d72d2d74dbf10c559
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51783126"
---
# <a name="annotating-function-behavior"></a>Zadávání poznámek k chování funkcí
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kromě zadávání poznámek k [funkci parametry a návratové hodnoty](../code-quality/annotating-function-parameters-and-return-values.md), přidávat poznámky k vlastnosti celé funkce.  
  
## <a name="function-annotations"></a>Poznámky – funkce  
 Následující poznámky platí pro funkce jako celek a popisují, jak se chová nebo co se očekává, že na hodnotu true.  
  
|Poznámka|Popis|  
|----------------|-----------------|  
|`_Called_from_function_class_(name)`|Není určen pro samostatné; Místo toho je predikátu, která se použije `_When_` poznámky. Další informace najdete v tématu [zadání při a kde Poznámka použít](../code-quality/specifying-when-and-where-an-annotation-applies.md).<br /><br /> `name` Parametr je libovolný řetězec, který se také zobrazí `_Function_class_` poznámky v deklaraci některé funkce.  `_Called_from_function_class_` vrátí nenulovou hodnotu, pokud funkce, která se právě analyzuje je označena pomocí `_Function_class_` , který má stejnou hodnotu `name`; v opačném případě vrátí 0.|  
|`_Check_return_`|Označí návratovou hodnotu a uvádí, že volající by měl zkontrolovat. Nástroj pro kontrolu hlásí chybu, pokud je tato funkce volána v rámci typu void.|  
|`_Function_class_(name)`|`name` Parametr je libovolný řetězec, který je určený uživatel.  Existuje v oboru názvů, která se liší od jiných obory názvů. Funkce, ukazatele na funkci nebo – největší úspěšně – typ ukazatele funkce může být určen jako patřící do jedné nebo více tříd funkce.|  
|`_Raises_SEH_exception_`|Označí funkci, která vždy vyvolá výjimku strukturovaných výjimek (SEH) obslužné rutiny, podléhají `_When_` a `_On_failure_` podmínky. Další informace najdete v tématu [zadání při a kde Poznámka použít](../code-quality/specifying-when-and-where-an-annotation-applies.md).|  
|`_Maybe_raises_SEH_exception_`|Označí funkci, která může volitelně vyvolat výjimku SEH podléhají `_When_` a `_On_failure_` podmínky.|  
|`_Must_inspect_result_`|Označí všechny výstupní hodnota, včetně návratovou hodnotu, parametry a globální prvky.  Analyzátor hlásí chybu, pokud není následně zkontroloval hodnotu v objektu s poznámkami. "Kontrola" zahrnuje, ať už se používá v podmíněném výrazu, je přiřazená k výstupní parametr nebo globální nebo je předán jako parametr.  Pro vrácené hodnoty `_Must_inspect_result_` znamená `_Check_return_`.|  
|`_Use_decl_annotations_`|Mohou být použity v definici funkce (označované také jako tělo funkce) namísto seznamu poznámky v záhlaví.  Když `_Use_decl_annotations_` je používají, poznámky, které se zobrazují na hlavičku v oboru pro stejnou funkci se používají, jako by šlo také obsažené v definici, která má `_Use_decl_annotations_` poznámky.|  
  
## <a name="successfailure-annotations"></a>Poznámky o úspěchu nebo selhání  
 Funkce může selhat, a pokud ano, jeho výsledky mohou být neúplná nebo se liší od výsledky, pokud funkce uspěje.  Poznámky v následujícím seznamu poskytují způsoby, jak express chování selhání.  Pokud chcete použít tyto anotace, musíte povolit jak určit úspěch; Proto `_Success_` je vyžadována Poznámka.  Všimněte si, že `NTSTATUS` a `HRESULT` už máte `_Success_` poznámky, které jsou integrované do nich; však při zadání vlastní `_Success_` poznámky na `NTSTATUS` nebo `HRESULT`, přepíše integrované poznámky.  
  
|Poznámka|Popis|  
|----------------|-----------------|  
|`_Always_(anno_list)`|Ekvivalentní `anno_list _On_failure_(anno_list)`; to znamená, poznámky v `anno_list` použít, jestli je funkce úspěšná.|  
|`_On_failure_(anno_list)`|Má být použit pouze tehdy, když `_Success_` je také používaná k anotaci funkce – buď explicitně nebo implicitně prostřednictvím `_Return_type_success_` v definici typu. Když `_On_failure_` poznámky je k dispozici na parametr nebo návratovou hodnotou funkce, jednotlivé poznámky v `anno_list` (anno) se chová jako kdyby bylo kódováno jako `_When_(!expr, anno)`, kde `expr` je parametr k požadovaným `_Success_` poznámky. To znamená, že implicitní použití `_Success_` všechny podmínky se nedá použít pro `_On_failure_`.|  
|`_Return_type_success_(expr)`|Může použít pro definice typu. Označuje, že všechny funkce, který vrací typ, který není nutné explicitně `_Success_` jsou označena jako by měly `_Success_(expr)`. `_Return_type_success_` nelze použít na funkce nebo definice typu ukazatele funkce.|  
|`_Success_(expr)`|`expr` je výraz, jehož výsledkem jsou r-hodnoty. Když `_Success_` poznámky je k dispozici v deklaraci funkce nebo definice, jednotlivé poznámky (`anno`) na funkce a je ve stavu po se chová jako kdyby bylo kódováno jako `_When_(expr, anno)`. `_Success_` Poznámka může být použita pouze na funkce, ne na jeho parametry nebo návratový typ. Může existovat maximálně jeden `_Success_` Poznámka pro funkci a nemůže být v libovolném `_When_`, `_At_`, nebo `_Group_`. Další informace najdete v tématu [zadání při a kde Poznámka použít](../code-quality/specifying-when-and-where-an-annotation-applies.md).|  
  
## <a name="see-also"></a>Viz také  
 [Použití poznámek SAL k omezení defektů kódu C/C++](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [Porozumění SAL](../code-quality/understanding-sal.md)   
 [Zadávání poznámek k parametrům funkcí a návratovým hodnotám](../code-quality/annotating-function-parameters-and-return-values.md)   
 [Zadávání poznámek ke strukturám a třídám](../code-quality/annotating-structs-and-classes.md)   
 [Zadávání poznámek o chování při zamykání](../code-quality/annotating-locking-behavior.md)   
 [Určení, kdy a kde se má poznámka použít](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [Vnitřní funkce](../code-quality/intrinsic-functions.md)   
 [Doporučené postupy a příklady](../code-quality/best-practices-and-examples-sal.md)



