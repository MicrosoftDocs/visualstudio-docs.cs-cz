---
title: Výrazy v ladicím programu | Microsoft Docs
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
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78406333"
---
# <a name="expressions-in-the-debugger"></a>Výrazy v ladicím programu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ladicí program sady Visual Studio obsahuje vyhodnocovací filtry výrazů, které fungují při zadání výrazu do dialogového okna **QuickWatch** , v okně **kukátka** nebo v okně **Immediate** . Vyhodnocovací filtry výrazů jsou také v práci v okně **zarážky** a v mnoha dalších místech v ladicím programu.  
  
 Následující části obsahují podrobné informace o výrazech v různých jazycích.  
  
## <a name="f-expressions-are-not-supported"></a>F#výrazy nejsou podporované.  
 F#výrazy nejsou rozpoznané. Pokud ladíte F# kód, je nutné přeložit výrazy do C# syntaxe před vstupem do okna ladicího programu nebo do dialogového okna. Při překládání výrazů F# z C#na, nezapomeňte, že C# používá operátor `==` k otestování rovnosti, zatímco F# používá jediný `=`.  
  
## <a name="c-expressions"></a>C++Expression  
 Informace o použití kontextových operátorů s výrazy C++v naleznete v tématu [operátorC++kontextu ()](../debugger/context-operator-cpp.md).  
  
### <a name="unsupported-expressions-in-c"></a>Nepodporované výrazy vC++  
  
#### <a name="constructors-destructors-and-conversions"></a>Konstruktory, destruktory a převody  
 Nelze volat konstruktor nebo destruktor pro objekt, buď explicitně nebo implicitně. Například následující výraz explicitně volá konstruktor a má za následek chybovou zprávu:  
  
```cpp  
my_date( 2, 3, 1985 )  
```  
  
 Funkci převodu nelze volat, pokud je cíl převodu třída. Takový převod zahrnuje konstrukci objektu. Například pokud `myFraction` je instance `CFraction`, která definuje operátor funkce převodu `FixedPoint`, následující výraz má za následek chybu:  
  
```cpp  
(FixedPoint)myFraction  
```  
  
 Nemůžete volat operátory New nebo DELETE. Například následující výraz není podporován:  
  
```cpp  
new Date(2,3,1985)  
```  
  
#### <a name="preprocessor-macros"></a>Makra preprocesoru  
 Makra preprocesoru nejsou v ladicím programu podporována. Například pokud je konstanta `VALUE` deklarována jako: `#define VALUE 3`, nelze v okně **kukátko** použít `VALUE`. Chcete-li se tomuto omezení vyhnout, je třeba nahradit `#define`s výčty a funkcemi, kdykoli je to možné.  
  
### <a name="using-namespace-declarations"></a>použití deklarací oboru názvů  
 Deklarace `using namespace` nemůžete použít.  Aby bylo možné přistupovat k názvu typu nebo proměnné mimo aktuální obor názvů, je nutné použít plně kvalifikovaný název.  
  
### <a name="anonymous-namespaces"></a>Anonymní obory názvů  
 Anonymní obory názvů nejsou podporované. Pokud máte následující kód, nelze přidat `test` do okna Kukátko:  
  
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
  
### <a name="BKMK_Using_debugger_intrinisic_functions_to_maintain_state"></a>Zachování stavu pomocí vnitřních funkcí ladicího programu  
 Vnitřní funkce ladicího programu poskytují způsob, jak volat určité funkce jazykaC++ C nebo ve výrazech beze změny stavu aplikace.  
  
 Vnitřní funkce ladicího programu:  
  
- Jsou zaručené jako bezpečné: provádění vnitřní funkce ladicího programu nebude poškodit proces, který se právě ladí.  
  
- Jsou povoleny ve všech výrazech, dokonce i ve scénářích, kde nejsou povoleny vedlejší účinky a vyhodnocení funkce.  
  
