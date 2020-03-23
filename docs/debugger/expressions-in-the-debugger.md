---
title: Výrazy v ladicím programu | Dokumenty společnosti Microsoft
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
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302166"
---
# <a name="expressions-in-the-visual-studio-debugger"></a>Výrazy v ladicím programu sady Visual Studio
Ladicí program sady Visual Studio obsahuje vyhodnocení výrazů, které fungují při zadání výrazu v dialogovém okně **QuickWatch,** okně **Kukátka** nebo **V okně Okamžité.** Vyhodnocení výrazu jsou také v práci v okně **Zarážky** a mnoho dalších míst v ladicím programu.

Následující části popisují omezení vyhodnocení výrazů pro jazyky podporované visual studio.

## <a name="f-expressions-are-not-supported"></a>Výrazy Jazyka F# nejsou podporovány.
Výrazy Jazyka F# nejsou rozpoznány. Pokud ladíte kód F#, musíte před zadáním výrazů do okna ladicího programu nebo dialogového okna přeložit výrazy do syntaxe jazyka C#. Při překladu výrazů z Jazyka F# do jazyka C# `==` nezapomeňte, že c# používá operátor `=`k testování rovnosti, zatímco F# používá jeden .

## <a name="c-expressions"></a>Výrazy jazyka C++
Informace o použití kontextových operátorů s výrazy v jazyce C++ naleznete v [tématu Context Operator (C++).](../debugger/context-operator-cpp.md)

### <a name="unsupported-expressions-in-c"></a>Nepodporované výrazy v jazyce C++

#### <a name="constructors-destructors-and-conversions"></a>Konstruktory, destruktory a převody
Nelze volat konstruktor nebo destruktor pro objekt, explicitně nebo implicitně. Například následující výraz explicitně volá konstruktor a výsledkem je chybová zpráva:

```C++
my_date( 2, 3, 1985 )
```

Funkci převodu nelze volat, pokud je cílem převodu třída. Taková konverze zahrnuje konstrukci objektu. Například pokud `myFraction` je instance `CFraction`, která definuje operátor `FixedPoint`funkce převodu , následující výraz má za následek chybu:

```C++
(FixedPoint)myFraction
```

Nelze volat nové nebo odstranit operátory. Například následující výraz není podporován:

```C++
new Date(2,3,1985)
```

#### <a name="preprocessor-macros"></a>Preprocesorová makra
Preprocesorová makra nejsou v ladicím programu podporována. `VALUE` Například pokud konstanta je `#define VALUE 3`deklarována jako: , nelze použít `VALUE` v okně **kukátko.** Chcete-li se tomuto `#define`omezení vyhnout, měli byste nahradit 's s výčty a funkce, kdykoli je to možné.

### <a name="using-namespace-declarations"></a>použití deklarací oboru názvů
Deklarace `using namespace` nelze použít.  Chcete-li získat přístup k názvu nebo proměnné mimo aktuální obor názvů, musíte použít plně kvalifikovaný název.

### <a name="anonymous-namespaces"></a>Anonymní obory názvů
Anonymní obory názvů nejsou podporovány. Pokud máte následující kód, nelze `test` přidat do okna kukátka:

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

### <a name="using-debugger-intrinsic-functions-to-maintain-state"></a><a name="BKMK_Using_debugger_intrinisic_functions_to_maintain_state"></a>Použití vnitřních funkcí ladicího programu k udržení stavu
Vnitřní funkce ladicího programu poskytují způsob, jak volat určité funkce jazyka C/C++ ve výrazech bez změny stavu aplikace.

Ladicí program vnitřní funkce:

- Jsou zaručeny jako bezpečné: spuštění ladicího programu vnitřní funkce nepoškodí proces, který je laděn.

- Jsou povoleny ve všech výrazech , a to i ve scénářích, kde nejsou povoleny vedlejší účinky a vyhodnocení funkce.

- Práce ve scénářích, kde nejsou možné volání pravidelné funkce, jako je například ladění minidump.

  Dedebační program vnitřní funkce může také vyhodnotit výrazy pohodlnější. Například `strncmp(str, "asd")` je mnohem jednodušší psát v podmínce zarážky než `str[0] == 'a' && str[1] == 's' && str[2] == 'd'`. )

