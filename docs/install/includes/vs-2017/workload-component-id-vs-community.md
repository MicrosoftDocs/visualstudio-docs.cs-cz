---
title: Pracovní vytížení visual studio 2017 a ID součástí
titleSuffix: ''
description: Použití id úloh a součástí k instalaci sady Visual Studio pomocí příkazového řádku nebo k určení závislosti v manifestu VSIX
keywords: ''
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.date: 2/12/2019
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.topic: include
ms.openlocfilehash: 83a1daa65642d720bd5f2420ee634688cf4be2c4
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "76159453"
---
## <a name="visual-studio-core-editor-included-with-visual-studio-community-2017"></a>Visual Studio core editor (součástí Visual Studio Community 2017)

**ID:** Microsoft.VisualStudio.Workload.CoreEditor

**Popis:** Prostředí základní prostředí sady Visual Studio, včetně úprav kódu podporujícího syntaxi, správy zdrojového kódu a správy pracovních položek.

### <a name="components-included-by-this-workload"></a>Komponenty zahrnuté do tohoto pracovního vytížení

ID součásti | Name (Název) | Version | Typ závislosti
--- | --- | --- | ---
Microsoft.VisualStudio.Component.CoreEditor | Základní editor Visual Studia | 15.8.27729.1 | Požaduje se
Soubor Microsoft.VisualStudio.Component.StartPageExperiment.Cpp | Úvodní stránka Visual Studia pro uživatele c++ | 15.0.27128.1 | Nepovinné

## <a name="azure-development"></a>Vývoj pro Azure

**ID:** Microsoft.VisualStudio.Workload.Azure

**Popis:** Sady Azure SDK, nástroje a projekty pro vývoj cloudových aplikací, vytváření prostředků a vytváření kontejnerů včetně podpory Dockeru.

### <a name="components-included-by-this-workload"></a>Komponenty zahrnuté do tohoto pracovního vytížení

ID součásti | Name (Název) | Version | Typ závislosti
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Razor Language Services | 15.0.26720.2 | Požaduje se
Component.Microsoft.VisualStudio.Web.AzureFunkce | Nástroje pro webové úlohy Microsoft Azure | 15.7.27617.1 | Požaduje se
Component.Microsoft.Web.LibraryManager | Správce knihovny | 15.8.27705.0 | Požaduje se
Komponenta.WebSocket | WebSocket4Net | 15.0.26606.0 | Požaduje se
Microsoft.Component.ClickOnce | Publikování clickonce | 15.8.27825.0 | Požaduje se
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | Požaduje se
Microsoft.Component.NetFX.Core.Runtime | Doba běhu jádra .NET | 15.0.26208.0 | Požaduje se
Microsoft.Net.Component.4.5.2.TargetingPack | Balíček cílení .NET Framework 4.5.2 | 15.6.27406.0 | Požaduje se
Sada Microsoft.Net.Component.4.5.TargetingPack | Balíček cílení rozhraní .NET Framework 4.5 | 15.6.27406.0 | Požaduje se
Microsoft.Net.Component.4.6.1.SDK | Rozhraní .NET Framework 4.6.1 SDK | 15.6.27406.0 | Požaduje se
Microsoft.Net.Component.4.6.1.TargetingPack | Balíček cílení rozhraní .NET Framework 4.6.1 | 15.6.27406.0 | Požaduje se
Microsoft.Net.ComponentGroup.DevelopmentPředpoklads | Vývojové nástroje .NET Framework 4.6.1 | 15.8.27825.0 | Požaduje se
Microsoft.Net.core.component.Sdk.2.1 | Vývojové nástroje .NET Core 2.1 | 15.8.27924.0 | Požaduje se
Microsoft.NetCore.ComponentGroup.DevelopmentTools.2.1 | Vývojové nástroje .NET Core 2.1 | 15.8.27924.0 | Požaduje se
Microsoft.NetCore.ComponentGroup.Web.2.1 | Vývojové nástroje .NET Core 2.1 | 15.8.27924.0 | Požaduje se
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Vývojové nástroje Azure | 15.9.28307.421 | Požaduje se
Microsoft.VisualStudio.Component.Azure.ClientLibs | Knihovny Azure pro rozhraní .NET | 15.0.26208.0 | Požaduje se
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Výpočetní emulátor Azure | 15.9.28307.421 | Požaduje se
Microsoft.VisualStudio.Component.Azure.Storage.Emulátor | Emulátor úložiště Azure | 15.9.28125.51 | Požaduje se
Microsoft.VisualStudio.Component.CloudExplorer | Průzkumník cloudu | 15.9.28230.55 | Požaduje se
Microsoft.VisualStudio.Component.Common.Azure.Tools | Nástroje pro konektivitu a publikování | 15.9.28107.0 | Požaduje se
Microsoft.VisualStudio.Component.DockerTools | Kontejnerové vývojové nástroje | 15.8.27906.1 | Požaduje se
Microsoft.VisualStudio.Component.DockerTools.BuildTools | Nástroje pro vývoj kontejnerů – nástroje pro vytváření | 15.7.27617.1 | Požaduje se
Microsoft.VisualStudio.Component.FSharp | Podpora jazyka F# | 15.8.27825.0 | Požaduje se
Šablony Microsoft.VisualStudio.Component.FSharp.WebTemplates | Podpora jazyka F# pro webové projekty | 15.9.28307.421 | Požaduje se
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 15.0.26208.0 | Požaduje se
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostika javascriptu | 15.8.27729.1 | Požaduje se
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Podpora jazyka JavaScript a TypeScript | 15.9.28125.51 | Požaduje se
Soubor Microsoft.VisualStudio.Component.ManagedDesktop.Core | Jádro spravovaného pracovního vytížení plochy | 15.8.27729.1 | Požaduje se
Soubor Microsoft.VisualStudio.Component.NuGet | Správce balíčků NuGet | 15.9.28016.0 | Požaduje se
Knihovna Microsoft.VisualStudio.Component.PortableLibrary | Balíček cílení na přenosnou knihovnu .NET | 15.6.27309.0 | Požaduje se
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
Microsoft.VisualStudio.Component.TypeScript.3.1 | TypeScript 3.1 SDK | 15.0.28218.60 | Požaduje se
Microsoft.VisualStudio.Component.VisualStudioData | Zdroje dat a odkazy na služby | 15.6.27406.0 | Požaduje se
Microsoft.VisualStudio.Component.Web | ASP.NET a nástroje pro vývoj webových aplikací | 15.8.27825.0 | Požaduje se
Microsoft.VisualStudio.ComponentGroup.Azure.Prerequisites | Předpoklady pro vývoj Azure | 15.9.28107.0 | Požaduje se
Funkce Microsoft.VisualStudio.ComponentGroup.Azure | Nástroje pro webové úlohy Microsoft Azure | 15.7.27617.1 | Požaduje se
Microsoft.VisualStudio.ComponentGroup.Web | předpoklady pro ASP.NET a nástroje pro vývoj webových aplikací | 15.9.28219.51 | Požaduje se
Rozšíření microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Vývoj pro ASP.NET a web | 15.8.27825.0 | Požaduje se
Microsoft.Component.Azure.datalake.Tools | Nástroje Azure Data Lake a Stream Analytics | 15.9.28107.0 | Doporučené
Microsoft.Net.Component.4.5.1.TargetingPack | Balíček cílení v rámci .NET Framework 4.5.1 | 15.6.27406.0 | Doporučené
Sada Microsoft.Net.Component.4.6.TargetingPack | Balíček cílení rozhraní .NET Framework 4.6 | 15.6.27406.0 | Doporučené
Sada Microsoft.Net.Component.4.TargetingPack | Balíček cílení rozhraní .NET Framework 4 | 15.6.27406.0 | Doporučené
Microsoft.Net.ComponentGroup.TargetingPacks.Common | .NET Framework 4 – 4.6 vývojové nástroje | 15.6.27406.0 | Doporučené
Microsoft.VisualStudio.Component.AspNet45 | Pokročilé ASP.NET funkce | 15.7.27625.0 | Doporučené
Microsoft.VisualStudio.Component.Azure.MobileAppsSdk | Azure Mobilní aplikace SDK | 15.7.27625.0 | Doporučené
Microsoft.VisualStudio.Component.Azure.ResourceManager.Tools | Základní nástroje Azure Resource Manageru | 15.9.28107.0 | Doporučené
Microsoft.VisualStudio.Component.Azure.ServiceFabric.Tools | Nástroje Service Fabricu | 15.8.27825.0 | Doporučené
Microsoft.VisualStudio.Component.Azure.Waverton | Základní nástroje Cloudových služeb Azure | 15.9.28107.0 | Doporučené
Microsoft.VisualStudio.Component.Azure.Waverton.BuildTools | Nástroje pro vytváření cloudových služeb Azure | 15.7.27617.1 | Doporučené
Microsoft.VisualStudio.Component.DiagnosticTools | Nástroje profilování rozhraní .NET | 15.8.27729.1 | Doporučené
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 15.8.27729.1 | Doporučené
Služby Microsoft.VisualStudio.ComponentGroup.Azure.CloudServices | Nástroje cloudových služeb Azure | 15.0.26504.0 | Doporučené
Microsoft.VisualStudio.ComponentGroup.Azure.ResourceManager.Tools | Nástroje Azure Resource Manager | 15.0.27005.2 | Doporučené
Microsoft.Net.Component.4.6.2.SDK | Rozhraní .NET Framework 4.6.2 SDK | 15.6.27406.0 | Nepovinné
Sada Microsoft.Net.Component.4.6.2.TargetingPack | Balíček cílení .NET Framework 4.6.2 | 15.6.27406.0 | Nepovinné
Microsoft.Net.Component.4.7.1.SDK | Rozhraní .NET Framework 4.7.1 SDK | 15.6.27406.0 | Nepovinné
Microsoft.Net.Component.4.7.1.TargetingPack | Balíček cílení .NET Framework 4.7.1 | 15.6.27406.0 | Nepovinné
Microsoft.Net.Component.4.7.2.SDK | Rozhraní .NET Framework 4.7.2 SDK | 15.8.27825.0 | Nepovinné
Microsoft.Net.Component.4.7.2.TargetingPack | Balíček cílení .NET Framework 4.7.2 | 15.8.27825.0 | Nepovinné
Sada Microsoft.Net.Component.4.7.SdK | Rozhraní .NET Framework 4.7 SDK | 15.6.27406.0 | Nepovinné
Sada Microsoft.Net.Component.4.7.TargetingPack | Balíček cílení rozhraní .NET Framework 4.7 | 15.6.27406.0 | Nepovinné
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | Vývojové nástroje .NET Framework 4.6.2 | 15.6.27406.0 | Nepovinné
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | Vývojové nástroje .NET Framework 4.7.1 | 15.6.27406.0 | Nepovinné
Microsoft.Net.ComponentGroup.4.7.2.DeveloperTools | Vývojové nástroje .NET Framework 4.7.2 | 15.8.27825.0 | Nepovinné
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | Vývojové nástroje rozhraní .NET Framework 4.7 | 15.6.27406.0 | Nepovinné
Soubor Microsoft.Net.core.component.SDK | Vývojové nástroje .NET Core 2.0 | 15.6.27406.0 | Nepovinné
Microsoft.Net.Core.Component.SDK.1x | .NET Core 1.0 - 1.1 vývojové nástroje | 15.6.27406.0 | Nepovinné
Microsoft.NetCore.1x.ComponentGroup.Web | .NET Core 1.0 - 1.1 vývojové nástroje pro web | 15.6.27406.0 | Nepovinné
Microsoft.Netcore.ComponentGroup.DevelopmentTools | Vývojové nástroje .NET Core 2.0 | 15.8.27729.1 | Nepovinné
Microsoft.Netcore.ComponentGroup.Web | Vývojové nástroje .NET Core 2.0 | 15.7.27625.0 | Nepovinné
Microsoft.VisualStudio.Component.Azure.Storage.AzCopy | Azure Storage AzCopy | 15.0.26906.1 | Nepovinné
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | 15.8.27924.0 | Nepovinné

## <a name="data-storage-and-processing"></a>Ukládání a zpracování dat

**ID:** Microsoft.VisualStudio.Workload.Data

**Popis:** Připojte, vyvíjejte a otestujte datová řešení pomocí SQL Serveru, Azure Data Lake nebo Hadoop.

### <a name="components-included-by-this-workload"></a>Komponenty zahrnuté do tohoto pracovního vytížení

