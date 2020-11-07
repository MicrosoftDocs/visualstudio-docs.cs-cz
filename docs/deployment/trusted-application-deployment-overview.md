---
title: Přehled nasazení důvěryhodných aplikací | Microsoft Docs
description: Naučte se, jak nasadit aplikace ClickOnce se zvýšenými oprávněními pomocí technologie nasazení důvěryhodných aplikací.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, install without prompting
- ClickOnce deployment, security
- trusted application deployment
ms.assetid: b24a1702-8fbe-45b1-87a0-9618a0708f1d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 96dfb98b468782f771d866b33b94b2c18de6276f
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2020
ms.locfileid: "94350488"
---
# <a name="trusted-application-deployment-overview"></a>Přehled nasazení důvěryhodných aplikací
Toto téma poskytuje přehled o tom, jak nasadit [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikace se zvýšenými oprávněními pomocí technologie nasazení důvěryhodných aplikací.

 Nasazení důvěryhodných aplikací, které je součástí [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] technologie nasazení, usnadňuje organizacím libovolné velikosti přístup k spravované aplikaci, a to bez nutnosti zobrazení výzvy uživateli. V případě nasazení důvěryhodných aplikací může organizace nakonfigurovat pouze klientský počítač tak, aby měl seznam důvěryhodných vydavatelů, kteří jsou identifikováni pomocí certifikátů technologie Authenticode. Potom jakákoliv [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikace podepsaná jedním z těchto důvěryhodných vydavatelů obdrží vyšší úroveň důvěryhodnosti.

> [!NOTE]
> Nasazení důvěryhodných aplikací vyžaduje jednorázovou konfiguraci počítače uživatele. Ve spravovaných prostředích plochy se tato konfigurace dá provést pomocí globálních zásad. Pokud to pro vaši aplikaci nechcete, použijte místo toho zvýšení oprávnění. Další informace najdete v tématu [zabezpečení aplikací ClickOnce](../deployment/securing-clickonce-applications.md).

## <a name="trusted-application-deployment-basics"></a>Základy nasazení důvěryhodných aplikací
 V následující tabulce jsou uvedeny objekty a role, které jsou součástí nasazení důvěryhodné aplikace.

|Objekt nebo role|Popis|
|--------------------|-----------------|
|správce|Organizační entita zodpovědná za aktualizace a údržbu klientských počítačů|
|správce vztahu důvěryhodnosti|Podsystém v rámci modulu CLR (Common Language Runtime), který je zodpovědný za vynucování zabezpečení klientských aplikací.|
|vydavatel|Entita, která zapisuje a udržuje aplikaci.|
|modul pro nasazení|Entita, kterou aplikace balí a distribuuje uživatelům.|
|certifikát|Kryptografický podpis, který se skládá z veřejného a privátního klíče; obecně vydané certifikační autoritou (CA), která může zaručí za jeho pravost.|
|Certifikát Authenticode|Certifikát s vloženými metadaty, které popisují mimo jiné použití, pro které může být certifikát zaměstnán.|
|certifikační autorita|Organizace, která ověřuje identitu vydavatelů a vydává jim certifikáty vložené s metadaty vydavatele.|
|Kořenová autorita|Certifikační autorita, která zmocňuje jiné certifikační autority k vystavování certifikátů.|
|kontejner klíčů|Logický prostor úložiště v systému Microsoft Windows pro ukládání certifikátů.|
|důvěryhodný vydavatel|Vydavatel, jehož certifikát Authenticode byl přidán do seznamu důvěryhodných certifikátů (CTL) v klientském počítači.|

 Ve větších organizacích je Vydavatel a nástroj pro nasazení často dvě samostatné entity:

- Vydavatel je skupina, která vytváří [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikaci.

- Modul pro nasazení je skupina, obvykle oddělení informačních technologií (IT), která distribuuje [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikaci do firemních stolních počítačů.

Chcete-li využít výhod nasazení důvěryhodných aplikací, je nutné postupovat podle těchto kroků:

1. Získejte certifikát pro vydavatele.

2. Přidejte vydavatele do úložiště důvěryhodných vydavatelů na všech klientech.

3. Vytvořte [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikaci.

4. Podepište manifest nasazení s certifikátem vydavatele.

5. Publikujte nasazení aplikace do klientských počítačů.

### <a name="obtain-a-certificate-for-the-publisher"></a>Získání certifikátu pro vydavatele
 Digitální certifikáty jsou základní součástí systému ověřování a zabezpečení technologie Authenticode společnosti Microsoft. Technologie Authenticode je standardní součástí operačního systému Windows. Všechny [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikace musí být podepsané digitálním certifikátem bez ohledu na to, jestli se účastní nasazení důvěryhodné aplikace. Úplné vysvětlení, jak technologie Authenticode pracuje s [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] , naleznete v tématu [ClickOnce and Authenticode](../deployment/clickonce-and-authenticode.md).

### <a name="add-the-publisher-to-the-trusted-publishers-store"></a>Přidat vydavatele do úložiště důvěryhodných vydavatelů
 Aby [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikace získala vyšší úroveň důvěryhodnosti, je nutné přidat certifikát jako důvěryhodného vydavatele do každého klientského počítače, na kterém bude aplikace spuštěna. Provádění této úlohy je jednorázová konfigurace. Po dokončení můžete nasadit tolik [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikací podepsaných vaším certifikátem vydavatele podle potřeby a všechny budou spouštěny s vysokou důvěryhodností.

 Pokud nasazujete aplikaci ve spravovaném desktopovém prostředí; například podnikový intranet s operačním systémem Windows; můžete přidat důvěryhodné vydavatele do úložiště klienta vytvořením nového seznamu důvěryhodných certifikátů (CTL) pomocí Zásady skupiny. Další informace najdete v tématu [Vytvoření seznamu důvěryhodných certifikátů pro objekt Zásady skupiny](/previous-versions/windows/it-pro/windows-server-2003/cc728449(v=ws.10)).

 Pokud nechcete aplikaci nasazovat do spravovaného desktopového prostředí, máte k dispozici následující možnosti pro přidání certifikátu do úložiště důvěryhodných vydavatelů:

- <xref:System.Security.Cryptography?displayProperty=fullName>Obor názvů.

- *CertMgr.exe* , která je součástí aplikace Internet Explorer a je proto v systému Windows 98 a všech novějších verzích. Další informace najdete v tématu [Certmgr.exe (nástroj Správce certifikátů)](/dotnet/framework/tools/certmgr-exe-certificate-manager-tool).

### <a name="create-a-clickonce-application"></a>Vytvoření aplikace ClickOnce
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]Aplikace je klientská aplikace .NET Framework v kombinaci se soubory manifestu, které popisují aplikaci a poskytují parametry instalace. Program můžete převést do [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikace pomocí příkazu **publikovat** v [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Případně můžete vygenerovat všechny soubory potřebné pro [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] nasazení pomocí nástrojů, které jsou součástí nástroje [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)] . Podrobné pokyny k [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] nasazení najdete v tématu [Návod: Ruční nasazení aplikace ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).

 Nasazení důvěryhodných aplikací je specifické pro [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] a lze je používat pouze s [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacemi.

### <a name="sign-the-deployment"></a>Podepsat nasazení
 Po získání certifikátu ho musíte použít k podepsání vašeho nasazení. Pokud nasazujete aplikaci pomocí [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Průvodce publikováním, průvodce automaticky vygeneruje testovací certifikát, pokud jste nezadali certifikát sami. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]K poskytnutí certifikátu poskytnutého certifikační autoritou ale můžete použít také okno Návrháře projektu.  Viz také [Postupy: publikování aplikace ClickOnce pomocí Průvodce publikováním](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).

> [!CAUTION]
> Nedoporučujeme, aby se aplikace nasadila s testovacím certifikátem.

 Aplikaci můžete podepsat také pomocí nástrojů *Mage.exe* nebo *MageUI.exe* SDK. Další informace najdete v tématu [Návod: Ruční nasazení aplikace ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Úplný seznam možností příkazového řádku souvisejících s podepisováním nasazení najdete v tématu [Mage.exe (Manifest Generation and Editing Tool)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool).

### <a name="publish-the-application"></a>Publikování aplikace
 Jakmile budete mít podepsané [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifesty, aplikace je připravena k publikování do umístění instalace. Umístění instalace může být webovým serverem, sdílenou složkou nebo místním diskem. Při prvním přístupu klienta k manifestu nasazení musí správce vztahu důvěryhodnosti zvolit, zda byla [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikaci udělena autoritě nebo aby neběžela na vyšší úrovni vztahu důvěryhodnosti nainstalovaného důvěryhodného vydavatele. Správce vztahu důvěryhodnosti tuto volbu provede porovnáním certifikátu použitého k podepsání nasazení s certifikáty uloženými v důvěryhodném úložišti vydavatelů klienta. Pokud správce vztahu důvěryhodnosti najde shodu, aplikace se spustí s vysokou důvěryhodností.

## <a name="trusted-application-deployment-and-permission-elevation"></a>Nasazení důvěryhodné aplikace a zvýšení oprávnění
 Pokud aktuální Vydavatel není důvěryhodný vydavatel, správce vztahu důvěryhodnosti použije zvýšení oprávnění k dotazování uživatele na to, jestli chce udělit aplikaci zvýšená oprávnění. Pokud správce zakáže zvýšení oprávnění, aplikace ale nemůže získat oprávnění ke spuštění. Aplikace nebude spuštěna a uživateli se nezobrazí žádné oznámení. Další informace o zvýšení oprávnění najdete v tématu [zabezpečení aplikací ClickOnce](../deployment/securing-clickonce-applications.md).

## <a name="limitations-of-trusted-application-deployment"></a>Omezení nasazení důvěryhodné aplikace
 Nasazení důvěryhodné aplikace můžete použít k udělení zvýšené důvěryhodnosti [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacím nasazeným přes web nebo prostřednictvím podnikové sdílené složky. Nemusíte používat důvěryhodné nasazení aplikací pro [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikace distribuované na disku CD, protože ve výchozím nastavení jsou těmto aplikacím udělený úplný vztah důvěryhodnosti.

## <a name="see-also"></a>Viz také
- [Mage.exe (Manifest Generation and Editing Tool)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)
- [Návod: Ruční nasazení aplikace ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)
