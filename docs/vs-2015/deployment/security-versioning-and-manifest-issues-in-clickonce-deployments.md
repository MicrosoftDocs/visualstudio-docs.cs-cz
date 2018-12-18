---
title: Zabezpečení správy verzí, problémy a manifestem v nasazeních ClickOnce | Dokumentace Microsoftu
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
- versioning, ClickOnce applications
- ClickOnce applications, Windows Vista User Account Control
- ClickOnce applications, versioning issues
- security, ClickOnce applications
- Windows 7, ClickOnce deployments
- ClickOnce applications, manifest issues
- User Account Control, ClickOnce applications
- Windows Vista, ClickOnce deployments
- manifests [ClickOnce]
- ClickOnce applications, security issues
ms.assetid: d5d0c90b-ac1a-44e2-88dc-0d0ffd881624
caps.latest.revision: 23
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 77685b2eb6397d1edf9a342c25838fcefac2e619
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49289221"
---
# <a name="security-versioning-and-manifest-issues-in-clickonce-deployments"></a>Problémy se zabezpečením, správou verzí a manifestem v nasazeních ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Existuje řada různých problémů s [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] zabezpečení, správy verzí aplikací a manifestu syntaxi a sémantiku, která může způsobit, že [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] není na úspěšné nasazení.  
  
