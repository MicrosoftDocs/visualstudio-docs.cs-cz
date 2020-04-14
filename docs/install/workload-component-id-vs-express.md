---
title: Pracovní vytížení a ID součástí visual studio Desktop Express
titleSuffix: ''
description: Použití id úloh a součástí k instalaci sady Visual Studio pomocí příkazového řádku nebo k určení závislosti v manifestu VSIX
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
ms.sourcegitcommit: 22deb247ad951e4971f27fdab413b158415d0584
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81276289"
---
# <a name="visual-studio-desktop-express-component-directory"></a>Adresář komponent Visual Studio Desktop Express

Tabulky na této stránce uvádějí ID, které můžete použít k instalaci sady Visual Studio pomocí příkazového řádku nebo které můžete zadat jako závislost v manifestu VSIX. Všimněte si, že budeme přidávat další součásti, jak budeme vydávat aktualizace visual studio.

Všimněte si také následující o stránce:

* Každé pracovní vytížení má vlastní část, následovanou ID pracovního vytížení a tabulkou součástí, které jsou k dispozici pro úlohu.
* Ve výchozím nastavení budou **požadované** součásti nainstalovány při instalaci úlohy.
* Pokud se rozhodnete, můžete také nainstalovat **doporučené** a **volitelné** součásti.
* Přidali jsme také oddíl, který obsahuje seznam dalších součástí, které nejsou přidruženy k žádné pracovní zátěži.

Když nastavíte závislosti v manifestu VSIX, musíte zadat pouze ID součástí. Pomocí tabulek na této stránce určete naše minimální závislosti součástí. V některých případech to může znamenat, že zadáte pouze jednu součást z pracovního vytížení. V jiných scénářích to může znamenat, že zadáte více součástí z jednoho pracovního vytížení nebo více součástí z více úloh. Další informace najdete v tématu [Postup: Migrace projektů rozšiřitelnosti do Visual Studia 2017](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2017.md) stránku.

Další informace o použití těchto ID najdete [v tématu Použití parametrů příkazového řádku k instalaci stránky Visual Studia 2017.](use-command-line-parameters-to-install-visual-studio.md) A seznam úloh a ID součástí pro jiné produkty najdete na stránce [Visual Studio 2017 Workload and Component ID.](workload-and-component-ids.md)

## <a name="express-for-windows-desktop"></a>Express pro plochu systému Windows

**ID:** Microsoft.VisualStudio.Workload.WDExpress

**Popis:** Vytvářejte nativní a spravované aplikace jako WPF, WinForms a Win32 pomocí úprav kódu podporujícího syntaxi, správy zdrojového kódu a správy pracovních položek. Zahrnuje podporu pro C#, Visual Basic a Visual C++.

### <a name="components-included-by-this-workload"></a>Komponenty zahrnuté do tohoto pracovního vytížení

