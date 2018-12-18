---
title: Trusted Application Deployment Overview | Dokumentace Microsoftu
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
- ClickOnce deployment, install without prompting
- ClickOnce deployment, security
- trusted application deployment
ms.assetid: b24a1702-8fbe-45b1-87a0-9618a0708f1d
caps.latest.revision: 33
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 733eb98544d48716ec073605d68628ddeab7b794
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49827581"
---
# <a name="trusted-application-deployment-overview"></a>Přehled nasazení důvěryhodných aplikací
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Toto téma obsahuje přehled o tom, jak nasadit [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikace, které se zvýšenými oprávněními pomocí technologie Trusted Application Deployment.  
  
 Nasazení důvěryhodných aplikací, součástí [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] technologie nasazení usnadňuje pro organizace všech velikostí udělit další oprávnění, aby spravované aplikace bez vyzvání uživatele bezpečnější a lépe zabezpečeným způsobem. Pomocí nasazení důvěryhodné aplikace organizace jenom konfigurace klientského počítače na seznam důvěryhodných vydavatelů, kteří se identifikují pomocí technologie Authenticode certifikátů. Poté jakákoli [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] žádosti podepsány jednu z těchto důvěryhodných vydavatelů obdrží vyšší úroveň důvěryhodnosti.  
  
> [!NOTE]
>  Důvěryhodné že aplikace nasazení vyžaduje jednorázovou konfiguraci počítače uživatele. Ve spravovaném prostředí plochy můžete tuto konfiguraci provést pomocí globálních zásad. Pokud je to, co jste, aby pro vaši aplikaci, místo toho použijte zvýšení oprávnění. Další informace najdete v tématu [zabezpečení aplikací ClickOnce](../deployment/securing-clickonce-applications.md).  
  
## <a name="trusted-application-deployment-basics"></a>Základní informace o nasazení důvěryhodné aplikace  
 Následující tabulka uvádí objekty a rolí, které jsou zahrnuty v Trusted Application Deployment.  
  
|Objekt nebo role|Popis|  
|--------------------|-----------------|  
|Správce|Subjektem organizace odpovědná za aktualizaci a správu klientských počítačů|  
|správce vztahu důvěryhodnosti|Subsystém v rámci modul CLR (CLR) zodpovědná za vynucování zabezpečení klientské aplikace.|  
|vydavatele|Entita, která zapisuje a udržuje aplikace.|  
|Nástroje pro nasazení|Entita, která zabalí a distribuuje aplikace pro uživatele.|  
|certificate|Kryptografický podpis, který se skládá z veřejného a privátního klíče; obecně vydaný certifikační autoritou (CA), který dokazuje pravost.|  
|Authenticode certifikátu|Certifikát s vložená metadata popisující, mimo jiné používá, pro které je možné použít certifikát.|  
|certifikační autorita|Organizace, která ověří identitu vydavatele a jejich vydává certifikáty vložených s jeho metadata.|  
|kořenová autorita|Certifikační autority, který autorizuje jiných certifikačních autorit k vystavování certifikátů.|  
|kontejner klíčů|Prostor logického úložiště pro ukládání certifikátů v Microsoft Windows.|  
|důvěryhodným vydavatelem|Vydavatel certifikátu jehož Authenticode je přidaný do seznamu důvěryhodných certifikátů (CTL) na klientském počítači.|  
  
 Větší organizace jsou často dvě samostatné entity vydavatele a nástroje pro nasazení:  
  
- Vydavatel je skupina, která vytvoří [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikace.  
  
- Modul pro nasazení je skupina, obvykle oddělení informačních technologií (IT), která distribuuje [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikace na podnikové stolní počítače.  
  
  Musíte následujícím postupem využít výhod nasazení důvěryhodné aplikace:  
  
1.  Získání certifikátu pro vydavatele.  
  
2.  Do úložiště Důvěryhodní vydavatelé na všechny klienty přidejte vydavatele.  
  
3.  Vytvoření vašeho [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikace.  
  
4.  Podepsat manifest nasazení pomocí certifikátu vydavatele.  
  
5.  Publikování nasazení aplikace do klientských počítačů.  
  
### <a name="obtain-a-certificate-for-the-publisher"></a>Získání certifikátu pro vydavatele  
 Digitální certifikáty jsou základní součástí Microsoft Authenticode ověřování a zabezpečení systému. Authenticode je standardní součástí operačního systému Windows. Všechny [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikace musí být podepsané digitálním certifikátem, bez ohledu na to, zda se účastní v Trusted Application Deployment. Úplné vysvětlení fungování Authenticode s [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)], naleznete v tématu [ClickOnce and Authenticode](../deployment/clickonce-and-authenticode.md).  
  
### <a name="add-the-publisher-to-the-trusted-publishers-store"></a>Přidat vydavatele pro důvěryhodného vydavatele Store  
 Pro vaše [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikaci pro příjem vyšší úroveň důvěryhodnosti, musíte přidat certifikát jako důvěryhodného vydavatele na každý klientský počítač, na kterém bude aplikace spuštěna. Provedení této úlohy je jednorázovou konfiguraci. Po dokončení, můžete nasadit tolik [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikace podepsané certifikátem pro vydavatele a chcete, aby všechny se spustí s vysokou důvěryhodností.  
  
 Pokud nasazujete aplikaci ve spravovaném prostředí, desktopové; třeba firemní intranetovou operačním systémem Windows; Důvěryhodní vydavatelé můžete přidat do klienta úložiště tak, že vytvoříte nový seznam důvěryhodných certifikátů (CTL) pomocí zásad skupiny. Další informace najdete v tématu [vytvoření seznamu důvěryhodných certifikátů pro objekt zásad skupiny](http://go.microsoft.com/fwlink/?LinkId=102576).  
  
 Pokud se nasazení aplikace ve spravovaném prostředí klasické pracovní plochy, máte následující možnosti pro přidání certifikátu do úložiště důvěryhodných vydavatelů:  
  
-   <xref:System.Security.Cryptography?displayProperty=fullName> Oboru názvů.  
  
-   CertMgr.exe, která je součástí aplikace Internet Explorer a proto existuje ve Windows 98 a všech novějších verzích. Další informace najdete v tématu [Certmgr.exe (nástroj Certificate Manager)](http://msdn.microsoft.com/library/7e953b43-1374-4bbc-814f-53ca1b6b52bb).  
  
### <a name="create-a-clickonce-application"></a>Vytvoření aplikace ClickOnce  
 A [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikace je [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] klientská aplikace spolu se soubory manifestu, které popisují aplikace a zadat parametry instalace. Můžete zapnout program do [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikace s použitím **publikovat** v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Alternativně můžete generovat všechny soubory potřebné pro [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] nasazení pomocí nástrojů, které jsou součástí [!INCLUDE[winsdklong](../includes/winsdklong-md.md)]. Podrobné pokyny o [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] nasazení, najdete v článku [návod: Ruční nasazení aplikace ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  
  
 Nasazení důvěryhodných aplikací je specifické pro [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]a jde použít jenom s [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikací.  
  
### <a name="sign-the-deployment"></a>Podepsat nasazení  
 Po obdržení vašeho certifikátu, musíte použít ho k podepsání vašeho nasazení. Pokud nasazujete aplikaci s použitím [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Průvodce publikováním, průvodce automaticky vytvoří testovací certifikát za vás v případě špatných certifikát sami. Můžete také použít [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] okna Návrháře projektu, ale k poskytnutí certifikátu Certifikační autoritou.  Viz také [postupy: publikování aplikace ClickOnce pomocí Průvodce publikováním](http://msdn.microsoft.com/library/31kztyey\(v=vs.110\)) nebo [postupy: publikování aplikace ClickOnce pomocí Průvodce publikováním](http://msdn.microsoft.com/library/31kztyey\(v=vs.110\)).  
  
> [!CAUTION]
>  Nedoporučujeme, nasadit aplikace pomocí testovacího certifikátu.  
  
 Můžete také podepsání aplikace pomocí nástroje Mage.exe nebo MageUI.exe SDK. Další informace najdete v tématu [návod: Ruční nasazení aplikace ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Úplný seznam možností příkazového řádku související podepisování nasazení najdete v tématu [Mage.exe (Manifest Generation and Editing Tool)](http://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1).  
  
### <a name="publish-the-application"></a>Publikování aplikace  
 Poté, co jste se zaregistrovali vaše [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] manifesty, aplikace je připravena k publikování do umístění instalace. Umístění instalace může být webový server, sdílené složky nebo na místní disk. Když klient přistupuje k manifestu nasazení poprvé, musíte zvolit správce vztahu důvěryhodnosti, zda [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikace získala autority nebo nespouštět na vyšší úrovni důvěryhodnosti nainstalovaného důvěryhodné vydavatele. Správce vztahu důvěryhodnosti je tato volba porovnáním certifikát používaný k podepisování nasazení pomocí certifikátů uložených v důvěryhodným vydavatelem klienta úložiště. Pokud správce vztahu důvěryhodnosti najde shodu, aplikace bude spuštěna s vysokou důvěryhodností.  
  
## <a name="trusted-application-deployment-and-permission-elevation"></a>Nasazení důvěryhodné aplikace a zvýšení úrovně oprávnění  
 Pokud aktuální vydavatel není důvěryhodným vydavatelem, správce vztahu důvěryhodnosti použije zvýšení oprávnění k dotazování uživatele, jestli uživatel chce, aby se udělení že oprávnění aplikace se zvýšenými oprávněními. Pokud zvýšení úrovně oprávnění je zakázán správcem, ale aplikace nemůže získat oprávnění ke spuštění. Aplikace se nespustí a nezobrazí se žádná oznámení uživateli. Další informace o zvýšení úrovně oprávnění najdete v tématu [zabezpečení aplikací ClickOnce](../deployment/securing-clickonce-applications.md).  
  
## <a name="limitations-of-trusted-application-deployment"></a>Omezení nasazení důvěryhodné aplikace  
 Nasazení důvěryhodné aplikace můžete použít k zajištění zvýšené důvěryhodnosti [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] nasazené prostřednictvím webu nebo prostřednictvím sdílenou složku enterprise. Není nutné používat Trusted Application Deployment pro [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] distribuované na disku CD, protože ve výchozím nastavení, jsou tyto aplikace udělena úplná důvěryhodnost aplikace.  
  
## <a name="see-also"></a>Viz také  
 [Mage.exe (generování manifestu a nástroj pro úpravy)](http://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1)   
 [Návod: Ruční nasazení aplikace ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)



