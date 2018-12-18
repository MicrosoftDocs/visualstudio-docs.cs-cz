---
title: Doporučené postupy a příklady (poznámky SAL)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: 7922d381d61d40c20fa69859dd091849684723b2
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49899965"
---
# <a name="best-practices-and-examples-sal"></a>Doporučené postupy a příklady (poznámky SAL)
Tady jsou některé způsoby, jak získat maximum z zdrojového kódu anotace jazyka (SAL) a vyhnout se některé běžné problémy.

## <a name="in"></a>\_V\_

Pokud funkce by měl k zápisu do elementu, použijte `_Inout_` místo `_In_`. To platí zejména v případech automatizované převod starší makra na SAL. Před SAL, mnoho programátorů použít makra jako komentáře, makra, které byly pojmenovány `IN`, `OUT`, `IN_OUT`, nebo varianty tyto názvy. Přestože doporučujeme, abyste převedli na SAL tato makra, také doporučujeme vám buďte opatrní při jejich převodu protože kód byl změněn, protože byla zapsána původní prototypu a staré – makro může už odrážejí, co kód dělá. Buďte opatrní hlavně o `OPTIONAL` komentář – makro, protože je často umístěny nesprávně – například na straně nesprávné čárku.

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

## <a name="opt"></a>\_Odhlásit se\_

Pokud volající není povoleno a zajistěte tak předání ukazatel s hodnotou null, použijte `_In_` nebo `_Out_` místo `_In_opt_` nebo `_Out_opt_`. To platí i pro funkce, která ověří jeho parametry a vrátí chybu, pokud má hodnotu NULL, pokud by neměl být. I když mají funkci zkontrolovat její parametr Neočekávaná hodnota NULL a vrátí bez výpadku je vhodné obranné kódování, neznamená, že parametr poznámky můžou být nepovinné typu (`_*Xxx*_opt_`).

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

## <a name="predefensive-and-postdefensive"></a>\_Pre\_obranné\_ a \_příspěvek\_obrany\_

Pokud funkce se zobrazí na hranici vztahu důvěryhodnosti, doporučujeme použít `_Pre_defensive_` poznámky.  "Obrany" modifikátor upravuje určité poznámky a uvést, že v místě volání, rozhraní by měly být porovnány výhradně, ale v těle implementace by měl předpokládat, že může být předány nesprávné parametry. V takovém případě `_In_ _Pre_defensive_` je upřednostňována na hranici vztahu důvěryhodnosti k označení, že i když volající dojde k chybě, pokud se ji pokusí předat hodnotu NULL, tělo funkce bude analyzován, jakoby parametr může mít hodnotu NULL a všechny pokusy o zrušení referenční ukazatele, aniž byste nejdřív kontroly hodnoty NULL budou označeny.  A `_Post_defensive_` poznámky je také k dispozici pro použití v zpětná volání, kde důvěryhodná strana je předpokládá se, že volající a nedůvěryhodný kód je volána kód.

## <a name="outwrites"></a>\_Navýšení kapacity\_zapíše\_

Následující příklad ukazuje běžné zneužití `_Out_writes_`.

```cpp

// Incorrect
void Func1(_Out_writes_(size) CHAR *pb,
    DWORD size
);
```

Poznámka `_Out_writes_` znamená, že máte vyrovnávací paměti. Má `cb` bajtů přidělených s prvním bajtem inicializován při ukončení. Tato poznámka není striktně nesprávné a je vhodné express přidělená velikost. Však neobsahuje žádné informace, kolik prvky jsou inicializovány pomocí funkce.

Další příklad ukazuje tři způsoby správné na plném určení přesnou velikost inicializované část vyrovnávací paměti.

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

## <a name="out-pstr"></a>\_Navýšení kapacity\_ PSTR

Použití `_Out_ PSTR` je téměř vždy nesprávná. To je interpretován jako výstupní parametr, který odkazuje na vyrovnávací paměti pro znaky a je zakončený hodnotou NULL.

```cpp

// Incorrect
void Func1(_Out_ PSTR pFileName, size_t n);

// Correct
void Func2(_Out_writes_(n) PSTR wszFileName, size_t n);
```

Poznámka, jako jsou `_In_ PCSTR` je běžné a užitečné. Odkazuje na vstupní řetězec, který má ukončení hodnotou NULL, protože podmínkou pro `_In_` umožňuje rozpoznávání řetězec zakončený hodnotou NULL.

