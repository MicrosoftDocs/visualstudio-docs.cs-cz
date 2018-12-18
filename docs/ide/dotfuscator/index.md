---
title: Dotfuscator Community Edition (CE)
ms.date: 10/10/2017
ms.devlang: dotnet
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
keywords: Nástroj Dotfuscator, řešení Dotfuscator CE, PreEmptive, společnosti PreEmptive Solutions PreEmptive ochrany, ochranu, community edition, obfuskace, .NET, bezplatný, Visual Studio 2017
helpviewer_keywords:
- PreEmptive Protection Dotfuscator
- Dotfuscator Community Edition
- Dotfuscator CE
- Dotfuscator
- obfuscation
- protection
description: Zjistěte, jak můžete ochránit aplikace technologie .NET bezplatný nástroj Dotfuscator Community Edition zahrnuty v sadě Visual Studio 2017.
ms.assetid: d9550502-0a82-49a6-b005-2caa791fbe02
author: Joe-Sewell-PreEmptive
ms.author: gewarren
manager: douge
ms.openlocfilehash: d6cac51aaa73053dc0e1f306288d8198fdacccfd
ms.sourcegitcommit: d462dd10746624ad139f1db04edd501e7737d51e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2018
ms.locfileid: "50219054"
---
# <a name="dotfuscator-community-edition-ce"></a>Dotfuscator Community Edition (CE)

*PreEmptive ochranu – řešení Dotfuscator* poskytuje komplexní ochranu aplikací .NET snadno přizpůsobí do vývojového cyklu zabezpečeného softwaru.
Použijte ho k posílení zabezpečení, ochraně a vyřadit plochy, mobilních, server a vložené aplikace zabezpečené obchodní tajemství a jinému duševnímu (IP), snížit pirátství a padělání a Chraňte se proti manipulaci a neoprávněným ladění.
Nástroj Dotfuscator funguje v kompilovaných sestavení bez potřeby dalšího programování nebo dokonce i přístup ke zdrojovému kódu.

![PreEmptive ochranu – řešení Dotfuscator](media/header.svg)

## <a name="why-protection-matters"></a>Proč na záleží ochrany

Je důležité **chránit duševní vlastnictví** (IP).
Kód vaší aplikace obsahuje návrhu a podrobnosti implementace, které lze považovat za IP.
Ale aplikace založená na rozhraní .NET Framework [významné metadat a základní mezikódu obsahovat][assemblies], provedení je snadné provést zpětnou analýzu, stačí použít jeden z mnoha zdarma, automatizovat nástroje.
Přerušení a zastavení zpětné analýzy vám může zabránit neautorizovaným zveřejněním IP, jakož i prokázat, že váš kód obsahuje tajemství.
Nástroje Dotfuscator můžete [obfuskaci] [ obfuscation] sestavení .NET bránit zpětné analýzy, při zachování původního chování aplikace.

Je také důležité **chrání integritu aplikace**.
Kromě zpětné analýzy můžou snažit nesprávnými účastníky pirate vaší aplikace, měnit chování aplikace za běhu ani manipulaci s daty.
Nástroje Dotfuscator můžete vkládat aplikace možnost [rozpoznání hrozeb a reakce na neoprávněné použití][checks], včetně úmyslné poškozování, ladění třetích stran a zařízením s rootem.

Další informace o jak řešení Dotfuscator zapadá do životního cyklu vývoje zabezpečeného softwaru, najdete v článku společnosti PreEmptive Solutions [SDL App Protection stránky][sdl-protection].

## <a name="about-dotfuscator-ce"></a>Informace o řešení Dotfuscator CE

Vaše kopie sady Microsoft Visual Studio 2017 obsahuje kopii  **_PreEmptive ochranu – řešení Dotfuscator_ Community Edition**, označovaný také jako řešení Dotfuscator CE, která je zdarma pro osobní použití.
Pokyny k instalaci verze řešení Dotfuscator CE je součástí sady Visual Studio 2017 najdete v tématu [stránky instalace][install].

Řešení Dotfuscator CE nabízí celou řadu [ochrany před softwarem a posílení zabezpečení] [ software-protection] služby pro vývojáře, architekty a testery.
Příklady [.NET obfuskace] [ obfuscation] a dalších [Ochrana aplikace] [ app-protection] jsou funkce obsažené v nástroji Dotfuscator CE:

