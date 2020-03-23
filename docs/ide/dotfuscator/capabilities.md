---
title: Funkce Dotfuscatoru
ms.date: 03/28/2019
ms.devlang: dotnet
ms.topic: conceptual
keywords: Dotfuscator, Dotfuscator Community, Dotfuscator CE, PreEmptive, PreEmptive Solutions, PreEmptive Protection, protection, community edition, obfuscation, .NET, free, Visual Studio 2017, Visual Studio 2019, Visual Studio
helpviewer_keywords:
- PreEmptive Protection Dotfuscator
- Dotfuscator Community Edition
- Dotfuscator Community
- Dotfuscator CE
- Dotfuscator
- obfuscation
- protection
description: Seznamte se s možnostmi bezplatné kopie komunity Dotfuscator, která je součástí sady Visual Studio.
ms.assetid: 0ee89c58-c900-48fc-a6a2-65ace00e8bab
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 019acd338ab49dd08255e3dc5d174cf2e371b71e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75918404"
---
# <a name="capabilities-of-dotfuscator"></a>Funkce Dotfuscatoru

Tato stránka se zaměřuje na schopnosti Dotfuscator Společenství s některými odkazy na pokročilé možnosti jsou k dispozici prostřednictvím [upgradů][upgrades].

Dotfuscator Community je *systém po sestavení* pro aplikace .NET.
S ním uživatelé sady Visual Studio jsou schopni [zamlžovat sestavení][obfuscation] a vstřikovat [aktivní obranné opatření][checks] do aplikace – to vše bez Dotfuscator potřebují přístup k původní zdrojový kód.
Dotfuscator chrání vaši aplikaci několika způsoby a vytváří strategii ochrany s vrstvami.

Dotfuscator Community podporuje širokou škálu typů sestavení a aplikací .NET, včetně [univerzální platformy Windows (UPW)][uwp] a [Xamarinu][xamarin].

## <a name="intellectual-property-protection"></a>Ochrana duševního vlastnictví

Návrh, chování a implementace aplikace jsou formy duševního vlastnictví (IP).
Aplikace vytvořené pro rozhraní .NET jsou však v podstatě otevřené knihy; je snadné zpětnou analýzu .NET sestavení, [protože obsahují metadata vysoké úrovně a zprostředkující kód][assemblies].

Dotfuscator Community zahrnuje základní [obfuskaci .NET][obfuscation] ve formě [přejmenování][renaming].
Zamlžení kódu pomocí Dotfuscator snižuje riziko neoprávněného přístupu ke zdrojovému kódu prostřednictvím reverzní analýzy, protože důležité informace o pojmenování již nebudou veřejné.
Zamlžení také ukazuje úsilí z vaší strany chránit váš kód před vyšetřením - cennýkrok při stanovení, že vaše IP je právně chráněna jako obchodní tajemství.

Mnoho [funkcí ochrany integrity aplikací](#application-integrity-protection) Dotfuscator Community dále brání zpětnému inženýrství.
Například chybný objekt actor se může pokusit připojit ladicí program ke spuštěné instanci aplikace, aby porozuměl logice programu.
Dotfuscator můžete vložit [anti-ladění chování][debug] do aplikace bránit to.

## <a name="application-integrity-protection"></a>Ochrana integrity aplikace

Kromě ochrany zdrojového kódu je také důležité zajistit, aby vaše aplikace byla použita tak, jak byla navržena.
Útočníci se mohou pokusit zneužít vaši aplikaci za účelem obcházení licenčních zásad (tj. softwarové kriminality), krádeže nebo manipulace s citlivými daty zpracovávaných aplikací nebo ke změně chování aplikace.

Dotfuscator Community může do sestavení vložit [ověřovací kód aplikace,][checks] včetně [anti-tamper][tamper], [anti-debug][debug]a [anti-rooted device][root] measures.
Pokud je zjištěn neplatný stav aplikace, ověřovací kód může [volat na kód aplikace k řešení situace vhodným způsobem][check-app].
Nebo pokud nechcete psát kód pro zpracování neplatných použití aplikace, Dotfuscator můžete také vložit [chování odpovědi,][check-action] aniž by bylo nutné jakékoli změny zdrojového kódu.

Mnohé z těchto stejných metod mohou být také použity k vynucení termínů ukončení [životnosti][shelflife] pro zkušební nebo zkušební software.

## <a name="see-also"></a>Viz také

[Toto téma v úplné uživatelské příručce komunity Dotfuscator][full]

<!-- Copyright © 2019 PreEmptive Solutions, LLC -->

[assemblies]:  /dotnet/standard/assembly-format
[uwp]:  https://www.preemptive.com/blog/article/856-uwp-applications-in-dotfuscator-ce/91-dotfuscator-ce
[xamarin]:  https://www.preemptive.com/obfuscating-xamarin-with-dotfuscator

[upgrades]:  upgrades.md

[obfuscation]:  https://www.preemptive.com/dotfuscator/ce/docs/help/obfuscation_overview.html
[renaming]:  https://www.preemptive.com/dotfuscator/ce/docs/help/obfuscation_renaming.html

[checks]:  https://www.preemptive.com/dotfuscator/ce/docs/help/checks_overview.html
[check-app]:  https://www.preemptive.com/dotfuscator/ce/docs/help/checks_overview.html#app-notification
[check-action]:  https://www.preemptive.com/dotfuscator/ce/docs/help/checks_overview.html#action

[tamper]:  https://www.preemptive.com/dotfuscator/ce/docs/help/checks_tamper.html
[debug]:  https://www.preemptive.com/dotfuscator/ce/docs/help/checks_debug.html
[root]: https://www.preemptive.com/dotfuscator/ce/docs/help/checks_root.html
[shelflife]:  https://www.preemptive.com/dotfuscator/ce/docs/help/checks_shelflife.html

[full]:  https://www.preemptive.com/dotfuscator/ce/docs/help/intro_capabilities.html
