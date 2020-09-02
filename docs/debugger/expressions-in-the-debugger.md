---
title: Výrazy v ladicím programu | Microsoft Docs
ms.date: 03/02/2020
ms.topic: conceptual
f1_keywords:
- vs.debug.expressions
helpviewer_keywords:
- expressions [debugger]
- debugging [Visual Studio], expressions
- expression evaluation, debugger evaluator
- native expression evaluation
- expression evaluators
- debugger, evaluating expressions
- debugging [Visual Studio], expression evaluation
- debugging [Visual Studio], variable evaluation
ms.assetid: 70f9b531-44c7-4d77-980d-5eddbf2bff41
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4ab66f288ad8442b6f2b5aab3499e2c1f3857632
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "89311453"
---
# <a name="expressions-in-the-visual-studio-debugger"></a>Výrazy v ladicím programu sady Visual Studio
Ladicí program sady Visual Studio obsahuje vyhodnocovací filtry výrazů, které fungují při zadání výrazu do dialogového okna **QuickWatch** , v okně **kukátka** nebo v okně **Immediate** . Vyhodnocovací filtry výrazů jsou také v práci v okně **zarážky** a v mnoha dalších místech v ladicím programu.

Následující části popisují omezení vyhodnocení výrazu pro jazyky, které podporuje Visual Studio.

## <a name="f-expressions-are-not-supported"></a>Výrazy F # nejsou podporované.
Výrazy F # se nerozpoznaly. Pokud ladíte kód F #, je nutné přeložit výrazy do syntaxe jazyka C# před vstupem do okna ladicího programu nebo do dialogového okna. Při překladu výrazů z jazyka F # do jazyka C# nezapomeňte, že jazyk C# používá `==` operátor k testování rovnosti, zatímco jazyk F # používá jeden `=` .

## <a name="c-expressions"></a>Výrazy jazyka C++
Informace o použití kontextových operátorů s výrazy v jazyce C++ naleznete v tématu [operátor Context (C++)](../debugger/context-operator-cpp.md).

### <a name="unsupported-expressions-in-c"></a>Nepodporované výrazy v jazyce C++

#### <a name="constructors-destructors-and-conversions"></a>Konstruktory, destruktory a převody
Nelze volat konstruktor nebo destruktor pro objekt, buď explicitně nebo implicitně. Například následující výraz explicitně volá konstruktor a má za následek chybovou zprávu:

```C++
my_date( 2, 3, 1985 )
```

Funkci převodu nelze volat, pokud je cíl převodu třída. Takový převod zahrnuje konstrukci objektu. Například pokud `myFraction` je instance `CFraction` , která definuje operátor funkce pro převod `FixedPoint` , následující výraz má za následek chybu:

```C++
(FixedPoint)myFraction
```

Nemůžete volat operátory New nebo DELETE. Například následující výraz není podporován:

```C++
new Date(2,3,1985)
```

#### <a name="preprocessor-macros"></a>Makra preprocesoru
Makra preprocesoru nejsou v ladicím programu podporována. Například pokud je konstanta `VALUE` deklarována jako: `#define VALUE 3` , nelze použít `VALUE` v okně **kukátko** . Chcete-li se tomuto omezení vyhnout, měli byste nahradit `#define` výčty a funkce, kdykoli to bude možné.

### <a name="using-namespace-declarations"></a>použití deklarací oboru názvů
Deklarace nelze použít `using namespace` .  Aby bylo možné přistupovat k názvu typu nebo proměnné mimo aktuální obor názvů, je nutné použít plně kvalifikovaný název.

### <a name="anonymous-namespaces"></a>Anonymní obory názvů
Anonymní obory názvů nejsou podporované. Pokud máte následující kód, nemůžete přidat `test` do okna Kukátko:

```C++
namespace mars
{
    namespace
    {
        int test = 0;
    }
}
int main()
{
    // Adding a watch on test does not work.
    mars::test++;
    return 0;
}

```

### <a name="using-debugger-intrinsic-functions-to-maintain-state"></a><a name="BKMK_Using_debugger_intrinisic_functions_to_maintain_state"></a> Zachování stavu pomocí vnitřních funkcí ladicího programu
Vnitřní funkce ladicího programu poskytují způsob, jak volat určité funkce jazyka C/C++ ve výrazech beze změny stavu aplikace.

Vnitřní funkce ladicího programu:

- Jsou zaručené jako bezpečné: provádění vnitřní funkce ladicího programu nebude poškodit proces, který se právě ladí.

- Jsou povoleny ve všech výrazech, dokonce i ve scénářích, kde nejsou povoleny vedlejší účinky a vyhodnocení funkce.

