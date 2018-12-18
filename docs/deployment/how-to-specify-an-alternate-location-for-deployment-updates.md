---
title: 'Postupy: určení alternativního umístění pro aktualizace nasazení | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 76be049c670fb91911be70132b459cad5e5183bd
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49902461"
---
# <a name="how-to-specify-an-alternate-location-for-deployment-updates"></a>Postupy: určení alternativního umístění pro aktualizace nasazení
Můžete nainstalovat vaše [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikace zpočátku z disku CD-ROM nebo sdílené složky, ale aplikace musíte hledat pravidelné aktualizace na webu. Můžete zadat alternativní umístění pro aktualizace v manifestu nasazení, tak, aby vaše aplikace můžete aktualizovat přímo z webu po počáteční instalaci.  
  
> [!NOTE]
>  Aplikace musí být nakonfigurován k instalaci místně pro tuto funkci používat. Další informace najdete v tématu [návod: Ruční nasazení aplikace ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Kromě toho, pokud nainstalujete [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] v síti, nastavení způsobí, že alternativního umístění [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] použije toto umístění pro počáteční instalaci a všechny následné aktualizace. Pokud nainstalujete aplikaci místně (například z disku CD), počáteční instalace se provádí pomocí původního média a všechny následné aktualizace použije alternativního umístění.  
  
### <a name="specify-an-alternate-location-for-updates-by-using-mageuiexe-windows-forms-based-utility"></a>Zadejte alternativní umístění pro aktualizace pomocí MageUI.exe (nástroj založený na Windows Forms)  
  
1.  Otevřete příkazový řádek rozhraní .NET Framework a zadejte:  
  
     **MageUI.exe**  
  
2.  Na **souboru** nabídce zvolte **otevřete** pro otevření manifestu nasazení vaší aplikace.  
  
3.  Vyberte **možnosti nasazení** kartu.  
  
4.  V textovém poli s názvem **umístění spuštění**, zadejte adresu URL k adresáři, který bude obsahovat manifest nasazení pro aktualizace aplikace.  
  
5.  Uložte manifest nasazení.  
  
### <a name="specify-an-alternate-location-for-updates-by-using-mageexe"></a>Zadejte alternativní umístění pro aktualizace pomocí Mage.exe  
  
1. Otevřete příkazový řádek rozhraní .NET Framework.  
  
2. Nastavte umístění aktualizace pomocí následujícího příkazu. V tomto příkladu *HelloWorld.exe.application* způsob, jak je vaše [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifestu aplikace, který má vždy příponu .application a *<http://adatum.com/Update/Path>* je adresa URL tohoto [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] se kontrola aktualizací aplikace.  
  
    **Obrázek – aktualizovat HelloWorld.exe.application - ProviderUrl http://adatum.com/Update/Path**  
  
3. Uložte soubor.  
  
   > [!NOTE]
   >  Teď musíte znovu podepsat soubor s *Mage.exe*. Další informace najdete v tématu [návod: Ruční nasazení aplikace ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Pokud nainstalujete aplikaci z offline média, jako je například disk CD-ROM a je počítač online, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] nejprve zkontroluje adrese URL zadané hodnotou `<deploymentProvider>` značky v manifestu nasazení, aby určilo, jestli umístění aktualizace obsahuje novější verzi aplikace. Pokud ano, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] nainstaluje aplikaci přímo z daného místa, místo v adresáři počáteční instalaci a common language runtime (CLR) určuje důvěryhodnost vaší aplikace pomocí na úrovni `<deploymentProvider>`. Pokud je počítač v režimu offline, nebo `<deploymentProvider>` nedostupný, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] instalace z disku CD-ROM a CLR uděluje vztah důvěryhodnosti podle umístění instalace; pro instalaci z disku CD, to znamená, že vaše aplikace obdrží úplný vztah důvěryhodnosti. Všechny následné aktualizace zdědí tuto úroveň důvěryhodnosti.  
  
 Všechny [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikace, které používají `<deploymentProvider>` by měly explicitně deklarovat oprávnění potřebují ve svém manifestu aplikace tak, aby aplikace neobdrží různé úrovně důvěryhodnosti na různých počítačích.  
  
## <a name="see-also"></a>Viz také:  
 [Návod: Ruční nasazení aplikace ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)   
 [ClickOnce – manifest nasazení](../deployment/clickonce-deployment-manifest.md)   
 [Zabezpečení aplikací ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Volba strategie aktualizace ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)