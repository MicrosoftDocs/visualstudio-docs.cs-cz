---
title: Ladění živých ASP.NET virtuálních počítačů Azure a škálování sad
description: Zjistěte, jak nastavit snímkovací body a zobrazit snímky se Snapshot Debugger.
ms.custom: ''
ms.date: 02/06/2019
ms.topic: conceptual
helpviewer_keywords:
- debugger
author: poppastring
ms.author: madownie
manager: andster
monikerRange: '>= vs-2019'
ms.workload:
- aspnet
- azure
ms.openlocfilehash: ef314cf78c685251496274309af91e3bb2108a1b
ms.sourcegitcommit: 10d16e18c5f5e482c4c2856e6cacaad283463b65
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/09/2020
ms.locfileid: "75776110"
---
# <a name="debug-live-aspnet-apps-on-azure-virtual-machines-and-azure-virtual-machine-scale-sets-using-the-snapshot-debugger"></a>Ladění živých aplikací ASP.NET na virtuálních počítačích Azure a Azure Virtual Machine Scale Sets pomocí Snapshot Debugger

Snapshot Debugger pořídí snímek vaší aplikace do produkčního prostředí, když spustí kód, který vás zajímá. Dáte pokyn, aby ladicí program k vytvoření snímku, můžete nastavit snímkovací a protokolovací body ve vašem kódu. Ladicí program umožňuje zobrazit přesně toho, co nefunguje, aniž by to ovlivnilo provozu aplikace v produkčním prostředí. Snapshot Debugger můžete výrazně zkrátit čas potřebný k vyřešení problémů, ke kterým dochází v produkčním prostředí.

Snímkovací a protokolovací body jsou podobná zarážky, ale na rozdíl od zarážek, není snímkovacích bodů: zastavení aplikace při průchodu. Zachytávání snímků na snímkovacího bodu obvykle trvá 10 20 milisekund.

V tomto kurzu se naučíte:

> [!div class="checklist"]
> * Spuštění ladicího programu snímků
> * Nastavení snímkovacího bodu a zobrazení snímku
> * Nastavte protokolovacích bodů:

## <a name="prerequisites"></a>Požadavky