ID součásti | Name (Název) | Version | Typ závislosti
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Razor Language Services | 15.0.26720.2 | Doporučené
Component.Microsoft.Web.LibraryManager | Správce knihovny | 15.8.27705.0 | Doporučené
Součást.Redgate.SQLSearch.VSExtension | Hledání v Redgate SQL | 3.1.7.2062 | Doporučené
Komponenta.WebSocket | WebSocket4Net | 15.0.26606.0 | Doporučené
Microsoft.Component.Azure.datalake.Tools | Nástroje Azure Data Lake a Stream Analytics | 15.9.28107.0 | Doporučené
Microsoft.Component.ClickOnce | Publikování clickonce | 15.8.27825.0 | Doporučené
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | Doporučené
Microsoft.Net.Component.4.5.1.TargetingPack | Balíček cílení v rámci .NET Framework 4.5.1 | 15.6.27406.0 | Doporučené
Microsoft.Net.Component.4.5.2.TargetingPack | Balíček cílení .NET Framework 4.5.2 | 15.6.27406.0 | Doporučené
Sada Microsoft.Net.Component.4.5.TargetingPack | Balíček cílení rozhraní .NET Framework 4.5 | 15.6.27406.0 | Doporučené
Microsoft.Net.Component.4.6.1.SDK | Rozhraní .NET Framework 4.6.1 SDK | 15.6.27406.0 | Doporučené
Microsoft.Net.Component.4.6.1.TargetingPack | Balíček cílení rozhraní .NET Framework 4.6.1 | 15.6.27406.0 | Doporučené
Sada Microsoft.Net.Component.4.6.TargetingPack | Balíček cílení rozhraní .NET Framework 4.6 | 15.6.27406.0 | Doporučené
Sada Microsoft.Net.Component.4.TargetingPack | Balíček cílení rozhraní .NET Framework 4 | 15.6.27406.0 | Doporučené
Microsoft.Net.ComponentGroup.DevelopmentPředpoklads | Vývojové nástroje .NET Framework 4.6.1 | 15.8.27825.0 | Doporučené
Microsoft.Net.ComponentGroup.TargetingPacks.Common | .NET Framework 4 – 4.6 vývojové nástroje | 15.6.27406.0 | Doporučené
Microsoft.Net.core.component.Sdk.2.1 | Vývojové nástroje .NET Core 2.1 | 15.8.27924.0 | Doporučené
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Vývojové nástroje Azure | 15.9.28307.421 | Doporučené
Microsoft.VisualStudio.Component.Azure.ClientLibs | Knihovny Azure pro rozhraní .NET | 15.0.26208.0 | Doporučené
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Výpočetní emulátor Azure | 15.9.28307.421 | Doporučené
Microsoft.VisualStudio.Component.Azure.Storage.Emulátor | Emulátor úložiště Azure | 15.9.28125.51 | Doporučené
Microsoft.VisualStudio.Component.Azure.Waverton | Základní nástroje Cloudových služeb Azure | 15.9.28107.0 | Doporučené
Microsoft.VisualStudio.Component.Azure.Waverton.BuildTools | Nástroje pro vytváření cloudových služeb Azure | 15.7.27617.1 | Doporučené
Microsoft.VisualStudio.Component.CloudExplorer | Průzkumník cloudu | 15.9.28230.55 | Doporučené
Microsoft.VisualStudio.Component.Common.Azure.Tools | Nástroje pro konektivitu a publikování | 15.9.28107.0 | Doporučené
Microsoft.VisualStudio.Component.DockerTools | Kontejnerové vývojové nástroje | 15.8.27906.1 | Doporučené
Microsoft.VisualStudio.Component.DockerTools.BuildTools | Nástroje pro vývoj kontejnerů – nástroje pro vytváření | 15.7.27617.1 | Doporučené
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 15.0.26208.0 | Doporučené
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostika javascriptu | 15.8.27729.1 | Doporučené
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Podpora jazyka JavaScript a TypeScript | 15.9.28125.51 | Doporučené
Soubor Microsoft.VisualStudio.Component.ManagedDesktop.Core | Jádro spravovaného pracovního vytížení plochy | 15.8.27729.1 | Doporučené
Soubor Microsoft.VisualStudio.Component.NuGet | Správce balíčků NuGet | 15.9.28016.0 | Doporučené
Knihovna Microsoft.VisualStudio.Component.PortableLibrary | Balíček cílení na přenosnou knihovnu .NET | 15.6.27309.0 | Doporučené
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilátory Roslyn jazyka C# a Visual Basic | 15.6.27309.0 | Doporučené
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# a Visual Basic | 15.8.27729.1 | Doporučené
Microsoft.VisualStudio.Component.SQL.ADAL | Modul runtime SQL ADAL | 15.6.27406.0 | Doporučené
Microsoft.VisualStudio.Component.SQL.CLR | Datové typy CLR pro SQL Server | 15.0.26208.0 | Doporučené
Microsoft.VisualStudio.Component.SQL.CMDUtils | Nástroje příkazového řádku serveru SQL Server | 15.0.26208.0 | Doporučené
Microsoft.VisualStudio.Component.SQL.DataSources | Zdroje dat pro podporu serveru SQL Server | 15.0.26621.2 | Doporučené
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 15.7.27617.1 | Doporučené
Microsoft.VisualStudio.Component.SQL.NCLI | Nativní klient systému SQL Server | 15.0.26208.0 | Doporučené
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 15.9.28107.0 | Doporučené
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Nástroje statické analýzy | 15.0.26208.0 | Doporučené
Microsoft.VisualStudio.Component.TextTemplating | Transformace šablony textu | 15.0.26208.0 | Doporučené
Microsoft.VisualStudio.Component.TypeScript.3.1 | TypeScript 3.1 SDK | 15.0.28218.60 | Doporučené
Microsoft.VisualStudio.Component.VisualStudioData | Zdroje dat a odkazy na služby | 15.6.27406.0 | Doporučené
Microsoft.VisualStudio.Component.Web | ASP.NET a nástroje pro vývoj webových aplikací | 15.8.27825.0 | Doporučené
Microsoft.VisualStudio.ComponentGroup.Web | předpoklady pro ASP.NET a nástroje pro vývoj webových aplikací | 15.9.28219.51 | Doporučené
Rozšíření microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Vývoj pro ASP.NET a web | 15.8.27825.0 | Doporučené
Microsoft.VisualStudio.Component.FSharp.Desktop | Podpora jazyka pro stolní počítače F# | 15.8.27825.0 | Nepovinné

## <a name="data-science-and-analytical-applications"></a>Aplikace pro datové vědy a analýzy

**ID:** Microsoft.VisualStudio.Workload.DataScience

**Popis:** Jazyky a nástroje pro vytváření aplikací pro datové vědy, včetně Pythonu, R a F#.

### <a name="components-included-by-this-workload"></a>Komponenty zahrnuté do tohoto pracovního vytížení

ID součásti | Name (Název) | Version | Typ závislosti
--- | --- | --- | ---
Komponenta.Anakonda3.x64 | Anakonda3 64bitový (5.2.0) | 5.2.0 | Doporučené
Microsoft.Component.CookiecutterTools | Podpora pro Cookiecutter template | 15.0.26621.2 | Doporučené
Microsoft.Component.PythonTools | Podpora jazyka Pythonu | 15.0.26823.1 | Doporučené
Microsoft.Component.PythonTools.Web | Webová podpora pythonu | 15.9.28107.0 | Doporučené
Microsoft.Net.Component.4.6.1.TargetingPack | Balíček cílení rozhraní .NET Framework 4.6.1 | 15.6.27406.0 | Doporučené
Microsoft.VisualStudio.Component.Common.Azure.Tools | Nástroje pro konektivitu a publikování | 15.9.28107.0 | Doporučené
Microsoft.VisualStudio.Component.FSharp.Desktop | Podpora jazyka pro stolní počítače F# | 15.8.27825.0 | Doporučené
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Podpora jazyka JavaScript a TypeScript | 15.9.28125.51 | Doporučené
Soubor Microsoft.VisualStudio.Component.NuGet | Správce balíčků NuGet | 15.9.28016.0 | Doporučené
Microsoft.VisualStudio.Component.R.Open | Klient Microsoft R (3.3.2) | 15.6.27406.0 | Doporučené
Microsoft.VisualStudio.Component.RHost | Podpora runtime pro vývojové nástroje R | 15.6.27406.0 | Doporučené
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilátory Roslyn jazyka C# a Visual Basic | 15.6.27309.0 | Doporučené
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# a Visual Basic | 15.8.27729.1 | Doporučené
Microsoft.VisualStudio.Component.RTools | Podpora jazyka R | 15.0.26919.1 | Doporučené
Microsoft.VisualStudio.Component.SQL.CLR | Datové typy CLR pro SQL Server | 15.0.26208.0 | Doporučené
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Nástroje statické analýzy | 15.0.26208.0 | Doporučené
Microsoft.VisualStudio.Component.TypeScript.3.1 | TypeScript 3.1 SDK | 15.0.28218.60 | Doporučené
Microsoft.VisualStudio.Component.VisualStudioData | Zdroje dat a odkazy na služby | 15.6.27406.0 | Doporučené
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 15.8.27729.1 | Doporučené
Rozšíření microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Vývoj pro ASP.NET a web | 15.8.27825.0 | Doporučené
Komponenta.Anakonda2.x64 | Anakonda2 64bitový (5.2.0) | 5.2.0 | Nepovinné
Komponenta.Anakonda2.x86 | Anakonda2 32bitový (5.2.0) | 5.2.0 | Nepovinné
Komponenta.Anakonda3.x86 | Anakonda3 32bitový (5.2.0) | 5.2.0 | Nepovinné
Soubor Microsoft.Component.VC.Runtime.UCRTSDK | Windows Universal CRT SDK | 15.6.27309.0 | Nepovinné
Vývoj souboru Microsoft.ComponentGroup.PythonTools.NativeDevelopment | Nativní vývojové nástroje Pythonu | 15.9.28307.102 | Nepovinné
Microsoft.VisualStudio.Component.Graphics.Tools | Grafický ladicí program a profiler GPU pro DirectX | 15.6.27406.0 | Nepovinné
Microsoft.VisualStudio.Component.Graphics.Win81 | Grafické nástroje Windows 8.1 SDK | 15.6.27406.0 | Nepovinné
Microsoft.VisualStudio.Component.VC.140 | Sada nástrojů VC++ 2015.3 v14.00 (v140) pro stolní počítače | 15.7.27617.1 | Nepovinné
Microsoft.VisualStudio.Component.VC.CoreIde | Základní funkce Visual Studia C++ | 15.6.27406.0 | Nepovinné
Nástroje Microsoft.VisualStudio.Component.VC.DiagnosticTools | Nástroje pro profilování jazyka C++ | 15.0.26823.1 | Nepovinné
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | VC++ 2017 verze 15.9 v14.16 nejnovější nástroje v141 | 15.9.28230.55 | Nepovinné
Microsoft.VisualStudio.Component.Windows10SDK | Windows Universal C Runtime | 15.6.27406.0 | Nepovinné
Microsoft.VisualStudio.Component.Windows10SDK.17763 | Windows 10 SDK (10.0.17763.0) | 15.9.28307.102 | Nepovinné
Microsoft.VisualStudio.Component.Windows81SDK | Windows 8.1 SDK | 15.6.27406.0 | Nepovinné

## <a name="net-desktop-development"></a>Vývoj stolních počítačů .NET

**ID:** Microsoft.VisualStudio.Workload.ManagedDesktop

**Popis:** Vytvářejte aplikace WPF, Windows Forms a konzolové aplikace pomocí c#, visual basicu a f#.

### <a name="components-included-by-this-workload"></a>Komponenty zahrnuté do tohoto pracovního vytížení

ID součásti | Name (Název) | Version | Typ závislosti
--- | --- | --- | ---
Microsoft.Component.ClickOnce | Publikování clickonce | 15.8.27825.0 | Požaduje se
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | Požaduje se
Microsoft.Net.Component.4.6.1.SDK | Rozhraní .NET Framework 4.6.1 SDK | 15.6.27406.0 | Požaduje se
Microsoft.Net.Component.4.6.1.TargetingPack | Balíček cílení rozhraní .NET Framework 4.6.1 | 15.6.27406.0 | Požaduje se
Microsoft.Net.ComponentGroup.DevelopmentPředpoklads | Vývojové nástroje .NET Framework 4.6.1 | 15.8.27825.0 | Požaduje se
Soubor Microsoft.VisualStudio.Component.ManagedDesktop.Core | Jádro spravovaného pracovního vytížení plochy | 15.8.27729.1 | Požaduje se
Microsoft.VisualStudio.Component.ManagedDesktop.Prerequisites | Nástroje pro vývoj stolních počítačů .NET | 15.7.27625.0 | Požaduje se
Knihovna Microsoft.VisualStudio.Component.PortableLibrary | Balíček cílení na přenosnou knihovnu .NET | 15.6.27309.0 | Požaduje se
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilátory Roslyn jazyka C# a Visual Basic | 15.6.27309.0 | Požaduje se
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# a Visual Basic | 15.8.27729.1 | Požaduje se
Microsoft.VisualStudio.Component.SQL.CLR | Datové typy CLR pro SQL Server | 15.0.26208.0 | Požaduje se
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Nástroje statické analýzy | 15.0.26208.0 | Požaduje se
Microsoft.VisualStudio.Component.TextTemplating | Transformace šablony textu | 15.0.26208.0 | Požaduje se
Microsoft.VisualStudio.Component.VisualStudioData | Zdroje dat a odkazy na služby | 15.6.27406.0 | Požaduje se
Microsoft.ComponentGroup.Blend | Blend for Visual Studio | 15.6.27406.0 | Doporučené
Microsoft.Net.Component.4.5.1.TargetingPack | Balíček cílení v rámci .NET Framework 4.5.1 | 15.6.27406.0 | Doporučené
Microsoft.Net.Component.4.5.2.TargetingPack | Balíček cílení .NET Framework 4.5.2 | 15.6.27406.0 | Doporučené
Sada Microsoft.Net.Component.4.5.TargetingPack | Balíček cílení rozhraní .NET Framework 4.5 | 15.6.27406.0 | Doporučené
Sada Microsoft.Net.Component.4.6.TargetingPack | Balíček cílení rozhraní .NET Framework 4.6 | 15.6.27406.0 | Doporučené
Sada Microsoft.Net.Component.4.TargetingPack | Balíček cílení rozhraní .NET Framework 4 | 15.6.27406.0 | Doporučené
Microsoft.Net.ComponentGroup.TargetingPacks.Common | .NET Framework 4 – 4.6 vývojové nástroje | 15.6.27406.0 | Doporučené
Microsoft.VisualStudio.Component.Debugger.JustInTime | Ladicí program Just-In-Time | 15.0.27005.2 | Doporučené
Microsoft.VisualStudio.Component.EntityFramework | Nástroje entity Framework 6 | 15.6.27406.0 | Doporučené
Komponenta.Dotfuscator | PreEmptive Protection – Dotfuscator | 15.0.26208.0 | Nepovinné
Component.Microsoft.VisualStudio.RazorExtension | Razor Language Services | 15.0.26720.2 | Nepovinné
Component.Microsoft.Web.LibraryManager | Správce knihovny | 15.8.27705.0 | Nepovinné
Komponenta.WebSocket | WebSocket4Net | 15.0.26606.0 | Nepovinné
Microsoft.Net.Component.4.6.2.SDK | Rozhraní .NET Framework 4.6.2 SDK | 15.6.27406.0 | Nepovinné
Sada Microsoft.Net.Component.4.6.2.TargetingPack | Balíček cílení .NET Framework 4.6.2 | 15.6.27406.0 | Nepovinné
Microsoft.Net.Component.4.7.1.SDK | Rozhraní .NET Framework 4.7.1 SDK | 15.6.27406.0 | Nepovinné
Microsoft.Net.Component.4.7.1.TargetingPack | Balíček cílení .NET Framework 4.7.1 | 15.6.27406.0 | Nepovinné
Microsoft.Net.Component.4.7.2.SDK | Rozhraní .NET Framework 4.7.2 SDK | 15.8.27825.0 | Nepovinné
Microsoft.Net.Component.4.7.2.TargetingPack | Balíček cílení .NET Framework 4.7.2 | 15.8.27825.0 | Nepovinné
Sada Microsoft.Net.Component.4.7.SdK | Rozhraní .NET Framework 4.7 SDK | 15.6.27406.0 | Nepovinné
Sada Microsoft.Net.Component.4.7.TargetingPack | Balíček cílení rozhraní .NET Framework 4.7 | 15.6.27406.0 | Nepovinné
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | Vývojové nástroje .NET Framework 4.6.2 | 15.6.27406.0 | Nepovinné
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | Vývojové nástroje .NET Framework 4.7.1 | 15.6.27406.0 | Nepovinné
Microsoft.Net.ComponentGroup.4.7.2.DeveloperTools | Vývojové nástroje .NET Framework 4.7.2 | 15.8.27825.0 | Nepovinné
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | Vývojové nástroje rozhraní .NET Framework 4.7 | 15.6.27406.0 | Nepovinné
Soubor Microsoft.Net.core.component.SDK | Vývojové nástroje .NET Core 2.0 | 15.6.27406.0 | Nepovinné
Microsoft.Net.Core.Component.SDK.1x | .NET Core 1.0 - 1.1 vývojové nástroje | 15.6.27406.0 | Nepovinné
Microsoft.Net.core.component.Sdk.2.1 | Vývojové nástroje .NET Core 2.1 | 15.8.27924.0 | Nepovinné
Microsoft.Netcore.ComponentGroup.DevelopmentTools | Vývojové nástroje .NET Core 2.0 | 15.8.27729.1 | Nepovinné
Microsoft.NetCore.ComponentGroup.DevelopmentTools.2.1 | Vývojové nástroje .NET Core 2.1 | 15.8.27924.0 | Nepovinné
Microsoft.VisualStudio.Component.Common.Azure.Tools | Nástroje pro konektivitu a publikování | 15.9.28107.0 | Nepovinné
Microsoft.VisualStudio.Component.DockerTools | Kontejnerové vývojové nástroje | 15.8.27906.1 | Nepovinné
Microsoft.VisualStudio.Component.DockerTools.BuildTools | Nástroje pro vývoj kontejnerů – nástroje pro vytváření | 15.7.27617.1 | Nepovinné
Microsoft.VisualStudio.Component.FSharp | Podpora jazyka F# | 15.8.27825.0 | Nepovinné
Microsoft.VisualStudio.Component.FSharp.Desktop | Podpora jazyka pro stolní počítače F# | 15.8.27825.0 | Nepovinné
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 15.0.26208.0 | Nepovinné
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostika javascriptu | 15.8.27729.1 | Nepovinné
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Podpora jazyka JavaScript a TypeScript | 15.9.28125.51 | Nepovinné
Soubor Microsoft.VisualStudio.Component.NuGet | Správce balíčků NuGet | 15.9.28016.0 | Nepovinné
Microsoft.VisualStudio.Component.SQL.ADAL | Modul runtime SQL ADAL | 15.6.27406.0 | Nepovinné
Microsoft.VisualStudio.Component.SQL.CMDUtils | Nástroje příkazového řádku serveru SQL Server | 15.0.26208.0 | Nepovinné
Microsoft.VisualStudio.Component.SQL.DataSources | Zdroje dat pro podporu serveru SQL Server | 15.0.26621.2 | Nepovinné
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 15.7.27617.1 | Nepovinné
Microsoft.VisualStudio.Component.SQL.NCLI | Nativní klient systému SQL Server | 15.0.26208.0 | Nepovinné
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 15.9.28107.0 | Nepovinné
Microsoft.VisualStudio.Component.TypeScript.3.1 | TypeScript 3.1 SDK | 15.0.28218.60 | Nepovinné
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | 15.8.27924.0 | Nepovinné
Microsoft.VisualStudio.Component.Web | ASP.NET a nástroje pro vývoj webových aplikací | 15.8.27825.0 | Nepovinné
Microsoft.VisualStudio.ComponentGroup.Web | předpoklady pro ASP.NET a nástroje pro vývoj webových aplikací | 15.9.28219.51 | Nepovinné
Rozšíření microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Vývoj pro ASP.NET a web | 15.8.27825.0 | Nepovinné

