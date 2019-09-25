---
title: Co je nového pro ladicí program v aplikaci Visual Studio 2017 | Microsoft Docs
titleSuffix: ''
ms.date: 01/22/2018
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
manager: jillfra
ms.workload:
- multiple
monikerRange: vs-2017
ms.openlocfilehash: 130387fedce065948ebe09ea605e32cf89ad820b
ms.sourcegitcommit: ea182703e922c74725045afc251bcebac305068a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71210586"
---
# <a name="whats-new-for-the-debugger-in-visual-studio-2017"></a>Novinky v ladicím programu v aplikaci Visual Studio 2017

Ladicí program zahrnuje tyto nové funkce:

- Novinka ve verzi 15,5 **Snapshot Debugger** pořizování snímku vašich aplikací v produkčním prostředí, když se spustí kód, který vás zajímá. Dáte pokyn, aby ladicí program k vytvoření snímku, můžete nastavit snímkovací a protokolovací body ve vašem kódu. Ladicí program umožňuje zobrazit přesně toho, co nefunguje, aniž by to ovlivnilo provozu aplikace v produkčním prostředí. Snapshot Debugger můžete výrazně zkrátit čas potřebný k vyřešení problémů, ke kterým dochází v produkčním prostředí.

    Shromažďování snímků je k dispozici pro následující web apps ve službě Azure App Service:

  * Aplikace ASP.NET spuštěné na rozhraní .NET Framework 4.6.1 nebo novější.
  * Aplikace ASP.NET Core na .NET Core 2.0 nebo novější na Windows.

    Další informace najdete v tématu [ladění živých aplikací ASP.NET pomocí Snapshot Debugger](../debugger/debug-live-azure-applications.md).

- Novinka ve verzi 15,5 pouze v Visual Studio Enterprise **IntelliTrace krok za krokem** automaticky převezme snímek aplikace při každé události krok zarážky a ladicího programu. Zaznamenané snímky umožňují snadno vrátit k předchozím zarážkám nebo krokům a zobrazit stav aplikace jako v minulosti. IntelliTrace zpětným krokem vám může ušetřit čas při chcete zobrazit předchozí stav aplikace, ale nebudete chtít znovu spusťte ladění nebo znovu vytvořit stav požadované aplikace.

    Snímky můžete procházet a zobrazovat pomocí tlačítek **krok zpět** a **krok vpřed** na panelu nástrojů ladění. Tato tlačítka přecházejí na události, které se zobrazí na kartě **události** v okně **diagnostické nástroje** .

    ![Krokovat tlačítka zpět a dopředu](../debugger/media/intellitrace-step-back-icons-description.png  "Krokovat tlačítka zpět a dopředu")

    Další informace najdete v tématu [Kontrola stavů předchozích aplikací pomocí stránky IntelliTrace](../debugger/view-historical-application-state.md) .

- Pomocník pro **výjimky** nahradí pomocníka výjimky a zobrazí se v nemodálním dialogovém okně, kde došlo k chybě. **Pomocník pro výjimky** poskytuje rychlejší přístup k jakýmkoli vnitřním výjimkám, další analýzu ladicího programu (Pokud je k dispozici) a okamžitý přístup k **nastavení výjimky** pro výjimku. Pomocníka výjimky lze také přetáhnout do plovoucího zobrazení, pokud blokuje něco, co potřebujete vidět.

    Například **NullReferenceException** nyní zobrazuje proměnnou, která má nulový odkaz (Další informace).

    ![Pomocník pro výjimky ladicího programu](../debugger/media/dbg-exception-helper.png "DbgExceptionHelper")

    Další informace naleznete v příspěvku na blogu o [použití nového pomocníka výjimky v rámci sady Visual Studio](https://blogs.msdn.microsoft.com/visualstudioalm/2016/03/31/using-the-new-exception-helper-in-visual-studio-15-preview/) .

- V ladicím programu teď můžete spustit na řádek kódu, a to tak, že vyberete ikonu **Spustit** po, zelená ikona šipky (při najetí myší na řádek kódu se zobrazí ikona). Tím se eliminuje nutnost nastavování dočasných zarážek.

    ![Spuštění ladicího programu pro kliknutí](../debugger/media/dbg-run-to-click.png "DbgRunToClick")

- Můžete nastavit podmínky pro výjimky v dialogovém okně **Nastavení výjimek** (to můžete provést pomocí ikony **Upravit podmínku** v dialogovém okně nastavení výjimky nebo pomocí místní nabídky na výjimce.) Aktuálně se podporují příkladem podmínek může být její název modulu pro zahrnutí nebo vyloučení pro výjimku.

    ![Podmínky pro výjimku](../debugger/media/dbg-conditional-exception.png "DbgConditionalException")

- Dialogové okno připojit k procesu obsahuje novou funkci vyhledávání, která vám pomůže rychleji identifikovat proces, ke kterému se potřebujete připojit.

    ![Hledat v procesu připojit k procesu](../debugger/media/dbg-attach-to-process-search.png "DbgAttachToProcessSearch")

Další informace o těchto nových funkcích naleznete v [poznámkách k verzi [!include[vs_dev15](../misc/includes/vs_dev15_md.md)]pro ](/visualstudio/releasenotes/vs2017-relnotes).

## <a name="see-also"></a>Viz také:

- [Ladění v sadě Visual Studio](../debugger/index.yml)
- [První seznámení s ladicím programem](../debugger/debugger-feature-tour.md)