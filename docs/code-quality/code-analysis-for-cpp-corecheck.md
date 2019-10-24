---
title: C++Reference k základní kontrole – referenční pokyny
ms.date: 03/22/2018
ms.topic: reference
helpviewer_keywords:
- code analysis, C++ core check
ms.assetid: f1429463-136e-41ed-8a75-a8dbf0b4fd89
author: mikeblome
ms.author: mblome
manager: markl
ms.workload:
- cplusplus
ms.openlocfilehash: 9a5fe14c1bcb2b375a104a928513134b1789d437
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745968"
---
# <a name="c-core-guidelines-checker-reference"></a>C++Reference k základní kontrole – referenční pokyny

V této části C++ jsou uvedené základní pokyny – upozornění kontroly. Informace o analýze kódu naleznete v tématu [/analyze (Code Analysis)](/cpp/build/reference/analyze-code-analysis) a [rychlé zprovoznění: Analýza kódu pro C/C++](../code-quality/quick-start-code-analysis-for-c-cpp.md).

> [!NOTE]
> Některá upozornění patří do více než jedné skupiny a ne všechna upozornění mají kompletní odkaz na téma.

## <a name="owner_pointer-group"></a>Skupina OWNER_POINTER

[C26402 DONT_HEAP_ALLOCATE_MOVABLE_RESULT](C26402.md) Vrátí objekt s oborem namísto přidělené haldě, pokud má konstruktor Move. Viz [ C++ základní pokyny R. 3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).

[C26403 RESET_OR_DELETE_OWNER](C26403.md) Resetování nebo explicitní odstranění vlastníka \<T > ukazatel% Variable%. Viz [ C++ základní pokyny R. 3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).

[C26404 DONT_DELETE_INVALID](C26404.md) Neodstraňujte vlastníka \<T >, který může být v neplatném stavu. Viz [ C++ základní pokyny R. 3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).

[C26405 DONT_ASSIGN_TO_VALID](C26405.md) Nepřiřazujte k vlastníkovi \<T >, který může být v platném stavu. Viz [ C++ základní pokyny R. 3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).

[C26406 DONT_ASSIGN_RAW_TO_OWNER](C26406.md) Nepřiřazujte nezpracovaný ukazatel k Owner \<T >. Viz [ C++ základní pokyny R. 3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).

[C26407 DONT_HEAP_ALLOCATE_UNNECESSARILY](C26407.md) Preferovat objekty s obory, nepoužívejte zbytečně přidělovat haldu. Viz [ C++ základní pokyny R. 5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-scoped).

[C26429 USE_NOTNULL](C26429.md) Symbol% symbol% se nikdy netestoval na hodnotu null, může být označený jako Not_Null. Viz [ C++ základní pokyny F. 23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).

[C26430 TEST_ON_ALL_PATHS](C26430.md) Symbol% symbol% není testován na hodnotu null u všech cest. Viz [ C++ základní pokyny F. 23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).

[C26431 DONT_TEST_NOTNULL](C26431.md) Typ výrazu% expr% už je GSL:: Not_Null. Netestujte ho na hodnotu null. Viz [ C++ základní pokyny F. 23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).

## <a name="raw_pointer-group"></a>Skupina RAW_POINTER

[C26400 NO_RAW_POINTER_ASSIGNMENT](c26400.md) Nepřiřazujte výsledek přidělení nebo volání funkce s vlastníkem \<T > návratovou hodnotu k nezpracovanému ukazateli. místo toho použijte \<T Owner >. Viz [ C++ základní pokyny I. 11](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Ri-raw).

[C26401 DONT_DELETE_NON_OWNER](c26401.md) Neodstraňujte nezpracovaný ukazatel, který není vlastníkem \<T >. Viz [ C++ základní pokyny I. 11](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Ri-raw).

[C26402 DONT_HEAP_ALLOCATE_MOVABLE_RESULT](C26402.md)   vrátí oborový objekt namísto přidělené haldě, pokud má konstruktor Move. Viz [ C++ základní pokyny R. 3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).

[C26408 NO_MALLOC_FREE](C26408.md) Vyhněte se zavoláním \ () a Free (), preferovat verzi nové s odstraněním. Viz [ C++ základní pokyny R. 10](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-mallocfree).

