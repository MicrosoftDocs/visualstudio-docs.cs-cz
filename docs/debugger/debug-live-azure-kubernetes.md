---
title: Ladění za provozu služby Azure Kubernetes technologie ASP.NET
description: Zjistěte, jak nastavit snímkovací body a zobrazit snímky se Snapshot Debugger.
ms.custom: ''
ms.date: 02/11/2019
ms.topic: conceptual
helpviewer_keywords:
- debugger
author: poppastring
ms.author: madownie
manager: andster
monikerRange: vs-2019
ms.workload:
- aspnet
- azure
ms.openlocfilehash: b3bbffc0ae04fa9a91739a14ce4b0b4d85215ea8
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/18/2019
ms.locfileid: "56335917"
---
# <a name="debug-live-aspnet-azure-kubernetes-services-using-the-snapshot-debugger"></a>Ladění služby Azure Kubernetes za provozu technologie ASP.NET se pomocí ladicího programu snímků

Snapshot Debugger pořídí snímek vaší aplikace do produkčního prostředí, když spustí kód, který vás zajímá. Dáte pokyn, aby ladicí program k vytvoření snímku, můžete nastavit snímkovací a protokolovací body ve vašem kódu. Ladicí program umožňuje zobrazit přesně toho, co nefunguje, aniž by to ovlivnilo provozu aplikace v produkčním prostředí. Snapshot Debugger můžete výrazně zkrátit čas potřebný k vyřešení problémů, ke kterým dochází v produkčním prostředí.

Snímkovací a protokolovací body jsou podobná zarážky, ale na rozdíl od zarážek, není snímkovacích bodů: zastavení aplikace při průchodu. Zachytávání snímků na snímkovacího bodu obvykle trvá 10 20 milisekund.

V tomto kurzu se naučíte:

> [!div class="checklist"]
> * Spuštění ladicího programu snímků
> * Nastavení snímkovacího bodu a zobrazení snímku
> * Nastavte protokolovacích bodů:

## <a name="prerequisites"></a>Požadavky

