---
title: Udělení vztahu důvěryhodnosti řešením pro systém Office
description: Pro udělení vztahu důvěryhodnosti řešením pro systém Office můžete změnit zásady zabezpečení pro každý cílový počítač, aby důvěřovali sestavení řešení, manifestu nasazení a dokumentu.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- security [Office development in Visual Studio], trust
- inclusion lists [Office development in Visual Studio], about inclusion lists
- trust [Office development in Visual Studio], 2007 Office system
- granting trust [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f0b81c034ed0f8934da378dc214191d3be1f4506
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/08/2020
ms.locfileid: "96848323"
---
# <a name="grant-trust-to-office-solutions"></a>Udělení vztahu důvěryhodnosti řešením pro systém Office
  Udělení vztahu důvěryhodnosti řešením pro systém Office znamená úpravu zásad zabezpečení pro každý cílový počítač pro důvěřování sestavení řešení, manifestu aplikace, manifestu nasazení a dokumentu. K řešení pro Office můžete udělit přístup buď vy, nebo koncovým uživatelem.

 Úplný vztah důvěryhodnosti k řešení Office můžete udělit podepsáním manifestů aplikace a nasazení.

 Koncoví uživatelé můžou udělit důvěru k řešení pro Office, a to tak, že v [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] příkazovém řádku důvěřuje rozhodnutí o důvěryhodnosti.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="trust-the-solution-by-signing-the-application-and-deployment-manifests"></a><a name="Signing"></a> Důvěřovat řešení podepsáním manifestů aplikace a nasazení
 Všechny manifesty aplikace a nasazení pro řešení Office musí být podepsané certifikátem, který identifikuje vydavatele. Certifikáty poskytují základ pro rozhodování o důvěryhodnosti.

 Pro vás se vytvoří dočasný certifikát a při sestavení se udělí důvěryhodnost, aby se řešení spouštělo při ladění. Pokud publikujete řešení podepsané dočasným certifikátem, zobrazí se koncovému uživateli výzva k rozhodnutí o důvěryhodnosti.

 Pokud podepíšete řešení se známým a důvěryhodným certifikátem, řešení bude automaticky nainstalováno bez vyzvání koncového uživatele, aby provedlo rozhodnutí o důvěryhodnosti. Další informace o tom, jak získat certifikát pro podepsání, naleznete v tématu [ClickOnce and Authenticode](../deployment/clickonce-and-authenticode.md). Po získání certifikátu musí být certifikát explicitně důvěryhodný přidáním do seznamu důvěryhodných vydavatelů. Další informace najdete v tématu [Postup: Přidání důvěryhodného vydavatele do klientského počítače pro aplikace ClickOnce](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md).

 Pokud vývojář podepíše řešení s dočasným certifikátem, může správce znovu podepsat vlastní nastavení se známým a důvěryhodným certifikátem pomocí Manifest Generation and Editing Tool (*mage.exe*), což je jeden z nástrojů Microsoft .NET Framework Tools. Další informace o podpisových řešeních naleznete v tématu [How to: Signing Solutions Office](../vsto/how-to-sign-office-solutions.md) and [to: Signing Application and Deployment Manifests](../ide/how-to-sign-application-and-deployment-manifests.md).

## <a name="trust-the-solution-by-using-the-clickonce-trust-prompt"></a><a name="TrustPrompt"></a>Důvěřovat řešení pomocí výzvy vztahu důvěryhodnosti ClickOnce
 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] vyzve koncového uživatele, aby vynesl rozhodnutí o důvěryhodnosti, pokud neexistuje zásada, která důvěřuje certifikátu řešení. Pokud koncový uživatel pro řešení udělí důvěru, vytvoří se položka seznamu zahrnutí, která obsahuje adresu URL a veřejný klíč pro uložení tohoto rozhodnutí o důvěryhodnosti. Po pozdějším spuštění důvěryhodného vlastního nastavení se koncový uživatel nevyzve znovu.

 Správci můžou zakázat [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] výzvu k vztahu důvěryhodnosti nebo vyžadovat, aby se zobrazila výzva jenom pro řešení, která jsou podepsaná certifikátem Authenticode. Další informace o tom, jak změnit tato nastavení pro zóny MyComputer, LocalIntranet, Internet, TrustedSites a UntrustedSites, najdete v tématu [How to: Configure a Behavior pro zobrazení výzvy důvěryhodnosti ClickOnce](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md).

## <a name="see-also"></a>Viz také

- [Zabezpečení řešení pro systém Office](../vsto/securing-office-solutions.md)
- [Udělení důvěryhodnosti k dokumentům](../vsto/granting-trust-to-documents.md)
- [Řešení potíží se zabezpečením řešení pro systém Office](../vsto/troubleshooting-office-solution-security.md)
- [Konkrétní požadavky na zabezpečení pro řešení Office](../vsto/specific-security-considerations-for-office-solutions.md)