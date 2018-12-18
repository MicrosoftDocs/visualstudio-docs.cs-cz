---
title: Visual Studio otevřít složku rozšíření přehled | Microsoft Docs
ms.custom: ''
ms.date: 02/21/2018
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 94c3f8bf-1de3-40ea-aded-7f40c4b314c7
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: dcb2d1d922b4ebd4943c42c478400c5873af9cc4
ms.sourcegitcommit: 498e39e89a89ad7bf9dcb0617424fff999b1c3b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/21/2018
ms.locfileid: "36302973"
---
# <a name="open-folder-extensibility"></a>Otevřete složku rozšíření

[Otevřete složku](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) funkce umožňuje uživatelům otevírat žádné základu kódu v sadě Visual Studio bez nutnosti projekt nebo řešení soubory. Otevřít složku nabízí funkce uživatelé očekávat ze sady Visual Studio, jako:

* Integrace Průzkumníka řešení a vyhledávání
* Editor zabarvení
* Přejít na navigační
* Najít v vyhledávání souborů

Při použití s úlohami například pro rozhraní .NET a C++ vývoj, uživatelé se také získat:

* Bohaté Intellisense
* Jazykové funkce

Pomocí otevřít složku autorům rozšíření vytvářet bohaté funkce pro žádný jazyk. Existují rozhraní API pro podporu vytváření, ladění a hledání symbolů pro každý soubor v uživatele základu kódu. Aktuální Extender můžete aktualizovat jejich stávajících funkcí sady Visual Studio zjistit kód bez základní projekty nebo řešení.

## <a name="an-api-without-project-systems"></a>Rozhraní API bez systémy projektu

Visual Studio v minulosti rozumí pouze soubory v řešení a jeho projektů pomocí projektu systémy. Systém projektu je zodpovědná za funkce a uživatelské interakce načíst projektu. Že rozumí co soubory jeho projekt obsahuje vizuální reprezentace obsahu projektu, závislostí na další projekty a úpravy základní souboru projektu. Je prostřednictvím těchto hierarchií a možnosti, které ostatní součásti fungují jménem uživatele. Ne všechny základy kódu jsou také reprezentované do projektu a řešení struktury. Skriptovací jazyky a open source kód napsaný v jazyce C++ pro Linux jsou dobrými příklady. Visual Studio se otevřít složku poskytuje uživatelům nový způsob interakci s jejich zdrojového kódu.

Rozhraní API, otevřete složku jsou v části `Microsoft.VisualStudio.Workspace.*` obor názvů a jsou k dispozici pro Extender vytvářet a využívat data nebo akce kolem souborů v rámci otevřít složku. Rozšíření můžete použít tato rozhraní API nabízí funkce pro mnoha oblastech, včetně:

- [Pracovní prostory](workspaces.md) – od bodu otevřít složku rozšíření je v pracovním prostoru a jejích rozhraní API.
- [Soubor kontexty a akce](workspace-file-contexts.md) -souboru konkrétního kódu intelligence poskytované prostřednictvím kontexty souboru.
- [Indexování](workspace-indexing.md) – shromažďuje a zachovat data o pracovních prostorech otevřít složku.
- [Jazyk služby](workspace-language-services.md) -integrace jazyka služeb do pracovních prostorů otevřít složku.
- [Sestavení](workspace-build.md) – podpora pro pracovní prostory otevřít složku sestavení.

Funkce, které používají následující typy bude muset přijmout nová rozhraní API pro podporu otevřít složku:

- `IVsHierarchy`
- `IVsProject`
- `DTE`

## <a name="feedback-comments-issues"></a>Zpětná vazba, komentáře, problémy

Otevřete složku a `Microsoft.VisualStudio.Workspace.*` rozhraní API jsou ve vývoji aktivní. Pokud se zobrazí neočekávanému chování, pak najdete v části Známé problémy pro tuto verzi, které vás zajímají. [Komunity vývojářů](https://developercommunity.visualstudio.com) je doporučené místo, hlasování a vytvořit všechny problémy. Pro každý zpětnou vazbu důrazně doporučujeme podrobný popis vašeho problému. Zahrnují verzi sady Visual Studio, které vyvíjíte pro, rozhraní API používáte (co jste implementovali i jste interakci s), očekávaný výsledek a skutečný výsledek. Pokud je to možné zahrnují výpis procesu devenv.exe. Pomocí sledování pro odeslání názoru na tento problém Githubu a související dokumentaci.

## <a name="next-steps"></a>Další kroky

* [Pracovní prostory](workspaces.md) -Další informace o pracovním prostoru otevřít složku rozhraní API.