## <a name="game-development-with-unity"></a>Vývoj her pomocí Unity

**ID:** Microsoft.VisualStudio.Workload.ManagedGame

**Popis:** Vytvářejte 2D a 3D hry s Unity, výkonným vývojovým prostředím napříč platformami.

### <a name="components-included-by-this-workload"></a>Komponenty zahrnuté do tohoto pracovního vytížení

ID součásti | Name (Název) | Version | Typ závislosti
--- | --- | --- | ---
Microsoft.Net.Component.3.5.DeveloperTools | Vývojové nástroje rozhraní .NET Framework 3.5 | 15.6.27406.0 | Požaduje se
Microsoft.Net.Component.4.7.1.TargetingPack | Balíček cílení .NET Framework 4.7.1 | 15.6.27406.0 | Požaduje se
Soubor Microsoft.VisualStudio.Component.NuGet | Správce balíčků NuGet | 15.9.28016.0 | Požaduje se
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilátory Roslyn jazyka C# a Visual Basic | 15.6.27309.0 | Požaduje se
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# a Visual Basic | 15.8.27729.1 | Požaduje se
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Nástroje statické analýzy | 15.0.26208.0 | Požaduje se
Microsoft.VisualStudio.Component.Unity | Visual Studio Tools for Unity | 15.7.27617.1 | Požaduje se
Component.UnityEngine.x64 | 64bitový editor Unity 2018.3 | 15.9.28307.271 | Doporučené
Component.UnityEngine.x86 | Unity 5,6 32bitový editor | 15.6.27406.0 | Doporučené

## <a name="linux-development-with-c"></a>Vývoj linuxových aplikací v jazyce C++

**ID:** Microsoft.VisualStudio.Workload.NativeCrossPlat

**Popis:** Vytvářejte a ladíte aplikace spuštěné v prostředí Linuxu.

### <a name="components-included-by-this-workload"></a>Komponenty zahrnuté do tohoto pracovního vytížení

ID součásti | Name (Název) | Version | Typ závislosti
--- | --- | --- | ---
Component.MDD.Linux | Visual C++ pro vývoj Linuxu | 15.6.27406.0 | Požaduje se
Microsoft.VisualStudio.Component.VC.CoreIde | Základní funkce Visual Studia C++ | 15.6.27406.0 | Požaduje se
Microsoft.VisualStudio.Component.Windows10SDK | Windows Universal C Runtime | 15.6.27406.0 | Požaduje se
Component.Linux.CMake | Nástroje Visual C++ pro CMake a Linux | 15.9.28307.102 | Doporučené
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Nástroje statické analýzy | 15.0.26208.0 | Doporučené
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | VC++ 2017 verze 15.9 v14.16 nejnovější nástroje v141 | 15.9.28230.55 | Doporučené
Microsoft.VisualStudio.Component.Windows10SDK.17763 | Windows 10 SDK (10.0.17763.0) | 15.9.28307.102 | Doporučené
Rozšíření microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Vývoj pro ASP.NET a web | 15.8.27825.0 | Doporučené
Component.MDD.Linux.GCC.arm | Vestavěný a vývoj IoT | 15.6.27309.0 | Nepovinné

## <a name="desktop-development-with-c"></a>Vývoj desktopových aplikací pomocí C++

**ID:** Microsoft.VisualStudio.Workload.NativeDesktop

**Popis:** Vytvářejte desktopové aplikace systému Windows pomocí sady nástrojů Microsoft C++, KNIHOVNY ATL nebo knihovny MFC.

### <a name="components-included-by-this-workload"></a>Komponenty zahrnuté do tohoto pracovního vytížení

ID součásti | Name (Název) | Version | Typ závislosti
--- | --- | --- | ---
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | Požaduje se
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilátory Roslyn jazyka C# a Visual Basic | 15.6.27309.0 | Požaduje se
Microsoft.VisualStudio.Component.TextTemplating | Transformace šablony textu | 15.0.26208.0 | Požaduje se
Microsoft.VisualStudio.Component.VC.CoreIde | Základní funkce Visual Studia C++ | 15.6.27406.0 | Požaduje se
Microsoft.VisualStudio.Component.VC.Redist.14.Latest | Aktualizace redistribuovatelné ho období 2017 visual c++ | 15.6.27406.0 | Požaduje se
Soubor Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Core | Základní desktopové funkce Visual C++ | 15.8.27729.1 | Požaduje se
Microsoft.VisualStudio.Component.Debugger.JustInTime | Ladicí program Just-In-Time | 15.0.27005.2 | Doporučené
Microsoft.VisualStudio.Component.Graphics.Tools | Grafický ladicí program a profiler GPU pro DirectX | 15.6.27406.0 | Doporučené
Microsoft.VisualStudio.Component.Graphics.Win81 | Grafické nástroje Windows 8.1 SDK | 15.6.27406.0 | Doporučené
Soubor Microsoft.VisualStudio.Component.NuGet | Správce balíčků NuGet | 15.9.28016.0 | Doporučené
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Nástroje statické analýzy | 15.0.26208.0 | Doporučené
Soubor Microsoft.VisualStudio.Component.VC.ATL | Visual C++ ATL pro x86 a x64 | 15.7.27625.0 | Doporučené
Microsoft.VisualStudio.Component.VC.Cmake.Project | Nástroje Visual C++ pro CMake | 15.9.28307.102 | Doporučené
Nástroje Microsoft.VisualStudio.Component.VC.DiagnosticTools | Nástroje pro profilování jazyka C++ | 15.0.26823.1 | Doporučené
Microsoft.VisualStudio.Component.VC.TestAdapterForBoostTest | Testovací adaptér pro boost.test | 15.8.27906.1 | Doporučené
Microsoft.VisualStudio.Component.VC.TestAdapterForGoogleTest | Testovací adaptér pro test Google | 15.8.27906.1 | Doporučené
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | VC++ 2017 verze 15.9 v14.16 nejnovější nástroje v141 | 15.9.28230.55 | Doporučené
Microsoft.VisualStudio.Component.Windows10SDK.17763 | Windows 10 SDK (10.0.17763.0) | 15.9.28307.102 | Doporučené
Rozšíření microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Vývoj pro ASP.NET a web | 15.8.27825.0 | Doporučené
Komponenta.Incredibuild | IncrediBuild - Zrychlení sestavení | 15.7.27617.1 | Nepovinné
Komponenta.IncredibuildMenu | Nabídka IncrediBuild | 1.5.0.2 | Nepovinné
Soubor Microsoft.Component.VC.Runtime.UCRTSDK | Windows Universal CRT SDK | 15.6.27309.0 | Nepovinné
Microsoft.Net.Component.4.6.1.SDK | Rozhraní .NET Framework 4.6.1 SDK | 15.6.27406.0 | Nepovinné
Microsoft.Net.Component.4.6.1.TargetingPack | Balíček cílení rozhraní .NET Framework 4.6.1 | 15.6.27406.0 | Nepovinné
Microsoft.VisualStudio.Component.VC.140 | Sada nástrojů VC++ 2015.3 v14.00 (v140) pro stolní počítače | 15.7.27617.1 | Nepovinné
Soubor Microsoft.VisualStudio.Component.VC.ATLMFC | Visual C++ MFC pro x86 a x64 | 15.7.27625.0 | Nepovinné
Microsoft.VisualStudio.Component.VC.CLI.Support | Podpora pro C++/CLI | 15.6.27309.0 | Nepovinné
Microsoft.VisualStudio.Component.VC.Modules.x86.x64 | Moduly pro standardní knihovnu (experimentální) | 15.6.27309.0 | Nepovinné
Microsoft.VisualStudio.Component.Windows10SDK.10240 | Windows 10 SDK (10.0.10240.0) | 15.6.27406.0 | Nepovinné
Microsoft.VisualStudio.Component.Windows10SDK.10586 | Windows 10 SDK (10.0.10586.0) | 15.6.27406.0 | Nepovinné
Microsoft.VisualStudio.Component.Windows10SDK.14393 | Windows 10 SDK (10.0.14393.0) | 15.6.27406.0 | Nepovinné
Microsoft.VisualStudio.Component.Windows10SDK.15063.desktop | Sada Windows 10 SDK (10.0.15063.0) pro stolní počítač C++ [x86 a x64] | 15.6.27406.0 | Nepovinné
Microsoft.VisualStudio.Component.Windows10SDK.15063.UWP | Windows 10 SDK (10.0.15063.0) pro UPW: C#, VB, JS | 15.6.27406.0 | Nepovinné
Microsoft.VisualStudio.Component.Windows10SDK.15063.uWP.Native | Windows 10 SDK (10.0.15063.0) pro UPW: C++ | 15.6.27406.0 | Nepovinné
Microsoft.VisualStudio.Component.Windows10SDK.16299.desktop | Sada Windows 10 SDK (10.0.16299.0) pro stolní počítač C++ [x86 a x64] | 15.6.27406.0 | Nepovinné
Microsoft.VisualStudio.Component.Windows10SDK.16299.Desktop.arm | Sada Windows 10 SDK (10.0.16299.0) pro stolní počítač C++ [ARM a ARM64] | 15.6.27406.0 | Nepovinné
Microsoft.VisualStudio.Component.Windows10SDK.16299.UWP | Windows 10 SDK (10.0.16299.0) pro UPW: C#, VB, JS | 15.6.27406.0 | Nepovinné
Microsoft.VisualStudio.Component.Windows10SDK.16299.uWP.Native | Windows 10 SDK (10.0.16299.0) pro UPW: C++ | 15.6.27406.0 | Nepovinné
Microsoft.VisualStudio.Component.Windows10SDK.17134 | Windows 10 SDK (10.0.17134.0) | 15.9.28307.102 | Nepovinné
Microsoft.VisualStudio.Component.Windows81SDK | Windows 8.1 SDK | 15.6.27406.0 | Nepovinné
Soubor Microsoft.VisualStudio.Component.WinXP | Podpora systému Windows XP pro jazyk C++ | 15.8.27924.0 | Nepovinné
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Win81 | Sada Windows 8.1 SDK a UCRT SDK | 15.6.27406.0 | Nepovinné
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.WinXP | Podpora systému Windows XP pro jazyk C++ | 15.8.27705.0 | Nepovinné
Microsoft.VisualStudio.ComponentGroup.Windows10SDK.15063 | Windows 10 SDK (10.0.15063.0) | 15.8.27825.0 | Nepovinné
Microsoft.VisualStudio.ComponentGroup.Windows10SDK.16299 | Windows 10 SDK (10.0.16299.0) | 15.8.27825.0 | Nepovinné

## <a name="game-development-with-c"></a>Vývoj her v jazyce C++

**ID:** Microsoft.VisualStudio.Workload.NativeGame

**Popis:** Využijte plný výkon c++ k vytváření profesionálních her poháněných rozhraními DirectX, Unreal nebo Cocos2d.

### <a name="components-included-by-this-workload"></a>Komponenty zahrnuté do tohoto pracovního vytížení

