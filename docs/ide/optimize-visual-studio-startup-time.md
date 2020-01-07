---
title: Vylepšení doba spuštění
ms.date: 11/15/2017
ms.topic: conceptual
helpviewer_keywords:
- startup time [Visual Studio]
- optimizing performance [Visual Studio]
- speed up start time [Visual Studio]
ms.assetid: d1508121-8499-4084-8eb5-fa89fa7b17d3
author: TerryGLee
ms.author: tglee
manager: jillfra
f1_keywords:
- vs.performancecenter
ms.workload:
- multiple
ms.openlocfilehash: 4824939b4ef3ed1bc7fa48b2508fc891c984a3c5
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75585779"
---
# <a name="optimize-visual-studio-startup-time"></a>Optimalizace spouštění sady Visual Studio

Visual Studio je navržena pro spuštění jako rychle a efektivně nejvíce. Ale určitá rozšíření sady Visual Studio a okna nástrojů může nepříznivě ovlivnit dobu spuštění, když jsou načteny. Můžete řídit chování rozšíření pomalé a okna nástrojů v **spravovat výkon sady Visual Studio** dialogové okno. Další Obecné tipy pro zvýšení výkonu, naleznete v tématu [a tipy k výkonu sady Visual Studio](../ide/visual-studio-performance-tips-and-tricks.md).

## <a name="startup-behavior"></a>Chování při spuštění

Aby nedošlo k prodloužení doby spuštění, aplikace Visual Studio načítá rozšíření pomocí přístupu _na vyžádání_ . Toto chování znamená, že rozšíření neotevírat okamžitě po spuštění sady Visual Studio, ale podle potřeby. Protože okna nástrojů ponechány otevřené v předchozí relaci sady Visual Studio může zhoršit dobu spuštění, Visual Studio otevře okna nástrojů inteligentnější způsobem, aby se zabránilo dopadu na dobu spuštění.

Pokud sada Visual Studio zjistí pomalé spouštění, zobrazí se místní zpráva, upozorní vás do okna rozšíření nebo nástroj, který je příčinou zpomalení. Zpráva obsahuje odkaz **spravovat výkon sady Visual Studio** dialogové okno. Můžete také přistupovat k dialogovému oknu výběrem **pomáhají** > **spravovat výkon sady Visual Studio** z řádku nabídek.

![Spravovat výkon sady Visual Studio – automaticky otevírané okno pro čtení "Všimli jsme si tuto příponu zpomaluje sady Visual Studio.](../ide/media/vside_perfdialog_popup.png)

Dialogové okno obsahuje nástroje a rozšíření windows, které mají vliv na výkon při spuštění. Můžete změnit nastavení okna nástroje a rozšíření pro zvýšení výkonu při spuštění.

## <a name="a-nameextensions-to-change-extension-settings-to-improve-startup-solution-load-and-typing-performance"></a><a name="extensions" />Chcete-li změnit nastavení rozšíření k vylepšení spouštění, načítání řešení a zadáním výkonu

1. Otevřít **spravovat výkon sady Visual Studio** dialogové okno výběrem **pomáhají** > **spravovat výkon sady Visual Studio** z řádku nabídek.

    Pokud je rozšíření zpomalení při spuštění sady Visual Studio, řešení načítání, nebo zadáte, se rozšíření zobrazí v **spravovat výkon sady Visual Studio** dialogové okno pod **rozšíření**  >   **Po spuštění** (nebo **načtení řešení** nebo **zadáním**).

    ![Spravovat výkon sady Visual Studio – rozšíření zobrazení](../ide/media/vside_perfdialog_extensions.png)

2. Vyberte rozšíření, kterou chcete zakázat, a pak zvolte **zakázat** tlačítko.

Vždy znovu povolíte rozšíření pro budoucí relace pomocí **Správce rozšíření** nebo **spravovat výkon sady Visual Studio** dialogové okno.

## <a name="a-nametool-windows-to-change-tool-window-settings-to-improve-startup-time"></a><a name="tool-windows" />Chcete-li změnit nastavení okna nástroje ke zlepšení času spuštění

1. Otevřít **spravovat výkon sady Visual Studio** dialogové okno výběrem **pomáhají** > **spravovat výkon sady Visual Studio** z řádku nabídek.

    Pokud panel nástrojů je zpomalení při spuštění sady Visual Studio, zobrazí se panel nástrojů v **spravovat výkon sady Visual Studio** dialogové okno pod **nástroj Windows** > **spuštění**.

2. Zvolte panel nástrojů, kterou chcete změnit chování.

3. Vyberte jednu z následujících tří možností:

   - **Použije výchozí chování:** výchozí chování pro panel nástrojů. Udržování tato možnost aktivní, nebude zlepšit výkon při spuštění.

   - **Nezobrazovat okno při spuštění:** okně určeného nástroje je vždy uzavřen, při otevření sady Visual Studio, i pokud jste nechali otevřít v předchozí relaci. Až ji budete potřebovat, můžete otevřít okno nástroje z příslušné nabídky.

   - **Automaticky skrýt okno při spuštění:** ponecháte-li panel nástrojů byl otevřen v předchozí relaci, tato možnost sbalí panel nástrojů skupiny při spuštění, aby inicializace panel nástrojů. Tato možnost je dobrou volbou, když často používáte panelu nástrojů. Panel nástrojů je stále k dispozici, ale má vliv na už nebude mít negativní čas spuštění sady Visual Studio.

     ![Správa výkonu sady Visual Studio – zobrazení okna nástrojů](../ide/media/vside_perfdialog_toolwindows.png)

> [!NOTE]
> Některé starší verze sady Visual Studio 2017 má funkci zvanou **zjednodušené načtení řešení**. V aktuálních verzích velké řešení obsahující spravované kód je mnohem rychlejší než dřív, a to i bez zjednodušeného načtení řešení.

## <a name="see-also"></a>Viz také:

- [Optimalizace výkonu sady Visual Studio](../ide/optimize-visual-studio-performance.md)
- [Tipy k výkonu sady Visual Studio a triky](../ide/visual-studio-performance-tips-and-tricks.md)
- [Blog Visual Studio – zátěžové řešení rychleji s využitím sady Visual Studio 2017 verze 15.6](https://devblogs.microsoft.com/visualstudio/load-solutions-faster-with-visual-studio-2017-version-15-6/)
