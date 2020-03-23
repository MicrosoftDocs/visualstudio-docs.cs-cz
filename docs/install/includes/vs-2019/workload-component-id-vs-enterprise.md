---
title: Pracovní vytížení a ID součástí Visual Studio Enterprise 2019
titleSuffix: ''
description: Použití id úloh a součástí k instalaci sady Visual Studio pomocí příkazového řádku nebo k určení závislosti v manifestu VSIX
keywords: ''
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.date: 03/16/2020
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.topic: include
ms.openlocfilehash: 5844e30a9ca1f73026ed86f45dd8eb3d8842594f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "79437659"
---
## <a name="visual-studio-core-editor-included-with-visual-studio-enterprise-2019"></a>Visual Studio core editor (součástí Visual Studio Enterprise 2019)

**ID:** Microsoft.VisualStudio.Workload.CoreEditor

**Popis:** Prostředí základní prostředí sady Visual Studio, včetně úprav kódu podporujícího syntaxi, správy zdrojového kódu a správy pracovních položek.

### <a name="components-included-by-this-workload"></a>Komponenty zahrnuté do tohoto pracovního vytížení

ID součásti | Name (Název) | Version | Typ závislosti
--- | --- | --- | ---
Microsoft.VisualStudio.Component.CoreEditor | Základní editor Visual Studia | 16.1.28811.260 | Požaduje se
Soubor Microsoft.VisualStudio.Component.StartPageExperiment.Cpp | Úvodní stránka Visual Studia pro uživatele c++ | 16.0.28315.86 | Nepovinné

## <a name="azure-development"></a>Vývoj pro Azure

**ID:** Microsoft.VisualStudio.Workload.Azure

**Popis:** Sady Azure SDK, nástroje a projekty pro vývoj cloudových aplikací a vytváření prostředků pomocí rozhraní .NET Core a .NET Framework. Obsahuje také nástroje pro kontejnerizaci vaší aplikace, včetně podpory Dockeru.

### <a name="components-included-by-this-workload"></a>Komponenty zahrnuté do tohoto pracovního vytížení

ID součásti | Name (Název) | Version | Typ závislosti
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Razor Language Services | 16.0.28714.129 | Požaduje se
Component.Microsoft.VisualStudio.Web.AzureFunkce | Nástroje Azure WebJobs | 16.0.28714.129 | Požaduje se
Component.Microsoft.Web.LibraryManager | Správce knihovny | 16.0.28315.86 | Požaduje se
Microsoft.Component.MSBuild | MSBuild | 16.5.29515.121 | Požaduje se
Microsoft.Net.Component.4.5.2.TargetingPack | Balíček cílení .NET Framework 4.5.2 | 16.0.28517.75 | Požaduje se
Sada Microsoft.Net.Component.4.5.TargetingPack | Balíček cílení rozhraní .NET Framework 4.5 | 16.0.28517.75 | Požaduje se
Microsoft.Net.Component.4.6.1.TargetingPack | Balíček cílení rozhraní .NET Framework 4.6.1 | 16.0.28517.75 | Požaduje se
Microsoft.Net.Component.4.7.2.TargetingPack | Balíček cílení .NET Framework 4.7.2 | 16.0.28517.75 | Požaduje se
Sada Microsoft.Net.Component.4.8.SdK | Rozhraní .NET Framework 4.8 SDK | 16.4.29313.120 | Požaduje se
Microsoft.Net.ComponentGroup.DevelopmentPředpoklads | Vývojové nástroje .NET Framework 4.7.2 | 16.3.29207.166 | Požaduje se
Microsoft.Netcore.Component.DevelopmentTools | Nástroje pro vývoj .NET Core | 16.5.29721.120 | Požaduje se
Microsoft.NetCore.Component.Runtime.3.1 | Doba běhu .NET Core 3.1 LTS | 16.5.29905.7 | Požaduje se
Soubor Microsoft.Netcore.Component.SDK | Sada .NET Core SDK | 16.5.29905.7 | Požaduje se
Soubor Microsoft.Netcore.Component.Web | Nástroje pro vývoj .NET Core | 16.5.29721.120 | Požaduje se
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Vývojové nástroje Azure | 16.0.28625.61 | Požaduje se
Microsoft.VisualStudio.Component.Azure.ClientLibs | Knihovny Azure pro rozhraní .NET | 16.0.28315.86 | Požaduje se
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Výpočetní emulátor Azure | 16.1.28810.153 | Požaduje se
Microsoft.VisualStudio.Component.Azure.Storage.Emulátor | Emulátor úložiště Azure | 16.4.29313.120 | Požaduje se
Microsoft.VisualStudio.Component.CloudExplorer | Průzkumník cloudu | 16.0.28625.61 | Požaduje se
Microsoft.VisualStudio.Component.Common.Azure.Tools | Nástroje pro konektivitu a publikování | 16.4.29409.204 | Požaduje se
Microsoft.VisualStudio.Component.DockerTools | Kontejnerové vývojové nástroje | 16.4.29409.204 | Požaduje se
Microsoft.VisualStudio.Component.FSharp | Podpora jazyka F# | 16.0.28315.86 | Požaduje se
Šablony Microsoft.VisualStudio.Component.FSharp.WebTemplates | Podpora jazyka F# pro webové projekty | 16.3.29207.166 | Požaduje se
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 16.0.28315.86 | Požaduje se
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 0.1 | Požaduje se
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostika javascriptu | 16.0.28517.75 | Požaduje se
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Podpora jazyka JavaScript a TypeScript | 16.5.29721.120 | Požaduje se
Soubor Microsoft.VisualStudio.Component.ManagedDesktop.Core | Jádro spravovaného pracovního vytížení plochy | 16.4.29318.151 | Požaduje se
Soubor Microsoft.VisualStudio.Component.MSODBC.SQL | Ovladač ODBC serveru SQL Server | 16.0.28625.61 | Požaduje se
Microsoft.VisualStudio.Component.MSSQL.CMDLnUtils | Nástroje příkazového řádku serveru SQL Server | 16.0.28707.177 | Požaduje se
Soubor Microsoft.VisualStudio.Component.NuGet | Správce balíčků NuGet | 16.1.28829.92 | Požaduje se
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilátory Roslyn jazyka C# a Visual Basic | 16.0.28714.129 | Požaduje se
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# a Visual Basic | 16.5.29515.121 | Požaduje se
Microsoft.VisualStudio.Component.SQL.ADAL | Modul runtime SQL ADAL | 16.0.28517.75 | Požaduje se
Microsoft.VisualStudio.Component.SQL.CLR | Datové typy CLR pro SQL Server | 16.0.28315.86 | Požaduje se
Microsoft.VisualStudio.Component.SQL.DataSources | Zdroje dat pro podporu serveru SQL Server | 16.0.28315.86 | Požaduje se
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 16.0.28625.61 | Požaduje se
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 16.3.29207.166 | Požaduje se
Microsoft.VisualStudio.Component.TextTemplating | Transformace šablony textu | 16.0.28625.61 | Požaduje se
Microsoft.VisualStudio.Component.TypeScript.3.8 | TypeScript 3.8 SDK | 16.0.29813.82 | Požaduje se
Microsoft.VisualStudio.Component.Web | ASP.NET a nástroje pro vývoj webových aplikací | 16.0.28517.75 | Požaduje se
Microsoft.VisualStudio.ComponentGroup.Azure.Prerequisites | Předpoklady pro vývoj Azure | 16.4.29409.204 | Požaduje se
Funkce Microsoft.VisualStudio.ComponentGroup.Azure | Nástroje Azure WebJobs | 16.0.28621.142 | Požaduje se
Microsoft.VisualStudio.ComponentGroup.Web | předpoklady pro ASP.NET a nástroje pro vývoj webových aplikací | 16.4.29318.151 | Požaduje se
Rozšíření microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Vývoj pro ASP.NET a web | 16.0.28621.142 | Požaduje se
Microsoft.Component.Azure.datalake.Tools | Nástroje Azure Data Lake a Stream Analytics | 16.5.29721.120 | Doporučené
Microsoft.Net.Component.4.5.1.TargetingPack | Balíček cílení v rámci .NET Framework 4.5.1 | 16.0.28517.75 | Doporučené
Sada Microsoft.Net.Component.4.6.TargetingPack | Balíček cílení rozhraní .NET Framework 4.6 | 16.0.28517.75 | Doporučené
Sada Microsoft.Net.Component.4.TargetingPack | Balíček cílení rozhraní .NET Framework 4 | 16.0.28517.75 | Doporučené
Microsoft.Net.ComponentGroup.TargetingPacks.Common | .NET Framework 4 – 4.6 vývojové nástroje | 16.0.28516.191 | Doporučené
Microsoft.Net.core.component.Sdk.2.1 | Doba běhu .NET Core 2.1 LTS | 16.5.29905.7 | Doporučené
Microsoft.VisualStudio.Component.AspNet45 | Pokročilé ASP.NET funkce | 16.0.28315.86 | Doporučené
Microsoft.VisualStudio.Component.Azure.Kubernetes.Tools | Visual Studio Tools for Kubernetes | 16.0.28625.61 | Doporučené
Microsoft.VisualStudio.Component.Azure.Powershell | Azure Powershell | 16.5.29515.121 | Doporučené
Microsoft.VisualStudio.Component.Azure.ResourceManager.Tools | Základní nástroje Azure Resource Manageru | 16.4.29409.204 | Doporučené
Microsoft.VisualStudio.Component.Azure.ServiceFabric.Tools | Nástroje Service Fabricu | 16.4.29313.120 | Doporučené
Microsoft.VisualStudio.Component.Azure.Waverton | Základní nástroje Cloudových služeb Azure | 16.4.29409.204 | Doporučené
Microsoft.VisualStudio.Component.Azure.Waverton.BuildTools | Nástroje pro vytváření cloudových služeb Azure | 16.3.29207.166 | Doporučené
Microsoft.VisualStudio.Component.Debugger.Snapshot | Ladicí program snímků | 16.5.29813.82 | Doporučené
Microsoft.VisualStudio.Component.Debugger.TimeTravel | Ladicí program cestování v čase | 16.5.29515.121 | Doporučené
Microsoft.VisualStudio.Component.DiagnosticTools | Nástroje profilování rozhraní .NET | 16.5.29515.121 | Doporučené
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | 16.5.29515.121 | Doporučené
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 16.0.28517.75 | Doporučené
Služby Microsoft.VisualStudio.ComponentGroup.Azure.CloudServices | Nástroje cloudových služeb Azure | 16.4.29409.204 | Doporučené
Microsoft.VisualStudio.ComponentGroup.Azure.ResourceManager.Tools | Nástroje Azure Resource Manager | 16.0.28528.71 | Doporučené
Sada Microsoft.Net.Component.4.6.2.TargetingPack | Balíček cílení .NET Framework 4.6.2 | 16.0.28517.75 | Nepovinné
Microsoft.Net.Component.4.7.1.TargetingPack | Balíček cílení .NET Framework 4.7.1 | 16.0.28517.75 | Nepovinné
Sada Microsoft.Net.Component.4.7.TargetingPack | Balíček cílení rozhraní .NET Framework 4.7 | 16.0.28517.75 | Nepovinné
Sada Microsoft.Net.Component.4.8.TargetingPack | Balíček cílení rozhraní .NET Framework 4.8 | 16.4.29313.120 | Nepovinné
Microsoft.Net.ComponentGroup.4.6.1.DeveloperTools | Vývojové nástroje .NET Framework 4.6.1 | 16.3.29207.166 | Nepovinné
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | Vývojové nástroje .NET Framework 4.6.2 | 16.3.29207.166 | Nepovinné
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | Vývojové nástroje .NET Framework 4.7.1 | 16.3.29207.166 | Nepovinné
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | Vývojové nástroje rozhraní .NET Framework 4.7 | 16.3.29207.166 | Nepovinné
Microsoft.Net.ComponentGroup.4.8.DeveloperTools | Vývojové nástroje rozhraní .NET Framework 4.8 | 16.4.29318.151 | Nepovinné
Microsoft.VisualStudio.Component.Azure.Storage.AzCopy | Azure Storage AzCopy | 16.0.28517.75 | Nepovinné
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | 16.0.28625.61 | Nepovinné

## <a name="data-storage-and-processing"></a>Ukládání a zpracování dat

**ID:** Microsoft.VisualStudio.Workload.Data

**Popis:** Připojte, vyvíjejte a otestujte datová řešení pomocí SQL Serveru, Azure Data Lake nebo Hadoop.

### <a name="components-included-by-this-workload"></a>Komponenty zahrnuté do tohoto pracovního vytížení