ID součásti | Name (Název) | Version | Typ závislosti
--- | --- | --- | ---
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Nástroje statické analýzy | 15.0.26208.0 | Požaduje se
Microsoft.VisualStudio.Component.VC.CoreIde | Základní funkce Visual Studia C++ | 15.6.27406.0 | Požaduje se
Microsoft.VisualStudio.Component.VC.Redist.14.Latest | Aktualizace redistribuovatelné ho období 2017 visual c++ | 15.6.27406.0 | Požaduje se
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | VC++ 2017 verze 15.9 v14.16 nejnovější nástroje v141 | 15.9.28230.55 | Požaduje se
Microsoft.VisualStudio.Component.Windows10SDK | Windows Universal C Runtime | 15.6.27406.0 | Požaduje se
Microsoft.VisualStudio.Component.Graphics.Tools | Grafický ladicí program a profiler GPU pro DirectX | 15.6.27406.0 | Doporučené
Microsoft.VisualStudio.Component.Graphics.Win81 | Grafické nástroje Windows 8.1 SDK | 15.6.27406.0 | Doporučené
Nástroje Microsoft.VisualStudio.Component.VC.DiagnosticTools | Nástroje pro profilování jazyka C++ | 15.0.26823.1 | Doporučené
Microsoft.VisualStudio.Component.Windows10SDK.17763 | Windows 10 SDK (10.0.17763.0) | 15.9.28307.102 | Doporučené
Komponenta.Android.NDK.R12B | Android NDK (R12B) | 12.1.10 | Nepovinné
komponent.android.SDK23.Private | Nastavení sady Android SDK (úroveň ROZHRANÍ API 23) (lokální instalace pro vývoj pro mobilní zařízení s JavaScriptem / C++) | 15.9.28016.0 | Nepovinné
Komponenta.Mat | Pašanek Apache (1.9.3) | 1.9.3.8 | Nepovinné
Component.Cocos | Cocos | 15.0.26906.1 | Nepovinné
Komponenta.Incredibuild | IncrediBuild - Zrychlení sestavení | 15.7.27617.1 | Nepovinné
Komponenta.IncredibuildMenu | Nabídka IncrediBuild | 1.5.0.2 | Nepovinné
Komponenta.MDD.Android | Vývojové nástroje pro Android pro C++ | 15.0.26606.0 | Nepovinné
komponenta OpenJDK | Microsoft distribuce OpenJDK | 15.9.28125.51 | Nepovinné
Komponenta.Nereálné | Instalátor unreal engine | 15.8.27729.1 | Nepovinné
Component.Unreal.Android | Podpora visual studia Android pro unreal engine | 15.9.28307.341 | Nepovinné
Soubor Microsoft.Component.VC.Runtime.UCRTSDK | Windows Universal CRT SDK | 15.6.27309.0 | Nepovinné
Microsoft.Net.Component.4.5.1.TargetingPack | Balíček cílení v rámci .NET Framework 4.5.1 | 15.6.27406.0 | Nepovinné
Microsoft.Net.Component.4.5.2.TargetingPack | Balíček cílení .NET Framework 4.5.2 | 15.6.27406.0 | Nepovinné
Sada Microsoft.Net.Component.4.5.TargetingPack | Balíček cílení rozhraní .NET Framework 4.5 | 15.6.27406.0 | Nepovinné
Microsoft.Net.Component.4.6.1.SDK | Rozhraní .NET Framework 4.6.1 SDK | 15.6.27406.0 | Nepovinné
Microsoft.Net.Component.4.6.1.TargetingPack | Balíček cílení rozhraní .NET Framework 4.6.1 | 15.6.27406.0 | Nepovinné
Sada Microsoft.Net.Component.4.6.TargetingPack | Balíček cílení rozhraní .NET Framework 4.6 | 15.6.27406.0 | Nepovinné
Sada Microsoft.Net.Component.4.TargetingPack | Balíček cílení rozhraní .NET Framework 4 | 15.6.27406.0 | Nepovinné
Microsoft.Net.ComponentGroup.DevelopmentPředpoklads | Vývojové nástroje .NET Framework 4.6.1 | 15.8.27825.0 | Nepovinné
Microsoft.Net.ComponentGroup.TargetingPacks.Common | .NET Framework 4 – 4.6 vývojové nástroje | 15.6.27406.0 | Nepovinné
Microsoft.VisualStudio.Component.NuGet.BuildTools | NuGet cíle a vytvářet úkoly | 15.9.28016.0 | Nepovinné
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilátory Roslyn jazyka C# a Visual Basic | 15.6.27309.0 | Nepovinné
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# a Visual Basic | 15.8.27729.1 | Nepovinné
Microsoft.VisualStudio.Component.Windows10SDK.10240 | Windows 10 SDK (10.0.10240.0) | 15.6.27406.0 | Nepovinné
Microsoft.VisualStudio.Component.Windows10SDK.10586 | Windows 10 SDK (10.0.10586.0) | 15.6.27406.0 | Nepovinné
Microsoft.VisualStudio.Component.Windows10SDK.14393 | Windows 10 SDK (10.0.14393.0) | 15.6.27406.0 | Nepovinné
Microsoft.VisualStudio.Component.Windows10SDK.15063.desktop | Sada Windows 10 SDK (10.0.15063.0) pro stolní počítač C++ [x86 a x64] | 15.6.27406.0 | Nepovinné
Microsoft.VisualStudio.Component.Windows10SDK.15063.UWP | Windows 10 SDK (10.0.15063.0) pro UPW: C#, VB, JS | 15.6.27406.0 | Nepovinné
Microsoft.VisualStudio.Component.Windows10SDK.15063.uWP.Native | Windows 10 SDK (10.0.15063.0) pro UPW: C++ | 15.6.27406.0 | Nepovinné
Microsoft.VisualStudio.Component.Windows10SDK.16299.desktop | Sada Windows 10 SDK (10.0.16299.0) pro stolní počítač C++ [x86 a x64] | 15.6.27406.0 | Nepovinné
Microsoft.VisualStudio.Component.Windows10SDK.16299.Desktop.arm | Sada Windows 10 SDK (10.0.16299.0) pro stolní počítač C++ [ARM a ARM64] | 15.6.27406.0 | Nepovinné
Microsoft.VisualStudio.Component.Windows10SDK.16299.UWP | Windows 10 SDK (10.0.16299.0) pro UPW: C#, VB, JS | 15.6.27406.0 | Nepovinné
Microsoft.VisualStudio.Component.Windows10SDK.16299.uWP.Native | Windows 10 SDK (10.0.16299.0) pro UPW: C++ | 15.6.27406.0 | Nepovinné
Microsoft.VisualStudio.Component.Windows10SDK.17134 | Windows 10 SDK (10.0.17134.0) | 15.9.28307.102 | Nepovinné
Microsoft.VisualStudio.Component.Windows81SDK | Windows 8.1 SDK | 15.6.27406.0 | Nepovinné
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Win81 | Sada Windows 8.1 SDK a UCRT SDK | 15.6.27406.0 | Nepovinné
Microsoft.VisualStudio.ComponentGroup.Windows10SDK.15063 | Windows 10 SDK (10.0.15063.0) | 15.8.27825.0 | Nepovinné
Microsoft.VisualStudio.ComponentGroup.Windows10SDK.16299 | Windows 10 SDK (10.0.16299.0) | 15.8.27825.0 | Nepovinné

## <a name="mobile-development-with-c"></a>Vývoj mobilních aplikací v jazyce C++

**ID:** Microsoft.VisualStudio.Workload.NativeMobile

**Popis:** Vytvářejte aplikace pro různé platformy pro iOS, Android nebo Windows pomocí C++.

### <a name="components-included-by-this-workload"></a>Komponenty zahrnuté do tohoto pracovního vytížení

ID součásti | Name (Název) | Version | Typ závislosti
--- | --- | --- | ---
komponent.android.SDK19.private | Nastavení sady Android SDK (úroveň ROZHRANÍ API 19) (lokální instalace pro vývoj pro mobilní zařízení s JavaScriptem / C++) | 15.9.28107.0 | Požaduje se
komponent.android.SDK21.Private | Nastavení sady Android SDK (úroveň ROZHRANÍ API 21) (lokální instalace pro vývoj pro mobilní zařízení s JavaScriptem / C++) | 15.9.28016.0 | Požaduje se
komponent.android.SDK22.Private | Nastavení sady Android SDK (úroveň ROZHRANÍ API 22) (lokální instalace pro vývoj pro mobilní zařízení s JavaScriptem / C++) | 15.9.28016.0 | Požaduje se
komponent.android.SDK23.Private | Nastavení sady Android SDK (úroveň ROZHRANÍ API 23) (lokální instalace pro vývoj pro mobilní zařízení s JavaScriptem / C++) | 15.9.28016.0 | Požaduje se
komponent.android.SDK25.Private | Nastavení sady Android SDK (úroveň ROZHRANÍ API 25) (lokální instalace pro vývoj pro mobilní zařízení s JavaScriptem / C++) | 15.9.28016.0 | Požaduje se
komponenta OpenJDK | Microsoft distribuce OpenJDK | 15.9.28125.51 | Požaduje se
Microsoft.VisualStudio.Component.VC.CoreIde | Základní funkce Visual Studia C++ | 15.6.27406.0 | Požaduje se
Komponenta.Android.NDK.R15C | Android NDK (R15C) | 15.2.1 | Doporučené
Komponenta.Mat | Pašanek Apache (1.9.3) | 1.9.3.8 | Doporučené
Komponenta.MDD.Android | Vývojové nástroje pro Android pro C++ | 15.0.26606.0 | Doporučené
Komponenta.Android.NDK.R12B | Android NDK (R12B) | 12.1.10 | Nepovinné
Komponenta.Android.NDK.R12B_3264 | Android NDK (R12B) (32bit) | 12.1.11 | Nepovinné
Komponenta.Android.NDK.R13B | Android NDK (R13B) | 13.1.7 | Nepovinné
Komponenta.Android.NDK.R13B_3264 | Android NDK (R13B) (32bit) | 13.1.8 | Nepovinné
Component.Android.NDK.R15C_3264 | Android NDK (R15C) (32bit) | 15.2.1 | Nepovinné
Komponenta.Google.Android.Emulator.API23.Private | Google Android Emulátor (API Úroveň 23) (místní instalace) | 15.6.27413.0 | Nepovinné
Component.HAXM.Private | Intel Hardware Accelerated Execution Manager (HAXM) (místní instalace) | 15.9.28307.421 | Nepovinné
Komponenta.Incredibuild | IncrediBuild - Zrychlení sestavení | 15.7.27617.1 | Nepovinné
Komponenta.IncredibuildMenu | Nabídka IncrediBuild | 1.5.0.2 | Nepovinné
Komponenta.MDD.iOS | Vývojové nástroje pro iOS v C++ | 15.0.26621.2 | Nepovinné

## <a name="net-core-cross-platform-development"></a>Vývoj aplikací pro různé platformy pomocí rozhraní .NET Core

**ID:** Microsoft.VisualStudio.Workload.NetCoreTools

**Popis:** Vytvářejte aplikace napříč platformami pomocí .NET Core, ASP.NET Core, HTML/JavaScript a kontejnery včetně podpory Dockeru.

### <a name="components-included-by-this-workload"></a>Komponenty zahrnuté do tohoto pracovního vytížení

ID součásti | Name (Název) | Version | Typ závislosti
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Razor Language Services | 15.0.26720.2 | Požaduje se
Component.Microsoft.Web.LibraryManager | Správce knihovny | 15.8.27705.0 | Požaduje se
Komponenta.WebSocket | WebSocket4Net | 15.0.26606.0 | Požaduje se
Microsoft.Component.ClickOnce | Publikování clickonce | 15.8.27825.0 | Požaduje se
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | Požaduje se
Microsoft.Net.Component.4.5.2.TargetingPack | Balíček cílení .NET Framework 4.5.2 | 15.6.27406.0 | Požaduje se
Sada Microsoft.Net.Component.4.5.TargetingPack | Balíček cílení rozhraní .NET Framework 4.5 | 15.6.27406.0 | Požaduje se
Microsoft.Net.Component.4.6.1.SDK | Rozhraní .NET Framework 4.6.1 SDK | 15.6.27406.0 | Požaduje se
Microsoft.Net.Component.4.6.1.TargetingPack | Balíček cílení rozhraní .NET Framework 4.6.1 | 15.6.27406.0 | Požaduje se
Microsoft.Net.ComponentGroup.DevelopmentPředpoklads | Vývojové nástroje .NET Framework 4.6.1 | 15.8.27825.0 | Požaduje se
Microsoft.Net.core.component.Sdk.2.1 | Vývojové nástroje .NET Core 2.1 | 15.8.27924.0 | Požaduje se
Microsoft.NetCore.ComponentGroup.DevelopmentTools.2.1 | Vývojové nástroje .NET Core 2.1 | 15.8.27924.0 | Požaduje se
Microsoft.NetCore.ComponentGroup.Web.2.1 | Vývojové nástroje .NET Core 2.1 | 15.8.27924.0 | Požaduje se
Microsoft.VisualStudio.Component.Common.Azure.Tools | Nástroje pro konektivitu a publikování | 15.9.28107.0 | Požaduje se
Microsoft.VisualStudio.Component.DockerTools | Kontejnerové vývojové nástroje | 15.8.27906.1 | Požaduje se
Microsoft.VisualStudio.Component.DockerTools.BuildTools | Nástroje pro vývoj kontejnerů – nástroje pro vytváření | 15.7.27617.1 | Požaduje se
Microsoft.VisualStudio.Component.FSharp | Podpora jazyka F# | 15.8.27825.0 | Požaduje se
Šablony Microsoft.VisualStudio.Component.FSharp.WebTemplates | Podpora jazyka F# pro webové projekty | 15.9.28307.421 | Požaduje se
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 15.0.26208.0 | Požaduje se
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostika javascriptu | 15.8.27729.1 | Požaduje se
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Podpora jazyka JavaScript a TypeScript | 15.9.28125.51 | Požaduje se
Soubor Microsoft.VisualStudio.Component.ManagedDesktop.Core | Jádro spravovaného pracovního vytížení plochy | 15.8.27729.1 | Požaduje se
Soubor Microsoft.VisualStudio.Component.NuGet | Správce balíčků NuGet | 15.9.28016.0 | Požaduje se
Knihovna Microsoft.VisualStudio.Component.PortableLibrary | Balíček cílení na přenosnou knihovnu .NET | 15.6.27309.0 | Požaduje se
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
Microsoft.VisualStudio.Component.TypeScript.3.1 | TypeScript 3.1 SDK | 15.0.28218.60 | Požaduje se
Microsoft.VisualStudio.Component.VisualStudioData | Zdroje dat a odkazy na služby | 15.6.27406.0 | Požaduje se
Microsoft.VisualStudio.ComponentGroup.Web | předpoklady pro ASP.NET a nástroje pro vývoj webových aplikací | 15.9.28219.51 | Požaduje se
Rozšíření microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Vývoj pro ASP.NET a web | 15.8.27825.0 | Požaduje se
Component.Microsoft.VisualStudio.Web.AzureFunkce | Nástroje pro webové úlohy Microsoft Azure | 15.7.27617.1 | Doporučené
Microsoft.VisualStudio.Component.AppInsights.Tools | Nástroje analýzy pro vývojáře | 15.8.27825.0 | Doporučené
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Vývojové nástroje Azure | 15.9.28307.421 | Doporučené
Microsoft.VisualStudio.Component.Azure.ClientLibs | Knihovny Azure pro rozhraní .NET | 15.0.26208.0 | Doporučené
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Výpočetní emulátor Azure | 15.9.28307.421 | Doporučené
Microsoft.VisualStudio.Component.Azure.Storage.Emulátor | Emulátor úložiště Azure | 15.9.28125.51 | Doporučené
Microsoft.VisualStudio.Component.CloudExplorer | Průzkumník cloudu | 15.9.28230.55 | Doporučené
Microsoft.VisualStudio.Component.DiagnosticTools | Nástroje profilování rozhraní .NET | 15.8.27729.1 | Doporučené
Microsoft.VisualStudio.Component.Web | ASP.NET a nástroje pro vývoj webových aplikací | 15.8.27825.0 | Doporučené
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 15.8.27729.1 | Doporučené
Funkce Microsoft.VisualStudio.ComponentGroup.Azure | Nástroje pro webové úlohy Microsoft Azure | 15.7.27617.1 | Doporučené
Microsoft.VisualStudio.ComponentGroup.Web.CloudTools | Cloudové nástroje pro vývoj webových aplikací | 15.8.27729.1 | Doporučené
Soubor Microsoft.Net.core.component.SDK | Vývojové nástroje .NET Core 2.0 | 15.6.27406.0 | Nepovinné
Microsoft.Net.Core.Component.SDK.1x | .NET Core 1.0 - 1.1 vývojové nástroje | 15.6.27406.0 | Nepovinné
Microsoft.NetCore.1x.ComponentGroup.Web | .NET Core 1.0 - 1.1 vývojové nástroje pro web | 15.6.27406.0 | Nepovinné
Microsoft.Netcore.ComponentGroup.DevelopmentTools | Vývojové nástroje .NET Core 2.0 | 15.8.27729.1 | Nepovinné
Microsoft.Netcore.ComponentGroup.Web | Vývojové nástroje .NET Core 2.0 | 15.7.27625.0 | Nepovinné
Vývoj souboru Microsoft.VisualStudio.ComponentGroup.IIS | Podpora služby IIS v době vývoje | 15.9.28219.51 | Nepovinné