|Oblast|Vnitřní funkce|
|----------|-------------------------|
|**Délka řetězce**|[strlen, wcslen](https://docs.microsoft.com/cpp/c-runtime-library/reference/strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l), [strnlen, wcsnlen](https://docs.microsoft.com/cpp/c-runtime-library/reference/strnlen-strnlen-s)|
|**Porovnání řetězců**|[strcmp, wcscmp](https://docs.microsoft.com/cpp/c-runtime-library/reference/strcmp-wcscmp-mbscmp), [stricmp, wcsicmp](https://docs.microsoft.com/cpp/c-runtime-library/reference/stricmp-wcsicmp), [_stricmp, _strcmpi, _wcsicmp, _wcscmpi](https://docs.microsoft.com/cpp/c-runtime-library/reference/stricmp-wcsicmp-mbsicmp-stricmp-l-wcsicmp-l-mbsicmp-l), [strncmp, wcsncmp](https://docs.microsoft.com/cpp/c-runtime-library/reference/strncmp-wcsncmp-mbsncmp-mbsncmp-l), [strnicmp, wcsnicmp](https://docs.microsoft.com/cpp/c-runtime-library/reference/strnicmp-wcsnicmp), [_strnicmp, _wcsnicmp](https://docs.microsoft.com/cpp/c-runtime-library/reference/strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l)|
|**Hledání v řetězci**|[strchr, wcschr](https://docs.microsoft.com/cpp/c-runtime-library/reference/strchr-wcschr-mbschr-mbschr-l), [memchr, wmemchr](https://docs.microsoft.com/cpp/c-runtime-library/reference/memchr-wmemchr), [strstr, wcsstr](https://docs.microsoft.com/cpp/c-runtime-library/reference/strstr-wcsstr-mbsstr-mbsstr-l)|
|**Win32**|[CoDecodeProxy](https://docs.microsoft.com/windows/win32/api/combaseapi/nf-combaseapi-codecodeproxy), [DecodePointer](https://docs.microsoft.com/previous-versions/bb432242%28v%3dvs.85%29), [GetLastError](https://docs.microsoft.com/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror), [TlsGetValue](https://docs.microsoft.com/windows/win32/api/processthreadsapi/nf-processthreadsapi-tlsgetvalue)|
|**Windows 8**|[RoInspectCapturedStackBackTrace](https://docs.microsoft.com/windows/win32/api/roerrorapi/nf-roerrorapi-roinspectcapturedstackbacktrace), [WindowsCompareStringOrdinal](https://docs.microsoft.com/windows/win32/api/winstring/nf-winstring-windowscomparestringordinal), [WindowsGetStringLen](https://docs.microsoft.com/windows/win32/api/winstring/nf-winstring-windowsgetstringlen), [WindowsGetStringRawBuffer](https://docs.microsoft.com/windows/win32/api/winstring/nf-winstring-windowsgetstringrawbuffer)<br /><br /> Tyto funkce vyžadují proces, který je právě laděn, aby byl spuštěn v systému Windows 8. Ladění souborů výpisu generovaných ze zařízení se systémem Windows 8 také vyžaduje, aby počítač Visual Studio se systémem Windows 8. Pokud však vzdáleně ladíte zařízení se systémem Windows 8, může být v počítači sady Visual Studio spuštěn systém Windows 7.|
|**Různé**|__log2 // Vrátí základnu protokolu 2 zadaného celého čísla zaokrouhlenou na nejbližší nižší celé číslo.<br /><br />__findNonNull, DecodeHString, DecodeWinRTRestrictedException, DynamicCast, DynamicMemberLookup, GetEnvBlockLength<br /><br />Stdext_HashMap_Int_OperatorBracket_idx, Std_UnorderedMap_Int_OperatorBracket_idx<br /><br />ConcurrencyArray_OperatorBracket_idx // Souběžnost::pole<>::operátor[index<>] a operátor (index<>)<br /><br />ConcurrencyArray_OperatorBracket_int // Souběžnost::pole<>::operátor(int, int, ...)<br /><br />ConcurrencyArray_OperatorBracket_tidx // Souběžnost::maticové<>::operátor[tiled_index<>] a operátor (tiled_index<>)<br /><br />ConcurrencyArrayView_OperatorBracket_idx // Souběžnost::array_view<>::operátor[index<>] a operátor(index<>)<br /><br />ConcurrencyArrayView_OperatorBracket_int // Souběžnost::array_view<>::operátor(int, int, ...)<br /><br />ConcurrencyArrayView_OperatorBracket_tidx // Souběžnost::array_view<>::operátor[tiled_index<>] a operátor (<> tiled_index)<br /><br />TreeTraverse_Init // Inicializuje nový strom traversal<br /><br />TreeTraverse_Next // Vrátí uzly ve stromu.<br /><br />TreeTraverse_Skip // Přeskočí uzly v čekajícím průchodu stromu'|

## <a name="ccli---unsupported-expressions"></a>C++/CLI - nepodporované výrazy

- Přetypová dlažem, které zahrnují ukazatele nebo uživatelem definované přetypovače, nejsou podporovány.

- Porovnání objektů a přiřazení nejsou podporovány.

- Přetížené operátory a přetížené funkce nejsou podporovány.

- Zabalení a rozbalení nejsou podporovány.

- `Sizeof`operátor není podporován.

## <a name="c---unsupported-expressions"></a>C# - nepodporované výrazy

### <a name="dynamic-objects"></a>Dynamické objekty
Proměnné můžete použít ve výrazech ladicího programu, které jsou staticky zadány jako dynamické. Když jsou <xref:System.Dynamic.IDynamicMetaObjectProvider> objekty, které implementují, vyhodnoceny v okně Kukátko, je přidán uzel dynamického zobrazení. Uzel Dynamické zobrazení zobrazuje členy objektu, ale neumožňuje úpravy hodnot členů.

Následující funkce dynamických objektů nejsou podporovány:

- Složené hospodářské `+=` `-=`subjekty , , `%=`, `/=`a`*=`

- Mnoho přetypování, včetně číselných přetypování a přetypování argumentů typu

- Volání metody s více než dvěma argumenty

- Getters vlastností s více než dvěma argumenty

- Nastavení vlastností s argumenty

- Přiřazení indexeru

- Logické operátory `&&` a`||`

### <a name="anonymous-methods"></a>Anonymní metody
Vytváření nových anonymních metod není podporováno.

## <a name="visual-basic---unsupported-expressions"></a>Visual Basic - nepodporované výrazy

### <a name="dynamic-objects"></a>Dynamické objekty
Proměnné můžete použít ve výrazech ladicího programu, které jsou staticky zadány jako dynamické. Když jsou objekty, které implementují <xref:System.Dynamic.IDynamicMetaObjectProvider> jsou vyhodnoceny v okně kukátka, je přidán uzel dynamického zobrazení. Uzel Dynamické zobrazení zobrazuje členy objektu, ale neumožňuje úpravy hodnot členů.

Následující funkce dynamických objektů nejsou podporovány:

- Složené hospodářské `+=` `-=`subjekty , , `%=`, `/=`a`*=`

- Mnoho přetypování, včetně číselných přetypování a přetypování argumentů typu

- Volání metody s více než dvěma argumenty

- Getters vlastností s více než dvěma argumenty

- Nastavení vlastností s argumenty

- Přiřazení indexeru

- Logické operátory `&&` a`||`

### <a name="local-constants"></a>Místní konstanty
Místní konstanty nejsou podporovány.

### <a name="import-aliases"></a>Importovat aliasy
Aliasy importu nejsou podporovány.

### <a name="variable-declarations"></a>Deklarace proměnných
V oknech ladicího programu nelze deklarovat explicitní nové proměnné. Můžete však přiřadit nové implicitní proměnné uvnitř okna **Okamžité.** Tyto implicitní proměnné jsou vymezeny na relaci ladění a nejsou přístupné mimo ladicí program. Například příkaz `o = 5` implicitně vytvoří novou `o` proměnnou a přiřadí jí hodnotu 5. Tyto implicitní proměnné jsou typu **Object,** pokud typ lze odvodit ladicí program.

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

- Klíčová slova oboru názvů nebo `End Sub` modulu, například nebo `Module`.

## <a name="see-also"></a>Viz také
- [Formát specifikátorů v jazyce C++](../debugger/format-specifiers-in-cpp.md)
- [Kontextový operátor (C++)](../debugger/context-operator-cpp.md)
- [Specifikátory formátu v jazyce C#](../debugger/format-specifiers-in-csharp.md)
- [Pseudoproměnné](../debugger/pseudovariables.md)
