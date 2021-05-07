---
title: Ladění živých ASP.NET Azure Kubernetes Services
description: Naučte se používat Snapshot Debugger Visual Studio k nastavení snappointů a pořizování snímků při ladění živého ASP.NET Azure Kubernetes Services.
ms.custom: ''
ms.date: 02/11/2019
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
ms.openlocfilehash: c1c8a593d147b8ba38393aabd89b293e0fbd5d26
ms.sourcegitcommit: d4887ef2ca97c55e2dad9f179eec2c9631d91c95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/06/2021
ms.locfileid: "108798463"
---
# <a name="debug-live-aspnet-azure-kubernetes-services-using-the-snapshot-debugger"></a>Ladění živých ASP.NET Azure Kubernetes Services pomocí Snapshot Debugger

Aplikace Snapshot Debugger snímek vašich aplikací v produkčním prostředí, když se spustí kód, který vás zajímá. Pokud chcete ladicímu programu nastavit pořízení snímku, nastavte v kódu zachytáovací a protokolovací body. Ladicí program umožňuje přesně vidět, co se pokazilo, aniž by to ovlivnilo provoz produkční aplikace. Tento Snapshot Debugger vám může pomoct výrazně zkrátit dobu vyřešit problémy, ke kterým dochází v produkčních prostředích.

Snappointy a protokolové body se podobají zarážek, ale na rozdíl od zarážek nezasáhne při použití funkce snappoints aplikaci. Zachytávání snímku na snímku trvá obvykle 10 až 20 milisekund.

V tomto kurzu:

> [!div class="checklist"]
> * Spuštění Snapshot Debugger
> * Nastavení snímku a zobrazení snímku
> * Nastavení protokolového bodu

## <a name="prerequisites"></a>Požadavky