ID součásti | Name (Název) | Version | Typ závislosti
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Razor Language Services | 16.0.28714.129 | Doporučené
Component.Microsoft.Web.LibraryManager | Správce knihovny | 16.0.28315.86 | Doporučené
Microsoft.Component.Azure.datalake.Tools | Nástroje Azure Data Lake a Stream Analytics | 16.5.29721.120 | Doporučené
Microsoft.Component.MSBuild | MSBuild | 16.5.29515.121 | Doporučené
Microsoft.Net.Component.4.5.1.TargetingPack | Balíček cílení v rámci .NET Framework 4.5.1 | 16.0.28517.75 | Doporučené
Microsoft.Net.Component.4.5.2.TargetingPack | Balíček cílení .NET Framework 4.5.2 | 16.0.28517.75 | Doporučené
Sada Microsoft.Net.Component.4.5.TargetingPack | Balíček cílení rozhraní .NET Framework 4.5 | 16.0.28517.75 | Doporučené
Sada Microsoft.Net.Component.4.6.TargetingPack | Balíček cílení rozhraní .NET Framework 4.6 | 16.0.28517.75 | Doporučené
Microsoft.Net.Component.4.7.2.TargetingPack | Balíček cílení .NET Framework 4.7.2 | 16.0.28517.75 | Doporučené
Sada Microsoft.Net.Component.4.8.SdK | Rozhraní .NET Framework 4.8 SDK | 16.4.29313.120 | Doporučené
Sada Microsoft.Net.Component.4.TargetingPack | Balíček cílení rozhraní .NET Framework 4 | 16.0.28517.75 | Doporučené
Microsoft.Net.ComponentGroup.DevelopmentPředpoklads | Vývojové nástroje .NET Framework 4.7.2 | 16.3.29207.166 | Doporučené
Microsoft.Net.ComponentGroup.TargetingPacks.Common | .NET Framework 4 – 4.6 vývojové nástroje | 16.0.28516.191 | Doporučené
Microsoft.NetCore.Component.Runtime.3.1 | Doba běhu .NET Core 3.1 LTS | 16.5.29905.7 | Doporučené
Soubor Microsoft.Netcore.Component.SDK | Sada .NET Core SDK | 16.5.29905.7 | Doporučené
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Vývojové nástroje Azure | 16.0.28625.61 | Doporučené
Microsoft.VisualStudio.Component.Azure.ClientLibs | Knihovny Azure pro rozhraní .NET | 16.0.28315.86 | Doporučené
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Výpočetní emulátor Azure | 16.1.28810.153 | Doporučené
Microsoft.VisualStudio.Component.Azure.Storage.Emulátor | Emulátor úložiště Azure | 16.4.29313.120 | Doporučené
Microsoft.VisualStudio.Component.Azure.Waverton | Základní nástroje Cloudových služeb Azure | 16.4.29409.204 | Doporučené
Microsoft.VisualStudio.Component.Azure.Waverton.BuildTools | Nástroje pro vytváření cloudových služeb Azure | 16.3.29207.166 | Doporučené
Microsoft.VisualStudio.Component.CloudExplorer | Průzkumník cloudu | 16.0.28625.61 | Doporučené
Microsoft.VisualStudio.Component.Common.Azure.Tools | Nástroje pro konektivitu a publikování | 16.4.29409.204 | Doporučené
Microsoft.VisualStudio.Component.DockerTools | Kontejnerové vývojové nástroje | 16.4.29409.204 | Doporučené
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 16.0.28315.86 | Doporučené
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostika javascriptu | 16.0.28517.75 | Doporučené
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Podpora jazyka JavaScript a TypeScript | 16.5.29721.120 | Doporučené
Soubor Microsoft.VisualStudio.Component.ManagedDesktop.Core | Jádro spravovaného pracovního vytížení plochy | 16.4.29318.151 | Doporučené
Soubor Microsoft.VisualStudio.Component.MSODBC.SQL | Ovladač ODBC serveru SQL Server | 16.0.28625.61 | Doporučené
Microsoft.VisualStudio.Component.MSSQL.CMDLnUtils | Nástroje příkazového řádku serveru SQL Server | 16.0.28707.177 | Doporučené
Soubor Microsoft.VisualStudio.Component.NuGet | Správce balíčků NuGet | 16.1.28829.92 | Doporučené
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilátory Roslyn jazyka C# a Visual Basic | 16.0.28714.129 | Doporučené
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# a Visual Basic | 16.5.29515.121 | Doporučené
Microsoft.VisualStudio.Component.SQL.ADAL | Modul runtime SQL ADAL | 16.0.28517.75 | Doporučené
Microsoft.VisualStudio.Component.SQL.CLR | Datové typy CLR pro SQL Server | 16.0.28315.86 | Doporučené
Microsoft.VisualStudio.Component.SQL.DataSources | Zdroje dat pro podporu serveru SQL Server | 16.0.28315.86 | Doporučené
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 16.0.28625.61 | Doporučené
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 16.3.29207.166 | Doporučené
Microsoft.VisualStudio.Component.TextTemplating | Transformace šablony textu | 16.0.28625.61 | Doporučené
Microsoft.VisualStudio.Component.TypeScript.3.8 | TypeScript 3.8 SDK | 16.0.29813.82 | Doporučené
Microsoft.VisualStudio.Component.Web | ASP.NET a nástroje pro vývoj webových aplikací | 16.0.28517.75 | Doporučené
Microsoft.VisualStudio.ComponentGroup.Web | předpoklady pro ASP.NET a nástroje pro vývoj webových aplikací | 16.4.29318.151 | Doporučené
Rozšíření microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Vývoj pro ASP.NET a web | 16.0.28621.142 | Doporučené
Microsoft.Net.Component.4.6.1.TargetingPack | Balíček cílení rozhraní .NET Framework 4.6.1 | 16.0.28517.75 | Nepovinné
Microsoft.VisualStudio.Component.FSharp.Desktop | Podpora jazyka pro stolní počítače F# | 16.0.28315.86 | Nepovinné

## <a name="data-science-and-analytical-applications"></a>Aplikace pro datové vědy a analýzy

**ID:** Microsoft.VisualStudio.Workload.DataScience

**Popis:** Jazyky a nástroje pro vytváření aplikací pro datové vědy, včetně Pythonu a F#.

### <a name="components-included-by-this-workload"></a>Komponenty zahrnuté do tohoto pracovního vytížení

ID součásti | Name (Název) | Version | Typ závislosti
--- | --- | --- | ---
Microsoft.Component.PythonTools | Podpora jazyka Pythonu | 16.5.29515.121 | Doporučené
Microsoft.Component.PythonTools.Minicondax64 | Python miniconda | 16.2.29003.222 | Doporučené
Microsoft.Component.PythonTools.Web | Webová podpora pythonu | 16.0.28517.75 | Doporučené
Microsoft.Net.Component.4.6.1.TargetingPack | Balíček cílení rozhraní .NET Framework 4.6.1 | 16.0.28517.75 | Doporučené
Microsoft.VisualStudio.Component.Common.Azure.Tools | Nástroje pro konektivitu a publikování | 16.4.29409.204 | Doporučené
Microsoft.VisualStudio.Component.FSharp.Desktop | Podpora jazyka pro stolní počítače F# | 16.0.28315.86 | Doporučené
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Podpora jazyka JavaScript a TypeScript | 16.5.29721.120 | Doporučené
Soubor Microsoft.VisualStudio.Component.NuGet | Správce balíčků NuGet | 16.1.28829.92 | Doporučené
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilátory Roslyn jazyka C# a Visual Basic | 16.0.28714.129 | Doporučené
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# a Visual Basic | 16.5.29515.121 | Doporučené
Microsoft.VisualStudio.Component.TypeScript.3.8 | TypeScript 3.8 SDK | 16.0.29813.82 | Doporučené
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 16.0.28517.75 | Doporučené
Rozšíření microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Vývoj pro ASP.NET a web | 16.0.28621.142 | Doporučené
Vývoj souboru Microsoft.ComponentGroup.PythonTools.NativeDevelopment | Nativní vývojové nástroje Pythonu | 16.2.29020.229 | Nepovinné
Microsoft.VisualStudio.Component.Graphics.Tools | Grafický ladicí program a profiler GPU pro DirectX | 16.0.28625.61 | Nepovinné
Microsoft.VisualStudio.Component.VC.CoreIde | Základní funkce C++ | 16.0.28625.61 | Nepovinné
Nástroje Microsoft.VisualStudio.Component.VC.DiagnosticTools | Nástroje pro profilování jazyka C++ | 16.5.29515.121 | Nepovinné
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | Nástroje sestavení MSVC v142 - VS 2019 C++ x64/x86 (v14.25) | 16.5.29721.120 | Nepovinné
Microsoft.VisualStudio.Component.Windows10SDK | Windows Universal C Runtime | 16.4.29409.204 | Nepovinné
Microsoft.VisualStudio.Component.Windows10SDK.18362 | Windows 10 SDK (10.0.18362.0) | 16.1.28829.92 | Nepovinné

## <a name="net-desktop-development"></a>Vývoj stolních počítačů .NET

**ID:** Microsoft.VisualStudio.Workload.ManagedDesktop

**Popis:** Vytvářejte aplikace WPF, Windows Forms a konzolové aplikace pomocí c#, visual basicu a jazyka F# pomocí rozhraní .NET Core a .NET Framework.

### <a name="components-included-by-this-workload"></a>Komponenty zahrnuté do tohoto pracovního vytížení

ID součásti | Name (Název) | Version | Typ závislosti
--- | --- | --- | ---
Microsoft.Component.MSBuild | MSBuild | 16.5.29515.121 | Požaduje se
Microsoft.Net.Component.4.7.2.TargetingPack | Balíček cílení .NET Framework 4.7.2 | 16.0.28517.75 | Požaduje se
Sada Microsoft.Net.Component.4.8.SdK | Rozhraní .NET Framework 4.8 SDK | 16.4.29313.120 | Požaduje se
Microsoft.Net.ComponentGroup.DevelopmentPředpoklads | Vývojové nástroje .NET Framework 4.7.2 | 16.3.29207.166 | Požaduje se
Microsoft.NetCore.Component.Runtime.3.1 | Doba běhu .NET Core 3.1 LTS | 16.5.29905.7 | Požaduje se
Soubor Microsoft.Netcore.Component.SDK | Sada .NET Core SDK | 16.5.29905.7 | Požaduje se
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 0.1 | Požaduje se
Soubor Microsoft.VisualStudio.Component.ManagedDesktop.Core | Jádro spravovaného pracovního vytížení plochy | 16.4.29318.151 | Požaduje se
Microsoft.VisualStudio.Component.ManagedDesktop.Prerequisites | Nástroje pro vývoj stolních počítačů .NET | 16.5.29514.35 | Požaduje se
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilátory Roslyn jazyka C# a Visual Basic | 16.0.28714.129 | Požaduje se
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# a Visual Basic | 16.5.29515.121 | Požaduje se
Microsoft.VisualStudio.Component.SQL.CLR | Datové typy CLR pro SQL Server | 16.0.28315.86 | Požaduje se
Microsoft.VisualStudio.Component.TextTemplating | Transformace šablony textu | 16.0.28625.61 | Požaduje se
Component.Microsoft.VisualStudio.LiveShare | Live Share | 1.0.1561 | Doporučené
Microsoft.ComponentGroup.Blend | Blend for Visual Studio | 16.0.28315.86 | Doporučené
Microsoft.Net.Component.4.5.1.TargetingPack | Balíček cílení v rámci .NET Framework 4.5.1 | 16.0.28517.75 | Doporučené
Microsoft.Net.Component.4.5.2.TargetingPack | Balíček cílení .NET Framework 4.5.2 | 16.0.28517.75 | Doporučené
Sada Microsoft.Net.Component.4.5.TargetingPack | Balíček cílení rozhraní .NET Framework 4.5 | 16.0.28517.75 | Doporučené
Microsoft.Net.Component.4.6.1.TargetingPack | Balíček cílení rozhraní .NET Framework 4.6.1 | 16.0.28517.75 | Doporučené
Sada Microsoft.Net.Component.4.6.TargetingPack | Balíček cílení rozhraní .NET Framework 4.6 | 16.0.28517.75 | Doporučené
Sada Microsoft.Net.Component.4.TargetingPack | Balíček cílení rozhraní .NET Framework 4 | 16.0.28517.75 | Doporučené
Microsoft.Net.ComponentGroup.TargetingPacks.Common | .NET Framework 4 – 4.6 vývojové nástroje | 16.0.28516.191 | Doporučené
Microsoft.Net.core.component.Sdk.2.1 | Doba běhu .NET Core 2.1 LTS | 16.5.29905.7 | Doporučené
Microsoft.Netcore.Component.DevelopmentTools | Nástroje pro vývoj .NET Core | 16.5.29721.120 | Doporučené
Microsoft.VisualStudio.Component.Debugger.JustInTime | Ladicí program Just-In-Time | 16.0.28517.75 | Doporučené
Microsoft.VisualStudio.Component.DiagnosticTools | Nástroje profilování rozhraní .NET | 16.5.29515.121 | Doporučené
Microsoft.VisualStudio.Component.EntityFramework | Nástroje entity Framework 6 | 16.0.28315.86 | Doporučené
Microsoft.VisualStudio.Component.FSharp | Podpora jazyka F# | 16.0.28315.86 | Doporučené
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | 16.5.29515.121 | Doporučené
Microsoft.VisualStudio.Component.LiveUnitTesting | Live Unit Testing | 16.1.28811.260 | Doporučené
Soubor Microsoft.VisualStudio.Component.NuGet | Správce balíčků NuGet | 16.1.28829.92 | Doporučené
Komponenta.Dotfuscator | PreEmptive Protection – Dotfuscator | 16.0.28528.71 | Nepovinné
Component.Microsoft.VisualStudio.RazorExtension | Razor Language Services | 16.0.28714.129 | Nepovinné
Component.Microsoft.Web.LibraryManager | Správce knihovny | 16.0.28315.86 | Nepovinné
Sada Microsoft.Net.Component.4.6.2.TargetingPack | Balíček cílení .NET Framework 4.6.2 | 16.0.28517.75 | Nepovinné
Microsoft.Net.Component.4.7.1.TargetingPack | Balíček cílení .NET Framework 4.7.1 | 16.0.28517.75 | Nepovinné
Sada Microsoft.Net.Component.4.7.TargetingPack | Balíček cílení rozhraní .NET Framework 4.7 | 16.0.28517.75 | Nepovinné
Sada Microsoft.Net.Component.4.8.TargetingPack | Balíček cílení rozhraní .NET Framework 4.8 | 16.4.29313.120 | Nepovinné
Microsoft.Net.ComponentGroup.4.6.1.DeveloperTools | Vývojové nástroje .NET Framework 4.6.1 | 16.3.29207.166 | Nepovinné
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | Vývojové nástroje .NET Framework 4.6.2 | 16.3.29207.166 | Nepovinné
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | Vývojové nástroje .NET Framework 4.7.1 | 16.3.29207.166 | Nepovinné
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | Vývojové nástroje rozhraní .NET Framework 4.7 | 16.3.29207.166 | Nepovinné
Microsoft.Net.ComponentGroup.4.8.DeveloperTools | Vývojové nástroje rozhraní .NET Framework 4.8 | 16.4.29318.151 | Nepovinné
Microsoft.VisualStudio.Component.ClassDesigner | Návrhář tříd | 16.0.28528.71 | Nepovinné
Microsoft.VisualStudio.Component.CodeClone | Klon kódu | 16.4.29409.204 | Nepovinné
Mapa kódu Microsoft.VisualStudio.Component.CodeMap | Mapa kódu | 16.0.28625.61 | Nepovinné
Microsoft.VisualStudio.Component.Common.Azure.Tools | Nástroje pro konektivitu a publikování | 16.4.29409.204 | Nepovinné
Microsoft.VisualStudio.Component.DependencyValidation.Enterprise | Ověření živé závislosti | 16.0.28625.61 | Nepovinné
Microsoft.VisualStudio.Component.DockerTools | Kontejnerové vývojové nástroje | 16.4.29409.204 | Nepovinné
Microsoft.VisualStudio.Component.FSharp.Desktop | Podpora jazyka pro stolní počítače F# | 16.0.28315.86 | Nepovinné
Microsoft.VisualStudio.Component.GraphDocument | Editor DGML | 16.0.28625.61 | Nepovinné
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 16.0.28315.86 | Nepovinné
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostika javascriptu | 16.0.28517.75 | Nepovinné
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Podpora jazyka JavaScript a TypeScript | 16.5.29721.120 | Nepovinné
Soubor Microsoft.VisualStudio.Component.MSODBC.SQL | Ovladač ODBC serveru SQL Server | 16.0.28625.61 | Nepovinné
Microsoft.VisualStudio.Component.MSSQL.CMDLnUtils | Nástroje příkazového řádku serveru SQL Server | 16.0.28707.177 | Nepovinné
Knihovna Microsoft.VisualStudio.Component.PortableLibrary | Balíček cílení na přenosnou knihovnu .NET | 16.0.28517.75 | Nepovinné
Microsoft.VisualStudio.Component.SQL.ADAL | Modul runtime SQL ADAL | 16.0.28517.75 | Nepovinné
Microsoft.VisualStudio.Component.SQL.DataSources | Zdroje dat pro podporu serveru SQL Server | 16.0.28315.86 | Nepovinné
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 16.0.28625.61 | Nepovinné
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 16.3.29207.166 | Nepovinné
Microsoft.VisualStudio.Component.TypeScript.3.8 | TypeScript 3.8 SDK | 16.0.29813.82 | Nepovinné
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | 16.0.28625.61 | Nepovinné
Microsoft.VisualStudio.Component.Web | ASP.NET a nástroje pro vývoj webových aplikací | 16.0.28517.75 | Nepovinné
Microsoft.VisualStudio.Component.Windows10SDK.18362 | Windows 10 SDK (10.0.18362.0) | 16.1.28829.92 | Nepovinné
Microsoft.VisualStudio.ComponentGroup.ArchitectureTools.Managed | Nástroje pro architekturu a analýzu | 16.5.29514.35 | Nepovinné
Microsoft.VisualStudio.ComponentGroup.MSIX.Packaging | Balicí nástroje MSIX | 16.4.29409.204 | Nepovinné
Microsoft.VisualStudio.ComponentGroup.Web | předpoklady pro ASP.NET a nástroje pro vývoj webových aplikací | 16.4.29318.151 | Nepovinné
Rozšíření microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Vývoj pro ASP.NET a web | 16.0.28621.142 | Nepovinné

