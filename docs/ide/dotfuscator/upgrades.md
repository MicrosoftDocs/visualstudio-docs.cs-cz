---
title: Upgrade Dotfuscatoru Community
ms.date: 03/28/2019
ms.devlang: dotnet
ms.topic: conceptual
keywords: Dotfuscator, Dotfuscator Community, Dotfuscator CE, nepřesné, bezplatná řešení, bezplatná ochrana, ochrana, komunita Edition, zmatene, .NET, free, Visual Studio 2019, Visual Studio 2017, Visual Studio, upgrade, příkazový řádek
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
description: Naučte se upgradovat bezplatnou kopii Dotfuscator komunity zahrnutou v aplikaci Visual Studio.
ms.assetid: c7c60904-27f9-4f1f-b79b-ddf65041b810
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.openlocfilehash: a0e3ad3e5f6afbd6675f8e65c918b4a5d7c66dd8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99922774"
---
# <a name="upgrade-dotfuscator-community"></a>Upgrade Dotfuscatoru Community

Komunita Dotfuscator nabízí všem vývojářům, kteří používají Microsoft Visual Studio, mnoho funkcí ochrany aplikací a posílení zabezpečení hned.
Pro uživatele, kteří upgradují svou verzi Dotfuscator, je však k dispozici více funkcí.

## <a name="registering-dotfuscator-community"></a>Registrace komunity Dotfuscator

Registrovaní uživatelé komunity Dotfuscator získají přístup k dalším funkcím, jako je [Podpora příkazového řádku][cli], což usnadňuje integraci Dotfuscator komunity do procesu automatizovaného sestavení. Registrace také uděluje přístup k integrovanému nástroji použitému k [dekódování zakódovaných trasování zásobníku][decode-obfuscated].

Registrace je rychlá, jednoduchá a bezplatná.
Pokud chcete zaregistrovat komunitu Dotfuscator, přečtěte si [pokyny v tématu úplná Dotfuscator uživatelská příručka komunity][register-ce].

## <a name="dotfuscator-professional"></a>Dotfuscator Professional

I když komunita Dotfuscator poskytuje základní úroveň ochrany, bezkontaktní ***ochrana – Dotfuscator Professional*** zahrnuje vylepšené transformace a možnosti ochrany, jako například:

* *Ochrana duševního vlastnictví*
  * Další možnosti přejmenování, včetně rozšířených srážek přetížení™ a náhodného výběru identifikátorů.
  * Přístup k transformačním transformacím na podnikové úrovni, včetně [transformací cílených na zpracování automatizované dekompilace kódu][control-flow].
  * Možnost [zakrýt citlivé řetězce][string-encryption], což znemožňuje jednoduché hledání dekompilovaného kódu.
  * Možnost [discreetly vkládat vlastnictví a distribuční řetězce do sestavení][watermarking], což vám umožní určit zdroj neautorizovaných úniků softwaru.
  * Možnost [zkombinovat více sestavení do jednoho][linking], což je ještě obtížnější pro útočníky, aby určili role prvků kódu, protože oddělení obav bylo eliminováno.
  * Možnost [automaticky odebrat nepoužitý kód z aplikace][pruning]a snížit množství citlivého kódu, který je dodán.
* *Ochrana integrity aplikací*
  * Další [chování ochrany aplikace][check-actions].
  * Možnost poskytnout období upozornění před konečným termínem ukončení platnosti aplikace.
  * Možnost upozornění kódu aplikace v průběhu období upozornění na ukončení životnosti nebo po termínu.

Dotfuscator Professional je průmyslový standard [.NET][net-obfuscator] , který je vhodný pro podnikové vývojáře, který vyžaduje průběžnou podporu, údržbu a aktualizace produktů.
Dotfuscator Professional navíc nabízí úzkou integraci se sadou Visual Studio a má licenci pro komerční použití.

Další informace o pokročilých funkcích ochrany aplikací v Dotfuscator Professional najdete na [stránce Přehled][product-about] řešení s možnostmi Dotfuscator a [porovnejte je s komunitou Dotfuscator][product-compare].
[Plně podporované zkušební verze jsou k dispozici na adrese PreEmptive.com][eval].

## <a name="see-also"></a>Viz také

[Tento článek v úplné příručce pro uživatele komunity Dotfuscator][full]

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
