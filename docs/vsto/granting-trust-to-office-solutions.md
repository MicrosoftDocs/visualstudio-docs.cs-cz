---
title: Udělení důvěryhodnosti řešení office
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
ms.openlocfilehash: cf7a68d5d3567305e4f70049d76a1c260ddecf25
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/13/2020
ms.locfileid: "79303300"
---
# <a name="grant-trust-to-office-solutions"></a>Udělení důvěryhodnosti řešení office
  Udělení důvěryhodnosti řešení sady Office znamená úpravu zásad zabezpečení každého cílového počítače tak, aby důvěřovala sestavení řešení, manifestu aplikace, manifestu nasazení a dokumentu. Vztah důvěryhodnosti může řešení sady Office udělit vy nebo koncový uživatel.

 Úplný vztah důvěryhodnosti řešení sady Office můžete udělit podepsáním manifestů aplikace a nasazení.

 Koncoví uživatelé mohou udělit vztah důvěryhodnosti [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] řešení Sady Office tím, že v řádku důvěryhodnosti učiní rozhodnutí o důvěryhodnosti.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="trust-the-solution-by-signing-the-application-and-deployment-manifests"></a><a name="Signing"></a>Důvěřovat řešení podpisem manifestů aplikace a nasazení
 Všechny manifesty aplikací a nasazení pro řešení sady Office musí být podepsány certifikátem, který identifikuje vydavatele. Certifikáty jsou základem pro rozhodování o důvěryhodnosti.

 Dočasný certifikát je vytvořen pro vás a udělena důvěryhodnost v době sestavení, takže řešení bude spuštěna při ladění. Pokud publikujete řešení, které je podepsáno dočasným certifikátem, bude koncový uživatel vyzván k rozhodnutí o důvěryhodnosti.

 Pokud podepíšete řešení pomocí známého a důvěryhodného certifikátu, bude automaticky nainstalováno bez výzvy koncovému uživateli k rozhodnutí o důvěryhodnosti. Další informace o získání certifikátu k podpisu naleznete v [tématech ClickOnce a Authenticode](../deployment/clickonce-and-authenticode.md). Po získání certifikátu musí být certifikát explicitně důvěryhodný přidáním do seznamu Důvěryhodných vydavatelů. Další informace naleznete v [tématu Postup: Přidání důvěryhodného vydavatele do klientského počítače pro aplikace ClickOnce](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md).

 Pokud vývojář podepíše řešení dočasným certifikátem, může správce znovu podepsat vlastní nastavení pomocí známého a důvěryhodného certifikátu pomocí nástroje Generování a úpravy manifestu *(mage.exe),* který je jedním z nástrojů rozhraní Microsoft .NET Framework. Další informace o řešeních pro podepisování najdete v [tématu Postup: Přihlášení řešení office](../vsto/how-to-sign-office-solutions.md) a [Postup: Podepsání manifestů aplikací a nasazení](../ide/how-to-sign-application-and-deployment-manifests.md).

## <a name="trust-the-solution-by-using-the-clickonce-trust-prompt"></a><a name="TrustPrompt"></a>Důvěřovat řešení pomocí výzvy důvěryhodnosti ClickOnce
 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]vyzve koncového uživatele, aby učinil rozhodnutí o důvěryhodnosti, pokud neexistuje žádná zásada pro celou organizaci, která by důvěřovala certifikátu řešení. Pokud koncový uživatel udělí řešení důvěryhodnost, vytvoří se položka seznamu zahrnutí, která obsahuje adresu URL a veřejný klíč pro uložení tohoto rozhodnutí o důvěryhodnosti. Při spuštění důvěryhodného vlastního nastavení později nebude koncový uživatel znovu vyzván.

 Správci mohou [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] zakázat výzvu důvěryhodnosti nebo vyžadovat, aby výzva nastala pouze u řešení podepsaných certifikátem Authenticode. Další informace o tom, jak změnit tato nastavení pro zóny MyComputer, LocalIntranet, Internet, TrustedSites a UntrustedSites, naleznete v [tématu Postup: Konfigurace chování výzvy důvěryhodnosti ClickOnce](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md).

## <a name="see-also"></a>Viz také

- [Bezpečná řešení Office](../vsto/securing-office-solutions.md)
- [Udělení vztahu důvěryhodnosti dokumentům](../vsto/granting-trust-to-documents.md)
- [Poradce při potížích se zabezpečením řešení Office](../vsto/troubleshooting-office-solution-security.md)
- [Konkrétní aspekty zabezpečení řešení Office](../vsto/specific-security-considerations-for-office-solutions.md)