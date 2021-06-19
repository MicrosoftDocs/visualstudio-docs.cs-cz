---
title: Vyhodnocení funkce funkce mělo časový limit a bylo potřeba ji přerušit nebezpečným &apos; &apos; způsobem| Microsoft Docs
description: 'Celý text zprávy: Při vyhodnocování funkce function (funkce) se vyhodnotil časový limit a bylo potřeba ji přerušit nebezpečným způsobem.'
ms.date: 06/18/2021
ms.topic: error-reference
f1_keywords:
- vs.debug.error.unsafe_func_eval_abort
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e928bb0ebae1e644729fcaf4f47b7dd461399be6
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2021
ms.locfileid: "112386667"
---
# <a name="error-evaluating-the-function-39function39-timed-out-and-needed-to-be-aborted-in-an-unsafe-way"></a>Chyba: Při vyhodnocování funkce &#39;došlo&#39; časový limit a bylo potřeba ji přerušit nebezpečným způsobem.

Celý text zprávy: Při vyhodnocování funkce function (funkce) se vyhodnotil časový limit a bylo potřeba ji přerušit nebezpečným způsobem. Může dojít k poškození cílového procesu.

Aby bylo snazší zkontrolovat stav objektů .NET, ladicí program automaticky vynutí, aby laděné procesy spouštěly další kód (obvykle metody getter vlastností a funkce ToString). Ve většině scénářů se tyto funkce dokončí rychle a ladění je mnohem jednodušší. Ladicí program ale nespouštěl aplikaci v sandboxu. Výsledkem je, že metoda getter vlastnosti nebo ToString, která volá nativní funkci, která přestane reagovat, může vést k dlouhým časovým limitům, které nemusí být možné obnovit. Pokud se zobrazí tato chybová zpráva, došlo k tomu.

Jedním z běžných důvodů tohoto problému je to, že když ladicí program vyhodnocuje vlastnost, umožňuje spuštění pouze vlákna, které se prověřuje. Takže pokud vlastnost čeká na spuštění v jiných vláknech v laděné aplikaci a pokud čeká způsobem, který modul runtime .NET nemůže přerušit, dojde k tomuto problému.

## <a name="to-correct-this-error"></a>Oprava této chyby

V následujících částech najdete několik možných řešení tohoto problému.

## <a name="solution-1-prevent-the-debugger-from-calling-the-getter-property-or-tostring-method"></a>Řešení #1: Zabránit ladicímu programu v volání vlastnosti getter nebo metody ToString

Chybová zpráva vám řekne název funkce, kterou se ladicí program pokusil volat. Pokud tuto funkci můžete upravit, můžete ladicímu programu zabránit v volání metody property getter nebo ToString. Vyzkoušejte jednu z následujících možností:

* Změňte metodu na jiný typ kódu kromě metody property getter nebo ToString a problém zmizí.
  -nebo-
* (Pro ToString) Definujte [atribut DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md) pro typ a ladicí program může vyhodnotit něco jiného než ToString.
  -nebo-
* (Pro getter vlastnost) Do vlastnosti umístěte atribut [System.Diagnostics.DebuggerBrowsable(DebuggerBrowsableState.Never).](/dotnet/api/system.diagnostics.debuggerbrowsableattribute) To může být užitečné, pokud máte metodu, která musí zůstat vlastností z důvodů kompatibility rozhraní API, ale ve skutečnosti by to měla být metoda.

## <a name="solution-2-have-the-target-code-ask-the-debugger-to-abort-the-evaluation"></a>Řešení #2: Požádejte cílový kód ladicího programu, aby přerušil vyhodnocení.

Chybová zpráva vám řekne název funkce, kterou se ladicí program pokusil volat. Pokud se někdy nepodaří správně spustit metodu getter nebo ToString vlastnosti, zejména v situacích, kdy je problém v tom, že kód ke spuštění kódu potřebuje jiné vlákno, může implementační funkce zavolat [metodu System.Diagnostics.Debugger.NotifyOfCrossThreadDependency](/dotnet/api/system.diagnostics.debugger.notifyofcrossthreaddependency) a požádat ladicí program o přerušení vyhodnocení funkce. V tomto řešení je stále možné explicitně vyhodnotit tyto funkce, ale výchozí chování je, že provádění se zastaví, když dojde k volání NotifyOfCrossThreadDependency.

## <a name="solution-3-disable-all-implicit-evaluation"></a>Řešení #3: Zákaz veškerého implicitního vyhodnocení

Pokud předchozí řešení problém nevyřeší, přejděte na Možnosti nástrojů a zrušte zaškrtnutí nastavení Ladění obecného povolení vyhodnocení vlastností a dalších  >     >    >  **implicitních volání funkcí**. Tím se zakáže většina implicitních vyhodnocení funkcí a problém by se měl vyřešit.

## <a name="solution-4-check-compatibility-with-third-party-developer-tools"></a>Řešení #4: Kontrola kompatibility s vývojářských nástrojů třetích stran

Pokud používáte Resharper, najdete návrhy v [tomto](https://youtrack.jetbrains.com/issue/RSRP-476824) problému.

## <a name="solution-5-enable-managed-compatibility-mode"></a>Řešení #5: Povolení režimu spravované kompatibility

Pokud přepnete na starší verzi modulu ladění, můžete tuto chybu eliminovat. Přejděte na **Nástroje** Možnosti a vyberte nastavení Ladění Obecné  >     >    >  **použití spravovaného režimu kompatibility**. Další informace najdete v tématu [Obecné možnosti ladění.](../debugger/general-debugging-options-dialog-box.md)
