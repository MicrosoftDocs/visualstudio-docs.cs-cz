---
title: Zabezpečení řešení pro systém Office
description: Přečtěte si, jak model zabezpečení pro řešení Office zahrnuje několik technologií, včetně Visual Studio Tools for Office runtime a ClickOnce.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, security
- Office applications [Office development in Visual Studio], security
- security [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 3576bdc41f25b95b68230e09e07b1a5ed97016c6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99906648"
---
# <a name="secure-office-solutions"></a>Zabezpečení řešení pro systém Office
  Model zabezpečení pro řešení Office zahrnuje několik technologií: [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] , [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] , Centrum zabezpečení v systém Microsoft Office a zónu serverů s omezeným přístupem v Internet Exploreru. Následující části popisují, jak fungují různé funkce zabezpečení:

- [Udělení vztahu důvěryhodnosti řešením pro systém Office](#GrantingTrustToSolutions)

- [Udělení důvěryhodnosti k dokumentům](#GrantingTrustToDocuments)

- [Udělit důvěryhodnost při použití Instalační služba systému Windows](#GrantingTrustWindowsInstaller)

- [Konkrétní požadavky na zabezpečení pro řešení Office](#Security)

- [Zabezpečení během vývoje](#SecurityDuringDeployment)

- [Visual Studio Tools for Office runtime](#VisualStudioToolsForOfficeRuntime)

  [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="grant-trust-to-office-solutions"></a><a name="GrantingTrustToSolutions"></a> Udělení vztahu důvěryhodnosti řešením pro systém Office
 Udělení vztahu důvěryhodnosti řešením pro systém Office znamená úpravu zásad zabezpečení pro každého koncového uživatele, aby důvěřovali řešení Office v závislosti na následujících důkazech:

- Certifikát použitý k podepsání manifestu nasazení.

- Adresa URL manifestu nasazení.

  Další informace najdete v tématu [udělení vztahu důvěryhodnosti řešením pro systém Office](../vsto/granting-trust-to-office-solutions.md).

## <a name="grant-trust-to-documents"></a><a name="GrantingTrustToDocuments"></a> Udělení důvěryhodnosti k dokumentům
 Přizpůsobení na úrovni dokumentu vyžaduje, aby byl dokument v adresáři, který je určen jako důvěryhodné umístění. Další informace najdete v tématu [udělení důvěryhodnosti k dokumentům](../vsto/granting-trust-to-documents.md).

## <a name="grant-trust-when-using-windows-installer"></a><a name="GrantingTrustWindowsInstaller"></a> Udělit důvěryhodnost při použití Instalační služba systému Windows
 Pomocí Instalační služba systému Windows můžete vytvořit soubor MSI pro instalaci řešení Office do adresáře Program Files, který vyžaduje oprávnění správce. V případě řešení pro systém Office v adresáři Program Files aplikace Visual Studio 2010 Tools for Office runtime posuzuje tato řešení pro systém Office jako důvěryhodná a nezobrazuje výzvu k zobrazení výzvy k zadání důvěryhodnosti ClickOnce.

## <a name="specific-security-considerations-for-office-solutions"></a><a name="Security"></a> Konkrétní požadavky na zabezpečení pro řešení Office
 Funkce zabezpečení poskytované [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] , [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] a systém Microsoft Office můžou přispět k ochraně před nejrůznějšími případnými bezpečnostními hrozbami v řešeních pro systém Office. Další informace najdete v tématu [specifické požadavky na zabezpečení pro řešení Office](../vsto/specific-security-considerations-for-office-solutions.md).

## <a name="security-during-development"></a><a name="SecurityDuringDeployment"></a> Zabezpečení během vývoje
 Aby byl proces vývoje snazší, sada Visual Studio nastaví zásady zabezpečení, které jsou nutné ke spuštění a ladění řešení v počítači při každém sestavení projektu. V některých scénářích může být nutné provést další kroky zabezpečení pro vývoj projektu.

### <a name="document-level-solutions"></a>Řešení na úrovni dokumentu
 Plně kvalifikovaná cesta k dokumentu musí být přidána do seznamu důvěryhodných umístění v aplikaci systém Microsoft Office, pokud vyvíjíte následující typy projektů:

- Řešení na úrovni dokumentu, která jsou v síťové sdílené složce, například *\\ \servername\sharename*.

- Řešení na úrovni dokumentu pro Word, které používají soubory. *doc* nebo *. docm* .

  Zahrňte podadresáře, když přidáte umístění dokumentu do seznamu důvěryhodných umístění nebo konkrétně zahrnete složky pro ladění a sestavení. Další informace najdete v článku systém Microsoft Office online nápovědě pro [Vytvoření, odebrání nebo změnu důvěryhodného umístění souborů](https://support.office.com/article/Create-remove-or-change-a-trusted-location-for-your-files-f5151879-25ea-4998-80a5-4208b3540a62).

### <a name="temporary-certificates"></a>Dočasné certifikáty
 Pokud podpisový certifikát ještě neexistuje, Visual Studio vytvoří dočasný certifikát. Tento dočasný certifikát byste měli použít jenom během vývoje a koupit oficiální certifikát pro nasazení.

 Po prvním sestavení projektu Office se vygeneruje dočasný certifikát. Při příštím stisknutí klávesy **F5** se projekt znovu sestaví, protože projekt je po přidání certifikátu označen jako změněný.

 Po chvíli může existovat spousta dočasných certifikátů, proto byste měli dočasné certifikáty vymazat občas.

## <a name="visual-studio-tools-for-office-runtime"></a><a name="VisualStudioToolsForOfficeRuntime"></a> Modul runtime Visual Studio Tools for Office
 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]Obsahuje funkce pro ověření identity vydavatele a oprávnění, která jsou udělena pro vlastní nastavení. Ověřuje tato oprávnění prostřednictvím posloupnosti kontrol zabezpečení.

### <a name="security-during-customization-loading"></a>Zabezpečení při načítání vlastního nastavení
 Když je načteno přizpůsobení na úrovni dokumentu, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] vždy zkontroluje, zda je dokument v seznamu důvěryhodných umístění. Kromě toho modul runtime kontroluje, zda řešení požaduje FullTrust v manifestu aplikace. Během načítání přizpůsobení neprovede žádné další kontroly zabezpečení.

### <a name="sequence-of-security-checks-during-installation"></a>Sekvence kontrol zabezpečení při instalaci
 Při instalaci nebo aktualizaci řešení pro systém Office provede aplikace [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] sadu kontrol zabezpečení v určitém pořadí, aby bylo možné rozhodnout o důvěryhodnosti. Řešení je nainstalováno nebo aktualizováno pouze v případě, že modul runtime zjistí, že řešení je důvěryhodné.

 Proces instalace můžete spustit jedním ze čtyř způsobů: spuštěním instalačního programu, otevřením manifestu nasazení, otevřením hostitele aplikace systém Microsoft Office nebo spuštěním *VSTOInstaller.exe*.

 První kontrolu zabezpečení platí pouze pro řešení na úrovni dokumentu. Dokument řešení na úrovni dokumentu musí být v důvěryhodném umístění. Pokud se dokument nachází ve vzdálené síťové sdílené složce nebo má příponu názvu souboru *. doc* nebo *. docm* , musí být umístění dokumentu přidáno do seznamu důvěryhodných umístění. Další informace najdete v tématu [udělení důvěryhodnosti k dokumentům](../vsto/granting-trust-to-documents.md).

 ![Zabezpečení VSTO – instalace z systém Microsoft Office](../vsto/media/host-install.png "Zabezpečení VSTO – instalace z systém Microsoft Office")

 Další sada kontrol zabezpečení je z rozhraní [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] a ClickOnce. Aby bylo možné tyto kontroly předat, musí řešení pro systém Office vyžadovat oprávnění FullTrust, být podepsána certifikátem, který není uveden v seznamu nedůvěryhodných vydavatelů, a musí být v umístění, které není v zóně s omezeným přístupem aplikace Internet Explorer. Pokud je certifikát v seznamu důvěryhodných vydavatelů, řešení se nainstaluje hned. V opačném případě, pokud nedošlo k selhání jedné z kontrol, řešení pokračuje v závěrečné sadě kontrol.

 ![Zabezpečení VSTO pro instalaci řešení](../vsto/media/installing.png "Zabezpečení VSTO pro instalaci řešení")

 Pokud [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] je povolená výzva vztahu důvěryhodnosti a řešení ještě nebylo uděleno jako důvěryhodný, modul runtime umožní, aby uživatel učinil rozhodnutí o důvěryhodnosti koncového uživatele. Pokud uživatel pro řešení udělí důvěru, přidá se do seznamu povolených uživatelů položka. Všechna řešení v seznamu pro zahrnutí uživatelů mají úplný vztah důvěryhodnosti a můžou být nainstalovaná a spuštěná.

 Počínaje sadou Visual Studio 2010 se seznam zahrnutí obejít, pokud je řešení Office nainstalované pomocí Instalační služba systému Windows (MSI) do adresáře Program Files. Další informace najdete v tématu [důvěřující řešení pro Office pomocí seznamů zahrnutí](../vsto/trusting-office-solutions-by-using-inclusion-lists.md).

 ![Zabezpečení VSTO – použití instalačního programu k instalaci](../vsto/media/setup-vstoinstaller.png "Zabezpečení VSTO – použití instalačního programu k instalaci")

## <a name="see-also"></a>Viz také

- [Udělení vztahu důvěryhodnosti řešením pro systém Office](../vsto/granting-trust-to-office-solutions.md)
- [Udělení důvěryhodnosti k dokumentům](../vsto/granting-trust-to-documents.md)
- [Důvěryhodná řešení pro Office pomocí seznamů zahrnutí](../vsto/trusting-office-solutions-by-using-inclusion-lists.md)
- [Postupy: Konfigurace zabezpečení seznamu zahrnutí](../vsto/how-to-configure-inclusion-list-security.md)
- [Postupy: podepisování řešení pro systém Office](../vsto/how-to-sign-office-solutions.md)
- [Řešení potíží se zabezpečením řešení pro systém Office](../vsto/troubleshooting-office-solution-security.md)
- [Manifesty aplikace pro řešení Office](../vsto/application-manifests-for-office-solutions.md)
- [Manifesty nasazení pro řešení Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Odkaz na ClickOnce](../deployment/clickonce-reference.md)
- [Nasazení řešení pro systém Office](../vsto/deploying-an-office-solution.md)
