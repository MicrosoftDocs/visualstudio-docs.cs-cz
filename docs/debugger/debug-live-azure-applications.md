---
title: Ladění aplikací Azure v reálném ASP.NET
titleSuffix: Visual Studio Enterprise
description: Naučte se používat Snapshot Debugger v sadě Visual Studio k nastavení snímkovací body a pořizování snímků při ladění aplikací Azure Live ASP.NET.
ms.custom: ''
ms.date: 03/16/2018
ms.topic: how-to
helpviewer_keywords:
- debugger
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- aspnet
- azure
ms.openlocfilehash: 94c65814572c99f95d7a6edc6769e5af0ea6e748
ms.sourcegitcommit: d4887ef2ca97c55e2dad9f179eec2c9631d91c95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/06/2021
ms.locfileid: "108798372"
---
# <a name="debug-live-aspnet-azure-apps-using-the-snapshot-debugger"></a>Ladění živých ASP.NET aplikací Azure pomocí Snapshot Debugger

Snapshot Debugger pořizování snímku vašich aplikací v produkčním prostředí, když se zajímá váš kód. Chcete-li ladicímu programu dát pokyn k pořízení snímku, nastavte snímkovací body a protokolovacích bodů ve svém kódu. Ladicí program vám umožní zobrazit přesně to, co se nepovedlo, aniž by to ovlivnilo provoz vaší produkční aplikace. Snapshot Debugger vám může výrazně zkrátit dobu potřebnou k vyřešení problémů, ke kterým dochází v produkčních prostředích.

Snímkovací body a protokolovacích bodů jsou podobné zarážekm, ale na rozdíl od zarážek, snímkovací body aplikaci při volání neukončí. Záznam snímku na snímkovací bod obvykle trvá 10-20 milisekund.

V tomto kurzu:

> [!div class="checklist"]
> * Spusťte Snapshot Debugger
> * Nastavení snímkovací bod a zobrazení snímku
> * Nastavení protokolovací bod

## <a name="prerequisites"></a>Požadavky

