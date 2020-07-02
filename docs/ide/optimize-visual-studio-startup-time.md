---
title: Zlepšit čas spuštění
ms.date: 11/15/2017
ms.topic: how-to
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
ms.openlocfilehash: 399bab1b95a7f17166f205902d04a1abec10e6dd
ms.sourcegitcommit: f27084e64c79e6428746a20dda92795df996fb31
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85770972"
---
# <a name="optimize-visual-studio-startup-time"></a>Optimalizace doby spuštění sady Visual Studio

Aplikace Visual Studio je navržená tak, aby se spouštěla co nejrychleji a co nejefektivněji. Některá rozšíření a okna nástrojů sady Visual Studio ale můžou negativně ovlivnit čas spuštění při jejich načítání. Můžete ovládat chování pomalých rozšíření a oken nástrojů v dialogovém okně **spravovat výkon sady Visual Studio** . Obecnější tipy pro zlepšení výkonu najdete v tématu [tipy a triky pro výkon sady Visual Studio](../ide/visual-studio-performance-tips-and-tricks.md).

## <a name="startup-behavior"></a>Chování při spuštění

Aby nedošlo k prodloužení doby spuštění, aplikace Visual Studio načítá rozšíření pomocí přístupu _na vyžádání_ . Toto chování znamená, že rozšíření se neotevřou ihned po spuštění sady Visual Studio, ale na základě potřeby. Vzhledem k tomu, že okna nástrojů, která zůstala otevřená v předchozí relaci sady Visual Studio, mohou také zpomalit spuštění, Visual Studio otevírá okna nástrojů inteligentním způsobem, aby se předešlo neovlivnění času spuštění.

Pokud aplikace Visual Studio zjistí pomalé spuštění, zobrazí se automaticky otevíraná okna upozorňující na rozšíření nebo panel nástrojů, který způsobuje zpomalení. Zpráva poskytuje odkaz na dialogové okno **spravovat výkon sady Visual Studio** . K tomuto dialogovému oknu můžete získat přístup také tak, že v řádku nabídek kliknete na možnost **help**  >  **Manage Visual Studio Performance** .

![Spravovat výkon sady Visual Studio – místní nabídka čtení si všimli, že rozšíření... zpomaluje Visual Studio](../ide/media/vside_perfdialog_popup.png)

Dialogové okno obsahuje seznam oken rozšíření a nástroje, které mají vliv na výkon při spuštění. Můžete změnit nastavení rozšíření a panelu nástrojů, aby se zlepšil výkon při spuštění.

## <a name="to-change-extension-settings-to-improve-startup-solution-load-and-typing-performance"></a><a name="extensions" />Postup změny nastavení rozšíření pro zlepšení spouštění, načítání řešení a psaní výkonu

1. Otevřete dialogové okno **spravovat výkon sady Visual Studio** výběrem možnosti **help**  >  **spravovat výkon sady Visual Studio** z řádku nabídek.

    Pokud rozšíření zpomaluje spuštění sady Visual Studio, načítání řešení nebo psaní, toto rozšíření se zobrazí v dialogovém okně **spravovat výkon sady Visual Studio** v části spuštění **rozšíření**  >  **Startup** (nebo **načtení** nebo **zadání**řešení).

    ![Správa zobrazení výkon – zobrazení rozšíření pro Visual Studio](../ide/media/vside_perfdialog_extensions.png)

2. Zvolte rozšíření, které chcete zakázat, a pak klikněte na tlačítko **Zakázat** .

Rozšíření pro budoucí relace můžete kdykoli znovu povolit pomocí **Správce rozšíření** nebo dialogového okna **spravovat výkon sady Visual Studio** .

## <a name="to-change-tool-window-settings-to-improve-startup-time"></a><a name="tool-windows" />Změna nastavení okna nástroje pro zlepšení času spuštění

1. Otevřete dialogové okno **spravovat výkon sady Visual Studio** výběrem možnosti **help**  >  **spravovat výkon sady Visual Studio** z řádku nabídek.

    Pokud okno nástroje zpomaluje spuštění sady Visual Studio, okno nástroje se zobrazí v dialogovém okně **spravovat výkon sady Visual Studio** v části **Nástroj spuštění systému Windows**  >  **Startup**.

2. Vyberte okno nástroje, pro které chcete změnit chování.

3. Vyberte jednu z následujících tří možností:

   - **Použít výchozí chování:** Výchozí chování pro okno nástroje Když zachováte tuto možnost, nedojde ke zvýšení výkonu při spuštění.

   - **Nezobrazovat okno při spuštění:** Zadané okno nástroje je vždy uzavřeno při otevření sady Visual Studio, a to i v případě, že jste ho v předchozí relaci nechali otevřeli. Okno nástroje můžete otevřít z příslušné nabídky, až ji budete potřebovat.

   - **Automaticky skrýt okno při spuštění:** Pokud bylo okno nástroje ponecháno otevřené v předchozí relaci, tato možnost sbalí skupinu okna nástroje při spuštění, aby nedošlo k inicializaci okna nástroje. Tato možnost je vhodná, pokud používáte okno nástrojů často. Okno nástroje je stále k dispozici, ale již nemá negativní vliv na dobu spuštění sady Visual Studio.

     ![Správa výkonu sady Visual Studio – zobrazení oken nástrojů](../ide/media/vside_perfdialog_toolwindows.png)

> [!NOTE]
> Některé starší verze sady Visual Studio 2017 měly funkci s názvem **zjednodušené načtení řešení**. V aktuálních verzích velké řešení obsahující spravované kód je mnohem rychlejší než dřív, a to i bez zjednodušeného načtení řešení.

## <a name="see-also"></a>Viz také:

- [Optimalizace výkonu sady Visual Studio](../ide/optimize-visual-studio-performance.md)
- [Tipy a triky pro výkon sady Visual Studio](../ide/visual-studio-performance-tips-and-tricks.md)
- [Blog sady Visual Studio – nahrávání řešení rychleji pomocí sady Visual Studio 2017 verze 15,6](https://devblogs.microsoft.com/visualstudio/load-solutions-faster-with-visual-studio-2017-version-15-6/)
