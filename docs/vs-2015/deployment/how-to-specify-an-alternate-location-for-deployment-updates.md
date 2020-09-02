---
title: 'Postupy: určení alternativního umístění pro aktualizace nasazení | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "82037217"
---
# <a name="how-to-specify-an-alternate-location-for-deployment-updates"></a>Postupy: Určení alternativního umístění pro aktualizace nasazení
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Svou [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikaci můžete nejdřív nainstalovat ze složky CD nebo sdílené složky, ale aplikace musí kontrolovat pravidelné aktualizace na webu. Můžete zadat alternativní umístění pro aktualizace v manifestu nasazení, aby se vaše aplikace mohla po počáteční instalaci aktualizovat z webu.  
  
> [!NOTE]
> Aby bylo možné tuto funkci používat, musí být aplikace nakonfigurována pro místní instalaci. Další informace naleznete v tématu [Návod: Ruční nasazení aplikace ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Kromě toho, pokud instalujete [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikaci ze sítě, nastavení alternativního umístění způsobí [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] , že bude toto umístění použito pro počáteční instalaci i pro všechny následné aktualizace. Pokud instalujete aplikaci místně (například z disku CD), počáteční instalace se provádí pomocí původního média a všechny následné aktualizace použijí alternativní umístění.  
  
### <a name="specifying-an-alternate-location-for-updates-by-using-mageuiexe-windows-forms-based-utility"></a>Určení alternativního umístění pro aktualizace pomocí MageUI.exe (nástroj založený na model Windows Forms)  
  
1. Otevřete příkazový řádek .NET Framework a zadejte:  
  
     **mageui.exe**  
  
2. V nabídce **soubor** vyberte **otevřít** a otevřete manifest nasazení vaší aplikace.  
  
3. Vyberte kartu **Možnosti nasazení** .  
  
4. Do textového pole nazvané **umístění pro spuštění**zadejte adresu URL adresáře, který bude obsahovat manifest nasazení pro aktualizace aplikace.  
  
5. Uložte manifest nasazení.  
  
### <a name="specifying-an-alternate-location-for-updates-by-using-mageexe"></a>Určení alternativního umístění pro aktualizace pomocí Mage.exe  
  
1. Otevřete příkazový řádek .NET Framework.  
  
2. Umístění aktualizace nastavte pomocí následujícího příkazu. V tomto příkladu je **HelloWorld.exe. Application** cesta k [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] manifestu aplikace, který vždy má příponu. Application a `http://adatum.com/Update/Path` je adresa URL, která [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] bude kontrolovat aktualizace aplikace.  
  
     **Mage – aktualizace HelloWorld.exe. Application-ProviderUrl http: \/ /adatum.com/Update/Path**  
  
3. Uložte soubor.  
  
    > [!NOTE]
    > Nyní je třeba soubor znovu podepsat pomocí Mage.exe. Další informace naleznete v tématu [Návod: Ruční nasazení aplikace ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Pokud instalujete aplikaci z offline média, jako je například CD, a počítač je online, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] nejprve zkontroluje adresu URL určenou `<deploymentProvider>` značkou v manifestu nasazení, aby bylo možné zjistit, zda umístění aktualizace obsahuje novější verzi aplikace. Pokud k tomu dojde, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikace nainstaluje aplikaci přímo z adresáře místo počáteční instalace a modul CLR (Common Language Runtime) určí úroveň důvěryhodnosti vaší aplikace pomocí `<deploymentProvider>` . Pokud je počítač offline nebo `<deploymentProvider>` je nedosažitelný, nainstaluje se [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] z disku CD a CLR udělí důvěru na základě bodu instalace. pro instalaci z disku CD to znamená, že vaše aplikace získá úplný vztah důvěryhodnosti. Všechny následné aktualizace budou dědit tuto úroveň důvěryhodnosti.  
  
 Všechny [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikace, které používají, `<deploymentProvider>` by měly explicitně deklarovat oprávnění, která potřebují v manifestu aplikace, aby aplikace nepřijímala různé úrovně důvěry v různých počítačích.  
  
## <a name="see-also"></a>Viz také  
 [Návod: Ruční nasazení aplikace ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)   
 [ClickOnce – manifest nasazení](../deployment/clickonce-deployment-manifest.md)   
 [Zabezpečení aplikací ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Výběr strategie aktualizace ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)
