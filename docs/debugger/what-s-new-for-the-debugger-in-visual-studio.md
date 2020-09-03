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
ms.openlocfilehash: 523867a8f9aa074e9122c74deb8bcd91cddd8bee
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "75944220"
---
# <a name="whats-new-for-the-debugger-in-visual-studio-2017"></a>Novinky v ladicím programu v aplikaci Visual Studio 2017

Ladicí program zahrnuje tyto nové funkce:

- Novinka ve verzi 15,5 **Snapshot Debugger** pořizování snímku vašich aplikací v produkčním prostředí, když se spustí kód, který vás zajímá. Chcete-li ladicímu programu dát pokyn k pořízení snímku, nastavte snímkovací body a protokolovacích bodů ve svém kódu. Ladicí program vám umožní zobrazit přesně to, co se nepovedlo, aniž by to ovlivnilo provoz vaší produkční aplikace. Snapshot Debugger vám může výrazně zkrátit dobu potřebnou k vyřešení problémů, ke kterým dochází v produkčních prostředích.

    Kolekce snímků je k dispozici pro následující webové aplikace, které jsou spuštěny v Azure App Service:

  * ASP.NET aplikace spuštěné v .NET Framework 4.6.1 nebo novějším.
  * ASP.NET Core aplikace běžící na rozhraní .NET Core 2,0 nebo novějším ve Windows.

    Další informace najdete v tématu [ladění živých aplikací ASP.NET pomocí Snapshot Debugger](../debugger/debug-live-azure-applications.md).

- Novinka ve verzi 15,5 pouze v Visual Studio Enterprise **IntelliTrace krok za krokem** automaticky převezme snímek aplikace při každé události krok zarážky a ladicího programu. Zaznamenané snímky vám umožní přejít zpět na předchozí zarážky nebo kroky a zobrazit stav aplikace, stejně jako v minulosti. IntelliTraceý krok zpátky vám ušetří čas, když chcete zobrazit předchozí stav aplikace, ale nechcete znovu spustit ladění nebo znovu vytvořit požadovaný stav aplikace.

    Snímky můžete procházet a zobrazovat pomocí tlačítek **krok zpět** a **krok vpřed** na panelu nástrojů ladění. Tato tlačítka přecházejí na události, které se zobrazí na kartě **události** v okně **diagnostické nástroje** .

    ![Krokovat tlačítka zpět a dopředu](../debugger/media/intellitrace-step-back-icons-description.png  "Krokovat tlačítka zpět a dopředu")

    Další informace najdete v tématu [Kontrola stavů předchozích aplikací pomocí stránky IntelliTrace](view-historical-application-state.md) .

- Pomocník pro **výjimky** nahradí pomocníka výjimky a zobrazí se v nemodálním dialogovém okně, kde došlo k chybě. **Pomocník pro výjimky** poskytuje rychlejší přístup k jakýmkoli vnitřním výjimkám, další analýzu ladicího programu (Pokud je k dispozici) a okamžitý přístup k **nastavení výjimky** pro výjimku. Pomocníka výjimky lze také přetáhnout do plovoucího zobrazení, pokud blokuje něco, co potřebujete vidět.

    Například **NullReferenceException** nyní zobrazuje proměnnou, která má nulový odkaz (Další informace).

    ![Pomocník pro výjimky ladicího programu](../debugger/media/dbg-exception-helper.png "DbgExceptionHelper")

    Další informace naleznete v příspěvku na blogu o [použití nového pomocníka výjimky v rámci sady Visual Studio](https://devblogs.microsoft.com/devops/using-the-new-exception-helper-in-visual-studio-15-preview/) .

- V ladicím programu teď můžete spustit na řádek kódu, a to tak, že vyberete ikonu **Spustit** po, zelená ikona šipky (při najetí myší na řádek kódu se zobrazí ikona). Tím se eliminuje nutnost nastavování dočasných zarážek.

    ![Spuštění ladicího programu pro kliknutí](../debugger/media/dbg-run-to-click.png "DbgRunToClick")

- Můžete nastavit podmínky pro výjimky v dialogovém okně **Nastavení výjimek** (to můžete provést pomocí ikony **Upravit podmínku** v dialogovém okně nastavení výjimky nebo pomocí místní nabídky na výjimce.) Aktuálně podporované podmínky zahrnují názvy modulů, které se mají pro výjimku zahrnout nebo vyloučit.

    ![Podmínky pro výjimku](../debugger/media/dbg-conditional-exception.png "DbgConditionalException")

- Dialogové okno připojit k procesu obsahuje novou funkci vyhledávání, která vám pomůže rychleji identifikovat proces, ke kterému se potřebujete připojit.

    ![Hledat v procesu připojit k procesu](../debugger/media/dbg-attach-to-process-search.png "DbgAttachToProcessSearch")

Další informace o těchto nových funkcích naleznete v [poznámkách k verzi [!include[vs_dev15](../misc/includes/vs_dev15_md.md)] pro ](/visualstudio/releasenotes/vs2017-relnotes).

## <a name="see-also"></a>Viz také

- [Ladění v sadě Visual Studio](../debugger/index.yml)
- [První seznámení s ladicím programem](../debugger/debugger-feature-tour.md)