[C26409 NO_NEW_DELETE](C26409.md) Vyhněte se volání New a DELETE explicitně, místo toho použijte std:: make_unique \<T >. Viz [ C++ základní pokyny R. 11](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-newdelete).

[C26429 USE_NOTNULL](C26429.md) Symbol% symbol% se nikdy netestoval na hodnotu null, může být označený jako Not_Null. Viz [ C++ základní pokyny F. 23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).

[C26430 TEST_ON_ALL_PATHS](C26430.md) Symbol% symbol% není testován na hodnotu null u všech cest. Viz [ C++ základní pokyny F. 23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).

[C26431 DONT_TEST_NOTNULL](C26431.md) Typ výrazu% expr% už je GSL:: Not_Null. Netestujte ho na hodnotu null. Viz [ C++ základní pokyny F. 23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).

[C26481 NO_POINTER_ARITHMETIC](C26481.md) Nepoužívejte aritmetický ukazatel. Místo toho použijte rozpětí. Viz [ C++ základní pokyny meze. 1](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds).

[C26485 NO_ARRAY_TO_POINTER_DECAY](C26485.md).
Výraz% expr%: žádné pole pro ukazatel Decay. Viz [ C++ základní pokyny jsou vázané. 3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds).

## <a name="unique_pointer-group"></a>Skupina UNIQUE_POINTER

[C26410 NO_REF_TO_CONST_UNIQUE_PTR](C26410.md) Parametr% Parameter% je odkazem na `const` jedinečný ukazatel, místo toho použijte const T * nebo const T &. Viz [ C++ základní pokyny R. 32](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-uniqueptrparam).

[C26411 NO_REF_TO_UNIQUE_PTR](C26411.md) Parametr% Parameter% je odkaz na jedinečný ukazatel a nikdy se znovu nepřiřazuje ani neresetuje, místo toho použijte & T * nebo T. Viz [ C++ základní pokyny R. 33](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-reseat).

[C26414 RESET_LOCAL_SMART_PTR](C26414.md) Přesuňte, zkopírujte, přeřaďte nebo resetujte místní inteligentní ukazatel% symbol%. Viz [ C++ základní pokyny R. 5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-scoped).

[C26415 SMART_PTR_NOT_NEEDED](C26415.md) Parametr inteligentního ukazatele% symbol% se používá jenom pro přístup k obsaženému ukazateli. Místo toho použijte & T * nebo T. Viz [ C++ základní pokyny R. 30](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-smartptrparam).

## <a name="shared_pointer-group"></a>Skupina SHARED_POINTER

[C26414 RESET_LOCAL_SMART_PTR](C26414.md) Přesuňte, zkopírujte, přeřaďte nebo resetujte místní inteligentní ukazatel% symbol%. Viz [ C++ základní pokyny R. 5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-scoped).

[C26415 SMART_PTR_NOT_NEEDED](C26415.md) Parametr inteligentního ukazatele% symbol% se používá jenom pro přístup k obsaženému ukazateli. Místo toho použijte & T * nebo T. Viz [ C++ základní pokyny R. 30](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-smartptrparam).

[C26416 NO_RVALUE_REF_SHARED_PTR](C26416.md) Parametr sdíleného ukazatele% symbol% je předaný odkazem rvalue. Místo toho předejte hodnotu. Viz [ C++ základní pokyny R. 34](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-sharedptrparam-owner).

[C26417 NO_LVALUE_REF_SHARED_PTR](C26417.md) Sdílený parametr ukazatele% symbol% je předaný odkazem a neresetuje se ani znovu nepřiřazuje. Místo toho použijte & T * nebo T. Viz [ C++ základní pokyny R. 35](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-sharedptrparam).

[C26418 NO_VALUE_OR_CONST_REF_SHARED_PTR](C26418.md) Sdílený parametr ukazatele% symbol% není zkopírovaný ani přesunutý. Místo toho použijte & T * nebo T. Viz [ C++ základní pokyny R. 36](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-sharedptrparam-const).

## <a name="declaration-group"></a>Skupina DEKLARACÍ