## <a name="game-development-with-unity"></a>Vývoj her pomocí Unity

**ID:** Microsoft.VisualStudio.Workload.ManagedGame

**Popis:** Vytvářejte 2D a 3D hry s Unity, výkonným vývojovým prostředím napříč platformami.

### <a name="components-included-by-this-workload"></a>Komponenty zahrnuté do tohoto pracovního vytížení

ID součásti | Name (Název) | Version | Typ závislosti
--- | --- | --- | ---
Microsoft.Net.Component.3.5.DeveloperTools | Vývojové nástroje rozhraní .NET Framework 3.5 | 16.0.28517.75 | Požaduje se
Microsoft.Net.Component.4.7.1.TargetingPack | Balíček cílení .NET Framework 4.7.1 | 16.0.28517.75 | Požaduje se
Soubor Microsoft.VisualStudio.Component.NuGet | Správce balíčků NuGet | 16.1.28829.92 | Požaduje se
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilátory Roslyn jazyka C# a Visual Basic | 16.0.28714.129 | Požaduje se
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# a Visual Basic | 16.5.29515.121 | Požaduje se
Microsoft.VisualStudio.Component.Unity | Visual Studio Tools for Unity | 16.0.28315.86 | Požaduje se
Component.UnityEngine.x64 | Unity 2019.2 64bitový editor | 16.5.29515.121 | Doporučené
Component.UnityEngine.x86 | Unity 5,6 32bitový editor | 16.1.28811.260 | Doporučené

## <a name="linux-development-with-c"></a>Vývoj linuxových aplikací v jazyce C++

**ID:** Microsoft.VisualStudio.Workload.NativeCrossPlat

**Popis:** Vytvářejte a ladíte aplikace spuštěné v prostředí Linuxu.

### <a name="components-included-by-this-workload"></a>Komponenty zahrnuté do tohoto pracovního vytížení

ID součásti | Name (Název) | Version | Typ závislosti
--- | --- | --- | ---
Component.MDD.Linux | C++ pro vývoj Linuxu | 16.5.29515.121 | Požaduje se
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 0.1 | Požaduje se
Microsoft.VisualStudio.Component.VC.CoreIde | Základní funkce C++ | 16.0.28625.61 | Požaduje se
Component.Linux.CMake | C++ CMake nástroje pro Linux | 16.2.29003.222 | Doporučené
Rozšíření microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Vývoj pro ASP.NET a web | 16.0.28621.142 | Doporučené
Component.MDD.Linux.GCC.arm | Vložené a ioT vývojové nástroje | 16.5.29515.121 | Nepovinné

## <a name="desktop-development-with-c"></a>Vývoj desktopových aplikací pomocí C++

**ID:** Microsoft.VisualStudio.Workload.NativeDesktop

**Popis:** Vytvářejte moderní aplikace C++ pro Windows pomocí nástrojů podle vašeho výběru, včetně MSVC, Clang, CMake nebo MSBuild.

### <a name="components-included-by-this-workload"></a>Komponenty zahrnuté do tohoto pracovního vytížení

ID součásti | Name (Název) | Version | Typ závislosti
--- | --- | --- | ---
Microsoft.Component.MSBuild | MSBuild | 16.5.29515.121 | Požaduje se
Microsoft.VisualStudio.Component.ClassDesigner | Návrhář tříd | 16.0.28528.71 | Požaduje se
Mapa kódu Microsoft.VisualStudio.Component.CodeMap | Mapa kódu | 16.0.28625.61 | Požaduje se
Microsoft.VisualStudio.Component.GraphDocument | Editor DGML | 16.0.28625.61 | Požaduje se
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 0.1 | Požaduje se
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilátory Roslyn jazyka C# a Visual Basic | 16.0.28714.129 | Požaduje se
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 16.0.28625.61 | Požaduje se
Microsoft.VisualStudio.Component.TextTemplating | Transformace šablony textu | 16.0.28625.61 | Požaduje se
Microsoft.VisualStudio.Component.VC.CoreIde | Základní funkce C++ | 16.0.28625.61 | Požaduje se
Microsoft.VisualStudio.Component.VC.Redist.14.Latest | Redistribuovatelná aktualizace C++ 2019 | 16.5.29515.121 | Požaduje se
Microsoft.VisualStudio.ComponentGroup.ArchitectureTools.Nativní | Nástroje architektury pro C++ | 16.0.28621.142 | Požaduje se
Soubor Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Core | Základní desktopové funkce C++ | 16.2.29012.281 | Požaduje se
Component.Microsoft.VisualStudio.LiveShare | Live Share | 1.0.1561 | Doporučené
Microsoft.VisualStudio.Component.Debugger.JustInTime | Ladicí program Just-In-Time | 16.0.28517.75 | Doporučené
Microsoft.VisualStudio.Component.Graphics.Tools | Grafický ladicí program a profiler GPU pro DirectX | 16.0.28625.61 | Doporučené
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | 16.5.29515.121 | Doporučené
Soubor Microsoft.VisualStudio.Component.NuGet | Správce balíčků NuGet | 16.1.28829.92 | Doporučené
Microsoft.VisualStudio.Component.VC.ASAN | C++ AddressSanitizer (experimentální) | 16.5.29515.121 | Doporučené
Soubor Microsoft.VisualStudio.Component.VC.ATL | C++ ATL pro nejnovější nástroje pro sestavení v142 (x86 & x64) | 16.4.29313.120 | Doporučené
Microsoft.VisualStudio.Component.VC.Cmake.Project | Nástroje C++ CMake pro Windows | 16.3.29103.31 | Doporučené
Nástroje Microsoft.VisualStudio.Component.VC.DiagnosticTools | Nástroje pro profilování jazyka C++ | 16.5.29515.121 | Doporučené
Microsoft.VisualStudio.Component.VC.TestAdapterForBoostTest | Testovací adaptér pro boost.test | 16.0.28517.75 | Doporučené
Microsoft.VisualStudio.Component.VC.TestAdapterForGoogleTest | Testovací adaptér pro test Google | 16.0.28517.75 | Doporučené
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | Nástroje sestavení MSVC v142 - VS 2019 C++ x64/x86 (v14.25) | 16.5.29721.120 | Doporučené
Microsoft.VisualStudio.Component.Windows10SDK.18362 | Windows 10 SDK (10.0.18362.0) | 16.1.28829.92 | Doporučené
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions.CMake | Editor JSON | 16.3.29207.166 | Doporučené
Komponenta.Incredibuild | IncrediBuild - Zrychlení sestavení | 16.5.29721.120 | Nepovinné
Komponenta.IncredibuildMenu | Nabídka IncrediBuild | 1.5.0.13 | Nepovinné
Soubor Microsoft.Component.VC.Runtime.UCRTSDK | Windows Universal CRT SDK | 16.0.28625.61 | Nepovinné
Microsoft.Net.Component.4.6.1.TargetingPack | Balíček cílení rozhraní .NET Framework 4.6.1 | 16.0.28517.75 | Nepovinné
Sada Microsoft.Net.Component.4.8.SdK | Rozhraní .NET Framework 4.8 SDK | 16.4.29313.120 | Nepovinné
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostika javascriptu | 16.0.28517.75 | Nepovinné
Microsoft.VisualStudio.Component.VC.140 | MSVC v140 - VS 2015 C++ nástroje pro sestavení (v14.00) | 16.0.28625.61 | Nepovinné
Soubor Microsoft.VisualStudio.Component.VC.ATLMFC | C++ Knihovna MFC pro nejnovější nástroje sestavení v142 (x86 & x64) | 16.4.29313.120 | Nepovinné
Microsoft.VisualStudio.Component.VC.CLI.Support | Podpora C++/CLI pro nástroje sestavení v142 (14.25) | 16.5.29721.120 | Nepovinné
Microsoft.VisualStudio.Component.VC.Llvm.Clang | Kompilátor C++ Clang pro Windows (9.0.0) | 16.5.29515.121 | Nepovinné
Sada nástrojů Microsoft.VisualStudio.Component.VC.Llvm.ClangToolset | C++ Clang-cl pro nástroje pro sestavení v142 (x64/x86) | 16.3.29207.166 | Nepovinné
Microsoft.VisualStudio.Component.VC.Modules.x86.x64 | Moduly C++ pro nástroje pro sestavení v142 (x64/x86 – experimentální) | 16.0.28625.61 | Nepovinné
Microsoft.VisualStudio.Component.VC.v141.x86.x64 | Nástroje sestavení MSVC v141 - VS 2017 C++ x64/x86 (v14.16) | 16.1.28829.92 | Nepovinné
Microsoft.VisualStudio.Component.Windows10SDK.16299 | Windows 10 SDK (10.0.16299.0) | 16.0.28517.75 | Nepovinné
Microsoft.VisualStudio.Component.Windows10SDK.17134 | Windows 10 SDK (10.0.17134.0) | 16.0.28517.75 | Nepovinné
Microsoft.VisualStudio.Component.Windows10SDK.17763 | Windows 10 SDK (10.0.17763.0) | 16.0.28517.75 | Nepovinné
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Llvm.Clang | C++ Clang nástroje pro Windows (9.0.0 - x64/x86) | 16.5.29514.35 | Nepovinné

## <a name="game-development-with-c"></a>Vývoj her v jazyce C++

**ID:** Microsoft.VisualStudio.Workload.NativeGame

**Popis:** Využijte plný výkon c++ k vytváření profesionálních her poháněných rozhraními DirectX, Unreal nebo Cocos2d.

### <a name="components-included-by-this-workload"></a>Komponenty zahrnuté do tohoto pracovního vytížení

ID součásti | Name (Název) | Version | Typ závislosti
--- | --- | --- | ---
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 0.1 | Požaduje se
Microsoft.VisualStudio.Component.VC.CoreIde | Základní funkce C++ | 16.0.28625.61 | Požaduje se
Microsoft.VisualStudio.Component.VC.Redist.14.Latest | Redistribuovatelná aktualizace C++ 2019 | 16.5.29515.121 | Požaduje se
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | Nástroje sestavení MSVC v142 - VS 2019 C++ x64/x86 (v14.25) | 16.5.29721.120 | Požaduje se
Microsoft.VisualStudio.Component.Windows10SDK | Windows Universal C Runtime | 16.4.29409.204 | Požaduje se
Microsoft.VisualStudio.Component.Graphics.Tools | Grafický ladicí program a profiler GPU pro DirectX | 16.0.28625.61 | Doporučené
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | 16.5.29515.121 | Doporučené
Microsoft.VisualStudio.Component.VC.ASAN | C++ AddressSanitizer (experimentální) | 16.5.29515.121 | Doporučené
Nástroje Microsoft.VisualStudio.Component.VC.DiagnosticTools | Nástroje pro profilování jazyka C++ | 16.5.29515.121 | Doporučené
Microsoft.VisualStudio.Component.Windows10SDK.18362 | Windows 10 SDK (10.0.18362.0) | 16.1.28829.92 | Doporučené
Komponenta.Android.NDK.R16B | Android NDK (R16B) | 16.5.29916.74 | Nepovinné
komponent.android.SDK25.Private | Nastavení sady Android SDK (úroveň rozhraní API 25) (místní instalace pro vývoj pro mobilní zařízení s C++) | 16.0.28625.61 | Nepovinné
Komponenta.Mat | Pašanek Apache (1.9.3) | 1.9.3.8 | Nepovinné
Component.Cocos | Cocos | 16.0.28315.86 | Nepovinné
Komponenta.Incredibuild | IncrediBuild - Zrychlení sestavení | 16.5.29721.120 | Nepovinné
Komponenta.IncredibuildMenu | Nabídka IncrediBuild | 1.5.0.13 | Nepovinné
Komponenta.MDD.Android | Vývojové nástroje pro Android pro C++ | 16.0.28517.75 | Nepovinné
komponenta OpenJDK | OpenJDK (distribuce společnosti Microsoft) | 16.1.28811.260 | Nepovinné
Komponenta.Nereálné | Instalátor unreal engine | 16.1.28810.153 | Nepovinné
Component.Unreal.Android | Podpora IDE Android pro unreal engine | 16.1.28810.153 | Nepovinné
Microsoft.Net.Component.4.5.1.TargetingPack | Balíček cílení v rámci .NET Framework 4.5.1 | 16.0.28517.75 | Nepovinné
Microsoft.Net.Component.4.5.2.TargetingPack | Balíček cílení .NET Framework 4.5.2 | 16.0.28517.75 | Nepovinné
Sada Microsoft.Net.Component.4.5.TargetingPack | Balíček cílení rozhraní .NET Framework 4.5 | 16.0.28517.75 | Nepovinné
Sada Microsoft.Net.Component.4.6.2.TargetingPack | Balíček cílení .NET Framework 4.6.2 | 16.0.28517.75 | Nepovinné
Sada Microsoft.Net.Component.4.6.TargetingPack | Balíček cílení rozhraní .NET Framework 4.6 | 16.0.28517.75 | Nepovinné
Microsoft.Net.Component.4.7.2.TargetingPack | Balíček cílení .NET Framework 4.7.2 | 16.0.28517.75 | Nepovinné
Sada Microsoft.Net.Component.4.8.SdK | Rozhraní .NET Framework 4.8 SDK | 16.4.29313.120 | Nepovinné
Sada Microsoft.Net.Component.4.TargetingPack | Balíček cílení rozhraní .NET Framework 4 | 16.0.28517.75 | Nepovinné
Microsoft.Net.ComponentGroup.DevelopmentPředpoklads | Vývojové nástroje .NET Framework 4.7.2 | 16.3.29207.166 | Nepovinné
Microsoft.Net.ComponentGroup.TargetingPacks.Common | .NET Framework 4 – 4.6 vývojové nástroje | 16.0.28516.191 | Nepovinné
Microsoft.VisualStudio.Component.NuGet.BuildTools | NuGet cíle a vytvářet úkoly | 16.1.28829.92 | Nepovinné
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilátory Roslyn jazyka C# a Visual Basic | 16.0.28714.129 | Nepovinné
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# a Visual Basic | 16.5.29515.121 | Nepovinné
Microsoft.VisualStudio.Component.Windows10SDK.16299 | Windows 10 SDK (10.0.16299.0) | 16.0.28517.75 | Nepovinné
Microsoft.VisualStudio.Component.Windows10SDK.17134 | Windows 10 SDK (10.0.17134.0) | 16.0.28517.75 | Nepovinné
Microsoft.VisualStudio.Component.Windows10SDK.17763 | Windows 10 SDK (10.0.17763.0) | 16.0.28517.75 | Nepovinné

