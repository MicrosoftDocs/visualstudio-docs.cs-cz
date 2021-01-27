---
title: Omezení instrumentace na konkrétní funkce | Microsoft Docs
description: Přečtěte si, jak omezit instrumentaci a shromažďování dat na jednu nebo více funkcí, a to nastavením možností na stránce Upřesnit nebo v cílových binárních vlastnostech stránky.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- performance tools, limiting instrumentation to functions
ms.assetid: bd98d6bf-2560-4eba-b063-2facb09f87c4
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 92825f77b1c94a7545b399dbc1cb35ecefb8218d
ms.sourcegitcommit: 8e15b434bf5db3e0f719320ca82682df1a3da110
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/27/2021
ms.locfileid: "98883329"
---
# <a name="how-to-limit-instrumentation-to-specific-functions"></a>Postupy: omezení instrumentace na konkrétní funkce
Instrumentaci a shromažďování dat můžete omezit na jednu nebo více funkcí tak, že nastavíte možnosti na stránce **Upřesnit** v části **relace výkonu** nebo cílové binární vlastnosti:

- Pokud zadáte funkce na stránce vlastností relace výkonu, budou instrumentovat pouze tyto funkce v rámci všech instrumentované binárních souborů relace.

- Zadáte-li funkce na stránce vlastností cílového binárního souboru, budou instrumentované pouze ty funkce, které jsou v tomto konkrétním binárním souboru. Funkce v dalších binárních souborech výkonu jsou instrumentované jako obvykle.

  Omezení shromažďování dat tímto způsobem se podporuje jenom v případě, že je vybraná metoda profilace instrumentace.

> [!NOTE]
> Můžete také použít stránku **Upřesnit** na stránce vlastností **relace výkonu** a nastavit další možnosti, které jsou k dispozici pro nástroj nástroje pro profilaci [VSInstr](../profiling/vsinstr.md) příkazového řádku nástroje pro instrumentaci.

### <a name="to-limit-instrumentation-to-specific-functions-in-a-performance-session"></a>Omezení instrumentace na konkrétní funkce v relaci výkonu

1. V **prohlížeč výkonu** klikněte pravým tlačítkem na název relace a pak klikněte na **vlastnosti**.

    Zobrazí se dialogové okno **Stránky vlastností**.

2. V dialogovém okně **stránky vlastností** klikněte na tlačítko **Upřesnit**.

3. Do textového pole **Další možnosti instrumentace** zadejte název funkcí, které chcete instrumentovat, pomocí následující syntaxe:

    **/include:** `FuncSpec` **[;** `FuncSpec` **]**`...`

    `FuncSpec` je název oboru názvů a funkce. Má formát `Namespace` **::** `FunctionName` . K oddělení více funkcí použijte středník. Pomocí hvězdičky ( \* ) zadejte zástupný znak pro jeden nebo více znaků. Například **/include: MyNS:: \\** _ určuje všechny funkce v oboru názvů MyNS.

   > [!NOTE]
   > Pokud chcete zobrazit seznam funkcí v binárním souboru, otevřete okno příkazového řádku v instalačním adresáři Nástroje pro profilaci (podívejte se na téma [Určení cesty k nástrojům příkazového řádku](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)) a pak zadejte _ *VSInstr/DumpFuncs* .*

### <a name="to-limit-instrumentation-to-specific-functions-in-a-binary"></a>Omezení instrumentace na konkrétní funkce v binárním souboru

1. V **prohlížeč výkonu** vyhledejte binární název v uzlu **cíle** relace výkonu.

2. Klikněte pravým tlačítkem na název binárního souboru a pak klikněte na **vlastnosti**.

    Zobrazí se dialogové okno **Stránky vlastností**.

3. V dialogovém okně **stránky vlastností** klikněte na tlačítko **Upřesnit**.

4. Do textového pole **Další možnosti instrumentace** zadejte název funkcí, které chcete instrumentovat, pomocí následující syntaxe:

    **/include:** `FuncSpec` **[;** `FuncSpec` **]**`...`

    `FuncSpec` je název oboru názvů a funkce. Má formát `Namespace` **::** `FunctionName` . K oddělení více funkcí použijte středník. Pomocí hvězdičky ( \* ) zadejte zástupný znak pro jeden nebo více znaků. Například **/include: MyNS:: \\** _ určuje všechny funkce v oboru názvů MyNS.

   > [!NOTE]
   > Pokud chcete zobrazit seznam funkcí v binárním souboru, otevřete okno příkazového řádku v instalačním adresáři Nástroje pro profilaci (podívejte se na téma [Určení cesty k nástrojům příkazového řádku](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)) a pak zadejte _ *VSInstr/DumpFuncs* .*

## <a name="see-also"></a>Viz také
- [Řízení shromažďování dat](../profiling/controlling-data-collection.md)
- [Postupy: Omezení instrumentace na konkrétní knihovny DLL](../profiling/how-to-limit-instrumentation-to-specific-dlls.md)
- [Postupy: Určení dalších možností instrumentace](../profiling/how-to-specify-additional-instrumentation-options.md)
