---
title: 'Postup: Zadání alternativního umístění aktualizací nasazení | Dokumenty společnosti Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, updates
- deployment update, alternative locations
ms.assetid: 7faacd35-2638-492d-80f6-6b57e5f820de
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8b6388833e6574fc1d631d391fa7b67d5f0a3372
ms.sourcegitcommit: c1339f64fbeee6f17bf80fedea81afc8dac40dc0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "82037217"
---
# <a name="how-to-specify-an-alternate-location-for-deployment-updates"></a>Postupy: Určení alternativního umístění pro aktualizace nasazení
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aplikaci [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] můžete nainstalovat zpočátku z disku CD nebo ze sdílené složky, ale aplikace musí kontrolovat pravidelné aktualizace na webu. Můžete zadat alternativní umístění pro aktualizace v manifestu nasazení tak, aby vaše aplikace může aktualizovat sám z webu po jeho počáteční instalaci.  
  
> [!NOTE]
> Aplikace musí být nakonfigurována pro místní instalaci, aby tuto funkci používala. Další informace naleznete [v tématu Návod: Ruční nasazení aplikace ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Pokud navíc nainstalujete [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikaci ze sítě, nastavení [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] alternativního umístění způsobí použití tohoto umístění pro počáteční instalaci i všechny následné aktualizace. Pokud instalujete aplikaci místně (například z disku CD), počáteční instalace se provádí pomocí původního média a všechny následné aktualizace budou používat alternativní umístění.  
  
### <a name="specifying-an-alternate-location-for-updates-by-using-mageuiexe-windows-forms-based-utility"></a>Určení alternativního umístění aktualizací pomocí nástroje MageUI.exe (nástroj založený na formulářích Windows)  
  
1. Otevřete příkazový řádek rozhraní .NET Framework a zadejte:  
  
     **Mageui.exe**  
  
2. V nabídce **Soubor** zvolte **Otevřít,** abyste otevřeli manifest nasazení aplikace.  
  
3. Vyberte kartu **Možnosti nasazení.**  
  
4. Do textového pole s názvem **Umístění spuštění**zadejte adresu URL do adresáře, který bude obsahovat manifest nasazení pro aktualizace aplikací.  
  
5. Uložte manifest nasazení.  
  
### <a name="specifying-an-alternate-location-for-updates-by-using-mageexe"></a>Určení alternativního umístění aktualizací pomocí souboru Mage.exe  
  
1. Otevřete příkazový řádek rozhraní .NET Framework.  
  
2. Nastavte umístění aktualizace pomocí následujícího příkazu. V tomto příkladu **HelloWorld.exe.application** je [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] cesta k manifestu aplikace, který `http://adatum.com/Update/Path` má vždy [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] rozšíření .application a je adresa URL, která bude kontrolovat aktualizace aplikací.  
  
     **Mage -Update HelloWorld.exe.application -ProviderUrl http:\//adatum.com/Update/Path**  
  
3. Uložte soubor.  
  
    > [!NOTE]
    > Nyní musíte soubor znovu podepsat pomocí souboru Mage.exe. Další informace naleznete [v tématu Návod: Ruční nasazení aplikace ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Pokud instalujete aplikaci z offline média, například [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] z disku CD-ROM, a počítač je online, nejprve zkontroluje adresu URL určenou `<deploymentProvider>` značkou v manifestu nasazení a zjistíte, zda umístění aktualizace obsahuje novější verzi aplikace. Pokud ano, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] nainstaluje aplikaci přímo odtud, nikoli z počátečního instalačního adresáře, a clr (COMMON Language `<deploymentProvider>`runtime) určuje úroveň důvěryhodnosti aplikace pomocí . Pokud je počítač offline `<deploymentProvider>` nebo je [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] nedostupný, nainstaluje se z disku CD a clr udělí vztah důvěryhodnosti na základě instalačního bodu. pro instalaci disku CD, to znamená, že aplikace obdrží plnou důvěryhodnost. Všechny následné aktualizace zdědí tuto úroveň důvěryhodnosti.  
  
 Všechny [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikace, `<deploymentProvider>` které používají by měl explicitně deklarovat oprávnění, která potřebují v manifestu aplikace, tak, aby aplikace neobdrží různé úrovně důvěryhodnosti v různých počítačích.  
  
## <a name="see-also"></a>Viz také  
 [Návod: Ruční nasazení aplikace ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)   
 [Manifest nasazení ClickOnce](../deployment/clickonce-deployment-manifest.md)   
 [Zabezpečení aplikací ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Výběr strategie aktualizace ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)
