---
title: Co je nového v ladicím programu sady Visual Studio 2017 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 01/22/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, what's new
- what's new [debugger]
- debugging [Visual Studio], what's new
- what's new [Visual Studio], debugging
ms.assetid: 2aed9caa-2384-4e49-8595-82d8b06cf271
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 342cb6c1f014c94bd86363415177ec747b0dc1b7
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49943138"
---
# <a name="whats-new-for-the-debugger-in-includevsdev15miscincludesvsdev15mdmd"></a>Co je nového v ladicím programu [!include[vs_dev15](../misc/includes/vs_dev15_md.md)]

Ladicí program obsahuje tyto nové funkce:

- Nové ve verzi 15.5, **Snapshot Debugger** pořídí snímek vaší aplikace do produkčního prostředí, když spustí kód, který vás zajímá. Dáte pokyn, aby ladicí program k vytvoření snímku, můžete nastavit snímkovací a protokolovací body ve vašem kódu. Ladicí program umožňuje zobrazit přesně toho, co nefunguje, aniž by to ovlivnilo provozu aplikace v produkčním prostředí. Snapshot Debugger můžete výrazně zkrátit čas potřebný k vyřešení problémů, ke kterým dochází v produkčním prostředí.

    Shromažďování snímků je k dispozici pro následující web apps ve službě Azure App Service:

  * Aplikace ASP.NET spuštěné na rozhraní .NET Framework 4.6.1 nebo novější.
  * Aplikace ASP.NET Core na .NET Core 2.0 nebo novější na Windows.

    Další informace najdete v tématu [ladit živé aplikace ASP.NET pomocí ladicího programu snímků](../debugger/debug-live-azure-applications.md).

- Nové ve verzi 15.5 v sadě Visual Studio Enterprise, **zpětného kroku IntelliTrace** automaticky vytvoří snímek vaší aplikace v každé zarážce a ladicí program krok události. Zaznamenané snímky umožňují snadno vrátit k předchozím zarážkám nebo krokům a zobrazit stav aplikace jako v minulosti. IntelliTrace zpětným krokem vám může ušetřit čas při chcete zobrazit předchozí stav aplikace, ale nebudete chtít znovu spusťte ladění nebo znovu vytvořit stav požadované aplikace.

    Můžete procházet a zobrazit snímky pomocí **krok zpět** a **krok vpřed** tlačítka na panelu nástrojů ladění. Tato tlačítka Procházet události, které se zobrazují v **události** kartu **diagnostické nástroje** okna.

    ![Krokovat zpět a vpřed tlačítka](../debugger/media/intellitrace-step-back-icons-description.png  "krok zpět a vpřed tlačítka")

    Další informace najdete v tématu [kontrolovat předchozí nové aplikace pomocí nástroje IntelliTrace](../debugger/view-historical-application-state.md) stránky.

- **Pomocníka výjimky** nahrazuje Pomocníka pro výjimky a se zobrazí v nemodálním dialogovém kde došlo k chybě. **Pomocníka výjimky** poskytuje rychlejší přístup k žádné vnitřní výjimky, další analýzu, ladicí program (Pokud je k dispozici) a okamžitý přístup k **nastavení výjimek** pro výjimku. Pomocníka výjimky lze také přetáhnout do zobrazení s plovoucí desetinnou čárkou Pokud blokuje něco, co potřebujete zobrazit.

    Například **NullReferenceException** nyní zobrazuje proměnné, která má nulový odkaz (Další informace).

    ![Pomocníka pro výjimky ladicího programu](../debugger/media/dbg-exception-helper.png "DbgExceptionHelper")

    Další informace najdete v tématu [pomocí nového pomocníka výjimky v sadě Visual Studio](https://blogs.msdn.microsoft.com/visualstudioalm/2016/03/31/using-the-new-exception-helper-in-visual-studio-15-preview/) blogový příspěvek.

- Teď můžete spustit na řádek kódu během pozastavení v ladicím programu tak, že vyberete **běžet do tohoto místa** ikonou zelené šipky (uvidíte ikonu při najetí myší nad řádek kódu). Tím se eliminuje potřeba nastavovat dočasné zarážky.

    ![Ladicí program je běžet do kliknutí](../debugger/media/dbg-run-to-click.png "DbgRunToClick")

- Můžete nastavit podmínky pro výjimky v **nastavení výjimek** dialogové okno (můžete to provést pomocí **upravit podmínku** v dialogovém okně Nastavení výjimek nebo v nabídce klepněte pravým tlačítkem myši na ikonu došlo k výjimce.) Aktuálně se podporují příkladem podmínek může být její název modulu pro zahrnutí nebo vyloučení pro výjimku.

    ![Podmínky při výskytu výjimky](../debugger/media/dbg-conditional-exception.png "DbgConditionalException")

- Připojte k procesu, dialogové okno obsahuje novou funkci vyhledávání, která může vám umožní rychle identifikovat, které potřebujete k připojení k procesu.

    ![Hledání v připojení k procesu](../debugger/media/dbg-attach-to-process-search.png "DbgAttachToProcessSearch")

Další informace o těchto nových funkcích najdete v článku [zpráva k vydání verze pro [!include[vs_dev15](../misc/includes/vs_dev15_md.md)] ](/visualstudio/releasenotes/vs2017-relnotes#debuggingdiag).

## <a name="see-also"></a>Viz také:

- [Ladění v sadě Visual Studio](../debugger/index.md)
- [Prohlídka funkcí ladicího programu](../debugger/debugger-feature-tour.md)