[C26426 NO_GLOBAL_INIT_CALLS](C26426.md) Globální inicializátor volá funkci% symbol%, která není constexpr. Viz [ C++ základní pokyny I. 22](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#i22-avoid-complex-initialization-of-global-objects).

[C26427 NO_GLOBAL_INIT_EXTERNS](C26427.md) Globální inicializátor přistupuje k externímu objektu% symbol%. Viz [ C++ základní pokyny I. 22](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#i22-avoid-complex-initialization-of-global-objects).

[C26444 NO_UNNAMED_RAII_OBJECTS](c26444.md) Nepoužívejte nepojmenované objekty s vlastní konstrukcí a destrukcí. Viz [ES. 84: nejde (zkusit) deklarovat místní proměnnou bez názvu](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md).

## <a name="class-group"></a>Skupina tříd

[C26432 DEFINE_OR_DELETE_SPECIAL_OPS](C26432.md) Pokud definujete nebo odstraníte jakoukoli výchozí operaci v typu% symbol%, definujte nebo odstraňte všechny. Viz [ C++ základní pokyny C. 21](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#c21-if-you-define-or-delete-any-default-operation-define-or-delete-them-all).

[C26433 OVERRIDE_EXPLICITLY](c26433.md) Funkce% symbol% by měla být označená klíčovým slovem override. Viz [C. 128: virtuální funkce by měly zadat přesně jednu z funkcí Virtual, override nebo Final](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#c128-virtual-functions-should-specify-exactly-one-of-virtual-override-or-final).

[C26434 DONT_HIDE_METHODS](C26434.md) Funkce% symbol_1% skrývá nevirtuální funkci% symbol_2%. Viz [ C++ základní pokyny C. 128](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#c128-virtual-functions-should-specify-exactly-one-of-virtual-override-or-final).

[C26435 SINGLE_VIRTUAL_SPECIFICATION](c26435.md) Funkce% symbol% by měla určovat právě jedno z těchto funkcí: Virtual, override nebo Final. Viz [C. 128: virtuální funkce by měly zadat přesně jednu z funkcí Virtual, override nebo Final](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md).

[C26436 NEED_VIRTUAL_DTOR](C26436.md) Typ% symbol% s virtuální funkcí potřebuje buď veřejný virtuální, nebo chráněný nevirtuální destruktor. Viz [ C++ základní pokyny C. 35](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#c35-a-base-class-destructor-should-be-either-public-and-virtual-or-protected-and-nonvirtual).

[C26443 NO_EXPLICIT_DTOR_OVERRIDE](c26443.md) Při přepisování destruktoru by se neměl používat explicitní specifikátor override nebo Virtual. Viz [C. 128: virtuální funkce by měly zadat přesně jednu z funkcí Virtual, override nebo Final](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md).

## <a name="type-group"></a>Skupina typů

[C26437 DONT_SLICE](C26437.md) Nevytvářejte řezy. Viz [ C++ základní pokyny ES. 63](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#es63-dont-slice).

## <a name="style-group"></a>Skupina stylů

[C26438 NO_GOTO](C26438.md) Vyhněte se `goto`. Viz [ C++ základní pokyny ES. 76](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#es76-avoid-goto).

## <a name="function-group"></a>Skupina funkcí

[C26439 SPECIAL_NOEXCEPT](C26439.md) Tento druh funkce nemůže vyvolat výjimku. Deklarujte `noexcept`. Viz [ C++ základní pokyny F. 6](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f6-if-your-function-may-not-throw-declare-it-noexcept).

[C26440 DECLARE_NOEXCEPT](C26440.md) Funkce% symbol% se dá deklarovat `noexcept`. Viz [ C++ základní pokyny F. 6](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f6-if-your-function-may-not-throw-declare-it-noexcept).

[C26447 DONT_THROW_IN_NOEXCEPT](c26447.md) Funkce je deklarována **s výjimkou** , ale volá funkci, která může vyvolat výjimky.
Viz [ C++ základní pokyny: F. 6: Pokud funkce nemůže vyvolat throw, deklarujte ji s výjimkou](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f6-if-your-function-may-not-throw-declare-it-noexcept).

## <a name="concurrency-group"></a>Skupina SOUBĚŽNosti

[C26441 NO_UNNAMED_GUARDS](C26441.md) Objekty Guard musí mít název. Podívejte se na [ C++ základní pokyny CP. 44](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#cp44-remember-to-name-your-lock_guards-and-unique_locks).

## <a name="const-group"></a>Skupina CONSt

[C26460 USE_CONST_REFERENCE_ARGUMENTS](c26460.md) Argument odkazu% argumentu% pro funkci% Function% může být označený jako `const`. Viz [ C++ základní pokyny con. 3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rconst-ref).

[C26461 USE_CONST_POINTER_ARGUMENTS](c26461.md): argument ukazatele% argumentu% pro funkci% Function% může být označen jako ukazatel na `const`. Viz [ C++ základní pokyny con. 3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rconst-ref).

[C26462 USE_CONST_POINTER_FOR_VARIABLE](c26462.md) Hodnota, na kterou ukazuje% Variable%, je přiřazená jen jednou, označte ji jako ukazatel na `const`. Viz [ C++ základní pokyny con. 4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con4-use-const-to-define-objects-with-values-that-do-not-change-after-construction).

[C26463 USE_CONST_FOR_ELEMENTS](c26463.md) Prvky pole '% Array% ' jsou přiřazeny pouze jednou, označte prvky `const`. Viz [ C++ základní pokyny con. 4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con4-use-const-to-define-objects-with-values-that-do-not-change-after-construction).

[C26464 USE_CONST_POINTER_FOR_ELEMENTS](c26464.md) Hodnoty, na které ukazují prvky pole% Array%, jsou přiřazené pouze jednou, označte prvky jako ukazatel na `const`. Viz [ C++ základní pokyny con. 4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con4-use-const-to-define-objects-with-values-that-do-not-change-after-construction).

[C26496 USE_CONST_FOR_VARIABLE](c26496.md) Proměnná% Variable% je přiřazená jen jednou, označte ji jako `const`. Viz [ C++ základní pokyny con. 4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con4-use-const-to-define-objects-with-values-that-do-not-change-after-construction).

[C26497 USE_CONSTEXPR_FOR_FUNCTION](c26497.md) Tato funkce% Function% by mohla být označena jako `constexpr`, pokud je požadováno vyhodnocení v době kompilace. Viz [ C++ základní pokyny F. 4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rf-constexpr).

[C26498 USE_CONSTEXPR_FOR_FUNCTIONCALL](c26498.md) Toto volání funkce% Function% může použít `constexpr`, pokud je požadováno vyhodnocení v době kompilace. Viz [ C++ základní pokyny con. 5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rconst-constexpr).

## <a name="type-group"></a>Skupina typů

[C26465 NO_CONST_CAST_UNNECESSARY](c26465.md) Nepoužívejte `const_cast` k přetypování `const` pryč. `const_cast` není vyžadováno; v tomto převodu se neodebírá const nebo nestálost. Viz [ C++ základní pokyny typ. 3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-constcast).

[C26466 NO_STATIC_DOWNCAST_POLYMORPHIC](c26466.md) Nepoužívejte `static_cast` dolů. Přetypování z polymorfního typu by mělo používat dynamic_cast. Viz [ C++ základní pokyny typ. 2](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-downcast).

[C26471 NO_REINTERPRET_CAST_FROM_VOID_PTR](c26471.md) Nepoužívejte `reinterpret_cast`. Přetypování z void * může používat `static_cast`. Viz [ C++ základní pokyny typ. 1](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-reinterpretcast).

[C26472 NO_CASTS_FOR_ARITHMETIC_CONVERSION](C26472.md) Nepoužívejte `static_cast` pro aritmetické převody. Použijte inicializaci složené závorky, GSL:: narrow_cast nebo GSL:: narow. Viz [ C++ základní pokyny typ. 1](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-reinterpretcast).

[C26473 NO_IDENTITY_CAST](C26473.md) Nepoužívejte přetypování mezi typy ukazatelů, přičemž zdrojový typ a cílový typ jsou stejné. Viz [ C++ základní pokyny typ. 1](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-reinterpretcast).

[C26474 NO_IMPLICIT_CAST](C26474.md) Nepoužívejte přetypování mezi typy ukazatelů, když převod může být implicitní. Viz [ C++ základní pokyny typ. 1](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-reinterpretcast).

[C26475 NO_FUNCTION_STYLE_CASTS](C26475.md) Nepoužívejte přetypování funkcí stylu C. Viz [ C++ základní pokyny ES. 49](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#es49-if-you-must-use-a-cast-use-a-named-cast).

[C26490 NO_REINTERPRET_CAST](c26490.md) Nepoužívejte `reinterpret_cast`. Viz [ C++ základní pokyny typ. 1](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).

[C26491 NO_STATIC_DOWNCAST](c26490.md) Nepoužívejte `static_cast` dolů. Viz [ C++ základní pokyny typ. 2](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).

[C26492 NO_CONST_CAST](c26492.md) Nepoužívejte `const_cast` k přetypování `const` pryč. Viz [ C++ základní pokyny typ. 3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).

[C26493 NO_CSTYLE_CAST](c26493.md) Nepoužívejte přetypování ve stylu jazyka C. Viz [ C++ základní pokyny typ. 4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).

[C26494 VAR_USE_BEFORE_INIT](c26494.md) Proměnná% Variable% není inicializovaná. Vždy Inicializujte objekt. Viz [ C++ základní pokyny typ. 5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).

[C26495 MEMBER_UNINIT](c26495.md) Proměnná% Variable% není inicializovaná. Vždy inicializujte členskou proměnnou. Viz [ C++ základní pokyny typ. 6](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).

## <a name="bounds-group"></a>Skupina vazeb

[C26446 USE_GSL_AT](c26446.md) Raději použít `gsl::at()` namísto nekontrolovaného operátoru dolního indexu. Viz [ C++ základní pokyny: meze. 4: Nepoužívejte funkce a typy standardní knihovny, které nejsou zaškrtnuté](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#probounds-bounds-safety-profile).

[C26481 NO_POINTER_ARITHMETIC](C26481.md).
Nepoužívejte aritmetický ukazatel. Místo toho použijte rozpětí. Viz [ C++ základní pokyny jsou vázané. 1](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds)

[C26482 NO_DYNAMIC_ARRAY_INDEXING](c26482.md) Indexujte pole pouze pomocí konstantních výrazů. Viz [ C++ základní pokyny jsou vázané. 2](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds)

[C26483 STATIC_INDEX_OUT_OF_RANGE](c26483.md) Hodnota% Value% je mimo hranice (0, vázaných%). proměnné% Variable%. Indexujte pole pouze pomocí konstantních výrazů, které jsou uvnitř mezí pole. Viz [ C++ základní pokyny jsou vázané. 2](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds)

[C26485 NO_ARRAY_TO_POINTER_DECAY](C26485.md) Výraz% expr%: žádné pole pro ukazatel Decay. Viz [ C++ základní pokyny jsou vázané. 3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds)

## <a name="gsl-group"></a>Skupina GSL

[C26445 NO_SPAN_REF](c26445.md) Odkaz na `gsl::span` nebo `std::string_view` může být známkou problému s dobou života.
Viz [ C++ základní pokyny GSL. View: zobrazení](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#gslview-views)

[C26446 USE_GSL_AT](c26446.md) Raději použít `gsl::at()` namísto nekontrolovaného operátoru dolního indexu. Viz [ C++ základní pokyny: meze. 4: Nepoužívejte funkce a typy standardní knihovny, které nejsou zaškrtnuté](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#probounds-bounds-safety-profile).

[C26448 USE_GSL_FINALLY](c26448.md) Zvažte použití `gsl::finally`, pokud je konečná akce určena. Viz [ C++ základní pokyny: GSL. util: Utilities](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-utilities).

[C26449 NO_SPAN_FROM_TEMPORARY](c26449.md) 
 `gsl::span` nebo `std::string_view` vytvořené z dočasného typu budou neplatné při zrušení platnosti dočasného údaje. Viz [ C++ základní pokyny: GSL. View: zobrazení](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#gslview-views).

## <a name="deprecated-warnings"></a>Zastaralá upozornění

Následující upozornění jsou k dispozici v prvotní experimentální sadě pravidel pro kontrolu základních pokynů, ale nyní jsou zastaralé a je možné je bezpečně ignorovat. Upozornění jsou nahrazena upozorněními ze seznamu výše.

- 26412 DEREF_INVALID_POINTER
- 26413 DEREF_NULLPTR
- 26420 ASSIGN_NONOWNER_TO_EXPLICIT_OWNER
- 26421 ASSIGN_VALID_OWNER
- 26422 VALID_OWNER_LEAVING_SCOPE
- 26423 ALLOCATION_NOT_ASSIGNED_TO_OWNER
- 26424 VALID_ALLOCATION_LEAVING_SCOPE
- 26425 ASSIGNING_TO_STATIC
- 26499 NO_LIFETIME_TRACKING

## <a name="see-also"></a>Viz také:
[Použití základních C++ pokynů pro kontrolu](using-the-cpp-core-guidelines-checkers.md)
