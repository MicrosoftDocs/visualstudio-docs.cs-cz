---
title: Doporučené postupy a příklady (poznámky SAL)
ms.date: 11/04/2016
ms.topic: conceptual
author: mikeblome
ms.author: mblome
manager: markl
ms.workload:
- multiple
ms.openlocfilehash: ccb18a704c2e8a2c185d3751483736631b0bba68
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72448640"
---
# <a name="best-practices-and-examples-sal"></a>Doporučené postupy a příklady (poznámky SAL)
Tady je několik způsobů, jak využít jazyk pro poznámky ke zdrojovému kódu (SAL) a vyhnout se některým běžným problémům.

## <a name="_in_"></a>@no__t – 0In @ no__t-1

Pokud má být funkce zapsána do prvku, použijte `_Inout_` místo `_In_`. To je zvlášť důležité v případech automatizovaného převodu ze starších maker do SAL. Před SAL, mnoho programátorů použili makra jako komentáře – makra s názvem `IN`, `OUT`, `IN_OUT` nebo varianty těchto názvů. I když doporučujeme převést tato makra na SAL, doporučujeme vám, abyste byli opatrní při jejich převodu, protože došlo ke změně kódu od chvíle, kdy byl napsán původní prototyp, a staré makro již nemusí odrážet, co kód dělá. Buďte obzvláště opatrní na makru s komentářem `OPTIONAL`, protože je často nesprávně umístěný – například na nesprávné straně čárky.

```cpp

// Incorrect
void Func1(_In_ int *p1)
{
    if (p1 == NULL)
        return;

    *p1 = 1;
}

// Correct
void Func2(_Inout_ PCHAR p1)
{
    if (p1 == NULL)
        return;

    *p1 = 1;
}
```

## <a name="_opt_"></a>@no__t – 0opt @ no__t-1

Pokud volajícímu nepovoluje předat ukazatel s hodnotou null, použijte `_In_` nebo `_Out_` namísto `_In_opt_` nebo `_Out_opt_`. To platí i pro funkci, která kontroluje jeho parametry a vrátí chybu, pokud má hodnotu NULL, pokud by neměla být. I když funkce vrátí svůj parametr pro neočekávanou hodnotu NULL a řádným návratem je dobrý postup kódování obrannou linií, neznamená to, že anotace parametru může být volitelného typu (`_*Xxx*_opt_`).

```cpp

// Incorrect
void Func1(_Out_opt_ int *p1)
{
    *p = 1;
}

// Correct
void Func2(_Out_ int *p1)
{
    *p = 1;
}
```

## <a name="_pre_defensive_-and-_post_defensive_"></a>\_Pre @ no__t-1defensive @ no__t-2 a \_Post @ no__t-4defensive @ no__t-5

Pokud se funkce objeví na hranici vztahu důvěryhodnosti, doporučujeme použít `_Pre_defensive_` anotace.  Modifikátor "obrannou linií" mění určité poznámky, což znamená, že v bodě volání by mělo být rozhraní kontrolováno striktně, ale v těle implementace by mělo předpokládat, že mohou být předány nesprávné parametry. V takovém případě je `_In_ _Pre_defensive_` upřednostňována na hranici vztahu důvěryhodnosti, což znamená, že i když se volající dostane chyba, pokud se pokusí předat hodnotu NULL, text funkce se analyzuje, jako by parametr mohl mít hodnotu NULL, a všechny pokusy o zrušení odkazu na ukazatel bez předchozího zaškrtnutí pro hodnotu NULL bude označeno příznakem.  K dispozici je také anotace `_Post_defensive_`, která se používá ve zpětných voláních, kde se považuje důvěryhodná strana jako volající a nedůvěryhodný kód je pojmenovaný kód.

## <a name="_out_writes_"></a>\_Out @ no__t-1writes @ no__t-2

Následující příklad ukazuje běžné zneužití `_Out_writes_`.

```cpp

// Incorrect
void Func1(_Out_writes_(size) CHAR *pb,
    DWORD size
);
```

Poznámka `_Out_writes_` znamená, že máte vyrovnávací paměť. Má `cb` přidělených bajtů a první bajt inicializovaný při ukončení. Tato poznámka není výhradně chybná a je užitečné vyjádřit přidělenou velikost. Ale nesděluje, kolik prvků je funkcí inicializováno.

Následující příklad ukazuje tři správné způsoby, jak plně určit přesnou velikost inicializované části vyrovnávací paměti.

```cpp

// Correct
void Func1(_Out_writes_to_(size, *pCount) CHAR *pb,
    DWORD size,
    PDWORD pCount
);

void Func2(_Out_writes_all_(size) CHAR *pb,
    DWORD size
);

void Func3(_Out_writes_(size) PSTR pb,
    DWORD size
);
```

## <a name="_out_-pstr"></a>\_Out @ no__t-1 PSTR

Použití `_Out_ PSTR` je téměř vždy chybné. To je interpretováno jako výstupní parametr, který odkazuje na vyrovnávací paměť znaků a je zakončený hodnotou NULL.

```cpp

// Incorrect
void Func1(_Out_ PSTR pFileName, size_t n);

// Correct
void Func2(_Out_writes_(n) PSTR wszFileName, size_t n);
```

Poznámka, jako je například `_In_ PCSTR`, je společná a užitečná. Odkazuje na vstupní řetězec, který má nulové ukončení, protože představa `_In_` umožňuje rozpoznání řetězce zakončeného hodnotou NULL.

## <a name="_in_-wchar-p"></a>\_In @ no__t-1 WCHAR * p

`_In_ WCHAR* p` znamená, že existuje vstupní ukazatel `p`, který odkazuje na jeden znak. Ve většině případů to však není pravděpodobně specifikace, která je určena. Místo toho, co je pravděpodobně určeno, je specifikace pole zakončeného hodnotou NULL; k tomu použijte `_In_ PWSTR`.

