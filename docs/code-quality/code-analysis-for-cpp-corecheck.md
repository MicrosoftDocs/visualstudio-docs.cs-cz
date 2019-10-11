---
title: Referenční dokumentace pro kontrolu požadovaných součástí C++ Core Guidelines
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
ms.openlocfilehash: fc6c7c1dbc5009129e9e793f3b8eea1f7927b2bb
ms.sourcegitcommit: 535ef05b1e553f0fc66082cd2e0998817eb2a56a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "72018447"
---
# <a name="c-core-guidelines-checker-reference"></a>Referenční dokumentace pro kontrolu požadovaných součástí C++ Core Guidelines

Tato část obsahuje seznam upozornění kontrola C++ Core pokyny. Informace o analýze kódu naleznete v tématu [/analyze (Code Analysis)](/cpp/build/reference/analyze-code-analysis) a [Quick Start: Analýza kódu pro C/C++](../code-quality/quick-start-code-analysis-for-c-cpp.md).

> [!NOTE]
> Upozornění patřit do více než jedné skupiny, a ne všechna upozornění mají úplnou referenční téma.

## <a name="owner_pointer-group"></a>OWNER_POINTER skupiny

[C26402 DONT_HEAP_ALLOCATE_MOVABLE_RESULT](C26402.md) vraťte objektu namísto alokovaného haldou vymezený objekt, pokud obsahuje konstruktor přesunu. Zobrazit [C++ Core Guidelines R.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).

[C26403 RESET_OR_DELETE_OWNER](C26403.md) resetovat nebo explicitně odstraňte vlastníka\<T > ukazatele % variable %. Zobrazit [C++ Core Guidelines R.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).

[C26404 DONT_DELETE_INVALID](C26404.md) neodstraňujte owner\<T >, která může být v neplatném stavu. Zobrazit [C++ Core Guidelines R.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).

[C26405 DONT_ASSIGN_TO_VALID](C26405.md) nepřiřazujte k Owner\<T >, která může být v platném stavu. Zobrazit [C++ Core Guidelines R.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).

[C26406 DONT_ASSIGN_RAW_TO_OWNER](C26406.md) nepřiřazujte nezpracovaný ukazatel k Owner\<T >. Zobrazit [C++ Core Guidelines R.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).

[C26407 DONT_HEAP_ALLOCATE_UNNECESSARILY](C26407.md) preferujte vymezené objekty a není haldy nealokovat zbytečně pomocí. Zobrazit [C++ Core Guidelines R.5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-scoped).

[C26429 USE_NOTNULL](C26429.md) Symbol 'symbol %' se nikdy netestuje na hodnotu Null, může být označený jako not_null. Zobrazit [C++ Core Guidelines F.23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).

[C26430 TEST_ON_ALL_PATHS](C26430.md) Symbol 'symbol %' není testovaný na hodnotu Null ve všech cestách. Zobrazit [C++ Core Guidelines F.23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).

[C26431 DONT_TEST_NOTNULL](C26431.md) typ výrazu "% výraz" je už gsl::not_null. Netestujte ho hodnotu Null. Zobrazit [C++ Core Guidelines F.23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).

## <a name="raw_pointer-group"></a>RAW_POINTER skupiny

[C26400 NO_RAW_POINTER_ASSIGNMENT](c26400.md) nepřiřazujte výsledek alokace nebo volání funkce s vlastníkem\<T > k nezpracovanému ukazateli vracet hodnotu; použijte owner\<T > místo toho. Zobrazit [C++ Core Guidelines I.11](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Ri-raw).

[C26401 DONT_DELETE_NON_OWNER](c26401.md) neodstraňujte nezpracovaný ukazatel, který není vlastníkem\<T >. Zobrazit [C++ Core Guidelines I.11](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Ri-raw).

[C26402 DONT_HEAP_ALLOCATE_MOVABLE_RESULT](C26402.md)   vraťte objektu namísto alokovaného haldou vymezený objekt, pokud obsahuje konstruktor přesunu. Zobrazit [C++ Core Guidelines R.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).

[C26408 NO_MALLOC_FREE](C26408.md) vyhne malloc() a free(), upřednostněte verzi nothrow nové s odstranit. Zobrazit [C++ Core Guidelines R.10](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-mallocfree).

[C26409 NO_NEW_DELETE](C26409.md) Vyhněte se volání nové a explicitnímu odstranění, použijte std::make_unique\<T > místo toho. Zobrazit [C++ Core Guidelines R.11](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-newdelete).

