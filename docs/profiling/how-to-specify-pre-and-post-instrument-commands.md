---
title: 'Postup: Určení příkazů před a po přístrojové desce | Dokumenty společnosti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.property.instrument
helpviewer_keywords:
- profiling tools, pre-instrument events
- events [Visual Studio], pre-instrument
- pre-instrument events, performance tools
ms.assetid: 6a8d5340-1d1b-4d81-88dd-8e1f435eb828
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 22ad5558ed01e5bb1b8d12b7a4cc65b4d677d0cd
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778710"
---
# <a name="how-to-specify-pre--and-post-instrument-commands"></a>Postup: Určení příkazů před a po přístroji

Můžete zadat příkazy, které jsou spuštěny před nebo po binární soubory v relaci výkonu jsou instrumentovány. Jakýkoli příkaz, který může být vydán z příkazového řádku, může být určen jako předpřístroj nebo událost po přístroji. Můžete například zadat příkazy, které automatizují reignování sestavení se silným názvem klíče v dávkovém souboru, který je proveden po instrumentaci binárních souborů.

Můžete zadat příkazy pro všechny instrumentované binární soubory v profilování spustit nebo pro jednotlivé binární soubory. Můžete však zadat pouze jeden příkaz před instrumentací, který se má spustit před, a pouze jeden příkaz po přístrojové desce, který se spustí po procesu instrumentace. Nelze zadat příkazy pro všechny binární soubory i pro jednotlivé binární soubory. Zadáte-li příkazy pro všechny binární soubory, příkazy jsou spuštěny před nebo po instrumentaci každého binárního souboru v relaci.

Pracovní adresář, ve kterém jsou příkazy spouštěny, závisí [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] na operačním systému, ve kterém běžíte, a na cílové platformě profilované aplikace.

Chcete-li získat cestu k nástrojům profilování, přečtěte si informace [o určení cesty k nástrojům příkazového řádku](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).

## <a name="to-specify-pre-instrument-commands"></a>Určení příkazů před přístrojem

1. Proveďte jeden z následujících kroků:

    - Chcete-li zadat příkazy před přístrojem pro všechny binární soubory v relaci výkonu, vyberte uzel relace výkonu v **Průzkumníku výkonu**a potom klepněte pravým tlačítkem myši a vyberte **vlastnosti**.

    - Chcete-li zadat příkazy před pomocí pro určitý binární soubor, klepněte pravým tlačítkem myši na název binárního souboru v seznamu **Cíle** relace výkonu a potom vyberte **příkaz Vlastnosti**.

2. Na **stránkách vlastností**klepněte na **položku Instrumentace**.

3. Zadejte příkaz do textového pole **Příkazový řádek** v části **Události před přístrojem**.

    > [!NOTE]
    > Klepnutím na tlačítko se třemi tečkami **(...),** které sousedí s **polem příkazového řádku,** můžete vyhledat příslušný soubor EXE, CMD nebo .bat.

4. Klikněte na tlačítko **OK**.

     Chcete-li příkaz zakázat, aniž byste ho odebrali, zaškrtněte políčko **Vyloučit z instrumentace.** Chcete-li upravit nastavení kompilátoru nebo propojovacího zařízení, použijte stránky vlastností projektu.

## <a name="to-specify-post-instrument-commands"></a>Určení příkazů po přístroji

1. Proveďte jeden z následujících kroků:

    - Chcete-li zadat příkazy po přístroji pro všechny binární soubory v relaci výkonu, vyberte uzel relace výkonu v **Průzkumníku výkonu**a potom klepněte pravým tlačítkem myši a vyberte **vlastnosti**.

    - Chcete-li zadat příkazy po nástroji pro určitý binární soubor, klepněte pravým tlačítkem myši na název binárního souboru v seznamu **Cíle** relace výkonu a potom vyberte **příkaz Vlastnosti**.

2. Na **stránkách vlastností**klepněte na **položku Instrumentace**.

3. Zadejte příkaz do textového pole **Příkazový řádek** v části **Události po přístroji**.

    > [!NOTE]
    > Klepnutím na tlačítko se třemi tečkami **(...),** které sousedí s **polem příkazového řádku,** můžete vyhledat příslušný soubor EXE, CMD nebo .bat.

4. Klikněte na tlačítko **OK**.

     Chcete-li příkaz zakázat, aniž byste ho odebrali, zaškrtněte políčko **Vyloučit z instrumentace.** Chcete-li upravit nastavení kompilátoru nebo propojovacího zařízení, použijte stránky vlastností projektu.

## <a name="see-also"></a>Viz také

[Konfigurace výkonnostních relací](../profiling/configuring-performance-sessions.md)