```cpp

// Incorrect
void Func1(_In_ WCHAR* wszFileName);

// Correct
void Func2(_In_ PWSTR wszFileName);
```

Není k dispozici správná specifikace ukončení hodnoty NULL je běžné. Použijte příslušnou verzi `STR` k nahrazení typu, jak je znázorněno v následujícím příkladu.

```cpp

// Incorrect
BOOL StrEquals1(_In_ PCHAR p1, _In_ PCHAR p2)
{
    return strcmp(p1, p2) == 0;
}

// Correct
BOOL StrEquals2(_In_ PSTR p1, _In_ PSTR p2)
{
    return strcmp(p1, p2) == 0;
}
```

## <a name="_out_range_"></a>\_Out @ no__t-1range @ no__t-2

Pokud je parametr ukazatel a chcete vyjádřit rozsah hodnoty prvku, na který ukazuje ukazatel, použijte `_Deref_out_range_` namísto `_Out_range_`. V následujícím příkladu je vyjádřena rozsah * pcbFilled, ne pcbFilled.

```cpp

// Incorrect
void Func1(
    _Out_writes_bytes_to_(cbSize, *pcbFilled) BYTE *pb,
    DWORD cbSize,
    _Out_range_(0, cbSize) DWORD *pcbFilled
);

// Correct
void Func2(
    _Out_writes_bytes_to_(cbSize, *pcbFilled) BYTE *pb,
    DWORD cbSize,
    _Deref_out_range_(0, cbSize) _Out_ DWORD *pcbFilled
);
```

`_Deref_out_range_(0, cbSize)` není bezpodmínečně nutné pro některé nástroje, protože může být odvozena z `_Out_writes_to_(cbSize,*pcbFilled)`, ale je zde uvedena pro úplnost.

## <a name="wrong-context-in-_when_"></a>Chybný kontext v \_When @ no__t-1

Další běžnou chybou je použití vyhodnocení po stavu pro předběžné podmínky. V následujícím příkladu je `_Requires_lock_held_` Předběžná podmínka.

```cpp

// Incorrect
_When_(return == 0, _Requires_lock_held_(p->cs))
int Func1(_In_ MyData *p, int flag);

// Correct
_When_(flag == 0, _Requires_lock_held_(p->cs))
int Func2(_In_ MyData *p, int flag);
```

Výraz `result` odkazuje na hodnotu po stavu, která není k dispozici v předběžném stavu.

## <a name="true-in-_success_"></a>TRUE v \_Success @ no__t-1

Pokud je funkce úspěšná, když je vrácená hodnota nenulová, místo `return == TRUE` použijte `return != 0` jako podmínku úspěch. Nenulové hodnota nutně neznamená rovnocennosti skutečné hodnoty, kterou kompilátor poskytuje pro `TRUE`. Parametr pro `_Success_` je výraz a následující výrazy jsou vyhodnoceny jako ekvivalentní: `return != 0`, `return != false`, `return != FALSE` a `return` bez parametrů nebo porovnání.

```cpp

// Incorrect
_Success_(return == TRUE, _Acquires_lock_(*lpCriticalSection))
BOOL WINAPI TryEnterCriticalSection(
  _Inout_ LPCRITICAL_SECTION lpCriticalSection
);

// Correct
_Success_(return != 0, _Acquires_lock_(*lpCriticalSection))
BOOL WINAPI TryEnterCriticalSection(
  _Inout_ LPCRITICAL_SECTION lpCriticalSection
);
```

## <a name="reference-variable"></a>Referenční proměnná

V případě referenční proměnné předchozí verze SAL použila implicitní ukazatel jako cíl poznámky a vyžadoval přidání `__deref` k poznámkám, které jsou připojeny k referenční proměnné. Tato verze používá samotný objekt a nevyžaduje další `_Deref_`.

```cpp

// Incorrect
void Func1(
    _Out_writes_bytes_all_(cbSize) BYTE *pb,
    _Deref_ _Out_range_(0, 2) _Out_ DWORD &cbSize
);

// Correct
void Func2(
    _Out_writes_bytes_all_(cbSize) BYTE *pb,
    _Out_range_(0, 2) _Out_ DWORD &cbSize
);
```

## <a name="annotations-on-return-values"></a>Poznámky k návratovým hodnotám

Následující příklad ukazuje běžný problém v poznámkách k návratovým hodnotám.

```cpp

// Incorrect
_Out_opt_ void *MightReturnNullPtr1();

// Correct
_Ret_maybenull_ void *MightReturnNullPtr2();
```

V tomto příkladu `_Out_opt_` říká, že ukazatel může mít hodnotu NULL jako součást předpodmínky. Pro návratovou hodnotu však nelze použít předběžné podmínky. V takovém případě je správná Poznámka `_Ret_maybenull_`.

## <a name="see-also"></a>Viz také:

[Použití poznámek SAL k snížení míry výskytu závad kódu C/C++](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)  
[Porozumění SAL](../code-quality/understanding-sal.md)  
[Zadávání poznámek k parametrům funkcí a návratovým hodnotám](../code-quality/annotating-function-parameters-and-return-values.md)  
[Zadávání poznámek k chování funkcí](../code-quality/annotating-function-behavior.md)  
[Zadávání poznámek ke strukturám a třídám](../code-quality/annotating-structs-and-classes.md)  
[Zadávání poznámek o chování při zamykání](../code-quality/annotating-locking-behavior.md)  
[Určení, kdy a kde se má poznámka použít](../code-quality/specifying-when-and-where-an-annotation-applies.md)  
[Vnitřní funkce](../code-quality/intrinsic-functions.md)
