---
title: 'Postupy: určení alternativního umístění pro aktualizace nasazení | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: wpickett
ms.openlocfilehash: c992feab2b31ffebf07dcea36bc5bd5cfddc6eab
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49228797"
---
# <a name="how-to-specify-an-alternate-location-for-deployment-updates"></a>Postupy: Určení alternativního umístění pro aktualizace nasazení
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete nainstalovat vaše [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikace zpočátku z disku CD-ROM nebo sdílené složky, ale aplikace musíte hledat pravidelné aktualizace na webu. Můžete zadat alternativní umístění pro aktualizace v manifestu nasazení, tak, aby vaše aplikace můžete aktualizovat přímo z webu po počáteční instalaci.  
  
> [!NOTE]
>  Aplikace musí být nakonfigurován k instalaci místně pro tuto funkci používat. Další informace najdete v tématu [návod: Ruční nasazení aplikace ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Kromě toho, pokud nainstalujete [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] v síti, nastavení způsobí, že alternativního umístění [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] použije toto umístění pro počáteční instalaci a všechny následné aktualizace. Pokud nainstalujete aplikaci místně (například z disku CD), počáteční instalace se provádí pomocí původního média a všechny následné aktualizace použije alternativního umístění.  
  
### <a name="specifying-an-alternate-location-for-updates-by-using-mageuiexe-windows-forms-based-utility"></a>Zadat alternativní umístění pro aktualizace s použitím MageUI.exe (nástroj založený na Windows Forms)  
  
1.  Otevřete příkazový řádek rozhraní .NET Framework a zadejte:  
  
     **MageUI.exe**  
  
2.  Na **souboru** nabídce zvolte **otevřete** pro otevření manifestu nasazení vaší aplikace.  
  
3.  Vyberte **možnosti nasazení** kartu.  
  
4.  V textovém poli s názvem **umístění spuštění**, zadejte adresu URL k adresáři, který bude obsahovat manifest nasazení pro aktualizace aplikace.  
  
5.  Uložte manifest nasazení.  
  
### <a name="specifying-an-alternate-location-for-updates-by-using-mageexe"></a>Zadat alternativní umístění pro aktualizace s použitím Mage.exe  
  
1.  Otevřete příkazový řádek rozhraní .NET Framework.  
  
2.  Nastavte umístění aktualizace pomocí následujícího příkazu. V tomto příkladu **HelloWorld.exe.application** způsob, jak je vaše [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] manifestu aplikace, který má vždy příponu .application a **http://adatum.com/Update/Path** je adresa URL tohoto [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] se kontrola aktualizací aplikace.  
  
     **Obrázek – aktualizovat HelloWorld.exe.application - ProviderUrl http://adatum.com/Update/Path**  
  
3.  Uložte soubor.  
  
    > [!NOTE]
    >  Teď je potřeba znovu podepsat soubor s Mage.exe. Další informace najdete v tématu [návod: Ruční nasazení aplikace ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Pokud nainstalujete aplikaci z offline média, jako je například disk CD-ROM a je počítač online, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] nejprve zkontroluje adrese URL zadané hodnotou `<deploymentProvider>` značky v manifestu nasazení, aby určilo, jestli umístění aktualizace obsahuje novější verzi aplikace. Pokud ano, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] nainstaluje aplikaci přímo z daného místa, místo v adresáři počáteční instalaci a common language runtime (CLR) určuje důvěryhodnost vaší aplikace pomocí na úrovni `<deploymentProvider>`. Pokud je počítač v režimu offline, nebo `<deploymentProvider>` nedostupný, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] instalace z disku CD-ROM a CLR uděluje vztah důvěryhodnosti podle umístění instalace; pro instalaci z disku CD, to znamená, že vaše aplikace obdrží úplný vztah důvěryhodnosti. Všechny následné aktualizace zdědí tuto úroveň důvěryhodnosti.  
  
 Všechny [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikace, které používají `<deploymentProvider>` by měly explicitně deklarovat oprávnění potřebují ve svém manifestu aplikace tak, aby aplikace neobdrží různé úrovně důvěryhodnosti na různých počítačích.  
  
## <a name="see-also"></a>Viz také  
 [Návod: Ruční nasazení aplikace ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)   
 [ClickOnce – Manifest nasazení](../deployment/clickonce-deployment-manifest.md)   
 [Zabezpečování aplikací ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Výběr strategie aktualizace ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)