[C26429 USE_NOTNULL](C26429.md) Symbol 'symbol %' se nikdy netestuje na hodnotu Null, může být označený jako not_null. Zobrazit [C++ Core Guidelines F.23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).

[C26430 TEST_ON_ALL_PATHS](C26430.md) Symbol 'symbol %' není testovaný na hodnotu Null ve všech cestách. Zobrazit [C++ Core Guidelines F.23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).

[C26431 DONT_TEST_NOTNULL](C26431.md) typ výrazu "% výraz" je už gsl::not_null. Netestujte ho hodnotu Null. Zobrazit [C++ Core Guidelines F.23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).

[C26481 NO_POINTER_ARITHMETIC](C26481.md) nepoužívejte aritmetiku ukazatele. Místo toho použijte span. Zobrazit [Bounds.1 pokyny pro jádro C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds).

[C26485 NO_ARRAY_TO_POINTER_DECAY](C26485.md).
Výraz% expr%: Žádné pole pro ukazatel Decay. Zobrazit [Bounds.3 pokyny pro jádro C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds).

## <a name="unique_pointer-group"></a>UNIQUE_POINTER skupiny

[C26410 NO_REF_TO_CONST_UNIQUE_PTR](C26410.md) parametr % parametr %' je odkaz na `const` jedinečný ukazatel, použijte const T * nebo const T & místo. Zobrazit [C++ Core Guidelines R.32](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-uniqueptrparam).

[C26411 NO_REF_TO_UNIQUE_PTR](C26411.md) parametr % parametr %' je odkazem na jedinečný ukazatel a ho nikdy se nepřeřazuje ani neresetuje, použijte T * nebo T & místo. Zobrazit [C++ Core Guidelines R.33](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-reseat).

[C26414 RESET_LOCAL_SMART_PTR](C26414.md) přesunout, zkopírujte, znovu přiřadit nebo resetujte místní inteligentní ukazatel "symbol %". Zobrazit [C++ Core Guidelines R.5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-scoped).

[C26415 SMART_PTR_NOT_NEEDED](C26415.md) parametr inteligentního ukazatele % symbol %' slouží pouze k přístupu k omezením ukazatele. Použijte T * nebo T & místo. Zobrazit [C++ Core Guidelines R.30](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-smartptrparam).

## <a name="shared_pointer-group"></a>SHARED_POINTER skupiny

[C26414 RESET_LOCAL_SMART_PTR](C26414.md) přesunout, zkopírujte, znovu přiřadit nebo resetujte místní inteligentní ukazatel "symbol %". Zobrazit [C++ Core Guidelines R.5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-scoped).

[C26415 SMART_PTR_NOT_NEEDED](C26415.md) parametr inteligentního ukazatele % symbol %' slouží pouze k přístupu k omezením ukazatele. Použijte T * nebo T & místo. Zobrazit [C++ Core Guidelines R.30](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-smartptrparam).

[C26416 NO_RVALUE_REF_SHARED_PTR](C26416.md) sdílený parametr ukazatele % symbol %' je předána odkazem hodnoty rvalue. Místo toho předejte podle hodnoty. Zobrazit [C++ Core Guidelines R.34](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-sharedptrparam-owner).

[C26417 NO_LVALUE_REF_SHARED_PTR](C26417.md) předány podle odkazu a neresetuje nebo znovu přiřadit sdílený parametr ukazatele % symbol %. Použijte T * nebo T & místo. Zobrazit [C++ Core Guidelines R.35](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-sharedptrparam).

[C26418 NO_VALUE_OR_CONST_REF_SHARED_PTR](C26418.md) sdílený parametr ukazatele % symbol %' není zkopírovaný ani přesunutý. Použijte T * nebo T & místo. Zobrazit [C++ Core Guidelines R.36](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-sharedptrparam-const).

## <a name="declaration-group"></a>DEKLARACE skupiny

