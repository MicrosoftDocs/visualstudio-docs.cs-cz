---
title: 'Postup: Omezit instrumentaci na specifické funkce | Dokumenty společnosti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- performance tools, limiting instrumentation to functions
ms.assetid: bd98d6bf-2560-4eba-b063-2facb09f87c4
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 34a63645933a173e449cf4292cc3d014cc3ec740
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74775316"
---
# <a name="how-to-limit-instrumentation-to-specific-functions"></a>Postup: Omezení instrumentace na konkrétní funkce
Instrumentace a shromažďování dat můžete omezit na jednu nebo více funkcí nastavením možností na stránce **Upřesnit** **v relaci výkonu** nebo na cílové binární stránky vlastností:

- Pokud zadáte funkce na stránce vlastností relace výkonu, jsou ve všech instrumentovaných binárních souborech relace instrumentovány pouze tyto funkce.

- Pokud zadáte funkce na stránce vlastností cílového binárního souboru, jsou instrumentovány pouze ty funkce, které jsou v daném binárním souboru. Funkce v jiných binárních souborech výkonu jsou instrumentovány jako obvykle.

  Omezení shromažďování dat tímto způsobem je podporováno pouze v případě, že je vybrána metoda profilování instrumentace.

> [!NOTE]
> Pomocí stránky **Upřesnit** na stránkách **vlastností Relace výkonu** můžete také nastavit další možnosti, které jsou k dispozici nástroj instrumentace příkazového řádku Profilování Nástroje [VSInstr.](../profiling/vsinstr.md)

### <a name="to-limit-instrumentation-to-specific-functions-in-a-performance-session"></a>Omezení instrumentace na konkrétní funkce v relaci výkonu

1. V **Průzkumníku výkonu**klepněte pravým tlačítkem myši na název relace a potom klepněte na příkaz **Vlastnosti**.

    Zobrazí se dialogové okno **Stránky vlastností**.

2. V dialogovém okně **Stránky vlastností** klepněte na tlačítko **Upřesnit**.

3. Do textového pole **Další možnosti instrumentace** zadejte název funkcí, které chcete instrumentovat, pomocí následující syntaxe:

    **/include:** `FuncSpec` **[;** `FuncSpec` **]**`...`

    `FuncSpec`je název oboru názvů a funkce. Má formát `Namespace` **::**`FunctionName`. Pomocí středníku oddělte více funkcí. Hvězdičkou (\*) můžete zadat zástupný znak pro jeden nebo více znaků. Například **/include:MyNS::\\*** určuje všechny funkce v oboru názvů MyNS.

   > [!NOTE]
   > Chcete-li vypsat funkce v binárním souboru, otevřete okno příkazového řádku v instalačním adresáři Nástroje profilování (viz [Určení cesty k nástrojům příkazového řádku)](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)a zadejte **příkaz vsinstr /DumpFuncs**

### <a name="to-limit-instrumentation-to-specific-functions-in-a-binary"></a>Omezení instrumentace na konkrétní funkce v binárním

1. V **Průzkumníku výkonu**vyhledejte binární název v uzlu **Cíle** relace výkonu.

2. Klepněte pravým tlačítkem myši na binární název a potom klepněte na příkaz **Vlastnosti**.

    Zobrazí se dialogové okno **Stránky vlastností**.

3. V dialogovém okně **Stránky vlastností** klepněte na tlačítko **Upřesnit**.

4. Do textového pole **Další možnosti instrumentace** zadejte název funkcí, které chcete instrumentovat, pomocí následující syntaxe:

    **/include:** `FuncSpec` **[;** `FuncSpec` **]**`...`

    `FuncSpec`je název oboru názvů a funkce. Má formát `Namespace` **::**`FunctionName`. Pomocí středníku oddělte více funkcí. Hvězdičkou (\*) můžete zadat zástupný znak pro jeden nebo více znaků. Například **/include:MyNS::\\*** určuje všechny funkce v oboru názvů MyNS.

   > [!NOTE]
   > Chcete-li vypsat funkce v binárním souboru, otevřete okno příkazového řádku v instalačním adresáři Nástroje profilování (viz [Určení cesty k nástrojům příkazového řádku)](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)a zadejte **příkaz vsinstr /DumpFuncs**

## <a name="see-also"></a>Viz také
- [Řízení shromažďování dat](../profiling/controlling-data-collection.md)
- [Postupy: Omezení instrumentace na konkrétní knihovny DLL](../profiling/how-to-limit-instrumentation-to-specific-dlls.md)
- [Postupy: Určení dalších možností instrumentace](../profiling/how-to-specify-additional-instrumentation-options.md)
