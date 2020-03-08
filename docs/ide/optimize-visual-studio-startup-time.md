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
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78408386"
---
# <a name="optimize-visual-studio-startup-time"></a>Optimalizace spouštění sady Visual Studio

Visual Studio je navržena pro spuštění jako rychle a efektivně nejvíce. Ale určitá rozšíření sady Visual Studio a okna nástrojů může nepříznivě ovlivnit dobu spuštění, když jsou načteny. Můžete ovládat chování pomalých rozšíření a oken nástrojů v dialogovém okně **spravovat výkon sady Visual Studio** . Obecnější tipy pro zlepšení výkonu najdete v tématu [tipy a triky pro výkon sady Visual Studio](../ide/visual-studio-performance-tips-and-tricks.md).

## <a name="startup-behavior"></a>Chování při spuštění

Aby nedošlo k prodloužení doby spuštění, aplikace Visual Studio načítá rozšíření pomocí přístupu _na vyžádání_ . Toto chování znamená, že rozšíření neotevírat okamžitě po spuštění sady Visual Studio, ale podle potřeby. Protože okna nástrojů ponechány otevřené v předchozí relaci sady Visual Studio může zhoršit dobu spuštění, Visual Studio otevře okna nástrojů inteligentnější způsobem, aby se zabránilo dopadu na dobu spuštění.

Pokud sada Visual Studio zjistí pomalé spouštění, zobrazí se místní zpráva, upozorní vás do okna rozšíření nebo nástroj, který je příčinou zpomalení. Zpráva poskytuje odkaz na dialogové okno **spravovat výkon sady Visual Studio** . K tomuto dialogovému oknu se dostanete také tak, že v řádku nabídek vyberete **Help** > **spravovat výkon sady Visual Studio** .

![Spravovat výkon sady Visual Studio – automaticky otevírané okno pro čtení "Všimli jsme si tuto příponu zpomaluje sady Visual Studio.](../ide/media/vside_perfdialog_popup.png)

Dialogové okno obsahuje nástroje a rozšíření windows, které mají vliv na výkon při spuštění. Můžete změnit nastavení okna nástroje a rozšíření pro zvýšení výkonu při spuštění.

## <a name="a-nameextensions-to-change-extension-settings-to-improve-startup-solution-load-and-typing-performance"></a><a name="extensions" />ke změně nastavení rozšíření pro zlepšení spouštění, načítání řešení a psaní výkonu

1. Otevřete dialogové okno **spravovat výkon sady Visual Studio** výběrem možnosti **help** > **spravovat výkon sady Visual Studio** z panelu nabídek.

    Pokud rozšíření zpomaluje spuštění sady Visual Studio, načítání řešení nebo psaní, toto rozšíření se zobrazí v dialogovém okně **spravovat výkon sady Visual Studio** v části **rozšíření** > **spuštění** (nebo načtení nebo **zadání** **řešení** ).

    ![Spravovat výkon sady Visual Studio – rozšíření zobrazení](../ide/media/vside_perfdialog_extensions.png)

2. Zvolte rozšíření, které chcete zakázat, a pak klikněte na tlačítko **Zakázat** .

Rozšíření pro budoucí relace můžete kdykoli znovu povolit pomocí **Správce rozšíření** nebo dialogového okna **spravovat výkon sady Visual Studio** .

## <a name="a-nametool-windows-to-change-tool-window-settings-to-improve-startup-time"></a><a name="tool-windows" />ke změně nastavení okna nástroje pro zlepšení času spuštění

1. Otevřete dialogové okno **spravovat výkon sady Visual Studio** výběrem možnosti **help** > **spravovat výkon sady Visual Studio** z panelu nabídek.

    Pokud okno nástroje zpomaluje spuštění sady Visual Studio, okno nástroje se zobrazí v dialogovém okně **spravovat výkon sady Visual Studio** v části **Nástroj Windows** > **po spuštění**.

2. Zvolte panel nástrojů, kterou chcete změnit chování.

3. Vyberte jednu z následujících tří možností:

   - **Použít výchozí chování:** Výchozí chování pro okno nástroje Udržování tato možnost aktivní, nebude zlepšit výkon při spuštění.

   - **Nezobrazovat okno při spuštění:** Zadané okno nástroje je vždy uzavřeno při otevření sady Visual Studio, a to i v případě, že jste ho v předchozí relaci nechali otevřeli. Až ji budete potřebovat, můžete otevřít okno nástroje z příslušné nabídky.

   - **Automaticky skrýt okno při spuštění:** Pokud bylo okno nástroje ponecháno otevřené v předchozí relaci, tato možnost sbalí skupinu okna nástroje při spuštění, aby nedošlo k inicializaci okna nástroje. Tato možnost je dobrou volbou, když často používáte panelu nástrojů. Panel nástrojů je stále k dispozici, ale má vliv na už nebude mít negativní čas spuštění sady Visual Studio.

     ![Správa výkonu sady Visual Studio – zobrazení okna nástrojů](../ide/media/vside_perfdialog_toolwindows.png)

> [!NOTE]
> Některé starší verze sady Visual Studio 2017 měly funkci s názvem **zjednodušené načtení řešení**. V aktuálních verzích velké řešení obsahující spravované kód je mnohem rychlejší než dřív, a to i bez zjednodušeného načtení řešení.

## <a name="see-also"></a>Viz také

- [Optimalizace výkonu sady Visual Studio](../ide/optimize-visual-studio-performance.md)
- [Tipy a triky pro výkon sady Visual Studio](../ide/visual-studio-performance-tips-and-tricks.md)
- [Blog sady Visual Studio – nahrávání řešení rychleji pomocí sady Visual Studio 2017 verze 15,6](https://devblogs.microsoft.com/visualstudio/load-solutions-faster-with-visual-studio-2017-version-15-6/)
