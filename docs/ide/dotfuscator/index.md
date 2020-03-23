---
title: Dotfuscator Community
ms.date: 03/28/2019
ms.devlang: dotnet
ms.topic: conceptual
keywords: Dotfuscator, Dotfuscator CE, Dotfuscator Community, PreEmptive, PreEmptive Solutions, PreEmptive Protection, ochrana, edice pro komunitu, obfuskace, .NET, zdarma, Visual Studio 2019, Visual Studio 2017, Visual Studio
helpviewer_keywords:
- PreEmptive Protection Dotfuscator
- Dotfuscator Community Edition
- Dotfuscator CE
- Dotfuscator Community
- Dotfuscator
- obfuscation
- protection
description: Zjistěte, jak můžete chránit své aplikace .NET pomocí bezplatné kopie nástroje Dotfuscator Community, která je součástí sady Visual Studio.
ms.assetid: d9550502-0a82-49a6-b005-2caa791fbe02
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: f1b2c0bfd4adbd4a952a64f20fc3d2639a8abb5f
ms.sourcegitcommit: f8e3715c64255b476520bfa9267ceaf766bde3b0
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "75918447"
---
# <a name="dotfuscator-community"></a>Dotfuscator Community

Nástroj ***PreEmptive Protection – Dotfuscator*** poskytuje komplexní ochranu aplikací .NET, která hladce zapadá do životního cyklu zabezpečeného vývoje softwaru.
Umožňuje posílení, ochranu a pročištění desktopových, mobilních, serverových a vložených aplikací, abyste dosáhli lepšího zabezpečení obchodních tajemství a jiného duševního vlastnictví, snížili riziko pirátství a padělání a zvýšili ochranu před manipulací se softwarem a jeho neoprávněným laděním.
Dotfuscator pracuje na zkompilovaných sestaveních, aniž by vyžadoval další programování, nebo dokonce přístup ke zdrojovému kódu.

![PreEmptive Protection – Dotfuscator](media/header.svg)

## <a name="why-protection-matters"></a>Proč je tato ochrana důležitá

Je důležité **chránit duševní vlastnictví**.
Návrh a implementace kódu vaší aplikace zahrnuje detaily, které lze považovat za duševní vlastnictví.
Aplikace založené na rozhraní .NET Framework ale současně [obsahují významný objem metadat a mezikódu na vysoké úrovni][assemblies], což usnadňuje jejich zpětnou analýzu, a to i pomocí některého z mnoha bezplatných automatizovaných nástrojů.
Znemožněním zpětné analýzy můžete zabránit neoprávněnému zpřístupnění duševního vlastnictví a také dát najevo, že váš kód obsahuje obchodní tajemství.
Dotfuscator dokáže sestavení .NET [obfuskovat][obfuscation] tak, aby znemožnil zpětnou analýzu, ale zachoval původní chování aplikací.

Je také důležité **chránit integritu aplikace**.
Kromě zpětné analýzy se mohou aktéři se zlými úmysly pokusit u vaší aplikace o pirátství, změnu chování za běhu nebo manipulaci s daty.
Dotfuscator může do vaší aplikace vložit schopnost [detekovat neoprávněná použití a reagovat na ně][checks], a to včetně manipulací, ladění třetími stranami a výskytu zařízení s rootem.

Další informace o tom, jak Dotfuscator zapadá do životního cyklu zabezpečeného vývoje softwaru, najdete na stránce společnosti PreEmptive Solutions o [ochraně aplikací v rámci procesu SDL][sdl-protection].

## <a name="about-dotfuscator-community"></a>O nástroji Dotfuscator Community

Vaše kopie sady Microsoft Visual Studio obsahuje kopii nástroje ***PreEmptive Protection – Dotfuscator Community***, která je zdarma pro osobní použití.
(Tato bezplatná verze se dříve označovala jako Dotfuscator Community Edition nebo Dotfuscator CE.) Pokyny k instalaci verze nástroje Dotfuscator Community, která je součástí sady Visual Studio, najdete na stránce věnované [instalaci][install].