## <a name="mobile-development-with-c"></a>Vývoj mobilních aplikací v jazyce C++

**ID:** Microsoft.VisualStudio.Workload.NativeMobile

**Popis:** Vytvářejte aplikace pro různé platformy pro iOS, Android nebo Windows pomocí C++.

### <a name="components-included-by-this-workload"></a>Komponenty zahrnuté do tohoto pracovního vytížení

ID součásti | Name (Název) | Version | Typ závislosti
--- | --- | --- | ---
komponent.android.SDK25.Private | Nastavení sady Android SDK (úroveň rozhraní API 25) (místní instalace pro vývoj pro mobilní zařízení s C++) | 16.0.28625.61 | Požaduje se
komponenta OpenJDK | OpenJDK (distribuce společnosti Microsoft) | 16.1.28811.260 | Požaduje se
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 0.1 | Požaduje se
Microsoft.VisualStudio.Component.VC.CoreIde | Základní funkce C++ | 16.0.28625.61 | Požaduje se
Komponenta.Android.NDK.R16B | Android NDK (R16B) | 16.5.29916.74 | Doporučené
Komponenta.Mat | Pašanek Apache (1.9.3) | 1.9.3.8 | Doporučené
Komponenta.MDD.Android | Vývojové nástroje pro Android pro C++ | 16.0.28517.75 | Doporučené
Komponenta.Android.NDK.R16B_3264 | Android NDK (R16B) (32bit) | 16.5.29916.74 | Nepovinné
Komponenta.Google.Android.Emulator.API25.Private | Google Android Emulátor (API Úroveň 25) (místní instalace) | 16.1.28810.153 | Nepovinné
Component.HAXM.Private | Intel Hardware Accelerated Execution Manager (HAXM) (místní instalace) | 16.0.28528.71 | Nepovinné
Komponenta.Incredibuild | IncrediBuild - Zrychlení sestavení | 16.5.29721.120 | Nepovinné
Komponenta.IncredibuildMenu | Nabídka IncrediBuild | 1.5.0.13 | Nepovinné
Komponenta.MDD.iOS | Vývojové nástroje pro iOS v C++ | 16.0.28517.75 | Nepovinné

## <a name="net-core-cross-platform-development"></a>Vývoj aplikací pro různé platformy pomocí rozhraní .NET Core

**ID:** Microsoft.VisualStudio.Workload.NetCoreTools

**Popis:** Vytvářejte aplikace napříč platformami pomocí .NET Core, ASP.NET Core, HTML/JavaScript a kontejnery včetně podpory Dockeru.

### <a name="components-included-by-this-workload"></a>Komponenty zahrnuté do tohoto pracovního vytížení

ID součásti | Name (Název) | Version | Typ závislosti
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Razor Language Services | 16.0.28714.129 | Požaduje se
Component.Microsoft.Web.LibraryManager | Správce knihovny | 16.0.28315.86 | Požaduje se
Microsoft.Component.MSBuild | MSBuild | 16.5.29515.121 | Požaduje se
Microsoft.Net.Component.4.5.2.TargetingPack | Balíček cílení .NET Framework 4.5.2 | 16.0.28517.75 | Požaduje se
Sada Microsoft.Net.Component.4.5.TargetingPack | Balíček cílení rozhraní .NET Framework 4.5 | 16.0.28517.75 | Požaduje se
Microsoft.Net.Component.4.6.1.TargetingPack | Balíček cílení rozhraní .NET Framework 4.6.1 | 16.0.28517.75 | Požaduje se
Microsoft.Net.Component.4.7.2.TargetingPack | Balíček cílení .NET Framework 4.7.2 | 16.0.28517.75 | Požaduje se
Sada Microsoft.Net.Component.4.8.SdK | Rozhraní .NET Framework 4.8 SDK | 16.4.29313.120 | Požaduje se
Microsoft.Net.ComponentGroup.DevelopmentPředpoklads | Vývojové nástroje .NET Framework 4.7.2 | 16.3.29207.166 | Požaduje se
Microsoft.Netcore.Component.DevelopmentTools | Nástroje pro vývoj .NET Core | 16.5.29721.120 | Požaduje se
Microsoft.NetCore.Component.Runtime.3.1 | Doba běhu .NET Core 3.1 LTS | 16.5.29905.7 | Požaduje se
Soubor Microsoft.Netcore.Component.SDK | Sada .NET Core SDK | 16.5.29905.7 | Požaduje se
Soubor Microsoft.Netcore.Component.Web | Nástroje pro vývoj .NET Core | 16.5.29721.120 | Požaduje se
Microsoft.VisualStudio.Component.Common.Azure.Tools | Nástroje pro konektivitu a publikování | 16.4.29409.204 | Požaduje se
Microsoft.VisualStudio.Component.DockerTools | Kontejnerové vývojové nástroje | 16.4.29409.204 | Požaduje se
Microsoft.VisualStudio.Component.FSharp | Podpora jazyka F# | 16.0.28315.86 | Požaduje se
Šablony Microsoft.VisualStudio.Component.FSharp.WebTemplates | Podpora jazyka F# pro webové projekty | 16.3.29207.166 | Požaduje se
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 16.0.28315.86 | Požaduje se
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 0.1 | Požaduje se
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostika javascriptu | 16.0.28517.75 | Požaduje se
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Podpora jazyka JavaScript a TypeScript | 16.5.29721.120 | Požaduje se
Soubor Microsoft.VisualStudio.Component.ManagedDesktop.Core | Jádro spravovaného pracovního vytížení plochy | 16.4.29318.151 | Požaduje se
Soubor Microsoft.VisualStudio.Component.MSODBC.SQL | Ovladač ODBC serveru SQL Server | 16.0.28625.61 | Požaduje se
Microsoft.VisualStudio.Component.MSSQL.CMDLnUtils | Nástroje příkazového řádku serveru SQL Server | 16.0.28707.177 | Požaduje se
Soubor Microsoft.VisualStudio.Component.NuGet | Správce balíčků NuGet | 16.1.28829.92 | Požaduje se
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilátory Roslyn jazyka C# a Visual Basic | 16.0.28714.129 | Požaduje se
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# a Visual Basic | 16.5.29515.121 | Požaduje se
Microsoft.VisualStudio.Component.SQL.ADAL | Modul runtime SQL ADAL | 16.0.28517.75 | Požaduje se
Microsoft.VisualStudio.Component.SQL.CLR | Datové typy CLR pro SQL Server | 16.0.28315.86 | Požaduje se
Microsoft.VisualStudio.Component.SQL.DataSources | Zdroje dat pro podporu serveru SQL Server | 16.0.28315.86 | Požaduje se
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 16.0.28625.61 | Požaduje se
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 16.3.29207.166 | Požaduje se
Microsoft.VisualStudio.Component.TextTemplating | Transformace šablony textu | 16.0.28625.61 | Požaduje se
Microsoft.VisualStudio.Component.TypeScript.3.8 | TypeScript 3.8 SDK | 16.0.29813.82 | Požaduje se
Microsoft.VisualStudio.ComponentGroup.Web | předpoklady pro ASP.NET a nástroje pro vývoj webových aplikací | 16.4.29318.151 | Požaduje se
Rozšíření microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Vývoj pro ASP.NET a web | 16.0.28621.142 | Požaduje se
Component.Microsoft.VisualStudio.LiveShare | Live Share | 1.0.1561 | Doporučené
Component.Microsoft.VisualStudio.Web.AzureFunkce | Nástroje Azure WebJobs | 16.0.28714.129 | Doporučené
Microsoft.Net.core.component.Sdk.2.1 | Doba běhu .NET Core 2.1 LTS | 16.5.29905.7 | Doporučené
Microsoft.VisualStudio.Component.AppInsights.Tools | Nástroje analýzy pro vývojáře | 16.5.29515.121 | Doporučené
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Vývojové nástroje Azure | 16.0.28625.61 | Doporučené
Microsoft.VisualStudio.Component.Azure.ClientLibs | Knihovny Azure pro rozhraní .NET | 16.0.28315.86 | Doporučené
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Výpočetní emulátor Azure | 16.1.28810.153 | Doporučené
Microsoft.VisualStudio.Component.Azure.Storage.Emulátor | Emulátor úložiště Azure | 16.4.29313.120 | Doporučené
Microsoft.VisualStudio.Component.CloudExplorer | Průzkumník cloudu | 16.0.28625.61 | Doporučené
Microsoft.VisualStudio.Component.Debugger.Snapshot | Ladicí program snímků | 16.5.29813.82 | Doporučené
Microsoft.VisualStudio.Component.Debugger.TimeTravel | Ladicí program cestování v čase | 16.5.29515.121 | Doporučené
Microsoft.VisualStudio.Component.DiagnosticTools | Nástroje profilování rozhraní .NET | 16.5.29515.121 | Doporučené
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | 16.5.29515.121 | Doporučené
Microsoft.VisualStudio.Component.LiveUnitTesting | Live Unit Testing | 16.1.28811.260 | Doporučené
Microsoft.VisualStudio.Component.Web | ASP.NET a nástroje pro vývoj webových aplikací | 16.0.28517.75 | Doporučené
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 16.0.28517.75 | Doporučené
Funkce Microsoft.VisualStudio.ComponentGroup.Azure | Nástroje Azure WebJobs | 16.0.28621.142 | Doporučené
Microsoft.VisualStudio.ComponentGroup.Web.CloudTools | Cloudové nástroje pro vývoj webových aplikací | 16.2.29003.222 | Doporučené
Microsoft.VisualStudio.Component.Windows10SDK.18362 | Windows 10 SDK (10.0.18362.0) | 16.1.28829.92 | Nepovinné
Vývoj souboru Microsoft.VisualStudio.ComponentGroup.IIS | Podpora služby IIS v době vývoje | 16.0.28315.86 | Nepovinné
Microsoft.VisualStudio.ComponentGroup.MSIX.Packaging | Balicí nástroje MSIX | 16.4.29409.204 | Nepovinné

## <a name="mobile-development-with-net"></a>Vývoj mobilních zařízení s rozhraním .NET

**ID:** Microsoft.VisualStudio.Workload.NetcrossPlat

**Popis:** Vytvářejte aplikace pro různé platformy pro iOS, Android nebo Windows pomocí Xamarinu.

### <a name="components-included-by-this-workload"></a>Komponenty zahrnuté do tohoto pracovního vytížení

ID součásti | Name (Název) | Version | Typ závislosti
--- | --- | --- | ---
komponenta OpenJDK | OpenJDK (distribuce společnosti Microsoft) | 16.1.28811.260 | Požaduje se
Komponenta.Xamarin | Xamarin | 16.5.29721.120 | Požaduje se
Component.Xamarin.RemotedSimulator | Simulátor vzdáleného pohybu Xamarin | 16.0.28315.86 | Požaduje se
Microsoft.Component.MSBuild | MSBuild | 16.5.29515.121 | Požaduje se
Microsoft.Net.Component.4.6.1.TargetingPack | Balíček cílení rozhraní .NET Framework 4.6.1 | 16.0.28517.75 | Požaduje se
Microsoft.Net.Component.4.7.2.TargetingPack | Balíček cílení .NET Framework 4.7.2 | 16.0.28517.75 | Požaduje se
Sada Microsoft.Net.Component.4.8.SdK | Rozhraní .NET Framework 4.8 SDK | 16.4.29313.120 | Požaduje se
Microsoft.Net.ComponentGroup.DevelopmentPředpoklads | Vývojové nástroje .NET Framework 4.7.2 | 16.3.29207.166 | Požaduje se
Microsoft.Netcore.Component.DevelopmentTools | Nástroje pro vývoj .NET Core | 16.5.29721.120 | Požaduje se
Microsoft.NetCore.Component.Runtime.3.1 | Doba běhu .NET Core 3.1 LTS | 16.5.29905.7 | Požaduje se
Soubor Microsoft.Netcore.Component.SDK | Sada .NET Core SDK | 16.5.29905.7 | Požaduje se
Microsoft.VisualStudio.Component.FSharp | Podpora jazyka F# | 16.0.28315.86 | Požaduje se
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 0.1 | Požaduje se
Soubor Microsoft.VisualStudio.Component.Merq | Běžné interní nástroje Xamarin | 16.2.29012.281 | Požaduje se
Microsoft.VisualStudio.Component.MonoDebugger | Jednoladění | 16.0.28517.75 | Požaduje se
Soubor Microsoft.VisualStudio.Component.NuGet | Správce balíčků NuGet | 16.1.28829.92 | Požaduje se
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilátory Roslyn jazyka C# a Visual Basic | 16.0.28714.129 | Požaduje se
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# a Visual Basic | 16.5.29515.121 | Požaduje se
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions.TemplateEngine | ASP.NET templating motor | 16.0.28315.86 | Požaduje se
Komponenta.Android.SDK28 | Nastavení sady Android SDK (úroveň rozhraní API 28) | 16.2.29003.222 | Doporučené