## <a name="mobile-development-with-net"></a>Vývoj mobilních zařízení s rozhraním .NET

**ID:** Microsoft.VisualStudio.Workload.NetcrossPlat

**Popis:** Vytvářejte aplikace pro různé platformy pro iOS, Android nebo Windows pomocí Xamarinu.

### <a name="components-included-by-this-workload"></a>Komponenty zahrnuté do tohoto pracovního vytížení

ID součásti | Name (Název) | Version | Typ závislosti
--- | --- | --- | ---
Komponenta.Xamarin | Xamarin | 15.8.27906.1 | Požaduje se
Component.Xamarin.RemotedSimulator | Simulátor vzdáleného pohybu Xamarin | 15.6.27323.2 | Požaduje se
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | Požaduje se
Microsoft.Net.Component.4.6.1.SDK | Rozhraní .NET Framework 4.6.1 SDK | 15.6.27406.0 | Požaduje se
Microsoft.Net.Component.4.6.1.TargetingPack | Balíček cílení rozhraní .NET Framework 4.6.1 | 15.6.27406.0 | Požaduje se
Microsoft.Net.ComponentGroup.DevelopmentPředpoklads | Vývojové nástroje .NET Framework 4.6.1 | 15.8.27825.0 | Požaduje se
Soubor Microsoft.Net.core.component.SDK | Vývojové nástroje .NET Core 2.0 | 15.6.27406.0 | Požaduje se
Microsoft.Netcore.ComponentGroup.DevelopmentTools | Vývojové nástroje .NET Core 2.0 | 15.8.27729.1 | Požaduje se
Microsoft.VisualStudio.Component.FSharp | Podpora jazyka F# | 15.8.27825.0 | Požaduje se
Soubor Microsoft.VisualStudio.Component.Merq | Běžné interní nástroje Xamarin | 15.8.27924.0 | Požaduje se
Microsoft.VisualStudio.Component.MonoDebugger | Jednoladění | 15.0.26720.2 | Požaduje se
Soubor Microsoft.VisualStudio.Component.NuGet | Správce balíčků NuGet | 15.9.28016.0 | Požaduje se
Knihovna Microsoft.VisualStudio.Component.PortableLibrary | Balíček cílení na přenosnou knihovnu .NET | 15.6.27309.0 | Požaduje se
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilátory Roslyn jazyka C# a Visual Basic | 15.6.27309.0 | Požaduje se
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# a Visual Basic | 15.8.27729.1 | Požaduje se
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Nástroje statické analýzy | 15.0.26208.0 | Požaduje se
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions.TemplateEngine | ASP.NET templating motor | 15.8.27729.1 | Požaduje se
Komponenta.Android.SDK27 | Nastavení sady Android SDK (úroveň rozhraní API 27) | 15.9.28016.0 | Doporučené
Komponenta.Google.Android.Emulator.API27 | Google Android emulátor (API Úroveň 27) | 15.9.28307.421 | Doporučené
Komponenta.HAXM | Intel Hardware Accelerated Execution Manager (HAXM) (globální instalace) | 15.9.28307.421 | Doporučené
komponenta OpenJDK | Microsoft distribuce OpenJDK | 15.9.28125.51 | Doporučené
Component.Xamarin.Inspector | Sešity ke Xamarinu | 15.0.26606.0 | Nepovinné
Microsoft.Component.ClickOnce | Publikování clickonce | 15.8.27825.0 | Nepovinné
Microsoft.Component.NetFX.Nativní | .NET Native | 15.0.26208.0 | Nepovinné
Microsoft.VisualStudio.Component.AppInsights.Tools | Nástroje analýzy pro vývojáře | 15.8.27825.0 | Nepovinné
Microsoft.VisualStudio.Component.DiagnosticTools | Nástroje profilování rozhraní .NET | 15.8.27729.1 | Nepovinné
Microsoft.VisualStudio.Component.Graphics | Editory obrázků a 3D modelů | 15.6.27406.0 | Nepovinné
Microsoft.VisualStudio.Component.SQL.CLR | Datové typy CLR pro SQL Server | 15.0.26208.0 | Nepovinné
Microsoft.VisualStudio.Component.VisualStudioData | Zdroje dat a odkazy na služby | 15.6.27406.0 | Nepovinné
Microsoft.VisualStudio.Component.Windows10SDK.17763 | Windows 10 SDK (10.0.17763.0) | 15.9.28307.102 | Nepovinné
Microsoft.VisualStudio.ComponentGroup.UWP.Xamarin | Univerzální nástroje platformy Windows pro Xamarin | 15.9.28307.102 | Nepovinné

## <a name="aspnet-and-web-development"></a>Vývoj pro ASP.NET a web

**ID:** Microsoft.VisualStudio.Workload.NetWeb

**Popis:** Vytvářejte webové aplikace pomocí ASP.NET, ASP.NET jádra, HTML/JavaScriptu a kontejnerů včetně podpory Dockeru.

### <a name="components-included-by-this-workload"></a>Komponenty zahrnuté do tohoto pracovního vytížení

ID součásti | Name (Název) | Version | Typ závislosti
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Razor Language Services | 15.0.26720.2 | Požaduje se
Component.Microsoft.Web.LibraryManager | Správce knihovny | 15.8.27705.0 | Požaduje se
Komponenta.WebSocket | WebSocket4Net | 15.0.26606.0 | Požaduje se
Microsoft.Component.ClickOnce | Publikování clickonce | 15.8.27825.0 | Požaduje se
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | Požaduje se
Microsoft.Net.Component.4.5.2.TargetingPack | Balíček cílení .NET Framework 4.5.2 | 15.6.27406.0 | Požaduje se
Sada Microsoft.Net.Component.4.5.TargetingPack | Balíček cílení rozhraní .NET Framework 4.5 | 15.6.27406.0 | Požaduje se
Microsoft.Net.Component.4.6.1.SDK | Rozhraní .NET Framework 4.6.1 SDK | 15.6.27406.0 | Požaduje se
Microsoft.Net.Component.4.6.1.TargetingPack | Balíček cílení rozhraní .NET Framework 4.6.1 | 15.6.27406.0 | Požaduje se
Microsoft.Net.ComponentGroup.DevelopmentPředpoklads | Vývojové nástroje .NET Framework 4.6.1 | 15.8.27825.0 | Požaduje se
Microsoft.Net.core.component.Sdk.2.1 | Vývojové nástroje .NET Core 2.1 | 15.8.27924.0 | Požaduje se
Microsoft.NetCore.ComponentGroup.DevelopmentTools.2.1 | Vývojové nástroje .NET Core 2.1 | 15.8.27924.0 | Požaduje se
Microsoft.NetCore.ComponentGroup.Web.2.1 | Vývojové nástroje .NET Core 2.1 | 15.8.27924.0 | Požaduje se
Microsoft.VisualStudio.Component.Common.Azure.Tools | Nástroje pro konektivitu a publikování | 15.9.28107.0 | Požaduje se
Microsoft.VisualStudio.Component.DockerTools | Kontejnerové vývojové nástroje | 15.8.27906.1 | Požaduje se
Microsoft.VisualStudio.Component.DockerTools.BuildTools | Nástroje pro vývoj kontejnerů – nástroje pro vytváření | 15.7.27617.1 | Požaduje se
Microsoft.VisualStudio.Component.FSharp | Podpora jazyka F# | 15.8.27825.0 | Požaduje se
Šablony Microsoft.VisualStudio.Component.FSharp.WebTemplates | Podpora jazyka F# pro webové projekty | 15.9.28307.421 | Požaduje se
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 15.0.26208.0 | Požaduje se
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostika javascriptu | 15.8.27729.1 | Požaduje se
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Podpora jazyka JavaScript a TypeScript | 15.9.28125.51 | Požaduje se
Soubor Microsoft.VisualStudio.Component.ManagedDesktop.Core | Jádro spravovaného pracovního vytížení plochy | 15.8.27729.1 | Požaduje se
Soubor Microsoft.VisualStudio.Component.NuGet | Správce balíčků NuGet | 15.9.28016.0 | Požaduje se
Knihovna Microsoft.VisualStudio.Component.PortableLibrary | Balíček cílení na přenosnou knihovnu .NET | 15.6.27309.0 | Požaduje se
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
Microsoft.VisualStudio.Component.TypeScript.3.1 | TypeScript 3.1 SDK | 15.0.28218.60 | Požaduje se
Microsoft.VisualStudio.Component.VisualStudioData | Zdroje dat a odkazy na služby | 15.6.27406.0 | Požaduje se
Microsoft.VisualStudio.Component.Web | ASP.NET a nástroje pro vývoj webových aplikací | 15.8.27825.0 | Požaduje se
Microsoft.VisualStudio.ComponentGroup.Web | předpoklady pro ASP.NET a nástroje pro vývoj webových aplikací | 15.9.28219.51 | Požaduje se
Rozšíření microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Vývoj pro ASP.NET a web | 15.8.27825.0 | Požaduje se
Component.Microsoft.VisualStudio.Web.AzureFunkce | Nástroje pro webové úlohy Microsoft Azure | 15.7.27617.1 | Doporučené
Microsoft.Net.Component.4.5.1.TargetingPack | Balíček cílení v rámci .NET Framework 4.5.1 | 15.6.27406.0 | Doporučené
Sada Microsoft.Net.Component.4.6.TargetingPack | Balíček cílení rozhraní .NET Framework 4.6 | 15.6.27406.0 | Doporučené
Sada Microsoft.Net.Component.4.TargetingPack | Balíček cílení rozhraní .NET Framework 4 | 15.6.27406.0 | Doporučené
Microsoft.Net.ComponentGroup.TargetingPacks.Common | .NET Framework 4 – 4.6 vývojové nástroje | 15.6.27406.0 | Doporučené
Microsoft.VisualStudio.Component.AppInsights.Tools | Nástroje analýzy pro vývojáře | 15.8.27825.0 | Doporučené
Microsoft.VisualStudio.Component.AspNet45 | Pokročilé ASP.NET funkce | 15.7.27625.0 | Doporučené
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Vývojové nástroje Azure | 15.9.28307.421 | Doporučené
Microsoft.VisualStudio.Component.Azure.ClientLibs | Knihovny Azure pro rozhraní .NET | 15.0.26208.0 | Doporučené
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Výpočetní emulátor Azure | 15.9.28307.421 | Doporučené
Microsoft.VisualStudio.Component.Azure.Storage.Emulátor | Emulátor úložiště Azure | 15.9.28125.51 | Doporučené
Microsoft.VisualStudio.Component.CloudExplorer | Průzkumník cloudu | 15.9.28230.55 | Doporučené
Microsoft.VisualStudio.Component.DiagnosticTools | Nástroje profilování rozhraní .NET | 15.8.27729.1 | Doporučené
Microsoft.VisualStudio.Component.EntityFramework | Nástroje entity Framework 6 | 15.6.27406.0 | Doporučené
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | 15.8.27924.0 | Doporučené
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 15.8.27729.1 | Doporučené
Funkce Microsoft.VisualStudio.ComponentGroup.Azure | Nástroje pro webové úlohy Microsoft Azure | 15.7.27617.1 | Doporučené
Microsoft.VisualStudio.ComponentGroup.Web.CloudTools | Cloudové nástroje pro vývoj webových aplikací | 15.8.27729.1 | Doporučené
Microsoft.Net.Component.4.6.2.SDK | Rozhraní .NET Framework 4.6.2 SDK | 15.6.27406.0 | Nepovinné
Sada Microsoft.Net.Component.4.6.2.TargetingPack | Balíček cílení .NET Framework 4.6.2 | 15.6.27406.0 | Nepovinné
Microsoft.Net.Component.4.7.1.SDK | Rozhraní .NET Framework 4.7.1 SDK | 15.6.27406.0 | Nepovinné
Microsoft.Net.Component.4.7.1.TargetingPack | Balíček cílení .NET Framework 4.7.1 | 15.6.27406.0 | Nepovinné
Microsoft.Net.Component.4.7.2.SDK | Rozhraní .NET Framework 4.7.2 SDK | 15.8.27825.0 | Nepovinné
Microsoft.Net.Component.4.7.2.TargetingPack | Balíček cílení .NET Framework 4.7.2 | 15.8.27825.0 | Nepovinné
Sada Microsoft.Net.Component.4.7.SdK | Rozhraní .NET Framework 4.7 SDK | 15.6.27406.0 | Nepovinné
Sada Microsoft.Net.Component.4.7.TargetingPack | Balíček cílení rozhraní .NET Framework 4.7 | 15.6.27406.0 | Nepovinné
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | Vývojové nástroje .NET Framework 4.6.2 | 15.6.27406.0 | Nepovinné
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | Vývojové nástroje .NET Framework 4.7.1 | 15.6.27406.0 | Nepovinné
Microsoft.Net.ComponentGroup.4.7.2.DeveloperTools | Vývojové nástroje .NET Framework 4.7.2 | 15.8.27825.0 | Nepovinné
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | Vývojové nástroje rozhraní .NET Framework 4.7 | 15.6.27406.0 | Nepovinné
Soubor Microsoft.Net.core.component.SDK | Vývojové nástroje .NET Core 2.0 | 15.6.27406.0 | Nepovinné
Microsoft.Net.Core.Component.SDK.1x | .NET Core 1.0 - 1.1 vývojové nástroje | 15.6.27406.0 | Nepovinné
Microsoft.NetCore.1x.ComponentGroup.Web | .NET Core 1.0 - 1.1 vývojové nástroje pro web | 15.6.27406.0 | Nepovinné
Microsoft.Netcore.ComponentGroup.DevelopmentTools | Vývojové nástroje .NET Core 2.0 | 15.8.27729.1 | Nepovinné
Microsoft.Netcore.ComponentGroup.Web | Vývojové nástroje .NET Core 2.0 | 15.7.27625.0 | Nepovinné
Vývoj souboru Microsoft.VisualStudio.ComponentGroup.IIS | Podpora služby IIS v době vývoje | 15.9.28219.51 | Nepovinné
Microsoft.VisualStudio.Web.Mvc4.ComponentGroup | ASP.NET MVC 4 | 15.6.27406.0 | Nepovinné

