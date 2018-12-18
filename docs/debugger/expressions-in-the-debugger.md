---
title: Výrazy v ladicím programu | Dokumentace Microsoftu
ms.custom: ''
ms.date: 02/07/2017
ms.technology: vs-ide-debug
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 035d66590c6b6087c56887a4eaa2b0538406f87b
ms.sourcegitcommit: a7de99f36e9ead7ea9e9bac23c88d05ddfc38b00
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/20/2018
ms.locfileid: "52257248"
---
# <a name="expressions-in-the-visual-studio-debugger"></a>Výrazy v ladicím programu sady Visual Studio
Ladicího programu sady Visual Studio obsahuje hodnotitele výrazu, které pracují při zadání výrazu v **QuickWatch** dialogovém okně **Watch** okna, nebo **okamžité** okna. Vyhodnocení výrazu jsou také v práci **zarážky** okno a mnoha dalších místech v ladicím programu.
  
 V následujících částech se popisuje omezení vyhodnocení výrazu pro jazyky podporované v aplikaci Visual Studio.
  
## <a name="f-expressions-are-not-supported"></a>F#výrazy nejsou podporovány.  
 F#výrazy nejsou rozpoznány. Pokud ladíte F# kódu, musíte převést vaše výrazů do C# syntaxe před vstupem do ladicího programu okně nebo dialogovém okně pole výrazy. Při překlad výrazů od F# k C#, nezapomeňte mějte na paměti, C# používá `==` operátor testovat rovnost, zatímco F# používá jedné `=`.  
  
## <a name="c-expressions"></a>Výrazy jazyka C++  
 Informace o použití kontextu operátory s výrazy v jazyce C++, naleznete v tématu [kontextu – operátor (C++)](../debugger/context-operator-cpp.md).  
  
### <a name="unsupported-expressions-in-c"></a>Nepodporované výrazy v jazyce C++  
  
#### <a name="constructors-destructors-and-conversions"></a>Konstruktory, destruktory a převody  
 Konstruktor nebo destruktor nelze volat pro objekt, explicitně nebo implicitně. Například následující výraz explicitně volá konstruktor a výsledkem chybová zpráva:  
  
```C++  
my_date( 2, 3, 1985 )  
```  
  
 Funkce převodu nelze volat, pokud je cíl převodu třídy. Takový převod zahrnuje konstrukce objektu. Například pokud `myFraction` je instance `CFraction`, která definuje funkci operátoru převodu `FixedPoint`, následující výraz způsobí chybu:  
  
```C++  
(FixedPoint)myFraction  
```  
  
 Nelze zavolat novou nebo odstranit operátory. Například následující výraz není podporovaný:  
  
```C++  
new Date(2,3,1985)  
```  
  
#### <a name="preprocessor-macros"></a>Makra preprocesoru  
 Makra preprocesoru nejsou podporovány v ladicím programu. Například pokud konstantu `VALUE` je deklarován jako: `#define VALUE 3`, nemůžete použít `VALUE` v **Watch** okna. Aby se zabránilo toto omezení, byste měli vyměnit `#define`uživatele s výčty a funkce, kdykoli je to možné.  
  
### <a name="using-namespace-declarations"></a>pomocí deklarace oboru názvů  
 Nemůžete použít `using namespace` deklarace.  Aby bylo možné získat přístup k proměnné mimo aktuální obor názvů a název typu, musíte použít plně kvalifikovaný název.  
  
### <a name="anonymous-namespaces"></a>Anonymní obory názvů  
 Anonymní obory názvů nejsou podporovány. Pokud máte následující kód, nelze přidat `test` k oknu kukátka:  
  
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
  
###  <a name="BKMK_Using_debugger_intrinisic_functions_to_maintain_state"></a> Pomocí vnitřní funkce ladicího programu pro uchování stavu  
 Vnitřní funkce ladicího programu poskytují způsob, jak volat určité funkce jazyka C/C++ ve výrazech beze změny stavu aplikace.  
  
 Vnitřní funkce ladicího programu:  
  
- Je zaručeno bezpečné: provádění vnitřní funkce ladicího programu nebude poškodit proces, který je právě laděna.  
  
- Jsou povoleny v všechny výrazy, dokonce i ve scénářích, kde nejsou povolené vedlejší efekty a vyhodnocení funkce.  
  
- Práce ve scénářích, kde nejsou volání normální funkce je to možné, jako je ladění s minimálním výpisem.  
  
  Vnitřní funkce ladicího programu můžete také nastavit vyhodnocování výrazů pohodlnější. Například `strncmp(str, "asd")` je mnohem jednodušší psaní v podmínku zarážky než `str[0] == 'a' && str[1] == 's' && str[2] == 'd'`. )  
  
