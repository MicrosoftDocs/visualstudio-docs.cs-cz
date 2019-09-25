---
title: Doporučené postupy a příklady (poznámky SAL)
ms.date: 11/04/2016
ms.topic: conceptual
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: 27570e282c230d4bec47e70aa1bcdd053b75597c
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71236749"
---
# <a name="best-practices-and-examples-sal"></a>Doporučené postupy a příklady (poznámky SAL)
Tady je několik způsobů, jak využít jazyk pro poznámky ke zdrojovému kódu (SAL) a vyhnout se některým běžným problémům.

## <a name="_in_"></a>\_Pro\_

Pokud má být funkce zapsána do prvku, použijte `_Inout_` `_In_`místo. To je zvlášť důležité v případech automatizovaného převodu ze starších maker do SAL. Před Sal, mnoho programátorů použili makra jako komentáře – makra, která byla `IN`pojmenována `IN_OUT`, `OUT`, nebo varianty těchto názvů. I když doporučujeme převést tato makra na SAL, doporučujeme vám, abyste byli opatrní při jejich převodu, protože došlo ke změně kódu od chvíle, kdy byl napsán původní prototyp, a staré makro již nemusí odrážet, co kód dělá. Buďte obzvláště opatrní na `OPTIONAL` makru komentáře, protože je často nesprávně umístěný – například na nesprávné straně čárky.

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

## <a name="_opt_"></a>\_přihlásit\_

Pokud volajícímu není povoleno předat ukazatel s hodnotou null `_In_` , použijte nebo `_Out_` místo `_In_opt_` nebo `_Out_opt_`. To platí i pro funkci, která kontroluje jeho parametry a vrátí chybu, pokud má hodnotu NULL, pokud by neměla být. I když funkce vrátí svůj parametr pro neočekávanou hodnotu NULL a řádným návratem je dobrý postup kódování obrannou linií, neznamená to, že anotace parametru může být volitelného typu (`_*Xxx*_opt_`).

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

## <a name="_pre_defensive_-and-_post_defensive_"></a>\_Pre\_obrannou linií\_ a post\_obrannou linií\_\_

Pokud se funkce objeví na hranici vztahu důvěryhodnosti, doporučujeme použít `_Pre_defensive_` poznámku.  Modifikátor "obrannou linií" mění určité poznámky, což znamená, že v bodě volání by mělo být rozhraní kontrolováno striktně, ale v těle implementace by mělo předpokládat, že mohou být předány nesprávné parametry. V takovém případě `_In_ _Pre_defensive_` je preferován na hranici vztahu důvěryhodnosti, aby označoval, že i když se volající dostane chyba, pokud se pokusí předat hodnotu null, tělo funkce se analyzuje, jako by parametr může mít hodnotu null, a všechny pokusy o zrušení odkazu na ukazatel bez předchozího zaškrtnutí pro hodnotu NULL bude označeno příznakem.  `_Post_defensive_` Poznámka je k dispozici také pro použití ve zpětných voláních, kde se důvěryhodná strana považuje za volající a nedůvěryhodný kód je pojmenovaný kód.

## <a name="_out_writes_"></a>\_Zápisy ven\_\_

Následující příklad ukazuje běžné zneužití `_Out_writes_`.

```cpp

// Incorrect
void Func1(_Out_writes_(size) CHAR *pb,
    DWORD size
);
```

Poznámka `_Out_writes_` znamená, že máte vyrovnávací paměť. Má `cb` přidělené bajty a první bajt inicializovaný při ukončení. Tato poznámka není výhradně chybná a je užitečné vyjádřit přidělenou velikost. Ale nesděluje, kolik prvků je funkcí inicializováno.

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

## <a name="_out_-pstr"></a>\_\_ PSTR

Použití `_Out_ PSTR` je téměř vždy chybné. To je interpretováno jako výstupní parametr, který odkazuje na vyrovnávací paměť znaků a je zakončený hodnotou NULL.

```cpp

// Incorrect
void Func1(_Out_ PSTR pFileName, size_t n);

// Correct
void Func2(_Out_writes_(n) PSTR wszFileName, size_t n);
```

