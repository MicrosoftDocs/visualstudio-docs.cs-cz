---
title: Ladění aplikací Azure v reálném ASP.NET
description: Naučte se, jak nastavit snímkovací body a zobrazit snímky pomocí Snapshot Debugger.
ms.custom: ''
ms.date: 03/16/2018
ms.topic: how-to
helpviewer_keywords:
- debugger
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- aspnet
- azure
ms.openlocfilehash: 07ebe8a583717689ca424bf969e7c19e87ebf08e
ms.sourcegitcommit: c076fe12e459f0dbe2cd508e1294af14cb53119f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2020
ms.locfileid: "85350664"
---
# <a name="debug-live-aspnet-azure-apps-using-the-snapshot-debugger"></a>Ladění živých ASP.NET aplikací Azure pomocí Snapshot Debugger

Snapshot Debugger pořizování snímku vašich aplikací v produkčním prostředí, když se zajímá váš kód. Chcete-li ladicímu programu dát pokyn k pořízení snímku, nastavte snímkovací body a protokolovacích bodů ve svém kódu. Ladicí program vám umožní zobrazit přesně to, co se nepovedlo, aniž by to ovlivnilo provoz vaší produkční aplikace. Snapshot Debugger vám může výrazně zkrátit dobu potřebnou k vyřešení problémů, ke kterým dochází v produkčních prostředích.

Snímkovací body a protokolovacích bodů jsou podobné zarážekm, ale na rozdíl od zarážek, snímkovací body aplikaci při volání neukončí. Záznam snímku na snímkovací bod obvykle trvá 10-20 milisekund.

V tomto kurzu provedete následující:

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
  * ASP.NET aplikace spuštěné v .NET Framework 4.6.1 nebo novějším.
  * ASP.NET Core aplikace běžící na rozhraní .NET Core 2,0 nebo novějším ve Windows.

## <a name="open-your-project-and-start-the-snapshot-debugger"></a>Otevřete projekt a spusťte Snapshot Debugger

1. Otevřete projekt, pro který chcete vytvořit snímek ladění.

   > [!IMPORTANT]
   > Chcete-li ladit snímky, je nutné otevřít *stejnou verzi zdrojového kódu* , která je publikována v Azure App Service.

::: moniker range="<=vs-2017"

2. V Průzkumníku cloudu (**zobrazit > Průzkumník cloudu**) klikněte pravým tlačítkem na Azure App Service je projekt nasazený a vyberte **připojit Snapshot Debugger**.

   ![Spustit ladicí program snímků](../debugger/media/snapshot-launch.png)

::: moniker-end

::: moniker range=">=vs-2019"

2. Zvolit **ladění > připojit Snapshot Debugger...**. Vyberte Azure App Service projekt je nasazený a účet úložiště Azure a pak klikněte na **připojit**. Snapshot Debugger také podporuje [službu Azure Kubernetes](debug-live-azure-kubernetes.md) a [& Virtual Machine Scale Sets Azure Virtual Machines (VM)](debug-live-azure-virtual-machines.md).

   ![Spuštění Snapshot debuggeru z nabídky ladění](../debugger/media/snapshot-debug-menu-attach.png)

   ![Vybrat prostředek Azure](../debugger/media/snapshot-select-azure-resource-appservices.png)