## <a name="nodejs-development"></a>Vývoj souboru Node.js

**ID:** Uzel Microsoft.VisualStudio.Workload.Node

**Popis:** Vytvářejte škálovatelné síťové aplikace pomocí souboru Node.js, což je asynchronní modul javascriptu řízený událostmi. 

### <a name="components-included-by-this-workload"></a>Komponenty zahrnuté do tohoto pracovního vytížení

ID součásti | Name (Název) | Version | Typ závislosti
--- | --- | --- | ---
Komponenta.WebSocket | WebSocket4Net | 15.0.26606.0 | Požaduje se
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostika javascriptu | 15.8.27729.1 | Požaduje se
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Podpora jazyka JavaScript a TypeScript | 15.9.28125.51 | Požaduje se
Microsoft.VisualStudio.Component.Node.Build | Podpora node.js MSBuild | 15.8.27825.0 | Požaduje se
Microsoft.VisualStudio.Component.Node.Tools | Podpora vývoje node.js | 15.8.27825.0 | Požaduje se
Soubor Microsoft.VisualStudio.Component.NuGet | Správce balíčků NuGet | 15.9.28016.0 | Požaduje se
Microsoft.VisualStudio.Component.TestTools.Core | Základní funkce nástrojů pro testování | 15.7.27520.0 | Požaduje se
Microsoft.VisualStudio.Component.TypeScript.3.1 | TypeScript 3.1 SDK | 15.0.28218.60 | Požaduje se
Rozšíření microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Vývoj pro ASP.NET a web | 15.8.27825.0 | Požaduje se
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 15.8.27729.1 | Doporučené
Microsoft.VisualStudio.Component.AppInsights.Tools | Nástroje analýzy pro vývojáře | 15.8.27825.0 | Nepovinné
Microsoft.VisualStudio.Component.Common.Azure.Tools | Nástroje pro konektivitu a publikování | 15.9.28107.0 | Nepovinné
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Nástroje statické analýzy | 15.0.26208.0 | Nepovinné
Microsoft.VisualStudio.Component.VC.CoreIde | Základní funkce Visual Studia C++ | 15.6.27406.0 | Nepovinné
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | VC++ 2017 verze 15.9 v14.16 nejnovější nástroje v141 | 15.9.28230.55 | Nepovinné

## <a name="officesharepoint-development"></a>Vývoj Office/SharePointu

**ID:** Microsoft.VisualStudio.Workload.Office

**Popis:** Vytvořte doplňky Office a SharePointu, sharepointová řešení a doplňky VSTO pomocí C#, VB a JavaScriptu.

### <a name="components-included-by-this-workload"></a>Komponenty zahrnuté do tohoto pracovního vytížení

ID součásti | Name (Název) | Version | Typ závislosti
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Razor Language Services | 15.0.26720.2 | Požaduje se
Component.Microsoft.Web.LibraryManager | Správce knihovny | 15.8.27705.0 | Požaduje se
Komponenta.WebSocket | WebSocket4Net | 15.0.26606.0 | Požaduje se
Microsoft.Component.ClickOnce | Publikování clickonce | 15.8.27825.0 | Požaduje se
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | Požaduje se
Microsoft.Net.Component.4.5.2.TargetingPack | Balíček cílení .NET Framework 4.5.2 | 15.6.27406.0 | Požaduje se
Sada Microsoft.Net.Component.4.5.TargetingPack | Balíček cílení rozhraní .NET Framework 4.5 | 15.6.27406.0 | Požaduje se
Microsoft.Net.Component.4.6.1.SDK | Rozhraní .NET Framework 4.6.1 SDK | 15.6.27406.0 | Požaduje se
Microsoft.Net.Component.4.6.1.TargetingPack | Balíček cílení rozhraní .NET Framework 4.6.1 | 15.6.27406.0 | Požaduje se
Sada Microsoft.Net.Component.4.TargetingPack | Balíček cílení rozhraní .NET Framework 4 | 15.6.27406.0 | Požaduje se
Microsoft.Net.ComponentGroup.DevelopmentPředpoklads | Vývojové nástroje .NET Framework 4.6.1 | 15.8.27825.0 | Požaduje se
Microsoft.Net.core.component.Sdk.2.1 | Vývojové nástroje .NET Core 2.1 | 15.8.27924.0 | Požaduje se
Microsoft.VisualStudio.Component.AppInsights.Tools | Nástroje analýzy pro vývojáře | 15.8.27825.0 | Požaduje se
Microsoft.VisualStudio.Component.Common.Azure.Tools | Nástroje pro konektivitu a publikování | 15.9.28107.0 | Požaduje se
Microsoft.VisualStudio.Component.DockerTools | Kontejnerové vývojové nástroje | 15.8.27906.1 | Požaduje se
Microsoft.VisualStudio.Component.DockerTools.BuildTools | Nástroje pro vývoj kontejnerů – nástroje pro vytváření | 15.7.27617.1 | Požaduje se
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 15.0.26208.0 | Požaduje se
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostika javascriptu | 15.8.27729.1 | Požaduje se
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Podpora jazyka JavaScript a TypeScript | 15.9.28125.51 | Požaduje se
Soubor Microsoft.VisualStudio.Component.ManagedDesktop.Core | Jádro spravovaného pracovního vytížení plochy | 15.8.27729.1 | Požaduje se
Microsoft.VisualStudio.Component.ManagedDesktop.Prerequisites | Nástroje pro vývoj stolních počítačů .NET | 15.7.27625.0 | Požaduje se
Soubor Microsoft.VisualStudio.Component.NuGet | Správce balíčků NuGet | 15.9.28016.0 | Požaduje se
Knihovna Microsoft.VisualStudio.Component.PortableLibrary | Balíček cílení na přenosnou knihovnu .NET | 15.6.27309.0 | Požaduje se
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilátory Roslyn jazyka C# a Visual Basic | 15.6.27309.0 | Požaduje se
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# a Visual Basic | 15.8.27729.1 | Požaduje se
Microsoft.VisualStudio.Component.Sharepoint.Tools | Office Developer Tools for Visual Studio | 15.8.27924.0 | Požaduje se
Microsoft.VisualStudio.Component.SQL.ADAL | Modul runtime SQL ADAL | 15.6.27406.0 | Požaduje se
Microsoft.VisualStudio.Component.SQL.CLR | Datové typy CLR pro SQL Server | 15.0.26208.0 | Požaduje se
Microsoft.VisualStudio.Component.SQL.CMDUtils | Nástroje příkazového řádku serveru SQL Server | 15.0.26208.0 | Požaduje se
Microsoft.VisualStudio.Component.SQL.DataSources | Zdroje dat pro podporu serveru SQL Server | 15.0.26621.2 | Požaduje se
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 15.7.27617.1 | Požaduje se
Microsoft.VisualStudio.Component.SQL.NCLI | Nativní klient systému SQL Server | 15.0.26208.0 | Požaduje se
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 15.9.28107.0 | Požaduje se
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Nástroje statické analýzy | 15.0.26208.0 | Požaduje se
Microsoft.VisualStudio.Component.TextTemplating | Transformace šablony textu | 15.0.26208.0 | Požaduje se
Microsoft.VisualStudio.Component.TypeScript.3.1 | TypeScript 3.1 SDK | 15.0.28218.60 | Požaduje se
Microsoft.VisualStudio.Component.VisualStudioData | Zdroje dat a odkazy na služby | 15.6.27406.0 | Požaduje se
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | 15.8.27924.0 | Požaduje se
Microsoft.VisualStudio.Component.Web | ASP.NET a nástroje pro vývoj webových aplikací | 15.8.27825.0 | Požaduje se
Microsoft.VisualStudio.Component.Workflow | Windows Workflow Foundation | 15.8.27825.0 | Požaduje se
Microsoft.VisualStudio.ComponentGroup.Web | předpoklady pro ASP.NET a nástroje pro vývoj webových aplikací | 15.9.28219.51 | Požaduje se
Rozšíření microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Vývoj pro ASP.NET a web | 15.8.27825.0 | Požaduje se
Microsoft.VisualStudio.Component.TeamOffice | Nástroje Visual Studia pro Office (VSTO) | 15.7.27625.0 | Doporučené
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 15.8.27729.1 | Doporučené
Microsoft.Net.Component.4.6.2.SDK | Rozhraní .NET Framework 4.6.2 SDK | 15.6.27406.0 | Nepovinné
Sada Microsoft.Net.Component.4.6.2.TargetingPack | Balíček cílení .NET Framework 4.6.2 | 15.6.27406.0 | Nepovinné
Microsoft.Net.Component.4.7.1.SDK | Rozhraní .NET Framework 4.7.1 SDK | 15.6.27406.0 | Nepovinné
Microsoft.Net.Component.4.7.1.TargetingPack | Balíček cílení .NET Framework 4.7.1 | 15.6.27406.0 | Nepovinné
Microsoft.Net.Component.4.7.2.SDK | Rozhraní .NET Framework 4.7.2 SDK | 15.8.27825.0 | Nepovinné
Microsoft.Net.Component.4.7.2.TargetingPack | Balíček cílení .NET Framework 4.7.2 | 15.8.27825.0 | Nepovinné
Sada Microsoft.Net.Component.4.7.SdK | Rozhraní .NET Framework 4.7 SDK | 15.6.27406.0 | Nepovinné
Sada Microsoft.Net.Component.4.7.TargetingPack | Balíček cílení rozhraní .NET Framework 4.7 | 15.6.27406.0 | Nepovinné
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | Vývojové nástroje .NET Framework 4.6.2 | 15.6.27406.0 | Nepovinné
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | Vývojové nástroje .NET Framework 4.7.1 | 15.6.27406.0 | Nepovinné
Microsoft.Net.ComponentGroup.4.7.2.DeveloperTools | Vývojové nástroje .NET Framework 4.7.2 | 15.8.27825.0 | Nepovinné
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | Vývojové nástroje rozhraní .NET Framework 4.7 | 15.6.27406.0 | Nepovinné

## <a name="python-development"></a>Vývoj Pythonu

**ID:** Microsoft.VisualStudio.Workload.Python

**Popis:** Editace, ladění, interaktivní vývoj a směřování zdrojů pro Python.

### <a name="components-included-by-this-workload"></a>Komponenty zahrnuté do tohoto pracovního vytížení

