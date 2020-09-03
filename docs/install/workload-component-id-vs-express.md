---
title: Úlohy a ID součástí sady Visual Studio Desktop Express
titleSuffix: ''
description: Použití zatížení a ID komponent k instalaci sady Visual Studio pomocí příkazového řádku nebo pro určení jako závislosti v manifestu VSIX
keywords: ''
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.date: 11/13/2018
ms.topic: reference
helpviewer_keywords:
- workload ID, Visual Studio
- component ID, Visual Studio
- install Visual Studio, administrator guide
ms.assetid: a3c0cc76-e3ce-435c-a1af-a6318b5a4dbe
ms.prod: visual-studio-windows
ms.technology: vs-installation
monikerRange: vs-2017
open_to_public_contributors: false
ms.openlocfilehash: 1e24f90f24921bee9a6132ccc047c0b9da37fc90
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "81276289"
---
# <a name="visual-studio-desktop-express-component-directory"></a>Adresář komponenty Visual Studio Desktop Express

Tabulky na této stránce uvádějí ID, která můžete použít k instalaci sady Visual Studio pomocí příkazového řádku nebo které můžete zadat jako závislost v manifestu VSIX. Všimněte si, že přidáme další komponenty jako aktualizace vydané do sady Visual Studio.

Všimněte si také následujících informací o stránce:

* Každá úloha má svůj vlastní oddíl následovaný ID úlohy a tabulkou komponent, které jsou k dispozici pro zatížení.
* Ve výchozím nastavení se **požadované** součásti nainstalují při instalaci úlohy.
* Pokud se rozhodnete, můžete nainstalovat také **Doporučené** a **volitelné** součásti.
* Přidali jsme také část, která obsahuje seznam dalších komponent, které nejsou přidružené k žádnému zatížení.

Při nastavování závislostí v manifestu VSIX je nutné zadat pouze ID součástí. Pomocí tabulek na této stránce můžete určit minimální závislosti součástí. V některých scénářích to může znamenat, že zadáváte jenom jednu komponentu z úlohy. V jiných scénářích to může znamenat, že zadáváte více komponent z jedné úlohy nebo z více komponent z více úloh. Další informace naleznete v tématu [Postupy: migrace projektů rozšíření na stránku sady Visual Studio 2017](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2017.md) .

Další informace o použití těchto identifikátorů najdete v tématu věnovaném [použití parametrů příkazového řádku k instalaci stránky sady Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md) . Seznam úloh a ID komponent pro jiné produkty najdete na stránce [Visual Studio 2017 – úlohy a ID komponent](workload-and-component-ids.md) .

## <a name="express-for-windows-desktop"></a>Express for Windows Desktop

**ID:** Microsoft. VisualStudio. úlohy. WDExpress

**Popis:** Sestavování nativních a spravovaných aplikací, jako je WPF, WinForms a Win32, pomocí úprav kódu s podporou syntaxe, správy zdrojového kódu a správy pracovních položek. Zahrnuje podporu pro C#, Visual Basic a Visual C++.

### <a name="components-included-by-this-workload"></a>Součásti zahrnuté v tomto zatížení