::: moniker-end

   > [!IMPORTANT]
   > Při prvním výběru **připojit Snapshot Debugger**budete vyzváni k instalaci rozšíření Snapshot Debugger webu na Azure App Service. Tato instalace vyžaduje restartování Azure App Service.

   ::: moniker range="<=vs-2017"
   > [!NOTE]
   > Rozšíření Application Insights lokality také podporuje ladění snímků. Pokud se vám zobrazí chybová zpráva "rozšíření webu je zastaralé", přečtěte si téma [tipy pro řešení potíží a známé problémy ladění snímků](../debugger/debug-live-azure-apps-troubleshooting.md) pro upgrade podrobností.
   ::: moniker-end
   ::: moniker range=">=vs-2019"
   > [!NOTE]
   > (Visual Studio 2019 verze 16,2 a vyšší) Snapshot Debugger povolili podporu cloudu Azure. Ujistěte se, že se Váš účet Azure Resource i Azure Storage, který vyberete, nachází ve stejném cloudu. Pokud máte dotazy týkající se konfigurace [dodržování předpisů Azure](https://azure.microsoft.com/overview/trusted-cloud/) v rámci vaší organizace, obraťte se prosím na správce Azure.
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

   Z tohoto zobrazení můžete na proměnné umístit ukazatel myši a zobrazit tak tipy, použít **místní**okna, **kukátka**a **zásobník volání** a také vyhodnotit výrazy.

   Samotný web je stále živý a koncoví uživatelé to neovlivní. Ve výchozím nastavení je zachycen pouze jeden snímek na snímkovací bod: po zachycení snímku se snímkovací bod vypne. Pokud chcete zachytit jiný snímek na snímkovací bod, můžete snímkovací bod znovu zapnout kliknutím na **aktualizovat kolekci**.

Do své aplikace můžete také přidat další snímkovací body a zapnout je pomocí tlačítka **aktualizovat kolekci** .

**Potřebujete pomoc?** Podívejte se na téma [řešení potíží a známé problémy](../debugger/debug-live-azure-apps-troubleshooting.md) a [Nejčastější dotazy ke stránkám ladění snímků](../debugger/debug-live-azure-apps-faq.md) .

## <a name="set-a-conditional-snappoint"></a>Nastavení podmíněného snímkovací bod

Pokud je obtížné znovu vytvořit konkrétní stav ve vaší aplikaci, zvažte použití podmíněného snímkovací bod. Podmíněný snímkovací body vám umožňuje řídit, kdy se má pořídit snímek, například když proměnná obsahuje určitou hodnotu, kterou chcete zkontrolovat. Podmínky můžete nastavit pomocí výrazů, filtrů nebo počtu volání.

#### <a name="to-create-a-conditional-snappoint"></a>Vytvoření podmíněného snímkovací bod

1. Klikněte pravým tlačítkem myši na ikonu snímkovací bod (prázdná koule) a vyberte **Nastavení**.

   ![Vyberte Nastavení](../debugger/media/snapshot-snappoint-settings.png)

1. V okně nastavení snímkovací bod zadejte výraz.

   ![Zadejte výraz.](../debugger/media/snapshot-snappoint-conditions.png)

   Na předchozím obrázku se snímek bere pouze pro snímkovací bod, kdy `visitor.FirstName == "Dan"` .

## <a name="set-a-logpoint"></a>Nastavení protokolovací bod

Kromě pořizování snímku, když se snímkovací bod, můžete také nakonfigurovat snímkovací bod tak, aby protokoloval zprávu (to znamená vytvořit protokolovací bod). Můžete nastavit protokolovacích bodů bez nutnosti opětovného nasazení aplikace. Protokolovacích bodů se spouští prakticky a nezpůsobí žádný vliv ani vedlejší účinky na spuštěnou aplikaci.

#### <a name="to-create-a-logpoint"></a>Vytvoření protokolovací bod

1. Klikněte pravým tlačítkem myši na ikonu snímkovací bod (modrý šestiúhelník) a vyberte **Nastavení**.

1. V okně nastavení snímkovací bod vyberte **Akce**.

   ![Vytvoření protokolovací bod](../debugger/media/snapshot-logpoint.png)

1. Do pole **zpráva** můžete zadat novou zprávu protokolu, kterou chcete protokolovat. Můžete také vyhodnotit proměnné ve zprávě protokolu jejich umístěním do složených závorek.

   Pokud zvolíte možnost **Odeslat do okno výstup**, když se protokolovací bod, zpráva se zobrazí v okně diagnostické nástroje.

   ![Protokolovací bod data v okně Diagnostické nástroje](../debugger/media/snapshot-logpoint-output.png)

   Pokud zvolíte **Odeslat do protokolu aplikace**, když se protokolovací bod, zobrazí se zpráva kdekoli, kde vidíte zprávy z `System.Diagnostics.Trace` (nebo `ILogger` v .NET Core), jako je například [App Insights](/azure/application-insights/app-insights-asp-net-trace-logs).

## <a name="next-steps"></a>Další kroky

V tomto kurzu jste se naučili, jak používat Snapshot Debugger pro App Services. Možná budete chtít přečíst si další podrobnosti o této funkci.

> [!div class="nextstepaction"]
> [Nejčastější dotazy k ladění snímků](../debugger/debug-live-azure-apps-faq.md)