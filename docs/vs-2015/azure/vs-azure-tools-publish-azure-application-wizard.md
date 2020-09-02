---
title: Pomocí Průvodce publikováním aplikace Azure | Microsoft Docs
description: Naučte se konfigurovat různá nastavení v Průvodci publikováním aplikace Azure v nástroji Visual Studio.
author: ghogen
manager: jillfra
assetId: 7d8f1ac9-e439-47e0-a183-0642c4ea1920
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 03/21/2017
ms.author: ghogen
ms.openlocfilehash: a75e83e3fb2ac43b4fa1d658c7e2a08ec1ae3c1a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62831286"
---
# <a name="using-the-visual-studio-publish-azure-application-wizard"></a>Použití průvodce publikováním aplikace Azure v sadě Visual Studio

Po vývoji webové aplikace v aplikaci Visual Studio můžete tuto aplikaci publikovat do cloudové služby Azure pomocí průvodce **publikováním aplikace Azure** .

> [!Note]
> Tento článek se týká nasazení na cloudové služby, nikoli na webové servery. Informace o nasazení na webové servery najdete v tématu [nasazení webu Azure](https://social.msdn.microsoft.com/Search/windowsazure?query=How%20to%20Deploy%20an%20Azure%20Web%20Site&Refinement=138&ac=4#refinementChanges=117&pageNumber=1&showMore=false).

## <a name="accessing-the-publish-azure-application-wizard"></a>Přístup k Průvodci publikováním aplikace Azure

Průvodce publikováním aplikace Azure můžete použít dvěma způsoby v závislosti na typu projektu sady Visual Studio, který máte.

**Pokud máte projekt cloudové služby Azure:**

1. Vytvořte nebo otevřete projekt cloudové služby Azure v aplikaci Visual Studio.

1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt a v místní nabídce vyberte **publikovat**.

**Pokud máte projekt webové aplikace, který není pro Azure povolený:**

1. Vytvořte nebo otevřete projekt cloudové služby Azure v aplikaci Visual Studio.

1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt a v místní nabídce vyberte **převést**  >  **na projekt cloudové služby Azure**.

1. V **Průzkumník řešení**klikněte pravým tlačítkem na nově vytvořený projekt Azure a v místní nabídce vyberte **publikovat**.

## <a name="sign-in-page"></a>Přihlašovací stránka

![Přihlašovací stránka](./media/vs-azure-tools-publish-azure-application-wizard/sign-in.png)

**Účet** – vyberte účet nebo v rozevíracím seznamu účet vyberte **Přidat účet** .

**Vyberte své předplatné** – vyberte předplatné, které chcete použít pro vaše nasazení.

## <a name="settings-page---common-settings-tab"></a>Stránka Nastavení – karta společná nastavení

![Společná nastavení](./media/vs-azure-tools-publish-azure-application-wizard/settings-common-settings.png)

**Cloudová služba** – pomocí rozevíracího seznamu vyberte existující cloudovou službu nebo vyberte ** &lt; vytvořit novou>** a vytvořte cloudovou službu. Datové centrum se zobrazí v závorkách pro každou cloudovou službu. Doporučuje se, aby bylo umístění datového centra pro cloudovou službu stejné jako umístění datového centra pro účet úložiště (rozšířené nastavení).

**Prostředí** – vyberte buď **produkční** , nebo **fázování**. Pokud chcete aplikaci nasadit v testovacím prostředí, vyberte testovací prostředí.

**Konfigurace sestavení** – vyberte buď **ladění** , nebo **vydání**.

**Konfigurace služby** – vyberte buď **Cloud** , nebo **místní**.

**Povolit vzdálenou plochu pro všechny role** – tuto možnost vyberte, pokud chcete být schopni se vzdáleně připojit ke službě. Tato možnost se primárně používá pro řešení potíží. Další informace najdete v tématu [povolení připojení ke vzdálené ploše pro roli v Azure Cloud Services pomocí sady Visual Studio](/azure/cloud-services/cloud-services-role-enable-remote-desktop-visual-studio).

**Povolit nasazení webu pro všechny webové role** – výběrem této možnosti povolíte nasazení webu pro službu. Pokud chcete tuto funkci používat, musíte taky vybrat možnost **Povolit vzdálenou plochu pro všechny role** . Další informace najdete v tématu [publikování cloudové služby pomocí sady Visual Studio](vs-azure-tools-publishing-a-cloud-service.md).

## <a name="settings-page---advanced-settings-tab"></a>Stránka Nastavení – karta Upřesnit nastavení

![Rozšířená nastavení](./media/vs-azure-tools-publish-azure-application-wizard/settings-advanced-settings.png)

**Popisek nasazení** – buď přijměte výchozí název, nebo zadejte název, který zvolíte. Chcete-li připojit datum k popisku nasazení, ponechejte zaškrtnuté políčko.

**Účet úložiště** – vyberte účet úložiště, který se má použít pro toto nasazení, * * &lt; vytvořit nové> pro vytvoření účtu úložiště. Datové centrum se zobrazí v závorkách pro každý účet úložiště. Doporučuje se, aby bylo umístění datového centra pro účet úložiště stejné jako umístění datového centra pro cloudovou službu (společné nastavení).

Účet úložiště Azure ukládá balíček pro nasazení aplikace. Po nasazení aplikace se balíček odebere z účtu úložiště.

**Odstranit nasazení při selhání** – tuto možnost vyberte, pokud chcete, aby se nasazení odstranilo, pokud při publikování dojde k nějakým chybám. Tato funkce by měla být nezaškrtnutá, pokud chcete zachovat stálou virtuální IP adresu pro cloudovou službu.

**Nasazení aktualizace** – tuto možnost vyberte, pokud chcete nasadit jenom aktualizované součásti. Tento typ nasazení může být rychlejší než úplné nasazení. Tuto možnost byste měli zkontrolovat, pokud chcete zachovat konstantní virtuální IP adresu pro cloudovou službu.

**Aktualizace nasazení – nastavení** – pomocí tohoto dialogového okna můžete dále určit, jak se mají role aktualizovat. Zvolíte-li možnost **přírůstková aktualizace**, každá instance aplikace je po jiné aktualizována, aby byla aplikace vždy k dispozici. Pokud zvolíte možnost **Souběžná aktualizace**, všechny instance aplikace se aktualizují ve stejnou dobu. Současná aktualizace je rychlejší, ale služba nemusí být během procesu aktualizace dostupná.

![Nastavení nasazení](./media/vs-azure-tools-publish-azure-application-wizard/deployment-settings.png)

**Povolit IntelliTrace** – určuje, jestli chcete povolit IntelliTrace. Pomocí IntelliTrace můžete protokolovat rozsáhlé ladicí informace pro instanci role, když běží v Azure. Pokud potřebujete najít příčinu problému, můžete pomocí protokolů IntelliTrace Procházet kód ze sady Visual Studio, jako kdyby běžel v Azure. Další informace o použití IntelliTrace najdete v tématu [Ladění publikované cloudové služby Azure pomocí sady Visual Studio a IntelliTrace](./vs-azure-tools-intellitrace-debug-published-cloud-services.md).

**Povolit profilaci** – určete, jestli chcete povolit profilaci výkonu. Profiler sady Visual Studio umožňuje získat podrobnou analýzu výpočetních aspektů, jak vaše cloudová služba běží. Další informace o používání profileru sady Visual Studio najdete v tématu [testování výkonu cloudové služby Azure](./vs-azure-tools-performance-profiling-cloud-services.md).

**Povolit vzdálený ladicí program pro všechny role** – určete, jestli chcete povolit vzdálené ladění. Další informace o ladění cloudových služeb pomocí sady Visual Studio najdete v tématu [ladění cloudové služby Azure nebo virtuálního počítače v aplikaci Visual Studio](./vs-azure-tools-debug-cloud-services-virtual-machines.md).

## <a name="diagnostics-settings-page"></a>Stránka nastavení diagnostiky

![Nastavení diagnostiky](./media/vs-azure-tools-publish-azure-application-wizard/diagnostic-settings.png)

Diagnostika umožňuje řešit potíže s cloudovou službou Azure (nebo virtuálním počítačem Azure). Informace o diagnostice najdete v tématu [Konfigurace diagnostiky pro Azure Cloud Services a Virtual Machines](./vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines.md). Informace o Application Insights najdete v tématu [co je Application Insights?](/azure/application-insights/app-insights-overview).

## <a name="summary-page"></a>Stránka souhrnu

![Shrnutí](./media/vs-azure-tools-publish-azure-application-wizard/summary.png)

**Cílový profil** – můžete zvolit vytvoření profilu publikování z nastavení, které jste si zvolili. Můžete například vytvořit jeden profil pro testovací prostředí a jiný pro produkční prostředí. Chcete-li uložit tento profil, klikněte na ikonu **Uložit** . Průvodce vytvoří profil a uloží jej do projektu aplikace Visual Studio. Chcete-li změnit název profilu, otevřete seznam **cílový profil** a pak zvolte možnost ** &lt; Spravovat... &gt; **.

   > [!Note]
   > Profil publikování se zobrazí v Průzkumník řešení v aplikaci Visual Studio a nastavení profilu se zapisuje do souboru s příponou. azurePubxml. Nastavení jsou uložena jako atributy značek XML.

## <a name="publishing-your-application"></a>Publikování aplikace

Jakmile nakonfigurujete všechna nastavení pro nasazení projektu, v dolní části dialogového okna vyberte **publikovat** . Stav procesu můžete monitorovat v okně **výstup** v aplikaci Visual Studio.

## <a name="next-steps"></a>Další kroky

- [Migrace a publikování webové aplikace do cloudové služby Azure ze sady Visual Studio](./vs-azure-tools-migrate-publish-web-app-to-cloud-service.md)

- [Naučte se používat Visual Studio k publikování cloudové služby Azure.](./vs-azure-tools-publishing-a-cloud-service.md)

- [Ladění publikované cloudové služby Azure pomocí sady Visual Studio a nástroje IntelliTrace](./vs-azure-tools-intellitrace-debug-published-cloud-services.md)

- [Testování výkonu cloudové služby Azure](./vs-azure-tools-performance-profiling-cloud-services.md)

- [Konfiguruje se Diagnostika pro Azure Cloud Services a Virtual Machines](./vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines.md).

- [Co je Application Insights?](/azure/application-insights/app-insights-overview)