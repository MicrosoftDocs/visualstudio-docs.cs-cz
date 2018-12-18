---
title: Upgrade řešení Dotfuscator Community Edition (CE)
ms.date: 02/08/2017
ms.devlang: dotnet
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
keywords: Nástroj Dotfuscator, řešení Dotfuscator CE, PreEmptive, společnosti PreEmptive Solutions PreEmptive ochrany, ochranu, community edition, obfuskace, .NET, bezplatný, upgradu, příkazový řádek sady Visual Studio 2017
helpviewer_keywords:
- PreEmptive Protection Dotfuscator
- Dotfuscator Community Edition
- Dotfuscator CE
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
description: Zjistěte, jak upgradovat bezplatný nástroj Dotfuscator Community Edition zahrnuty v sadě Visual Studio 2017.
ms.assetid: c7c60904-27f9-4f1f-b79b-ddf65041b810
author: Joe-Sewell-PreEmptive
ms.author: gewarren
manager: douge
ms.openlocfilehash: f1158b0e5f438e49acafad79af1b33ec43690e9a
ms.sourcegitcommit: 0cf1e63b6e0e6a0130668278489b21a6e5038084
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/02/2018
ms.locfileid: "39468540"
---
# <a name="upgrade-dotfuscator-community-edition-ce"></a>Upgrade řešení Dotfuscator Community Edition (CE)

Nástroj Dotfuscator Community Edition (řešení Dotfuscator CE) nabízí mnoho Ochrana aplikace a funkce pro posílení zabezpečení okamžitě pro všechny vývojáře, kteří používají Microsoft Visual Studio.
Existují však další funkce dostupné pro uživatele, kteří upgrade řešení dotfuscator jejich verze.

## <a name="registering-dotfuscator-ce"></a>Registrace Nástroje Dotfuscator CE

Registrovaných uživatelů řešení Dotfuscator CE získat přístup k dalším funkcím, jako například [podpory příkazového řádku][cli], což usnadňuje integraci řešení Dotfuscator CE do procesu automatizované sestavování. Registrace také uděluje přístup k Lucidator, integrované nástroj používaný pro [dekódování trasování zásobníku obfuskovaný][decode-obfuscated].

Registrace je rychlé, jednoduché a zadarmo.
Registrace Nástroje Dotfuscator CE, naleznete v tématu [registrace Nástroje Dotfuscator CE části na stránce Začínáme úplné uživatelské příručce nástroje Dotfuscator CE][register-ce].

## <a name="dotfuscator-professional"></a>Nástroje Dotfuscator Professional

Nástroj Dotfuscator Community Edition poskytuje základní úroveň ochrany,  **_PreEmptive ochranu – řešení Dotfuscator_ Professional Edition** zahrnuje vylepšené obfuskace transformace a ochrana Možnosti. Vylepšené transformace a možnosti patří:

* *Ochranu duševního vlastnictví*
  * Další možnosti, včetně Enhanced Overload Induction™ a výběru náhodného identifikátor přejmenování.
  * Nástroje pro dekódování obfuskovaný trasování zásobníku.
  * Přístup k podnikové úrovni obfuskace transformací, včetně [transformace zaměřený na vytvoříte automatizované kód dekompilace][control-flow].
  * Schopnost [skryl citlivé řetězce][string-encryption], provádění možné jednoduché hledání dekompilované kódu.
  * Schopnost [diskrétní vlastnictví a distribuci řetězce vložení do sestavení][watermarking], umožňuje určit příčiny Neautorizováno nevracení softwaru.
  * Schopnost [kombinovat více sestavení do jednoho][linking], znesnadňuje i pro útočníky k určení rolí prvků kódu, protože byly odstraněny oddělení oblastí zájmu.
  * Schopnost [automaticky odebrat nepoužitý kód ze své aplikace][pruning], čímž snižuje velikost citlivé kód, který je dodáván.
* *Ochrana Integrity aplikace*
  * Další [chování aplikací defense][check-actions].
  * Schopnost poskytnout určité upozornění před konečným termínem ukončenou životností aplikace.
  * Možnost oznámit kód aplikace během období upozornění ukončenou životností nebo po konečném termínu.

Nástroje Dotfuscator Professional je standardní průmyslový [.NET Obfuskátor] [ net-obfuscator] a je vhodný pro podnikové vývojáře vyžadující probíhajících aktualizacích fungovat podporu, údržby a produktu.
Kromě toho nástroje Dotfuscator Professional nabízí užší integraci s Visual Studio a má licenci pro obchodní použití.

Další informace o funkcích pokročilé aplikace ochrany nástroje Dotfuscator Professional, najdete na webu společnosti PreEmptive Solutions [stránka s přehledem nástroje Dotfuscator] [ product-about] a [porovnat s Edice Community][product-compare].
[Plně podporované zkušební verze najdete na adrese preemptive.com][eval].

## <a name="see-also"></a>Viz také

[Tento článek v uživatelské příručce nástroje úplné řešení Dotfuscator CE][full]

<!-- Copyright © 2017 PreEmptive Solutions, LLC -->

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