## <a name="clickonce-and-windows-vista-user-account-control"></a>ClickOnce a řízení uživatelských účtů Windows Vista  
 V [!INCLUDE[windowsver](../includes/windowsver-md.md)], aplikace ve výchozím nastavení běží jako standardní uživatel, i v případě, že je aktuální uživatel přihlášen pomocí účtu, který má oprávnění správce. Pokud musí aplikace provádět akce, která vyžaduje oprávnění správce, informuje operační systém, který se potom zobrazí výzvu k zadání přihlašovacích údajů správce. Tuto funkci, která se nazývá řízení uživatelských účtů (UAC), zabrání aplikacím ve změnách, které může mít vliv na celý operační systém bez výslovného souhlasu uživatele. Aplikace Windows deklarovat, že potřebují toto zvýšení oprávnění tak, že zadáte `requestedExecutionLevel` atribut `trustInfo` jejich manifestu aplikace.  
  
 Kvůli riziku úniku aplikací k útokům na zabezpečení ke zvýšení úrovně oprávnění [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikace nelze požádat o zvýšení oprávnění, pokud je povolen nástroj Řízení uživatelských účtů pro klienta. Žádné [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikaci, která se pokouší nastavit jeho `requestedExecutionLevel` atribut `requireAdministrator` nebo `highestAvailable` nenainstaluje [!INCLUDE[windowsver](../includes/windowsver-md.md)].  
  
 V některých případech může váš [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikace můžou snažit spustit s oprávněními správce z důvodu logika pro detekci instalační program [!INCLUDE[windowsver](../includes/windowsver-md.md)]. V takovém případě můžete nastavit `requestedExecutionLevel` atribut v manifestu aplikace na `asInvoker`. To způsobí, že samotná aplikace spustit bez zvýšení oprávnění. [!INCLUDE[vs_orcas_long](../includes/vs-orcas-long-md.md)] Tento atribut se automaticky přidá do všech manifestů aplikací.  
  
 Pokud vyvíjíte aplikaci, která vyžaduje oprávnění správce pro celou dobu životnosti aplikace, musíte zvážit nasazení aplikace pomocí technologie Windows Installer (MSI). Další informace najdete v tématu [základy Instalační služby systému Windows](../extensibility/internals/windows-installer-basics.md).  
  
## <a name="online-application-quotas-and-partial-trust-applications"></a>Kvóty aplikace v režimu online a částečné důvěryhodnosti aplikací  
 Pokud vaše [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] spuštění online namísto prostřednictvím instalace aplikace, se musí vejít do kvóty vyhrazené pro online aplikace. Navíc síťová aplikace, na kterém běží v částečném vztahu důvěryhodnosti, například s omezenou sadou oprávnění zabezpečení, nemůže být větší než polovina kvóty velikosti.  
  
 Další informace a pokyny o tom, jak změnit kvóty aplikace v režimu online, najdete v článku [ClickOnce – Přehled mezipaměti](../deployment/clickonce-cache-overview.md).  
  
## <a name="versioning-issues"></a>Správa verzí – potíže  
 Pokud vaše sestavení přiřadit silný název a zvýší číslo verze sestavení tak, aby odrážely aktualizace aplikace, může docházet k potížím. Žádné sestavení zkompilovaná odkaz na sestavení se silným názvem musí samotné zopakovat nebo se pokusí o odkaz starší verzi sestavení. Sestavení se pokusí, protože sestavení používá starou hodnotu verze v žádosti o jeho vazby.  
  
 Řekněme například, že máte ve svém vlastním projektu verze 1.0.0.0 sestavení se silným názvem. Po kompilaci sestavení, můžete ho přidat jako odkaz na projekt, který obsahuje hlavní aplikace. Pokud zvýšení verze 1.0.0.1 aktualizaci sestavení a zkuste nasazení bez překompilování aplikace, aplikace nebude možné načíst sestavení v době běhu.  
  
 Této chybě může dojít pouze v případě, že upravujete vaše [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] manifesty ručně; tato chyba by nemělo dojít, pokud je generování nasazení pomocí [!INCLUDE[vsprvslong](../includes/vsprvslong-md.md)].  
  
## <a name="specifying-individual-net-framework-assemblies-in-the-manifest"></a>Zadání jednotlivých sestavení .NET Framework v manifestu  
 Vaše aplikace se nepodaří načíst, pokud musíte ručně upravit [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] nasazení tak, aby odkazovaly na starší verzi [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] sestavení. Například, pokud jste přidali odkaz na sestavení System.Net verzi [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] starší než verze určená v manifestu, pak by dojít k chybě. Obecně by se neměly pokoušet zadat odkazy na jednotlivé [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] sestavení jako verze [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] proti které aplikace běží je zadán jako závislost v manifestu aplikace.  
  
## <a name="manifest-parsing-issues"></a>Manifest analýzy chyb  
 Soubory manifestů, které jsou používány [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] jsou soubory formátu XML a musí být ve správném formátu a platný: musíte dodržovat pravidla syntaxe jazyka XML a používat pouze elementy a atributy definované v odpovídající schématu XML.  
  
 To může způsobit problémy v souboru manifestu je výběr názvu aplikace, který obsahuje speciální znaky, jako je například jednoduchých nebo dvojitých uvozovek. Název aplikace je součástí jeho [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] identity. [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aktuálně se nerozloží identity, které obsahují speciální znaky. Pokud se aplikaci nepodaří aktivovat, ujistěte se, že používáte jenom abecední a číselné znaky pro název a pokus o nasaďte jej znovu.  
  
 Pokud jste upravili ručně aplikace nebo nasazení manifestů, vám může mít je neúmyslně poškodit. Poškozená manifestu zabrání správné [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] instalace. Tyto chyby můžete ladit v době běhu kliknutím **podrobnosti** na **Chyba ClickOnce** dialogové okno a čtení chybová zpráva v protokolu. Protokol se zobrazí jedna z následujících zpráv:  
  
-   Popis chyby syntaxe a číslo řádku a znak pozici, kde došlo k chybě.  
  
-   Název elementu nebo atributu použitého v rozporu se schéma manifestu. Pokud jste ručně přidali XML do vaší manifesty, budete muset porovnání dodatky k schémat manifestů. Další informace najdete v tématu [Manifest nasazení ClickOnce](../deployment/clickonce-deployment-manifest.md) a [Manifest aplikace ClickOnce](../deployment/clickonce-application-manifest.md).  
  
-   Došlo ke konfliktu ID. Odkazy závislostí v manifesty nasazení a aplikace musí být jedinečný v obou jejich `name` a `publicKeyToken` atributy. Pokud oba atributy odpovídají mezi dva prvky v rámci manifestu, analýza manifestu nebude úspěšný.  
  
## <a name="precautions-when-manually-changing-manifests-or-applications"></a>Bezpečnostní opatření při ruční změna manifesty nebo aplikace  
 Při aktualizaci manifestu aplikace ji musíte znovu podepsat manifest aplikace a manifest nasazení. Manifest nasazení obsahuje odkaz na manifest aplikace, která obsahuje hodnotu hash pro tento soubor a jeho digitální podpis.  
  
### <a name="precautions-with-deployment-provider-usage"></a>Opatření s využitím poskytovatele nasazení  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Manifestu nasazení `deploymentProvider` vlastnost, která odkazuje na úplnou cestu k umístění z kde by měl být aplikace nainstalována a údržba:  
  
```  
<deploymentProvider codebase="http://myserver/myapp.application" />  
```  
  
 Tato cesta je nastavena, když [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] vytvoří aplikaci a je povinné pro nainstalované aplikace. Cesta odkazuje na standardní umístění ve kterém [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] instalační program nainstaluje aplikaci a vyhledat aktualizace. Pokud používáte **příkazu xcopy** příkaz pro kopírování [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikace do jiného umístění, ale neměňte `deploymentProvider` vlastnost, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] bude stále odkazovat zpět do původního umístění při pokusu o stažení aplikace.  
  
 Pokud chcete přesunout nebo kopírovat aplikaci, je nutné také aktualizovat `deploymentProvider` cestu, takže ve skutečnosti instalaci klienta z nové umístění. Aktualizuje se tato cesta je většinou žádný problém, pokud jste nainstalovali aplikace. Pro online aplikace, které jsou vždy spouštěny pomocí původní adresu URL, nastavení `deploymentProvider` je volitelný. Pokud `deploymentProvider` je nastavena, budou zachované; v opačném případě adresy URL pro spuštění aplikace se použije jako základní adresu URL pro stahování souborů aplikace.  
  
> [!NOTE]
>  Při každé aktualizaci manifestu je zapotřebí také soubor znovu podepsat.  
  
## <a name="see-also"></a>Viz také  
 [Řešení potíží s nasazením ClickOnce](../deployment/troubleshooting-clickonce-deployments.md)   
 [Zabezpečování aplikací ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Výběr strategie nasazení ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)



