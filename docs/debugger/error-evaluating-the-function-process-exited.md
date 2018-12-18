---
title: 'Chyba: Cílový proces se ukončil s kódem &#39;kód&#39; při vyhodnocování funkce &#39;funkce&#39; | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 4/06/2018
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.process_exit_during_func_eval
ms.technology: vs-ide-debug
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 98923757912d1f4619cc79c8f946aabaa531ac05
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49936261"
---
# <a name="error-the-target-process-exited-with-code-39code39-while-evaluating-the-function-39function39"></a>Chyba: Cílový proces se ukončil s kódem &#39;kód&#39; při vyhodnocování funkce &#39;– funkce&#39;

Úplný text zprávy: Cílový proces se ukončil s kódem "kód" při vyhodnocování funkce 'function'.

Aby bylo snazší kontrolovat stav objektů .NET, ladicí program automaticky vynutí laděného procesu ke spuštění dalšího kódu (obvykle metody getter vlastnosti a `ToString` funkce). Ve většině případů tyto funkce úspěšně dokončena, nebo vyvolat výjimky, které lze zachytit ladicím programem. Existují však některé okolnosti, ve kterých nejde zachytit výjimky, protože překračují hranice jádra, vyžadují – čerpání zpráv uživatele nebo Neopravitelná. Jako výsledek, metoda getter vlastnosti nebo metody ToString, která spustí kód tohoto buď ukončí proces (například volání `ExitProcess()`) nebo vyvolá neošetřenou výjimku, která nejde zachytit (například `StackOverflowException`) končí laděného procesu a ukončení relace ladění. Pokud dojde k této chybě to došlo k chybě.
 
Jedním z běžných důvodů tohoto problému je, že když ladicí program vyhodnotí vlastnost, která se zavolá sama sebe, to může vést k výjimce přetečení zásobníku. Výjimku přetečení zásobníku nelze obnovit, a cílový proces se ukončí.
 
## <a name="to-correct-this-error"></a>Oprava této chyby
 
Existují dvě možná řešení tohoto problému.
 
### <a name="solution-1-prevent-the-debugger-from-calling-the-getter-property-or-tostring-method"></a>Řešení #1: Zabrání ladicí program volání metoda getter vlastnosti nebo metody ToString 

Chybová zpráva vám sdělí název, který ladicí program se pokusil zavolat funkci. S názvem funkce, můžete zkusit znovu vaše rozhodnutí vyzkoušet tuto funkci **okamžité** okno pro ladění hodnocení. Ladění je možné při vyhodnocování z **okamžité** okno proto, že na rozdíl od implicitní vyhodnocení z **automatické hodnoty a místní hodnoty/Watch** windows, ladicí program přeruší v případě neošetřených výjimek.

Pokud upravíte tuto funkci, můžete zabránit ladicí program volání metoda getter vlastnosti nebo `ToString` metody. Zkuste použijte jeden z následujících akcí:
 
* Změnit metodu na jiný typ kódu kromě metoda getter vlastnosti nebo metody ToString a problém zmizí.
    -nebo-
* (Pro `ToString`) definovat `DebuggerDisplay` atribut na typ a může mít ladicí program vyhodnotí něco jiného než `ToString`.
    -nebo-
* (Pro metoda getter vlastnosti) Vložit `[System.Diagnostics.DebuggerBrowsable(DebuggerBrowsableState.Never)]` atribut na vlastnost. To může být užitečné, pokud máte metodu, která nadále vlastnost z důvodů kompatibility rozhraní API, ale ve skutečnosti měla by být metody.

Pokud tuto metodu nelze upravit, bude pravděpodobně možné Cílový proces zarážku alternativní instrukce, a opakujte hodnocení.
 
### <a name="solution-2-disable-all-implicit-evaluation"></a>Řešení #2: Zakáže všechny implicitní vyhodnocení
 
Pokud předchozí řešení není problém vyřešit, přejděte na **nástroje** > **možnosti**a zrušte zaškrtnutí políčka **ladění**  >   **Obecné** > **povolit vyhodnocování vlastností a jiných implicitních volání funkcí**. Tím dojde k zakázání většina vyhodnocení implicitní funkce a má problém vyřešit.



  
