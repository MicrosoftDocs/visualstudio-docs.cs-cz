---
title: 'Chyba: Vyhodnocování funkce &#39;funkce&#39; vypršel časový limit a nutné ho přerušit nebezpečným způsobem | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.unsafe_func_eval_abort
ms.technology: vs-ide-debug
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1f36e56b2870d5f099a3b8ed95265fe7e2d688ff
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49934441"
---
# <a name="error-evaluating-the-function-39function39-timed-out-and-needed-to-be-aborted-in-an-unsafe-way"></a>Chyba: Vyhodnocování funkce &#39;funkce&#39; vypršel časový limit a nutné ho přerušit nebezpečným způsobem

Úplný text zprávy: vyhodnocování funkce 'function' vypršel časový limit a je nutné ho přerušit nebezpečným způsobem. To může dojít k poškození cílového procesu. 

Aby bylo snazší kontrolovat stav objektů .NET, ladicí program automaticky vynutí laděného procesu ke spuštění dalšího kódu (obvykle metody getter vlastnosti a funkce ToString). Ve většině scénářů všechny tyto funkce rychlé dokončení a být ladění mnohem snazší. Nicméně ladicí program se nespustí aplikace v izolovaném prostoru. V důsledku toho metoda getter vlastnosti nebo metody ToString, která volá do nativní funkce, která existuje v může vést k dlouhé časové limity, která nemusí být obnovitelné. Pokud dojde k této chybě to došlo k chybě.
 
Jedním z běžných důvodů tohoto problému je, že když ladicí program vyhodnotí vlastnost, umožňuje jenom kontrolován ke spuštění vlákna. Proto pokud vlastnost čeká na ostatní vlákna ke spouštění uvnitř laděného aplikace a čeká, tak, aby modul .NET Runtime není možné přerušit, se stane problém.
 
## <a name="to-correct-this-error"></a>Oprava této chyby
 
Existují tři možné řešení tohoto problému.
 
### <a name="solution-1-prevent-the-debugger-from-calling-the-getter-property-or-tostring-method"></a>Řešení #1: Zabrání ladicí program volání metoda getter vlastnosti nebo metody ToString
 
Název funkce, do které ladicí program se pokusil zavolat vám sdělí chybová zpráva. Pokud upravíte tuto funkci, můžete zabránit ladicí program volání metoda getter vlastnosti nebo metody ToString. Zkuste použijte jeden z následujících akcí:
 
* Změnit metodu na jiný typ kódu kromě metoda getter vlastnosti nebo metody ToString a problém zmizí.
    -nebo-
* (Pro ToString) Definice atributu DebuggerDisplay na typu a může mít jinou hodnotu než ToString vyhodnotit ladicí program.
    -nebo-
* (Pro metoda getter vlastnosti) Vložit `[System.Diagnostics.DebuggerBrowsable(DebuggerBrowsableState.Never)]` atribut na vlastnost. To může být užitečné, pokud máte metodu, která musí zůstat vlastnost z důvodů kompatibility rozhraní API, ale ve skutečnosti měla by být metody.
 
### <a name="solution-2-have-the-target-code-ask-the-debugger-to-abort-the-evaluation"></a>Řešení #2: Cílový kód, požádejte ladicí program se přerušit vyhodnocování máte
 
Název funkce, do které ladicí program se pokusil zavolat vám sdělí chybová zpráva. Metoda getter vlastnosti nebo metody ToString někdy selže-li správně, zejména v situacích, kde je problém, které kód potřebuje jinému vláknu spuštění kódu a pak implementace funkce může volat `System.Diagnostics.Debugger.NotifyOfCrossThreadDependency` žádat ladicí program na přerušení funkce hodnocení. Pomocí tohoto řešení je stále možné explicitně vyhodnotit těchto funkcí, ale výchozí chování je, že provádění zastaví, když dojde k volání NotifyOfCrossThreadDependency.
 
### <a name="solution-3-disable-all-implicit-evaluation"></a>Řešení #3: Zakáže všechny implicitní vyhodnocení
 
Pokud předchozí řešení není problém vyřešit, přejděte na *nástroje* > *možnosti*a zrušte zaškrtnutí políčka *ladění*  >   *Obecné* > *povolit vyhodnocování vlastností a jiných implicitních volání funkcí*. Tím dojde k zakázání většina vyhodnocení implicitní funkce a má problém vyřešit.



  