Dotfuscator Community nabízí řadu služeb zajišťujících [ochranu softwaru a silnější zabezpečení][software-protection] pro vývojáře, architekty a testery.
Tady jsou příklady [obfuskace .NET][obfuscation] a dalších funkcí pro [ochranu aplikací][app-protection], které jsou součástí nástroje Dotfuscator Community:

* *[Přejmenování][renaming]* identifikátorů, aby zpětná analýza zkompilovaných sestavení byla obtížnější
* *[Ochrana před manipulacemi][tamper]* pro detekci spouštění pozměněných aplikací a ukončování pozměněných relací nebo reakce na ně
* *[Ochrana před neoprávněným laděním][debug]* pro detekci připojení ladicího programu k běžící aplikaci a ukončování laděných relací nebo reakce na ně
* *[Ochrana před zařízeními s rootem][root]* pro detekci, jestli aplikace neběží na androidovém zařízení s rootem, a ukončování těchto zařízení nebo reakce na ně
* *[Nastavené chování na konci platnosti aplikace][shelflife]* , což znamená, že kód zahrnuje „datum konce životnosti“ a relace po konci platnosti se ukončují

Podrobnosti o těchto funkcích, včetně toho, jak zapadnou do vaší strategie ochrany aplikací, najdete na stránce věnované různým [schopnostem tohoto nástroje][capabilities].

Nástroj Dotfuscator Community nabízí základní ochranu už v předdefinovaném stavu.
Registrovaní uživatelé nástroje Dotfuscator Community a uživatelé verze ***PreEmptive Protection – Dotfuscator Professional***, což je nejlepší [obfuskátor .NET][net-obfuscator] na světě, mohou využívat i další možnosti ochrany aplikací.
Informace o rozšířených možnostech nástroje Dotfuscator najdete na stránce věnované [upgradům][upgrades].

## <a name="getting-started"></a>Začínáme

::: moniker range="vs-2019"

Pokud chcete Dotfuscator Community ze sady Visual Studio začít používat, napište `dotfuscator` do **vyhledávacího pole** (CTRL + Q).

* Pokud už je tento nástroj nainstalovaný, **vyhledávací pole** zobrazí možnost jeho spuštění pod záhlavím *Nabídky*. Podrobnosti najdete na [stránce Getting Started (Začínáme) v kompletní uživatelské příručce k nástroji Dotfuscator Community][get-started].
* Pokud nástroj Dotfuscator Community ještě nainstalovaný není, zobrazí **vyhledávací pole** možnost **nainstalovat PreEmptive Protection – Dotfuscator** pod záhlavím *Jednotlivé komponenty*. Podrobnosti najdete na stránce věnované [instalaci][install].

::: moniker-end

::: moniker range="vs-2017"

Pokud chcete Dotfuscator Community ze sady Visual Studio začít používat, napište `dotfuscator` do vyhledávacího panelu **Snadné spuštění** (CTRL + Q).

* Pokud už je tento nástroj nainstalovaný, panel **Snadné spuštění** zobrazí možnost *nabídky* pro spuštění jeho uživatelského rozhraní. Podrobnosti najdete na [stránce Getting Started (Začínáme) v kompletní uživatelské příručce k nástroji Dotfuscator Community][get-started].
* Pokud nástroj Dotfuscator Community ještě nainstalovaný není, panel **Snadné spuštění** zobrazí příslušnou možnost *instalace*. Podrobnosti najdete na stránce věnované [instalaci][install].

::: moniker-end

**Nejnovější verzi** nástroje Dotfuscator Community můžete také získat ze stránky [Dotfuscator Downloads na webu preemptive.com][download].

## <a name="full-documentation"></a>Kompletní dokumentace

Tato stránka a její podstránky poskytují stručný přehled funkcí nástroje Dotfuscator Community, jakož i [pokyny k jeho instalaci][install].

Podrobné pokyny k použití najdete v [kompletní uživatelské příručce k nástroji Dotfuscator Community na webu preemptive.com][full]. Zahrnuje i informace o tom, [jak začít používat jeho uživatelské rozhraní][get-started].

<!-- Copyright © 2019 PreEmptive Solutions, LLC -->

[assemblies]:  /dotnet/standard/assembly-format
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
