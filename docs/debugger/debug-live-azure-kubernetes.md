---
title: Ladění živých ASP.NET služby Azure Kubernetes
description: Zjistěte, jak nastavit snímky snappointů a zobrazit snímky pomocí ladicího programu snímků.
ms.custom: ''
ms.date: 02/11/2019
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
ms.openlocfilehash: 6eb7af4ead7cd58a0ccf36cbeb2b9fc56e890315
ms.sourcegitcommit: 59e5758036223ee866f3de5e3c0ab2b6dbae97b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/23/2019
ms.locfileid: "68415749"
---
# <a name="debug-live-aspnet-azure-kubernetes-services-using-the-snapshot-debugger"></a>Ladění živých ASP.NET služby Azure Kubernetes pomocí ladicího programu snímků

Ladicí program snímek pořídí snímek vašich produkčních aplikací při kódu, který vás zajímá. Chcete-li pokyn ladicí program pořídit snímek, nastavte snappoints a logpoints v kódu. Ladicí program umožňuje přesně zobrazit, co se pokazilo, aniž by to mělo vliv na provoz produkční aplikace. Ladicí program snímek vám může pomoci výrazně zkrátit dobu potřebný k vyřešení problémů, ke kterým dochází v produkčním prostředí.

Snappoints a logpoints jsou podobné zarážky, ale na rozdíl od zarážek snappoints nezastaví aplikace při přístupu. Zachycení snímku v bodě snappoint obvykle trvá 10-20 milisekund.

V tomto kurzu provedete následující:

> [!div class="checklist"]
> * Spuštění ladicího programu snímků
> * Nastavení bodu snappointu a zobrazení snímku
> * Nastavení protokolu

## <a name="prerequisites"></a>Požadavky