## <a name="aspnet-and-web-development"></a>Vývoj pro ASP.NET a web

**ID:** Microsoft.VisualStudio.Workload.NetWeb

**Popis:** Vytvářejte webové aplikace pomocí ASP.NET jádra, ASP.NET, HTML/JavaScriptu a kontejnerů, včetně podpory Dockeru.

### <a name="components-included-by-this-workload"></a>Komponenty zahrnuté do tohoto pracovního vytížení

ID součásti | Name (Název) | Version | Typ závislosti
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Razor Language Services | 16.0.28714.129 | Požaduje se
Component.Microsoft.Web.LibraryManager | Správce knihovny | 16.0.28315.86 | Požaduje se
Microsoft.Component.MSBuild | MSBuild | 16.5.29515.121 | Požaduje se
Microsoft.Net.Component.4.5.2.TargetingPack | Balíček cílení .NET Framework 4.5.2 | 16.0.28517.75 | Požaduje se
Sada Microsoft.Net.Component.4.5.TargetingPack | Balíček cílení rozhraní .NET Framework 4.5 | 16.0.28517.75 | Požaduje se
Microsoft.Net.Component.4.6.1.TargetingPack | Balíček cílení rozhraní .NET Framework 4.6.1 | 16.0.28517.75 | Požaduje se
Microsoft.Net.Component.4.7.2.TargetingPack | Balíček cílení .NET Framework 4.7.2 | 16.0.28517.75 | Požaduje se
Sada Microsoft.Net.Component.4.8.SdK | Rozhraní .NET Framework 4.8 SDK | 16.4.29313.120 | Požaduje se
Microsoft.Net.ComponentGroup.DevelopmentPředpoklads | Vývojové nástroje .NET Framework 4.7.2 | 16.3.29207.166 | Požaduje se
Microsoft.Netcore.Component.DevelopmentTools | Nástroje pro vývoj .NET Core | 16.5.29721.120 | Požaduje se
Microsoft.NetCore.Component.Runtime.3.1 | Doba běhu .NET Core 3.1 LTS | 16.5.29905.7 | Požaduje se
Soubor Microsoft.Netcore.Component.SDK | Sada .NET Core SDK | 16.5.29905.7 | Požaduje se
Soubor Microsoft.Netcore.Component.Web | Nástroje pro vývoj .NET Core | 16.5.29721.120 | Požaduje se
Microsoft.VisualStudio.Component.Common.Azure.Tools | Nástroje pro konektivitu a publikování | 16.4.29409.204 | Požaduje se
Microsoft.VisualStudio.Component.DockerTools | Kontejnerové vývojové nástroje | 16.4.29409.204 | Požaduje se
Microsoft.VisualStudio.Component.FSharp | Podpora jazyka F# | 16.0.28315.86 | Požaduje se
Šablony Microsoft.VisualStudio.Component.FSharp.WebTemplates | Podpora jazyka F# pro webové projekty | 16.3.29207.166 | Požaduje se
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 16.0.28315.86 | Požaduje se
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 0.1 | Požaduje se
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostika javascriptu | 16.0.28517.75 | Požaduje se
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Podpora jazyka JavaScript a TypeScript | 16.5.29721.120 | Požaduje se
Soubor Microsoft.VisualStudio.Component.ManagedDesktop.Core | Jádro spravovaného pracovního vytížení plochy | 16.4.29318.151 | Požaduje se
Soubor Microsoft.VisualStudio.Component.MSODBC.SQL | Ovladač ODBC serveru SQL Server | 16.0.28625.61 | Požaduje se
Microsoft.VisualStudio.Component.MSSQL.CMDLnUtils | Nástroje příkazového řádku serveru SQL Server | 16.0.28707.177 | Požaduje se
Soubor Microsoft.VisualStudio.Component.NuGet | Správce balíčků NuGet | 16.1.28829.92 | Požaduje se
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilátory Roslyn jazyka C# a Visual Basic | 16.0.28714.129 | Požaduje se
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# a Visual Basic | 16.5.29515.121 | Požaduje se
Microsoft.VisualStudio.Component.SQL.ADAL | Modul runtime SQL ADAL | 16.0.28517.75 | Požaduje se
Microsoft.VisualStudio.Component.SQL.CLR | Datové typy CLR pro SQL Server | 16.0.28315.86 | Požaduje se
Microsoft.VisualStudio.Component.SQL.DataSources | Zdroje dat pro podporu serveru SQL Server | 16.0.28315.86 | Požaduje se
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 16.0.28625.61 | Požaduje se
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 16.3.29207.166 | Požaduje se
Microsoft.VisualStudio.Component.TextTemplating | Transformace šablony textu | 16.0.28625.61 | Požaduje se
Microsoft.VisualStudio.Component.TypeScript.3.8 | TypeScript 3.8 SDK | 16.0.29813.82 | Požaduje se
Microsoft.VisualStudio.Component.Web | ASP.NET a nástroje pro vývoj webových aplikací | 16.0.28517.75 | Požaduje se
Microsoft.VisualStudio.ComponentGroup.Web | předpoklady pro ASP.NET a nástroje pro vývoj webových aplikací | 16.4.29318.151 | Požaduje se
Rozšíření microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Vývoj pro ASP.NET a web | 16.0.28621.142 | Požaduje se
Component.Microsoft.VisualStudio.LiveShare | Live Share | 1.0.1561 | Doporučené
Component.Microsoft.VisualStudio.Web.AzureFunkce | Nástroje Azure WebJobs | 16.0.28714.129 | Doporučené
Microsoft.Net.Component.4.5.1.TargetingPack | Balíček cílení v rámci .NET Framework 4.5.1 | 16.0.28517.75 | Doporučené
Sada Microsoft.Net.Component.4.6.TargetingPack | Balíček cílení rozhraní .NET Framework 4.6 | 16.0.28517.75 | Doporučené
Sada Microsoft.Net.Component.4.TargetingPack | Balíček cílení rozhraní .NET Framework 4 | 16.0.28517.75 | Doporučené
Microsoft.Net.ComponentGroup.TargetingPacks.Common | .NET Framework 4 – 4.6 vývojové nástroje | 16.0.28516.191 | Doporučené
Microsoft.Net.core.component.Sdk.2.1 | Doba běhu .NET Core 2.1 LTS | 16.5.29905.7 | Doporučené
Microsoft.VisualStudio.Component.AppInsights.Tools | Nástroje analýzy pro vývojáře | 16.5.29515.121 | Doporučené
Microsoft.VisualStudio.Component.AspNet45 | Pokročilé ASP.NET funkce | 16.0.28315.86 | Doporučené
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Vývojové nástroje Azure | 16.0.28625.61 | Doporučené
Microsoft.VisualStudio.Component.Azure.ClientLibs | Knihovny Azure pro rozhraní .NET | 16.0.28315.86 | Doporučené
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Výpočetní emulátor Azure | 16.1.28810.153 | Doporučené
Microsoft.VisualStudio.Component.Azure.Storage.Emulátor | Emulátor úložiště Azure | 16.4.29313.120 | Doporučené
Microsoft.VisualStudio.Component.CloudExplorer | Průzkumník cloudu | 16.0.28625.61 | Doporučené
Microsoft.VisualStudio.Component.Debugger.Snapshot | Ladicí program snímků | 16.5.29813.82 | Doporučené
Microsoft.VisualStudio.Component.Debugger.TimeTravel | Ladicí program cestování v čase | 16.5.29515.121 | Doporučené
Microsoft.VisualStudio.Component.DiagnosticTools | Nástroje profilování rozhraní .NET | 16.5.29515.121 | Doporučené
Microsoft.VisualStudio.Component.EntityFramework | Nástroje entity Framework 6 | 16.0.28315.86 | Doporučené
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | 16.5.29515.121 | Doporučené
Microsoft.VisualStudio.Component.LiveUnitTesting | Live Unit Testing | 16.1.28811.260 | Doporučené
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 16.0.28517.75 | Doporučené
Funkce Microsoft.VisualStudio.ComponentGroup.Azure | Nástroje Azure WebJobs | 16.0.28621.142 | Doporučené
Microsoft.VisualStudio.ComponentGroup.Web.CloudTools | Cloudové nástroje pro vývoj webových aplikací | 16.2.29003.222 | Doporučené
Sada Microsoft.Net.Component.4.6.2.TargetingPack | Balíček cílení .NET Framework 4.6.2 | 16.0.28517.75 | Nepovinné
Microsoft.Net.Component.4.7.1.TargetingPack | Balíček cílení .NET Framework 4.7.1 | 16.0.28517.75 | Nepovinné
Sada Microsoft.Net.Component.4.7.TargetingPack | Balíček cílení rozhraní .NET Framework 4.7 | 16.0.28517.75 | Nepovinné
Sada Microsoft.Net.Component.4.8.TargetingPack | Balíček cílení rozhraní .NET Framework 4.8 | 16.4.29313.120 | Nepovinné
Microsoft.Net.ComponentGroup.4.6.1.DeveloperTools | Vývojové nástroje .NET Framework 4.6.1 | 16.3.29207.166 | Nepovinné
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | Vývojové nástroje .NET Framework 4.6.2 | 16.3.29207.166 | Nepovinné
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | Vývojové nástroje .NET Framework 4.7.1 | 16.3.29207.166 | Nepovinné
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | Vývojové nástroje rozhraní .NET Framework 4.7 | 16.3.29207.166 | Nepovinné
Microsoft.Net.ComponentGroup.4.8.DeveloperTools | Vývojové nástroje rozhraní .NET Framework 4.8 | 16.4.29318.151 | Nepovinné
Microsoft.VisualStudio.Component.ClassDesigner | Návrhář tříd | 16.0.28528.71 | Nepovinné
Microsoft.VisualStudio.Component.CodeClone | Klon kódu | 16.4.29409.204 | Nepovinné
Mapa kódu Microsoft.VisualStudio.Component.CodeMap | Mapa kódu | 16.0.28625.61 | Nepovinné
Microsoft.VisualStudio.Component.DependencyValidation.Enterprise | Ověření živé závislosti | 16.0.28625.61 | Nepovinné
Microsoft.VisualStudio.Component.GraphDocument | Editor DGML | 16.0.28625.61 | Nepovinné
Microsoft.VisualStudio.Component.TestTools.WebLoadTest | Nástroje pro testování výkonu webu a zatížení | 16.0.28625.61 | Nepovinné
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | 16.0.28625.61 | Nepovinné
Microsoft.VisualStudio.ComponentGroup.AdditionalWebProjectTemplates | Další šablony projektů (předchozí verze) | 16.0.28621.142 | Nepovinné
Microsoft.VisualStudio.ComponentGroup.ArchitectureTools.Managed | Nástroje pro architekturu a analýzu | 16.5.29514.35 | Nepovinné
Vývoj souboru Microsoft.VisualStudio.ComponentGroup.IIS | Podpora služby IIS v době vývoje | 16.0.28315.86 | Nepovinné

## <a name="nodejs-development"></a>Vývoj souboru Node.js

**ID:** Uzel Microsoft.VisualStudio.Workload.Node

**Popis:** Vytvářejte škálovatelné síťové aplikace pomocí souboru Node.js, což je asynchronní modul javascriptu řízený událostmi. 

### <a name="components-included-by-this-workload"></a>Komponenty zahrnuté do tohoto pracovního vytížení

ID součásti | Name (Název) | Version | Typ závislosti
--- | --- | --- | ---
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostika javascriptu | 16.0.28517.75 | Požaduje se
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Podpora jazyka JavaScript a TypeScript | 16.5.29721.120 | Požaduje se
Microsoft.VisualStudio.Component.Node.Tools | Vývojové nástroje Node.js | 16.5.29515.121 | Požaduje se
Microsoft.VisualStudio.Component.TypeScript.3.8 | TypeScript 3.8 SDK | 16.0.29813.82 | Požaduje se
Rozšíření microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Vývoj pro ASP.NET a web | 16.0.28621.142 | Požaduje se
Component.Microsoft.VisualStudio.LiveShare | Live Share | 1.0.1561 | Doporučené
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 0.1 | Doporučené
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 16.0.28517.75 | Doporučené
Microsoft.VisualStudio.Component.AppInsights.Tools | Nástroje analýzy pro vývojáře | 16.5.29515.121 | Nepovinné
Microsoft.VisualStudio.Component.Common.Azure.Tools | Nástroje pro konektivitu a publikování | 16.4.29409.204 | Nepovinné
Microsoft.VisualStudio.Component.VC.CoreIde | Základní funkce C++ | 16.0.28625.61 | Nepovinné
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | Nástroje sestavení MSVC v142 - VS 2019 C++ x64/x86 (v14.25) | 16.5.29721.120 | Nepovinné

## <a name="officesharepoint-development"></a>Vývoj Office/SharePointu

**ID:** Microsoft.VisualStudio.Workload.Office

**Popis:** Vytvořte doplňky Office a SharePointu, sharepointová řešení a doplňky VSTO pomocí C#, VB a JavaScriptu.

### <a name="components-included-by-this-workload"></a>Komponenty zahrnuté do tohoto pracovního vytížení

