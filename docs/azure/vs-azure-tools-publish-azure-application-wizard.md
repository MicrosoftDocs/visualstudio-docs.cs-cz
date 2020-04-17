---
title: Publikování cloudové služby Azure
description: Zjistěte, jak nakonfigurovat různá nastavení v Průvodci publikováním aplikací Azure ve Visual Studiu
author: ghogen
manager: jillfra
assetId: 7d8f1ac9-e439-47e0-a183-0642c4ea1920
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 03/21/2017
ms.author: ghogen
ms.openlocfilehash: bc3c58343c699833a5a12eee6f79c023f57a2e85
ms.sourcegitcommit: 59a8732dc563242590f7c6ccf4ced6c6d195533c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2020
ms.locfileid: "81489646"
---
# <a name="using-the-visual-studio-publish-azure-application-wizard"></a>Použití průvodce publikováním aplikace Azure v sadě Visual Studio

Po vývoji webové aplikace ve Visual Studiu můžete publikovat tuto aplikaci do cloudové služby Azure pomocí průvodce **publikováním aplikací Azure.**

> [!Note]
> Tento článek pojednává o nasazení do cloudových služeb, nikoli na weby. Informace o nasazení na webech najdete [v tématu Jak nasadit web Azure](https://social.msdn.microsoft.com/Search/windowsazure?query=How%20to%20Deploy%20an%20Azure%20Web%20Site&Refinement=138&ac=4#refinementChanges=117&pageNumber=1&showMore=false).

## <a name="accessing-the-publish-azure-application-wizard"></a>Přístup k průvodci publikováním aplikací Azure

K Průvodci publikováním aplikace Azure můžete přistupovat dvěma způsoby v závislosti na typu projektu sady Visual Studio, který máte.

**Pokud máte projekt cloudové služby Azure:**

1. Vytvořte nebo otevřete projekt cloudové služby Azure ve Visual Studiu.

1. V **Průzkumníku řešení**klepněte pravým tlačítkem myši na projekt a v kontextové nabídce vyberte **publikovat**.

**Pokud máte projekt webové aplikace, který není povolený pro Azure:**

1. Vytvořte nebo otevřete projekt cloudové služby Azure ve Visual Studiu.

1. V **Průzkumníku řešení**klikněte pravým tlačítkem myši na projekt a v kontextové nabídce vyberte **Převést** > **na projekt cloudové služby Azure**.

1. V **Průzkumníku řešení**klikněte pravým tlačítkem myši na nově vytvořený projekt Azure a v místní nabídce vyberte **Publikovat**.

## <a name="sign-in-page"></a>Přihlašovací stránka

![Přihlašovací stránka](./media/vs-azure-tools-publish-azure-application-wizard/sign-in.png)

**Účet** – Vyberte účet nebo vyberte **Přidat účet** v rozevíracím seznamu účtu.

**Zvolte předplatné** – zvolte předplatné, které chcete použít pro nasazení.

## <a name="settings-page---common-settings-tab"></a>Stránka Nastavení – karta Běžná nastavení

![Společná nastavení](./media/vs-azure-tools-publish-azure-application-wizard/settings-common-settings.png)

**Cloudová služba** – Pomocí rozevíracího přehledu vyberte existující cloudovou službu nebo vyberte ** &lt;Vytvořit novou>** a vytvořte cloudovou službu. Datové centrum se zobrazí v závorce pro každou cloudovou službu. Doporučujese, aby umístění datového centra pro cloudovou službu bylo stejné jako umístění datového centra pro účet úložiště (Upřesnit nastavení).

**Prostředí** – vyberte **možnost Výroba** nebo **Pracovní .** Pokud chcete nasadit aplikaci v testovacím prostředí, zvolte pracovní prostředí.

**Konfigurace sestavení** – vyberte možnost **Ladění** nebo **vydání**.

**Konfigurace služby** – vyberte **cloud nebo** **místní**.

**Povolit vzdálenou plochu pro všechny role** – tuto možnost vyberte, pokud se chcete vzdáleně připojit ke službě. Tato možnost se používá především pro řešení potíží. Další informace najdete [v tématu Povolení připojení ke vzdálené ploše pro roli v Cloudových službách Azure pomocí sady Visual Studio](/azure/cloud-services/cloud-services-role-enable-remote-desktop-visual-studio).

**Povolit nasazení webu pro všechny webové role** – Tuto možnost vyberte, chcete-li povolit nasazení webu pro službu. Chcete-li tuto funkci používat, musíte také vybrat možnost **Povolit vzdálenou plochu pro všechny role.** Další informace naleznete [v tématu Publikování cloudové služby pomocí sady Visual Studio](vs-azure-tools-publishing-a-cloud-service.md).

## <a name="settings-page---advanced-settings-tab"></a>Stránka Nastavení – karta Upřesnit nastavení

![Upřesnit nastavení](./media/vs-azure-tools-publish-azure-application-wizard/settings-advanced-settings.png)

**Popisek nasazení** – buď přijměte výchozí název, nebo zadejte název podle svého výběru. Chcete-li připojit datum k popisku nasazení, ponechte zaškrtnuté políčko.

**Účet úložiště** – Vyberte účet úložiště, který&lt;chcete použít pro toto nasazení, ** Vytvořit nový> k vytvoření účtu úložiště. Datové centrum se zobrazí v závorce pro každý účet úložiště. Doporučuje se, aby umístění datového centra pro účet úložiště bylo stejné jako umístění datového centra pro cloudovou službu (Společná nastavení).

Účet úložiště Azure ukládá balíček pro nasazení aplikace. Po nasazení aplikace je balíček odebrán z účtu úložiště.

**Odstranit nasazení při selhání** – Tuto možnost vyberte, chcete-li, aby bylo nasazení odstraněno, pokud během publikování dojde k chybám. To by mělo být nezaškrtnuté, pokud chcete udržovat konstantní virtuální IP adresu pro vaši cloudovou službu.

**Aktualizace nasazení** – tuto možnost vyberte, pokud chcete nasadit pouze aktualizované součásti. Tento typ nasazení může být rychlejší než úplné nasazení. To by mělo být kontrolováno, pokud chcete udržovat konstantní virtuální IP adresu pro vaši cloudovou službu.

**Aktualizace nasazení - nastavení** - Toto dialogové okno slouží k dalšímu určení, jak chcete role aktualizovat. Pokud zvolíte **přírůstková aktualizace**, každá instance aplikace se aktualizuje jeden po druhém, takže aplikace je vždy k dispozici. Pokud zvolíte **simultánní aktualizaci**, budou aktualizovány všechny instance aplikace současně. Simultánní aktualizace je rychlejší, ale vaše služba nemusí být během procesu aktualizace k dispozici.

![Nastavení nasazení](./media/vs-azure-tools-publish-azure-application-wizard/deployment-settings.png)

**Povolit IntelliTrace** - Zadejte, zda chcete povolit IntelliTrace. S IntelliTrace můžete protokolovat rozsáhlé informace o ladění pro instanci role při spuštění v Azure. Pokud potřebujete najít příčinu problému, můžete použít protokoly IntelliTrace krokovat kód z Visual Studia, jako kdyby byly spuštěny v Azure. Další informace o používání IntelliTrace najdete [v tématu ladění publikované cloudové služby Azure pomocí Visual Studia a IntelliTrace](./vs-azure-tools-intellitrace-debug-published-cloud-services.md).

**Povolit profilování** – určete, zda chcete povolit profilování výkonu. Profilování sady Visual Studio umožňuje získat hloubkovou analýzu výpočetních aspektů fungování cloudové služby. Další informace o použití profileru Sady Visual Studio najdete [v tématu Testování výkonu cloudové služby Azure](./vs-azure-tools-performance-profiling-cloud-services.md).

**Povolit vzdálený ladicí program pro všechny role** – určete, zda chcete povolit vzdálené ladění. Další informace o ladění cloudových služeb pomocí Visual Studia najdete [v tématu ladění cloudové služby Azure nebo virtuálního počítače v sadě Visual Studio](./vs-azure-tools-debug-cloud-services-virtual-machines.md).

## <a name="diagnostics-settings-page"></a>Stránka Nastavení diagnostiky

![Nastavení diagnostiky](./media/vs-azure-tools-publish-azure-application-wizard/diagnostic-settings.png)

Diagnostika umožňuje řešit potíže s cloudovou službou Azure (nebo virtuálním počítačem Azure). Informace o diagnostice najdete [v tématu Konfigurace diagnostiky pro cloudové služby Azure a virtuální počítače](./vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines.md). Informace o Application Insights najdete v tématu [Co je Application Insights?](/azure/application-insights/app-insights-overview).

## <a name="summary-page"></a>Stránka souhrnu

![Souhrn](./media/vs-azure-tools-publish-azure-application-wizard/summary.png)

**Cílový profil** – můžete vytvořit profil publikování z nastavení, které jste zvolili. Můžete například vytvořit jeden profil pro testovací prostředí a jiný pro výrobu. Chcete-li tento profil uložit, zvolte ikonu **Uložit.** Průvodce vytvoří profil a uloží jej v projektu sady Visual Studio. Chcete-li upravit název profilu, otevřete seznam **Cílový profil** a pak zvolte ** &lt;Spravovat... &gt;**.

   > [!Note]
   > Profil publikování se zobrazí v Průzkumníkovi řešení v sadě Visual Studio a nastavení profilu se zapíše do souboru s příponou .azurePubxml. Nastavení jsou uložena jako atributy tagů XML.

## <a name="publishing-your-application"></a>Publikování aplikace

Po konfiguraci všech nastavení pro nasazení projektu vyberte **Publikovat** v dolní části dialogového okna. Stav procesu můžete sledovat v okně **Výstup** v sadě Visual Studio.

## <a name="next-steps"></a>Další kroky

- [Migrace a publikování webové aplikace do cloudové služby Azure z Visual Studia](./vs-azure-tools-migrate-publish-web-app-to-cloud-service.md)

- [Přečtěte si, jak pomocí Visual Studia publikovat cloudovou službu Azure.](./vs-azure-tools-publishing-a-cloud-service.md)

- [Ladění publikované cloudové služby Azure pomocí sady Visual Studio a nástroje IntelliTrace](./vs-azure-tools-intellitrace-debug-published-cloud-services.md)

- [Testování výkonu cloudové služby Azure](./vs-azure-tools-performance-profiling-cloud-services.md)

- [Konfigurace diagnostiky pro cloudové služby Azure a virtuální počítače](./vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines.md).

- [Co je Application Insights?](/azure/application-insights/app-insights-overview)