---
title: Výrazy v ladicím programu | Dokumenty společnosti Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.expressions
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VBScript
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
caps.latest.revision: 30
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3999737a2fad04c9b513722ae11608574a72c410
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302523"
---
# <a name="expressions-in-the-debugger"></a>Výrazy v ladicím programu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ladicí program sady Visual Studio obsahuje vyhodnocení výrazů, které fungují při zadání výrazu v dialogovém okně **QuickWatch,** okně **Kukátka** nebo **V okně Okamžité.** Vyhodnocení výrazu jsou také v práci v okně **Zarážky** a mnoho dalších míst v ladicím programu.  
  
 V následujících částech jsou uvedeny podrobnosti o výrazech v různých jazycích.  
  
## <a name="f-expressions-are-not-supported"></a>Výrazy Jazyka F# nejsou podporovány.  
 Výrazy Jazyka F# nejsou rozpoznány. Pokud ladíte kód F#, musíte před zadáním výrazů do okna ladicího programu nebo dialogového okna přeložit výrazy do syntaxe jazyka C#. Při překladu výrazů z Jazyka F# do jazyka C# `==` nezapomeňte, že c# používá operátor `=`k testování rovnosti, zatímco F# používá jeden .  
  
## <a name="c-expressions"></a>Výrazy jazyka C++  
 Informace o použití kontextových operátorů s výrazy v jazyce C++ naleznete v [tématu Context Operator (C++).](../debugger/context-operator-cpp.md)  
  
### <a name="unsupported-expressions-in-c"></a>Nepodporované výrazy v jazyce C++  
  
#### <a name="constructors-destructors-and-conversions"></a>Konstruktory, destruktory a převody  
 Nelze volat konstruktor nebo destruktor pro objekt, explicitně nebo implicitně. Například následující výraz explicitně volá konstruktor a výsledkem je chybová zpráva:  
  
```cpp  
my_date( 2, 3, 1985 )  
```  
  
 Funkci převodu nelze volat, pokud je cílem převodu třída. Taková konverze zahrnuje konstrukci objektu. Například pokud `myFraction` je instance `CFraction`, která definuje operátor `FixedPoint`funkce převodu , následující výraz má za následek chybu:  
  
```cpp  
(FixedPoint)myFraction  
```  
  
 Nelze volat nové nebo odstranit operátory. Například následující výraz není podporován:  
  
```cpp  
new Date(2,3,1985)  
```  
  
#### <a name="preprocessor-macros"></a>Preprocesorová makra  
 Preprocesorová makra nejsou v ladicím programu podporována. `VALUE` Například pokud konstanta je `#define VALUE 3`deklarována jako: , nelze použít `VALUE` v okně **kukátko.** Chcete-li se tomuto `#define`omezení vyhnout, měli byste nahradit 's s výčty a funkce, kdykoli je to možné.  
  
### <a name="using-namespace-declarations"></a>použití deklarací oboru názvů  
 Deklarace `using namespace` nelze použít.  Chcete-li získat přístup k názvu nebo proměnné mimo aktuální obor názvů, musíte použít plně kvalifikovaný název.  
  
### <a name="anonymous-namespaces"></a>Anonymní obory názvů  
 Anonymní obory názvů nejsou podporovány. Pokud máte následující kód, nelze `test` přidat do okna kukátka:  
  
```cpp  
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
  
  Dedebační program vnitřní funkce může také vyhodnotit výrazy pohodlnější. Například `strncmp(str, “asd”)` je mnohem jednodušší psát v podmínce zarážky než `str[0] == ‘a’ && str[1] == ‘s’ && str[2] == ‘d’`. )  
  
|Oblast|Vnitřní funkce|  
|----------|-------------------------|  
|**Délka řetězce**|strlen, wcslen, strnlen, wcsnlen|  
|**Porovnání řetězců**|strcmp, wcscmp, stricmp, _stricmp, _strcmpi, wcsicmp, _wcscmpi, _wcsnicmp, strncmp, wcsncmp, strnicmp, wcsnicmp|  
|**Hledání v řetězci**|strchr, wcschr, strstr, wcsstr|  
|**Win32**|GetLastError(), TlsGetValue()|  
|**Windows 8**|WindowsGetStringLen(), WindowsGetStringRawBuffer()<br /><br /> Tyto funkce vyžadují proces, který je právě laděn, aby byl spuštěn v systému Windows 8. Ladění souborů výpisu generovaných ze zařízení se systémem Windows 8 také vyžaduje, aby počítač Visual Studio se systémem Windows 8. Pokud však vzdáleně ladíte zařízení se systémem Windows 8, může být v počítači sady Visual Studio spuštěn systém Windows 7.|  
|**Různé**|__log2<br /><br /> Vrátí základnu protokolu 2 zadaného celého čísla zaokrouhlenou na nejbližší nižší celé číslo.|  
  
## <a name="ccli---unsupported-expressions"></a>C++/CLI - nepodporované výrazy  
  
- Přetypová dlažem, které zahrnují ukazatele nebo uživatelem definované přetypovače, nejsou podporovány.  
  
- Porovnání objektů a přiřazení nejsou podporovány.  
  
- Přetížené operátory a přetížené funkce nejsou podporovány.  
  
- Zabalení a rozbalení nejsou podporovány.  
  
- `Sizeof`operátor není podporován.  
  
## <a name="c---unsupported-expressions"></a>C# - nepodporované výrazy  
  
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
 [Formát specifikátorů v jazyce C++](../debugger/format-specifiers-in-cpp.md)   
 [Operátor kontextu (C++)](../debugger/context-operator-cpp.md)   
 [Formát specifikátorů v C #](../debugger/format-specifiers-in-csharp.md)   
 [Pseudoproměnné](../debugger/pseudovariables.md)