ID součásti | Name (Název) | Version | Typ závislosti
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Razor Language Services | 16.0.28714.129 | Požaduje se
Component.Microsoft.Web.LibraryManager | Správce knihovny | 16.0.28315.86 | Požaduje se
Microsoft.Component.MSBuild | MSBuild | 16.5.29515.121 | Požaduje se
Microsoft.Net.Component.4.5.2.TargetingPack | Balíček cílení .NET Framework 4.5.2 | 16.0.28517.75 | Požaduje se
Sada Microsoft.Net.Component.4.5.TargetingPack | Balíček cílení rozhraní .NET Framework 4.5 | 16.0.28517.75 | Požaduje se
Microsoft.Net.Component.4.6.1.TargetingPack | Balíček cílení rozhraní .NET Framework 4.6.1 | 16.0.28517.75 | Požaduje se
Microsoft.Net.Component.4.7.2.TargetingPack | Balíček cílení .NET Framework 4.7.2 | 16.0.28517.75 | Požaduje se
Sada Microsoft.Net.Component.4.8.SdK | Rozhraní .NET Framework 4.8 SDK | 16.4.29313.120 | Požaduje se
Sada Microsoft.Net.Component.4.TargetingPack | Balíček cílení rozhraní .NET Framework 4 | 16.0.28517.75 | Požaduje se
Microsoft.Net.ComponentGroup.DevelopmentPředpoklads | Vývojové nástroje .NET Framework 4.7.2 | 16.3.29207.166 | Požaduje se
Microsoft.NetCore.Component.Runtime.3.1 | Doba běhu .NET Core 3.1 LTS | 16.5.29905.7 | Požaduje se
Soubor Microsoft.Netcore.Component.SDK | Sada .NET Core SDK | 16.5.29905.7 | Požaduje se
Microsoft.VisualStudio.Component.AppInsights.Tools | Nástroje analýzy pro vývojáře | 16.5.29515.121 | Požaduje se
Microsoft.VisualStudio.Component.Common.Azure.Tools | Nástroje pro konektivitu a publikování | 16.4.29409.204 | Požaduje se
Microsoft.VisualStudio.Component.DockerTools | Kontejnerové vývojové nástroje | 16.4.29409.204 | Požaduje se
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 16.0.28315.86 | Požaduje se
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 0.1 | Požaduje se
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostika javascriptu | 16.0.28517.75 | Požaduje se
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Podpora jazyka JavaScript a TypeScript | 16.5.29721.120 | Požaduje se
Soubor Microsoft.VisualStudio.Component.ManagedDesktop.Core | Jádro spravovaného pracovního vytížení plochy | 16.4.29318.151 | Požaduje se
Microsoft.VisualStudio.Component.ManagedDesktop.Prerequisites | Nástroje pro vývoj stolních počítačů .NET | 16.5.29514.35 | Požaduje se
Soubor Microsoft.VisualStudio.Component.MSODBC.SQL | Ovladač ODBC serveru SQL Server | 16.0.28625.61 | Požaduje se
Microsoft.VisualStudio.Component.MSSQL.CMDLnUtils | Nástroje příkazového řádku serveru SQL Server | 16.0.28707.177 | Požaduje se
Soubor Microsoft.VisualStudio.Component.NuGet | Správce balíčků NuGet | 16.1.28829.92 | Požaduje se
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilátory Roslyn jazyka C# a Visual Basic | 16.0.28714.129 | Požaduje se
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# a Visual Basic | 16.5.29515.121 | Požaduje se
Microsoft.VisualStudio.Component.Sharepoint.Tools | Office Developer Tools for Visual Studio | 16.4.29409.204 | Požaduje se
Microsoft.VisualStudio.Component.SQL.ADAL | Modul runtime SQL ADAL | 16.0.28517.75 | Požaduje se
Microsoft.VisualStudio.Component.SQL.CLR | Datové typy CLR pro SQL Server | 16.0.28315.86 | Požaduje se
Microsoft.VisualStudio.Component.SQL.DataSources | Zdroje dat pro podporu serveru SQL Server | 16.0.28315.86 | Požaduje se
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 16.0.28625.61 | Požaduje se
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 16.3.29207.166 | Požaduje se
Microsoft.VisualStudio.Component.TextTemplating | Transformace šablony textu | 16.0.28625.61 | Požaduje se
Microsoft.VisualStudio.Component.TypeScript.3.8 | TypeScript 3.8 SDK | 16.0.29813.82 | Požaduje se
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | 16.0.28625.61 | Požaduje se
Microsoft.VisualStudio.Component.Web | ASP.NET a nástroje pro vývoj webových aplikací | 16.0.28517.75 | Požaduje se
Microsoft.VisualStudio.Component.Workflow | Windows Workflow Foundation | 16.0.28315.86 | Požaduje se
Microsoft.VisualStudio.ComponentGroup.Web | předpoklady pro ASP.NET a nástroje pro vývoj webových aplikací | 16.4.29318.151 | Požaduje se
Rozšíření microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Vývoj pro ASP.NET a web | 16.0.28621.142 | Požaduje se
Microsoft.VisualStudio.Component.TeamOffice | Nástroje Visual Studia pro Office (VSTO) | 16.4.29409.204 | Doporučené
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 16.0.28517.75 | Doporučené
Sada Microsoft.Net.Component.4.6.2.TargetingPack | Balíček cílení .NET Framework 4.6.2 | 16.0.28517.75 | Nepovinné
Microsoft.Net.Component.4.7.1.TargetingPack | Balíček cílení .NET Framework 4.7.1 | 16.0.28517.75 | Nepovinné
Sada Microsoft.Net.Component.4.7.TargetingPack | Balíček cílení rozhraní .NET Framework 4.7 | 16.0.28517.75 | Nepovinné
Sada Microsoft.Net.Component.4.8.TargetingPack | Balíček cílení rozhraní .NET Framework 4.8 | 16.4.29313.120 | Nepovinné
Microsoft.Net.ComponentGroup.4.6.1.DeveloperTools | Vývojové nástroje .NET Framework 4.6.1 | 16.3.29207.166 | Nepovinné
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | Vývojové nástroje .NET Framework 4.6.2 | 16.3.29207.166 | Nepovinné
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | Vývojové nástroje .NET Framework 4.7.1 | 16.3.29207.166 | Nepovinné
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | Vývojové nástroje rozhraní .NET Framework 4.7 | 16.3.29207.166 | Nepovinné
Microsoft.Net.ComponentGroup.4.8.DeveloperTools | Vývojové nástroje rozhraní .NET Framework 4.8 | 16.4.29318.151 | Nepovinné
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | 16.5.29515.121 | Nepovinné
Soubor Microsoft.VisualStudio.ComponentGroup.Sharepoint.WIF | Windows Identity Foundation 3.5 | 16.0.28621.142 | Nepovinné

## <a name="python-development"></a>Vývoj Pythonu

**ID:** Microsoft.VisualStudio.Workload.Python

**Popis:** Editace, ladění, interaktivní vývoj a směřování zdrojů pro Python.

### <a name="components-included-by-this-workload"></a>Komponenty zahrnuté do tohoto pracovního vytížení

ID součásti | Name (Název) | Version | Typ závislosti
--- | --- | --- | ---
Microsoft.Component.PythonTools | Podpora jazyka Pythonu | 16.5.29515.121 | Požaduje se
Component.CPython3.x64 | Python 3 64bitový (3.7.5) | 3.7.5 | Doporučené
Component.Microsoft.VisualStudio.LiveShare | Live Share | 1.0.1561 | Doporučené
Microsoft.Component.PythonTools.Minicondax64 | Python miniconda | 16.2.29003.222 | Doporučené
Microsoft.Component.PythonTools.Web | Webová podpora pythonu | 16.0.28517.75 | Doporučené
Microsoft.VisualStudio.Component.Common.Azure.Tools | Nástroje pro konektivitu a publikování | 16.4.29409.204 | Doporučené
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Podpora jazyka JavaScript a TypeScript | 16.5.29721.120 | Doporučené
Microsoft.VisualStudio.Component.TypeScript.3.8 | TypeScript 3.8 SDK | 16.0.29813.82 | Doporučené
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 16.0.28517.75 | Doporučené
Rozšíření microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Vývoj pro ASP.NET a web | 16.0.28621.142 | Doporučené
Komponenta.CPython2.x64 | Python 2 64bitový (2.7.16) | 2.7.16 | Nepovinné
Component.CPython2.x86 | Python 2 32bitový (2.7.16) | 2.7.16 | Nepovinné
Component.CPython3.x86 | Python 3 32bitový (3.7.5) | 3.7.5 | Nepovinné
Component.Microsoft.VisualStudio.RazorExtension | Razor Language Services | 16.0.28714.129 | Nepovinné
Component.Microsoft.Web.LibraryManager | Správce knihovny | 16.0.28315.86 | Nepovinné
Microsoft.Component.MSBuild | MSBuild | 16.5.29515.121 | Nepovinné
Vývoj souboru Microsoft.ComponentGroup.PythonTools.NativeDevelopment | Nativní vývojové nástroje Pythonu | 16.2.29020.229 | Nepovinné
Microsoft.Net.Component.4.5.2.TargetingPack | Balíček cílení .NET Framework 4.5.2 | 16.0.28517.75 | Nepovinné
Sada Microsoft.Net.Component.4.5.TargetingPack | Balíček cílení rozhraní .NET Framework 4.5 | 16.0.28517.75 | Nepovinné
Microsoft.Net.Component.4.7.2.TargetingPack | Balíček cílení .NET Framework 4.7.2 | 16.0.28517.75 | Nepovinné
Sada Microsoft.Net.Component.4.8.SdK | Rozhraní .NET Framework 4.8 SDK | 16.4.29313.120 | Nepovinné
Microsoft.Net.ComponentGroup.DevelopmentPředpoklads | Vývojové nástroje .NET Framework 4.7.2 | 16.3.29207.166 | Nepovinné
Microsoft.NetCore.Component.Runtime.3.1 | Doba běhu .NET Core 3.1 LTS | 16.5.29905.7 | Nepovinné
Soubor Microsoft.Netcore.Component.SDK | Sada .NET Core SDK | 16.5.29905.7 | Nepovinné
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Vývojové nástroje Azure | 16.0.28625.61 | Nepovinné
Microsoft.VisualStudio.Component.Azure.ClientLibs | Knihovny Azure pro rozhraní .NET | 16.0.28315.86 | Nepovinné
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Výpočetní emulátor Azure | 16.1.28810.153 | Nepovinné
Microsoft.VisualStudio.Component.Azure.Storage.Emulátor | Emulátor úložiště Azure | 16.4.29313.120 | Nepovinné
Microsoft.VisualStudio.Component.Azure.Waverton | Základní nástroje Cloudových služeb Azure | 16.4.29409.204 | Nepovinné
Microsoft.VisualStudio.Component.Azure.Waverton.BuildTools | Nástroje pro vytváření cloudových služeb Azure | 16.3.29207.166 | Nepovinné
Microsoft.VisualStudio.Component.DockerTools | Kontejnerové vývojové nástroje | 16.4.29409.204 | Nepovinné
Microsoft.VisualStudio.Component.Graphics.Tools | Grafický ladicí program a profiler GPU pro DirectX | 16.0.28625.61 | Nepovinné
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 16.0.28315.86 | Nepovinné
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostika javascriptu | 16.0.28517.75 | Nepovinné
Soubor Microsoft.VisualStudio.Component.ManagedDesktop.Core | Jádro spravovaného pracovního vytížení plochy | 16.4.29318.151 | Nepovinné
Soubor Microsoft.VisualStudio.Component.MSODBC.SQL | Ovladač ODBC serveru SQL Server | 16.0.28625.61 | Nepovinné
Microsoft.VisualStudio.Component.MSSQL.CMDLnUtils | Nástroje příkazového řádku serveru SQL Server | 16.0.28707.177 | Nepovinné
Soubor Microsoft.VisualStudio.Component.NuGet | Správce balíčků NuGet | 16.1.28829.92 | Nepovinné
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilátory Roslyn jazyka C# a Visual Basic | 16.0.28714.129 | Nepovinné
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# a Visual Basic | 16.5.29515.121 | Nepovinné
Microsoft.VisualStudio.Component.SQL.ADAL | Modul runtime SQL ADAL | 16.0.28517.75 | Nepovinné
Microsoft.VisualStudio.Component.SQL.CLR | Datové typy CLR pro SQL Server | 16.0.28315.86 | Nepovinné
Microsoft.VisualStudio.Component.SQL.DataSources | Zdroje dat pro podporu serveru SQL Server | 16.0.28315.86 | Nepovinné
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 16.0.28625.61 | Nepovinné
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 16.3.29207.166 | Nepovinné
Microsoft.VisualStudio.Component.TextTemplating | Transformace šablony textu | 16.0.28625.61 | Nepovinné
Microsoft.VisualStudio.Component.VC.CoreIde | Základní funkce C++ | 16.0.28625.61 | Nepovinné
Nástroje Microsoft.VisualStudio.Component.VC.DiagnosticTools | Nástroje pro profilování jazyka C++ | 16.5.29515.121 | Nepovinné
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | Nástroje sestavení MSVC v142 - VS 2019 C++ x64/x86 (v14.25) | 16.5.29721.120 | Nepovinné
Microsoft.VisualStudio.Component.Web | ASP.NET a nástroje pro vývoj webových aplikací | 16.0.28517.75 | Nepovinné
Microsoft.VisualStudio.Component.Windows10SDK | Windows Universal C Runtime | 16.4.29409.204 | Nepovinné
Microsoft.VisualStudio.Component.Windows10SDK.18362 | Windows 10 SDK (10.0.18362.0) | 16.1.28829.92 | Nepovinné
Microsoft.VisualStudio.ComponentGroup.Web | předpoklady pro ASP.NET a nástroje pro vývoj webových aplikací | 16.4.29318.151 | Nepovinné

## <a name="universal-windows-platform-development"></a>Vývoj univerzální platformy Windows

**ID:** Microsoft.VisualStudio.Workload.Universal

**Popis:** Vytvořte aplikace pro univerzální platformu Windows s C#, VB nebo volitelně C++.

### <a name="components-included-by-this-workload"></a>Komponenty zahrnuté do tohoto pracovního vytížení