* Snapshot Debugger je k dispozici pouze počínaje verzí Visual Studio 2017 Enterprise verze 15,5 nebo vyšší s **úlohou vývoj pro Azure**. (Na kartě **jednotlivé součásti** najdete v části **ladění a testování**  >  **Ladicí program snímků**.)

   ::: moniker range=">=vs-2019"
   Pokud ještě není nainstalován, nainstalujte [Visual Studio 2019](https://visualstudio.microsoft.com/downloads). Pokud aktualizujete z předchozí instalace sady Visual Studio, spusťte Instalační program pro Visual Studio a podívejte se na součást Snapshot Debugger v **ASP.NET a vývoji webu**.
   ::: moniker-end
   ::: moniker range="<=vs-2017"
   Pokud ještě není nainstalovaný, nainstalujte [Visual Studio 2017 Enterprise verze 15,5](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) nebo novější. Pokud aktualizujete z předchozí instalace sady Visual Studio 2017, spusťte Instalační program pro Visual Studio a podívejte se na součást Snapshot Debugger v úloze **vývoje ASP.NET a webu**.
   ::: moniker-end

* Plán Azure App Service Basic nebo vyšší

* Kolekce snímků je k dispozici pro následující webové aplikace, které jsou spuštěny v Azure App Service:
  * ASP.NET aplikace běžící na .NET Framework verze 4.6.1 nebo novější.
  * ASP.NET Core běžící na .NET Core 2.0 nebo novějším ve Windows.

## <a name="open-your-project-and-start-the-snapshot-debugger"></a>Otevřete projekt a spusťte Snapshot Debugger

1. Otevřete projekt, který chcete ladit snímkem.

   > [!IMPORTANT]
   > Pokud chcete ladit snímky, musíte otevřít stejnou *verzi zdrojového* kódu, která je publikovaná ve vašem Azure App Service.

::: moniker range="<=vs-2017"

2. V Průzkumníku cloudu **(Zobrazit > Průzkumník cloudu)** klikněte pravým tlačítkem na Azure App Service, do které je váš projekt nasazený, a vyberte **Attach Snapshot Debugger**.

   ![Spuštění ladicího programu snímků](../debugger/media/snapshot-launch.png)

::: moniker-end

::: moniker range=">=vs-2019"

2. Zvolte **Ladit > Připojit Snapshot Debugger...**. Vyberte Azure App Service, do které je váš projekt nasazený, a účet úložiště Azure, a potom klikněte na **Připojit.** Snapshot Debugger podporuje také [Azure Kubernetes Service](debug-live-azure-kubernetes.md) [a azure Virtual Machines (VM) & Virtual Machine Scale Sets](debug-live-azure-virtual-machines.md).

   ![Spuštění ladicího programu snímků z nabídky Ladit](../debugger/media/snapshot-debug-menu-attach.png)

   ![Výběr prostředku Azure](../debugger/media/snapshot-select-azure-resource-appservices.png)

::: moniker-end

   > [!IMPORTANT]
   > Při prvním výběru možnosti **Připojit Snapshot Debugger** se zobrazí výzva k instalaci rozšíření Snapshot Debugger lokality na Azure App Service. Tato instalace vyžaduje restartování Azure App Service.

   ::: moniker range="<=vs-2017"
   > [!NOTE]
   > Rozšíření Application Insights lokality podporuje také ladění snímků. Pokud se zobrazí chybová zpráva Rozšíření webu je [](../debugger/debug-live-azure-apps-troubleshooting.md) zastaralé, podrobnosti o upgradu najdete v tématu tipy pro řešení potíží a známé problémy s laděním snímků.
   ::: moniker-end
   ::: moniker range=">=vs-2019"
   > [!NOTE]
   > (Visual Studio 2019 verze 16.2 a novější) Snapshot Debugger podporu cloudu Azure. Ujistěte se, že prostředky Azure i Azure Storage, které vyberete, ze stejného cloudu. Pokud máte dotazy ohledně konfigurací dodržování předpisů Azure ve vašem podniku, obraťte se na správce [Azure.](https://azure.microsoft.com/overview/trusted-cloud/)
   ::: moniker-end

   Visual Studio je teď v režimu ladění snímků.
   ![Režim ladění snímků](../debugger/media/snapshot-message.png)

   V okně **moduly** se zobrazí, když se všechny moduly načtou pro Azure App Service (pro otevření tohoto okna vyberte **modul ladění > Windows >** ).

   ![Kontrolovat okno modulů](../debugger/media/snapshot-modules.png)

## <a name="set-a-snappoint"></a>Nastavení snímkovací bod

1. V editoru kódu klikněte na levé tlačítko vedle řádku kódu, který vás zajímá, a nastavte snímkovací bod. Ujistěte se, že se jedná o kód, který víte, že se spustí.

   ![Nastavení snímkovací bod](../debugger/media/snapshot-set-snappoint.png)

2. Kliknutím na **Spustit shromažďování** zapněte snímkovací bod.

   ![Zapnout snímkovací bod](../debugger/media/snapshot-start-collection.png)

   > [!TIP]
   > Nemůžete krokovat při prohlížení snímku, ale v kódu můžete umístit více snímkovací body, aby se mohlo postupovat podle spuštění na různých řádcích kódu. Pokud máte ve svém kódu více snímkovací body, Snapshot Debugger zajistí, aby odpovídající snímky byly ze stejné relace koncového uživatele. Snapshot Debugger to dělá i v případě, že vaše aplikace bude na mnoho uživatelů.

## <a name="take-a-snapshot"></a>Pořízení snímku

Jakmile je snímkovací bod nastaveno, můžete buď ručně vygenerovat snímek, a to tak, že v prohlížeči zobrazíte svůj web a spustíte řádek kódu označený nebo počkejte, než vaši uživatelé vygenerují ze svého používání webu.

## <a name="inspect-snapshot-data"></a>Kontrola dat snímku

1. Když je dosaženo snímkovací bod, zobrazí se snímek v okně Diagnostické nástroje. Chcete-li otevřít toto okno, vyberte možnost **ladění > Windows > zobrazit diagnostické nástroje**.

   ![Otevřít snímkovací bod](../debugger/media/snapshot-diagsession-window.png)

1. Dvojím kliknutím na snímkovací bod otevřete snímek v editoru kódu.

   ![Kontrola dat snímku](../debugger/media/snapshot-inspect-data.png)

   Z tohoto zobrazení můžete na proměnné umístit ukazatel myši a zobrazit tak tipy, použít **místní** okna, **kukátka** a **zásobník volání** a také vyhodnotit výrazy.

   Samotný web je stále živý a koncoví uživatelé to neovlivní. Ve výchozím nastavení se pro každý bod snímku zachytá jenom jeden snímek: po zachycení snímku se modul snappoint vypne. Pokud chcete na snímku snímku zapnout další snímek, můžete ho znovu zapnout kliknutím na **Aktualizovat kolekci.**

Do aplikace můžete také přidat další snappointy a zapnout je pomocí **tlačítka Aktualizovat** kolekci.

**Potřebujete pomoc?** Podívejte se na [stránky Řešení potíží a známé problémy](../debugger/debug-live-azure-apps-troubleshooting.md) a Nejčastější dotazy k [ladění](../debugger/debug-live-azure-apps-faq.yml) snímků.

## <a name="set-a-conditional-snappoint"></a>Nastavení podmíněného bodu snappointu

Pokud je obtížné v aplikaci znovu vytvořit konkrétní stav, zvažte použití podmíněného bodu snappoint. Podmíněné moduly snappoint vám pomůžou určit, kdy se má pořaovat snímek, například když proměnná obsahuje konkrétní hodnotu, kterou chcete zkontrolovat. Podmínky můžete nastavit pomocí výrazů, filtrů nebo počtu přístupů.

#### <a name="to-create-a-conditional-snappoint"></a>Vytvoření podmíněného modulu snappoint

1. Klikněte pravým tlačítkem na ikonu bodu snappoint (prázdný míč) a zvolte **Nastavení**.

   ![Vyberte Nastavení](../debugger/media/snapshot-snappoint-settings.png)

1. V okně nastavení snappointu zadejte výraz.

   ![Zadání výrazu](../debugger/media/snapshot-snappoint-conditions.png)

   Na předchozím obrázku je snímek pořízen pouze pro bod snappoint, když `visitor.FirstName == "Dan"` .

## <a name="set-a-logpoint"></a>Nastavení protokolového bodu

Kromě pořízení snímku při použití snímku můžete také nakonfigurovat modul snappoint pro protokolování zprávy (to znamená vytvořit protokolový bod). Můžete nastavit protokolové body, aniž byste museli aplikaci znovu nasazovat. Logpointy se spouštěly prakticky a nemají žádný vliv ani vedlejší účinky na běžící aplikaci.

#### <a name="to-create-a-logpoint"></a>Vytvoření protokolového bodu

1. Klikněte pravým tlačítkem na ikonu bodu snappoint (modrý šestiúhelník) a zvolte **Nastavení**.

1. V okně nastavení snappointu vyberte **Actions (Akce).**

   ![Vytvoření protokolovací bod](../debugger/media/snapshot-logpoint.png)

1. Do pole **zpráva** můžete zadat novou zprávu protokolu, kterou chcete protokolovat. Můžete také vyhodnotit proměnné ve zprávě protokolu jejich umístěním do složených závorek.

   Pokud zvolíte možnost **Odeslat do okno výstup**, když se protokolovací bod, zpráva se zobrazí v okně diagnostické nástroje.

   ![Protokolovací bod data v okně Diagnostické nástroje](../debugger/media/snapshot-logpoint-output.png)

   Pokud zvolíte **Odeslat do protokolu aplikace**, když se protokolovací bod, zobrazí se zpráva kdekoli, kde vidíte zprávy z `System.Diagnostics.Trace` (nebo `ILogger` v .NET Core), jako je například [App Insights](/azure/application-insights/app-insights-asp-net-trace-logs).

## <a name="next-steps"></a>Další kroky

V tomto kurzu jste se naučili, jak používat Snapshot Debugger pro App Services. Možná budete chtít přečíst si další podrobnosti o této funkci.

> [!div class="nextstepaction"]
> [Nejčastější dotazy k ladění snímků](../debugger/debug-live-azure-apps-faq.yml)