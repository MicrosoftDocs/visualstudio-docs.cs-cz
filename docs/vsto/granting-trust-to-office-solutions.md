---
title: Vztah důvěryhodnosti grant řešení pro systém Office
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- security [Office development in Visual Studio], trust
- inclusion lists [Office development in Visual Studio], about inclusion lists
- trust [Office development in Visual Studio], 2007 Office system
- granting trust [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: cfce58ca765e7e3710ecb55a1c84c09f0ee14f52
ms.sourcegitcommit: 1466ac0f49ebf7448ea4507ae3f79acb25d51d3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/22/2018
ms.locfileid: "34447242"
---
# <a name="grant-trust-to-office-solutions"></a>Vztah důvěryhodnosti grant řešení pro systém Office
  Vztah důvěryhodnosti grant Office řešení znamená úprava zásady zabezpečení o každém cílovém počítači tak, aby důvěřoval sestavení řešení, manifest aplikace, manifest nasazení a dokumentu. Vztah důvěryhodnosti lze udělit řešení Office vy nebo koncový uživatel.  
  
 Úplný vztah důvěryhodnosti k řešení Office můžete udělit pomocí podepisování manifestů aplikace a nasazení.  
  
 Koncovým uživatelům můžete udělit vztah důvěryhodnosti řešení Office tak, že rozhodnutí o vztahu důvěryhodnosti [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] výzvu vztahu důvěryhodnosti.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
##  <a name="Signing"></a> Vztah důvěryhodnosti řešení pomocí podepisování manifestů aplikace a nasazení  
 Všechny aplikace a nasazení manifesty pro Office řešení musí být podepsané certifikátem, který identifikuje vydavatele. Certifikáty poskytují základ pro rozhodování o vztahu důvěryhodnosti.  
  
 Dočasné certifikát je vytvořená a udělit vztah důvěryhodnosti v okamžiku sestavení tak, aby řešení spuštěno při ladění ho. Pokud publikujete řešení, který je podepsaný certifikátem dočasné, koncový uživatel se vyzve k rozhodnutí o vztahu důvěryhodnosti.  
  
 Pokud podepíšete řešení s certifikátem známé a důvěryhodné, řešení se automaticky nainstalují bez zobrazení výzvy koncového uživatele k provedení rozhodnutí vztah důvěryhodnosti. Další informace o tom, jak získat certifikát pro podepisování najdete v tématu [ClickOnce a kód Authenticode](/visualstudio/deployment/clickonce-and-authenticode). Po získání certifikátu, certifikát musí být explicitně důvěryhodný přidáním do seznamu důvěryhodných vydavatelů. Další informace najdete v tématu [postupy: Přidání důvěryhodného vydavatele ke klientskému počítači pro aplikace ClickOnce](/visualstudio/deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications).  
  
 Pokud vývojář podepisuje řešení s certifikátem dočasné, správce znovu podepsat přizpůsobení známé a důvěryhodné certifikátem pomocí generování manifestu a nástroj pro úpravy (*mage.exe*), který je jedním z Microsoft .NET Framework – nástroje. Další informace o podepisování řešení najdete v tématu [postupy: řešení pro systém Office přihlašování](../vsto/how-to-sign-office-solutions.md) a [postupy: podepsání manifestů aplikace a nasazení](/visualstudio/ide/how-to-sign-application-and-deployment-manifests).  
  
##  <a name="TrustPrompt"></a>Vztah důvěryhodnosti řešení pomocí vztahu důvěryhodnosti ClickOnce  
 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] vyzve k zadání koncového uživatele, aby rozhodnutí o vztahu důvěryhodnosti, pokud nejsou žádné zásady celé organizace, která důvěřuje certifikátu na řešení. Pokud koncový uživatel uděluje vztah důvěryhodnosti k řešení, se vytvoří položku seznamu povolených, který obsahuje adresu URL a veřejný klíč slouží k uložení tohoto vztahu důvěryhodnosti rozhodnutí. Když důvěryhodné přizpůsobení se spustí později, koncový uživatel se znovu zobrazí výzva.  
  
 Správci mohou zakázat [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] důvěryhodný dotaz nebo vyžadovat, aby řádku vzniknout jen pro řešení, které jsou podepsané certifikátem Authenticode. Další informace o tom, jak změnit toto nastavení pro tento počítač, LocalIntranet, Internet, TrustedSites a UntrustedSites zóny najdete v tématu [postupy: Konfigurace chování výzvy důvěryhodnosti ClickOnce](/visualstudio/deployment/how-to-configure-the-clickonce-trust-prompt-behavior).  
  
## <a name="see-also"></a>Viz také  
 [Zabezpečení řešení pro systém Office](../vsto/securing-office-solutions.md)   
 [Udělení důvěryhodnosti do dokumentů](../vsto/granting-trust-to-documents.md)   
 [Odstraňování problémů se zabezpečením řešení Office](../vsto/troubleshooting-office-solution-security.md)   
 [Specifické aspekty zabezpečení pro řešení Office](../vsto/specific-security-considerations-for-office-solutions.md)  
  
  