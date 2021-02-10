---
title: Zadat příkazy před a po instrumentaci | Microsoft Docs
description: Přečtěte si, jak můžete zadat příkazy, které se spouštějí před nebo po binárních souborech v relaci výkonu.
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.performance.property.instrument
helpviewer_keywords:
- profiling tools, pre-instrument events
- events [Visual Studio], pre-instrument
- pre-instrument events, performance tools
ms.assetid: 6a8d5340-1d1b-4d81-88dd-8e1f435eb828
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 7f5bc12a8b0ffb7ef0fa1a78b771ced829f4d73c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99955811"
---
# <a name="how-to-specify-pre--and-post-instrument-commands"></a>Postupy: určení příkazů před a po instrumentaci

Můžete zadat příkazy, které se spustí před nebo po binárních souborech v relaci výkonu. Libovolný příkaz, který lze vydat z příkazového řádku, lze zadat jako událost před instrumentací nebo po instrumentaci. Můžete například zadat příkazy, které automatizují Opětovné podepsání sestavení pomocí klíče silného názvu v dávkovém souboru, který je spuštěn po instrumentaci binárních souborů.

Můžete zadat příkazy pro všechny instrumentované binární soubory při spuštění profilování nebo pro jednotlivé binární soubory. Můžete ale zadat jenom jeden příkaz před instrumentací, který se spustí před a jenom jeden příkaz po instrumentaci, který se spustí po procesu instrumentace. Nemůžete zadat příkazy pro všechny binární soubory a pro jednotlivé binární soubory. Když zadáte příkazy pro všechny binární soubory, příkazy se spustí před nebo po instrumentaci každého binárního souboru v relaci.

Pracovní adresář, ve kterém jsou příkazy provedeny, závisí na operačním systému, ve kterém běží [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] , a na cílové platformě profilované aplikace.

Postup získání cesty k nástrojům pro profilaci najdete v tématu [Určení cesty k nástrojům příkazového řádku](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).

## <a name="to-specify-pre-instrument-commands"></a>Určení příkazů před instrumentací

1. Proveďte jeden z následujících kroků:

    - Chcete-li určit příkazy před instrumentací pro všechny binární soubory v relaci výkonu, vyberte uzel relace výkonu v **prohlížeč výkonu** a potom klikněte pravým tlačítkem myši a vyberte možnost **vlastnosti**.

    - Chcete-li určit příkazy před instrumentací pro konkrétní binární soubor, klikněte pravým tlačítkem myši na název binárního souboru v seznamu **cílů** relace výkonu a poté vyberte možnost **vlastnosti**.

2. Na **stránkách vlastností** klikněte na **instrumentace**.

3. Do textového pole **příkazový řádek** v části **události před instrumentací** zadejte příkaz.

    > [!NOTE]
    > Můžete kliknout na tlačítko se třemi tečkami **(...)** sousedící s polem **příkazového řádku** a vyhledat a vybrat odpovídající soubor. exe,. cmd nebo. bat.

4. Klikněte na **OK**.

     Pokud chcete zakázat spuštění příkazu bez jeho odebrání, zaškrtněte políčko **vyloučit z instrumentace** . Chcete-li upravit nastavení kompilátoru nebo linkeru, použijte stránky vlastností projektu.

## <a name="to-specify-post-instrument-commands"></a>Určení příkazů po instrumentaci

1. Proveďte jeden z následujících kroků:

    - Chcete-li určit příkazy po instrumentaci pro všechny binární soubory v relaci výkonu, vyberte uzel relace výkonu v **prohlížeč výkonu** a potom klikněte pravým tlačítkem myši a vyberte možnost **vlastnosti**.

    - Chcete-li určit příkazy po instrumentaci pro konkrétní binární soubor, klikněte pravým tlačítkem myši na název binárního souboru v seznamu **cílů** relace výkonu a poté vyberte možnost **vlastnosti**.

2. Na **stránkách vlastností** klikněte na **instrumentace**.

3. Do textového pole **příkazový řádek** zadejte příkaz v části **události po instrumentaci**.

    > [!NOTE]
    > Můžete kliknout na tlačítko se třemi tečkami **(...)** sousedící s polem **příkazového řádku** a vyhledat a vybrat odpovídající soubor. exe,. cmd nebo. bat.

4. Klikněte na **OK**.

     Pokud chcete zakázat spuštění příkazu bez jeho odebrání, zaškrtněte políčko **vyloučit z instrumentace** . Chcete-li upravit nastavení kompilátoru nebo linkeru, použijte stránky vlastností projektu.

## <a name="see-also"></a>Viz také

[Konfigurace výkonnostních relací](../profiling/configuring-performance-sessions.md)