* *[Přejmenování] [ renaming]*  identifikátorů, které mají ztížit zpětnou zkompilovaného sestavení.
* *[Boj proti] [ tamper]*  k detekci spuštění zmanipulovanou aplikací a ukončit nebo v reakci na manipulováno relace.
* *[Ladění proti] [ debug]*  -li zjistit přílohy ladicího programu k běžící aplikaci a ukončit nebo reakce na ladit relace.
* *[Zařízení s rootem proti] [ root]*  -li zjistit, pokud aplikace běží na rootovaném zařízení s Androidem a ukončit nebo reakce na relace na těchto zařízeních.
* *[Chování vypršení platnosti aplikací] [ shelflife]*  , který kódování datem "ukončení životnosti technologie" a ukončí aplikaci vypršela platnost relace.

Podrobnosti o těchto funkcích, včetně toho, jak se vešly do strategie ochrany aplikací najdete v tématu [stránka schopnosti][capabilities].

Řešení Dotfuscator CE nabízí základní ochranu out-of-the-box.
Ještě více opatření na ochranu aplikací jsou k dispozici pro registrovaného uživatele řešení Dotfuscator CE a uživatelům *PreEmptive ochranu – řešení Dotfuscator* Professional Edition na světě je vedoucí [.NET Obfuskátor] [net-obfuscator].
Informace o rozšíření Dotfuscator, najdete v článku [stránce upgrady][upgrades].

## <a name="getting-started"></a>Začínáme

Chcete-li začít používat řešení Dotfuscator CE ze sady Visual Studio, zadejte `dotfuscator` do **Snadné spuštění** panelu hledání (Ctrl + Q).

* Pokud řešení Dotfuscator CE je už nainstalovaný, **Snadné spuštění** vyvolá *nabídky* možnosti spuštění uživatelského rozhraní nástroje Dotfuscator CE. Podrobnosti najdete v tématu [stránku Začínáme úplné řešení Dotfuscator CE uživatelské příručce nástroje][get-started].
* Pokud ještě není nainstalovaná řešení Dotfuscator CE, **Snadné spuštění** zobrazí příslušné *nainstalovat* možnost. Zobrazit [stránky instalace] [ install] podrobnosti.

Můžete získat také **nejnovější verzi** z řešení Dotfuscator CE z [stránce soubory ke stažení nástroje Dotfuscator preemptive.com][download].

## <a name="full-documentation"></a>Úplnou dokumentaci

Na této stránce a její podstránky poskytují přehled funkce řešení Dotfuscator CE, stejně jako [pokyny k instalaci nástroje][install].

V tématu [úplného Průvodce uživatele řešení Dotfuscator CE na preemptive.com] [ full] podrobné pokyny k použití, včetně [spuštění pomocí uživatelského rozhraní nástroje Dotfuscator CE] [ get-started].

<!-- Copyright © 2017 PreEmptive Solutions, LLC -->

[assemblies]:  https://docs.microsoft.com/dotnet/standard/assembly-format
[software-protection]:  https://www.preemptive.com/software-protection
[obfuscation]:  https://www.preemptive.com/obfuscation
[app-protection]:  https://www.preemptive.com/application-protection
[sdl-protection]:  https://www.preemptive.com/solutions/SDL-App-Protection
[net-obfuscator]:  https://www.preemptive.com/products/dotfuscator/overview
[download]:  https://www.preemptive.com/products/dotfuscator/downloads

[install]:  install.md
[capabilities]:  capabilities.md
[upgrades]:  upgrades.md

[get-started]:  https://www.preemptive.com/dotfuscator/ce/docs/help/gui_getstarted.html

[renaming]:  https://www.preemptive.com/dotfuscator/ce/docs/help/obfuscation_renaming.html

[checks]:  https://www.preemptive.com/dotfuscator/ce/docs/help/checks_overview.html
[tamper]:  https://www.preemptive.com/dotfuscator/ce/docs/help/checks_tamper.html
[debug]:  https://www.preemptive.com/dotfuscator/ce/docs/help/checks_debug.html
[root]: https://www.preemptive.com/dotfuscator/ce/docs/help/checks_root.html
[shelflife]:  https://www.preemptive.com/dotfuscator/ce/docs/help/checks_shelflife.html

[full]:  https://www.preemptive.com/dotfuscator/ce/docs/help/index.html