* Ladicí program snímků pro služby Azure Kubernetes Services je k dispozici jenom pro Visual Studio 2019 Enterprise nebo vyšší s **úlohou vývoje Azure**. (Na kartě **Jednotlivé komponenty** ji najdete v části **Ladění a testování** > **ladicího programu snímek**.)

    Pokud ještě není nainstalovaná, nainstalujte [Visual Studio 2019 Enterprise](https://visualstudio.microsoft.com/vs/).

* Kolekce snímků je k dispozici pro následující webové aplikace Azure Kubernetes Services:
  * ASP.NET Core aplikace běžící na rozhraní .NET Core 2.2 nebo novější mj.
  * ASP.NET základní aplikace spuštěné na rozhraní .NET Core 2.2 nebo novější v alpine 3.8.
  * ASP.NET Core aplikace běžící na .NET Core 2.2 nebo novější na Ubuntu 18.04.

    > [!NOTE]
    > Abychom vám pomohli povolit podporu pro snímek debugger v AKS jsme poskytli [úložiště obsahující sadu Dockerfiles, které ukazují nastavení na image Docker](https://github.com/Microsoft/vssnapshotdebugger-docker).

## <a name="open-your-project-and-start-the-snapshot-debugger"></a>Otevření projektu a spuštění ladicího programu snímků

1. Otevřete projekt, který chcete snímek ladění.

    > [!IMPORTANT]
    > Chcete-li snímek ladění, je třeba otevřít *stejnou verzi zdrojového kódu,* který je publikován do služby Azure Kubernetes.

1. Zvolte **Ladění > Připojit ladicí program snímku...**. Vyberte prostředek AKS, do který se vaše webová aplikace nasazuje, a účet úložiště Azure a klikněte na **Připojit**. Ladicí program snímků také podporuje [azure app service](debug-live-azure-applications.md) a virtuální počítače Azure [(VM) & škálovací sady virtuálních počítačů](debug-live-azure-virtual-machines.md).

    ![Spuštění ladicího programu snímků z nabídky Ladění](../debugger/media/snapshot-debug-menu-attach.png)

    ![Výběr prostředku Azure](../debugger/media/snapshot-select-azure-resource-aks.png)

    > [!NOTE]
    > (Visual Studio 2019 verze 16.2 a vyšší) Ladicí program snímků povolil cloudovou podporu Azure. Ujistěte se, že prostředek Azure i účet Azure Storage, který vyberete, jsou ze stejného cloudu. Máte-li dotazy týkající se konfigurace dodržování [předpisů Azure](https://azure.microsoft.com/overview/trusted-cloud/) ve vašem podniku, obraťte se na správce Azure.

Visual Studio je nyní v režimu ladění snímek.

   ![Režim ladění snímků](../debugger/media/snapshot-message.png)

   Okno **Moduly** se zobrazí, když všechny moduly mají načteny pro službu Azure App Service (zvolte **ladění > Windows > moduly** otevřít toto okno).

   ![Zkontrolujte okno Moduly](../debugger/media/snapshot-modules.png)

## <a name="set-a-snappoint"></a>Nastavení bodu snappoint

1. V editoru kódu klikněte na levý okap vedle řádku kódu, který vás zajímá, a nastavte tak rychlý bod. Ujistěte se, že je to kód, o kterém víte, že se spustí.

   ![Nastavení bodu snappoint](../debugger/media/snapshot-set-snappoint.png)

1. Kliknutím na **Spustit kolekci** zapněte snappoint.

   ![Zapnutí bodu snappointu](../debugger/media/snapshot-start-collection.png)

    > [!TIP]
    > Při zobrazení snímku nelze krokovat, ale můžete umístit více snappoints v kódu sledovat spuštění na různých řádcích kódu. Pokud máte více snappoints v kódu, ladicí program snímek zajišťuje, že odpovídající snímky jsou ze stejné relace koncového uživatele. Ladicí program snímek to dělá i v případě, že existuje mnoho uživatelů, kteří zasáhli vaši aplikaci.

## <a name="take-a-snapshot"></a>Pořízení snímku

Jakmile je nastaven bod snappoint, můžete buď ručně vygenerovat snímek tím, že přejdete do zobrazení prohlížeče vašeho webu a spotřebujete řádek kódu označený nebo počkejte, až uživatelé vygenerují jeden z jejich použití webu.

## <a name="inspect-snapshot-data"></a>Kontrola dat snímků

1. Po přístupu k snappoint, snímek se zobrazí v okně diagnostické nástroje. Chcete-li otevřít toto okno, zvolte **Ladit > windows > Zobrazit diagnostické nástroje**.

    ![Otevření bodu snappoint](../debugger/media/snapshot-diagsession-window.png)

1. Poklepáním na snappoint otevřete snímek v editoru kódu.

    ![Kontrola dat snímků](../debugger/media/snapshot-inspect-data.png)

    V tomto zobrazení můžete najet na proměnné a zobrazit datové tipy, použít okna **Locals**, **Watch**a **Call Stack** a také vyhodnotit výrazy.

    Samotná webová stránka je stále živá a koncoví uživatelé nejsou ovlivněni. Ve výchozím nastavení je na jeden snappoint zachycen pouze jeden snímek: po zachycení snímku se snappoint vypne. Pokud chcete zachytit další snímek v bodě snappoint, můžete jej znovu zapnout kliknutím na **aktualizovat kolekci**.

Do aplikace můžete taky přidat další snímky snappointu a zapnout je pomocí tlačítka **Aktualizovat kolekci.**

**Potřebujete pomoc?** Stránky pro ladění snímků najdete v [tématu Poradce při potížích a známých problémech](../debugger/debug-live-azure-apps-troubleshooting.md) a [nejčastější dotazy.](../debugger/debug-live-azure-apps-faq.md)

## <a name="set-a-conditional-snappoint"></a>Nastavení podmíněného bodu snappointu

Pokud je obtížné znovu vytvořit určitý stav v aplikaci, zvažte použití podmíněného přichycení. Podmíněné snappoints vám pomohou řídit, kdy chcete pořídit snímek, například když proměnná obsahuje určitou hodnotu, kterou chcete zkontrolovat. Podmínky můžete nastavit pomocí výrazů, filtrů nebo počtu přístupů.

#### <a name="to-create-a-conditional-snappoint"></a>Vytvoření podmíněného bodu snappointu

1. Klepněte pravým tlačítkem myši na ikonu snappointu (dutou kouli) a zvolte **Nastavení**.

   ![Vyberte Nastavení](../debugger/media/snapshot-snappoint-settings.png)

1. Do okna nastavení bodu snappoint zadejte výraz.

   ![Zadání výrazu](../debugger/media/snapshot-snappoint-conditions.png)

   Na předchozím obrázku snímek je přijata pouze `visitor.FirstName == "Dan"`pro snappoint when .

## <a name="set-a-logpoint"></a>Nastavení protokolu

Kromě pořízení snímku při přístupu k snappoint, můžete také nakonfigurovat snappoint pro protokolování zprávy (to znamená vytvořit logpoint). Body protokolu můžete nastavit, aniž byste museli aplikaci znovu nasadit. Logpoints jsou prováděny prakticky a způsobit žádný dopad nebo vedlejší účinky na spuštěné aplikace.

#### <a name="to-create-a-logpoint"></a>Vytvoření protokolu

1. Klikněte pravým tlačítkem myši na ikonu snappointu (modrý šestiúhelník) a zvolte **Nastavení**.

1. V okně nastavení bodu snappoint vyberte **Akce**.

    ![Vytvoření protokolu](../debugger/media/snapshot-logpoint.png)

1. Do pole **Zpráva** můžete zadat novou zprávu protokolu, kterou chcete protokolovat. Můžete také vyhodnotit proměnné ve zprávě protokolu jejich umístěním do složených závorek.

    Pokud zvolíte **Odeslat do výstupního okna**, když je přístupový bod protokolu, zobrazí se zpráva v okně Diagnostické nástroje.

    ![Data protokolu v okně Diagnostické nástroje](../debugger/media/snapshot-logpoint-output.png)

    Pokud zvolíte **Odeslat do protokolu aplikace**, když je přístupový bod `System.Diagnostics.Trace` protokolu, `ILogger` zobrazí se zpráva kdekoli, kde se zobrazují zprávy z (nebo v .NET Core), například [App Insights](/azure/application-insights/app-insights-asp-net-trace-logs).

## <a name="next-steps"></a>Další kroky

V tomto kurzu jste se naučili, jak používat ladicí program snímek pro Azure Kubernetes. Můžete si přečíst další podrobnosti o této funkci.

> [!div class="nextstepaction"]
> [Nejčastější dotazy k ladění snímků](../debugger/debug-live-azure-apps-faq.md)