---
title: Přehled rozšiřitelnosti otevřených složek sady Visual Studio | Microsoft Docs
ms.date: 02/21/2018
ms.topic: overview
ms.assetid: 94c3f8bf-1de3-40ea-aded-7f40c4b314c7
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: d213a7add358c46f7088f504d8c54352cda44a1c
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/02/2020
ms.locfileid: "85905976"
---
# <a name="open-folder-extensibility"></a>Rozšiřitelnost otevření složky

Funkce [Otevřít složku](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) umožňuje uživatelům otevřít libovolný základ kódu v aplikaci Visual Studio bez potřeby souborů projektu nebo řešení. Otevřená složka poskytuje funkce, které uživatelé očekávají od sady Visual Studio, například:

* Průzkumník řešení integrace a hledání
* Zabarvení editoru
* Přejít k navigaci
* Najít v hledání souborů

Při použití s úlohami, jako je například vývoj pro .NET a C++, získají uživatelé také tyto kroky:

* Bohatá technologie IntelliSense
* Funkce specifické pro jazyk

Díky otevřené složce můžou autoři rozšíření vytvářet bohatou funkci pro libovolný jazyk. Existují rozhraní API pro podporu vytváření, ladění a hledání symbolů pro libovolný soubor v základu kódu uživatele. Aktuální zařízení pro rozšiřování můžou aktualizovat své stávající funkce sady Visual Studio, aby porozuměly kódu bez nutnosti zálohovat projekty nebo řešení.

## <a name="an-api-without-project-systems"></a>Rozhraní API bez projektových systémů

V minulosti se v rámci sady Visual Studio přirozuměly pouze soubory v řešení a jeho projektech, které používají projektové systémy. Systém projektu je zodpovědný za funkčnost a interakce uživatelů načteného projektu. Rozumí to, jaké soubory obsahuje projekt, vizuální reprezentace obsahu projektu, závislosti na jiných projektech a úprava podkladového souboru projektu. Je prostřednictvím těchto hierarchií a schopností, které v zastoupení uživatele pracují s ostatními komponentami. Ne všechny základy kódu jsou dobře zastoupeny v projektu a struktuře řešení. Dobrými příklady jsou skriptovací jazyky a open source kód napsaný v jazyce C++ pro Linux. S otevřenou složkou Visual Studio poskytuje uživatelům nový způsob interakce s jejich zdrojovým kódem.

Rozhraní API pro otevření složky jsou v `Microsoft.VisualStudio.Workspace.*` oboru názvů a jsou k dispozici pro rozšíření pro vytváření a zpracování dat nebo akcí pro soubory v rámci otevřené složky. Rozšíření můžou používat tato rozhraní API k poskytování funkcí pro mnoho oblastí, včetně:

- [Pracovní prostory](workspaces.md) – počáteční bod rozšiřitelnosti otevřené složky je pracovní prostor a jeho rozhraní API.
- [Kontexty souborů a akce](workspace-file-contexts.md) – informace specifické pro soubory poskytované prostřednictvím kontextů souborů.
- [Indexování](workspace-indexing.md) – shromažďování a uchovávání dat o otevřených pracovních prostorech složky.
- [Jazykové služby](workspace-language-services.md) – Integrujte jazykové služby do pracovních prostorů otevřené složky.
- [Sestavení](workspace-build.md) – podpora sestavení pro pracovní prostory otevřených složek

Funkce, které používají následující typy, budou muset pro podporu otevřené složky přijmout nová rozhraní API:

- `IVsHierarchy`
- `IVsProject`
- `DTE`

## <a name="feedback-comments-issues"></a>Zpětná vazba, komentáře, problémy

Otevřená složka a `Microsoft.VisualStudio.Workspace.*` rozhraní API se nacházejí v aktivním vývoji. Pokud se zobrazí neočekávané chování, podívejte se na známé problémy pro vydání zájmu. [Komunita vývojářů](https://developercommunity.visualstudio.com) je doporučeným místem, kde můžete hlasovat a vytvářet případné problémy. U každé zpětné vazby důrazně doporučujeme detailní popis problému. Zahrňte verzi sady Visual Studio, kterou vyvíjíte, rozhraní API, která používáte (jak jste implementovali a co s tím interaktivně pracujete), očekávaný výsledek a skutečný výsledek. Pokud je to možné, zahrňte výpis devenv.exe procesu. Pro poskytování zpětné vazby k této a související dokumentaci použijte sledování problémů GitHubu.

## <a name="next-steps"></a>Další kroky

* [Pracovní prostory](workspaces.md) – Přečtěte si informace o rozhraní API pro otevřené složky v pracovním prostoru.