## <a name="in-wchar-p"></a>\_V\_ WCHAR * p

`_In_ WCHAR* p` říká, že se vstupní ukazatel `p` , která odkazuje na jeden znak. Ale ve většině případů to není pravděpodobně specifikace, která je určena. Místo toho co je pravděpodobně určený je specifikace pole zakončené znakem NULL; k tomuto účelu použijte `_In_ PWSTR`.

```cpp

// Incorrect
void Func1(_In_ WCHAR* wszFileName);

// Correct
void Func2(_In_ PWSTR wszFileName);
```

Chybí správné specifikace ukončení hodnotou NULL je běžné. Použít příslušné `STR` verze, kterou chcete nahradit typu, jak je znázorněno v následujícím příkladu.

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

## <a name="outrange"></a>\_Navýšení kapacity\_rozsahu\_

Pokud parametr je ukazatel a express rozsah hodnota elementu, který je odkazováno na ukazatel, použít `_Deref_out_range_` místo `_Out_range_`. V následujícím příkladu, rozsahu * pcbFilled je vyjádřena, ne pcbFilled.

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

 `_Deref_out_range_(0, cbSize)` není nezbytně nutné pro některé nástroje, protože ho jde odvodit z `_Out_writes_to_(cbSize,*pcbFilled)`, ale je zde uvedené pro úplnost.

## <a name="wrong-context-in-when"></a>V chybném kontextu \_při\_

Další běžnou chybou je pro účely vyhodnocení po stavu předběžné podmínky. V následujícím příkladu `_Requires_lock_held_` je podmínkou.

```cpp

// Incorrect
_When_(return == 0, _Requires_lock_held_(p->cs))
int Func1(_In_ MyData *p, int flag);

// Correct
_When_(flag == 0, _Requires_lock_held_(p->cs))
int Func2(_In_ MyData *p, int flag);
```

 Výraz `result` odkazuje na hodnotu po stavu, která není k dispozici v předběžné stavu.

## <a name="true-in-success"></a>Hodnota TRUE v \_úspěch\_

Pokud funkce uspěje, pokud vrácená hodnota je nenulový, použijte `return != 0` jako podmínka pro úspěch místo `return == TRUE`. NonZero nutně neznamená ekvivalence na skutečnou hodnotu, která poskytuje kompilátor pro `TRUE`. Parametr `_Success_` je výraz a tyto výrazy jsou vyhodnocovány jako ekvivalentní: `return != 0`, `return != false`, `return != FALSE`, a `return` bez parametrů nebo porovnání.

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

## <a name="reference-variable"></a>Odkaz na proměnnou

Pro odkaz na proměnnou, předchozí verzi SAL použít implicitní ukazatel jako cíl poznámky a vyžaduje přidání `__deref` k přidávání poznámek, připojené k odkaz na proměnnou. Tato verze používá samotného objektu a nevyžaduje další `_Deref_`.

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

## <a name="annotations-on-return-values"></a>Poznámky na návratové hodnoty

Následující příklad ukazuje běžný problém v poznámkách návratovou hodnotu.

```cpp

// Incorrect
_Out_opt_ void *MightReturnNullPtr1();

// Correct
_Ret_maybenull_ void *MightReturnNullPtr2();
```

V tomto příkladu `_Out_opt_` říká, že ukazatel může mít hodnotu NULL jako součást předpoklad. Předběžné podmínky však nelze použít návratovou hodnotu. V takovém případě je správný Poznámka `_Ret_maybenull_`.

## <a name="see-also"></a>Viz také:

[Použití poznámek SAL k omezení defektů kódu C/C++](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)
[Princip SAL](../code-quality/understanding-sal.md)
[zadávání poznámek k parametrům funkcí a vrácené hodnoty](../code-quality/annotating-function-parameters-and-return-values.md) 
 [Zadávání poznámek k chování funkcí](../code-quality/annotating-function-behavior.md)
[zadávání poznámek ke strukturám a třídám](../code-quality/annotating-structs-and-classes.md)
[zadávání poznámek o chování při zamykání](../code-quality/annotating-locking-behavior.md) 
 [Určující, kdy a kde se má poznámka použít](../code-quality/specifying-when-and-where-an-annotation-applies.md)
[vnitřní funkce](../code-quality/intrinsic-functions.md)