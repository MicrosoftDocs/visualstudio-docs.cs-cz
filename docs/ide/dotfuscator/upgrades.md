---
title: Upgrade Dotfuscatoru Community
ms.date: 03/28/2019
ms.devlang: dotnet
ms.topic: conceptual
keywords: Dotfuscator, Dotfuscator Community, Dotfuscator CE, PreEmptive, PreEmptive Solutions, PreEmptive Protection, Protection, Community Edition, obfuscation, .NET, free, Visual Studio 2019, Visual Studio 2017, Visual Studio, upgrade, příkazový řádek
helpviewer_keywords:
- PreEmptive Protection Dotfuscator
- Dotfuscator Community Edition
- Dotfuscator CE
- Dotfuscator Community
- Dotfuscator
- obfuscation
- protection
- Dotfuscator upgrade
- upgrade Dotfuscator
- upgrading Dotfuscator
- register Dotfuscator
- registering Dotfuscator
- Dotfuscator command line
- Dotfuscator Professional
description: Přečtěte si, jak upgradovat bezplatnou kopii komunity Dotfuscator, která je součástí sady Visual Studio.
ms.assetid: c7c60904-27f9-4f1f-b79b-ddf65041b810
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 08492340022f772beadca8061a216de69fafc8af
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75596798"
---
# <a name="upgrade-dotfuscator-community"></a>Upgrade Dotfuscatoru Community

Dotfuscator Community nabízí mnoho funkcí ochrany aplikací a posílení zabezpečení okamžitě všem vývojářům pomocí sady Microsoft Visual Studio.
Nicméně, existuje více funkcí k dispozici uživatelům, kteří inovovat jejich verzi Dotfuscator.

## <a name="registering-dotfuscator-community"></a>Registrace Dotfuscator Společenství

Registrovaní uživatelé komunity Dotfuscator získají přístup k dalším funkcím, jako je [podpora příkazového řádku][cli], což usnadňuje integraci komunity Dotfuscator do automatizovaného procesu sestavení. Registrace také uděluje přístup k integrovanému nástroji používanému k [dekódování zamlžených trasování zásobníku][decode-obfuscated].

Registrace je rychlá, jednoduchá a bezplatná.
Chcete-li zaregistrovat Komunitu dotfuscatorů, přečtěte si [pokyny v úplné uživatelské příručce komunity Dotfuscator][register-ce].

## <a name="dotfuscator-professional"></a>Dotfuscator Profesionální

Zatímco Dotfuscator Community poskytuje základní úroveň ochrany, ***PreEmptivní ochrana - Dotfuscator Professional*** zahrnuje vylepšené transformace obfuskace a ochranné schopnosti, jako jsou:

* *Ochrana duševního vlastnictví*
  * Další možnosti přejmenování, včetně rozšířené hodování indukcí ™ a výběru randomizovaného identifikátoru.
  * Přístup k transformace miny na podnikové úrovni, včetně [transformací zaměřených na poražení automatické dekompilace kódu][control-flow].
  * Schopnost [zakrývat citlivé řetězce][string-encryption], takže jednoduché hledání dekompilovaného kódu nemožné.
  * Možnost [diskrétně vložit vlastnictví a distribuční řetězce do sestavení][watermarking], což vám umožní určit zdroj neoprávněných úniků softwaru.
  * Schopnost [kombinovat více sestavení do jednoho][linking], takže je ještě obtížnější pro útočníky určit role prvků kódu, jako oddělení obavy byla odstraněna.
  * Možnost [automaticky odebrat nepoužitý kód z aplikace][pruning], snížení množství citlivého kódu, který je dodáván.
* *Ochrana integrity aplikace*
  * Další [chování obrany aplikace][check-actions].
  * Možnost poskytnout varovnou lhůtu před termínem ukončení životnosti aplikace.
  * Možnost upozornit kód aplikace během období varování na konci životnosti nebo po uplynutí lhůty.

Dotfuscator Professional je průmyslový standard [.NET Obfuscator][net-obfuscator] a je vhodný pro podnikové vývojáře, kteří vyžadují průběžnou podporu, údržbu a aktualizace produktů.
Kromě toho Dotfuscator Professional nabízí užší integraci s Visual Studio a je licencován pro komerční použití.

Další informace o pokročilých funkcích ochrany aplikací dotfuscator professional naleznete na [stránce Přehled dotfuscatoru][product-about] preemptivních řešení a [porovnejte ji s komunitou Dotfuscator][product-compare].
[Plně podporované zkoušky jsou k dispozici na preemptive.com][eval].

## <a name="see-also"></a>Viz také

[Tento článek v úplné uživatelské příručce komunity Dotfuscator][full]

<!-- Copyright © 2019 PreEmptive Solutions, LLC -->

[control-flow]:  https://www.preemptive.com/products/dotfuscator/features#controlflow
[string-encryption]:  https://www.preemptive.com/products/dotfuscator/features#string
[watermarking]:  https://www.preemptive.com/products/dotfuscator/features#watermarking
[linking]:  https://www.preemptive.com/products/dotfuscator/features#linking
[pruning]:  https://www.preemptive.com/products/dotfuscator/features#pruning

[check-actions]:  https://www.preemptive.com/dotfuscator/pro/userguide/en/protection_checks_overview.html#actions

[net-obfuscator]:  https://www.preemptive.com/products/dotfuscator/overview
[eval]:  https://www.preemptive.com/eval-request

[product-about]:  https://www.preemptive.com/products/dotfuscator/overview
[product-compare]:  https://www.preemptive.com/products/dotfuscator/compare-editions

[cli]:  https://www.preemptive.com/dotfuscator/ce/docs/help/intro_cli.html
[register-ce]:  https://www.preemptive.com/dotfuscator/ce/docs/help/gui_getstarted.html#register

[full]:  https://www.preemptive.com/dotfuscator/ce/docs/help/intro_upgrades.html
[decode-obfuscated]:  https://www.preemptive.com/dotfuscator/ce/docs/help/gui_decode_stack_trace.html