ID součásti | Name (Název) | Version | Typ závislosti
--- | --- | --- | ---
Microsoft.Component.PythonTools | Podpora jazyka Pythonu | 15.0.26823.1 | Požaduje se
Component.CPython3.x64 | Python 3 64bitový (3.6.6) | 3.6.6 | Doporučené
Microsoft.Component.CookiecutterTools | Podpora pro Cookiecutter template | 15.0.26621.2 | Doporučené
Microsoft.Component.PythonTools.Web | Webová podpora pythonu | 15.9.28107.0 | Doporučené
Microsoft.VisualStudio.Component.Common.Azure.Tools | Nástroje pro konektivitu a publikování | 15.9.28107.0 | Doporučené
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Podpora jazyka JavaScript a TypeScript | 15.9.28125.51 | Doporučené
Microsoft.VisualStudio.Component.SQL.CLR | Datové typy CLR pro SQL Server | 15.0.26208.0 | Doporučené
Microsoft.VisualStudio.Component.TypeScript.3.1 | TypeScript 3.1 SDK | 15.0.28218.60 | Doporučené
Microsoft.VisualStudio.Component.VisualStudioData | Zdroje dat a odkazy na služby | 15.6.27406.0 | Doporučené
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 15.8.27729.1 | Doporučené
Rozšíření microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Vývoj pro ASP.NET a web | 15.8.27825.0 | Doporučené
Komponenta.Anakonda2.x64 | Anakonda2 64bitový (5.2.0) | 5.2.0 | Nepovinné
Komponenta.Anakonda2.x86 | Anakonda2 32bitový (5.2.0) | 5.2.0 | Nepovinné
Komponenta.Anakonda3.x64 | Anakonda3 64bitový (5.2.0) | 5.2.0 | Nepovinné
Komponenta.Anakonda3.x86 | Anakonda3 32bitový (5.2.0) | 5.2.0 | Nepovinné
Komponenta.CPython2.x64 | Python 2 64bitový (2.7.14) | 2.7.14 | Nepovinné
Component.CPython2.x86 | Python 2 32bitový (2.7.14) | 2.7.14 | Nepovinné
Component.CPython3.x86 | Python 3 32bitový (3.6.6) | 3.6.6 | Nepovinné
Component.Microsoft.VisualStudio.RazorExtension | Razor Language Services | 15.0.26720.2 | Nepovinné
Component.Microsoft.Web.LibraryManager | Správce knihovny | 15.8.27705.0 | Nepovinné
Komponenta.WebSocket | WebSocket4Net | 15.0.26606.0 | Nepovinné
Microsoft.Component.ClickOnce | Publikování clickonce | 15.8.27825.0 | Nepovinné
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | Nepovinné
Microsoft.Component.NetFX.Nativní | .NET Native | 15.0.26208.0 | Nepovinné
Microsoft.Component.PythonTools.UWP | Podpora pro Python IoT | 15.0.26606.0 | Nepovinné
Soubor Microsoft.Component.VC.Runtime.UCRTSDK | Windows Universal CRT SDK | 15.6.27309.0 | Nepovinné
Vývoj souboru Microsoft.ComponentGroup.PythonTools.NativeDevelopment | Nativní vývojové nástroje Pythonu | 15.9.28307.102 | Nepovinné
Microsoft.Net.Component.4.5.2.TargetingPack | Balíček cílení .NET Framework 4.5.2 | 15.6.27406.0 | Nepovinné
Sada Microsoft.Net.Component.4.5.TargetingPack | Balíček cílení rozhraní .NET Framework 4.5 | 15.6.27406.0 | Nepovinné
Microsoft.Net.Component.4.6.1.SDK | Rozhraní .NET Framework 4.6.1 SDK | 15.6.27406.0 | Nepovinné
Microsoft.Net.Component.4.6.1.TargetingPack | Balíček cílení rozhraní .NET Framework 4.6.1 | 15.6.27406.0 | Nepovinné
Microsoft.Net.ComponentGroup.DevelopmentPředpoklads | Vývojové nástroje .NET Framework 4.6.1 | 15.8.27825.0 | Nepovinné
Microsoft.Net.core.component.Sdk.2.1 | Vývojové nástroje .NET Core 2.1 | 15.8.27924.0 | Nepovinné
Microsoft.VisualStudio.Component.AppInsights.Tools | Nástroje analýzy pro vývojáře | 15.8.27825.0 | Nepovinné
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Vývojové nástroje Azure | 15.9.28307.421 | Nepovinné
Microsoft.VisualStudio.Component.Azure.ClientLibs | Knihovny Azure pro rozhraní .NET | 15.0.26208.0 | Nepovinné
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Výpočetní emulátor Azure | 15.9.28307.421 | Nepovinné
Microsoft.VisualStudio.Component.Azure.Storage.Emulátor | Emulátor úložiště Azure | 15.9.28125.51 | Nepovinné
Microsoft.VisualStudio.Component.Azure.Waverton | Základní nástroje Cloudových služeb Azure | 15.9.28107.0 | Nepovinné
Microsoft.VisualStudio.Component.Azure.Waverton.BuildTools | Nástroje pro vytváření cloudových služeb Azure | 15.7.27617.1 | Nepovinné
Microsoft.VisualStudio.Component.ClassDesigner | Návrhář tříd | 15.0.26208.0 | Nepovinné
Microsoft.VisualStudio.Component.DiagnosticTools | Nástroje profilování rozhraní .NET | 15.8.27729.1 | Nepovinné
Microsoft.VisualStudio.Component.DockerTools | Kontejnerové vývojové nástroje | 15.8.27906.1 | Nepovinné
Microsoft.VisualStudio.Component.DockerTools.BuildTools | Nástroje pro vývoj kontejnerů – nástroje pro vytváření | 15.7.27617.1 | Nepovinné
Microsoft.VisualStudio.Component.Graphics | Editory obrázků a 3D modelů | 15.6.27406.0 | Nepovinné
Microsoft.VisualStudio.Component.Graphics.Tools | Grafický ladicí program a profiler GPU pro DirectX | 15.6.27406.0 | Nepovinné
Microsoft.VisualStudio.Component.Graphics.Win81 | Grafické nástroje Windows 8.1 SDK | 15.6.27406.0 | Nepovinné
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 15.0.26208.0 | Nepovinné
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostika javascriptu | 15.8.27729.1 | Nepovinné
Soubor Microsoft.VisualStudio.Component.ManagedDesktop.Core | Jádro spravovaného pracovního vytížení plochy | 15.8.27729.1 | Nepovinné
Soubor Microsoft.VisualStudio.Component.NuGet | Správce balíčků NuGet | 15.9.28016.0 | Nepovinné
Knihovna Microsoft.VisualStudio.Component.PortableLibrary | Balíček cílení na přenosnou knihovnu .NET | 15.6.27309.0 | Nepovinné
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilátory Roslyn jazyka C# a Visual Basic | 15.6.27309.0 | Nepovinné
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# a Visual Basic | 15.8.27729.1 | Nepovinné
Microsoft.VisualStudio.Component.SQL.ADAL | Modul runtime SQL ADAL | 15.6.27406.0 | Nepovinné
Microsoft.VisualStudio.Component.SQL.CMDUtils | Nástroje příkazového řádku serveru SQL Server | 15.0.26208.0 | Nepovinné
Microsoft.VisualStudio.Component.SQL.DataSources | Zdroje dat pro podporu serveru SQL Server | 15.0.26621.2 | Nepovinné
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 15.7.27617.1 | Nepovinné
Microsoft.VisualStudio.Component.SQL.NCLI | Nativní klient systému SQL Server | 15.0.26208.0 | Nepovinné
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 15.9.28107.0 | Nepovinné
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Nástroje statické analýzy | 15.0.26208.0 | Nepovinné
Microsoft.VisualStudio.Component.TextTemplating | Transformace šablony textu | 15.0.26208.0 | Nepovinné
Microsoft.VisualStudio.Component.VC.140 | Sada nástrojů VC++ 2015.3 v14.00 (v140) pro stolní počítače | 15.7.27617.1 | Nepovinné
Microsoft.VisualStudio.Component.VC.CoreIde | Základní funkce Visual Studia C++ | 15.6.27406.0 | Nepovinné
Nástroje Microsoft.VisualStudio.Component.VC.DiagnosticTools | Nástroje pro profilování jazyka C++ | 15.0.26823.1 | Nepovinné
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | VC++ 2017 verze 15.9 v14.16 nejnovější nástroje v141 | 15.9.28230.55 | Nepovinné
Microsoft.VisualStudio.Component.Web | ASP.NET a nástroje pro vývoj webových aplikací | 15.8.27825.0 | Nepovinné
Microsoft.VisualStudio.Component.Windows10SDK | Windows Universal C Runtime | 15.6.27406.0 | Nepovinné
Microsoft.VisualStudio.Component.Windows10SDK.10586 | Windows 10 SDK (10.0.10586.0) | 15.6.27406.0 | Nepovinné
Microsoft.VisualStudio.Component.Windows10SDK.17763 | Windows 10 SDK (10.0.17763.0) | 15.9.28307.102 | Nepovinné
Microsoft.VisualStudio.Component.Windows81SDK | Windows 8.1 SDK | 15.6.27406.0 | Nepovinné
Microsoft.VisualStudio.ComponentGroup.Web | předpoklady pro ASP.NET a nástroje pro vývoj webových aplikací | 15.9.28219.51 | Nepovinné

## <a name="universal-windows-platform-development"></a>Vývoj univerzální platformy Windows

**ID:** Microsoft.VisualStudio.Workload.Universal

**Popis:** Vytvářejte aplikace pro univerzální platformu Windows pomocí jazyka C#, VB, JavaScriptu nebo volitelně jazyka C++.

### <a name="components-included-by-this-workload"></a>Komponenty zahrnuté do tohoto pracovního vytížení

ID součásti | Name (Název) | Version | Typ závislosti
--- | --- | --- | ---
Komponenta.WebSocket | WebSocket4Net | 15.0.26606.0 | Požaduje se
Microsoft.Component.ClickOnce | Publikování clickonce | 15.8.27825.0 | Požaduje se
Microsoft.Component.NetFX.Nativní | .NET Native | 15.0.26208.0 | Požaduje se
Microsoft.ComponentGroup.Blend | Blend for Visual Studio | 15.6.27406.0 | Požaduje se
Sada Microsoft.Net.Component.4.5.TargetingPack | Balíček cílení rozhraní .NET Framework 4.5 | 15.6.27406.0 | Požaduje se
Microsoft.Net.Component.4.6.1.SDK | Rozhraní .NET Framework 4.6.1 SDK | 15.6.27406.0 | Požaduje se
Microsoft.Net.core.component.Sdk.2.1 | Vývojové nástroje .NET Core 2.1 | 15.8.27924.0 | Požaduje se
Microsoft.VisualStudio.Component.AppInsights.Tools | Nástroje analýzy pro vývojáře | 15.8.27825.0 | Požaduje se
Microsoft.VisualStudio.Component.DiagnosticTools | Nástroje profilování rozhraní .NET | 15.8.27729.1 | Požaduje se
Microsoft.VisualStudio.Component.Graphics | Editory obrázků a 3D modelů | 15.6.27406.0 | Požaduje se
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostika javascriptu | 15.8.27729.1 | Požaduje se
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Podpora jazyka JavaScript a TypeScript | 15.9.28125.51 | Požaduje se
Soubor Microsoft.VisualStudio.Component.NuGet | Správce balíčků NuGet | 15.9.28016.0 | Požaduje se
Knihovna Microsoft.VisualStudio.Component.PortableLibrary | Balíček cílení na přenosnou knihovnu .NET | 15.6.27309.0 | Požaduje se
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilátory Roslyn jazyka C# a Visual Basic | 15.6.27309.0 | Požaduje se
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# a Visual Basic | 15.8.27729.1 | Požaduje se
Microsoft.VisualStudio.Component.SQL.CLR | Datové typy CLR pro SQL Server | 15.0.26208.0 | Požaduje se
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Nástroje statické analýzy | 15.0.26208.0 | Požaduje se
Microsoft.VisualStudio.Component.TypeScript.3.1 | TypeScript 3.1 SDK | 15.0.28218.60 | Požaduje se
Podpora microsoft.visualstudio.component.uWP.Support | Univerzální nástroje platformy Windows | 15.9.28119.51 | Požaduje se
Microsoft.VisualStudio.Component.VisualStudioData | Zdroje dat a odkazy na služby | 15.6.27406.0 | Požaduje se
Microsoft.VisualStudio.Component.Windows10SDK.17763 | Windows 10 SDK (10.0.17763.0) | 15.9.28307.102 | Požaduje se
Microsoft.VisualStudio.ComponentGroup.UWP.Cordova | Univerzální nástroje platformy Windows pro Cordova | 15.9.28307.102 | Požaduje se
Microsoft.VisualStudio.ComponentGroup.UWP.NetcoreAndStandard | Nativní rozhraní .NET a standard .NET | 15.8.27906.1 | Požaduje se
Microsoft.VisualStudio.ComponentGroup.UWP.Xamarin | Univerzální nástroje platformy Windows pro Xamarin | 15.9.28307.102 | Požaduje se
Rozšíření microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Vývoj pro ASP.NET a web | 15.8.27825.0 | Požaduje se
Podpora Microsoft.Component.VC.Runtime.OSSupport | Visual C++ runtime pro UPW | 15.6.27406.0 | Nepovinné
Microsoft.Net.Component.4.7.2.SDK | Rozhraní .NET Framework 4.7.2 SDK | 15.8.27825.0 | Nepovinné
Microsoft.VisualStudio.Component.Graphics.Tools | Grafický ladicí program a profiler GPU pro DirectX | 15.6.27406.0 | Nepovinné
Microsoft.VisualStudio.Component.Graphics.Win81 | Grafické nástroje Windows 8.1 SDK | 15.6.27406.0 | Nepovinné
Microsoft.VisualStudio.Component.Phone.Emulator.15254 | Emulátor mobilních oken Windows 10 (aktualizace fall creators) | 15.0.27406.0 | Nepovinné
Microsoft.VisualStudio.Component.UWP.VC.ARM64 | Nástroje univerzální platformy Windows pro ARM64 | 15.0.28125.51 | Nepovinné
Microsoft.VisualStudio.Component.VC.CoreIde | Základní funkce Visual Studia C++ | 15.6.27406.0 | Nepovinné
Microsoft.VisualStudio.Component.VC.Tools.ARM | Kompilátory a knihovny Visual C++ pro ARM | 15.8.27825.0 | Nepovinné
Microsoft.VisualStudio.Component.VC.Tools.ARM64 | Kompilátory a knihovny Visual C++ pro ARM64 | 15.9.28230.55 | Nepovinné
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | VC++ 2017 verze 15.9 v14.16 nejnovější nástroje v141 | 15.9.28230.55 | Nepovinné
Microsoft.VisualStudio.Component.Windows10SDK.10240 | Windows 10 SDK (10.0.10240.0) | 15.6.27406.0 | Nepovinné
Microsoft.VisualStudio.Component.Windows10SDK.10586 | Windows 10 SDK (10.0.10586.0) | 15.6.27406.0 | Nepovinné
Microsoft.VisualStudio.Component.Windows10SDK.14393 | Windows 10 SDK (10.0.14393.0) | 15.6.27406.0 | Nepovinné
Microsoft.VisualStudio.Component.Windows10SDK.15063.desktop | Sada Windows 10 SDK (10.0.15063.0) pro stolní počítač C++ [x86 a x64] | 15.6.27406.0 | Nepovinné
Microsoft.VisualStudio.Component.Windows10SDK.15063.UWP | Windows 10 SDK (10.0.15063.0) pro UPW: C#, VB, JS | 15.6.27406.0 | Nepovinné
Microsoft.VisualStudio.Component.Windows10SDK.15063.uWP.Native | Windows 10 SDK (10.0.15063.0) pro UPW: C++ | 15.6.27406.0 | Nepovinné
Microsoft.VisualStudio.Component.Windows10SDK.16299.desktop | Sada Windows 10 SDK (10.0.16299.0) pro stolní počítač C++ [x86 a x64] | 15.6.27406.0 | Nepovinné
Microsoft.VisualStudio.Component.Windows10SDK.16299.Desktop.arm | Sada Windows 10 SDK (10.0.16299.0) pro stolní počítač C++ [ARM a ARM64] | 15.6.27406.0 | Nepovinné
Microsoft.VisualStudio.Component.Windows10SDK.16299.UWP | Windows 10 SDK (10.0.16299.0) pro UPW: C#, VB, JS | 15.6.27406.0 | Nepovinné
Microsoft.VisualStudio.Component.Windows10SDK.16299.uWP.Native | Windows 10 SDK (10.0.16299.0) pro UPW: C++ | 15.6.27406.0 | Nepovinné
Microsoft.VisualStudio.Component.Windows10SDK.17134 | Windows 10 SDK (10.0.17134.0) | 15.9.28307.102 | Nepovinné
Microsoft.VisualStudio.Component.Windows10SDK.ipoverusb | Připojení zařízení USB | 15.9.28307.102 | Nepovinné
Microsoft.VisualStudio.ComponentGroup.UWP.VC | Nástroje univerzální platformy Windows pro C++ | 15.9.28307.102 | Nepovinné
Microsoft.VisualStudio.ComponentGroup.Windows10SDK.15063 | Windows 10 SDK (10.0.15063.0) | 15.8.27825.0 | Nepovinné
Microsoft.VisualStudio.ComponentGroup.Windows10SDK.16299 | Windows 10 SDK (10.0.16299.0) | 15.8.27825.0 | Nepovinné

