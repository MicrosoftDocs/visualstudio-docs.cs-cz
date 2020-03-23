---
title: Zlepšete dobu spuštění
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "79301865"
---
# <a name="optimize-visual-studio-startup-time"></a>Optimalizace času spuštění sady Visual Studio

Visual Studio je navržen tak, aby se spouštět tak rychle a efektivně, jak je to možné. Některé rozšíření sady Visual Studio a okna nástrojů však může nepříznivě ovlivnit čas spuštění při jejich načtení. Chování pomalých rozšíření a oken nástrojů můžete řídit v dialogovém okně **Spravovat výkon sady Visual Studio.** Další obecné tipy pro zlepšení výkonu najdete v [tématu Visual Studio výkon tipy a triky](../ide/visual-studio-performance-tips-and-tricks.md).

## <a name="startup-behavior"></a>Chování při spuštění

Chcete-li se vyhnout prodloužení doby spuštění, Visual Studio načte rozšíření pomocí přístupu _na vyžádání._ Toto chování znamená, že rozšíření neotevře ihned po spuštění sady Visual Studio, ale podle potřeby. Vzhledem k tomu, že okna nástrojů, která jsou ponechána otevřená v předchozí relaci sady Visual Studio, mohou zpomalit dobu spouštění, otevře sada Visual Studio okna nástrojů inteligentnějším způsobem, aby neovlivnila čas spuštění.

Pokud Visual Studio zjistí pomalé spuštění, zobrazí se automaticky otevíraná zpráva s upozorněním na rozšíření nebo okno nástroje, které způsobuje zpomalení. Zpráva obsahuje odkaz na dialogové **okno Spravovat výkon sady Visual Studio.** K tomuto dialogovému oknu můžete také přistupovat tak, že z panelu nabídek zvolíte **Nápověda** > **ke správě výkonu sady Visual Studio.**

![Správa Visual Studio Performance - vyskakovací okno čtení 'Všimli jsme si, že rozšíření ... zpomaluje visual studio'](../ide/media/vside_perfdialog_popup.png)

V dialogovém okně jsou uvedena rozšíření a nástroje systému Windows, které ovlivňují výkon při spuštění. Chcete-li zlepšit výkon při spuštění, můžete změnit nastavení rozšíření a okna nástroje.

## <a name="to-change-extension-settings-to-improve-startup-solution-load-and-typing-performance"></a><a name="extensions" />Změna nastavení rozšíření za účelem zlepšení výkonu při spuštění, načtení řešení a psaní

1. Otevřete dialogové okno **Spravovat výkon sady Visual Studio** tak, že z panelu nabídek zvolíte **Nápověda** > **ke správě výkonu sady Visual Studio.**

    Pokud rozšíření zpomaluje spuštění sady Visual Studio, načítání nebo psaní řešení, rozšíření se zobrazí v dialogovém okně **Spravovat výkon sady Visual Studio** v části**Spuštění** **rozšíření** > (nebo **načtení nebo** **psaní**řešení).

    ![Správa výkonu sady Visual Studio – zobrazení rozšíření](../ide/media/vside_perfdialog_extensions.png)

2. Zvolte rozšíření, které chcete zakázat, a pak zvolte **tlačítko Zakázat.**

Rozšíření pro budoucí relace můžete vždy znovu povolit pomocí **Správce rozšíření** nebo dialogového okna Spravovat výkon sady **Visual Studio.**

## <a name="to-change-tool-window-settings-to-improve-startup-time"></a><a name="tool-windows" />Změna nastavení okna nástroje za účelem zlepšení doby spuštění

1. Otevřete dialogové okno **Spravovat výkon sady Visual Studio** tak, že z panelu nabídek zvolíte **Nápověda** > **ke správě výkonu sady Visual Studio.**

    Pokud okno nástroje zpomaluje spuštění sady Visual Studio, zobrazí se okno nástroje v dialogovém okně **Spravovat výkon sady Visual Studio** v části Nástroj spuštění **systému** > **Windows**.

2. Zvolte okno nástroje, pro které chcete změnit chování.

3. Zvolte jednu z následujících tří možností:

   - **Použít výchozí chování:** Výchozí chování pro okno nástroje. Pokud si tuto možnost vyberete, výkon při spuštění se nezlepší.

   - **Při spuštění se nezobrazuje okno:** Zadané okno nástroje je vždy zavřeno při otevření sady Visual Studio, i když jste jej nechali otevřené v předchozí relaci. Okno nástroje můžete otevřít z příslušné nabídky, když ho potřebujete.

   - **Automatické skrytí okna při spuštění:** Pokud okno nástroje bylo ponecháno otevřené v předchozí relaci, tato možnost sbalí skupinu okna nástroje při spuštění, aby se zabránilo inicializaci okna nástroje. Tato možnost je dobrou volbou, pokud používáte okno nástroje často. Okno nástroje je stále k dispozici, ale již negativně ovlivňuje čas spuštění sady Visual Studio.

     ![Správa výkonu sady Visual Studio – zobrazení systému Windows nástrojů](../ide/media/vside_perfdialog_toolwindows.png)

> [!NOTE]
> Některé starší verze Visual Studia 2017 měly funkci nazvanou **zjednodušené zatížení řešení**. V aktuálních verzích velké řešení, které obsahují spravovaný kód zatížení mnohem rychleji než dříve, a to i bez načtení zjednodušené řešení.

## <a name="see-also"></a>Viz také

- [Optimalizace výkonu sady Visual Studio](../ide/optimize-visual-studio-performance.md)
- [Tipy a triky pro výkon visual studia](../ide/visual-studio-performance-tips-and-tricks.md)
- [Blog visual studia – rychlejší načítání řešení pomocí Visual Studia 2017 verze 15.6](https://devblogs.microsoft.com/visualstudio/load-solutions-faster-with-visual-studio-2017-version-15-6/)