* Snapshot Debugger pro Azure Kubernetes Services je k dispozici pouze pro Visual Studio 2019 Enterprise nebo vyšší s úlohou **Vývoj pro Azure.** (Na kartě **Jednotlivé komponenty** ji najdete v části Ladění **a testování.**  >  **Ladicí program snímků**.)

    Pokud ještě není nainstalovaný, nainstalujte [Visual Studio 2019 Enterprise.](https://visualstudio.microsoft.com/vs/)

* Kolekce snímků je k dispozici pro následující webové aplikace Azure Kubernetes Services:
  * ASP.NET Core běžící na .NET Core 2.2 nebo novějším v Debianu 9.
  * ASP.NET Core běžící na .NET Core 2.2 nebo novějším v systému Alpine 3.8.
  * ASP.NET Core běžící na .NET Core 2.2 nebo novějším ubuntu 18.04.

    > [!NOTE]
    > Pro pomoc s povolením podpory pro Snapshot Debugger v AKS jsme poskytli repo obsahující sadu [souborů Dockerfile,](https://github.com/Microsoft/vssnapshotdebugger-docker)které ukazují nastavení na imagích Dockeru.

## <a name="open-your-project-and-start-the-snapshot-debugger"></a>Otevřete projekt a spusťte Snapshot Debugger

1. Otevřete projekt, pro který chcete vytvořit snímek ladění.

    > [!IMPORTANT]
    > Chcete-li ladit snímky, je nutné otevřít *stejnou verzi zdrojového kódu* , která je publikována ve službě Azure Kubernetes.

1. Zvolit **ladění > připojit Snapshot Debugger...**. Vyberte prostředek AKS, na který je webová aplikace nasazená, a účet úložiště Azure a pak klikněte na **připojit**. Snapshot Debugger taky podporuje [Azure App Service](debug-live-azure-applications.md) a [Azure Virtual Machines (VM) & Virtual Machine Scale Sets](debug-live-azure-virtual-machines.md).

    ![Spuštění Snapshot debuggeru z nabídky ladění](../debugger/media/snapshot-debug-menu-attach.png)

    ![Vybrat prostředek Azure](../debugger/media/snapshot-select-azure-resource-aks.png)

    > [!NOTE]
    > (Visual Studio 2019 verze 16,2 a vyšší) Snapshot Debugger povolili podporu cloudu Azure. Ujistěte se, že se Váš účet Azure Resource i Azure Storage, který vyberete, nachází ve stejném cloudu. Pokud máte dotazy týkající se konfigurace [dodržování předpisů Azure](https://azure.microsoft.com/overview/trusted-cloud/) v rámci vaší organizace, obraťte se prosím na správce Azure.

Visual Studio je teď v režimu ladění snímků.

   ![Režim ladění snímků](../debugger/media/snapshot-message.png)

   V okně **moduly** se zobrazí, když se všechny moduly načtou pro Azure App Service (pro otevření tohoto okna vyberte **modul ladění > Windows >** ).

   ![Kontrolovat okno modulů](../debugger/media/snapshot-modules.png)

## <a name="set-a-snappoint"></a>Nastavení snímkovací bod

1. V editoru kódu klikněte na levé tlačítko vedle řádku kódu, který vás zajímá, a nastavte snímkovací bod. Ujistěte se, že se jedná o kód, který víte, že se spustí.

   ![Nastavení snímkovací bod](../debugger/media/snapshot-set-snappoint.png)

1. Kliknutím na **Spustit shromažďování** zapněte snímkovací bod.

   ![Zapnout snímkovací bod](../debugger/media/snapshot-start-collection.png)

    > [!TIP]
    > Při prohlížení snímku nemůžete krokovat, ale můžete do kódu umístit několik snappointů, abyste mohli sledovat provádění na různých řádcích kódu. Pokud máte v kódu více snappointů, aplikace Snapshot Debugger, že odpovídající snímky jsou ze stejné relace koncového uživatele. To Snapshot Debugger i v případě, že se k vaší aplikaci dotáhne mnoho uživatelů.

## <a name="take-a-snapshot"></a>Pořízení snímku

Po nastavení snímku můžete snímek vygenerovat ručně tak, že se v prohlížeči zobrazí váš web a po spuštění označeného řádku kódu nebo počkáte, až ho uživatelé vygenerují z používání webu.

## <a name="inspect-snapshot-data"></a>Kontrola dat snímků

1. Po spuštění snímku se v okně snímku Diagnostické nástroje snímku. Pokud chcete toto okno otevřít, zvolte **Ladit > Windows > Zobrazit Diagnostické nástroje**.

    ![Otevření bodu snappoint](../debugger/media/snapshot-diagsession-window.png)

1. Dvojím kliknutím na bod snappoint otevřete snímek v editoru kódu.

    ![Kontrola dat snímků](../debugger/media/snapshot-inspect-data.png)

    V tomto zobrazení můžete najet myší na proměnné a zobrazit popisky dat, použít okna **Místní** **hodnoty,** Sleduje a Zásobník volání a také vyhodnotit výrazy. 

    Samotný web je stále aktivní a koncoví uživatelé na to nemají vliv. Ve výchozím nastavení se pro každý bod snímku zachytá jenom jeden snímek: po zachycení snímku se modul snappoint vypne. Pokud chcete na snímku snímku zapnout další snímek, můžete ho znovu zapnout kliknutím na **Aktualizovat kolekci.**

Do aplikace můžete také přidat další snappointy a zapnout je pomocí **tlačítka Aktualizovat** kolekci.

**Potřebujete pomoc?** Podívejte se na [stránky Řešení potíží a známé problémy](../debugger/debug-live-azure-apps-troubleshooting.md) a Nejčastější dotazy k [ladění](../debugger/debug-live-azure-apps-faq.yml) snímků.

## <a name="set-a-conditional-snappoint"></a>Nastavení podmíněného bodu snappointu

Pokud je obtížné v aplikaci znovu vytvořit konkrétní stav, zvažte použití podmíněného bodu snappoint. Podmíněné moduly snappoint vám pomůžou určit, kdy se má pořaovat snímek, například když proměnná obsahuje konkrétní hodnotu, kterou chcete zkontrolovat. Podmínky můžete nastavit pomocí výrazů, filtrů nebo počtu přístupů.

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

V tomto kurzu jste se naučili, jak používat Snapshot Debugger pro Azure Kubernetes. Možná budete chtít přečíst si další podrobnosti o této funkci.

> [!div class="nextstepaction"]
> [Nejčastější dotazy k ladění snímků](../debugger/debug-live-azure-apps-faq.yml)