- Práce ve scénářích, kde běžné volání funkce nejsou možná, jako je například ladění s minimálním výpisem.  
  
  Vnitřní funkce ladicího programu můžou také lépe vyhodnocovat výrazy. Například `strncmp(str, “asd”)` je mnohem snazší zapsat do podmínky zarážky, než `str[0] == ‘a’ && str[1] == ‘s’ && str[2] == ‘d’`. )  
  
|Oblast|Vnitřní funkce|  
|----------|-------------------------|  
|**Délka řetězce**|strlen, wcslen, strnlen, wcsnlen|  
|**Porovnání řetězců**|strcmp, wcscmp, stricmp, _stricmp, _strcmpi, wcsicmp, _wcscmpi, _wcsnicmp, strncmp, wcsncmp, strnicmp, wcsnicmp|  
|**Hledání řetězců**|strchr, wcschr, strstr, wcsstr|  
|**Chyb**|GetLastError(), TlsGetValue()|  
|**Systém Windows 8**|WindowsGetStringLen(), WindowsGetStringRawBuffer()<br /><br /> Tyto funkce vyžadují, aby byl proces, který se právě ladí, spuštěný v systému Windows 8. Ladění souborů výpisu paměti generovaných ze zařízení se systémem Windows 8 vyžaduje také, aby na počítači se systémem Visual Studio běžel systém Windows 8. Pokud však provádíte ladění zařízení se systémem Windows 8 vzdáleně, může na počítači se systémem Visual Studio běžet systém Windows 7.|  
|**Různé**|__log2<br /><br /> Vrátí základ protokolu 2 zadaného celého čísla zaokrouhlený na nejbližší dolní celé číslo.|  
  
## <a name="ccli---unsupported-expressions"></a>C++/CLI – nepodporované výrazy  
  
- Přetypování, které zahrnují ukazatele nebo uživatelem definovaná přetypování, nejsou podporovány.  
  
- Porovnání objektů a přiřazení nejsou podporovány.  
  
- Přetížené operátory a přetížené funkce nejsou podporovány.  
  
- Zabalení a rozbalení nejsou podporovaná.  
  
- operátor `Sizeof` není podporován.  
  
## <a name="c---unsupported-expressions"></a>C#– Nepodporované výrazy  
  
### <a name="dynamic-objects"></a>Dynamické objekty  
 Ve výrazech ladicího programu můžete použít proměnné, které jsou staticky zadány jako dynamické. Když jsou objekty, které implementují <xref:System.Dynamic.IDynamicMetaObjectProvider>, vyhodnocovány v okno Kukátko, je přidán uzel dynamického zobrazení. Uzel dynamického zobrazení zobrazuje členy objektu, ale neumožňuje úpravy hodnot členů.  
  
 Následující funkce dynamických objektů nejsou podporovány:  
  
- Složené operátory `+=`, `-=`, `%=`, `/=`a `*=`  
  
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
 Ve výrazech ladicího programu můžete použít proměnné, které jsou staticky zadány jako dynamické. Když jsou objekty, které implementují <xref:System.Dynamic.IDynamicMetaObjectProvider>, vyhodnocovány v okno Kukátko, je přidán uzel dynamického zobrazení. Uzel dynamického zobrazení zobrazuje členy objektu, ale neumožňuje úpravy hodnot členů.  
  
 Následující funkce dynamických objektů nejsou podporovány:  
  
- Složené operátory `+=`, `-=`, `%=`, `/=`a `*=`  
  
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
  
- Klíčová slova na úrovni oboru názvů nebo modulu, například `End Sub` nebo `Module`.  
  
## <a name="see-also"></a>Viz také  
 [Specifikátory formátu v C++ ](../debugger/format-specifiers-in-cpp.md)   
 [Operátor kontextu (C++)](../debugger/context-operator-cpp.md)   
 [Specifikátory formátu v C# ](../debugger/format-specifiers-in-csharp.md)   
 [Pseudoproměnné](../debugger/pseudovariables.md)
