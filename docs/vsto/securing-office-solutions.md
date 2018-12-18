---
title: Zabezpečení řešení pro systém Office
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, security
- Office applications [Office development in Visual Studio], security
- security [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 13b0680e9222302feab8a7cbe1ad375a1f7255be
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49846197"
---
# <a name="secure-office-solutions"></a>Zabezpečení řešení pro systém Office
  Model zabezpečení pro Office řešení zahrnuje několik technologií: [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)], [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)], v Centru zabezpečení v Microsoft Office a zónu lokalit s omezeným přístupem aplikace Internet Explorer. Následující části popisují, jak fungují různé funkce zabezpečení:  
  
- [Zajistit jeho důvěryhodnost do řešení pro systém Office](#GrantingTrustToSolutions)  
  
- [Zajistit jeho důvěryhodnost do dokumentů](#GrantingTrustToDocuments)  
  
- [Zajistit jeho důvěryhodnost při použití Instalační služby systému Windows](#GrantingTrustWindowsInstaller)  
  
- [Specifické aspekty zabezpečení pro řešení pro systém Office](#Security)  
  
- [Zabezpečení během vývoje.](#SecurityDuringDeployment)  
  
- [Visual Studio Tools for Office runtime](#VisualStudioToolsForOfficeRuntime)  
  
  [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
##  <a name="GrantingTrustToSolutions"></a> Zajistit jeho důvěryhodnost do řešení pro systém Office  
 Muselo důvěřovat řešení pro systém Office znamená, že úprava zásady zabezpečení jednotlivých koncových uživatelů důvěřovat řešení pro Office podle následujících informací:  
  
- Certifikát použitý k podepsání manifestu nasazení.  
  
- Adresa URL manifestu nasazení.  
  
  Další informace najdete v tématu [zajištění důvěryhodnosti řešení pro systém Office](../vsto/granting-trust-to-office-solutions.md).  
  
##  <a name="GrantingTrustToDocuments"></a> Zajistit jeho důvěryhodnost do dokumentů  
 Přizpůsobení úrovni dokumentu vyžaduje, aby v adresáři, který je určený jako důvěryhodné umístění dokumentu. Další informace najdete v tématu [udělit důvěryhodnost dokumenty](../vsto/granting-trust-to-documents.md).  
  
##  <a name="GrantingTrustWindowsInstaller"></a> Zajistit jeho důvěryhodnost při použití Instalační služby systému Windows  
 Instalační služby systému Windows slouží k vytvoření soubor MSI, který chcete nainstalovat řešení pro systém Office v adresáři Program Files, což vyžaduje oprávnění správce. Pro řešení pro systém Office v adresáři Program Files Visual Studio 2010 Tools for Office runtime bere v úvahu tyto řešení Office na důvěryhodné a nezobrazuje výzvy důvěryhodnosti ClickOnce.  
  
##  <a name="Security"></a> Specifické aspekty zabezpečení pro řešení pro systém Office  
 Funkcích zabezpečení poskytovaných [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)], [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)], a Microsoft Office může pomoct chránit proti různým druhům možné bezpečnostní hrozby v řešeních pro systém Office. Další informace najdete v tématu [specifické aspekty zabezpečení pro řešení Office](../vsto/specific-security-considerations-for-office-solutions.md).  
  
##  <a name="SecurityDuringDeployment"></a> Zabezpečení během vývoje.  
 Abychom usnadnili vašeho vývojového procesu, Visual Studio nastaví zásady zabezpečení, které je potřeba spustit a ladit vaše řešení ve vašem počítači pokaždé, když sestavení projektu. V některých případech můžete potřebovat udělat dodatečné zabezpečení k vývoji projektu.  
  
### <a name="document-level-solutions"></a>Řešení na úrovni dokumentu  
 Plně kvalifikovanou cestu k dokumentu musí přidat do seznamu důvěryhodných umístění v aplikaci Microsoft Office, pokud vyvíjíte následující typy projektů:  
  
- Řešení, která jsou ve sdílené síti, jako je například na úrovni dokumentu  *\\\servername\sharename*.  
  
- Dokument úrovni řešení pro Word, použít *doc* nebo *DOCM* soubory.  
  
  Zahrnout podadresáře přidejte umístění dokumentu do seznamu důvěryhodných umístění nebo konkrétně zahrnout ladění a vytvoření složky. Další informace najdete v článku Microsoft Office Online nápověda [vytvoření, odebrání nebo změna důvěryhodného umístění pro soubory](https://support.office.com/article/Create-remove-or-change-a-trusted-location-for-your-files-f5151879-25ea-4998-80a5-4208b3540a62).  
  
### <a name="temporary-certificates"></a>Dočasné certifikáty  
 Visual Studio vytvoří dočasný certifikát, pokud podpisový certifikát ještě neexistuje. Doporučujeme použít tento dočasný certifikát pouze během vývoje a zakoupit certifikát oficiální pro nasazení.  
  
 Dočasný certifikát je vygenerovaný po prvním sestavení projektu pro Office. Při příštím stisknutí klávesy **F5**, znovu projekt je vytvořen, protože projekt je označen jako změnit, pokud je certifikát přidat.  
  
 Po chvíli se může být velký počet certifikátů dočasné tak dočasné certifikáty byste měli vymazat čas od času.  
  
##  <a name="VisualStudioToolsForOfficeRuntime"></a> Visual Studio Tools for Office runtime  
 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Obsahuje funkce, které chcete ověřit identitu vydavatele a oprávnění, která jsou udělena pro přizpůsobení. Ověřuje tato oprávnění pomocí sekvence kontroly zabezpečení.  
  
### <a name="security-during-customization-loading"></a>Zabezpečení během načítání vlastního nastavení  
 Při načtení přizpůsobení na úrovni dokumentu [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] vždy kontroluje, zda je dokument v seznamu důvěryhodných umístění. Kromě toho modul runtime zkontroluje, jestli řešení požadavků FullTrust v manifestu aplikace. Při načítání vlastního nastavení provede žádné další kontroly zabezpečení.  
  
### <a name="sequence-of-security-checks-during-installation"></a>Posloupnost kontroly zabezpečení během instalace  
 Při instalaci nebo aktualizaci, řešení pro Office [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] provede sadu kontroly zabezpečení v určitém pořadí pro provedení rozhodnutí důvěryhodnosti. Řešení instalaci nebo aktualizaci pouze v případě, že modul runtime určuje, že řešení je důvěryhodný.  
  
 Můžete zahájit proces instalace v jedné ze čtyř způsobů: spuštěním instalační program, otevřou manifest nasazení, otevřením hostitele aplikace Microsoft Office nebo spuštěním *VSTOInstaller.exe*.  
  
 První kontrola zabezpečení se vztahuje pouze na řešeních na úrovni dokumentu. Řešení úrovni dokumentu dokument musí být v důvěryhodném umístění. Pokud dokument je ve sdílené složce vzdálené sítě nebo má *doc* nebo *DOCM* příponu názvu souboru umístění dokumentu musí být přidané do seznamu důvěryhodných umístění. Další informace najdete v tématu [udělit důvěryhodnost dokumenty](../vsto/granting-trust-to-documents.md).  
  
 ![Zabezpečení VSTO – instalace z aplikace Microsoft Office](../vsto/media/host-install.png "VSTO zabezpečení – instalace z aplikace Microsoft Office")  
  
 Další sadu kontroly zabezpečení jsou z [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] a ClickOnce. K předání těchto kontrol, řešení pro systém Office musí požádat o oprávnění FullTrust, byly podepsány certifikátem, který není uvedený v seznamu nedůvěryhodných vydavatele a být v umístění, které se nenachází v zóně Internet Exploreru s omezeným přístupem. Pokud je certifikát v seznamu Důvěryhodné vydavatele, řešení nainstalováno okamžitě. V opačném případě pokud jejího selhání není jedna z kontrol, řešení dál obsahuje závěrečnou sadu kontroly.  
  
 ![Zabezpečení VSTO pro instalaci řešení](../vsto/media/installing.png "VSTO zabezpečení pro instalaci řešení")  
  
 Pokud [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] povolený výzva vztahu důvěryhodnosti a řešení dosud nebyl udělen vztahu důvěryhodnosti, modul runtime vám umožní rozhodnutí důvěryhodnosti, který má být provedeno koncovým uživatelem. Pokud uživatel uděluje vztah důvěryhodnosti k řešení, bude položka přidána do seznamu povolených položek uživatele. Všechna řešení v seznamu povolených položek uživatelů úplný vztah důvěryhodnosti a může být nainstalován a spuštěn.  
  
 Spouští se v sadě Visual Studio 2010, seznam povolených položek přeskočí nainstalovali řešení sady Office pomocí Instalační služby systému Windows (MSI) do adresáře Program Files. Další informace najdete v tématu [řešení důvěřovat Office s použitím seznamů povolených položek](../vsto/trusting-office-solutions-by-using-inclusion-lists.md).  
  
 ![Zabezpečení VSTO – instalace pomocí instalačního programu](../vsto/media/setup-vstoinstaller.png "VSTO zabezpečení – instalace pomocí instalačního programu")  
  
## <a name="see-also"></a>Viz také:  
 [Zajistit jeho důvěryhodnost do řešení pro systém Office](../vsto/granting-trust-to-office-solutions.md)   
 [Zajistit jeho důvěryhodnost do dokumentů](../vsto/granting-trust-to-documents.md)   
 [Vztah důvěryhodnosti řešení pro systém Office s použitím seznamů povolených položek](../vsto/trusting-office-solutions-by-using-inclusion-lists.md)   
 [Postupy: konfigurace zabezpečení se seznamem povolených položek](../vsto/how-to-configure-inclusion-list-security.md)   
 [Postupy: podepisování řešení pro Office](../vsto/how-to-sign-office-solutions.md)   
 [Řešení potíží se zabezpečením řešení pro systém Office](../vsto/troubleshooting-office-solution-security.md)   
 [Manifesty aplikace pro řešení pro systém Office](../vsto/application-manifests-for-office-solutions.md)   
 [Manifesty nasazení pro řešení pro systém Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Referenční dokumentace technologie ClickOnce](/visualstudio/deployment/clickonce-reference)   
 [Nasazení řešení Office](../vsto/deploying-an-office-solution.md)  
  
  