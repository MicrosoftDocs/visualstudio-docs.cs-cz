---
title: Dotfuscator Community
ms.date: 03/28/2019
ms.devlang: dotnet
ms.topic: conceptual
keywords: Dotfuscator, Dotfuscator CE, Dotfuscator Community, bezplatná, bezplatná řešení, bezplatná ochrana, ochrana, Community Edition, zmatene, .NET, free, Visual Studio 2019, Visual Studio 2017, Visual Studio
helpviewer_keywords:
- PreEmptive Protection Dotfuscator
- Dotfuscator Community Edition
- Dotfuscator CE
- Dotfuscator Community
- Dotfuscator
- obfuscation
- protection
description: Seznamte se s tím, jak můžete chránit aplikace .NET pomocí bezplatné kopie komunity Dotfuscator, která je součástí sady Visual Studio.
ms.assetid: d9550502-0a82-49a6-b005-2caa791fbe02
author: Joe-Sewell-PreEmptive
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 53bd95875cf990afee6d356744961d3637f16842
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2019
ms.locfileid: "71253772"
---
# <a name="dotfuscator-community"></a>Dotfuscator Community

Bezstavová ***ochrana – Dotfuscator*** poskytuje komplexní ochranu aplikací .NET, kterou snadno zapadá do životního cyklu bezpečného vývojového softwaru.
Použijte ho k posílení, ochraně a vyřazení aplikací pro stolní počítače, mobilní zařízení, servery a aplikace, které vám pomůžou zabezpečit obchodní tajemství a jiné duševní vlastnictví (IP), omezit pirátství a padělání a chránit před manipulací a neoprávněným laděním.
Dotfuscator pracuje na kompilovaných sestaveních, aniž by bylo nutné další programování nebo dokonce přístup ke zdrojovému kódu.

![PreEmptive ochranu – řešení Dotfuscator](media/header.svg)

## <a name="why-protection-matters"></a>Proč v oblasti ochrany

Je důležité **chránit duševní** vlastnictví (IP).
Kód vaší aplikace obsahuje podrobnosti návrhu a implementace, které lze považovat za IP adresu.
Aplikace založené na .NET Framework však [obsahují významné metadata a průběžný kód vysoké úrovně][assemblies], což usnadňuje zpětnou analýzu, a to pouze pomocí jednoho z mnoha bezplatných automatizovaných nástrojů.
Přerušením a zastavením zpětného řízení můžete zabránit neoprávněnému zpřístupnění IP adresy a také prokázat, že váš kód obsahuje obchodní tajemství.
Dotfuscator může [Zaměnit vaše sestavení][obfuscation] .NET, aby bránila zpětnému strojírenství, a přitom zachovala chování původní aplikace.

Je také důležité **chránit integritu aplikace**.
Kromě zpětného strojírenství se mohou špatné aktéry pokusit o nedovolenou aplikaci, měnit chování aplikace za běhu nebo manipulovat s daty.
Dotfuscator může vložit vaši aplikaci s možností [rozpoznávat a reagovat na neoprávněná použití][checks], včetně manipulace, ladění třetích stran a zařízení s rootem.

Další informace o tom, jak Dotfuscator zapadá do životního cyklu zabezpečení softwaru, najdete na stránce s možnostmi řešení pro správu [SDL][sdl-protection].

## <a name="about-dotfuscator-community"></a>O komunitě Dotfuscator

Vaše kopie Microsoft Visual Studio obsahuje kopii bezplatné ***ochrany Dotfuscator Community***, která je bezplatná pro osobní použití.
(Tato bezplatná verze se dřív nazývala jako Dotfuscator Community Edition nebo Dotfuscator CE.) Pokyny k instalaci verze Dotfuscator Community, která je součástí sady Visual Studio, najdete na [stránce instalace][install].