Poznámka jako `_In_ PCSTR` je společná a užitečná. Odkazuje na vstupní řetězec, který má nulové ukončení, protože představa `_In_` umožňuje rozpoznávání řetězce zakončeného hodnotou null.

## <a name="_in_-wchar-p"></a>\_V\_ WCHAR * p

`_In_ WCHAR* p`říká, že je vstupní ukazatel `p` , který odkazuje na jeden znak. Ve většině případů to však není pravděpodobně specifikace, která je určena. Místo toho, co je pravděpodobně určeno, je specifikace pole zakončeného hodnotou NULL; k tomu použijte `_In_ PWSTR`.

```cpp

// Incorrect
void Func1(_In_ WCHAR* wszFileName);

// Correct
void Func2(_In_ PWSTR wszFileName);
```

Není k dispozici správná specifikace ukončení hodnoty NULL je běžné. Použijte odpovídající `STR` verzi k nahrazení typu, jak je znázorněno v následujícím příkladu.

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

## <a name="_out_range_"></a>\_Rozsah\_mimo oblast\_

Pokud je parametr ukazatel a chcete vyjádřit rozsah hodnoty prvku, na který ukazuje ukazatel, použijte `_Deref_out_range_` `_Out_range_`místo. V následujícím příkladu je vyjádřena rozsah * pcbFilled, ne pcbFilled.

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

`_Deref_out_range_(0, cbSize)`není bezpodmínečně nutné pro některé nástroje, protože může být odvozena z `_Out_writes_to_(cbSize,*pcbFilled)`, ale je zde uvedena pro úplnost.

## <a name="wrong-context-in-_when_"></a>Chybný kontext v \_případě, kdy\_

Další běžnou chybou je použití vyhodnocení po stavu pro předběžné podmínky. V následujícím příkladu `_Requires_lock_held_` je předběžnou podmínkou.

```cpp

// Incorrect
_When_(return == 0, _Requires_lock_held_(p->cs))
int Func1(_In_ MyData *p, int flag);

// Correct
_When_(flag == 0, _Requires_lock_held_(p->cs))
int Func2(_In_ MyData *p, int flag);
```

Výraz `result` odkazuje na hodnotu po stavu, která není k dispozici v předběžném stavu.

## <a name="true-in-_success_"></a>Pravda v \_úspěchu\_

Pokud je funkce úspěšná, když je vrácená hodnota nenulová, použijte `return != 0` jako podmínku úspěch `return == TRUE`místo. Nenulové hodnota nutně neznamená rovnocennosti s skutečnou hodnotou, pro `TRUE`kterou kompilátor poskytuje. Parametr `_Success_` na je výraz a následující výrazy jsou vyhodnoceny jako ekvivalentní: `return != false` `return != 0`, `return != FALSE`, a `return` bez parametrů nebo porovnání.

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

V případě referenční proměnné předchozí verze Sal použila implicitní ukazatel jako cíl poznámky a vyžadoval přidání `__deref` do poznámek, které jsou připojeny k referenční proměnné. Tato verze používá samotný objekt a nevyžaduje další `_Deref_`.

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

V tomto příkladu `_Out_opt_` říká, že ukazatel může mít hodnotu null jako součást předběžné podmínky. Pro návratovou hodnotu však nelze použít předběžné podmínky. V takovém případě je `_Ret_maybenull_`správná Poznámka.

## <a name="see-also"></a>Viz také:

[Použití poznámek SAL k snížení míry výskytu závad kódu C/C++](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)  
[Porozumění SAL](../code-quality/understanding-sal.md)  
[Zadávání poznámek k parametrům funkcí a návratovým hodnotám](../code-quality/annotating-function-parameters-and-return-values.md)  
[Zadávání poznámek k chování funkcí](../code-quality/annotating-function-behavior.md)  
[Zadávání poznámek ke strukturám a třídám](../code-quality/annotating-structs-and-classes.md)  
[Zadávání poznámek o chování při zamykání](../code-quality/annotating-locking-behavior.md)  
[Určení, kdy a kde se má poznámka použít](../code-quality/specifying-when-and-where-an-annotation-applies.md)  
[Vnitřní funkce](../code-quality/intrinsic-functions.md)  