ID součásti | Name (Název) | Version | Typ závislosti
--- | --- | --- | ---
Microsoft.Component.NetFX.Nativní | .NET Native | 16.5.29515.121 | Požaduje se
Microsoft.ComponentGroup.Blend | Blend for Visual Studio | 16.0.28315.86 | Požaduje se
Sada Microsoft.Net.Component.4.5.TargetingPack | Balíček cílení rozhraní .NET Framework 4.5 | 16.0.28517.75 | Požaduje se
Microsoft.NetCore.Component.Runtime.3.1 | Doba běhu .NET Core 3.1 LTS | 16.5.29905.7 | Požaduje se
Soubor Microsoft.Netcore.Component.SDK | Sada .NET Core SDK | 16.5.29905.7 | Požaduje se
Microsoft.VisualStudio.Component.AppInsights.Tools | Nástroje analýzy pro vývojáře | 16.5.29515.121 | Požaduje se
Microsoft.VisualStudio.Component.DiagnosticTools | Nástroje profilování rozhraní .NET | 16.5.29515.121 | Požaduje se
Microsoft.VisualStudio.Component.Graphics | Editory obrázků a 3D modelů | 16.0.28517.75 | Požaduje se
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 0.1 | Požaduje se
Soubor Microsoft.VisualStudio.Component.NuGet | Správce balíčků NuGet | 16.1.28829.92 | Požaduje se
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilátory Roslyn jazyka C# a Visual Basic | 16.0.28714.129 | Požaduje se
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# a Visual Basic | 16.5.29515.121 | Požaduje se
Microsoft.VisualStudio.Component.SQL.CLR | Datové typy CLR pro SQL Server | 16.0.28315.86 | Požaduje se
Microsoft.VisualStudio.Component.Windows10SDK.18362 | Windows 10 SDK (10.0.18362.0) | 16.1.28829.92 | Požaduje se
Microsoft.VisualStudio.ComponentGroup.MSIX.Packaging | Balicí nástroje MSIX | 16.4.29409.204 | Požaduje se
Microsoft.VisualStudio.ComponentGroup.UWP.NetcoreAndStandard | Nativní rozhraní .NET a standard .NET | 16.3.29102.218 | Požaduje se
Podpora microsoft.visualstudio.componentgroup.uWP.support | Univerzální nástroje platformy Windows | 16.4.29409.204 | Požaduje se
Microsoft.VisualStudio.ComponentGroup.UWP.Xamarin | Univerzální nástroje platformy Windows pro Xamarin | 16.5.29514.35 | Požaduje se
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | 16.5.29515.121 | Doporučené
Microsoft.Component.MSBuild | MSBuild | 16.5.29515.121 | Nepovinné
Sada Microsoft.Net.Component.4.8.SdK | Rozhraní .NET Framework 4.8 SDK | 16.4.29313.120 | Nepovinné
Microsoft.VisualStudio.Component.ClassDesigner | Návrhář tříd | 16.0.28528.71 | Nepovinné
Microsoft.VisualStudio.Component.CodeClone | Klon kódu | 16.4.29409.204 | Nepovinné
Mapa kódu Microsoft.VisualStudio.Component.CodeMap | Mapa kódu | 16.0.28625.61 | Nepovinné
Microsoft.VisualStudio.Component.DependencyValidation.Enterprise | Ověření živé závislosti | 16.0.28625.61 | Nepovinné
Microsoft.VisualStudio.Component.GraphDocument | Editor DGML | 16.0.28625.61 | Nepovinné
Microsoft.VisualStudio.Component.Graphics.Tools | Grafický ladicí program a profiler GPU pro DirectX | 16.0.28625.61 | Nepovinné
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 16.0.28625.61 | Nepovinné
Microsoft.VisualStudio.Component.TextTemplating | Transformace šablony textu | 16.0.28625.61 | Nepovinné
Microsoft.VisualStudio.Component.UWP.VC.ARM64 | Podpora univerzální platformy Windows pro nástroje pro sestavení v142 (ARM64) | 16.3.29207.166 | Nepovinné
Microsoft.VisualStudio.Component.VC.CoreIde | Základní funkce C++ | 16.0.28625.61 | Nepovinné
Microsoft.VisualStudio.Component.VC.Redist.14.Latest | Redistribuovatelná aktualizace C++ 2019 | 16.5.29515.121 | Nepovinné
Microsoft.VisualStudio.Component.VC.Tools.ARM | MSVC v142 - VS 2019 C++ ARM nástroje pro sestavení (v14.25) | 16.5.29721.120 | Nepovinné
Microsoft.VisualStudio.Component.VC.Tools.ARM64 | Nástroje pro sestavení MSVC v142 - VS 2019 C++ ARM64 (v14.25) | 16.5.29721.120 | Nepovinné
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | Nástroje sestavení MSVC v142 - VS 2019 C++ x64/x86 (v14.25) | 16.5.29721.120 | Nepovinné
Microsoft.VisualStudio.Component.VC.v141.ARM | MSVC v141 - VS 2017 C++ ARM nástroje pro sestavení (v14.16) | 16.2.29003.222 | Nepovinné
Microsoft.VisualStudio.Component.VC.v141.ARM64 | MSVC v141 - VS 2017 C++ ARM64 nástroje sestavení (v14.16) | 16.1.28829.92 | Nepovinné
Microsoft.VisualStudio.Component.VC.v141.x86.x64 | Nástroje sestavení MSVC v141 - VS 2017 C++ x64/x86 (v14.16) | 16.1.28829.92 | Nepovinné
Microsoft.VisualStudio.Component.Windows10SDK.16299 | Windows 10 SDK (10.0.16299.0) | 16.0.28517.75 | Nepovinné
Microsoft.VisualStudio.Component.Windows10SDK.17134 | Windows 10 SDK (10.0.17134.0) | 16.0.28517.75 | Nepovinné
Microsoft.VisualStudio.Component.Windows10SDK.17763 | Windows 10 SDK (10.0.17763.0) | 16.0.28517.75 | Nepovinné
Microsoft.VisualStudio.Component.Windows10SDK.19041 | Windows 10 Náhled SDK (10.0.19041.0) | 16.5.29721.120 | Nepovinné
Microsoft.VisualStudio.Component.Windows10SDK.ipoverusb | Připojení zařízení USB | 16.5.29515.121 | Nepovinné
Microsoft.VisualStudio.ComponentGroup.ArchitectureTools.Managed | Nástroje pro architekturu a analýzu | 16.5.29514.35 | Nepovinné
Microsoft.VisualStudio.ComponentGroup.ArchitectureTools.Nativní | Nástroje architektury pro C++ | 16.0.28621.142 | Nepovinné
Soubor Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Core | Základní desktopové funkce C++ | 16.2.29012.281 | Nepovinné
Microsoft.VisualStudio.ComponentGroup.UWP.VC | Nástroje univerzální platformy Windows pro C++ (v142) | 16.3.29207.166 | Nepovinné
Microsoft.VisualStudio.ComponentGroup.UWP.VC.v141 | Nástroje univerzální platformy Windows pro C++ (v141) | 16.1.28810.153 | Nepovinné

## <a name="visual-studio-extension-development"></a>Vývoj rozšíření sady Visual Studio

**ID:** Rozšíření Microsoft.VisualStudio.Workload.VisualStudioExtension

**Popis:** Vytvořte doplňky a rozšíření pro Visual Studio, včetně nových příkazů, analyzátorů kódu a oken nástrojů.

### <a name="components-included-by-this-workload"></a>Komponenty zahrnuté do tohoto pracovního vytížení

ID součásti | Name (Název) | Version | Typ závislosti
--- | --- | --- | ---
Microsoft.Component.MSBuild | MSBuild | 16.5.29515.121 | Požaduje se
Sada Microsoft.Net.Component.4.6.TargetingPack | Balíček cílení rozhraní .NET Framework 4.6 | 16.0.28517.75 | Požaduje se
Microsoft.Net.Component.4.7.2.TargetingPack | Balíček cílení .NET Framework 4.7.2 | 16.0.28517.75 | Požaduje se
Sada Microsoft.Net.Component.4.8.SdK | Rozhraní .NET Framework 4.8 SDK | 16.4.29313.120 | Požaduje se
Microsoft.Net.ComponentGroup.DevelopmentPředpoklads | Vývojové nástroje .NET Framework 4.7.2 | 16.3.29207.166 | Požaduje se
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 0.1 | Požaduje se
Soubor Microsoft.VisualStudio.Component.NuGet | Správce balíčků NuGet | 16.1.28829.92 | Požaduje se
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilátory Roslyn jazyka C# a Visual Basic | 16.0.28714.129 | Požaduje se
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# a Visual Basic | 16.5.29515.121 | Požaduje se
Microsoft.VisualStudio.Component.VSSDK | Visual Studio SDK | 16.0.28315.86 | Požaduje se
Microsoft.VisualStudio.ComponentGroup.VisualStudioExtension.Prerequisites | Požadavky na vývoj rozšíření sady Visual Studio | 16.4.29318.151 | Požaduje se
Microsoft.VisualStudio.Component.DiagnosticTools | Nástroje profilování rozhraní .NET | 16.5.29515.121 | Doporučené
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | 16.5.29515.121 | Doporučené
Microsoft.VisualStudio.Component.TextTemplating | Transformace šablony textu | 16.0.28625.61 | Doporučené
Soubor Microsoft.Component.CodeAnalysis.SDK | Sada .NET Compiler Platform SDK | 16.2.29003.222 | Nepovinné
Microsoft.VisualStudio.Component.AppInsights.Tools | Nástroje analýzy pro vývojáře | 16.5.29515.121 | Nepovinné
Microsoft.VisualStudio.Component.DslTools | Modelování sady SDK | 16.0.28315.86 | Nepovinné

## <a name="unaffiliated-components"></a>Nepřidružené součásti

Jedná se o součásti, které nejsou součástí žádné úlohy, ale mohou být vybrány jako jednotlivé součásti.

