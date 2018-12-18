---
title: 'Postupy: Zadejte příkazy před a po instrumentaci | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d8ce82bea823307e02b719fbfae43fe0697aca65
ms.sourcegitcommit: ce154aee5b403d5c1c41da42302b896ad3cf8d82
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/07/2018
ms.locfileid: "34844635"
---
# <a name="how-to-specify-pre--and-post-instrument-commands"></a>Postupy: Zadejte příkazy před a po instrumentaci

Můžete zadat příkazy, které před nebo po jsou vybaveny binárních souborů v relaci výkonu. Všemi příkazy, které můžou být vystavené z příkazového řádku lze zadat jako před instrumentací nebo po instrumentaci událost. Můžete například zadat příkazy, které automatizují opětovného podpisu sestavení se silným názvem klíčem v dávkovém souboru, která se spustí po jsou vybaveny binární soubory.

Můžete zadat příkazy pro všechny instrumentované binární soubory v profilaci spustit nebo jednotlivých binárních souborů. Můžete však zadat jenom jeden příkaz před instrumentací na spuštění před a spustit po dokončení procesu instrumentace jenom jeden příkaz po instrumentaci. Nelze zadat příkazy pro obě všechny binární soubory a jednotlivých binárních souborů. Když zadáte příkazy pro všechny binární soubory, příkazy se spouštějí před nebo po každé binární instrumentace v relaci.

Pracovní adresář, ve kterém jsou prováděny příkazy závisí na operační systen, ve kterém je spuštěn [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] a na cílové platformy PROFILOVANÉHO aplikace.

 **32bitové počítače**

Na 32bitové počítače, je výchozí adresář profileru nástroje *disk\Program 10.0\Team Files\Microsoft Visual Studio Tools nástroje*.

**64bitové počítače**

Na 64bitových počítačích zadejte cestu podle cílové platformy PROFILOVANÉHO aplikace:

- Pro 32bitové aplikace je výchozí adresář profiler nástrojů:

     *disk\Program soubory (x86) \Microsoft Visual Studio 10.0\Team nástrojů nástroje*

- Pro 64bitové aplikace je výchozí adresář profiler nástrojů:

     *disk\Program soubory (x86) \Microsoft Visual Studio 10.0\Team Tools\x64 nástroje*

## <a name="to-specify-pre-instrument-commands"></a>Chcete-li určit příkazy před instrumentací

1. Proveďte jeden z následujících kroků:

    - Příkazy před instrumentací pro všechny binární soubory v relaci výkonu, vyberte uzel relace výkonu v **prohlížeč výkonu**a potom klikněte pravým tlačítkem a vyberte **vlastnosti**.

    - Pokud chcete zadat příkazy před instrumentací pro konkrétní binární, klikněte pravým tlačítkem na název binárního souboru v **cíle** seznam výkonnostní relace a potom vyberte **vlastnosti**.

2. V **stránky vlastností**, klikněte na tlačítko **instrumentace**.

3. Zadejte příkaz v **příkazového řádku** textového pole pod **události před Instrumentací**.

    > [!NOTE]
    > Kliknutí tlačítko se třemi tečkami **(...)**  se přiléhající k **příkazového řádku** pole Procházet a vyberte příslušný soubor .exe, CMD nebo BAT.

4. Click **OK**.

     Zakázat příkaz spouštění bez nutnosti ho odebrat, vyberte **vyloučit z instrumentace** zaškrtávací políčko. Ke změně kompilátoru nebo linkeru nastavení můžete použijte na stránkách vlastností projektu.

## <a name="to-specify-post-instrument-commands"></a>Chcete-li určit příkazy po instrumentaci

1. Proveďte jeden z následujících kroků:

    - Po instrumentaci příkazy pro všechny binární soubory v relaci výkonu, vyberte uzel relace výkonu v **prohlížeč výkonu**a potom klikněte pravým tlačítkem a vyberte **vlastnosti**.

    - Pokud chcete zadat příkazy po instrumentaci pro konkrétní binární, klikněte pravým tlačítkem na název binárního souboru v **cíle** seznam výkonnostní relace a potom vyberte **vlastnosti**.

2. V **stránky vlastností**, klikněte na tlačítko **instrumentace**.

3. Zadejte příkaz v **příkazového řádku** textového pole pod **po instrumentovat svoje události**.

    > [!NOTE]
    > Kliknutí tlačítko se třemi tečkami **(...)**  se přiléhající k **příkazového řádku** pole Procházet a vyberte příslušný soubor .exe, CMD nebo BAT.

4. Click **OK**.

     Zakázat příkaz spouštění bez nutnosti ho odebrat, vyberte **vyloučit z instrumentace** zaškrtávací políčko. Ke změně kompilátoru nebo linkeru nastavení můžete použijte na stránkách vlastností projektu.

## <a name="see-also"></a>Viz také:

[Konfigurace výkonnostních relací](../profiling/configuring-performance-sessions.md)