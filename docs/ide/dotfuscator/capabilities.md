---
title: Funkce Dotfuscatoru
ms.date: 03/28/2019
ms.devlang: dotnet
ms.topic: conceptual
keywords: Dotfuscator, Dotfuscator Community, Dotfuscator CE, nepřesné, bezplatná řešení, preventivní ochrana, ochrana, Community Edition, zmatene, .NET, free, Visual Studio 2017, Visual Studio 2019, Visual Studio, Visual Studio
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
ms.openlocfilehash: a36aa17207affa257cdbb2caec0f2d6d9392285b
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75590004"
---
# <a name="capabilities-of-dotfuscator"></a>Funkce Dotfuscatoru

Tato stránka se zaměřuje na možnosti komunity Dotfuscator s některými odkazy na pokročilé možnosti, které jsou k dispozici prostřednictvím [upgradu][upgrades].

Dotfuscator Community je systém *po sestavení* pro aplikace .NET.
Díky tomu mohou uživatelé sady Visual Studio zakódovat [sestavení][obfuscation] a vložit do aplikace [aktivní opatření ochrany][checks] – bez Dotfuscator nutnosti získat přístup k původnímu zdrojovému kódu.
Dotfuscator chrání vaši aplikaci několika způsoby a vytváří vrstvu ochrany s vrstvami.

Komunita Dotfuscator podporuje široké spektrum typů sestavení a aplikací .NET, včetně [Univerzální platforma Windows (UWP)][uwp] a [Xamarin][xamarin].

## <a name="intellectual-property-protection"></a>Ochrana duševního vlastnictví

Návrh, chování a implementace vaší aplikace jsou formy duševního vlastnictví (IP).
Aplikace vytvořené pro .NET jsou ale v podstatě otevřené knihy. sestavení .NET je snadno možné zpětně zpracovat, [protože obsahují metadata vysoké úrovně a zprostředkující kód][assemblies].

Komunita Dotfuscator zahrnuje základní [zmatení rozhraní .NET][obfuscation] ve formě [přejmenování][renaming].
Zmatení kódu pomocí Dotfuscator snižuje riziko neoprávněného přístupu ke zdrojovému kódu prostřednictvím zpětné analýzy, protože důležité informace o pojmenování nebudou nadále veřejné.
Dekódování také ukazuje úsilí vaší součásti, aby chránila váš kód před přezkoumáním – hodnotným krokem při zjišťování, že vaše IP adresa je právně chráněna jako obchodní tajemství.

Mnohé z [funkcí ochrany integrity aplikací](#application-integrity-protection) Dotfuscator komunity dále brání zpětné analýze.
Například špatný objekt actor se může pokusit připojit ladicí program ke spuštěné instanci vaší aplikace, aby porozuměl logice programu.
Dotfuscator může do vaší aplikace vložit [chování proti ladění][debug] a zabránit tak tomu.

## <a name="application-integrity-protection"></a>Ochrana integrity aplikací

Kromě ochrany zdrojového kódu je také důležité zajistit, aby se vaše aplikace používala tak, jak je navržena.
Útočníci se můžou pokusit o zneužití vaší aplikace za účelem obejít zásady licencování (to znamená softwarová kriminalita), ukrást nebo manipulovat s citlivými daty, která zpracovává aplikace, nebo změnit chování aplikace.

Komunita Dotfuscator může vložit [kód pro ověření aplikace][checks] do vašich sestavení, včetně [ochrany proti falšování][tamper], [anti-ladění][debug]a [antirootem zařízení][root] .
Při zjištění neplatného stavu aplikace může ověřovací kód zavolat na [kód aplikace a vyřešit tak situaci vhodným způsobem][check-app].
Nebo, pokud nechcete psát kód pro zpracování neplatných použití aplikace, může Dotfuscator také vkládat chování [odpovědi][check-action] , aniž by to vyžadovalo úpravu zdrojového kódu.

Mnohé z těchto stejných metod se taky dají použít k vykonání konečných [termínů][shelflife] pro zkušební nebo zkušební software.

## <a name="see-also"></a>Viz také:

[Toto téma v úplné příručce pro uživatele komunity Dotfuscator][full]

<!-- Copyright © 2019 PreEmptive Solutions, LLC -->

[assemblies]:  https://docs.microsoft.com/dotnet/standard/assembly-format
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