ID součásti | Name (Název) | Version | Typ závislosti
--- | --- | --- | ---
Microsoft.Component.ClickOnce | Publikování clickonce | 15.8.27825.0 | Požaduje se
Microsoft.Component.HelpViewer | Prohlížeč nápovědy | 15.6.27323.2 | Požaduje se
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | Požaduje se
Podpora Microsoft.Component.VC.Runtime.OSSupport | Visual C++ runtime pro UPW | 15.6.27406.0 | Požaduje se
Microsoft.Net.Component.4.5.1.TargetingPack | Balíček cílení v rámci .NET Framework 4.5.1 | 15.6.27406.0 | Požaduje se
Microsoft.Net.Component.4.5.2.TargetingPack | Balíček cílení .NET Framework 4.5.2 | 15.6.27406.0 | Požaduje se
Sada Microsoft.Net.Component.4.5.TargetingPack | Balíček cílení rozhraní .NET Framework 4.5 | 15.6.27406.0 | Požaduje se
Microsoft.Net.Component.4.6.1.SDK | Rozhraní .NET Framework 4.6.1 SDK | 15.6.27406.0 | Požaduje se
Microsoft.Net.Component.4.6.1.TargetingPack | Balíček cílení rozhraní .NET Framework 4.6.1 | 15.6.27406.0 | Požaduje se
Sada Microsoft.Net.Component.4.6.TargetingPack | Balíček cílení rozhraní .NET Framework 4.6 | 15.6.27406.0 | Požaduje se
Sada Microsoft.Net.Component.4.TargetingPack | Balíček cílení rozhraní .NET Framework 4 | 15.6.27406.0 | Požaduje se
Microsoft.Net.ComponentGroup.DevelopmentPředpoklads | Vývojové nástroje .NET Framework 4.6.1 | 15.8.27825.0 | Požaduje se
Microsoft.Net.ComponentGroup.TargetingPacks.Common | .NET Framework 4 – 4.6 vývojové nástroje | 15.6.27406.0 | Požaduje se
Microsoft.VisualStudio.Component.Common.Azure.Tools | Nástroje pro konektivitu a publikování | 15.9.28107.0 | Požaduje se
Microsoft.VisualStudio.Component.CoreEditor | Základní editor Visual Studia | 15.8.27729.1 | Požaduje se
Microsoft.VisualStudio.Component.EntityFramework | Nástroje entity Framework 6 | 15.6.27406.0 | Požaduje se
Soubor Microsoft.VisualStudio.Component.NuGet | Správce balíčků NuGet | 15.9.28016.0 | Požaduje se
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilátory Roslyn jazyka C# a Visual Basic | 15.6.27309.0 | Požaduje se
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# a Visual Basic | 15.8.27729.1 | Požaduje se
Microsoft.VisualStudio.Component.SQL.ADAL | Modul runtime SQL ADAL | 15.6.27406.0 | Požaduje se
Microsoft.VisualStudio.Component.SQL.CLR | Datové typy CLR pro SQL Server | 15.0.26208.0 | Požaduje se
Microsoft.VisualStudio.Component.SQL.CMDUtils | Nástroje příkazového řádku serveru SQL Server | 15.0.26208.0 | Požaduje se
Microsoft.VisualStudio.Component.SQL.DataSources | Zdroje dat pro podporu serveru SQL Server | 15.0.26621.2 | Požaduje se
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 15.7.27617.1 | Požaduje se
Microsoft.VisualStudio.Component.SQL.NCLI | Nativní klient systému SQL Server | 15.0.26208.0 | Požaduje se
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 15.9.28107.0 | Požaduje se
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Nástroje statické analýzy | 15.0.26208.0 | Požaduje se
Microsoft.VisualStudio.Component.TextTemplating | Transformace šablony textu | 15.0.26208.0 | Požaduje se
Microsoft.VisualStudio.Component.VC.CLI.Support | Podpora pro C++/CLI | 15.6.27309.0 | Požaduje se
Microsoft.VisualStudio.Component.VC.Tools.ARM | Kompilátory a knihovny Visual C++ pro ARM | 15.8.27825.0 | Požaduje se
Microsoft.VisualStudio.Component.VC.Tools.ARM64 | Kompilátory a knihovny Visual C++ pro ARM64 | 15.9.28230.55 | Požaduje se
Microsoft.VisualStudio.Component.VisualStudioData | Zdroje dat a odkazy na služby | 15.6.27406.0 | Požaduje se
Microsoft.VisualStudio.Component.Windows10SDK.14393 | Windows 10 SDK (10.0.14393.0) | 15.6.27406.0 | Požaduje se
Microsoft.VisualStudio.Component.Windows10SDK.17134 | Windows 10 SDK (10.0.17134.0) | 15.8.27924.0 | Požaduje se

## <a name="unaffiliated-components"></a>Nepřidružené součásti

Jedná se o součásti, které nejsou součástí žádné úlohy, ale mohou být vybrány jako jednotlivé součásti.

ID součásti | Name (Název) | Version
--- | --- | ---
neuvedeno | neuvedeno | neuvedeno

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Viz také

* [ID úloh a komponent sady Visual Studio](workload-and-component-ids.md)
* [Příručka správce sady Visual Studio](visual-studio-administrator-guide.md)
* [Instalace sady Visual Studio s použitím parametrů příkazového řádku](use-command-line-parameters-to-install-visual-studio.md)
  * [Příklady parametrů příkazového řádku](command-line-parameter-examples.md)
* [Vytvoření offline instalace sady Visual Studio](create-an-offline-installation-of-visual-studio.md)