## <a name="visual-studio-extension-development"></a>Vývoj rozšíření sady Visual Studio

**ID:** Rozšíření Microsoft.VisualStudio.Workload.VisualStudioExtension

**Popis:** Vytvořte doplňky a rozšíření pro Visual Studio, včetně nových příkazů, analyzátorů kódu a oken nástrojů.

### <a name="components-included-by-this-workload"></a>Komponenty zahrnuté do tohoto pracovního vytížení

ID součásti | Name (Název) | Version | Typ závislosti
--- | --- | --- | ---
Microsoft.Component.ClickOnce | Publikování clickonce | 15.8.27825.0 | Požaduje se
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | Požaduje se
Microsoft.Net.Component.4.6.1.SDK | Rozhraní .NET Framework 4.6.1 SDK | 15.6.27406.0 | Požaduje se
Microsoft.Net.Component.4.6.1.TargetingPack | Balíček cílení rozhraní .NET Framework 4.6.1 | 15.6.27406.0 | Požaduje se
Sada Microsoft.Net.Component.4.6.TargetingPack | Balíček cílení rozhraní .NET Framework 4.6 | 15.6.27406.0 | Požaduje se
Microsoft.Net.ComponentGroup.DevelopmentPředpoklads | Vývojové nástroje .NET Framework 4.6.1 | 15.8.27825.0 | Požaduje se
Soubor Microsoft.VisualStudio.Component.NuGet | Správce balíčků NuGet | 15.9.28016.0 | Požaduje se
Knihovna Microsoft.VisualStudio.Component.PortableLibrary | Balíček cílení na přenosnou knihovnu .NET | 15.6.27309.0 | Požaduje se
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilátory Roslyn jazyka C# a Visual Basic | 15.6.27309.0 | Požaduje se
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# a Visual Basic | 15.8.27729.1 | Požaduje se
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Nástroje statické analýzy | 15.0.26208.0 | Požaduje se
Microsoft.VisualStudio.Component.VSSDK | Visual Studio SDK | 15.8.27729.1 | Požaduje se
Microsoft.VisualStudio.ComponentGroup.VisualStudioExtension.Prerequisites | Požadavky na vývoj rozšíření sady Visual Studio | 15.7.27625.0 | Požaduje se
Microsoft.VisualStudio.Component.DiagnosticTools | Nástroje profilování rozhraní .NET | 15.8.27729.1 | Doporučené
Microsoft.VisualStudio.Component.TextTemplating | Transformace šablony textu | 15.0.26208.0 | Doporučené
Komponenta.Dotfuscator | PreEmptive Protection – Dotfuscator | 15.0.26208.0 | Nepovinné
Soubor Microsoft.Component.CodeAnalysis.SDK | Sada .NET Compiler Platform SDK | 15.0.27729.1 | Nepovinné
Podpora Microsoft.Component.VC.Runtime.OSSupport | Visual C++ runtime pro UPW | 15.6.27406.0 | Nepovinné
Microsoft.VisualStudio.Component.AppInsights.Tools | Nástroje analýzy pro vývojáře | 15.8.27825.0 | Nepovinné
Microsoft.VisualStudio.Component.ClassDesigner | Návrhář tříd | 15.0.26208.0 | Nepovinné
Microsoft.VisualStudio.Component.DslTools | Modelování sady SDK | 15.0.27005.2 | Nepovinné
Soubor Microsoft.VisualStudio.Component.VC.ATL | Visual C++ ATL pro x86 a x64 | 15.7.27625.0 | Nepovinné
Soubor Microsoft.VisualStudio.Component.VC.ATLMFC | Visual C++ MFC pro x86 a x64 | 15.7.27625.0 | Nepovinné
Microsoft.VisualStudio.Component.VC.CoreIde | Základní funkce Visual Studia C++ | 15.6.27406.0 | Nepovinné
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | VC++ 2017 verze 15.9 v14.16 nejnovější nástroje v141 | 15.9.28230.55 | Nepovinné

## <a name="mobile-development-with-javascript"></a>Vývoj mobilních aplikací v jazyce JavaScript

**ID:** Microsoft.VisualStudio.Workload.WebCrossPlat

**Popis:** Vytvářejte aplikace pro Android, iOS a UPW pomocí nástrojů pro Apache Cordova.

### <a name="components-included-by-this-workload"></a>Komponenty zahrnuté do tohoto pracovního vytížení

ID součásti | Name (Název) | Version | Typ závislosti
--- | --- | --- | ---
Komponenta.CordovaSada nářadí.6.3.1 | Sada nástrojů Cordova 6.3.1 | 15.7.27625.0 | Požaduje se
Komponenta.WebSocket | WebSocket4Net | 15.0.26606.0 | Požaduje se
Microsoft.VisualStudio.Component.Cordova | Vývoj mobilních zařízení s jádrovými funkcemi JavaScriptu | 15.0.26606.0 | Požaduje se
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostika javascriptu | 15.8.27729.1 | Požaduje se
Microsoft.VisualStudio.Component.JavaScript.ProjectSystem | JavaScript ProjectSystem a sdílené nástroje | 15.0.26606.0 | Požaduje se
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Podpora jazyka JavaScript a TypeScript | 15.9.28125.51 | Požaduje se
Microsoft.VisualStudio.Component.TypeScript.2.3 | TypeScript 2.3 SDK | 15.8.27729.1 | Požaduje se
Microsoft.VisualStudio.Component.TypeScript.3.1 | TypeScript 3.1 SDK | 15.0.28218.60 | Požaduje se
Rozšíření microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Vývoj pro ASP.NET a web | 15.8.27825.0 | Požaduje se
komponent.android.SDK23.Private | Nastavení sady Android SDK (úroveň ROZHRANÍ API 23) (lokální instalace pro vývoj pro mobilní zařízení s JavaScriptem / C++) | 15.9.28016.0 | Nepovinné
Komponenta.Google.Android.Emulator.API23.Private | Google Android Emulátor (API Úroveň 23) (místní instalace) | 15.6.27413.0 | Nepovinné
Component.HAXM.Private | Intel Hardware Accelerated Execution Manager (HAXM) (místní instalace) | 15.9.28307.421 | Nepovinné
komponenta OpenJDK | Microsoft distribuce OpenJDK | 15.9.28125.51 | Nepovinné
Microsoft.Component.ClickOnce | Publikování clickonce | 15.8.27825.0 | Nepovinné
Microsoft.Component.NetFX.Nativní | .NET Native | 15.0.26208.0 | Nepovinné
Microsoft.VisualStudio.Component.AppInsights.Tools | Nástroje analýzy pro vývojáře | 15.8.27825.0 | Nepovinné
Microsoft.VisualStudio.Component.DiagnosticTools | Nástroje profilování rozhraní .NET | 15.8.27729.1 | Nepovinné
Microsoft.VisualStudio.Component.Git | Git pro Windows | 15.0.26208.0 | Nepovinné
Microsoft.VisualStudio.Component.Graphics | Editory obrázků a 3D modelů | 15.6.27406.0 | Nepovinné
Microsoft.VisualStudio.Component.Phone.Emulator.15254 | Emulátor mobilních oken Windows 10 (aktualizace fall creators) | 15.0.27406.0 | Nepovinné
Microsoft.VisualStudio.Component.SQL.CLR | Datové typy CLR pro SQL Server | 15.0.26208.0 | Nepovinné
Microsoft.VisualStudio.Component.VisualStudioData | Zdroje dat a odkazy na služby | 15.6.27406.0 | Nepovinné
Microsoft.VisualStudio.Component.Windows10SDK.17763 | Windows 10 SDK (10.0.17763.0) | 15.9.28307.102 | Nepovinné
Microsoft.VisualStudio.ComponentGroup.UWP.Cordova | Univerzální nástroje platformy Windows pro Cordova | 15.9.28307.102 | Nepovinné

## <a name="unaffiliated-components"></a>Nepřidružené součásti

Jedná se o součásti, které nejsou součástí žádné úlohy, ale mohou být vybrány jako jednotlivé součásti.

ID součásti | Name (Název) | Version
--- | --- | ---
Komponenta.Android.Emulátor | Emulátor sady Visual Studio pro Android | 15.6.27413.0
Komponenta.Android.NDK.R11C | Android NDK (R11C) | 11.3.14
Komponenta.Android.NDK.R11C_3264 | Android NDK (R11C) (32bit) | 11.3.16
Komponenta.Android.SDK23 | Nastavení sady Android SDK (úroveň rozhraní API 23) (globální instalace) | 15.9.28107.0
Komponenta.Android.SDK25 | Nastavení sady Android SDK (úroveň rozhraní API 25) | 15.9.28107.0
Component.GitHub.VisualStudio | Rozšíření GitHub pro Visual Studio | 2.5.2.2500
Komponenta.Google.Android.Emulator.API23.V2 | Google Android Emulátor (API Úroveň 23) (globální instalace) | 15.6.27413.0
Komponenta.Google.Android.Emulator.API25 | Google Android emulátor (API Úroveň 25) | 15.7.27604.0
Soubor Microsoft.Component.Blend.SDK.WPF | Blend pro sady Visual Studio SDK pro rozhraní .NET | 15.6.27406.0
Microsoft.Component.HelpViewer | Prohlížeč nápovědy | 15.9.28307.421
Microsoft.VisualStudio.Component.DependencyValidation.Community | Ověření závislostí | 15.0.26208.0
Microsoft.VisualStudio.Component.GraphDocument | Editor DGML | 15.0.27005.2
Microsoft.VisualStudio.Component.LinqToSql | Nástroje LINQ to SQL | 15.6.27406.0
Microsoft.VisualStudio.Component.Phone.Emulator | Emulátor Windows 10 Mobile (Anniversary Edition) | 15.6.27406.0
Microsoft.VisualStudio.Component.Phone.Emulator.15063 | Emulátor mobilních windows 10 (aktualizace tvůrců) | 15.6.27406.0
Microsoft.VisualStudio.Component.Runtime.Node.x86.6.4.0 | Doba běhu pro součásti založená na souboru Node.js v6.4.0 (x86) | 15.7.27617.1
Microsoft.VisualStudio.Component.Runtime.Node.x86.7.4.0 | Doba běhu pro součásti založená na souboru Node.js v7.4.0 (x86) | 15.7.27617.1
Microsoft.VisualStudio.Component.TypeScript.2.0 | TypeScript 2.0 SDK | 15.8.27729.1
Microsoft.VisualStudio.Component.TypeScript.2.1 | TypeScript 2.1 SDK | 15.8.27729.1
Microsoft.VisualStudio.Component.TypeScript.2.2 | TypeScript 2.2 SDK | 15.8.27729.1
Microsoft.VisualStudio.Component.TypeScript.2.5 | TypeScript 2.5 SDK | 15.6.27406.0
Microsoft.VisualStudio.Component.TypeScript.2.6 | TypeScript 2.6 SDK | 15.0.27729.1
Microsoft.VisualStudio.Component.TypeScript.2.7 | TypeScript 2.7 SDK | 15.0.27729.1
Microsoft.VisualStudio.Component.TypeScript.2.8 | TypeScript 2.8 SDK | 15.0.27729.1
Microsoft.VisualStudio.Component.TypeScript.2.9 | TypeScript 2.9 SDK | 15.0.27924.0
Microsoft.VisualStudio.Component.TypeScript.3.0 | TypeScript 3.0 SDK | 15.0.27924.0
Soubor Microsoft.VisualStudio.Component.VC.ATL.ARM | Visual C++ ATL pro ARM | 15.7.27625.0
Soubor Microsoft.VisualStudio.Component.VC.ATL.ARM.Spectre | Visual C++ ATL pro ARM s spectre skutečnosti | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.ATL.ARM64 | Visual C++ ATL pro ARM64 | 15.7.27625.0
Soubor Microsoft.VisualStudio.Component.VC.ATL.ARM64.Spectre | Visual C++ ATL pro ARM64 s spectre skutečnosti | 15.7.27625.0
Soubor Microsoft.VisualStudio.Component.VC.ATL.Spectre | Visual C++ ATL (x86/x64) s rituzními riziky spectre | 15.7.27625.0
Soubor Microsoft.VisualStudio.Component.VC.ATLMFC.Spectre | Visual C++ MFC pro x86/x64 s spectre skutečnosti | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.ClangC2 | Clang/C2 (experimentální) | 15.7.27520.0
Microsoft.VisualStudio.Component.VC.MFC.ARM | Vizuální c++ knihovna MFC pro ARM | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.MFC.ARM.Spectre | Visual C++ MFC pro ARM s spectre skutečnosti | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.MFC.ARM64 | Vizuální c++ knihovna MFC pro ARM64 | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.MFC.ARM64.Spectre | Podpora visual c++ knihovny MFC pro ARM64 s rituzními riziky spectre | 15.7.27625.0
Soubor Microsoft.VisualStudio.Component.VC.Runtimes.ARM.Spectre | VC++ 2017 verze 15.9 v14.16 Libs pro Spectre (ARM) | 15.9.28230.55
Soubor Microsoft.VisualStudio.Component.VC.Runtimes.ARM64.Spectre | VC++ 2017 verze 15.9 v14.16 Libs pro Spectre (ARM64) | 15.9.28230.55
Soubor Microsoft.VisualStudio.Component.VC.Runtimes.x86.x64.Spectre | VC++ 2017 verze 15.9 v14.16 Libs pro Spectre (x86 a x64) | 15.9.28230.55
Microsoft.VisualStudio.Component.VC.Tools.14.11 | Sada nástrojů VC++ 2017 verze 15.4 v14.11 | 15.0.27924.0
Microsoft.VisualStudio.Component.VC.Tools.14.12 | Sada nástrojů VC++ 2017 verze 15.5 v14.12 | 15.0.27924.0
Microsoft.VisualStudio.Component.VC.Tools.14.13 | Sada nástrojů VC++ 2017 verze 15.6 v14.13 | 15.0.27924.0
Microsoft.VisualStudio.Component.VC.Tools.14.14 | Sada nástrojů VC++ 2017 verze 15.7 v14.14 | 15.0.27924.0
Microsoft.VisualStudio.Component.VC.Tools.14.15 | Sada nástrojů VC++ 2017 verze 15.8 v14.15 | 15.0.28230.55
