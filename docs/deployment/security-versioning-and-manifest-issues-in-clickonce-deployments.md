---
title: Zabezpečení správy verzí, problémy a manifestem v nasazeních ClickOnce | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a7ae835b53960ca6952b71c10a2348f707785e16
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/17/2018
ms.locfileid: "39081742"
---
# <a name="security-versioning-and-manifest-issues-in-clickonce-deployments"></a>Zabezpečení správy verzí, problémy a manifestem v nasazeních ClickOnce

Existuje řada různých problémů s [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] zabezpečení, správy verzí aplikací a manifestu syntaxi a sémantiku, která může způsobit, že [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] není na úspěšné nasazení.

## <a name="clickonce-and-windows-vista-user-account-control"></a>ClickOnce a řízení uživatelských účtů Windows Vista

V [!INCLUDE[windowsver](../deployment/includes/windowsver_md.md)], aplikace ve výchozím nastavení běží jako standardní uživatel, i v případě, že je aktuální uživatel přihlášen pomocí účtu, který má oprávnění správce. Pokud musí aplikace provádět akce, která vyžaduje oprávnění správce, informuje operační systém, který se potom zobrazí výzvu k zadání přihlašovacích údajů správce. Tuto funkci, která se nazývá řízení uživatelských účtů (UAC), zabrání aplikacím ve změnách, které může mít vliv na celý operační systém bez výslovného souhlasu uživatele. Aplikace Windows deklarovat, že potřebují toto zvýšení oprávnění tak, že zadáte `requestedExecutionLevel` atribut `trustInfo` jejich manifestu aplikace.

