---
title: Problémy se zabezpečením, správou verzí a manifestem v nasazeních ClickOnce | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
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
ms.assetid: d5d0c90b-ac1a-44e2-88dc-0d0ffd881624
caps.latest.revision: 23
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a4864d37cb5930075b292ee765bce9b288794019
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64799227"
---
# <a name="security-versioning-and-manifest-issues-in-clickonce-deployments"></a>Problémy se zabezpečením, správou verzí a manifestem v nasazeních ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Existuje řada problémů se [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] zabezpečením, správou verzí aplikací a syntaxí manifestu a sémantikou, které můžou způsobit, že [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] nasazení nebude úspěšné.  
  
## <a name="clickonce-and-windows-vista-user-account-control"></a>Technologie ClickOnce a řízení uživatelských účtů v systému Windows Vista  
 V aplikaci [!INCLUDE[windowsver](../includes/windowsver-md.md)] se aplikace ve výchozím nastavení spouštějí jako standardní uživatel, a to i v případě, že je aktuální uživatel přihlášený pomocí účtu, který má oprávnění správce. Pokud aplikace musí provést akci, která vyžaduje oprávnění správce, sdělí operačnímu systému, který pak vyzve uživatele k zadání přihlašovacích údajů správce. Tato funkce, která se nazývá řízení uživatelských účtů (UAC), zabraňuje aplikacím v provádění změn, které mohou ovlivnit celý operační systém bez explicitního schválení uživatele. Aplikace systému Windows deklarují, že vyžadují toto zvýšení oprávnění zadáním `requestedExecutionLevel` atributu v `trustInfo` části jeho manifestu aplikace.  
  
 Z důvodu rizika vystavení aplikací útokům na zvýšení zabezpečení [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] nemůžou aplikace požádat o zvýšení oprávnění, pokud je pro klienta povolený nástroj řízení uživatelských účtů. Všechny [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikace, které se pokusí nastavit svůj `requestedExecutionLevel` atribut na `requireAdministrator` nebo `highestAvailable` nebudou nainstalovány v [!INCLUDE[windowsver](../includes/windowsver-md.md)] .  
  
 V některých případech se vaše [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikace může pokusit spustit s oprávněními správce z důvodu logiky zjišťování instalační služby [!INCLUDE[windowsver](../includes/windowsver-md.md)] . V takovém případě můžete nastavit `requestedExecutionLevel` atribut v manifestu aplikace na `asInvoker` . Tato akce způsobí, že aplikace bude spuštěna bez zvýšení oprávnění. [!INCLUDE[vs_orcas_long](../includes/vs-orcas-long-md.md)] automaticky přidá tento atribut do všech manifestů aplikace.  
  
 Pokud vyvíjíte aplikaci, která vyžaduje oprávnění správce pro celou dobu životnosti aplikace, měli byste zvážit nasazení aplikace pomocí technologie Instalační služba systému Windows (MSI). Další informace najdete v tématu [základy Instalační služba systému Windows](../extensibility/internals/windows-installer-basics.md).  
  
## <a name="online-application-quotas-and-partial-trust-applications"></a>Online kvóty aplikací a aplikace s částečným vztahem důvěryhodnosti  
 Pokud vaše [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikace běží v online režimu, a ne prostřednictvím instalace, musí se přizpůsobit kvótě nastavené pro online aplikace. Také síťová aplikace, která běží v částečném vztahu důvěryhodnosti, například s omezenou sadou oprávnění zabezpečení, nemůže být větší než polovina velikosti kvóty.  
  
 Další informace a pokyny, jak změnit kvótu online aplikace, najdete v tématu [Přehled mezipaměti ClickOnce](../deployment/clickonce-cache-overview.md).  
  
## <a name="versioning-issues"></a>Problémy se správou verzí  
 Při přiřazování silných názvů sestavení a zvýšení čísla verze sestavení tak, aby odráželo aktualizaci aplikace, může docházet k problémům. Jakékoli sestavení zkompilované s odkazem na sestavení se silným názvem musí být znovu zkompilováno, jinak se sestavení pokusí odkazovat na starší verzi. Sestavení se to pokusí, protože sestavení používá starou hodnotu verze v žádosti o vytvoření vazby.  
  
 Řekněme například, že máte sestavení se silným názvem ve svém vlastním projektu s verzí 1.0.0.0. Po zkompilování sestavení ho přidáte jako odkaz na projekt, který obsahuje vaši hlavní aplikaci. Pokud aktualizujete sestavení, zvýšíte verzi na 1.0.0.1 a pokusíte se ji nasadit bez opětovné kompilace aplikace, aplikace nebude moci načíst sestavení v době běhu.  
  
 K této chybě může dojít pouze v případě, že upravujete [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] manifesty ručně. tuto chybu byste neměli mít při generování nasazení pomocí [!INCLUDE[vsprvslong](../includes/vsprvslong-md.md)] .  
  
## <a name="specifying-individual-net-framework-assemblies-in-the-manifest"></a>Určení jednotlivých sestavení .NET Framework v manifestu  
 Pokud jste nastavili ruční úpravu [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] nasazení tak, aby odkazovalo na starší verzi sestavení, vaše aplikace se nepodaří načíst [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] . Například pokud jste přidali odkaz na sestavení System.Net pro verzi [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] před verzí určenou v manifestu, pak dojde k chybě. Obecně byste neměli zkoušet odkazy na jednotlivá [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] sestavení, protože verze, [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] oproti které vaše aplikace běží, je zadána jako závislost v manifestu aplikace.  
  
## <a name="manifest-parsing-issues"></a>Problémy s analýzou manifestu  
 Soubory manifestu používané nástrojem [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] jsou soubory XML a musí být ve správném formátu a platné: musí dodržovat pravidla syntaxe XML a používat pouze prvky a atributy definované v příslušném schématu XML.  
  
 Něco, co může způsobit problémy v souboru manifestu, je výběr názvu vaší aplikace, který obsahuje speciální znak, jako je například jednoduchá nebo dvojitá uvozovka. Název aplikace je součástí své [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] identity. [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] v současné době neanalyzuje identity, které obsahují speciální znaky. Pokud se vaší aplikaci nepovede aktivovat, ujistěte se, že pro název používáte jenom abecední a číselné znaky a pokusíte se ho znovu nasadit.  
  
 Pokud jste ručně upravili manifesty nasazení nebo aplikace, můžete je neúmyslně poškodit. Poškozený manifest zabrání správné [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] instalaci. Tyto chyby můžete za běhu ladit kliknutím na **Podrobnosti** v dialogovém okně **Chyba ClickOnce** a načtením chybové zprávy v protokolu. Protokol bude zobrazovat jednu z následujících zpráv:  
  
- Popis chyby syntaxe a číslo řádku a pozice znaku, kde došlo k chybě.  
  
- Název elementu nebo atributu použitý při porušení schématu manifestu. Pokud jste do svých manifestů přidali XML ručně, budete muset porovnat vaše dodatky se schématy manifestu. Další informace naleznete v tématu [manifest nasazení ClickOnce](../deployment/clickonce-deployment-manifest.md) a [manifest aplikace ClickOnce](../deployment/clickonce-application-manifest.md).  
  
- Konflikt ID. Odkazy na závislosti v manifestech nasazení a aplikací musí být jedinečné v jejich `name` `publicKeyToken` atributů i. Pokud oba atributy odpovídají všem dvěma prvkům v rámci manifestu, analýza manifestu nebude úspěšná.  
  
## <a name="precautions-when-manually-changing-manifests-or-applications"></a>Opatření při ruční změně manifestů nebo aplikací  
 Když aktualizujete manifest aplikace, musíte znovu podepsat manifest aplikace i manifest nasazení. Manifest nasazení obsahuje odkaz na manifest aplikace, který obsahuje hodnotu hash tohoto souboru a jeho digitální podpis.  
  
### <a name="precautions-with-deployment-provider-usage"></a>Opatření při použití poskytovatele nasazení  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]Manifest nasazení má `deploymentProvider` vlastnost, která odkazuje na úplnou cestu k umístění, ze kterého by měla být aplikace nainstalovaná a obsluhovaná:  
  
```  
<deploymentProvider codebase="http://myserver/myapp.application" />  
```  
  
 Tato cesta je nastavena při [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] vytváření aplikace a je povinná pro nainstalované aplikace. Cesta odkazuje na standardní umístění, ve kterém [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] instalační program nainstaluje aplikaci a bude vyhledávat aktualizace. Použijete-li příkaz **xcopy** ke zkopírování [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikace do jiného umístění, ale vlastnost nezměníte `deploymentProvider` , [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] bude se při pokusu o stažení aplikace stále odkazovat na původní umístění.  
  
 Pokud chcete aplikaci přesunout nebo zkopírovat, je nutné také aktualizovat `deploymentProvider` cestu, aby se klient skutečně nainstaloval z nového umístění. Aktualizace této cesty se většinou týká, pokud máte nainstalované aplikace. V případě online aplikací, které jsou vždy spouštěny prostřednictvím původní adresy URL, `deploymentProvider` je nastavení volitelné. Pokud `deploymentProvider` je nastavena, bude dodržena. v opačném případě bude adresa URL použitá ke spuštění aplikace použita jako základní adresa URL pro stahování souborů aplikace.  
  
> [!NOTE]
> Pokaždé, když aktualizujete manifest, musíte ho také znovu podepsat.  
  
## <a name="see-also"></a>Viz také  
 [Řešení potíží s nasazením ClickOnce](../deployment/troubleshooting-clickonce-deployments.md)   
 [Zabezpečení aplikací ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Výběr strategie nasazení ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)
