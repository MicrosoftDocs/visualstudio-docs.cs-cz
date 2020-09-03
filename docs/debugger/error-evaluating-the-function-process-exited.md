---
title: 'Chyba: cílový proces byl ukončen s kódem kódu &apos; &apos; při vyhodnocování funkce Function &apos; &apos; | Microsoft Docs'
ms.date: 4/06/2018
ms.topic: error-reference
f1_keywords:
- vs.debug.error.process_exit_during_func_eval
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 94effc8a5f75e7b38fb7275d175eb324c479a7a9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "88711635"
---
# <a name="error-the-target-process-exited-with-code-39code39-while-evaluating-the-function-39function39"></a>Chyba: cílový proces se ukončil s kódem &#39;kódem&#39; při vyhodnocování funkce &#39;funkce&#39;

Úplný text zprávy: cílový proces byl ukončen s kódem Code při vyhodnocování funkce Function.

Aby bylo snazší zkontrolovat stav objektů .NET, ladicí program automaticky vynutí proces laděného procesu spustit další kód (obvykle metody getter vlastnosti a `ToString` funkce). Ve většině scénářů jsou tyto funkce úspěšně dokončeny nebo vyvolaly výjimky, které mohou být zachyceny ladicím programem. Existují však určité okolnosti, kdy výjimky nelze zachytit, protože překračují hranice jádra, vyžadují čerpadlo uživatelských zpráv nebo jsou neobnovitelné. V důsledku toho metoda getter nebo ToString, která spouští kód, který buď explicitně ukončí proces (například volání `ExitProcess()` ) nebo vyvolá neošetřenou výjimku, kterou nelze zachytit (například `StackOverflowException` ), ukončí laděný proces a ukončí relaci ladění. Pokud se zobrazí tato chybová zpráva, došlo k této chybě.

Jednou z běžných příčin tohoto problému je, že když ladicí program vyhodnotí vlastnost, která volá sám sebe, může to mít za následek výjimku přetečení zásobníku. Nelze obnovit výjimku přetečení zásobníku a cílový proces bude ukončen.

## <a name="to-correct-this-error"></a>Oprava této chyby

Existují dvě možná řešení tohoto problému.

### <a name="solution-1-prevent-the-debugger-from-calling-the-getter-property-or-tostring-method"></a>Řešení #1: zabrání ladicímu programu volat vlastnost getter nebo metodu ToString. 

Chybová zpráva vám sdělí název funkce, kterou ladicí program pokusil zavolat. S názvem funkce můžete zkusit znovu vyhodnotit tuto funkci z příkazového **okna pro** ladění vyhodnocení. Ladění je možné při vyhodnocování z **příkazového okna,** protože na rozdíl od implicitních hodnocení z oken automatické hodnoty, místní hodnoty a **kukátko** se ladicí program ukončí na neošetřených výjimkách.

Pokud tuto funkci můžete změnit, můžete zabránit ladicímu programu v volání metody getter nebo Method vlastnosti `ToString` . Zkuste provést jednu z následujících akcí:

* Změňte metodu na jiný typ kódu kromě metody getter nebo ToString a problém zmizí.
    -nebo-
* (Pro `ToString` ) Definujte `DebuggerDisplay` atribut pro daný typ a ladicí program může vyhodnotit jinou hodnotu než `ToString` .
    -nebo-
* (Pro Getter vlastnost) Umístěte `[System.Diagnostics.DebuggerBrowsable(DebuggerBrowsableState.Never)]` atribut na vlastnost. To může být užitečné, pokud máte metodu, která musí mít vlastnost pro důvody kompatibility rozhraní API, ale měla by být ve skutečnosti metoda.

Pokud tuto metodu nemůžete změnit, je možné, že cílový proces bude možné rozdělit na alternativní instrukci a znovu provést vyhodnocení.

### <a name="solution-2-disable-all-implicit-evaluation"></a>Řešení #2: Zakázat všechna implicitní vyhodnocení

Pokud předchozí řešení problém nevyřeší, pokračujte na **Tools**  >  **Možnosti**nástroje a zrušte zaškrtněte nastavení **ladění**  >  **Obecné**  >  **Povolit vyhodnocení vlastností a další implicitní volání funkcí**. Tato akce zakáže většinu implicitních vyhodnocení funkcí a tento problém by měl vyřešit.
