---
title: Vyhodnocení funkce Function &apos; &apos; vypršel časový limit a bylo nutné ho přerušit nebezpečným způsobem | Microsoft Docs
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- vs.debug.error.unsafe_func_eval_abort
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 256b7858ed5714d716b31fa28c8cd463b96dbb8a
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/22/2020
ms.locfileid: "90852742"
---
# <a name="error-evaluating-the-function-39function39-timed-out-and-needed-to-be-aborted-in-an-unsafe-way"></a>Chyba: vyhodnocování funkce &#39;funkce&#39; vypršel časový limit a bylo nutné je přerušit nebezpečným způsobem.

Úplný text zprávy: při vyhodnocování funkce Function vypršel časový limit a bylo nutné ho přerušit nebezpečným způsobem. To může mít poškozený cílový proces.

Aby bylo snazší zkontrolovat stav objektů .NET, ladicí program automaticky vynutí laděný proces, aby spouštěl další kód (obvykle metody getter vlastností a funkce ToString). Ve většině scénářů se tyto funkce dokončí rychle a ladění je mnohem jednodušší. Ladicí program však aplikaci nespustí v izolovaném prostoru (sandbox). V důsledku toho metoda get nebo ToString, která volá do nativní funkce, která přestane reagovat, může způsobit dlouhé časové limity, které nemusí být obnovitelné. Pokud se zobrazí tato chybová zpráva, došlo k této chybě.

Jednou z běžných příčin tohoto problému je, že když ladicí program vyhodnotí vlastnost, umožňuje pouze kontrolované vlákno. Takže pokud vlastnost čeká na spuštění jiných vláken uvnitř laděné aplikace a pokud čeká způsobem, že modul runtime .NET nemůže provést přerušení, dojde k tomuto problému.

## <a name="to-correct-this-error"></a>Oprava této chyby

Existuje několik možných řešení tohoto problému.

### <a name="solution-1-prevent-the-debugger-from-calling-the-getter-property-or-tostring-method"></a>Řešení #1: zabrání ladicímu programu volat vlastnost getter nebo metodu ToString.

Chybová zpráva vám sdělí název funkce, kterou se ladicí program pokusil zavolat. Pokud tuto funkci můžete změnit, můžete zabránit ladicímu programu v volání metody getter nebo ToString vlastnosti. Zkuste provést jednu z následujících akcí:

* Změňte metodu na jiný typ kódu kromě metody getter nebo ToString a problém zmizí.
    -nebo-
* (Pro ToString) Definujte pro typ atribut DebuggerDisplay a ladicí program může vyhodnotit jinou hodnotu než ToString.
    -nebo-
* (Pro Getter vlastnost) Umístěte `[System.Diagnostics.DebuggerBrowsable(DebuggerBrowsableState.Never)]` atribut na vlastnost. To může být užitečné, pokud máte metodu, která musí zůstat v případě důvodu kompatibility rozhraní API, ale měla by být ve skutečnosti metoda.

### <a name="solution-2-have-the-target-code-ask-the-debugger-to-abort-the-evaluation"></a>#2 řešení: Pokud chcete, aby se v ladicím programu přerušuje zkušební verze, obraťte se na něj.

Chybová zpráva vám sdělí název funkce, kterou se ladicí program pokusil zavolat. Pokud metoda getter nebo ToString v některých případech nefunguje správně, zejména v situacích, kdy problém je, že kód potřebuje jiné vlákno ke spuštění kódu, pak funkce implementace může zavolat, `System.Diagnostics.Debugger.NotifyOfCrossThreadDependency` aby mohl ladicí program přerušit vyhodnocení funkce. V tomto řešení je stále možné tyto funkce explicitně vyhodnotit, ale výchozí chování je, že se spuštění zastaví, když dojde k volání NotifyOfCrossThreadDependency.

### <a name="solution-3-disable-all-implicit-evaluation"></a>Řešení #3: Zakázat všechna implicitní vyhodnocení

Pokud předchozí řešení problém nevyřeší, pokračujte na **Tools**  >  **Možnosti**nástroje a zrušte zaškrtněte nastavení **ladění**  >  **Obecné**  >  **Povolit vyhodnocení vlastností a další implicitní volání funkcí**. Tato akce zakáže většinu implicitních vyhodnocení funkcí a tento problém by měl vyřešit.

### <a name="solution-4-enable-managed-compatibility-mode"></a>#4 řešení: Povolit spravovaný režim kompatibility

Pokud přepnete na starší verzi ladicího modulu, možná budete moct tuto chybu eliminovat. V **nabídce nástroje**  >  klikněte na**Možnosti**a vyberte nastavení **ladění**  >  **Obecné**  >  **použití spravovaného režimu kompatibility**. Další informace najdete v tématu [Obecné možnosti ladění](../debugger/general-debugging-options-dialog-box.md).