|Oblast|Vnitřní funkce|  
|----------|-------------------------|  
|**Délka řetězce**|strlen, wcslen –, strnlen –, wcsnlen –|  
|**Porovnání řetězců**|strcmp –, wcscmp –, stricmp –, _stricmp –, _strcmpi –, wcsicmp –, _wcscmpi, _wcsnicmp –, strncmp –, wcsncmp –, strnicmp –, wcsnicmp –|  
|**Hledání řetězce**|strchr –, wcschr –, strstr –, wcsstr –|  
|**Win32**|Funkce GetLastError() TlsGetValue()|  
|**Windows 8**|WindowsGetStringLen() WindowsGetStringRawBuffer()<br /><br /> Tyto funkce vyžadují proces, který je právě laděna, aby byla spuštěna v systému Windows 8. Ladění s výpisem paměti soubory vygenerované ze zařízení s Windows 8 také vyžaduje, aby Visual Studio počítače s Windows 8. Nicméně pokud zařízení s Windows 8 ladíte vzdáleně, počítač Visual Studio může běžet Windows 7.|  
|**Různé**|__log2<br /><br /> Vrátí základní 2 zadané celé číslo, zaokrouhlí na nejbližší menší celé číslo v protokolu.|  
  
## <a name="ccli---unsupported-expressions"></a>C + +/ CLI - nepodporované výrazy  
  
-   Přetypování, které se týkají ukazatele nebo uživatelem definované přetypování, nejsou podporovány.  
  
-   Porovnání objektu a přiřazení nejsou podporovány.  
  
-   Přetížené operátory a přetížené funkce nejsou podporovány.  
  
-   Zabalení a rozbalení nejsou podporovány.  
  
-   `Sizeof` operátor není podporován.  
  
## <a name="c---unsupported-expressions"></a>C# – nepodporované výrazy  
  
### <a name="dynamic-objects"></a>Dynamické objekty  
 Proměnné můžete použít ve výrazech ladicího programu, které staticky se zadávají jako dynamický. Pokud objekty, které implementují <xref:System.Dynamic.IDynamicMetaObjectProvider> jsou vyhodnocovány v okně kukátka, přidat uzel dynamického zobrazení. Uzel dynamického zobrazení zobrazuje členy objektu, ale neumožňuje úpravy hodnot členů.  
  
 Nejsou podporovány následující funkce dynamické objekty:  
  
-   Složené operátory `+=`, `-=`, `%=`, `/=`, a `*=`  
  
-   Mnoho přetypování, včetně číselné přetypování a argument typu přetypování  
  
-   Volání metody s více než dva argumenty  
  
-   Gettery vlastností s více než dva argumenty  
  
-   Nastavením vlastností s argumenty  
  
-   Přiřazení k indexeru  
  
-   Logické operátory `&&` a `||`  
  
### <a name="anonymous-methods"></a>Anonymní metody  
 Vytvoření nové anonymní metody není podporováno.  
  
## <a name="visual-basic---unsupported-expressions"></a>Visual Basic – nepodporované výrazy  
  
### <a name="dynamic-objects"></a>Dynamické objekty  
 Proměnné můžete použít ve výrazech ladicího programu, které staticky se zadávají jako dynamický. Pokud objekty, které implementují <xref:System.Dynamic.IDynamicMetaObjectProvider> jsou vyhodnocovány v okně kukátka, přidat uzel dynamického zobrazení. Uzel dynamického zobrazení zobrazuje členy objektu, ale neumožňuje úpravy hodnot členů.  
  
 Nejsou podporovány následující funkce dynamické objekty:  
  
-   Složené operátory `+=`, `-=`, `%=`, `/=`, a `*=`  
  
-   Mnoho přetypování, včetně číselné přetypování a argument typu přetypování  
  
-   Volání metody s více než dva argumenty  
  
-   Gettery vlastností s více než dva argumenty  
  
-   Nastavením vlastností s argumenty  
  
-   Přiřazení k indexeru  
  
-   Logické operátory `&&` a `||`  
  
### <a name="local-constants"></a>Místní konstanty  
 Nepodporují se místní konstanty.  
  
### <a name="import-aliases"></a>Import aliasů  
 Import aliasů nejsou podporovány.  
  
### <a name="variable-declarations"></a>Deklarace proměnných  
 Nelze deklarovat explicitní nové proměnné v ladicím programu systému windows. Však můžete přiřadit nové implicitní proměnné uvnitř **okamžité** okna. Tyto implicitní proměnné jsou omezená na relaci ladění a nejsou přístupné mimo ladicí program. Například příkaz `o = 5` implicitně vytvoří novou proměnnou `o` a jí přiřadit hodnotu 5. Takové implicitní proměnné nejsou typu **objekt** Pokud typu lze odvodit ladicím programem.  
  
### <a name="unsupported-keywords"></a>Nepodporovaná klíčová slova  
  
-   `AddressOf`  
  
-   `End`  
  
-   `Error`  
  
-   `Exit`  
  
-   `Goto`  
  
-   `On Error`  
  
-   `Resume`  
  
-   `Return`  
  
-   `Select/Case`  
  
-   `Stop`  
  
-   `SyncLock`  
  
-   `Throw`  
  
-   `Try/Catch/Finally`  
  
-   `With`  
  
-   Namespace nebo modul úroveň klíčová slova, jako například `End Sub` nebo `Module`.  
  
## <a name="see-also"></a>Viz také  
 [Specifikátory formátu v jazyce C++](../debugger/format-specifiers-in-cpp.md)   
 [Kontextový operátor (C++)](../debugger/context-operator-cpp.md)   
 [Specifikátory formátu v jazyce C#](../debugger/format-specifiers-in-csharp.md)   
 [Pseudoproměnné](../debugger/pseudovariables.md)