Kvůli riziku úniku aplikací k útokům na zabezpečení ke zvýšení úrovně oprávnění [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikace nelze požádat o zvýšení oprávnění, pokud je povolen nástroj Řízení uživatelských účtů pro klienta. Žádné [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikaci, která se pokouší nastavit jeho `requestedExecutionLevel` atribut `requireAdministrator` nebo `highestAvailable` nenainstaluje [!INCLUDE[windowsver](../deployment/includes/windowsver_md.md)].

V některých případech může váš [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikace můžou snažit spustit s oprávněními správce z důvodu logika pro detekci instalační program [!INCLUDE[windowsver](../deployment/includes/windowsver_md.md)]. V takovém případě můžete nastavit `requestedExecutionLevel` atribut v manifestu aplikace na `asInvoker`. To způsobí, že samotná aplikace spustit bez zvýšení oprávnění. [!INCLUDE[vs_orcas_long](../debugger/includes/vs_orcas_long_md.md)] Tento atribut se automaticky přidá do všech manifestů aplikací.

Pokud vyvíjíte aplikaci, která vyžaduje oprávnění správce pro celou dobu životnosti aplikace, musíte zvážit nasazení aplikace pomocí technologie Windows Installer (MSI). Další informace najdete v tématu [Instalační služby systému Windows Základy](../extensibility/internals/windows-installer-basics.md).

## <a name="online-application-quotas-and-partial-trust-applications"></a>Kvóty online aplikace a aplikace s částečnou důvěryhodností

Pokud vaše [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] spuštění online namísto prostřednictvím instalace aplikace, se musí vejít do kvóty vyhrazené pro online aplikace. Navíc síťová aplikace, na kterém běží v částečném vztahu důvěryhodnosti, například s omezenou sadou oprávnění zabezpečení, nemůže být větší než polovina kvóty velikosti.

Další informace a pokyny o tom, jak změnit kvóty aplikace v režimu online, najdete v článku [ClickOnce – Přehled mezipaměti](../deployment/clickonce-cache-overview.md).

## <a name="versioning-issues"></a>Správa verzí – potíže

Pokud vaše sestavení přiřadit silný název a zvýší číslo verze sestavení tak, aby odrážely aktualizace aplikace, může docházet k potížím. Žádné sestavení zkompilovaná odkaz na sestavení se silným názvem musí samotné zopakovat nebo se pokusí o odkaz starší verzi sestavení. Sestavení se pokusí, protože sestavení používá starou hodnotu verze v žádosti o jeho vazby.

Řekněme například, že máte ve svém vlastním projektu verze 1.0.0.0 sestavení se silným názvem. Po kompilaci sestavení, můžete ho přidat jako odkaz na projekt, který obsahuje hlavní aplikace. Pokud zvýšení verze 1.0.0.1 aktualizaci sestavení a zkuste nasazení bez překompilování aplikace, aplikace nebude možné načíst sestavení v době běhu.

Této chybě může dojít pouze v případě, že upravujete vaše [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifesty ručně; tato chyba by nemělo dojít, pokud je generování nasazení pomocí sady Visual Studio.

## <a name="specify-individual-net-framework-assemblies-in-the-manifest"></a>V manifestu zadejte jednotlivá sestavení rozhraní .NET Framework

Vaše aplikace se nepodaří načíst, pokud musíte ručně upravit [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] nasazení tak, aby odkazovaly na starší verzi [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] sestavení. Například, pokud jste přidali odkaz na sestavení System.Net verzi [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] starší než verze určená v manifestu, pak by dojít k chybě. Obecně by se neměly pokoušet zadat odkazy na jednotlivé [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] sestavení jako verze [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] proti které aplikace běží je zadán jako závislost v manifestu aplikace.

## <a name="manifest-parsing-issues"></a>Manifest – potíže analýzy

Soubory manifestů, které jsou používány [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] jsou soubory formátu XML a musí být ve správném formátu a platný: musíte dodržovat pravidla syntaxe jazyka XML a používat pouze elementy a atributy definované v odpovídající schématu XML.

To může způsobit problémy v souboru manifestu je výběr názvu aplikace, který obsahuje speciální znaky, jako je například jednoduchých nebo dvojitých uvozovek. Název aplikace je součástí jeho [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] identity. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aktuálně se nerozloží identity, které obsahují speciální znaky. Pokud se aplikaci nepodaří aktivovat, ujistěte se, že používáte jenom abecední a číselné znaky pro název a pokus o nasaďte jej znovu.

Pokud jste upravili ručně aplikace nebo nasazení manifestů, vám může mít je neúmyslně poškodit. Poškozená manifestu zabrání správné [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] instalace. Tyto chyby můžete ladit v době běhu kliknutím **podrobnosti** na **Chyba ClickOnce** dialogové okno a čtení chybová zpráva v protokolu. Protokol se zobrazí jedna z následujících zpráv:

- Popis chyby syntaxe a číslo řádku a znak pozici, kde došlo k chybě.

- Název elementu nebo atributu použitého v rozporu se schéma manifestu. Pokud jste ručně přidali XML do vaší manifesty, budete muset porovnání dodatky k schémat manifestů. Další informace najdete v tématu [ClickOnce – manifest nasazení](../deployment/clickonce-deployment-manifest.md) a [ClickOnce – manifest aplikace](../deployment/clickonce-application-manifest.md).

- Došlo ke konfliktu ID. Odkazy závislostí v manifesty nasazení a aplikace musí být jedinečný v obou jejich `name` a `publicKeyToken` atributy. Pokud oba atributy odpovídají mezi dva prvky v rámci manifestu, analýza manifestu nebude úspěšný.

## <a name="precautions-when-manually-changing-manifests-or-applications"></a>Bezpečnostní opatření při ruční změna manifesty nebo aplikace

Při aktualizaci manifestu aplikace ji musíte znovu podepsat manifest aplikace a manifest nasazení. Manifest nasazení obsahuje odkaz na manifest aplikace, která obsahuje hodnotu hash pro tento soubor a jeho digitální podpis.

### <a name="precautions-with-deployment-provider-usage"></a>Opatření s využitím poskytovatele nasazení

[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Manifestu nasazení `deploymentProvider` vlastnost, která odkazuje na úplnou cestu k umístění z kde by měl být aplikace nainstalována a údržba:

```xml
<deploymentProvider codebase="http://myserver/myapp.application" />
```

Tato cesta je nastavena, když [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] vytvoří aplikaci a je povinné pro nainstalované aplikace. Cesta odkazuje na standardní umístění ve kterém [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] instalační program nainstaluje aplikaci a vyhledat aktualizace. Pokud používáte **příkazu xcopy** příkaz pro kopírování [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikace do jiného umístění, ale neměňte `deploymentProvider` vlastnost, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] bude stále odkazovat zpět do původního umístění při pokusu o stažení aplikace.

Pokud chcete přesunout nebo kopírovat aplikaci, je nutné také aktualizovat `deploymentProvider` cestu, takže ve skutečnosti instalaci klienta z nové umístění. Aktualizuje se tato cesta je většinou žádný problém, pokud jste nainstalovali aplikace. Pro online aplikace, které jsou vždy spouštěny pomocí původní adresu URL, nastavení `deploymentProvider` je volitelný. Pokud `deploymentProvider` je nastavena, budou zachované; v opačném případě adresy URL pro spuštění aplikace se použije jako základní adresu URL pro stahování souborů aplikace.

> [!NOTE]
> Při každé aktualizaci manifestu je zapotřebí také soubor znovu podepsat.

## <a name="see-also"></a>Viz také:

[Řešení potíží s nasazením ClickOnce](../deployment/troubleshooting-clickonce-deployments.md)  
[Aplikace Securw ClickOnce](../deployment/securing-clickonce-applications.md)  
[Volba strategie nasazení ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)