* Snapshot Debugger pro služby Azure Kubernetes, pouze je dostupná ve verzi preview sady Visual Studio. 2019 Enterprise nebo vyšší s **funkcí vývoj pro Azure**. (V části **jednotlivé komponenty** kartu, najdete ho pod **ladění a testování** > **Snapshot debugger**.)

    Pokud ještě není nainstalovaný, nainstalujte [ve verzi preview sady Visual Studio Enterprise. 2019](https://visualstudio.microsoft.com/vs/preview/).

* Shromažďování snímků je k dispozici pro následující web apps služby Azure Kubernetes:
  * Aplikace ASP.NET Core spuštěné v .NET Core 2.2 nebo vyšší na Debian 9.
  * Aplikace ASP.NET Core na .NET Core 2.2 nebo později Alpine 3.8.
  * Aplikace ASP.NET Core na .NET Core 2.2 nebo později Ubuntu 18.04.

    > [!NOTE]
    > Můžete povolit podporu pro Snapshot Debugger ve službě AKS uvádíme [úložiště obsahující sadu soubory Dockerfile, které ukazují instalační program na imagích Dockeru](https://github.com/Microsoft/vssnapshotdebugger-docker).

## <a name="open-your-project-and-start-the-snapshot-debugger"></a>Otevřete svůj projekt a spusťte ladicí program snímků

1. Otevřete projekt, který chcete snímek ladění.

    > [!IMPORTANT]
    > K ladění snímků, budete muset otevřít *stejnou verzi zdrojového kódu* , který je publikován do služby Azure Kubernetes.

1. Připojte Snapshot Debugger. Můžete použít jeden z několika různými způsoby:

    * Zvolte **ladit > připojit Snapshot Debugger...** . Vyberte prostředek AKS nasazuje se do vaší webové aplikace a účtu služby Azure storage a klikněte na **připojit**.
  
      ![Spuštění ladicího programu snímků z nabídky ladění](../debugger/media/snapshot-debug-menu-attach.png)

    * Klikněte pravým tlačítkem myši na projekt a vyberte **publikovat**a pak na stránce klikněte na publikovat **připojit Snapshot Debugger**. Vyberte prostředek AKS nasazuje se do vaší webové aplikace a účtu služby Azure storage a klikněte na **připojit**.
    ![Spuštění ladicího programu snímků ze stránky publikovat](../debugger/media/snapshot-publish-attach.png)

    * V ladění cíl rozevírací nabídky vyberte možnost **Snapshot Debugger**, přístupů **F5** a v případě potřeby vyberte prostředek AKS nasazuje se do vaší webové aplikace a služby Azure storage account a pak klikněte na tlačítko  **Připojit**.
    ![Spuštění ladicího programu snímků z rozevírací nabídky F5](../debugger/media/snapshot-F5-dropdown-attach.png)

    * Pomocí Průzkumníka cloudu (**zobrazení > Průzkumník cloudu**), klikněte pravým tlačítkem na vaší webové aplikace se nasadí do prostředku AKS a účtu služby Azure storage a potom klikněte na tlačítko **připojit Snapshot Debugger**.
  
      ![Spuštění ladicího programu snímků z Průzkumníka cloudu](../debugger/media/snapshot-launch.png)

    > [!NOTE]
    > Rozšíření webu Application Insights podporuje také ladění snímků. Pokud narazíte na chybovou zprávu "aktuální rozšíření webu", přečtěte si téma [řešení potíží, tipy a známé problémy pro ladění snímků](../debugger/debug-live-azure-apps-troubleshooting.md) pro upgrade podrobnosti.

   ![Režim ladění snímků](../debugger/media/snapshot-message.png)

   **Moduly** okno zobrazuje, když jste načetli všech modulů pro službu Azure App Service (zvolte **ladit > Windows > moduly** otevřete toto okno).

   ![Zkontrolujte okno modulů](../debugger/media/snapshot-modules.png)

## <a name="set-a-snappoint"></a>Nastavte snímkovacího bodu

1. V editoru kódu klikněte na levém hřbetu vedle řádku kódu, které vás zajímají nastavení snímkovacího bodu. Ujistěte se, že je kód, o kterém víte, že se spustí.

   ![Nastavte snímkovacího bodu](../debugger/media/snapshot-set-snappoint.png)

1. Klikněte na tlačítko **spustit shromažďování** zapnout snímkovacího bodu.

   ![Zapnout snímkovací bod](../debugger/media/snapshot-start-collection.png)

    > [!TIP]
    > Nelze krok při zobrazení snímku, ale můžete umístit více snímkovacích bodů: ve vašem kódu sledovat provádění na různé řádky kódu. Pokud máte více snímkovacích bodů: ve vašem kódu, Snapshot Debugger zajišťují, že odpovídající snímky se ze stejné relace koncového uživatele. Snapshot Debugger nepodporuje to i v případě, že existují mnoho uživatelé, kteří vyvolávají vaší aplikace.

## <a name="take-a-snapshot"></a>Pořízení snímku

Když snímkovacího bodu je zapnutá, budou se pokaždé, když se spustí na řádek kódu, kde je umístěn snímkovací bod zachytit snímek. Toto spuštění může být způsobeno skutečné žádosti na serveru. K vynucení vašich snímkovací bod přístupů, přejdete na zobrazení prohlížeče vašeho webu a provádět všechny akce požadované to způsobit vaší snímkovací bod k.

## <a name="inspect-snapshot-data"></a>Kontrolovat data snímku

1. Při dosažení snímkovacího bodu, se zobrazí v okně diagnostické nástroje snímku. Chcete-li otevřít toto okno, zvolte **ladit > Windows > zobrazit diagnostické nástroje**.

   ![Otevřete snímkovacího bodu](../debugger/media/snapshot-diagsession-window.png)

1. Dvakrát klikněte na panel snímkovacího bodu otevřete snímku v editoru kódu.

   ![Kontrolovat data snímku](../debugger/media/snapshot-inspect-data.png)

   V tomto zobrazení můžete najedete myší proměnné, které chcete zobrazit datové tipy, použijte **lokální**, **hodinky**, a **zásobník volání** windows a také vyhodnocujte výrazy.

    Je webem jako takovým stále aktivní a nejsou to vliv na koncové uživatele. Pouze jeden snímek je ve výchozím nastavení zaznamenávány za snímkovacích bodů: Po zachycení snímku snímkovací bod vypne. Pokud chcete zaznamenat další snímek na snímkovacího bodu, můžete zapnout snímkovací bod zpět kliknutím **aktualizovat shromažďování**.

Můžete také přidat další snímkovací body do vaší aplikace a je zapnout pomocí **aktualizovat shromažďování** tlačítko.

**Potřebujete pomoc?** Zobrazit [řešení potíží a známé problémy](../debugger/debug-live-azure-apps-troubleshooting.md) a [– nejčastější dotazy k ladění snímků](../debugger/debug-live-azure-apps-faq.md) stránky.

## <a name="set-a-conditional-snappoint"></a>Nastavit podmíněné snímkovací bod

Pokud je obtížné znovu vytvořit určitého stavu ve vaší aplikaci, zvažte, zda může pomoci použití podmíněné snímkovacího bodu. Podmíněné snímkovací body umožňují předcházet pořízení snímku, dokud aplikace přejde do požadovaného stavu, například pokud má proměnná určitou hodnotu, kterou chcete zkontrolovat. Můžete nastavit podmínky, které využívají výrazy a filtry, nebo počtu položek.

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

1. V **zpráva** pole, můžete zadat novou zprávu protokolu, chcete se přihlásit. Můžete také vyhodnotit proměnné ve zprávě protokolu je umístit uvnitř složených závorek.

    Pokud se rozhodnete **odeslat do okna výstup**, když protokolovacích bodů: dosažení, zpráva se zobrazí v okně diagnostické nástroje.

    ![V okně archivu diagsession data protokolovacích bodů:](../debugger/media/snapshot-logpoint-output.png)

    Pokud se rozhodnete **odeslat do protokolu aplikace**, když protokolovacích bodů: dosažení, zpráva se zobrazí kdekoli, zobrazí se zprávy z `System.Diagnostics.Trace` (nebo `ILogger` v .NET Core), například [App Insights](/azure/application-insights/app-insights-asp-net-trace-logs).

## <a name="next-steps"></a>Další kroky

V tomto kurzu jste zjistili, jak použít ladicí program snímků pro Kubernetes v Azure. Můžete chtít přečtěte si další podrobnosti o této funkci.

> [!div class="nextstepaction"]
> [Nejčastější dotazy k ladění snímků](../debugger/debug-live-azure-apps-faq.md)