- Práce ve scénářích, kde běžné volání funkce nejsou možná, jako je například ladění s minimálním výpisem.

  Vnitřní funkce ladicího programu můžou také lépe vyhodnocovat výrazy. Například `strncmp(str, "asd")` je mnohem snazší psát v podmínkách zarážky, než `str[0] == 'a' && str[1] == 's' && str[2] == 'd'` . )

|Oblast|Vnitřní funkce|
|----------|-------------------------|
|**Délka řetězce**|[strlen, wcslen](https://docs.microsoft.com/cpp/c-runtime-library/reference/strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l), [strnlen, wcsnlen](https://docs.microsoft.com/cpp/c-runtime-library/reference/strnlen-strnlen-s)|
|**Porovnání řetězců**|[strcmp, wcscmp](https://docs.microsoft.com/cpp/c-runtime-library/reference/strcmp-wcscmp-mbscmp), [stricmp, wcsicmp](https://docs.microsoft.com/cpp/c-runtime-library/reference/stricmp-wcsicmp), [_stricmp, _strcmpi, _wcsicmp, _wcscmpi](https://docs.microsoft.com/cpp/c-runtime-library/reference/stricmp-wcsicmp-mbsicmp-stricmp-l-wcsicmp-l-mbsicmp-l), [strncmp, wcsncmp](https://docs.microsoft.com/cpp/c-runtime-library/reference/strncmp-wcsncmp-mbsncmp-mbsncmp-l), [strnicmp, wcsnicmp](https://docs.microsoft.com/cpp/c-runtime-library/reference/strnicmp-wcsnicmp), [_strnicmp, _wcsnicmp](https://docs.microsoft.com/cpp/c-runtime-library/reference/strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l)|
|**Hledání řetězců**|[strchr, wcschr](https://docs.microsoft.com/cpp/c-runtime-library/reference/strchr-wcschr-mbschr-mbschr-l), [memchr, wmemchr](https://docs.microsoft.com/cpp/c-runtime-library/reference/memchr-wmemchr), [strstr, wcsstr](https://docs.microsoft.com/cpp/c-runtime-library/reference/strstr-wcsstr-mbsstr-mbsstr-l)|
|**Win32**|[CoDecodeProxy](https://docs.microsoft.com/windows/win32/api/combaseapi/nf-combaseapi-codecodeproxy), [DecodePointer](https://docs.microsoft.com/previous-versions/bb432242%28v%3dvs.85%29), [GetLastError](https://docs.microsoft.com/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror), [TlsGetValue](https://docs.microsoft.com/windows/win32/api/processthreadsapi/nf-processthreadsapi-tlsgetvalue)|
|**Windows 8**|[RoInspectCapturedStackBackTrace](https://docs.microsoft.com/windows/win32/api/roerrorapi/nf-roerrorapi-roinspectcapturedstackbacktrace), [WindowsCompareStringOrdinal](https://docs.microsoft.com/windows/win32/api/winstring/nf-winstring-windowscomparestringordinal), [WindowsGetStringLen](https://docs.microsoft.com/windows/win32/api/winstring/nf-winstring-windowsgetstringlen), [WindowsGetStringRawBuffer](https://docs.microsoft.com/windows/win32/api/winstring/nf-winstring-windowsgetstringrawbuffer)<br /><br /> Tyto funkce vyžadují, aby byl proces, který se právě ladí, spuštěný v systému Windows 8. Ladění souborů výpisu paměti generovaných ze zařízení se systémem Windows 8 vyžaduje také, aby na počítači se systémem Visual Studio běžel systém Windows 8. Pokud však provádíte ladění zařízení se systémem Windows 8 vzdáleně, může na počítači se systémem Visual Studio běžet systém Windows 7.|
|**Různé**|__log2//vrátí log Base 2 zadaného celého čísla zaokrouhlenou na nejbližší dolní celé číslo.<br /><br />__findNonNull, DecodeHString, DecodeWinRTRestrictedException, DynamicCast, DynamicMemberLookup, GetEnvBlockLength<br /><br />Stdext_HashMap_Int_OperatorBracket_idx Std_UnorderedMap_Int_OperatorBracket_idx<br /><br />ConcurrencyArray_OperatorBracket_idx//concurrency:: Array<>:: operator [index<>] and – operátor (index<>)<br /><br />ConcurrencyArray_OperatorBracket_int//concurrency:: Array<>:: operator (int, int,...)<br /><br />ConcurrencyArray_OperatorBracket_tidx//concurrency:: Array<>:: operator [tiled_index<>] a operator (tiled_index<>)<br /><br />ConcurrencyArrayView_OperatorBracket_idx//concurrency:: array_view<>:: operator [index<>] and – operátor (index<>)<br /><br />ConcurrencyArrayView_OperatorBracket_int//concurrency:: array_view<>:: operator (int, int,...)<br /><br />ConcurrencyArrayView_OperatorBracket_tidx//concurrency:: array_view<>:: operator [tiled_index<>] a operator (tiled_index<>)<br /><br />TreeTraverse_Init//inicializuje nový průchod stromem<br /><br />TreeTraverse_Next//vrátí uzly ve stromové struktuře.<br /><br />TreeTraverse_Skip//přeskočí uzly ve stromové struktuře čeká na vyřízení.|

## <a name="ccli---unsupported-expressions"></a>C++/CLI – nepodporované výrazy

- Přetypování, které zahrnují ukazatele nebo uživatelem definovaná přetypování, nejsou podporovány.

- Porovnání objektů a přiřazení nejsou podporovány.

- Přetížené operátory a přetížené funkce nejsou podporovány.

- Zabalení a rozbalení nejsou podporovaná.

- `Sizeof` operátor není podporován.

## <a name="c---unsupported-expressions"></a>C# – nepodporované výrazy

### <a name="dynamic-objects"></a>Dynamické objekty
Ve výrazech ladicího programu můžete použít proměnné, které jsou staticky zadány jako dynamické. Pokud jsou objekty, které implementují <xref:System.Dynamic.IDynamicMetaObjectProvider> , vyhodnocovány v okno kukátko, je přidán uzel dynamického zobrazení. Uzel dynamického zobrazení zobrazuje členy objektu, ale neumožňuje úpravy hodnot členů.

Následující funkce dynamických objektů nejsou podporovány:

- Složené operátory `+=` , `-=` ,, `%=` `/=` a `*=`

- Mnoho přetypování, včetně číselných přetypování a přetypování argumentů typu

- Volání metody s více než dvěma argumenty

- Třídy getter s více než dvěma argumenty

- Metody setter vlastností s argumenty

- Přiřazení k indexeru

- Logické operátory `&&` a `||`

### <a name="anonymous-methods"></a>Anonymní metody
Vytváření nových anonymních metod se nepodporuje.

## <a name="visual-basic---unsupported-expressions"></a>Visual Basic – nepodporované výrazy

### <a name="dynamic-objects"></a>Dynamické objekty
Ve výrazech ladicího programu můžete použít proměnné, které jsou staticky zadány jako dynamické. Když jsou objekty, které implementují, <xref:System.Dynamic.IDynamicMetaObjectProvider> vyhodnocovány v okno kukátko, je přidán uzel dynamického zobrazení. Uzel dynamického zobrazení zobrazuje členy objektu, ale neumožňuje úpravy hodnot členů.

Následující funkce dynamických objektů nejsou podporovány:

- Složené operátory `+=` , `-=` ,, `%=` `/=` a `*=`

- Mnoho přetypování, včetně číselných přetypování a přetypování argumentů typu

- Volání metody s více než dvěma argumenty

- Třídy getter s více než dvěma argumenty

- Metody setter vlastností s argumenty

- Přiřazení k indexeru

- Logické operátory `&&` a `||`

### <a name="local-constants"></a>Místní konstanty
Místní konstanty nejsou podporovány.

### <a name="import-aliases"></a>Importovat aliasy
Import aliasů není podporován.

### <a name="variable-declarations"></a>Deklarace proměnných
V oknech ladicího programu nelze deklarovat explicitní nové proměnné. V **příkazovém** okně ale můžete přiřadit nové implicitní proměnné. Tyto implicitní proměnné jsou vymezeny na relaci ladění a nejsou přístupné mimo ladicí program. Například příkaz `o = 5` implicitně vytvoří novou proměnnou `o` a přiřadí jí hodnotu 5. Tyto implicitní proměnné jsou typu **Object** , pokud typ nelze odvodit pomocí ladicího programu.

### <a name="unsupported-keywords"></a>Nepodporovaná klíčová slova

- `AddressOf`

- `End`

- `Error`

- `Exit`

- `Goto`

- `On Error`

- `Resume`

- `Return`

- `Select/Case`

- `Stop`

- `SyncLock`

- `Throw`

- `Try/Catch/Finally`

- `With`

- Klíčová slova na úrovni oboru názvů nebo modulu, například `End Sub` nebo `Module` .

## <a name="see-also"></a>Viz také
- [Specifikátory formátu v jazyce C++](../debugger/format-specifiers-in-cpp.md)
- [Kontextový operátor (C++)](../debugger/context-operator-cpp.md)
- [Specifikátory formátu v jazyce C#](../debugger/format-specifiers-in-csharp.md)
- [Pseudoproměnné](../debugger/pseudovariables.md)