ID součásti | Name (Název) | Version
--- | --- | ---
Component.GitHub.VisualStudio | Rozšíření GitHub pro Visual Studio | 2.5.9.5485
Component.Xamarin.Inspector | Xamarin Inspector | 16.0.28315.86
Component.Xamarin.Profiler | Xamarin Profiler | 16.0.28315.86
Component.Xamarin.Sešity | Sešity ke Xamarinu | 16.0.28315.86
Microsoft.Component.ClickOnce | Publikování clickonce | 16.4.29409.204
Microsoft.Component.HelpViewer | Prohlížeč nápovědy | 16.0.28625.61
Microsoft.Net.Component.4.6.1.SDK | Rozhraní .NET Framework 4.6.1 SDK | 16.4.29409.204
Microsoft.Net.Component.4.6.2.SDK | Rozhraní .NET Framework 4.6.2 SDK | 16.4.29409.204
Microsoft.Net.Component.4.7.1.SDK | Rozhraní .NET Framework 4.7.1 SDK | 16.4.29409.204
Microsoft.Net.Component.4.7.2.SDK | Rozhraní .NET Framework 4.7.2 SDK | 16.4.29409.204
Sada Microsoft.Net.Component.4.7.SdK | Rozhraní .NET Framework 4.7 SDK | 16.4.29409.204
Microsoft.Net.core.component.Sdk.2.2 | Doba běhu .NET Core 2.2 (EOL) | 16.5.29813.82
Microsoft.Net.core.component.Sdk.3.0 | Doba běhu .NET Core 3.0 (EOL) | 16.5.29905.7
Microsoft.NetCore.ComponentGroup.DevelopmentTools.2.1 | Vývojové nástroje plus .NET Core 2.1 | 16.3.29207.166
Microsoft.NetCore.ComponentGroup.Web.2.1 | Nástroje pro vývoj webových aplikací a .NET Core 2.1 | 16.3.29207.166
Microsoft.VisualStudio.Component.AzureDevOps.OfficeIntegrace | Integrace Azure DevOps Office | 16.0.28625.61
Microsoft.VisualStudio.Component.Debugger.VSOnline | Ladicí program pro prostředí Visual Studio Online | 16.5.29813.82
Microsoft.VisualStudio.Component.Git | Git pro Windows | 16.0.28625.61
Microsoft.VisualStudio.Component.LinqToSql | Nástroje LINQ to SQL | 16.0.28625.61
Microsoft.VisualStudio.Component.TestTools.CodedUITest | Programový test UI | 16.0.28327.66
Microsoft.VisualStudio.Component.VC.14.20.ARM | MSVC v142 - VS 2019 C++ ARM nástroje pro sestavení (v14.20) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.ARM.Spectre | MSVC v142 - VS 2019 C++ ARM Spectre-mitigated libs (v14.20) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.ARM64 | MSVC v142 - VS 2019 C++ ARM64 nástroje sestavení (v14.20) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.20.ARM64.Spectre | MSVC v142 - VS 2019 C++ ARM64 Spectre-mitigated libs (v14.20) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.ATL | C++ v14.20 ATL pro nástroje sestavení v142 (x86 & x64) | 16.1.28829.92
Microsoft.VisualStudio.Component.VC.14.20.ATL.ARM | C++ v14.20 ATL pro nástroje sestavení v142 (ARM) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.ATL.ARM.Spectre | C++ v14.20 ATL pro nástroje sestavení v142 s spectre mitigations (ARM) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.20.ATL.ARM64 | C++ v14.20 ATL pro nástroje sestavení v142 (ARM64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.ATL.ARM64.Spectre | C++ v14.20 ATL pro nástroje sestavení v142 s ritkem Spectre (ARM64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.ATL.Spectre | C++ v14.20 ATL pro nástroje sestavení v142 s spectre skutečnosti snižující závažnost rizika (x86 & x64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.CLI.Support | Podpora C++/CLI pro nástroje sestavení v142 (14.20) | 16.4.29409.204
Soubor Microsoft.VisualStudio.Component.VC.14.20.MFC | C++ v14.20 MFC pro nástroje sestavení v142 (x86 & x64) | 16.2.29003.222
Microsoft.VisualStudio.Component.VC.14.20.MFC.ARM | C++ v14.20 MFC pro nástroje sestavení v142 (ARM) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.MFC.ARM.Spectre | C++ v14.20 MFC pro nástroje sestavení v142 s spectre mitigations (ARM) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.MFC.ARM64 | C++ v14.20 MFC pro nástroje sestavení v142 (ARM64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.MFC.ARM64.Spectre | C++ v14.20 MFC pro nástroje sestavení v142 s rážováním spectre (ARM64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.MFC.Spectre | C++ v14.20 MFC pro nástroje sestavení v142 s spectre skutečnosti snižující závažnost rizika (x86 & x64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.x86.x64 | Nástroje sestavení MSVC v142 - VS 2019 C++ x64/x86 (v14.20) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.x86.x64.Spectre | MSVC v142 - VS 2019 C++ x64/x86 Spectre-mitigated libs (v14.20) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.21.ARM | MSVC v142 - VS 2019 C++ ARM nástroje pro sestavení (v14.21) | 16.3.29207.166
Microsoft.VisualStudio.Component.VC.14.21.ARM.Spectre | MSVC v142 - VS 2019 C++ ARM Spectre-mitigated libs (v14.21) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.21.ARM64 | Nástroje pro sestavení MSVC v142 - VS 2019 C++ ARM64 (v14.21) | 16.3.29207.166
Microsoft.VisualStudio.Component.VC.14.21.ARM64.Spectre | MSVC v142 - VS 2019 C++ ARM64 Spectre-mitigated libs (v14.21) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.21.ATL | C++ v14.21 ATL pro nástroje sestavení v142 (x86 & x64) | 16.2.29019.55
Microsoft.VisualStudio.Component.VC.14.21.ATL.ARM | C++ v14.21 ATL pro nástroje sestavení v142 (ARM) | 16.2.29019.55
Microsoft.VisualStudio.Component.VC.14.21.ATL.ARM.Spectre | C++ v14.21 ATL pro nástroje sestavení v142 s spectre mitigations (ARM) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.21.ATL.ARM64 | C++ v14.21 ATL pro nástroje sestavení v142 (ARM64) | 16.2.29019.55
Microsoft.VisualStudio.Component.VC.14.21.ATL.ARM64.Spectre | C++ v14.21 ATL pro nástroje sestavení v142 s ritkem Spectre (ARM64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.21.ATL.Spectre | C++ v14.21 ATL pro nástroje sestavení v142 s spectre skutečnosti snižující závažnost rizika (x86 & x64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.21.CLI.Support | Podpora C++/CLI pro nástroje sestavení v142 (14.21) | 16.3.29207.166
Soubor Microsoft.VisualStudio.Component.VC.14.21.MFC | C++ v14.21 MFC pro nástroje sestavení v142 (x86 & x64) | 16.2.29019.55
Microsoft.VisualStudio.Component.VC.14.21.MFC.ARM | C++ v14.21 MFC pro nástroje sestavení v142 (ARM) | 16.2.29019.55
Microsoft.VisualStudio.Component.VC.14.21.MFC.ARM.Spectre | C++ v14.21 MFC pro nástroje sestavení v142 s spectre skutečnosti snižující závažnost rizika (ARM) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.21.MFC.ARM64 | C++ v14.21 MFC pro nástroje sestavení v142 (ARM64) | 16.2.29019.55
Microsoft.VisualStudio.Component.VC.14.21.MFC.ARM64.Spectre | C++ v14.21 MFC pro nástroje sestavení v142 s rážováním spectre (ARM64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.21.MFC.Spectre | C++ v14.21 MFC pro nástroje sestavení v142 s spectre skutečnosti snižující závažnost rizika (x86 & x64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.21.x86.x64 | Nástroje sestavení MSVC v142 - VS 2019 C++ x64/x86 (v14.21) | 16.3.29207.166
Microsoft.VisualStudio.Component.VC.14.21.x86.x64.Spectre | MSVC v142 - VS 2019 C++ x64/x86 Spectre-mitigated libs (v14.21) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.22.ARM | MSVC v142 - VS 2019 C++ ARM nástroje pro sestavení (v14.22) | 16.4.29313.120
Microsoft.VisualStudio.Component.VC.14.22.ARM.Spectre | MSVC v142 - VS 2019 C++ ARM Spectre-mitigated libs (v14.22) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.22.ARM64 | Nástroje pro sestavení MSVC v142 - VS 2019 C++ ARM64 (v14.22) | 16.4.29313.120
Microsoft.VisualStudio.Component.VC.14.22.ARM64.Spectre | MSVC v142 - VS 2019 C++ ARM64 Spectre-mitigated libs (v14.22) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.22.ATL | C++ v14.22 ATL pro nástroje sestavení v142 (x86 & x64) | 16.4.29313.120
Microsoft.VisualStudio.Component.VC.14.22.ATL.ARM | C++ v14.22 ATL pro nástroje sestavení v142 (ARM) | 16.4.29313.120
Microsoft.VisualStudio.Component.VC.14.22.ATL.ARM.Spectre | C++ v14.22 ATL pro nástroje sestavení v142 s spectre mitigations (ARM) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.22.ATL.ARM64 | C++ v14.22 ATL pro nástroje sestavení v142 (ARM64) | 16.4.29313.120
Microsoft.VisualStudio.Component.VC.14.22.ATL.ARM64.Spectre | C++ v14.22 ATL pro nástroje sestavení v142 s ritkem Spectre (ARM64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.22.ATL.Spectre | C++ v14.22 ATL pro nástroje sestavení v142 s spectre mitigations (x86 & x64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.22.CLI.Support | Podpora C++/CLI pro nástroje sestavení v142 (14.22) | 16.4.29313.120
Soubor Microsoft.VisualStudio.Component.VC.14.22.MFC | C++ v14.22 MFC pro nástroje sestavení v142 (x86 & x64) | 16.4.29313.120
Microsoft.VisualStudio.Component.VC.14.22.MFC.ARM | C++ v14.22 MFC pro nástroje sestavení v142 (ARM) | 16.4.29313.120
Microsoft.VisualStudio.Component.VC.14.22.MFC.ARM.Spectre | C++ v14.22 MFC pro nástroje sestavení v142 s spectre mitigations (ARM) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.22.MFC.ARM64 | C++ v14.22 MFC pro nástroje sestavení v142 (ARM64) | 16.4.29313.120
Microsoft.VisualStudio.Component.VC.14.22.MFC.ARM64.Spectre | C++ v14.22 MFC pro nástroje sestavení v142 s rážováním spectre (ARM64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.22.MFC.Spectre | C++ v14.22 MFC pro nástroje sestavení v142 s spectre skutečnosti snižující závažnost rizika (x86 & x64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.22.x86.x64 | Nástroje sestavení MSVC v142 - VS 2019 C++ x64/x86 (v14.22) | 16.4.29313.120
Microsoft.VisualStudio.Component.VC.14.22.x86.x64.Spectre | MSVC v142 - VS 2019 C++ x64/x86 Spectre-mitigated libs (v14.22) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.ARM | MSVC v142 - VS 2019 C++ ARM nástroje pro sestavení (v14.23) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.ARM.Spectre | MSVC v142 - VS 2019 C++ ARM Spectre-mitigated libs (v14.23) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.ARM64 | Nástroje pro sestavení MSVC v142 - VS 2019 C++ ARM64 (v14.23) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.ARM64.Spectre | MSVC v142 - VS 2019 C++ ARM64 Spectre-mitigated libs (v14.23) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.ATL | C++ v14.23 ATL pro nástroje sestavení v142 (x86 & x64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.ATL.ARM | C++ v14.23 ATL pro nástroje sestavení v142 (ARM) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.ATL.ARM.Spectre | C++ v14.23 ATL pro nástroje sestavení v142 s spectre mitigations (ARM) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.23.ATL.ARM64 | C++ v14.23 ATL pro nástroje sestavení v142 (ARM64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.ATL.ARM64.Spectre | C++ v14.23 ATL pro nástroje sestavení v142 s ritkem Spectre (ARM64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.ATL.Spectre | C++ v14.23 ATL pro nástroje sestavení v142 s spectre skutečnosti snižující závažnost rizika (x86 & x64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.CLI.Support | Podpora C++/CLI pro nástroje sestavení v142 (14.23) | 16.4.29409.204
Soubor Microsoft.VisualStudio.Component.VC.14.23.MFC | C++ v14.23 MFC pro nástroje sestavení v142 (x86 & x64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.MFC.ARM | C++ v14.23 MFC pro nástroje sestavení v142 (ARM) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.MFC.ARM.Spectre | C++ v14.23 MFC pro nástroje sestavení v142 s spectre skutečnosti snižující závažnost rizika (ARM) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.MFC.ARM64 | C++ v14.23 MFC pro nástroje sestavení v142 (ARM64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.MFC.ARM64.Spectre | C++ v14.23 MFC pro nástroje sestavení v142 s spectre skutečnosti snižující závažnost rizika (ARM64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.MFC.Spectre | C++ v14.23 MFC pro nástroje sestavení v142 s spectre skutečnosti snižující závažnost rizika (x86 & x64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.x86.x64 | Nástroje sestavení MSVC v142 - VS 2019 C++ x64/x86 (v14.23) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.x86.x64.Spectre | MSVC v142 - VS 2019 C++ x64/x86 Spectre-mitigated libs (v14.23) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.24.ARM | MSVC v142 - VS 2019 C++ ARM nástroje pro sestavení (v14.24) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.ARM.Spectre | MSVC v142 - VS 2019 C++ ARM Spectre-mitigated libs (v14.24) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.ARM64 | Nástroje pro sestavení MSVC v142 - VS 2019 C++ ARM64 (v14.24) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.ARM64.Spectre | MSVC v142 - VS 2019 C++ ARM64 Spectre-mitigated libs (v14.24) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.ATL | C++ v14.24 ATL pro nástroje sestavení v142 (x86 & x64) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.ATL.ARM | C++ v14.24 ATL pro nástroje sestavení v142 (ARM) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.ATL.ARM.Spectre | C++ v14.24 ATL pro nástroje sestavení v142 s spectre mitigations (ARM) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.ATL.ARM64 | C++ v14.24 ATL pro nástroje sestavení v142 (ARM64) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.ATL.ARM64.Spectre | C++ v14.24 ATL pro nástroje sestavení v142 s ritkem Spectre (ARM64) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.ATL.Spectre | C++ v14.24 ATL pro nástroje sestavení v142 s spectre mitigations (x86 & x64) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.CLI.Support | Podpora C++/CLI pro nástroje sestavení v142 (14.24) | 16.5.29721.120
Soubor Microsoft.VisualStudio.Component.VC.14.24.MFC | C++ v14.24 MFC pro nástroje sestavení v142 (x86 & x64) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.MFC.ARM | C++ v14.24 MFC pro nástroje sestavení v142 (ARM) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.MFC.ARM.Spectre | C++ v14.24 MFC pro nástroje sestavení v142 s spectre skutečnosti snižující závažnost rizika (ARM) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.MFC.ARM64 | C++ v14.24 MFC pro nástroje sestavení v142 (ARM64) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.MFC.ARM64.Spectre | C++ v14.24 MFC pro nástroje sestavení v142 s rážováním spectre (ARM64) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.MFC.Spectre | C++ v14.24 MFC pro nástroje sestavení v142 s spectre skutečnosti snižující závažnost rizika (x86 & x64) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.x86.x64 | Nástroje sestavení MSVC v142 - VS 2019 C++ x64/x86 (v14.24) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.x86.x64.Spectre | MSVC v142 - VS 2019 C++ x64/x86 Spectre-mitigated libs (v14.24) | 16.5.29721.120
Soubor Microsoft.VisualStudio.Component.VC.ATL.ARM | C++ ATL pro nejnovější nástroje sestavení v142 (ARM) | 16.4.29313.120
Soubor Microsoft.VisualStudio.Component.VC.ATL.ARM.Spectre | C++ ATL pro nejnovější nástroje sestavení v142 s spectre mitigations (ARM) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.ATL.ARM64 | C++ ATL pro nejnovější nástroje pro sestavení v142 (ARM64) | 16.4.29313.120
Soubor Microsoft.VisualStudio.Component.VC.ATL.ARM64.Spectre | C++ ATL pro nejnovější nástroje sestavení v142 s spectre mitigations (ARM64) | 16.5.29515.121
Soubor Microsoft.VisualStudio.Component.VC.ATL.Spectre | C++ ATL pro nejnovější nástroje sestavení v142 s opatřeními ke zmírnění rizik spectre (x86 & x64) | 16.5.29515.121
Soubor Microsoft.VisualStudio.Component.VC.ATLMFC.Spectre | Knihovna MFC c++ pro nejnovější nástroje sestavení v142 s nástroji ke zmírnění rizik spectre (x86 & x64) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.MFC.ARM | C++ Knihovna MFC pro nejnovější nástroje sestavení v142 (ARM) | 16.4.29313.120
Microsoft.VisualStudio.Component.VC.MFC.ARM.Spectre | C++ Knihovna MFC pro nejnovější nástroje sestavení v142 s rážováním spectre (ARM) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.MFC.ARM64 | C++ Knihovna MFC pro nejnovější nástroje sestavení v142 (ARM64) | 16.4.29313.120
Microsoft.VisualStudio.Component.VC.MFC.ARM64.Spectre | C++ Knihovna MFC pro nejnovější nástroje sestavení v142 s rušivými riziky spectre (ARM64) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.Redist.MSM | C++ 2019 Redistribuovatelné msms | 16.5.29515.121
Soubor Microsoft.VisualStudio.Component.VC.Runtimes.ARM.Spectre | MSVC v142 - VS 2019 C++ ARM Spectre-mitigated libs (v14.25) | 16.5.29721.120
Soubor Microsoft.VisualStudio.Component.VC.Runtimes.ARM64.Spectre | MSVC v142 - VS 2019 C++ ARM64 Spectre-mitigated libs (v14.25) | 16.5.29721.120
Soubor Microsoft.VisualStudio.Component.VC.Runtimes.x86.x64.Spectre | MSVC v142 - VS 2019 C++ x64/x86 Spectre-mitigated libs (v14.25)  | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.v141.ARM.Spectre | MSVC v141 - VS 2017 C++ ARM Spectre-zmírnil libs (v14.16) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.v141.ARM64.Spectre | MSVC v141 - VS 2017 C++ ARM64 Spectre-mitigated libs (v14.16) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.v141.ATL | C++ ATL pro nástroje sestavení v141 (x86 & x64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.ATL.ARM | C++ ATL pro nástroje sestavení v141 (ARM) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.ATL.ARM.Spectre | C++ ATL pro nástroje sestavení v141 s spectre skutečnosti snižující závažnost rizika (ARM) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.v141.ATL.ARM64 | C++ ATL pro nástroje sestavení v141 (ARM64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.ATL.ARM64.Spectre | C++ ATL pro nástroje sestavení v141 s rušivými riziky spectre (ARM64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.ATL.Spectre | C++ ATL pro nástroje sestavení v141 s rituzními riziky Spectre (x86 & x64) | 16.0.28625.61
Podpora microsoft.VisualStudio.Component.VC.v141.CLI.Support | Podpora C++/CLI pro nástroje sestavení v141 (14.16) | 16.3.29207.166
Soubor Microsoft.VisualStudio.Component.VC.v141.MFC | C++ Knihovna MFC pro nástroje sestavení v141 (x86 & x64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.MFC.ARM | C++ Knihovna MFC pro nástroje sestavení v141 (ARM) | 16.2.28915.88
Microsoft.VisualStudio.Component.VC.v141.MFC.ARM.Spectre | C++ Knihovna MFC pro nástroje sestavení v141 s rážováním spectre (ARM) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.MFC.ARM64 | C++ Knihovna MFC pro nástroje sestavení v141 (ARM64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.MFC.ARM64.Spectre | C++ Knihovna MFC pro nástroje sestavení v141 s rážováním spectre (ARM64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.MFC.Spectre | Knihovna MFC C++ pro nástroje sestavení v141 s rituzními riziky Spectre (x86 & x64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.x86.x64.Spectre | MSVC v141 - VS 2017 C++ x64/x86 Spectre-mitigated libs (v14.16) | 16.5.29515.121
Microsoft.VisualStudio.Component.VisualStudioData | Zdroje dat a odkazy na služby | 16.0.28707.177
Soubor Microsoft.VisualStudio.Component.WinXP | Podpora systému C++ windows xp pro nástroje VS 2017 (v141) [Zastaralé] | 16.1.28811.260
Microsoft.VisualStudio.Web.Mvc4.ComponentGroup | ASP.NET MVC 4 | 16.1.28810.153
