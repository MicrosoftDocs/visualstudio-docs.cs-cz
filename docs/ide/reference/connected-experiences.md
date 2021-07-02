---
title: Propojená prostředí v Visual Studio
description: Připojené prostředí se připojuje k internetu z klientského počítače a poskytuje službu zákazníkovi.
ms.date: 05/20/2021
ms.topic: conceptual
helpviewer_keywords: ''
author: SayyedaM
ms.author: sayyedamussa
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.openlocfilehash: 689fc40be8aee959023777a3fac6d9134ee979ea
ms.sourcegitcommit: 8b75524dc544e34d09ef428c3ebbc9b09f14982d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/02/2021
ms.locfileid: "113222887"
---
# <a name="connected-experiences-in-visual-studio"></a>**Propojená prostředí v Visual Studio** #

Visual Studio se skládá z klientských softwarových aplikací a propojených prostředí navržených tak, aby vám umožnily kódovat efektivněji. Příkladem [propojených NuGet](/nuget/consume-packages/install-use-packages-visual-studio) je aktualizace balíčku Live Share, výběr návrhu [IntelliCode](/visualstudio/intellicode/overview) a spolupráce s jiným vývojářem prostřednictvím [Live Share](/visualstudio/liveshare/quickstart/share) prostředí. 

## <a name="choose-whether-these-connected-experiences-are-available-to-use"></a>Vyberte, jestli jsou tato propojená prostředí dostupná k použití. ##

Můžete si vybrat, která propojená prostředí se mají použít. Použití určitých propojených prostředí vyžaduje smlouvu s různými a dalšími podmínkami smlouvy EULA Visual Studio smlouvy EULA. Tato prostředí mohou být vlastněná Microsoftem online služby a/nebo služby vlastněné třetími stranami. Pokud například používáte prostředí připojená k GitHub, budou platit prohlášení [o](https://docs.github.com/github/site-policy/github-privacy-statement) zásadách ochrany osobních údajů GitHub a podmínky služby [](https://docs.github.com/github/site-policy/github-additional-product-terms) [GitHub](https://docs.github.com/github/site-policy/github-terms-of-service), [firemní](https://docs.github.com/github/site-policy/github-corporate-terms-of-service)podmínky služby GitHub/nebo další podmínky produktu. Pokud [nahlasíte problém,](/visualstudio/ide/how-to-report-a-problem-with-visual-studio)souhlasíte s [podmínkami](https://www.microsoft.com/legal/terms-of-use) použití společnosti Microsoft a [prohlášením o zásadách ochrany osobních údajů společnosti Microsoft.](https://privacy.microsoft.com/en-us/privacystatement) Pokud používáte službu NuGet, souhlasíte s NuGet [podmínek použití](https://www.nuget.org/policies/Terms) a Prohlášením o zásadách [ochrany osobních údajů společnosti Microsoft.](https://privacy.microsoft.com/en-us/privacystatement) 

Při instalaci Visual Studio můžete volitelně vybrat úlohy a [komponenty, které chcete nainstalovat.](/visualstudio/install/install-visual-studio) Úlohy a komponenty mohou využívat software třetích stran a v závislosti na jejich funkcích mohou povolit propojená prostředí. Například stažení [úlohy Vývoj pro Azure umožňuje publikovat cloudové aplikace do Azure.](https://visualstudio.microsoft.com/vs/features/azure/) Na základě vašeho výběru instalace můžete také použít nabídku Nástroje a možnosti pro připojení, konfiguraci a používání propojených prostředí. Můžete se například připojit k serveru, přidat ověřování služeb Azure nebo změnit nastavení IntelliCode nebo LiveShare.  

Můžete také použít nastavení brány firewall vaší [organizace a](/visualstudio/install/install-and-use-visual-studio-behind-a-firewall-or-proxy-server) povolit nebo zakázat připojení ke službám. Upozorňujeme, že zakázání připojení ke koncovému bodu může negativně ovlivnit nebo zakázat výkon souvisejících Visual Studio funkcí. 

A konečně, Visual Studio Marketplace nabízí rozšíření, která mohou umožnit prostředí připojená k prvním nebo třetím stranám. Visual Studio Na Marketplace se vztahují podmínky [použití Visual Studio Marketplace](https://cdn.vsassets.io/v/M146_20190123.39/_content/Microsoft-Visual-Studio-Marketplace-Terms-of-Use.pdf) a Prohlášení o zásadách ochrany [osobních údajů společnosti Microsoft.](https://privacy.microsoft.com/en-us/privacystatement) Každé rozšíření vyžaduje smlouvu s konkrétními podmínkami použití a prohlášením o zásadách ochrany osobních údajů, které jsou s těmito nabídkami spojené.  


## <a name="required-service-data"></a>Požadovaná data služby ##

Požadovaná data služby mohou zahrnovat informace související s provozem propojeného prostředí, které je potřeba k zajištění zabezpečení, aktualizace a výkonu podkladové služby podle očekávání. Pokud se rozhodnete použít připojené prostředí, které analyzuje váš obsah, například IntelliCode, kód, který jste pro model vybrali, se také odesílá a zpracovává, aby vám poskytl prostředí pro připojení. Požadovaná data služby mohou také zahrnovat informace potřebné připojeným prostředím k provedení své úlohy, jako je aktualizace NuGet balíčku. Požadovaná data služby můžete spravovat tak, že zvolíte, jestli se má konkrétní služba používat. Pokud službu nevyubíráte, neshromaždí se žádná požadovaná data služby. 

Požadovaná data služby se liší od diagnostických dat, protože diagnostická data se týkají softwaru spuštěného na vašem zařízení. Volba, jestli se chcete zapojit do programu [Visual Studio program Zlepšování softwaru a služeb na základě zkušeností uživatelů (VSCEIP),](/visualstudio/ide/visual-studio-experience-improvement-program)řídí nastavení ochrany osobních údajů pro diagnostická data, ale toto nastavení nemá vliv na to, jestli se mají požadovaná data služby odeslat. 

## <a name="diagnostic-data-collection"></a>Shromažďování diagnostických dat ##

Diagnostická data se používají Visual Studio zabezpečení a aktualizace, detekci, diagnostice a opravě problémů a také k vylepšování produktu. Diagnostická data jsou shromažďována a odesílána společnosti Microsoft Visual Studio klientský software spuštěný na zařízení uživatele.

Když se odhlásit, odhlásit se z volitelného shromažďování diagnostických dat. Některé shromažďování diagnostických dat je nutné k tomu, Visual Studio jsou zabezpečená, aktuální a výkonná podle očekávání. Vyžadované shromažďování diagnostických dat nebude vaší volbou ovlivněno tím, že se z [VSCEIP odsoudíte.](/visualstudio/ide/visual-studio-experience-improvement-program) 
