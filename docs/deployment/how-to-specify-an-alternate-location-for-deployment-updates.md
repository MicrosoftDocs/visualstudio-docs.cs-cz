---
title: 'Postup: Zadání alternativního umístění aktualizací nasazení | Dokumenty společnosti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, updates
- deployment update, alternative locations
ms.assetid: 7faacd35-2638-492d-80f6-6b57e5f820de
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e0484e36bb857f5d08382f86f42b2e09dda21616
ms.sourcegitcommit: c1339f64fbeee6f17bf80fedea81afc8dac40dc0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "82037334"
---
# <a name="how-to-specify-an-alternate-location-for-deployment-updates"></a>Postup: Určení alternativního umístění pro aktualizace nasazení
Aplikaci [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] můžete nainstalovat zpočátku z disku CD nebo ze sdílené složky, ale aplikace musí kontrolovat pravidelné aktualizace na webu. Můžete zadat alternativní umístění pro aktualizace v manifestu nasazení tak, aby vaše aplikace může aktualizovat sám z webu po jeho počáteční instalaci.

> [!NOTE]
> Aplikace musí být nakonfigurována pro místní instalaci, aby tuto funkci používala. Další informace naleznete [v tématu Návod: Ruční nasazení aplikace ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Pokud navíc nainstalujete [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikaci ze sítě, nastavení [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] alternativního umístění způsobí použití tohoto umístění pro počáteční instalaci i všechny následné aktualizace. Pokud instalujete aplikaci místně (například z disku CD), počáteční instalace se provádí pomocí původního média a všechny následné aktualizace budou používat alternativní umístění.

### <a name="specify-an-alternate-location-for-updates-by-using-mageuiexe-windows-forms-based-utility"></a>Určení alternativního umístění aktualizací pomocí nástroje MageUI.exe (nástroj založený na formulářích Windows)

1. Otevřete příkazový řádek rozhraní .NET Framework a zadejte:

     **Mageui.exe**

2. V nabídce **Soubor** zvolte **Otevřít,** abyste otevřeli manifest nasazení aplikace.

3. Vyberte kartu **Možnosti nasazení.**

4. Do textového pole s názvem **Umístění spuštění**zadejte adresu URL do adresáře, který bude obsahovat manifest nasazení pro aktualizace aplikací.

5. Uložte manifest nasazení.

### <a name="specify-an-alternate-location-for-updates-by-using-mageexe"></a>Určení alternativního umístění aktualizací pomocí souboru Mage.exe

1. Otevřete příkazový řádek rozhraní .NET Framework.

2. Nastavte umístění aktualizace pomocí následujícího příkazu. V tomto příkladu *HelloWorld.exe.application* je [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] cesta k manifestu aplikace, který `http://adatum.com/Update/Path` má vždy [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] rozšíření .application a je adresa URL, která bude kontrolovat aktualizace aplikací.

    **Mage -Update HelloWorld.exe.application -ProviderUrl http:\//adatum.com/Update/Path**

3. Uložte soubor.

   > [!NOTE]
   > Nyní je třeba znovu podepsat soubor s *Mage.exe*. Další informace naleznete [v tématu Návod: Ruční nasazení aplikace ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).

## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework
 Pokud instalujete aplikaci z offline média, například [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] z disku CD-ROM, a počítač je online, nejprve zkontroluje adresu URL určenou `<deploymentProvider>` značkou v manifestu nasazení a zjistíte, zda umístění aktualizace obsahuje novější verzi aplikace. Pokud ano, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] nainstaluje aplikaci přímo odtud, nikoli z počátečního instalačního adresáře, a clr (COMMON Language `<deploymentProvider>`runtime) určuje úroveň důvěryhodnosti aplikace pomocí . Pokud je počítač offline `<deploymentProvider>` nebo je [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] nedostupný, nainstaluje se z disku CD a clr udělí vztah důvěryhodnosti na základě instalačního bodu. pro instalaci disku CD, to znamená, že aplikace obdrží plnou důvěryhodnost. Všechny následné aktualizace zdědí tuto úroveň důvěryhodnosti.

 Všechny [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikace, `<deploymentProvider>` které používají by měl explicitně deklarovat oprávnění, která potřebují v manifestu aplikace, tak, aby aplikace neobdrží různé úrovně důvěryhodnosti v různých počítačích.

## <a name="see-also"></a>Viz také
- [Návod: Ruční nasazení aplikace ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)
- [Manifest nasazení ClickOnce](../deployment/clickonce-deployment-manifest.md)
- [Zabezpečení aplikací ClickOnce](../deployment/securing-clickonce-applications.md)
- [Výběr strategie aktualizace ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)