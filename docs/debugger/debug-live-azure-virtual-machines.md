---
title: Ladění živých ASP.NET virtuálních počítačů a sad škálování pro Azure
description: Naučte se používat Snapshot Debugger v sadě Visual Studio k nastavení snímkovací body a pořizování snímků při ladění živých aplikací ASP.NET na virtuálních počítačích Azure a sadách škálování.
ms.custom: SEO-VS-2020
ms.date: 02/06/2019
ms.topic: how-to
helpviewer_keywords:
- debugger
author: poppastring
ms.author: madownie
manager: andster
monikerRange: '>= vs-2019'
ms.workload:
- aspnet
- azure
ms.openlocfilehash: 9ed85616080859cd69c44c66b442f3f46d81f51a
ms.sourcegitcommit: d577818d3d8e365baa55c6108fa8159c46ed8b43
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2021
ms.locfileid: "97846956"
---
# <a name="debug-live-aspnet-apps-on-azure-virtual-machines-and-azure-virtual-machine-scale-sets-using-the-snapshot-debugger"></a>Ladění živých aplikací ASP.NET na virtuálních počítačích Azure a Azure Virtual Machine Scale Sets pomocí Snapshot Debugger

Snapshot Debugger pořizování snímku vašich aplikací v produkčním prostředí, když se zajímá váš kód. Chcete-li ladicímu programu dát pokyn k pořízení snímku, nastavte snímkovací body a protokolovacích bodů ve svém kódu. Ladicí program vám umožní zobrazit přesně to, co se nepovedlo, aniž by to ovlivnilo provoz vaší produkční aplikace. Snapshot Debugger vám může výrazně zkrátit dobu potřebnou k vyřešení problémů, ke kterým dochází v produkčních prostředích.

Snímkovací body a protokolovacích bodů jsou podobné zarážekm, ale na rozdíl od zarážek, snímkovací body aplikaci při volání neukončí. Záznam snímku na snímkovací bod obvykle trvá 10-20 milisekund.

V tomto kurzu:

> [!div class="checklist"]
> * Spusťte Snapshot Debugger
> * Nastavení snímkovací bod a zobrazení snímku
> * Nastavení protokolovací bod

## <a name="prerequisites"></a>Předpoklady

* Snapshot Debugger pro Azure Virtual Machines (VM) a Azure Virtual Machine Scale Sets jsou k dispozici pouze pro Visual Studio 2019 Enterprise nebo vyšší s **úlohou vývoj pro Azure**. (Na kartě **jednotlivé součásti** najdete v části **ladění a testování**  >  **Ladicí program snímků**.)

    Pokud ještě není nainstalovaný, nainstalujte [Visual Studio 2019 Enterprise](https://visualstudio.microsoft.com/vs/).

* Kolekce snímků je k dispozici pro následující webové aplikace Azure Virtual Machines\Virtual Machine Scale Sets:
  * ASP.NET aplikace spuštěné v .NET Framework 4.6.1 nebo novějším.
  * ASP.NET Core aplikace běžící na rozhraní .NET Core 2,0 nebo novějším ve Windows.

  > [!NOTE]
  >  Visual Studio Enterprise běžící v 32ch oknech nebudou moct zobrazovat snímky.

## <a name="open-your-project-and-start-the-snapshot-debugger"></a>Otevřete projekt a spusťte Snapshot Debugger

1. Otevřete projekt, pro který chcete vytvořit snímek ladění.

    > [!IMPORTANT]
    > Chcete-li ladit snímky, je třeba otevřít *stejnou verzi zdrojového kódu* , která je publikována ve službě Azure Virtual Machine\Virtual Machine Scale set.

1. Zvolit **ladění > připojit Snapshot Debugger...**. Vyberte Azure Virtual Machine\Virtual VM Scale set, ve kterém je vaše webová aplikace nasazená, a účet úložiště Azure a pak klikněte na **připojit**. Snapshot Debugger podporuje taky [službu Azure Kubernetes](debug-live-azure-kubernetes.md) a [Azure App Service](debug-live-azure-applications.md).

    ![Spuštění Snapshot debuggeru z nabídky ladění](../debugger/media/snapshot-debug-menu-attach.png)

    ![Vybrat prostředek Azure](../debugger/media/snapshot-select-azure-resource-vm.png)

    > [!IMPORTANT]
    > Při prvním výběru **připojit Snapshot Debugger** pro váš virtuální počítač se služba IIS automaticky restartuje.
    > Při prvním výběru **připojit Snapshot Debugger** pro Virtual Machine Scale Sets vyžaduje ruční upgrade každé instance Virtual Machine Scale Sets.

    > [!NOTE]
    > (Visual Studio 2019 verze 16,2 a vyšší) Snapshot Debugger povolili podporu cloudu Azure. Ujistěte se, že se Váš účet Azure Resource i Azure Storage, který vyberete, nachází ve stejném cloudu. Pokud máte dotazy týkající se konfigurace [dodržování předpisů Azure](https://azure.microsoft.com/overview/trusted-cloud/) v rámci vaší organizace, obraťte se prosím na správce Azure.

    Metadata pro **moduly** se zpočátku neaktivují, přejděte do webové aplikace a klikněte na tlačítko **Start Collection** (aktivní kolekce). Visual Studio je teď v režimu ladění snímků.

    ![Režim ladění snímků](../debugger/media/snapshot-message.png)

    > [!NOTE]
    > Pro VMSS musí uživatel po prvním připojení Snapshot Debugger ručně upgradovat instance v jejich Virtual Machine Scale Sets.

    V okně **moduly** se zobrazí, když se načtou všechny moduly pro Azure Virtual Machine\Virtual VM Scale (pro otevření tohoto okna vyberte **> moduly pro ladění > Windows** ).

    ![Kontrolovat okno modulů](../debugger/media/snapshot-modules.png)

## <a name="set-a-snappoint"></a>Nastavení snímkovací bod

1. V editoru kódu klikněte na levé tlačítko vedle řádku kódu, který vás zajímá, a nastavte snímkovací bod. Ujistěte se, že se jedná o kód, který víte, že se spustí.

    ![Nastavení snímkovací bod](../debugger/media/snapshot-set-snappoint.png)

1. Kliknutím na **Spustit shromažďování** zapněte snímkovací bod.

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

V tomto kurzu jste se naučili, jak používat Snapshot Debugger pro Azure Virtual Machines a Azure Virtual Machine Scale Sets. Možná budete chtít přečíst si další podrobnosti o této funkci.

> [!div class="nextstepaction"]
> [Nejčastější dotazy k ladění snímků](../debugger/debug-live-azure-apps-faq.md)