* Snapshot Debugger pro Azure Virtual Machines (VM) a Azure Virtual Machine Scale Sets jsou k dispozici pouze pro Visual Studio 2019 Enterprise nebo vyšší s **úlohou vývoj pro Azure**. (Na kartě **jednotlivé součásti** najdete v části **ladění a testování** > **Snapshot Debugger**.)

    Pokud ještě není nainstalovaný, nainstalujte [Visual Studio 2019 Enterprise](https://visualstudio.microsoft.com/vs/).

* Kolekce snímků je k dispozici pro následující webové aplikace Azure Virtual Machines\Virtual Machine Scale Sets:
  * Aplikace ASP.NET spuštěné na rozhraní .NET Framework 4.6.1 nebo novější.
  * Aplikace ASP.NET Core na .NET Core 2.0 nebo novější na Windows.

  > [!NOTE]
  >  Visual Studio Enterprise běžící v 32ch oknech nebudou moct zobrazovat snímky.

## <a name="open-your-project-and-start-the-snapshot-debugger"></a>Otevřete svůj projekt a spusťte ladicí program snímků

1. Otevřete projekt, který chcete snímek ladění.

    > [!IMPORTANT]
    > Chcete-li ladit snímky, je třeba otevřít *stejnou verzi zdrojového kódu* , která je publikována ve službě Azure Virtual Machine\Virtual Machine Scale set.

1. Zvolit **ladění > připojit Snapshot Debugger...** . Vyberte Azure Virtual Machine\Virtual VM Scale set, ve kterém je vaše webová aplikace nasazená, a účet úložiště Azure a pak klikněte na **připojit**. Snapshot Debugger podporuje taky [službu Azure Kubernetes](debug-live-azure-kubernetes.md) a [Azure App Service](debug-live-azure-applications.md).

    ![Spuštění Snapshot debuggeru z nabídky ladění](../debugger/media/snapshot-debug-menu-attach.png)

    ![Vybrat prostředek Azure](../debugger/media/snapshot-select-azure-resource-vm.png)

    > [!IMPORTANT]
    > Při prvním výběru **připojit Snapshot Debugger** pro váš virtuální počítač se služba IIS automaticky restartuje.
    > Při prvním výběru **připojit Snapshot Debugger** pro Virtual Machine Scale Sets vyžaduje ruční upgrade každé instance Virtual Machine Scale Sets.

    > [!NOTE]
    > (Visual Studio 2019 verze 16,2 a vyšší) Snapshot Debugger povolili podporu cloudu Azure. Ujistěte se, že se Váš účet Azure Resource i Azure Storage, který vyberete, nachází ve stejném cloudu. Pokud máte dotazy týkající se konfigurace [dodržování předpisů Azure](https://azure.microsoft.com/overview/trusted-cloud/) v rámci vaší organizace, obraťte se prosím na správce Azure.

    Metadata pro **moduly** se zpočátku neaktivují, přejděte do webové aplikace a klikněte na tlačítko **Start Collection** (aktivní kolekce). Visual Studio je nyní v režimu ladění snímků.

    ![Režim ladění snímků](../debugger/media/snapshot-message.png)

    > [!NOTE]
    > Pro VMSS musí uživatel po prvním připojení Snapshot Debugger ručně upgradovat instance v jejich Virtual Machine Scale Sets.

    V okně **moduly** se zobrazí, když se načtou všechny moduly pro Azure Virtual Machine\Virtual VM Scale (pro otevření tohoto okna vyberte **> moduly pro ladění > Windows** ).

    ![Zkontrolujte okno modulů](../debugger/media/snapshot-modules.png)

## <a name="set-a-snappoint"></a>Nastavte snímkovacího bodu

1. V editoru kódu klikněte na levé tlačítko vedle řádku kódu, který vás zajímá, a nastavte snímkovací bod. Ujistěte se, že se jedná o kód, který víte, že se spustí.

    ![Nastavte snímkovacího bodu](../debugger/media/snapshot-set-snappoint.png)

1. Klikněte na tlačítko **spustit shromažďování** zapnout snímkovacího bodu.

    ![Zapnout snímkovací bod](../debugger/media/snapshot-start-collection.png)

    > [!TIP]
    > Nelze krok při zobrazení snímku, ale můžete umístit více snímkovacích bodů: ve vašem kódu sledovat provádění na různé řádky kódu. Pokud máte více snímkovacích bodů: ve vašem kódu, Snapshot Debugger zajišťují, že odpovídající snímky se ze stejné relace koncového uživatele. Snapshot Debugger nepodporuje to i v případě, že existují mnoho uživatelé, kteří vyvolávají vaší aplikace.

## <a name="take-a-snapshot"></a>Pořízení snímku

Jakmile je snímkovací bod nastaveno, můžete buď ručně vygenerovat snímek, a to tak, že v prohlížeči zobrazíte svůj web a spustíte řádek kódu označený nebo počkejte, než vaši uživatelé vygenerují ze svého používání webu.

## <a name="inspect-snapshot-data"></a>Kontrolovat data snímku

1. Při dosažení snímkovacího bodu, se zobrazí v okně diagnostické nástroje snímku. Chcete-li otevřít toto okno, vyberte možnost **ladění > Windows > zobrazit diagnostické nástroje**.

    ![Otevřete snímkovacího bodu](../debugger/media/snapshot-diagsession-window.png)

1. Dvakrát klikněte na panel snímkovacího bodu otevřete snímku v editoru kódu.

    ![Kontrolovat data snímku](../debugger/media/snapshot-inspect-data.png)

    V tomto zobrazení můžete najedete myší proměnné, které chcete zobrazit datové tipy, použijte **lokální**, **hodinky**, a **zásobník volání** windows a také vyhodnocujte výrazy.

    Samotný web je stále živý a koncoví uživatelé to neovlivní. Pouze jeden snímek je ve výchozím nastavení zaznamenávány za snímkovacích bodů: Po zachycení snímku snímkovací bod vypne. Pokud chcete zaznamenat další snímek na snímkovacího bodu, můžete zapnout snímkovací bod zpět kliknutím **aktualizovat shromažďování**.

Můžete také přidat další snímkovací body do vaší aplikace a je zapnout pomocí **aktualizovat shromažďování** tlačítko.

**Potřebujete pomoc?** Zobrazit [řešení potíží a známé problémy](../debugger/debug-live-azure-apps-troubleshooting.md) a [– nejčastější dotazy k ladění snímků](../debugger/debug-live-azure-apps-faq.md) stránky.

## <a name="set-a-conditional-snappoint"></a>Nastavit podmíněné snímkovací bod

Pokud je obtížné znovu vytvořit konkrétní stav ve vaší aplikaci, zvažte použití podmíněného snímkovací bod. Podmíněný snímkovací body vám umožňuje řídit, kdy se má pořídit snímek, například když proměnná obsahuje určitou hodnotu, kterou chcete zkontrolovat. Můžete nastavit podmínky, které využívají výrazy a filtry, nebo počtu položek.

#### <a name="to-create-a-conditional-snappoint"></a>Chcete-li vytvořit podmíněného snímkovací bod

1. Klikněte pravým tlačítkem na ikonu snímkovací bod (prázdný koule) a zvolte **nastavení**.

   ![Zvolit nastavení](../debugger/media/snapshot-snappoint-settings.png)

1. V okně Nastavení snímkovací bod zadejte výraz.

   ![Zadejte výraz](../debugger/media/snapshot-snappoint-conditions.png)

   V předchozí ilustraci snímku pouze prováděné na snímkovací bod při `visitor.FirstName == "Dan"`.

## <a name="set-a-logpoint"></a>Nastavte protokolovacích bodů:

Kromě pořízení snímku při dosažení snímkovacího bodu, můžete také nakonfigurovat snímkovací bod k zaznamenání zprávy (to znamená, vytvořit protokolovacích bodů:). Můžete nastavit protokolovací body bez nutnosti nasazení vaší aplikace. Protokolovací body prakticky spustí a způsobit, že žádný dopad nebo vedlejší účinky k běžící aplikaci.

#### <a name="to-create-a-logpoint"></a>Chcete-li vytvořit protokolovacích bodů:

1. Klikněte pravým tlačítkem na ikonu snímkovací bod (modré šestiúhelník) a zvolte **nastavení**.

1. V okně Nastavení snímkovací bod vyberte **akce**.

    ![Vytvoření protokolovacích bodů:](../debugger/media/snapshot-logpoint.png)

1. Do pole **zpráva** můžete zadat novou zprávu protokolu, kterou chcete protokolovat. Můžete také vyhodnotit proměnné ve zprávě protokolu je umístit uvnitř složených závorek.

    Pokud se rozhodnete **odeslat do okna výstup**, když protokolovacích bodů: dosažení, zpráva se zobrazí v okně diagnostické nástroje.

    ![Protokolovací bod data v okně Diagnostické nástroje](../debugger/media/snapshot-logpoint-output.png)

    Pokud se rozhodnete **odeslat do protokolu aplikace**, když protokolovacích bodů: dosažení, zpráva se zobrazí kdekoli, zobrazí se zprávy z `System.Diagnostics.Trace` (nebo `ILogger` v .NET Core), například [App Insights](/azure/application-insights/app-insights-asp-net-trace-logs).

## <a name="next-steps"></a>Další kroky

V tomto kurzu jste se naučili, jak používat Snapshot Debugger pro Azure Virtual Machines a Azure Virtual Machine Scale Sets. Můžete chtít přečtěte si další podrobnosti o této funkci.

> [!div class="nextstepaction"]
> [Nejčastější dotazy k ladění snímků](../debugger/debug-live-azure-apps-faq.md)