[C26426 NO_GLOBAL_INIT_CALLS](C26426.md) globální inicializační výraz volá funkci non-constexpr "% symbol". Zobrazit [C++ Core Guidelines I.22](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#i22-avoid-complex-initialization-of-global-objects).

[C26427 NO_GLOBAL_INIT_EXTERNS](C26427.md) globální inicializační výraz přistupuje k externímu objektu "% symbol". Zobrazit [C++ Core Guidelines I.22](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#i22-avoid-complex-initialization-of-global-objects).

[C26444 NO_UNNAMED_RAII_OBJECTS](c26444.md) nepoužívejte nepojmenované objekty s vlastní konstrukcí a destrukcí. Viz [ES. 84: Nepokoušejte se (zkusit) deklarovat místní proměnnou bez názvu @ no__t-0.

## <a name="class-group"></a>Třída skupiny

[C26432 DEFINE_OR_DELETE_SPECIAL_OPS](C26432.md) Pokud definujete nebo odstraníte jakoukoli výchozí operaci v typu '% symbol %', definujte nebo odstraňte je všechny. Zobrazit [C++ Core Guidelines C.21](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#c21-if-you-define-or-delete-any-default-operation-define-or-delete-them-all).

[C26433 OVERRIDE_EXPLICITLY](c26433.md) funkce "% symbol" by měly být označené 'override'. Viz [C. 128: Virtuální funkce by měly určovat přesně jednu z funkcí Virtual, override nebo Final @ no__t-0.

[C26434 DONT_HIDE_METHODS](C26434.md) funkce 'symbol_1 %' skrývá nevirtuální funkce "% symbol_2". Zobrazit [C++ Core Guidelines C.128](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#c128-virtual-functions-should-specify-exactly-one-of-virtual-override-or-final).

[C26435 SINGLE_VIRTUAL_SPECIFICATION](c26435.md) funkce 'symbol %' by měla určovat právě jeden z 'virtual', 'override' nebo 'final. Viz [C. 128: Virtuální funkce by měly určovat přesně jednu z funkcí Virtual, override nebo Final @ no__t-0.

[C26436 NEED_VIRTUAL_DTOR](C26436.md) typ '% symbol %' s virtuální funkcí potřebuje buď veřejný virtuální, nebo chráněný nevirtuální destruktor. Zobrazit [C++ Core Guidelines C.35](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#c35-a-base-class-destructor-should-be-either-public-and-virtual-or-protected-and-nonvirtual).

[C26443 NO_EXPLICIT_DTOR_OVERRIDE](c26443.md) potlačení destruktoru by neměl používat explicitní 'override' nebo 'virtual' specifikátorů. Viz [C. 128: Virtuální funkce by měly určovat přesně jednu z funkcí Virtual, override nebo Final @ no__t-0.

## <a name="type-group"></a>Typ skupiny

[C26437 DONT_SLICE](C26437.md) nepoužívejte řez. Zobrazit [C++ Core Guidelines ES.63](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#es63-dont-slice).

## <a name="style-group"></a>Styl skupiny

[C26438 NO_GOTO](C26438.md) vyhnout `goto`. Zobrazit [C++ Core Guidelines ES.76](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#es76-avoid-goto).

## <a name="function-group"></a>Skupina – funkce

[C26439 SPECIAL_NOEXCEPT](C26439.md) tento druh funkce nemusí vyvolat. Deklarujte ho `noexcept`. Zobrazit [C++ Core Guidelines F.6](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f6-if-your-function-may-not-throw-declare-it-noexcept).

[C26440 DECLARE_NOEXCEPT](C26440.md) funkce % symbol %' mohou být deklarovány `noexcept`. Zobrazit [C++ Core Guidelines F.6](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f6-if-your-function-may-not-throw-declare-it-noexcept).

[C26447 DONT_THROW_IN_NOEXCEPT](c26447.md) funkce je deklarována **noexcept** ale volá funkci, která může vyvolat výjimky.
Viz pokyny @no__t-C++ 0 Core:  F. 6: Pokud funkce nemůže vyvolat výjimku, deklarujte ji s výjimkou @ no__t-0.

## <a name="concurrency-group"></a>Skupiny SOUBĚŽNOSTI

[C26441 NO_UNNAMED_GUARDS](C26441.md) objekty ochrany musí mít název. Zobrazit [cp.44 pokyny pro jádro C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#cp44-remember-to-name-your-lock_guards-and-unique_locks).

## <a name="const-group"></a>CONST skupiny

[C26460 USE_CONST_REFERENCE_ARGUMENTS](c26460.md) argument odkazu '% argumentu %' pro funkci '% funkce' může být označený jako `const`. Zobrazit [con.3 pokyny pro jádro C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rconst-ref).

[C26461 USE_CONST_POINTER_ARGUMENTS](c26461.md): Argument ukazatele% argumentu% pro funkci% Function% může být označený jako ukazatel na `const`. Zobrazit [con.3 pokyny pro jádro C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rconst-ref).

[C26462 USE_CONST_POINTER_FOR_VARIABLE](c26462.md) hodnota, na které odkazuje % variable % je přiřazená jen jednou, označte ji jako ukazatel na `const`. Zobrazit [con.4 pokyny pro jádro C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con4-use-const-to-define-objects-with-values-that-do-not-change-after-construction).

[C26463 USE_CONST_FOR_ELEMENTS](c26463.md) prvků pole "pole %" jsou přiřazené pouze jednou, označte tyto prvky `const`. Zobrazit [con.4 pokyny pro jádro C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con4-use-const-to-define-objects-with-values-that-do-not-change-after-construction).

[C26464 USE_CONST_POINTER_FOR_ELEMENTS](c26464.md) hodnoty odkazované elementy pole "pole %" jsou přiřazené pouze jednou, označte prvky jako ukazatele na `const`. Zobrazit [con.4 pokyny pro jádro C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con4-use-const-to-define-objects-with-values-that-do-not-change-after-construction).

[C26496 USE_CONST_FOR_VARIABLE](c26496.md) % variable % proměnná je přiřazená jen jednou, označte ji jako `const`. Zobrazit [con.4 pokyny pro jádro C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con4-use-const-to-define-objects-with-values-that-do-not-change-after-construction).

[C26497 USE_CONSTEXPR_FOR_FUNCTION](c26497.md) této funkce funkce % by mohla být označená jako `constexpr` Pokud se vyžaduje vyhodnocení za kompilace. Zobrazit [C++ Core Guidelines F.4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rf-constexpr).

[C26498 USE_CONSTEXPR_FOR_FUNCTIONCALL](c26498.md) můžete použít tuto funkci volání % funkce `constexpr` Pokud se vyžaduje vyhodnocení za kompilace. Zobrazit [con.5 pokyny pro jádro C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rconst-constexpr).

## <a name="type-group"></a>Typ skupiny

[C26465 NO_CONST_CAST_UNNECESSARY](c26465.md) nepoužívejte `const_cast` k přetypování `const`. `const_cast` není vyžadována. tímto převodem se se neodebere konstantnost nebo proměnlivost. Zobrazit [Type.3 pokyny pro jádro C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-constcast).

[C26466 NO_STATIC_DOWNCAST_POLYMORPHIC](c26466.md) nepoužívejte `static_cast` přetypování dolů. Přetypování z polymorfního typu by mělo používat dynamic_cast. Zobrazit [Type.2 pokyny pro jádro C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-downcast).

[C26471 NO_REINTERPRET_CAST_FROM_VOID_PTR](c26471.md) nepoužívejte `reinterpret_cast`. Přetypování z void * může používat `static_cast`. Zobrazit [Type.1 pokyny pro jádro C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-reinterpretcast).

[C26472 NO_CASTS_FOR_ARITHMETIC_CONVERSION](C26472.md) nepoužívejte `static_cast` pro aritmetické převody. Použijte inicializaci složenými, gsl::narrow_cast nebo gsl::narow. Zobrazit [Type.1 pokyny pro jádro C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-reinterpretcast).

[C26473 NO_IDENTITY_CAST](C26473.md) nepoužívejte přetypování mezi typy ukazatelů, kde stejný jsou zdrojového a cílového typu. Zobrazit [Type.1 pokyny pro jádro C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-reinterpretcast).

[C26474 NO_IMPLICIT_CAST](C26474.md) nepoužívejte přetypování mezi typy ukazatelů, když převod může být implicitní. Zobrazit [Type.1 pokyny pro jádro C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-reinterpretcast).

[C26475 NO_FUNCTION_STYLE_CASTS](C26475.md) nepoužívejte stylu funkce přetypování C-CAST. Zobrazit [C++ Core Guidelines ES.49](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#es49-if-you-must-use-a-cast-use-a-named-cast).

[C26490 NO_REINTERPRET_CAST](c26490.md) nepoužívejte `reinterpret_cast`. Zobrazit [Type.1 pokyny pro jádro C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).

[C26491 NO_STATIC_DOWNCAST](c26490.md) nepoužívejte `static_cast` přetypování dolů. Zobrazit [Type.2 pokyny pro jádro C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).

[C26492 NO_CONST_CAST](c26492.md) nepoužívejte `const_cast` k přetypování `const`. Zobrazit [Type.3 pokyny pro jádro C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).

[C26493 NO_CSTYLE_CAST](c26493.md) nepoužívejte přetypování C-style. Zobrazit [C++ jader Type.4 pokyny](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).

[C26494 VAR_USE_BEFORE_INIT](c26494.md) % variable % proměnná není inicializovaná. Vždy objekt inicializujte. Zobrazit [Type.5 pokyny pro jádro C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).

[C26495 MEMBER_UNINIT](c26495.md) % variable % proměnná není inicializovaná. Vždy proměnnou člena inicializujte. Zobrazit [Type.6 pokyny pro jádro C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).

## <a name="bounds-group"></a>Skupiny hranic

[C26446 USE_GSL_AT](c26446.md) dávají přednost používání `gsl::at()` místo Nekontrolovaná operátor dolního indexu. Viz pokyny @no__t-C++ 0 Core:  Meze. 4: Nepoužívejte funkce a typy standardní knihovny, které nejsou vázané na hranice-Checked @ no__t-0.

[C26481 NO_POINTER_ARITHMETIC](C26481.md).
Nepoužívejte aritmetiku ukazatele. Místo toho použijte span. Zobrazit [Bounds.1 pokyny pro jádro C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds)

[C26482 NO_DYNAMIC_ARRAY_INDEXING](c26482.md) pouze Indexujte pole pomocí výrazů konstant. Zobrazit [Bounds.2 pokyny pro jádro C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds)

[C26483 STATIC_INDEX_OUT_OF_RANGE](c26483.md) hodnotu % hodnotu % je mimo rozsah (0, vázaná %) proměnné % variable %. Budou indexovat jen pomocí výrazů konstant, které jsou uvnitř mezí pole. Zobrazit [Bounds.2 pokyny pro jádro C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds)

[C26485 NO_ARRAY_TO_POINTER_DECAY](C26485.md) Výraz% expr%: Žádné pole pro ukazatel Decay. Zobrazit [Bounds.3 pokyny pro jádro C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds)

## <a name="gsl-group"></a>Skupiny GSL

[C26445 NO_SPAN_REF](c26445.md) odkaz na `gsl::span` nebo `std::string_view` může být známkou problému s dobou života.
Viz pokyny @no__t-C++ 0 Core GSL. View: Zobrazení @ no__t-0

[C26446 USE_GSL_AT](c26446.md) dávají přednost používání `gsl::at()` místo Nekontrolovaná operátor dolního indexu. Viz pokyny @no__t-C++ 0 Core:  Meze. 4: Nepoužívejte funkce a typy standardní knihovny, které nejsou vázané na hranice-Checked @ no__t-0.

[C26448 USE_GSL_FINALLY](c26448.md) Pokud je konečná akce určena, zvažte použití `gsl::finally`. Viz pokyny @no__t-C++ 0 Core:  GSL.util: Pomůcky @ no__t-0.

[C26449 NO_SPAN_FROM_TEMPORARY](c26449.md) 
 `gsl::span` nebo `std::string_view` vytvořené z dočasného budou mít neplatná při dočasný zneplatněna. Viz pokyny @no__t-C++ 0 Core: GSL. View: Zobrazení @ no__t-0.

## <a name="deprecated-warnings"></a>Upozornění na zastaralé

Následující upozornění jsou k dispozici v rané fázi sadě experimentální pravidel z požadovaných součástí základní pokyny, ale jsou už zastaralé a můžete bezpečně ignorovat. Upozornění jsou nahrazena sadou upozornění ze seznamu výše.

- 26412 DEREF_INVALID_POINTER
- 26413 DEREF_NULLPTR
- 26420 ASSIGN_NONOWNER_TO_EXPLICIT_OWNER
- 26421 ASSIGN_VALID_OWNER
- 26422 VALID_OWNER_LEAVING_SCOPE
- 26423 ALLOCATION_NOT_ASSIGNED_TO_OWNER
- 26424 VALID_ALLOCATION_LEAVING_SCOPE
- 26425 ASSIGNING_TO_STATIC
- 26499 NO_LIFETIME_TRACKING

## <a name="see-also"></a>Viz také
[Pomocí pokynů šachovnice C++ Core](using-the-cpp-core-guidelines-checkers.md)