Komunita Dotfuscator nabízí řadu [ochrany softwaru a posílení][software-protection] služeb pro vývojáře, architekty a testery.
Příklady [Zazmatenosti rozhraní .NET][obfuscation] a dalších funkcí [ochrany aplikací][app-protection] , které jsou součástí komunity Dotfuscator:

* *[Přejmenování][renaming]* identifikátorů, aby zpětná analýza kompilovaných sestavení byla obtížnější.
* *[Ochrana proti falšování][tamper]* za účelem zjištění provádění poškozených aplikací a ukončení nebo reakce na úmyslně neoprávněné relace.
* *[Anti-Debug][debug]* pro detekci přílohy ladicího programu ke spuštěné aplikaci a ukončení nebo reakce na laděné relace.
* *[Zařízení s odrootem][root]* , aby se zjistilo, jestli je aplikace spuštěná na kořenovém zařízení s Androidem a jak na těchto zařízeních dokončí nebo reaguje na relace.
* *[Chování vypršení platnosti aplikace][shelflife]* , které zakódují "datum ukončení životního cyklu" a ukončí relaci aplikace s vypršenou platností.

Podrobnosti o těchto funkcích, včetně toho, jak se vejdou do vaší strategie ochrany aplikací, najdete na [stránce s funkcemi][capabilities].

Dotfuscator komunita nabízí základní ochranu předem.
K dispozici jsou i další míry ochrany aplikací pro registrované uživatele komunity Dotfuscator a pro uživatele s ***ochranou Dotfuscator Professional***na světě, což je špičkové špičkové [rozhraní .NET][net-obfuscator].
Informace o vylepšení Dotfuscator naleznete na [stránce upgrady][upgrades].

## <a name="getting-started"></a>Začínáme

::: moniker range="vs-2019"

Pokud chcete začít používat komunitu Dotfuscator ze sady Visual `dotfuscator` Studio, zadejte do **vyhledávacího pole** (CTRL + Q).

* Pokud je komunita Dotfuscator už nainstalovaná, **vyhledávací pole** zobrazí možnost spustit komunitu Dotfuscator v záhlaví *nabídek* . Podrobnosti najdete [na stránce Začínáme v úplné příručce pro uživatele komunity Dotfuscator][get-started].
* Pokud komunita Dotfuscator ještě není nainstalovaná, **vyhledávací pole** se místo toho zobrazí v záhlaví *jednotlivé komponenty* v části instalace s možností **přerušení ochrany – Dotfuscator** . Podrobnosti najdete na [stránce instalace][install] .

::: moniker-end

::: moniker range="vs-2017"

Pokud chcete začít používat komunitu Dotfuscator ze sady Visual `dotfuscator` Studio, zadejte do panelu hledání **Rychlé spuštění** (CTRL + Q).

* Pokud je komunita Dotfuscator už nainstalovaná, zobrazí se v nabídce **Snadné spuštění** možnost *nabídky* , která spustí uživatelské rozhraní komunity Dotfuscator. Podrobnosti najdete [na stránce Začínáme v úplné příručce pro uživatele komunity Dotfuscator][get-started].
* Pokud komunita Dotfuscator ještě není nainstalovaná, zobrazí se v okně **Snadné spuštění** odpovídající možnost *instalace* . Podrobnosti najdete na [stránce instalace][install] .

::: moniker-end

**Nejnovější verzi** Dotfuscator Community můžete získat také [na stránce soubory ke stažení Dotfuscator na PreEmptive.com][download].

## <a name="full-documentation"></a>Úplná dokumentace

Tato stránka a její podstránky poskytují podrobný přehled funkcí komunity Dotfuscator a také [pokyny pro instalaci nástroje][install].

Podrobné pokyny k používání najdete v tématu [Úplná Dotfuscator uživatelská příručka komunity na adrese PreEmptive.com][full] , včetně [toho, jak začít používat uživatelské rozhraní komunity Dotfuscator][get-started].

<!-- Copyright © 2019 PreEmptive Solutions, LLC -->

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