ID součásti | Název | Verze | Typ závislosti
--- | --- | --- | ---
Microsoft. Component. ClickOnce | Publikování ClickOnce | 15.8.27825.0 | Vyžadováno
Microsoft. Component. HelpViewer | Prohlížeč nápovědy | 15.6.27323.2 | Vyžadováno
Microsoft. Component. MSBuild | MSBuild | 15.7.27520.0 | Vyžadováno
Microsoft. Component. VC. Runtime. OSSupport | Modul runtime Visual C++ pro UWP | 15.6.27406.0 | Vyžadováno
Microsoft.Net. Component. 4.5.1. TargetingPack | Sada .NET Framework 4.5.1 targeting pack | 15.6.27406.0 | Vyžadováno
Microsoft.Net. Component. 4.5.2. TargetingPack | Sada .NET Framework 4.5.2 targeting pack | 15.6.27406.0 | Vyžadováno
Microsoft.Net. Component. 4.5. TargetingPack | Sada targeting pack .NET Framework 4,5 | 15.6.27406.0 | Vyžadováno
Microsoft. NET. Component. 4.6.1. SDK | .NET Framework 4.6.1 SDK | 15.6.27406.0 | Vyžadováno
Microsoft.Net. Component. 4.6.1. TargetingPack | .NET Framework 4.6.1 targeting pack | 15.6.27406.0 | Vyžadováno
Microsoft.Net. Component. 4.6. TargetingPack | Sada targeting pack .NET Framework 4,6 | 15.6.27406.0 | Vyžadováno
Microsoft.Net. Component. 4. TargetingPack | Sada targeting pack .NET Framework 4 | 15.6.27406.0 | Vyžadováno
Microsoft.Net. Component. DevelopmentPrerequisites | Vývojové nástroje .NET Framework 4.6.1 | 15.8.27825.0 | Vyžadováno
Microsoft.Net. Component. TargetingPacks. Common | .NET Framework nástroje pro vývoj 4 – 4,6 | 15.6.27406.0 | Vyžadováno
Microsoft. VisualStudio. Component. Common. Azure. Tools | Nástroje pro připojení a publikování | 15.9.28107.0 | Vyžadováno
Microsoft. VisualStudio. Component. CoreEditor | Základní editor sady Visual Studio | 15.8.27729.1 | Vyžadováno
Microsoft. VisualStudio. Component. EntityFramework | Nástroje Entity Framework 6 | 15.6.27406.0 | Vyžadováno
Microsoft. VisualStudio. Component. NuGet | Správce balíčků NuGet | 15.9.28016.0 | Vyžadováno
Microsoft. VisualStudio. Component. Roslyn. Compiler | Kompilátory C# a Visual Basic Roslyn | 15.6.27309.0 | Vyžadováno
Microsoft. VisualStudio. Component. Roslyn. LanguageServices | C# a Visual Basic | 15.8.27729.1 | Vyžadováno
Microsoft. VisualStudio. Component. SQL. ADAL | Modul runtime SQL ADAL | 15.6.27406.0 | Vyžadováno
Microsoft. VisualStudio. Component. SQL. CLR | Datové typy CLR pro SQL Server | 15.0.26208.0 | Vyžadováno
Microsoft. VisualStudio. Component. SQL. CMDUtils | SQL Server nástroje příkazového řádku | 15.0.26208.0 | Vyžadováno
Microsoft. VisualStudio. Component. SQL. DataSources | Zdroje dat pro podporu SQL Server | 15.0.26621.2 | Vyžadováno
Microsoft. VisualStudio. Component. SQL. LocalDB. Runtime | SQL Server Express 2016 LocalDB | 15.7.27617.1 | Vyžadováno
Microsoft. VisualStudio. Component. SQL. NCLI | Nativní klient systému SQL Server | 15.0.26208.0 | Vyžadováno
Microsoft. VisualStudio. Component. SQL. SSDT | SQL Server Data Tools | 15.9.28107.0 | Vyžadováno
Microsoft. VisualStudio. Component. static. Analysis. Tools | Nástroje statické analýzy | 15.0.26208.0 | Vyžadováno
Microsoft. VisualStudio. Component. TextTemplating | Transformace textové šablony | 15.0.26208.0 | Vyžadováno
Microsoft. VisualStudio. Component. VC. CLI. support | Podpora C++/CLI | 15.6.27309.0 | Vyžadováno
Microsoft. VisualStudio. Component. VC. Tools. ARM | Visual C++ kompilátorů a knihoven pro ARM | 15.8.27825.0 | Vyžadováno
Microsoft. VisualStudio. Component. VC. Tools. ARM64 | Visual C++ kompilátorů a knihoven pro ARM64 | 15.9.28230.55 | Vyžadováno
Microsoft. VisualStudio. Component. VisualStudioData | Zdroje dat a odkazy na služby | 15.6.27406.0 | Vyžadováno
Microsoft. VisualStudio. Component. Windows10SDK. 14393 | Windows 10 SDK (10.0.14393.0) | 15.6.27406.0 | Vyžadováno
Microsoft. VisualStudio. Component. Windows10SDK. 17134 | Windows 10 SDK (10.0.17134.0) | 15.8.27924.0 | Vyžadováno

## <a name="unaffiliated-components"></a>Nepřidružené součásti

Jedná se o součásti, které nejsou součástí žádné úlohy, ale mohou být vybrány jako jednotlivé komponenty.

ID součásti | Název | Verze
--- | --- | ---
Není k dispozici | Není k dispozici | Není k dispozici

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Viz také

* [ID úloh a komponent sady Visual Studio](workload-and-component-ids.md)
* [Příručka správce sady Visual Studio](visual-studio-administrator-guide.md)
* [Instalace sady Visual Studio s použitím parametrů příkazového řádku](use-command-line-parameters-to-install-visual-studio.md)
  * [Příklady parametrů příkazového řádku](command-line-parameter-examples.md)
* [Vytvoření offline instalace sady Visual Studio](create-an-offline-installation-of-visual-studio.md)
