---
title: ID úlohy a ID součástí Visual Studio Enterprise 2017
titleSuffix: ''
description: Použití zatížení a ID komponent k instalaci sady Visual Studio pomocí příkazového řádku nebo pro určení jako závislosti v manifestu VSIX
keywords: ''
author: j-martens
ms.author: jmartens
manager: jmartens
ms.date: 2/12/2019
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.topic: include
ms.openlocfilehash: 977c50d42a5c3b59a397714a656f6fd84d94de36
ms.sourcegitcommit: 6d88913a8b5a9e5eda01d3f95205b4d138f440f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/13/2021
ms.locfileid: "110449828"
---
## <a name="visual-studio-core-editor-included-with-visual-studio-enterprise-2017"></a>Základní editor sady Visual Studio (zahrnutý v Visual Studio Enterprise 2017)

**ID:** Microsoft. VisualStudio. úlohy. CoreEditor

**Popis:** Základní prostředí sady Visual Studio, včetně úprav kódu s podporou syntaxe, správy zdrojového kódu a správy pracovních položek.

### <a name="components-included-by-this-workload"></a>Součásti zahrnuté v tomto zatížení

ID součásti | Name | Verze | Typ závislosti
--- | --- | --- | ---
Microsoft. VisualStudio. Component. CoreEditor | Základní editor sady Visual Studio | 15.8.27729.1 | Vyžadováno
Microsoft. VisualStudio. Component. StartPageExperiment. cpp | Úvodní stránka sady Visual Studio pro uživatele C++ | 15.0.27128.1 | Volitelné

## <a name="azure-development"></a>Vývoj pro Azure

**ID:** Microsoft. VisualStudio. úlohy. Azure

**Popis:** Sady SDK, nástroje a projekty Azure pro vývoj cloudových aplikací, vytváření prostředků a vytváření kontejnerů včetně podpory Docker.

### <a name="components-included-by-this-workload"></a>Součásti zahrnuté v tomto zatížení

ID součásti | Name | Verze | Typ závislosti
--- | --- | --- | ---
Součást. Microsoft. VisualStudio. RazorExtension | Jazykové služby Razor | 15.0.26720.2 | Vyžadováno
Component.Microsoft.VisualStudio.Web.AzureFunctions | Microsoft Azure WebJobs Tools | 15.7.27617.1 | Vyžadováno
Component.Microsoft.Web.LibraryManager | Správce knihovny | 15.8.27705.0 | Vyžadováno
Component.WebSocket | WebSocket4Net | 15.0.26606.0 | Vyžadováno
Microsoft.Component.ClickOnce | Publikování ClickOnce | 15.8.27825.0 | Vyžadováno
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | Vyžadováno
Microsoft.Component.NetFX.Core.Runtime | Modul runtime .NET Core | 15.0.26208.0 | Vyžadováno
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 | 15.6.27406.0 | Vyžadováno
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 | 15.6.27406.0 | Vyžadováno
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 15.6.27406.0 | Vyžadováno
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 | 15.6.27406.0 | Vyžadováno
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Vývojové nástroje .NET Framework 4.6.1 | 15.8.27825.0 | Vyžadováno
Microsoft. NET. Core. Component. SDK. 2.1 | Vývojové nástroje .NET Core 2,1 | 15.8.27924.0 | Vyžadováno
Microsoft. NetCore. Component. DevelopmentTools. 2.1 | Vývojové nástroje .NET Core 2,1 | 15.8.27924.0 | Vyžadováno
Microsoft. NetCore. Component. Web. 2.1 | Vývojové nástroje .NET Core 2,1 | 15.8.27924.0 | Vyžadováno
Microsoft. VisualStudio. Component. Azure. AuthoringTools | Nástroje pro tvorbu Azure | 15.9.28307.421 | Vyžadováno
Microsoft. VisualStudio. Component. Azure. ClientLibs | Knihovny Azure pro .NET | 15.0.26208.0 | Vyžadováno
Microsoft. VisualStudio. Component. Azure. Compute. emulátor | Emulátor služby COMPUTE Azure | 15.9.28307.421 | Vyžadováno
Microsoft. VisualStudio. Component. Azure. Storage. emulátor | Emulátor úložiště Azure | 15.9.28125.51 | Vyžadováno
Microsoft. VisualStudio. Component. Průzkumník cloudu | Průzkumník cloudu | 15.9.28230.55 | Vyžadováno
Microsoft.VisualStudio.Component.Common.Azure.Tools | Nástroje pro připojení a publikování | 15.9.28107.0 | Vyžadováno
Microsoft.VisualStudio.Component.DockerTools | Kontejnerové vývojové nástroje | 15.8.27906.1 | Vyžadováno
Microsoft.VisualStudio.Component.DockerTools.BuildTools | Nástroje pro vývoj kontejnerů – Build Tools | 15.7.27617.1 | Vyžadováno
Microsoft.VisualStudio.Component.FSharp | Podpora jazyka F# | 15.8.27825.0 | Vyžadováno
Microsoft.VisualStudio.Component.FSharp.WebTemplates | Podpora jazyka F# pro webové projekty | 15.9.28307.421 | Vyžadováno
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 15.0.26208.0 | Vyžadováno
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostika JavaScriptu | 15.8.27729.1 | Vyžadováno
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Podpora jazyků JavaScript a TypeScript | 15.9.28125.51 | Vyžadováno
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Jádro úlohy spravované plochy | 15.8.27729.1 | Vyžadováno
Microsoft. VisualStudio. Component. NuGet | Správce balíčků NuGet | 15.9.28016.0 | Vyžadováno
Microsoft. VisualStudio. Component. PortableLibrary | Sada targeting pack přenosné knihovny .NET | 15.6.27309.0 | Vyžadováno
Microsoft. VisualStudio. Component. Roslyn. Compiler | Kompilátory C# a Visual Basic Roslyn | 15.6.27309.0 | Vyžadováno
Microsoft. VisualStudio. Component. Roslyn. LanguageServices | C# a Visual Basic | 15.8.27729.1 | Vyžadováno
Microsoft. VisualStudio. Component. SQL. ADAL | Modul runtime SQL ADAL | 15.6.27406.0 | Vyžadováno
Microsoft. VisualStudio. Component. SQL. CLR | Datové typy CLR pro SQL Server | 15.0.26208.0 | Vyžadováno
Microsoft. VisualStudio. Component. SQL. CMDUtils | SQL Server nástroje příkazového řádku | 15.0.26208.0 | Vyžadováno
Microsoft. VisualStudio. Component. SQL. DataSources | Zdroje dat pro podporu SQL Server | 15.0.26621.2 | Vyžadováno
Microsoft. VisualStudio. Component. SQL. LocalDB. Runtime | SQL Server Express 2016 LocalDB | 15.7.27617.1 | Vyžadováno
Microsoft.VisualStudio.Component.SQL.NCLI | Nativní klient systému SQL Server | 15.0.26208.0 | Vyžadováno
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 15.9.28107.0 | Vyžadováno
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Nástroje pro statickou analýzu | 15.0.26208.0 | Vyžadováno
Microsoft.VisualStudio.Component.TextTemplating | Transformace textových šablon | 15.0.26208.0 | Vyžadováno
Microsoft.VisualStudio.Component.TypeScript.3.1 | TypeScript 3.1 SDK | 15.0.28218.60 | Vyžadováno
Microsoft.VisualStudio.Component.VisualStudioData | Zdroje dat a odkazy na služby | 15.6.27406.0 | Vyžadováno
Microsoft.VisualStudio.Component.Web | ASP.NET a webové vývojové nástroje | 15.8.27825.0 | Vyžadováno
Microsoft.VisualStudio.ComponentGroup.Azure.Prerequisites | Požadavky na vývoj pro Azure | 15.9.28107.0 | Vyžadováno
Microsoft. VisualStudio. Component. AzureFunctions | Nástroje Microsoft Azure WebJobs | 15.7.27617.1 | Vyžadováno
Microsoft. VisualStudio. Component. Web | Požadavky na ASP.NET a vývojové nástroje pro web | 15.9.28219.51 | Vyžadováno
Microsoft. VisualStudio. Component. WebToolsExtensions | Vývoj pro ASP.NET a web | 15.8.27825.0 | Vyžadováno
Microsoft. Component. Azure. datalake. Tools | Nástroje Azure Data Lake a Stream Analytics | 15.9.28107.0 | Doporučeno
Microsoft.Net. Component. 4.5.1. TargetingPack | Sada .NET Framework 4.5.1 targeting pack | 15.6.27406.0 | Doporučeno
Microsoft.Net. Component. 4.6. TargetingPack | Sada targeting pack .NET Framework 4,6 | 15.6.27406.0 | Doporučeno
Microsoft.Net. Component. 4. TargetingPack | Sada targeting pack .NET Framework 4 | 15.6.27406.0 | Doporučeno
Microsoft.Net. Component. TargetingPacks. Common | .NET Framework nástroje pro vývoj 4 – 4,6 | 15.6.27406.0 | Doporučeno
Microsoft. VisualStudio. Component. AspNet45 | Pokročilé funkce ASP.NET | 15.7.27625.0 | Doporučeno
Microsoft.VisualStudio.Component.Azure.MobileAppsSdk | Azure Mobile Apps SDK | 15.7.27625.0 | Doporučeno
Microsoft.VisualStudio.Component.Azure.ResourceManager.Tools | Azure Resource Manager nástroje | 15.9.28107.0 | Doporučeno
Microsoft.VisualStudio.Component.Azure.ServiceFabric.Tools | Nástroje Service Fabricu | 15.8.27825.0 | Doporučeno
Microsoft.VisualStudio.Component.Azure.Waverton | Azure Cloud Services core tools | 15.9.28107.0 | Doporučeno
Microsoft.VisualStudio.Component.Azure.Waverton.BuildTools | Azure Cloud Services sestavovací nástroje | 15.7.27617.1 | Doporučeno
Microsoft.VisualStudio.Component.Debugger.Snapshot | Ladicí program snímků | 15.8.28010.0 | Doporučeno
Microsoft.VisualStudio.Component.DiagnosticTools | Nástroje pro profilaci .NET | 15.8.27729.1 | Doporučeno
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | 15.8.27729.1 | Doporučeno
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 15.8.27729.1 | Doporučeno
Microsoft.VisualStudio.ComponentGroup.Azure.CloudServices | Azure Cloud Services nástroje | 15.0.26504.0 | Doporučeno
Microsoft.VisualStudio.ComponentGroup.Azure.ResourceManager.Tools | Nástroje Azure Resource Manager | 15.0.27005.2 | Doporučeno
Microsoft. NET. Component. 4.6.2. SDK | Sada .NET Framework 4.6.2 SDK | 15.6.27406.0 | Volitelné
Microsoft.Net. Component. 4.6.2. TargetingPack | Sada targeting pack .NET Framework 4.6.2 | 15.6.27406.0 | Volitelné
Microsoft. NET. Component. 4.7.1. SDK | Sada .NET Framework 4.7.1 SDK | 15.6.27406.0 | Volitelné
Microsoft.Net. Component. 4.7.1. TargetingPack | Sada targeting pack .NET Framework 4.7.1 | 15.6.27406.0 | Volitelné
Microsoft. NET. Component. 4.7.2. SDK | Sada .NET Framework 4.7.2 SDK | 15.8.27825.0 | Volitelné
Microsoft.Net. Component. 4.7.2. TargetingPack | Sada targeting pack .NET Framework 4.7.2 | 15.8.27825.0 | Volitelné
Microsoft. NET. Component. 4.7. SDK | .NET Framework 4,7 SDK | 15.6.27406.0 | Volitelné
Microsoft.Net. Component. 4.7. TargetingPack | Sada targeting pack .NET Framework 4,7 | 15.6.27406.0 | Volitelné
Microsoft.Net. Component. 4.6.2. DeveloperTools | Vývojové nástroje .NET Framework 4.6.2 | 15.6.27406.0 | Volitelné
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | .NET Framework 4.7.1 | 15.6.27406.0 | Volitelné
Microsoft.Net.ComponentGroup.4.7.2.DeveloperTools | .NET Framework 4.7.2 – vývojové nástroje | 15.8.27825.0 | Volitelné
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | .NET Framework 4.7 – vývojové nástroje | 15.6.27406.0 | Volitelné
Microsoft.Net.Core.Component.SDK | Vývojové nástroje .NET Core 2.0 | 15.6.27406.0 | Volitelné
Microsoft.Net.Core.Component.SDK.1x | .NET Core 1.0 – vývojové nástroje verze 1.1 | 15.6.27406.0 | Volitelné
Microsoft.NetCore.1x.ComponentGroup.Web | .NET Core 1.0 – 1.1 – vývojové nástroje pro web | 15.6.27406.0 | Volitelné
Microsoft.NetCore.ComponentGroup.DevelopmentTools | Vývojové nástroje .NET Core 2.0 | 15.8.27729.1 | Volitelné
Microsoft.NetCore.ComponentGroup.Web | Vývojové nástroje .NET Core 2.0 | 15.7.27625.0 | Volitelné
Microsoft.VisualStudio.Component.Azure.Storage.AzCopy | Azure Storage AzCopy | 15.0.26906.1 | Volitelné
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | 15.8.27924.0 | Volitelné

## <a name="data-storage-and-processing"></a>Ukládání a zpracování dat

**ID:** Microsoft.VisualStudio.Workload.Data

**Popis:** Připojení, vývoj a testování datových řešení pomocí SQL Server, Azure Data Lake nebo Hadoop.

### <a name="components-included-by-this-workload"></a>Součásti zahrnuté v tomto zatížení

ID součásti | Name | Verze | Typ závislosti
--- | --- | --- | ---
Součást. Microsoft. VisualStudio. RazorExtension | Jazykové služby Razor | 15.0.26720.2 | Doporučeno
Součást. Microsoft. Web. LibraryManager | Správce knihovny | 15.8.27705.0 | Doporučeno
Component. Redgate. ReadyRoll | Redgate ReadyRoll Core | 1.17.18155.10346 | Doporučeno
Component. Redgate. SQLPrompt. VsPackage | Redgate SQL Prompt Core | 9.2.0.5601 | Doporučeno
Component. Redgate. SQLSearch. VSExtension | Hledání v Redgate SQL | 3.1.7.2062 | Doporučeno
Komponenta. WebSocket | WebSocket4Net | 15.0.26606.0 | Doporučeno
Microsoft. Component. Azure. datalake. Tools | Nástroje Azure Data Lake a Stream Analytics | 15.9.28107.0 | Doporučeno
Microsoft. Component. ClickOnce | Publikování ClickOnce | 15.8.27825.0 | Doporučeno
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | Doporučeno
Microsoft.Net.Component.4.5.1.TargetingPack | .NET Framework 4.5.1 | 15.6.27406.0 | Doporučeno
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 | 15.6.27406.0 | Doporučeno
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 | 15.6.27406.0 | Doporučeno
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 15.6.27406.0 | Doporučeno
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 | 15.6.27406.0 | Doporučeno
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework 4.6 | 15.6.27406.0 | Doporučeno
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 cílení pack | 15.6.27406.0 | Doporučeno
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | .NET Framework 4.6.1 | 15.8.27825.0 | Doporučeno
Microsoft.Net.ComponentGroup.TargetingPacks.Common | .NET Framework 4–4.6 – vývojové nástroje | 15.6.27406.0 | Doporučeno
Microsoft. NET. Core. Component. SDK. 2.1 | Vývojové nástroje .NET Core 2,1 | 15.8.27924.0 | Doporučeno
Microsoft. VisualStudio. Component. Azure. AuthoringTools | Nástroje pro tvorbu Azure | 15.9.28307.421 | Doporučeno
Microsoft. VisualStudio. Component. Azure. ClientLibs | Knihovny Azure pro .NET | 15.0.26208.0 | Doporučeno
Microsoft. VisualStudio. Component. Azure. Compute. emulátor | Emulátor služby COMPUTE Azure | 15.9.28307.421 | Doporučeno
Microsoft. VisualStudio. Component. Azure. Storage. emulátor | Emulátor úložiště Azure | 15.9.28125.51 | Doporučeno
Microsoft. VisualStudio. Component. Azure. Waverton | Základní nástroje pro Azure Cloud Services | 15.9.28107.0 | Doporučeno
Microsoft. VisualStudio. Component. Azure. Waverton. BuildTools | Nástroje pro vytváření Cloud Services pro Azure | 15.7.27617.1 | Doporučeno
Microsoft. VisualStudio. Component. Průzkumník cloudu | Průzkumník cloudu | 15.9.28230.55 | Doporučeno
Microsoft.VisualStudio.Component.Common.Azure.Tools | Nástroje pro připojení a publikování | 15.9.28107.0 | Doporučeno
Microsoft.VisualStudio.Component.DockerTools | Kontejnerové vývojové nástroje | 15.8.27906.1 | Doporučeno
Microsoft.VisualStudio.Component.DockerTools.BuildTools | Nástroje pro vývoj kontejnerů – Build Tools | 15.7.27617.1 | Doporučeno
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 15.0.26208.0 | Doporučeno
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostika JavaScriptu | 15.8.27729.1 | Doporučeno
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Podpora jazyků JavaScript a TypeScript | 15.9.28125.51 | Doporučeno
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Managed Desktop Workload Core | 15.8.27729.1 | Doporučeno
Microsoft.VisualStudio.Component.NuGet | Správce balíčků NuGet | 15.9.28016.0 | Doporučeno
Microsoft.VisualStudio.Component.PortableLibrary | Sada targeting pack přenosné knihovny .NET | 15.6.27309.0 | Doporučeno
Microsoft. VisualStudio. Component. Roslyn. Compiler | Kompilátory C# a Visual Basic Roslyn | 15.6.27309.0 | Doporučeno
Microsoft. VisualStudio. Component. Roslyn. LanguageServices | C# a Visual Basic | 15.8.27729.1 | Doporučeno
Microsoft. VisualStudio. Component. SQL. ADAL | Modul runtime SQL ADAL | 15.6.27406.0 | Doporučeno
Microsoft. VisualStudio. Component. SQL. CLR | Datové typy CLR pro SQL Server | 15.0.26208.0 | Doporučeno
Microsoft. VisualStudio. Component. SQL. CMDUtils | SQL Server nástroje příkazového řádku | 15.0.26208.0 | Doporučeno
Microsoft. VisualStudio. Component. SQL. DataSources | Zdroje dat pro podporu SQL Server | 15.0.26621.2 | Doporučeno
Microsoft. VisualStudio. Component. SQL. LocalDB. Runtime | SQL Server Express 2016 LocalDB | 15.7.27617.1 | Doporučeno
Microsoft. VisualStudio. Component. SQL. NCLI | Nativní klient systému SQL Server | 15.0.26208.0 | Doporučeno
Microsoft. VisualStudio. Component. SQL. SSDT | SQL Server Data Tools | 15.9.28107.0 | Doporučeno
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Nástroje pro statickou analýzu | 15.0.26208.0 | Doporučeno
Microsoft.VisualStudio.Component.TextTemplating | Transformace textových šablon | 15.0.26208.0 | Doporučeno
Microsoft.VisualStudio.Component.TypeScript.3.1 | TypeScript 3.1 SDK | 15.0.28218.60 | Doporučeno
Microsoft.VisualStudio.Component.VisualStudioData | Zdroje dat a odkazy na služby | 15.6.27406.0 | Doporučeno
Microsoft.VisualStudio.Component.Web | ASP.NET a webové vývojové nástroje | 15.8.27825.0 | Doporučeno
Microsoft.VisualStudio.ComponentGroup.Web | Požadavky ASP.NET a webových vývojových nástrojů | 15.9.28219.51 | Doporučeno
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Vývoj pro ASP.NET a web | 15.8.27825.0 | Doporučeno
Microsoft.VisualStudio.Component.FSharp.Desktop | Podpora desktopových jazyků F# | 15.8.27825.0 | Volitelné

## <a name="data-science-and-analytical-applications"></a>Aplikace pro datovou vědu a analýzu

**ID:** Microsoft.VisualStudio.Workload.DataScience

**Popis:** Jazyky a nástroje pro vytváření aplikací pro datové vědy, včetně Pythonu, R a F #

### <a name="components-included-by-this-workload"></a>Součásti zahrnuté v tomto zatížení

ID součásti | Name | Verze | Typ závislosti
--- | --- | --- | ---
Component. Anaconda3. x64 | Anaconda3 64 – bit (5.2.0) | 5.2.0 | Doporučeno
Microsoft. Component. CookiecutterTools | Podpora šablon Cookiecutter | 15.0.26621.2 | Doporučeno
Microsoft. Component. PythonTools | Podpora jazyka Python | 15.0.26823.1 | Doporučeno
Microsoft. Component. PythonTools. Web | Podpora webu Pythonu | 15.9.28107.0 | Doporučeno
Microsoft.Net. Component. 4.6.1. TargetingPack | .NET Framework 4.6.1 targeting pack | 15.6.27406.0 | Doporučeno
Microsoft. VisualStudio. Component. Common. Azure. Tools | Nástroje pro připojení a publikování | 15.9.28107.0 | Doporučeno
Microsoft. VisualStudio. Component. FSharp. Desktop | Podpora jazyka F # pro Desktop | 15.8.27825.0 | Doporučeno
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Podpora jazyků JavaScript a TypeScript | 15.9.28125.51 | Doporučeno
Microsoft.VisualStudio.Component.NuGet | Správce balíčků NuGet | 15.9.28016.0 | Doporučeno
Microsoft.VisualStudio.Component.R.Open | Microsoft R Client (3.3.2) | 15.6.27406.0 | Doporučeno
Microsoft.VisualStudio.Component.RHost | Podpora modulu runtime pro vývojové nástroje jazyka R | 15.6.27406.0 | Doporučeno
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilátory C# a Visual Basic Roslyn | 15.6.27309.0 | Doporučeno
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# a Visual Basic | 15.8.27729.1 | Doporučeno
Microsoft.VisualStudio.Component.RTools | Podpora jazyka R | 15.0.26919.1 | Doporučeno
Microsoft.VisualStudio.Component.SQL.CLR | Datové typy CLR pro SQL Server | 15.0.26208.0 | Doporučeno
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Nástroje statické analýzy | 15.0.26208.0 | Doporučeno
Microsoft. VisualStudio. Component. TypeScript. 3.1 | Sada TypeScript 3,1 SDK | 15.0.28218.60 | Doporučeno
Microsoft. VisualStudio. Component. VisualStudioData | Zdroje dat a odkazy na služby | 15.6.27406.0 | Doporučeno
Microsoft. VisualStudio. Component. WebDeploy | Web Deploy | 15.8.27729.1 | Doporučeno
Microsoft. VisualStudio. Component. WebToolsExtensions | Vývoj pro ASP.NET a web | 15.8.27825.0 | Doporučeno
Component. Anaconda2. x64 | Anaconda2 64 – bit (5.2.0) | 5.2.0 | Volitelné
Component. Anaconda2. x86 | Anaconda2 32 – bit (5.2.0) | 5.2.0 | Volitelné
Component. Anaconda3. x86 | Anaconda3 32 – bit (5.2.0) | 5.2.0 | Volitelné
Microsoft. Component. VC. Runtime. UCRTSDK | Sada Windows Universal CRT SDK | 15.6.27309.0 | Volitelné
Microsoft. Component. PythonTools. NativeDevelopment | Nástroje pro nativní vývoj v Pythonu | 15.9.28307.102 | Volitelné
Microsoft.VisualStudio.Component.Graphics.Tools | Ladicí program grafiky a profiler GPU pro DirectX | 15.6.27406.0 | Volitelné
Microsoft.VisualStudio.Component.Graphics.Win81 | Graphics Tools Windows 8.1 SDK | 15.6.27406.0 | Volitelné
Microsoft.VisualStudio.Component.VC.140 | Sada nástrojů VC++ 2015.3 v14.00 (v140) pro desktop | 15.7.27617.1 | Volitelné
Microsoft.VisualStudio.Component.VC.CoreIde | Visual Studio základních funkcí C++ | 15.6.27406.0 | Volitelné
Microsoft.VisualStudio.Component.VC.DiagnosticTools | Nástroje pro profilaci jazyka C++ | 15.0.26823.1 | Volitelné
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | Nástroje VC++ 2017 verze 15.9 v14.16 nejnovější verze 141 | 15.9.28230.55 | Volitelné
Microsoft.VisualStudio.Component.Windows10SDK | Windows Universal C Runtime | 15.6.27406.0 | Volitelné
Microsoft.VisualStudio.Component.Windows10SDK.17763 | Windows 10 SDK (10.0.17763.0) | 15.9.28307.102 | Volitelné
Microsoft.VisualStudio.Component.Windows81SDK | Windows 8.1 SDK | 15.6.27406.0 | Volitelné

## <a name="net-desktop-development"></a>Vývoj desktopových aplikací pro .NET

**ID:** Microsoft. VisualStudio. úlohy. ManagedDesktop

**Popis:** Vytvářejte aplikace WPF, model Windows Forms a konzolových aplikací pomocí jazyků C#, Visual Basic a F #.

### <a name="components-included-by-this-workload"></a>Součásti zahrnuté v tomto zatížení

ID součásti | Name | Verze | Typ závislosti
--- | --- | --- | ---
Microsoft. Component. ClickOnce | Publikování ClickOnce | 15.8.27825.0 | Vyžadováno
Microsoft. Component. MSBuild | MSBuild | 15.7.27520.0 | Vyžadováno
Microsoft. NET. Component. 4.6.1. SDK | .NET Framework 4.6.1 SDK | 15.6.27406.0 | Vyžadováno
Microsoft.Net. Component. 4.6.1. TargetingPack | .NET Framework 4.6.1 targeting pack | 15.6.27406.0 | Vyžadováno
Microsoft.Net. Component. DevelopmentPrerequisites | Vývojové nástroje .NET Framework 4.6.1 | 15.8.27825.0 | Vyžadováno
Microsoft. VisualStudio. Component. ManagedDesktop. Core | Jádro úlohy spravované plochy | 15.8.27729.1 | Vyžadováno
Microsoft. VisualStudio. Component. ManagedDesktop. požadavky | Nástroje pro vývoj desktopových aplikací .NET | 15.7.27625.0 | Vyžadováno
Microsoft. VisualStudio. Component. PortableLibrary | Sada targeting pack přenosné knihovny .NET | 15.6.27309.0 | Vyžadováno
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilátory C# a Visual Basic Roslyn | 15.6.27309.0 | Vyžadováno
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# a Visual Basic | 15.8.27729.1 | Vyžadováno
Microsoft.VisualStudio.Component.SQL.CLR | Datové typy CLR pro SQL Server | 15.0.26208.0 | Vyžadováno
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Nástroje pro statickou analýzu | 15.0.26208.0 | Vyžadováno
Microsoft.VisualStudio.Component.TextTemplating | Transformace textových šablon | 15.0.26208.0 | Vyžadováno
Microsoft.VisualStudio.Component.VisualStudioData | Zdroje dat a odkazy na služby | 15.6.27406.0 | Vyžadováno
Microsoft.ComponentGroup.Blend | Blend for Visual Studio | 15.6.27406.0 | Doporučeno
Microsoft.Net.Component.4.5.1.TargetingPack | .NET Framework 4.5.1 | 15.6.27406.0 | Doporučeno
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 | 15.6.27406.0 | Doporučeno
Microsoft.Net.Component.4.5.TargetingPack | Sada targeting pack .NET Framework 4,5 | 15.6.27406.0 | Doporučeno
Microsoft.Net. Component. 4.6. TargetingPack | Sada targeting pack .NET Framework 4,6 | 15.6.27406.0 | Doporučeno
Microsoft.Net. Component. 4. TargetingPack | Sada targeting pack .NET Framework 4 | 15.6.27406.0 | Doporučeno
Microsoft.Net. Component. TargetingPacks. Common | .NET Framework nástroje pro vývoj 4 – 4,6 | 15.6.27406.0 | Doporučeno
Microsoft. VisualStudio. Component. Debugger. JustInTime | Ladicí program za běhu | 15.0.27005.2 | Doporučeno
Microsoft. VisualStudio. Component. DiagnosticTools | Nástroje pro profilaci .NET | 15.8.27729.1 | Doporučeno
Microsoft. VisualStudio. Component. EntityFramework | Nástroje Entity Framework 6 | 15.6.27406.0 | Doporučeno
Microsoft. VisualStudio. Component. IntelliTrace. front-end | IntelliTrace | 15.8.27729.1 | Doporučeno
Microsoft. VisualStudio. Component. LiveUnitTesting | Live Unit Testing | 15.0.26720.2 | Doporučeno
Component. Dotfuscator | PreEmptive Protection – Dotfuscator | 15.0.26208.0 | Volitelné
Součást. Microsoft. VisualStudio. RazorExtension | Služby jazyka Razor | 15.0.26720.2 | Volitelné
Component.Microsoft.Web.LibraryManager | Správce knihovny | 15.8.27705.0 | Volitelné
Component.WebSocket | WebSocket4Net | 15.0.26606.0 | Volitelné
Microsoft.Net.Component.4.6.2.SDK | .NET Framework 4.6.2 SDK | 15.6.27406.0 | Volitelné
Microsoft.Net.Component.4.6.2.TargetingPack | .NET Framework 4.6.2 | 15.6.27406.0 | Volitelné
Microsoft.Net.Component.4.7.1.SDK | .NET Framework 4.7.1 SDK | 15.6.27406.0 | Volitelné
Microsoft.Net.Component.4.7.1.TargetingPack | .NET Framework 4.7.1 | 15.6.27406.0 | Volitelné
Microsoft.Net.Component.4.7.2.SDK | .NET Framework 4.7.2 SDK | 15.8.27825.0 | Volitelné
Microsoft.Net.Component.4.7.2.TargetingPack | .NET Framework 4.7.2 | 15.8.27825.0 | Volitelné
Microsoft.Net.Component.4.7.SDK | .NET Framework 4.7 SDK | 15.6.27406.0 | Volitelné
Microsoft.Net.Component.4.7.TargetingPack | Sada targeting pack .NET Framework 4,7 | 15.6.27406.0 | Volitelné
Microsoft.Net. Component. 4.6.2. DeveloperTools | Vývojové nástroje .NET Framework 4.6.2 | 15.6.27406.0 | Volitelné
Microsoft.Net. Component. 4.7.1. DeveloperTools | Vývojové nástroje .NET Framework 4.7.1 | 15.6.27406.0 | Volitelné
Microsoft.Net. Component. 4.7.2. DeveloperTools | Vývojové nástroje .NET Framework 4.7.2 | 15.8.27825.0 | Volitelné
Microsoft.Net. Component.. 4.7. DeveloperTools | Vývojové nástroje .NET Framework 4,7 | 15.6.27406.0 | Volitelné
Microsoft. NET. Core. Component. SDK | Vývojové nástroje .NET Core 2,0 | 15.6.27406.0 | Volitelné
Microsoft. NET. Core. Component. SDK. 1x | Vývojové nástroje .NET Core 1,0-1,1 | 15.6.27406.0 | Volitelné
Microsoft. NET. Core. Component. SDK. 2.1 | Vývojové nástroje .NET Core 2,1 | 15.8.27924.0 | Volitelné
Microsoft. NetCore. Component. DevelopmentTools | Vývojové nástroje .NET Core 2,0 | 15.8.27729.1 | Volitelné
Microsoft. NetCore. Component. DevelopmentTools. 2.1 | Vývojové nástroje .NET Core 2,1 | 15.8.27924.0 | Volitelné
Microsoft. VisualStudio. Component. CodeClone | Klonování kódu | 15.0.26208.0 | Volitelné
Microsoft.VisualStudio.Component.CodeMap | Mapa kódu | 15.0.26208.0 | Volitelné
Microsoft.VisualStudio.Component.Common.Azure.Tools | Nástroje pro připojení a publikování | 15.9.28107.0 | Volitelné
Microsoft.VisualStudio.Component.DependencyValidation.Enterprise | Živé ověřování závislostí | 15.0.26208.0 | Volitelné
Microsoft.VisualStudio.Component.DockerTools | Kontejnerové vývojové nástroje | 15.8.27906.1 | Volitelné
Microsoft.VisualStudio.Component.DockerTools.BuildTools | Nástroje pro vývoj kontejnerů – Build Tools | 15.7.27617.1 | Volitelné
Microsoft.VisualStudio.Component.FSharp | Podpora jazyka F# | 15.8.27825.0 | Volitelné
Microsoft.VisualStudio.Component.FSharp.Desktop | Podpora desktopových jazyků F# | 15.8.27825.0 | Volitelné
Microsoft.VisualStudio.Component.GraphDocument | Editor DGML | 15.0.27005.2 | Volitelné
Microsoft. VisualStudio. Component. IISExpress | IIS Express  | 15.0.26208.0 | Volitelné
Microsoft. VisualStudio. Component. JavaScript. Diagnostics | Diagnostika JavaScriptu | 15.8.27729.1 | Volitelné
Microsoft. VisualStudio. Component. JavaScript. TypeScript | Podpora jazyků JavaScript a TypeScript | 15.9.28125.51 | Volitelné
Microsoft. VisualStudio. Component. NuGet | Správce balíčků NuGet | 15.9.28016.0 | Volitelné
Microsoft. VisualStudio. Component. SQL. ADAL | Modul runtime SQL ADAL | 15.6.27406.0 | Volitelné
Microsoft. VisualStudio. Component. SQL. CMDUtils | SQL Server nástroje příkazového řádku | 15.0.26208.0 | Volitelné
Microsoft. VisualStudio. Component. SQL. DataSources | Zdroje dat pro podporu SQL Server | 15.0.26621.2 | Volitelné
Microsoft. VisualStudio. Component. SQL. LocalDB. Runtime | SQL Server Express 2016 LocalDB | 15.7.27617.1 | Volitelné
Microsoft.VisualStudio.Component.SQL.NCLI | Nativní klient systému SQL Server | 15.0.26208.0 | Volitelné
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 15.9.28107.0 | Volitelné
Microsoft.VisualStudio.Component.TypeScript.3.1 | TypeScript 3.1 SDK | 15.0.28218.60 | Volitelné
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | 15.8.27924.0 | Volitelné
Microsoft.VisualStudio.Component.Web | ASP.NET a webové vývojové nástroje | 15.8.27825.0 | Volitelné
Microsoft.VisualStudio.ComponentGroup.ArchitectureTools.Managed | Nástroje pro architekturu a analýzu | 15.0.26208.0 | Volitelné
Microsoft.VisualStudio.ComponentGroup.Web | Požadavky ASP.NET a webových vývojových nástrojů | 15.9.28219.51 | Volitelné
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Vývoj pro ASP.NET a web | 15.8.27825.0 | Volitelné

## <a name="game-development-with-unity"></a>Vývoj her pomocí Unity

**ID:** Microsoft.VisualStudio.Workload.ManagedGame

**Popis:** Vytváření 2D a 3D her pomocí Unity, výkonného vývojového prostředí pro více platforem

### <a name="components-included-by-this-workload"></a>Komponenty zahrnuté v této úlohu

ID součásti | Name | Verze | Typ závislosti
--- | --- | --- | ---
Microsoft.Net. Component. 3.5. DeveloperTools | Vývojové nástroje .NET Framework 3,5 | 15.6.27406.0 | Vyžadováno
Microsoft.Net. Component. 4.7.1. TargetingPack | Sada targeting pack .NET Framework 4.7.1 | 15.6.27406.0 | Vyžadováno
Microsoft. VisualStudio. Component. NuGet | Správce balíčků NuGet | 15.9.28016.0 | Vyžadováno
Microsoft. VisualStudio. Component. Roslyn. Compiler | Kompilátory C# a Visual Basic Roslyn | 15.6.27309.0 | Vyžadováno
Microsoft. VisualStudio. Component. Roslyn. LanguageServices | C# a Visual Basic | 15.8.27729.1 | Vyžadováno
Microsoft. VisualStudio. Component. static. Analysis. Tools | Nástroje statické analýzy | 15.0.26208.0 | Vyžadováno
Microsoft. VisualStudio. Component. Unity | Visual Studio Tools for Unity | 15.7.27617.1 | Vyžadováno
Component. UnityEngine. x64 | Editor bitových procesorů Unity 2018,3 64 | 15.9.28307.271 | Doporučeno
Component. UnityEngine. x86 | Unity 5.6 (32bitový editor) | 15.6.27406.0 | Doporučeno

## <a name="linux-development-with-c"></a>Vývoj linuxových aplikací v jazyce C++

**ID:** Microsoft.VisualStudio.Workload.NativeCrossPlat

**Popis:** Vytváření a ladění aplikací spuštěných v prostředí Linuxu

### <a name="components-included-by-this-workload"></a>Komponenty zahrnuté v této úlohu

ID komponenty | Name | Verze | Typ závislosti
--- | --- | --- | ---
Component.MDD.Linux | Visual C++ pro vývoj pro Linux | 15.6.27406.0 | Vyžadováno
Microsoft.VisualStudio.Component.VC.CoreIde | Visual Studio základních funkcí C++ | 15.6.27406.0 | Vyžadováno
Microsoft.VisualStudio.Component.Windows10SDK | Windows Universal C Runtime | 15.6.27406.0 | Vyžadováno
Component.Linux.CMake | Visual C++ nástroje pro CMake a Linux | 15.9.28307.102 | Doporučeno
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Nástroje pro statickou analýzu | 15.0.26208.0 | Doporučeno
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | Nástroje VC++ 2017 verze 15.9 v14.16 nejnovější verze 141 | 15.9.28230.55 | Doporučeno
Microsoft. VisualStudio. Component. Windows10SDK. 17763 | Windows 10 SDK (10.0.17763.0) | 15.9.28307.102 | Doporučeno
Microsoft. VisualStudio. Component. WebToolsExtensions | Vývoj pro ASP.NET a web | 15.8.27825.0 | Doporučeno
Component. MDD. Linux. RSZ. ARM | Vývoj integrovaných a IoT | 15.6.27309.0 | Volitelné

## <a name="desktop-development-with-c"></a>Vývoj desktopových aplikací pomocí C++

**ID:** Microsoft. VisualStudio. úlohy. NativeDesktop

**Popis:** Vytvářejte desktopové aplikace pro Windows pomocí sady nástrojů Microsoft C++, ATL nebo MFC.

### <a name="components-included-by-this-workload"></a>Součásti zahrnuté v tomto zatížení

ID součásti | Name | Verze | Typ závislosti
--- | --- | --- | ---
Microsoft. Component. MSBuild | MSBuild | 15.7.27520.0 | Vyžadováno
Microsoft. VisualStudio. Component. ClassDesigner | Návrhář tříd | 15.0.26208.0 | Vyžadováno
Microsoft. VisualStudio. Component. CodeMap | Mapa kódu | 15.0.26208.0 | Vyžadováno
Microsoft. VisualStudio. Component. GraphDocument | Editor DGML | 15.0.27005.2 | Vyžadováno
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilátory C# a Visual Basic Roslyn | 15.6.27309.0 | Vyžadováno
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 15.7.27617.1 | Vyžadováno
Microsoft.VisualStudio.Component.SQL.NCLI | Nativní klient systému SQL Server | 15.0.26208.0 | Vyžadováno
Microsoft.VisualStudio.Component.TextTemplating | Transformace textových šablon | 15.0.26208.0 | Vyžadováno
Microsoft.VisualStudio.Component.VC.CoreIde | Visual Studio základních funkcí C++ | 15.6.27406.0 | Vyžadováno
Microsoft.VisualStudio.Component.VC.Redist.14.Latest | Visual C++ 2017 Redistributable Update | 15.6.27406.0 | Vyžadováno
Microsoft.VisualStudio.ComponentGroup.ArchitectureTools.Native | Nástroje architektury pro C++ | 15.0.26208.0 | Vyžadováno
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Core | Visual C++ základní desktopové funkce | 15.8.27729.1 | Vyžadováno
Microsoft.VisualStudio.Component.Debugger.JustInTime | Ladicí program za běhu | 15.0.27005.2 | Doporučeno
Microsoft. VisualStudio. Component. Graphics. Tools | Ladicí program grafiky a Profiler GPU pro DirectX | 15.6.27406.0 | Doporučeno
Microsoft. VisualStudio. Component. Graphics. Win81 | Sada nástrojů Graphics Windows 8.1 SDK | 15.6.27406.0 | Doporučeno
Microsoft. VisualStudio. Component. IntelliTrace. front-end | IntelliTrace | 15.8.27729.1 | Doporučeno
Microsoft. VisualStudio. Component. NuGet | Správce balíčků NuGet | 15.9.28016.0 | Doporučeno
Microsoft. VisualStudio. Component. static. Analysis. Tools | Nástroje statické analýzy | 15.0.26208.0 | Doporučeno
Microsoft. VisualStudio. Component. VC. ATL | Visual C++ ATL pro x86 a x64 | 15.7.27625.0 | Doporučeno
Microsoft. VisualStudio. Component. VC. CMake. Project | Visual C++ nástroje pro CMake | 15.9.28307.102 | Doporučeno
Microsoft. VisualStudio. Component. VC. DiagnosticTools | Nástroje pro profilaci C++ | 15.0.26823.1 | Doporučeno
Microsoft. VisualStudio. Component. VC. TestAdapterForBoostTest | Testovací adaptér pro Boost.Test | 15.8.27906.1 | Doporučeno
Microsoft.VisualStudio.Component.VC.TestAdapterForGoogleTest | Testovací adaptér pro Google Test | 15.8.27906.1 | Doporučeno
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | Nástroje VC++ 2017 verze 15.9 v14.16 nejnovější verze 141 | 15.9.28230.55 | Doporučeno
Microsoft.VisualStudio.Component.Windows10SDK.17763 | Windows 10 SDK (10.0.17763.0) | 15.9.28307.102 | Doporučeno
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Vývoj pro ASP.NET a web | 15.8.27825.0 | Doporučeno
Component.Incredibuild | IncrediBuild – zrychlení sestavení | 15.7.27617.1 | Volitelné
Component.IncredibuildMenu | IncrediBuildMenu | 1.5.0.2 | Volitelné
Microsoft.Component.VC.Runtime.UCRTSDK | Univerzální sada CRT SDK pro Windows | 15.6.27309.0 | Volitelné
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 15.6.27406.0 | Volitelné
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 targeting pack | 15.6.27406.0 | Volitelné
Microsoft. VisualStudio. Component. VC. 140 | Sada nástrojů VC + + 2015,3 v 14.00 (v140) pro Desktop | 15.7.27617.1 | Volitelné
Microsoft. VisualStudio. Component. VC. ATLMFC | Visual C++ MFC pro x86 a x64 | 15.7.27625.0 | Volitelné
Microsoft. VisualStudio. Component. VC. CLI. support | Podpora C++/CLI | 15.6.27309.0 | Volitelné
Microsoft. VisualStudio. Component. VC. Modules. x86. x64 | Moduly pro standardní knihovnu (experimentální) | 15.6.27309.0 | Volitelné
Microsoft. VisualStudio. Component. Windows10SDK. 10240 | Windows 10 SDK (10.0.10240.0) | 15.6.27406.0 | Volitelné
Microsoft. VisualStudio. Component. Windows10SDK. 10586 | Windows 10 SDK (10.0.10586.0) | 15.6.27406.0 | Volitelné
Microsoft. VisualStudio. Component. Windows10SDK. 14393 | Windows 10 SDK (10.0.14393.0) | 15.6.27406.0 | Volitelné
Microsoft. VisualStudio. Component. Windows10SDK. 15063. Desktop | Windows 10 SDK (10.0.15063.0) pro Desktop C++ [x86 a x64] | 15.6.27406.0 | Volitelné
Microsoft. VisualStudio. Component. Windows10SDK. 15063. UWP | Windows 10 SDK (10.0.15063.0) pro UWP: C#, VB, JS | 15.6.27406.0 | Volitelné
Microsoft. VisualStudio. Component. Windows10SDK. 15063. UWP. Native | Windows 10 SDK (10.0.15063.0) pro UPW: C++ | 15.6.27406.0 | Volitelné
Microsoft.VisualStudio.Component.Windows10SDK.16299.Desktop | Windows 10 SDK (10.0.16299.0) pro Desktop C++ [x86 a x64] | 15.6.27406.0 | Volitelné
Microsoft.VisualStudio.Component.Windows10SDK.16299.Desktop.arm | Windows 10 SDK (10.0.16299.0) pro Desktop C++ [ARM a ARM64] | 15.6.27406.0 | Volitelné
Microsoft.VisualStudio.Component.Windows10SDK.16299.UPW | Windows 10 SDK (10.0.16299.0) pro UPW: C#, VB, JS | 15.6.27406.0 | Volitelné
Microsoft.VisualStudio.Component.Windows10SDK.16299.UPW.Native | Windows 10 SDK (10.0.16299.0) pro UPW: C++ | 15.6.27406.0 | Volitelné
Microsoft.VisualStudio.Component.Windows10SDK.17134 | Windows 10 SDK (10.0.17134.0) | 15.9.28307.102 | Volitelné
Microsoft.VisualStudio.Component.Windows81SDK | Windows 8.1 SDK | 15.6.27406.0 | Volitelné
Microsoft.VisualStudio.Component.WinXP | Podpora windows XP pro C++ | 15.8.27924.0 | Volitelné
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Win81 | Windows 8.1 SDK a UCRT SDK | 15.6.27406.0 | Volitelné
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.WinXP | Podpora windows XP pro C++ | 15.8.27705.0 | Volitelné
Microsoft.VisualStudio.ComponentGroup.Windows10SDK.15063 | Windows 10 SDK (10.0.15063.0) | 15.8.27825.0 | Volitelné
Microsoft. VisualStudio. Component. Windows10SDK. 16299 | Windows 10 SDK (10.0.16299.0) | 15.8.27825.0 | Volitelné

## <a name="game-development-with-c"></a>Vývoj her v jazyce C++

**ID:** Microsoft. VisualStudio. úlohy. NativeGame

**Popis:** Využijte výhod C++ k sestavování profesionálních her využívajících rozhraní DirectX, Unreal nebo Cocos2d.

### <a name="components-included-by-this-workload"></a>Součásti zahrnuté v tomto zatížení

ID součásti | Name | Verze | Typ závislosti
--- | --- | --- | ---
Microsoft. VisualStudio. Component. static. Analysis. Tools | Nástroje statické analýzy | 15.0.26208.0 | Vyžadováno
Microsoft. VisualStudio. Component. VC. CoreIde | Visual Studio C++ – základní funkce | 15.6.27406.0 | Vyžadováno
Microsoft. VisualStudio. Component. VC. Redist. 14. nejnovější | Aktualizace Visual C++ 2017 Redistributable | 15.6.27406.0 | Vyžadováno
Microsoft. VisualStudio. Component. VC. Tools. x86. x64 | VC + + 2017 verze 15,9 v 14.16 nejnovější nástroje v141 | 15.9.28230.55 | Vyžadováno
Microsoft. VisualStudio. Component. Windows10SDK | Windows Universal C Runtime | 15.6.27406.0 | Vyžadováno
Microsoft.VisualStudio.Component.Graphics.Tools | Ladicí program grafiky a profiler GPU pro DirectX | 15.6.27406.0 | Doporučeno
Microsoft.VisualStudio.Component.Graphics.Win81 | Graphics Tools Windows 8.1 SDK | 15.6.27406.0 | Doporučeno
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | 15.8.27729.1 | Doporučeno
Microsoft.VisualStudio.Component.VC.DiagnosticTools | Nástroje pro profilaci jazyka C++ | 15.0.26823.1 | Doporučeno
Microsoft.VisualStudio.Component.Windows10SDK.17763 | Windows 10 SDK (10.0.17763.0) | 15.9.28307.102 | Doporučeno
Component.Android.NDK.R12B | Android NDK (R12B) | 12.1.10 | Volitelné
Component.Android.SDK23.Private | Android SDK nastavení (úroveň 23 rozhraní API) (místní instalace pro vývoj pro mobilní zařízení pomocí JavaScriptu nebo C++) | 15.9.28016.0 | Volitelné
Component.Ant | Apache Ant (1.9.3) | 1.9.3.8 | Volitelné
Component.Cocos | Cocos | 15.0.26906.1 | Volitelné
Component. IncrediBuild | IncrediBuild – zrychlení sestavení | 15.7.27617.1 | Volitelné
Component. IncredibuildMenu | IncrediBuildMenu | 1.5.0.2 | Volitelné
Component. MDD. Android | Vývojové nástroje C++ pro Android | 15.0.26606.0 | Volitelné
Component. OpenJDK | Distribuční OpenJDK Microsoftu | 15.9.28125.51 | Volitelné
Component. Unreal | Instalační program Unreal Engine | 15.8.27729.1 | Volitelné
Component. Unreal. Android | Podpora Androidu v systému Visual Studio pro Unreal Engine | 15.9.28307.341 | Volitelné
Microsoft. Component. VC. Runtime. UCRTSDK | Sada Windows Universal CRT SDK | 15.6.27309.0 | Volitelné
Microsoft.Net. Component. 4.5.1. TargetingPack | Sada .NET Framework 4.5.1 targeting pack | 15.6.27406.0 | Volitelné
Microsoft.Net. Component. 4.5.2. TargetingPack | .NET Framework 4.5.2 | 15.6.27406.0 | Volitelné
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 | 15.6.27406.0 | Volitelné
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 15.6.27406.0 | Volitelné
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 | 15.6.27406.0 | Volitelné
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework 4.6 | 15.6.27406.0 | Volitelné
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 cílení pack | 15.6.27406.0 | Volitelné
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | .NET Framework 4.6.1 | 15.8.27825.0 | Volitelné
Microsoft.Net.ComponentGroup.TargetingPacks.Common | .NET Framework 4–4.6 – vývojové nástroje | 15.6.27406.0 | Volitelné
Microsoft.VisualStudio.Component.NuGet.BuildTools | Cíle a úlohy sestavení NuGet | 15.9.28016.0 | Volitelné
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilátory C# a Visual Basic Roslyn | 15.6.27309.0 | Volitelné
Microsoft. VisualStudio. Component. Roslyn. LanguageServices | C# a Visual Basic | 15.8.27729.1 | Volitelné
Microsoft. VisualStudio. Component. Windows10SDK. 10240 | Windows 10 SDK (10.0.10240.0) | 15.6.27406.0 | Volitelné
Microsoft. VisualStudio. Component. Windows10SDK. 10586 | Windows 10 SDK (10.0.10586.0) | 15.6.27406.0 | Volitelné
Microsoft. VisualStudio. Component. Windows10SDK. 14393 | Windows 10 SDK (10.0.14393.0) | 15.6.27406.0 | Volitelné
Microsoft. VisualStudio. Component. Windows10SDK. 15063. Desktop | Windows 10 SDK (10.0.15063.0) pro Desktop C++ [x86 a x64] | 15.6.27406.0 | Volitelné
Microsoft. VisualStudio. Component. Windows10SDK. 15063. UWP | Windows 10 SDK (10.0.15063.0) pro UWP: C#, VB, JS | 15.6.27406.0 | Volitelné
Microsoft. VisualStudio. Component. Windows10SDK. 15063. UWP. Native | Windows 10 SDK (10.0.15063.0) pro UWP: C++ | 15.6.27406.0 | Volitelné
Microsoft. VisualStudio. Component. Windows10SDK. 16299. Desktop | Windows 10 SDK (10.0.16299.0) pro Desktop C++ [x86 a x64] | 15.6.27406.0 | Volitelné
Microsoft. VisualStudio. Component. Windows10SDK. 16299. Desktop. ARM | Windows 10 SDK (10.0.16299.0) pro Desktop C++ [ARM a ARM64] | 15.6.27406.0 | Volitelné
Microsoft. VisualStudio. Component. Windows10SDK. 16299. UWP | Windows 10 SDK (10.0.16299.0) pro UWP: C#, VB, JS | 15.6.27406.0 | Volitelné
Microsoft. VisualStudio. Component. Windows10SDK. 16299. UWP. Native | Windows 10 SDK (10.0.16299.0) pro UPW: C++ | 15.6.27406.0 | Volitelné
Microsoft.VisualStudio.Component.Windows10SDK.17134 | Windows 10 SDK (10.0.17134.0) | 15.9.28307.102 | Volitelné
Microsoft.VisualStudio.Component.Windows81SDK | Windows 8.1 SDK | 15.6.27406.0 | Volitelné
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Win81 | Windows 8.1 SDK a UCRT SDK | 15.6.27406.0 | Volitelné
Microsoft.VisualStudio.ComponentGroup.Windows10SDK.15063 | Windows 10 SDK (10.0.15063.0) | 15.8.27825.0 | Volitelné
Microsoft.VisualStudio.ComponentGroup.Windows10SDK.16299 | Windows 10 SDK (10.0.16299.0) | 15.8.27825.0 | Volitelné

## <a name="mobile-development-with-c"></a>Vývoj mobilních aplikací v jazyce C++

**ID:** Microsoft.VisualStudio.Workload.NativeMobile

**Popis:** Vytváření aplikací pro více platforem pro iOS, Android nebo Windows pomocí C++.

### <a name="components-included-by-this-workload"></a>Komponenty zahrnuté v této úlohu

ID komponenty | Name | Verze | Typ závislosti
--- | --- | --- | ---
Component.Android.SDK19.Private | Android SDK nastavení (úroveň 19 rozhraní API) (místní instalace pro vývoj mobilních aplikací pomocí JavaScriptu nebo C++) | 15.9.28107.0 | Vyžadováno
Component.Android.SDK21.Private | Instalace Android SDK (úroveň rozhraní API 21) (místní instalace pro vývoj pro mobilní zařízení pomocí JavaScriptu nebo C++) | 15.9.28016.0 | Vyžadováno
Component. Android. SDK22. Private | Instalace Android SDK (úroveň rozhraní API 22) (místní instalace pro vývoj pro mobilní zařízení pomocí JavaScriptu nebo C++) | 15.9.28016.0 | Vyžadováno
Component. Android. SDK23. Private | Instalace Android SDK (úroveň rozhraní API 23) (místní instalace pro vývoj pro mobilní zařízení pomocí JavaScriptu nebo C++) | 15.9.28016.0 | Vyžadováno
Component. Android. SDK25. Private | Instalace Android SDK (úroveň rozhraní API 25) (místní instalace pro vývoj pro mobilní zařízení pomocí JavaScriptu nebo C++) | 15.9.28016.0 | Vyžadováno
Component. OpenJDK | Distribuční OpenJDK Microsoftu | 15.9.28125.51 | Vyžadováno
Microsoft. VisualStudio. Component. VC. CoreIde | Visual Studio C++ – základní funkce | 15.6.27406.0 | Vyžadováno
Komponenta. Android. NDK. R15C | Android NDK (R15C) | 15.2.1 | Doporučeno
Component. ANT | Apache Ant (1.9.3) | 1.9.3.8 | Doporučeno
Component.MDD.Android | Vývojové nástroje pro C++ pro Android | 15.0.26606.0 | Doporučeno
Component.Android.NDK.R12B | Android NDK (R12B) | 12.1.10 | Volitelné
Component.Android.NDK.R12B_3264 | Android NDK (R12B) (32bitová verze) | 12.1.11 | Volitelné
Component.Android.NDK.R13B | Android NDK (R13B) | 13.1.7 | Volitelné
Component.Android.NDK.R13B_3264 | Android NDK (R13B) (32bitová verze) | 13.1.8 | Volitelné
Component.Android.NDK.R15C_3264 | Android NDK (R15C) (32bitová verze) | 15.2.1 | Volitelné
Component.Google.Android.Emulator.API23.Private | Google Android Emulator (rozhraní API úrovně 23) (místní instalace) | 15.6.27413.0 | Volitelné
Component.HAXM.Private | Intel Hardware Accelerated Execution Manager (modul HAXM) (místní instalace) | 15.9.28307.421 | Volitelné
Component. IncrediBuild | IncrediBuild – zrychlení sestavení | 15.7.27617.1 | Volitelné
Component. IncredibuildMenu | IncrediBuildMenu | 1.5.0.2 | Volitelné
Component. MDD. IOS | Vývojové nástroje C++ pro iOS | 15.0.26621.2 | Volitelné

## <a name="net-core-cross-platform-development"></a>Vývoj multiplatformních aplikací pomocí rozhraní .NET Core

**ID:** Microsoft. VisualStudio. úlohy. NetCoreTools

**Popis:** Vytvářejte aplikace pro různé platformy pomocí .NET Core, ASP.NET Core, HTML/JavaScript a kontejnerů včetně podpory Docker.

### <a name="components-included-by-this-workload"></a>Součásti zahrnuté v tomto zatížení

ID součásti | Name | Verze | Typ závislosti
--- | --- | --- | ---
Součást. Microsoft. VisualStudio. RazorExtension | Jazykové služby Razor | 15.0.26720.2 | Vyžadováno
Součást. Microsoft. Web. LibraryManager | Správce knihovny | 15.8.27705.0 | Vyžadováno
Komponenta. WebSocket | WebSocket4Net | 15.0.26606.0 | Vyžadováno
Microsoft.Component.ClickOnce | Publikování ClickOnce | 15.8.27825.0 | Vyžadováno
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | Vyžadováno
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 | 15.6.27406.0 | Vyžadováno
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 | 15.6.27406.0 | Vyžadováno
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 15.6.27406.0 | Vyžadováno
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 | 15.6.27406.0 | Vyžadováno
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | .NET Framework 4.6.1 | 15.8.27825.0 | Vyžadováno
Microsoft.Net.Core.Component.SDK.2.1 | Vývojové nástroje .NET Core 2.1 | 15.8.27924.0 | Vyžadováno
Microsoft.NetCore.ComponentGroup.DevelopmentTools.2.1 | Vývojové nástroje .NET Core 2.1 | 15.8.27924.0 | Vyžadováno
Microsoft.NetCore.ComponentGroup.Web.2.1 | Vývojové nástroje .NET Core 2.1 | 15.8.27924.0 | Vyžadováno
Microsoft.VisualStudio.Component.Common.Azure.Tools | Nástroje pro připojení a publikování | 15.9.28107.0 | Vyžadováno
Microsoft.VisualStudio.Component.DockerTools | Kontejnerové vývojové nástroje | 15.8.27906.1 | Vyžadováno
Microsoft.VisualStudio.Component.DockerTools. BuildTools | Nástroje pro vývoj kontejnerů – nástroje sestavení | 15.7.27617.1 | Vyžadováno
Microsoft. VisualStudio. Component. FSharp | Podpora jazyka F # | 15.8.27825.0 | Vyžadováno
Microsoft. VisualStudio. Component. FSharp. Webtemplates | Podpora jazyka F # pro webové projekty | 15.9.28307.421 | Vyžadováno
Microsoft. VisualStudio. Component. IISExpress | IIS Express  | 15.0.26208.0 | Vyžadováno
Microsoft. VisualStudio. Component. JavaScript. Diagnostics | Diagnostika JavaScriptu | 15.8.27729.1 | Vyžadováno
Microsoft. VisualStudio. Component. JavaScript. TypeScript | Podpora jazyků JavaScript a TypeScript | 15.9.28125.51 | Vyžadováno
Microsoft. VisualStudio. Component. ManagedDesktop. Core | Jádro úlohy spravované plochy | 15.8.27729.1 | Vyžadováno
Microsoft.VisualStudio.Component.NuGet | Správce balíčků NuGet | 15.9.28016.0 | Vyžadováno
Microsoft.VisualStudio.Component.PortableLibrary | Balíček cílení na přenosnou knihovnu .NET | 15.6.27309.0 | Vyžadováno
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilátory C# a Visual Basic Roslyn | 15.6.27309.0 | Vyžadováno
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# a Visual Basic | 15.8.27729.1 | Vyžadováno
Microsoft.VisualStudio.Component.SQL.ADAL | Modul runtime SQL ADAL | 15.6.27406.0 | Vyžadováno
Microsoft.VisualStudio.Component.SQL.CLR | Datové typy CLR pro SQL Server | 15.0.26208.0 | Vyžadováno
Microsoft.VisualStudio.Component.SQL.CMDUtils | SQL Server nástroje příkazového řádku | 15.0.26208.0 | Vyžadováno
Microsoft.VisualStudio.Component.SQL.DataSources | Zdroje dat pro SQL Server dat | 15.0.26621.2 | Vyžadováno
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 15.7.27617.1 | Vyžadováno
Microsoft. VisualStudio. Component. SQL. NCLI | Nativní klient systému SQL Server | 15.0.26208.0 | Vyžadováno
Microsoft. VisualStudio. Component. SQL. SSDT | SQL Server Data Tools | 15.9.28107.0 | Vyžadováno
Microsoft. VisualStudio. Component. static. Analysis. Tools | Nástroje statické analýzy | 15.0.26208.0 | Vyžadováno
Microsoft. VisualStudio. Component. TextTemplating | Transformace textové šablony | 15.0.26208.0 | Vyžadováno
Microsoft. VisualStudio. Component. TypeScript. 3.1 | Sada TypeScript 3,1 SDK | 15.0.28218.60 | Vyžadováno
Microsoft. VisualStudio. Component. VisualStudioData | Zdroje dat a odkazy na služby | 15.6.27406.0 | Vyžadováno
Microsoft. VisualStudio. Component. Web | Požadavky na ASP.NET a vývojové nástroje pro web | 15.9.28219.51 | Vyžadováno
Microsoft. VisualStudio. Component. WebToolsExtensions | Vývoj pro ASP.NET a web | 15.8.27825.0 | Vyžadováno
Součást. Microsoft. VisualStudio. Web. AzureFunctions | Microsoft Azure WebJobs Tools | 15.7.27617.1 | Doporučeno
Microsoft.VisualStudio.Component.AppInsights.Tools | Vývojářské analytické nástroje | 15.8.27825.0 | Doporučeno
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Nástroje pro vytváření v Azure | 15.9.28307.421 | Doporučeno
Microsoft.VisualStudio.Component.Azure.ClientLibs | Knihovny Azure pro .NET | 15.0.26208.0 | Doporučeno
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Azure Compute emulátoru | 15.9.28307.421 | Doporučeno
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Emulátor úložiště Azure | 15.9.28125.51 | Doporučeno
Microsoft.VisualStudio.Component.CloudExplorer | Průzkumník cloudu | 15.9.28230.55 | Doporučeno
Microsoft.VisualStudio.Component.Debugger.Snapshot | Ladicí program snímků | 15.8.28010.0 | Doporučeno
Microsoft.VisualStudio.Component.DiagnosticTools | Nástroje pro profilaci .NET | 15.8.27729.1 | Doporučeno
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | 15.8.27729.1 | Doporučeno
Microsoft. VisualStudio. Component. LiveUnitTesting | Live Unit Testing | 15.0.26720.2 | Doporučeno
Microsoft. VisualStudio. Component. Web | ASP.NET a vývojové nástroje pro web | 15.8.27825.0 | Doporučeno
Microsoft. VisualStudio. Component. WebDeploy | Web Deploy | 15.8.27729.1 | Doporučeno
Microsoft. VisualStudio. Component. AzureFunctions | Nástroje Microsoft Azure WebJobs | 15.7.27617.1 | Doporučeno
Microsoft. VisualStudio. Component. Web. CloudTools | Cloudové nástroje pro vývoj pro web | 15.8.27729.1 | Doporučeno
Microsoft. NET. Core. Component. SDK | Vývojové nástroje .NET Core 2,0 | 15.6.27406.0 | Volitelné
Microsoft. NET. Core. Component. SDK. 1x | Vývojové nástroje .NET Core 1,0-1,1 | 15.6.27406.0 | Volitelné
Microsoft. NetCore. 1x. Component. Web | .NET Core 1,0 – 1,1 vývojové nástroje pro web | 15.6.27406.0 | Volitelné
Microsoft. NetCore. Component. DevelopmentTools | Vývojové nástroje .NET Core 2,0 | 15.8.27729.1 | Volitelné
Microsoft. NetCore. Component. Web | Vývojové nástroje .NET Core 2,0 | 15.7.27625.0 | Volitelné
Microsoft. VisualStudio. Component. IISDevelopment | Podpora služby IIS pro dobu vývoje | 15.9.28219.51 | Volitelné

## <a name="mobile-development-with-net"></a>Vývoj mobilních aplikací pomocí .NET

**ID:** Microsoft.VisualStudio.Workload.NetCrossPlat

**Popis:** Vytváření aplikací pro více platforem pro iOS, Android nebo Windows pomocí Xamarinu

### <a name="components-included-by-this-workload"></a>Komponenty zahrnuté v této úlohu

ID komponenty | Name | Verze | Typ závislosti
--- | --- | --- | ---
Component.Xamarin | Xamarin | 15.8.27906.1 | Vyžadováno
Component.Xamarin.RemotedSimulator | Xamarin Remoted Simulator | 15.6.27323.2 | Vyžadováno
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | Vyžadováno
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 15.6.27406.0 | Vyžadováno
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 | 15.6.27406.0 | Vyžadováno
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | .NET Framework 4.6.1 | 15.8.27825.0 | Vyžadováno
Microsoft.Net.Core.Component.SDK | Vývojové nástroje .NET Core 2.0 | 15.6.27406.0 | Vyžadováno
Microsoft. NetCore. Component. DevelopmentTools | Vývojové nástroje .NET Core 2,0 | 15.8.27729.1 | Vyžadováno
Microsoft. VisualStudio. Component. FSharp | Podpora jazyka F # | 15.8.27825.0 | Vyžadováno
Microsoft. VisualStudio. Component. Merq | Běžné interní nástroje Xamarin | 15.8.27924.0 | Vyžadováno
Microsoft. VisualStudio. Component. MonoDebugger | Ladicí program mono | 15.0.26720.2 | Vyžadováno
Microsoft. VisualStudio. Component. NuGet | Správce balíčků NuGet | 15.9.28016.0 | Vyžadováno
Microsoft. VisualStudio. Component. PortableLibrary | Sada targeting pack přenosné knihovny .NET | 15.6.27309.0 | Vyžadováno
Microsoft. VisualStudio. Component. Roslyn. Compiler | Kompilátory C# a Visual Basic Roslyn | 15.6.27309.0 | Vyžadováno
Microsoft. VisualStudio. Component. Roslyn. LanguageServices | C# a Visual Basic | 15.8.27729.1 | Vyžadováno
Microsoft. VisualStudio. Component. static. Analysis. Tools | Nástroje statické analýzy | 15.0.26208.0 | Vyžadováno
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions.TemplateEngine | ASP.NET šablonovací modul | 15.8.27729.1 | Vyžadováno
Component.Android.SDK27 | Android SDK nastavení (úroveň rozhraní API 27) | 15.9.28016.0 | Doporučeno
Component.Google.Android.Emulator.API27 | Google Android Emulator (rozhraní API úrovně 27) | 15.9.28307.421 | Doporučeno
Component.HAXM | Intel Hardware Accelerated Execution Manager (HAXM) (globální instalace) | 15.9.28307.421 | Doporučeno
Component.OpenJDK | OpenJDK pro distribuci Od Microsoftu | 15.9.28125.51 | Doporučeno
Component.Xamarin.Profiler | Xamarin Profiler | 15.0.27005.2 | Doporučeno
Component.Xamarin.Inspector | Sešity ke Xamarinu | 15.0.26606.0 | Volitelné
Microsoft.Component.ClickOnce | Publikování ClickOnce | 15.8.27825.0 | Volitelné
Microsoft.Component.NetFX.Native | .NET Native | 15.0.26208.0 | Volitelné
Microsoft. VisualStudio. Component. AppInsights. Tools | Vývojářské analytické nástroje | 15.8.27825.0 | Volitelné
Microsoft. VisualStudio. Component. CodeClone | Klon kódu | 15.0.26208.0 | Volitelné
Microsoft. VisualStudio. Component. CodeMap | Mapa kódu | 15.0.26208.0 | Volitelné
Microsoft. VisualStudio. Component. DependencyValidation. Enterprise | Ověřování závislostí v reálném čase | 15.0.26208.0 | Volitelné
Microsoft. VisualStudio. Component. DiagnosticTools | Nástroje pro profilaci .NET | 15.8.27729.1 | Volitelné
Microsoft. VisualStudio. Component. GraphDocument | Editor DGML | 15.0.27005.2 | Volitelné
Microsoft. VisualStudio. Component. Graphics | Editory obrázků a 3D model | 15.6.27406.0 | Volitelné
Microsoft. VisualStudio. Component. SQL. CLR | Datové typy CLR pro SQL Server | 15.0.26208.0 | Volitelné
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 15.7.27617.1 | Volitelné
Microsoft.VisualStudio.Component.SQL.NCLI | Nativní klient systému SQL Server | 15.0.26208.0 | Volitelné
Microsoft.VisualStudio.Component.VisualStudioData | Zdroje dat a odkazy na služby | 15.6.27406.0 | Volitelné
Microsoft.VisualStudio.Component.Windows10SDK.17763 | Windows 10 SDK (10.0.17763.0) | 15.9.28307.102 | Volitelné
Microsoft.VisualStudio.ComponentGroup.ArchitectureTools.Managed | Nástroje pro architekturu a analýzu | 15.0.26208.0 | Volitelné
Microsoft.VisualStudio.ComponentGroup.UWP.Xamarin | Univerzální platforma Windows nástroje pro Xamarin | 15.9.28307.102 | Volitelné

## <a name="aspnet-and-web-development"></a>Vývoj pro ASP.NET a web

**ID:** Microsoft.VisualStudio.Workload.NetWeb

**Popis:** Vytváření webových aplikací pomocí ASP.NET, ASP.NET Core, HTML/JavaScript a kontejnerů, včetně podpory Dockeru

### <a name="components-included-by-this-workload"></a>Komponenty zahrnuté v této úlohu

ID komponenty | Name | Verze | Typ závislosti
--- | --- | --- | ---
Součást. Microsoft. VisualStudio. RazorExtension | Jazykové služby Razor | 15.0.26720.2 | Vyžadováno
Součást. Microsoft. Web. LibraryManager | Správce knihovny | 15.8.27705.0 | Vyžadováno
Komponenta. WebSocket | WebSocket4Net | 15.0.26606.0 | Vyžadováno
Microsoft. Component. ClickOnce | Publikování ClickOnce | 15.8.27825.0 | Vyžadováno
Microsoft. Component. MSBuild | MSBuild | 15.7.27520.0 | Vyžadováno
Microsoft.Net. Component. 4.5.2. TargetingPack | Sada .NET Framework 4.5.2 targeting pack | 15.6.27406.0 | Vyžadováno
Microsoft.Net. Component. 4.5. TargetingPack | Sada targeting pack .NET Framework 4,5 | 15.6.27406.0 | Vyžadováno
Microsoft. NET. Component. 4.6.1. SDK | .NET Framework 4.6.1 SDK | 15.6.27406.0 | Vyžadováno
Microsoft.Net. Component. 4.6.1. TargetingPack | .NET Framework 4.6.1 targeting pack | 15.6.27406.0 | Vyžadováno
Microsoft.Net. Component. DevelopmentPrerequisites | Vývojové nástroje .NET Framework 4.6.1 | 15.8.27825.0 | Vyžadováno
Microsoft.Net.Core.Component.SDK.2.1 | Vývojové nástroje .NET Core 2.1 | 15.8.27924.0 | Vyžadováno
Microsoft.NetCore.ComponentGroup.DevelopmentTools.2.1 | Vývojové nástroje .NET Core 2.1 | 15.8.27924.0 | Vyžadováno
Microsoft.NetCore.ComponentGroup.Web.2.1 | Vývojové nástroje .NET Core 2.1 | 15.8.27924.0 | Vyžadováno
Microsoft.VisualStudio.Component.Common.Azure.Tools | Nástroje pro připojení a publikování | 15.9.28107.0 | Vyžadováno
Microsoft.VisualStudio.Component.DockerTools | Kontejnerové vývojové nástroje | 15.8.27906.1 | Vyžadováno
Microsoft.VisualStudio.Component.DockerTools.BuildTools | Nástroje pro vývoj kontejnerů – Build Tools | 15.7.27617.1 | Vyžadováno
Microsoft.VisualStudio.Component.FSharp | Podpora jazyka F# | 15.8.27825.0 | Vyžadováno
Microsoft.VisualStudio.Component.FSharp.WebTemplates | Podpora jazyka F# pro webové projekty | 15.9.28307.421 | Vyžadováno
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 15.0.26208.0 | Vyžadováno
Microsoft. VisualStudio. Component. JavaScript. Diagnostics | Diagnostika JavaScriptu | 15.8.27729.1 | Vyžadováno
Microsoft. VisualStudio. Component. JavaScript. TypeScript | Podpora jazyků JavaScript a TypeScript | 15.9.28125.51 | Vyžadováno
Microsoft. VisualStudio. Component. ManagedDesktop. Core | Jádro úlohy spravované plochy | 15.8.27729.1 | Vyžadováno
Microsoft. VisualStudio. Component. NuGet | Správce balíčků NuGet | 15.9.28016.0 | Vyžadováno
Microsoft. VisualStudio. Component. PortableLibrary | Sada targeting pack přenosné knihovny .NET | 15.6.27309.0 | Vyžadováno
Microsoft. VisualStudio. Component. Roslyn. Compiler | Kompilátory C# a Visual Basic Roslyn | 15.6.27309.0 | Vyžadováno
Microsoft. VisualStudio. Component. Roslyn. LanguageServices | C# a Visual Basic | 15.8.27729.1 | Vyžadováno
Microsoft. VisualStudio. Component. SQL. ADAL | Modul runtime SQL ADAL | 15.6.27406.0 | Vyžadováno
Microsoft. VisualStudio. Component. SQL. CLR | Datové typy CLR pro SQL Server | 15.0.26208.0 | Vyžadováno
Microsoft.VisualStudio.Component.SQL.CMDUtils | SQL Server nástroje příkazového řádku | 15.0.26208.0 | Vyžadováno
Microsoft.VisualStudio.Component.SQL.DataSources | Zdroje dat pro SQL Server dat | 15.0.26621.2 | Vyžadováno
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 15.7.27617.1 | Vyžadováno
Microsoft.VisualStudio.Component.SQL.NCLI | Nativní klient systému SQL Server | 15.0.26208.0 | Vyžadováno
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 15.9.28107.0 | Vyžadováno
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Nástroje pro statickou analýzu | 15.0.26208.0 | Vyžadováno
Microsoft.VisualStudio.Component.TextTemplating | Transformace textových šablon | 15.0.26208.0 | Vyžadováno
Microsoft.VisualStudio.Component.TypeScript.3.1 | TypeScript 3.1 SDK | 15.0.28218.60 | Vyžadováno
Microsoft. VisualStudio. Component. VisualStudioData | Zdroje dat a odkazy na služby | 15.6.27406.0 | Vyžadováno
Microsoft. VisualStudio. Component. Web | ASP.NET a vývojové nástroje pro web | 15.8.27825.0 | Vyžadováno
Microsoft. VisualStudio. Component. Web | Požadavky na ASP.NET a vývojové nástroje pro web | 15.9.28219.51 | Vyžadováno
Microsoft. VisualStudio. Component. WebToolsExtensions | Vývoj pro ASP.NET a web | 15.8.27825.0 | Vyžadováno
Součást. Microsoft. VisualStudio. Web. AzureFunctions | Nástroje Microsoft Azure WebJobs | 15.7.27617.1 | Doporučeno
Microsoft.Net. Component. 4.5.1. TargetingPack | Sada .NET Framework 4.5.1 targeting pack | 15.6.27406.0 | Doporučeno
Microsoft.Net. Component. 4.6. TargetingPack | Sada targeting pack .NET Framework 4,6 | 15.6.27406.0 | Doporučeno
Microsoft.Net. Component. 4. TargetingPack | Sada targeting pack .NET Framework 4 | 15.6.27406.0 | Doporučeno
Microsoft.Net. Component. TargetingPacks. Common | .NET Framework nástroje pro vývoj 4 – 4,6 | 15.6.27406.0 | Doporučeno
Microsoft. VisualStudio. Component. AppInsights. Tools | Vývojářské analytické nástroje | 15.8.27825.0 | Doporučeno
Microsoft.VisualStudio.Component.AspNet45 | Pokročilé ASP.NET funkcí | 15.7.27625.0 | Doporučeno
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Nástroje pro vytváření v Azure | 15.9.28307.421 | Doporučeno
Microsoft.VisualStudio.Component.Azure.ClientLibs | Knihovny Azure pro .NET | 15.0.26208.0 | Doporučeno
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Azure Compute emulátoru | 15.9.28307.421 | Doporučeno
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Emulátor úložiště Azure | 15.9.28125.51 | Doporučeno
Microsoft.VisualStudio.Component.CloudExplorer | Průzkumník cloudu | 15.9.28230.55 | Doporučeno
Microsoft.VisualStudio.Component.Debugger.Snapshot | Ladicí program snímků | 15.8.28010.0 | Doporučeno
Microsoft.VisualStudio.Component.DiagnosticTools | Nástroje pro profilaci .NET | 15.8.27729.1 | Doporučeno
Microsoft.VisualStudio.Component.EntityFramework | Entity Framework 6 nástrojů | 15.6.27406.0 | Doporučeno
Microsoft. VisualStudio. Component. IntelliTrace. front-end | IntelliTrace | 15.8.27729.1 | Doporučeno
Microsoft. VisualStudio. Component. LiveUnitTesting | Live Unit Testing | 15.0.26720.2 | Doporučeno
Microsoft. VisualStudio. Component. WCF. Tools | Windows Communication Foundation | 15.8.27924.0 | Doporučeno
Microsoft. VisualStudio. Component. WebDeploy | Web Deploy | 15.8.27729.1 | Doporučeno
Microsoft. VisualStudio. Component. AzureFunctions | Nástroje Microsoft Azure WebJobs | 15.7.27617.1 | Doporučeno
Microsoft. VisualStudio. Component. Web. CloudTools | Cloudové nástroje pro vývoj pro web | 15.8.27729.1 | Doporučeno
Microsoft. NET. Component. 4.6.2. SDK | Sada .NET Framework 4.6.2 SDK | 15.6.27406.0 | Volitelné
Microsoft.Net. Component. 4.6.2. TargetingPack | Sada targeting pack .NET Framework 4.6.2 | 15.6.27406.0 | Volitelné
Microsoft. NET. Component. 4.7.1. SDK | Sada .NET Framework 4.7.1 SDK | 15.6.27406.0 | Volitelné
Microsoft.Net. Component. 4.7.1. TargetingPack | Sada targeting pack .NET Framework 4.7.1 | 15.6.27406.0 | Volitelné
Microsoft. NET. Component. 4.7.2. SDK | Sada .NET Framework 4.7.2 SDK | 15.8.27825.0 | Volitelné
Microsoft.Net. Component. 4.7.2. TargetingPack | .NET Framework 4.7.2 | 15.8.27825.0 | Volitelné
Microsoft.Net.Component.4.7.SDK | .NET Framework 4.7 SDK | 15.6.27406.0 | Volitelné
Microsoft.Net.Component.4.7.TargetingPack | .NET Framework 4.7 | 15.6.27406.0 | Volitelné
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | .NET Framework 4.6.2 | 15.6.27406.0 | Volitelné
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | .NET Framework 4.7.1 | 15.6.27406.0 | Volitelné
Microsoft.Net.ComponentGroup.4.7.2.DeveloperTools | .NET Framework 4.7.2 – vývojové nástroje | 15.8.27825.0 | Volitelné
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | .NET Framework 4.7 – vývojové nástroje | 15.6.27406.0 | Volitelné
Microsoft.Net.Core.Component.SDK | Vývojové nástroje .NET Core 2.0 | 15.6.27406.0 | Volitelné
Microsoft.Net.Core.Component.SDK.1x | .NET Core 1.0 – vývojové nástroje verze 1.1 | 15.6.27406.0 | Volitelné
Microsoft.NetCore.1x.ComponentGroup.Web | .NET Core 1.0 – 1.1 – vývojové nástroje pro web | 15.6.27406.0 | Volitelné
Microsoft.NetCore.ComponentGroup.DevelopmentTools | Vývojové nástroje .NET Core 2,0 | 15.8.27729.1 | Volitelné
Microsoft. NetCore. Component. Web | Vývojové nástroje .NET Core 2,0 | 15.7.27625.0 | Volitelné
Microsoft. VisualStudio. Component. CodeClone | Klon kódu | 15.0.26208.0 | Volitelné
Microsoft. VisualStudio. Component. CodeMap | Mapa kódu | 15.0.26208.0 | Volitelné
Microsoft. VisualStudio. Component. DependencyValidation. Enterprise | Ověřování závislostí v reálném čase | 15.0.26208.0 | Volitelné
Microsoft. VisualStudio. Component. GraphDocument | Editor DGML | 15.0.27005.2 | Volitelné
Microsoft. VisualStudio. Component. TestTools. WebLoadTest | Nástroje pro testování výkonu webu a zátěžové testování | 15.8.27729.1 | Volitelné
Microsoft. VisualStudio. Component. ArchitectureTools. Managed | Nástroje pro architekturu a analýzy | 15.0.26208.0 | Volitelné
Microsoft. VisualStudio. Component. IISDevelopment | Podpora služby IIS pro dobu vývoje | 15.9.28219.51 | Volitelné
Microsoft.VisualStudio.Web.Mvc4.ComponentGroup | ASP.NET MVC 4 | 15.6.27406.0 | Volitelné

## <a name="nodejs-development"></a>Node.js vývoje

**ID:** Microsoft.VisualStudio.Workload.Node

**Popis:** Sestavovat škálovatelné síťové aplikace pomocí Node.js, asynchronního modulu runtime JavaScriptu řízeného událostmi. 

### <a name="components-included-by-this-workload"></a>Komponenty zahrnuté v této úlohu

ID komponenty | Name | Verze | Typ závislosti
--- | --- | --- | ---
Component.WebSocket | WebSocket4Net | 15.0.26606.0 | Vyžadováno
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostika JavaScriptu | 15.8.27729.1 | Vyžadováno
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Podpora jazyků JavaScript a TypeScript | 15.9.28125.51 | Vyžadováno
Microsoft.VisualStudio.Component.Node.Build | Node.js podpory nástroje MSBuild | 15.8.27825.0 | Vyžadováno
Microsoft.VisualStudio.Component.Node.Tools | Node.js podpory vývoje | 15.8.27825.0 | Vyžadováno
Microsoft. VisualStudio. Component. NuGet | Správce balíčků NuGet | 15.9.28016.0 | Vyžadováno
Microsoft. VisualStudio. Component. TestTools. Core | Základní funkce testovacích nástrojů | 15.7.27520.0 | Vyžadováno
Microsoft. VisualStudio. Component. TypeScript. 3.1 | Sada TypeScript 3,1 SDK | 15.0.28218.60 | Vyžadováno
Microsoft. VisualStudio. Component. WebToolsExtensions | Vývoj pro ASP.NET a web | 15.8.27825.0 | Vyžadováno
Microsoft. VisualStudio. Component. WebDeploy | Web Deploy | 15.8.27729.1 | Doporučeno
Microsoft. VisualStudio. Component. AppInsights. Tools | Vývojářské analytické nástroje | 15.8.27825.0 | Volitelné
Microsoft. VisualStudio. Component. Common. Azure. Tools | Nástroje pro připojení a publikování | 15.9.28107.0 | Volitelné
Microsoft. VisualStudio. Component. static. Analysis. Tools | Nástroje statické analýzy | 15.0.26208.0 | Volitelné
Microsoft. VisualStudio. Component. VC. CoreIde | Visual Studio C++ – základní funkce | 15.6.27406.0 | Volitelné
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | Nástroje VC++ 2017 verze 15.9 v14.16 nejnovější verze 141 | 15.9.28230.55 | Volitelné

## <a name="officesharepoint-development"></a>Vývoj pro Office/SharePoint

**ID:** Microsoft.VisualStudio.Workload.Office

**Popis:** Vytvářejte doplňky pro Office a SharePoint, řešení pro SharePoint a doplňky VSTO pomocí jazyků C#, VB a JavaScript.

### <a name="components-included-by-this-workload"></a>Komponenty zahrnuté v této úlohu

ID komponenty | Name | Verze | Typ závislosti
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Služby jazyka Razor | 15.0.26720.2 | Vyžadováno
Component.Microsoft.Web.LibraryManager | Správce knihovny | 15.8.27705.0 | Vyžadováno
Component.WebSocket | WebSocket4Net | 15.0.26606.0 | Vyžadováno
Microsoft.Component.ClickOnce | Publikování ClickOnce | 15.8.27825.0 | Vyžadováno
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | Vyžadováno
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 | 15.6.27406.0 | Vyžadováno
Microsoft.Net. Component. 4.5. TargetingPack | Sada targeting pack .NET Framework 4,5 | 15.6.27406.0 | Vyžadováno
Microsoft. NET. Component. 4.6.1. SDK | .NET Framework 4.6.1 SDK | 15.6.27406.0 | Vyžadováno
Microsoft.Net. Component. 4.6.1. TargetingPack | .NET Framework 4.6.1 targeting pack | 15.6.27406.0 | Vyžadováno
Microsoft.Net. Component. 4. TargetingPack | Sada targeting pack .NET Framework 4 | 15.6.27406.0 | Vyžadováno
Microsoft.Net. Component. DevelopmentPrerequisites | Vývojové nástroje .NET Framework 4.6.1 | 15.8.27825.0 | Vyžadováno
Microsoft. NET. Core. Component. SDK. 2.1 | Vývojové nástroje .NET Core 2,1 | 15.8.27924.0 | Vyžadováno
Microsoft. VisualStudio. Component. AppInsights. Tools | Vývojářské analytické nástroje | 15.8.27825.0 | Vyžadováno
Microsoft. VisualStudio. Component. Common. Azure. Tools | Nástroje pro připojení a publikování | 15.9.28107.0 | Vyžadováno
Microsoft.VisualStudio.Component.DockerTools | Kontejnerové vývojové nástroje | 15.8.27906.1 | Vyžadováno
Microsoft.VisualStudio.Component.DockerTools. BuildTools | Nástroje pro vývoj kontejnerů – nástroje sestavení | 15.7.27617.1 | Vyžadováno
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 15.0.26208.0 | Vyžadováno
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostika JavaScriptu | 15.8.27729.1 | Vyžadováno
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Podpora jazyků JavaScript a TypeScript | 15.9.28125.51 | Vyžadováno
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Managed Desktop Workload Core | 15.8.27729.1 | Vyžadováno
Microsoft.VisualStudio.Component.ManagedDesktop.Prerequisites | Nástroje pro vývoj desktopových aplikací .NET | 15.7.27625.0 | Vyžadováno
Microsoft.VisualStudio.Component.NuGet | Správce balíčků NuGet | 15.9.28016.0 | Vyžadováno
Microsoft.VisualStudio.Component.PortableLibrary | Balíček cílení na přenosnou knihovnu .NET | 15.6.27309.0 | Vyžadováno
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilátory C# a Visual Basic Roslyn | 15.6.27309.0 | Vyžadováno
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# a Visual Basic | 15.8.27729.1 | Vyžadováno
Microsoft. VisualStudio. Component. SharePoint. Tools | Office Developer Tools for Visual Studio | 15.8.27924.0 | Vyžadováno
Microsoft. VisualStudio. Component. SQL. ADAL | Modul runtime SQL ADAL | 15.6.27406.0 | Vyžadováno
Microsoft. VisualStudio. Component. SQL. CLR | Datové typy CLR pro SQL Server | 15.0.26208.0 | Vyžadováno
Microsoft. VisualStudio. Component. SQL. CMDUtils | SQL Server nástroje příkazového řádku | 15.0.26208.0 | Vyžadováno
Microsoft. VisualStudio. Component. SQL. DataSources | Zdroje dat pro podporu SQL Server | 15.0.26621.2 | Vyžadováno
Microsoft. VisualStudio. Component. SQL. LocalDB. Runtime | SQL Server Express 2016 LocalDB | 15.7.27617.1 | Vyžadováno
Microsoft. VisualStudio. Component. SQL. NCLI | Nativní klient systému SQL Server | 15.0.26208.0 | Vyžadováno
Microsoft. VisualStudio. Component. SQL. SSDT | SQL Server Data Tools | 15.9.28107.0 | Vyžadováno
Microsoft. VisualStudio. Component. static. Analysis. Tools | Nástroje statické analýzy | 15.0.26208.0 | Vyžadováno
Microsoft.VisualStudio.Component.TextTemplating | Transformace textových šablon | 15.0.26208.0 | Vyžadováno
Microsoft.VisualStudio.Component.TypeScript.3.1 | TypeScript 3.1 SDK | 15.0.28218.60 | Vyžadováno
Microsoft.VisualStudio.Component.VisualStudioData | Zdroje dat a odkazy na služby | 15.6.27406.0 | Vyžadováno
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | 15.8.27924.0 | Vyžadováno
Microsoft.VisualStudio.Component.Web | ASP.NET a webové vývojové nástroje | 15.8.27825.0 | Vyžadováno
Microsoft.VisualStudio.Component.Workflow | Windows Workflow Foundation | 15.8.27825.0 | Vyžadováno
Microsoft.VisualStudio.ComponentGroup.Web | Požadavky ASP.NET a webových vývojových nástrojů | 15.9.28219.51 | Vyžadováno
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Vývoj pro ASP.NET a web | 15.8.27825.0 | Vyžadováno
Microsoft.VisualStudio.Component.TeamOffice | Visual Studio Tools for Office (VSTO) | 15.7.27625.0 | Doporučeno
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 15.8.27729.1 | Doporučeno
Microsoft.Net.Component.4.6.2.SDK | Sada .NET Framework 4.6.2 SDK | 15.6.27406.0 | Volitelné
Microsoft.Net. Component. 4.6.2. TargetingPack | Sada targeting pack .NET Framework 4.6.2 | 15.6.27406.0 | Volitelné
Microsoft. NET. Component. 4.7.1. SDK | Sada .NET Framework 4.7.1 SDK | 15.6.27406.0 | Volitelné
Microsoft.Net. Component. 4.7.1. TargetingPack | Sada targeting pack .NET Framework 4.7.1 | 15.6.27406.0 | Volitelné
Microsoft. NET. Component. 4.7.2. SDK | Sada .NET Framework 4.7.2 SDK | 15.8.27825.0 | Volitelné
Microsoft.Net. Component. 4.7.2. TargetingPack | Sada targeting pack .NET Framework 4.7.2 | 15.8.27825.0 | Volitelné
Microsoft. NET. Component. 4.7. SDK | .NET Framework 4,7 SDK | 15.6.27406.0 | Volitelné
Microsoft.Net. Component. 4.7. TargetingPack | Sada targeting pack .NET Framework 4,7 | 15.6.27406.0 | Volitelné
Microsoft.Net. Component. 4.6.2. DeveloperTools | Vývojové nástroje .NET Framework 4.6.2 | 15.6.27406.0 | Volitelné
Microsoft.Net. Component. 4.7.1. DeveloperTools | Vývojové nástroje .NET Framework 4.7.1 | 15.6.27406.0 | Volitelné
Microsoft.Net. Component. 4.7.2. DeveloperTools | .NET Framework 4.7.2 – vývojové nástroje | 15.8.27825.0 | Volitelné
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | .NET Framework 4.7 – vývojové nástroje | 15.6.27406.0 | Volitelné
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | 15.8.27729.1 | Volitelné

## <a name="python-development"></a>Vývoj v Pythonu

**ID:** Microsoft.VisualStudio.Workload.Python

**Popis:** Úpravy, ladění, interaktivní vývoj a řízení zdrojového kódu pro Python.

### <a name="components-included-by-this-workload"></a>Komponenty zahrnuté v této úlohu

ID komponenty | Name | Verze | Typ závislosti
--- | --- | --- | ---
Microsoft.Component.PythonTools | Podpora jazyka Python | 15.0.26823.1 | Vyžadováno
Component.CPython3.x64 | Python 3 (64bitová verze) (3.6.6) | 3.6.6 | Doporučeno
Microsoft.Component.CookiecutterTools | Podpora šablon Cookiecutter | 15.0.26621.2 | Doporučeno
Microsoft.Component.PythonTools.Web | Webová podpora Pythonu | 15.9.28107.0 | Doporučeno
Microsoft. VisualStudio. Component. Common. Azure. Tools | Nástroje pro připojení a publikování | 15.9.28107.0 | Doporučeno
Microsoft. VisualStudio. Component. JavaScript. TypeScript | Podpora jazyků JavaScript a TypeScript | 15.9.28125.51 | Doporučeno
Microsoft. VisualStudio. Component. SQL. CLR | Datové typy CLR pro SQL Server | 15.0.26208.0 | Doporučeno
Microsoft. VisualStudio. Component. TypeScript. 3.1 | Sada TypeScript 3,1 SDK | 15.0.28218.60 | Doporučeno
Microsoft. VisualStudio. Component. VisualStudioData | Zdroje dat a odkazy na služby | 15.6.27406.0 | Doporučeno
Microsoft. VisualStudio. Component. WebDeploy | Web Deploy | 15.8.27729.1 | Doporučeno
Microsoft. VisualStudio. Component. WebToolsExtensions | Vývoj pro ASP.NET a web | 15.8.27825.0 | Doporučeno
Component. Anaconda2. x64 | Anaconda2 64 – bit (5.2.0) | 5.2.0 | Volitelné
Component. Anaconda2. x86 | Anaconda2 32 – bit (5.2.0) | 5.2.0 | Volitelné
Component.Anaconda3.x64 | Anaconda3 (64bitová verze) (5.2.0) | 5.2.0 | Volitelné
Component.Anaconda3.x86 | Anaconda3 (32bitová verze) (5.2.0) | 5.2.0 | Volitelné
Component.CPython2.x64 | Python 2 – 64 bitů (2.7.14) | 2.7.14 | Volitelné
Component.CPython2.x86 | Python 2 – 32 bitů (2.7.14) | 2.7.14 | Volitelné
Component.CPython3.x86 | Python 3 (32bitová verze) (3.6.6) | 3.6.6 | Volitelné
Component.Microsoft.VisualStudio.RazorExtension | Služby jazyka Razor | 15.0.26720.2 | Volitelné
Component.Microsoft.Web.LibraryManager | Správce knihovny | 15.8.27705.0 | Volitelné
Component.WebSocket | WebSocket4Net | 15.0.26606.0 | Volitelné
Microsoft.Component.ClickOnce | Publikování ClickOnce | 15.8.27825.0 | Volitelné
Microsoft. Component. MSBuild | MSBuild | 15.7.27520.0 | Volitelné
Microsoft. Component. NetFX. Native | .NET Native | 15.0.26208.0 | Volitelné
Microsoft. Component. PythonTools. UWP | Podpora IoT v Pythonu | 15.0.26606.0 | Volitelné
Microsoft. Component. VC. Runtime. UCRTSDK | Sada Windows Universal CRT SDK | 15.6.27309.0 | Volitelné
Microsoft. Component. PythonTools. NativeDevelopment | Nástroje pro nativní vývoj v Pythonu | 15.9.28307.102 | Volitelné
Microsoft.Net. Component. 4.5.2. TargetingPack | Sada .NET Framework 4.5.2 targeting pack | 15.6.27406.0 | Volitelné
Microsoft.Net. Component. 4.5. TargetingPack | Sada targeting pack .NET Framework 4,5 | 15.6.27406.0 | Volitelné
Microsoft. NET. Component. 4.6.1. SDK | .NET Framework 4.6.1 SDK | 15.6.27406.0 | Volitelné
Microsoft.Net. Component. 4.6.1. TargetingPack | .NET Framework 4.6.1 targeting pack | 15.6.27406.0 | Volitelné
Microsoft.Net. Component. DevelopmentPrerequisites | .NET Framework 4.6.1 | 15.8.27825.0 | Volitelné
Microsoft.Net.Core.Component.SDK.2.1 | Vývojové nástroje .NET Core 2.1 | 15.8.27924.0 | Volitelné
Microsoft.VisualStudio.Component.AppInsights.Tools | Vývojářské analytické nástroje | 15.8.27825.0 | Volitelné
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Nástroje pro vytváření v Azure | 15.9.28307.421 | Volitelné
Microsoft.VisualStudio.Component.Azure.ClientLibs | Knihovny Azure pro .NET | 15.0.26208.0 | Volitelné
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Azure Compute emulátoru | 15.9.28307.421 | Volitelné
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Emulátor úložiště Azure | 15.9.28125.51 | Volitelné
Microsoft.VisualStudio.Component.Azure.Waverton | Azure Cloud Services core tools | 15.9.28107.0 | Volitelné
Microsoft.VisualStudio.Component.Azure.Waverton.BuildTools | Nástroje pro vytváření Cloud Services pro Azure | 15.7.27617.1 | Volitelné
Microsoft. VisualStudio. Component. ClassDesigner | Návrhář tříd | 15.0.26208.0 | Volitelné
Microsoft. VisualStudio. Component. CodeClone | Klon kódu | 15.0.26208.0 | Volitelné
Microsoft. VisualStudio. Component. CodeMap | Mapa kódu | 15.0.26208.0 | Volitelné
Microsoft. VisualStudio. Component. DiagnosticTools | Nástroje pro profilaci .NET | 15.8.27729.1 | Volitelné
Microsoft.VisualStudio.Component.DockerTools | Kontejnerové vývojové nástroje | 15.8.27906.1 | Volitelné
Microsoft.VisualStudio.Component.DockerTools. BuildTools | Nástroje pro vývoj kontejnerů – nástroje sestavení | 15.7.27617.1 | Volitelné
Microsoft. VisualStudio. Component. GraphDocument | Editor DGML | 15.0.27005.2 | Volitelné
Microsoft. VisualStudio. Component. Graphics | Editory obrázků a 3D model | 15.6.27406.0 | Volitelné
Microsoft. VisualStudio. Component. Graphics. Tools | Ladicí program grafiky a Profiler GPU pro DirectX | 15.6.27406.0 | Volitelné
Microsoft.VisualStudio.Component.Graphics.Win81 | Graphics Tools Windows 8.1 SDK | 15.6.27406.0 | Volitelné
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 15.0.26208.0 | Volitelné
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | 15.8.27729.1 | Volitelné
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostika JavaScriptu | 15.8.27729.1 | Volitelné
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Managed Desktop Workload Core | 15.8.27729.1 | Volitelné
Microsoft.VisualStudio.Component.NuGet | Správce balíčků NuGet | 15.9.28016.0 | Volitelné
Microsoft.VisualStudio.Component.PortableLibrary | Balíček cílení na přenosnou knihovnu .NET | 15.6.27309.0 | Volitelné
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilátory C# a Visual Basic Roslyn | 15.6.27309.0 | Volitelné
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# a Visual Basic | 15.8.27729.1 | Volitelné
Microsoft.VisualStudio.Component.SQL.ADAL | Modul runtime SQL ADAL | 15.6.27406.0 | Volitelné
Microsoft. VisualStudio. Component. SQL. CMDUtils | SQL Server nástroje příkazového řádku | 15.0.26208.0 | Volitelné
Microsoft. VisualStudio. Component. SQL. DataSources | Zdroje dat pro podporu SQL Server | 15.0.26621.2 | Volitelné
Microsoft. VisualStudio. Component. SQL. LocalDB. Runtime | SQL Server Express 2016 LocalDB | 15.7.27617.1 | Volitelné
Microsoft. VisualStudio. Component. SQL. NCLI | Nativní klient systému SQL Server | 15.0.26208.0 | Volitelné
Microsoft. VisualStudio. Component. SQL. SSDT | SQL Server Data Tools | 15.9.28107.0 | Volitelné
Microsoft. VisualStudio. Component. static. Analysis. Tools | Nástroje statické analýzy | 15.0.26208.0 | Volitelné
Microsoft. VisualStudio. Component. TextTemplating | Transformace textové šablony | 15.0.26208.0 | Volitelné
Microsoft. VisualStudio. Component. VC. 140 | Sada nástrojů VC + + 2015,3 v 14.00 (v140) pro Desktop | 15.7.27617.1 | Volitelné
Microsoft. VisualStudio. Component. VC. CoreIde | Visual Studio základních funkcí C++ | 15.6.27406.0 | Volitelné
Microsoft.VisualStudio.Component.VC.DiagnosticTools | Nástroje pro profilaci jazyka C++ | 15.0.26823.1 | Volitelné
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | Nástroje VC++ 2017 verze 15.9 v14.16 nejnovější verze 141 | 15.9.28230.55 | Volitelné
Microsoft.VisualStudio.Component.Web | ASP.NET a webové vývojové nástroje | 15.8.27825.0 | Volitelné
Microsoft.VisualStudio.Component.Windows10SDK | Windows Universal C Runtime | 15.6.27406.0 | Volitelné
Microsoft.VisualStudio.Component.Windows10SDK.10586 | Windows 10 SDK (10.0.10586.0) | 15.6.27406.0 | Volitelné
Microsoft.VisualStudio.Component.Windows10SDK.17763 | Windows 10 SDK (10.0.17763.0) | 15.9.28307.102 | Volitelné
Microsoft.VisualStudio.Component.Windows81SDK | Windows 8.1 SDK | 15.6.27406.0 | Volitelné
Microsoft.VisualStudio.ComponentGroup.Web | Požadavky ASP.NET a webových vývojových nástrojů | 15.9.28219.51 | Volitelné

## <a name="universal-windows-platform-development"></a>Univerzální platforma Windows vývoje

**ID:** Microsoft. VisualStudio. úlohu. Universal

**Popis:** Vytvářejte aplikace pro Univerzální platforma Windows pomocí C#, VB, JavaScriptu nebo volitelně C++.

### <a name="components-included-by-this-workload"></a>Součásti zahrnuté v tomto zatížení

ID součásti | Name | Verze | Typ závislosti
--- | --- | --- | ---
Komponenta. WebSocket | WebSocket4Net | 15.0.26606.0 | Vyžadováno
Microsoft. Component. ClickOnce | Publikování ClickOnce | 15.8.27825.0 | Vyžadováno
Microsoft. Component. NetFX. Native | .NET Native | 15.0.26208.0 | Vyžadováno
Microsoft. Components. Blend | Blend for Visual Studio | 15.6.27406.0 | Vyžadováno
Microsoft.Net. Component. 4.5. TargetingPack | Sada targeting pack .NET Framework 4,5 | 15.6.27406.0 | Vyžadováno
Microsoft. NET. Component. 4.6.1. SDK | .NET Framework 4.6.1 SDK | 15.6.27406.0 | Vyžadováno
Microsoft. NET. Core. Component. SDK. 2.1 | Vývojové nástroje .NET Core 2,1 | 15.8.27924.0 | Vyžadováno
Microsoft. VisualStudio. Component. AppInsights. Tools | Vývojářské analytické nástroje | 15.8.27825.0 | Vyžadováno
Microsoft.VisualStudio.Component.DiagnosticTools | Nástroje pro profilaci .NET | 15.8.27729.1 | Vyžadováno
Microsoft.VisualStudio.Component.Graphics | Editory obrázků a 3D model souborů | 15.6.27406.0 | Vyžadováno
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostika JavaScriptu | 15.8.27729.1 | Vyžadováno
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Podpora jazyků JavaScript a TypeScript | 15.9.28125.51 | Vyžadováno
Microsoft.VisualStudio.Component.NuGet | Správce balíčků NuGet | 15.9.28016.0 | Vyžadováno
Microsoft.VisualStudio.Component.PortableLibrary | Balíček cílení na přenosnou knihovnu .NET | 15.6.27309.0 | Vyžadováno
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilátory C# a Visual Basic Roslyn | 15.6.27309.0 | Vyžadováno
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# a Visual Basic | 15.8.27729.1 | Vyžadováno
Microsoft.VisualStudio.Component.SQL.CLR | Datové typy CLR pro SQL Server | 15.0.26208.0 | Vyžadováno
Microsoft. VisualStudio. Component. static. Analysis. Tools | Nástroje statické analýzy | 15.0.26208.0 | Vyžadováno
Microsoft. VisualStudio. Component. TypeScript. 3.1 | Sada TypeScript 3,1 SDK | 15.0.28218.60 | Vyžadováno
Microsoft. VisualStudio. Component. UWP. support | Nástroje Univerzální platforma Windows | 15.9.28119.51 | Vyžadováno
Microsoft. VisualStudio. Component. VisualStudioData | Zdroje dat a odkazy na služby | 15.6.27406.0 | Vyžadováno
Microsoft. VisualStudio. Component. Windows10SDK. 17763 | Windows 10 SDK (10.0.17763.0) | 15.9.28307.102 | Vyžadováno
Microsoft. VisualStudio. Component. UWP. Cordova | Univerzální platforma Windows Tools pro Cordova | 15.9.28307.102 | Vyžadováno
Microsoft. VisualStudio. Component. UWP. NetCoreAndStandard | .NET Native a .NET Standard | 15.8.27906.1 | Vyžadováno
Microsoft. VisualStudio. Component. UWP. Xamarin | Univerzální platforma Windows nástroje pro Xamarin | 15.9.28307.102 | Vyžadováno
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Vývoj pro ASP.NET a web | 15.8.27825.0 | Vyžadováno
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | 15.8.27729.1 | Doporučeno
Microsoft.Component.VC.Runtime.OSSupport | Visual C++ runtime pro UPW | 15.6.27406.0 | Volitelné
Microsoft.Net.Component.4.7.2.SDK | .NET Framework 4.7.2 SDK | 15.8.27825.0 | Volitelné
Microsoft.VisualStudio.Component.CodeClone | Klonování kódu | 15.0.26208.0 | Volitelné
Microsoft.VisualStudio.Component.CodeMap | Mapa kódu | 15.0.26208.0 | Volitelné
Microsoft.VisualStudio.Component.DependencyValidation.Enterprise | Živé ověřování závislostí | 15.0.26208.0 | Volitelné
Microsoft.VisualStudio.Component.GraphDocument | Editor DGML | 15.0.27005.2 | Volitelné
Microsoft.VisualStudio.Component.Graphics.Tools | Ladicí program grafiky a Profiler GPU pro DirectX | 15.6.27406.0 | Volitelné
Microsoft. VisualStudio. Component. Graphics. Win81 | Sada nástrojů Graphics Windows 8.1 SDK | 15.6.27406.0 | Volitelné
Microsoft. VisualStudio. Component. telefon. emulátor. 15254 | Emulátor systému Windows 10 Mobile (aktualizace Creators Update) | 15.0.27406.0 | Volitelné
Microsoft. VisualStudio. Component. SQL. LocalDB. Runtime | SQL Server Express 2016 LocalDB | 15.7.27617.1 | Volitelné
Microsoft. VisualStudio. Component. SQL. NCLI | Nativní klient systému SQL Server | 15.0.26208.0 | Volitelné
Microsoft. VisualStudio. Component. UWP. VC. ARM64 | Nástroje C++ Univerzální platforma Windows pro ARM64 | 15.0.28125.51 | Volitelné
Microsoft. VisualStudio. Component. VC. CoreIde | Visual Studio C++ – základní funkce | 15.6.27406.0 | Volitelné
Microsoft. VisualStudio. Component. VC. Tools. ARM | Visual C++ kompilátorů a knihoven pro ARM | 15.8.27825.0 | Volitelné
Microsoft. VisualStudio. Component. VC. Tools. ARM64 | Visual C++ kompilátorů a knihoven pro ARM64 | 15.9.28230.55 | Volitelné
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | Nástroje VC++ 2017 verze 15.9 v14.16 nejnovější verze 141 | 15.9.28230.55 | Volitelné
Microsoft.VisualStudio.Component.Windows10SDK.10240 | Windows 10 SDK (10.0.10240.0) | 15.6.27406.0 | Volitelné
Microsoft.VisualStudio.Component.Windows10SDK.10586 | Windows 10 SDK (10.0.10586.0) | 15.6.27406.0 | Volitelné
Microsoft.VisualStudio.Component.Windows10SDK.14393 | Windows 10 SDK (10.0.14393.0) | 15.6.27406.0 | Volitelné
Microsoft.VisualStudio.Component.Windows10SDK.15063.Desktop | Windows 10 SDK (10.0.15063.0) pro Desktop C++ [x86 a x64] | 15.6.27406.0 | Volitelné
Microsoft.VisualStudio.Component.Windows10SDK.15063.UPW | Windows 10 SDK (10.0.15063.0) pro UPW: C#, VB, JS | 15.6.27406.0 | Volitelné
Microsoft.VisualStudio.Component.Windows10SDK.15063.UPW.Native | Windows 10 SDK (10.0.15063.0) pro UPW: C++ | 15.6.27406.0 | Volitelné
Microsoft.VisualStudio.Component.Windows10SDK.16299.Desktop | Windows 10 SDK (10.0.16299.0) pro Desktop C++ [x86 a x64] | 15.6.27406.0 | Volitelné
Microsoft.VisualStudio.Component.Windows10SDK.16299.Desktop.arm | Windows 10 SDK (10.0.16299.0) pro Desktop C++ [ARM a ARM64] | 15.6.27406.0 | Volitelné
Microsoft.VisualStudio.Component.Windows10SDK.16299.UPW | Windows 10 SDK (10.0.16299.0) pro UWP: C#, VB, JS | 15.6.27406.0 | Volitelné
Microsoft. VisualStudio. Component. Windows10SDK. 16299. UWP. Native | Windows 10 SDK (10.0.16299.0) pro UWP: C++ | 15.6.27406.0 | Volitelné
Microsoft. VisualStudio. Component. Windows10SDK. 17134 | Windows 10 SDK (10.0.17134.0) | 15.9.28307.102 | Volitelné
Microsoft. VisualStudio. Component. Windows10SDK. IpOverUsb | Připojení zařízení USB | 15.9.28307.102 | Volitelné
Microsoft. VisualStudio. Component. ArchitectureTools. Managed | Nástroje pro architekturu a analýzy | 15.0.26208.0 | Volitelné
Microsoft.VisualStudio.ComponentGroup.UWP.VC | Nástroje C++ Univerzální platforma Windows | 15.9.28307.102 | Volitelné
Microsoft. VisualStudio. Component. Windows10SDK. 15063 | Windows 10 SDK (10.0.15063.0) | 15.8.27825.0 | Volitelné
Microsoft. VisualStudio. Component. Windows10SDK. 16299 | Windows 10 SDK (10.0.16299.0) | 15.8.27825.0 | Volitelné

## <a name="visual-studio-extension-development"></a>Vývoj rozšíření sady Visual Studio

**ID:** Microsoft. VisualStudio. úlohy. VisualStudioExtension

**Popis:** Vytvářejte doplňky a rozšíření pro Visual Studio, včetně nových příkazů, analyzátorů kódu a oken nástrojů.

### <a name="components-included-by-this-workload"></a>Komponenty zahrnuté v této úlohu

ID komponenty | Name | Verze | Typ závislosti
--- | --- | --- | ---
Microsoft.Component.ClickOnce | Publikování ClickOnce | 15.8.27825.0 | Vyžadováno
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | Vyžadováno
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 15.6.27406.0 | Vyžadováno
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 | 15.6.27406.0 | Vyžadováno
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework 4.6 | 15.6.27406.0 | Vyžadováno
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | .NET Framework 4.6.1 | 15.8.27825.0 | Vyžadováno
Microsoft.VisualStudio.Component.NuGet | Správce balíčků NuGet | 15.9.28016.0 | Vyžadováno
Microsoft.VisualStudio.Component.PortableLibrary | Balíček cílení na přenosnou knihovnu .NET | 15.6.27309.0 | Vyžadováno
Microsoft. VisualStudio. Component. Roslyn. Compiler | Kompilátory C# a Visual Basic Roslyn | 15.6.27309.0 | Vyžadováno
Microsoft. VisualStudio. Component. Roslyn. LanguageServices | C# a Visual Basic | 15.8.27729.1 | Vyžadováno
Microsoft. VisualStudio. Component. static. Analysis. Tools | Nástroje statické analýzy | 15.0.26208.0 | Vyžadováno
Microsoft. VisualStudio. Component. VSSDK | Visual Studio SDK | 15.8.27729.1 | Vyžadováno
Microsoft. VisualStudio. Component. VisualStudioExtension. požadavky | Předpoklady pro vývoj rozšíření sady Visual Studio | 15.7.27625.0 | Vyžadováno
Microsoft. VisualStudio. Component. DiagnosticTools | Nástroje pro profilaci .NET | 15.8.27729.1 | Doporučeno
Microsoft. VisualStudio. Component. IntelliTrace. front-end | IntelliTrace | 15.8.27729.1 | Doporučeno
Microsoft. VisualStudio. Component. TextTemplating | Transformace textové šablony | 15.0.26208.0 | Doporučeno
Component. Dotfuscator | PreEmptive Protection – Dotfuscator | 15.0.26208.0 | Volitelné
Microsoft. Component. CodeAnalysis. SDK | Sada .NET Compiler Platform SDK | 15.0.27729.1 | Volitelné
Microsoft. Component. VC. Runtime. OSSupport | Visual C++ runtime pro UPW | 15.6.27406.0 | Volitelné
Microsoft.VisualStudio.Component.AppInsights.Tools | Vývojářské analytické nástroje | 15.8.27825.0 | Volitelné
Microsoft.VisualStudio.Component.ClassDesigner | Návrhář tříd | 15.0.26208.0 | Volitelné
Microsoft.VisualStudio.Component.CodeClone | Klonování kódu | 15.0.26208.0 | Volitelné
Microsoft.VisualStudio.Component.CodeMap | Mapa kódu | 15.0.26208.0 | Volitelné
Microsoft.VisualStudio.Component.DependencyValidation.Enterprise | Živé ověřování závislostí | 15.0.26208.0 | Volitelné
Microsoft.VisualStudio.Component.DslTools | Modeling SDK | 15.0.27005.2 | Volitelné
Microsoft.VisualStudio.Component.GraphDocument | Editor DGML | 15.0.27005.2 | Volitelné
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 15.7.27617.1 | Volitelné
Microsoft. VisualStudio. Component. SQL. NCLI | Nativní klient systému SQL Server | 15.0.26208.0 | Volitelné
Microsoft. VisualStudio. Component. VC. ATL | Visual C++ ATL pro x86 a x64 | 15.7.27625.0 | Volitelné
Microsoft. VisualStudio. Component. VC. ATLMFC | Visual C++ MFC pro x86 a x64 | 15.7.27625.0 | Volitelné
Microsoft. VisualStudio. Component. VC. CoreIde | Visual Studio C++ – základní funkce | 15.6.27406.0 | Volitelné
Microsoft. VisualStudio. Component. VC. Tools. x86. x64 | VC + + 2017 verze 15,9 v 14.16 nejnovější nástroje v141 | 15.9.28230.55 | Volitelné
Microsoft. VisualStudio. Component. ArchitectureTools. Managed | Nástroje pro architekturu a analýzy | 15.0.26208.0 | Volitelné

## <a name="mobile-development-with-javascript"></a>Vývoj mobilních aplikací v jazyce JavaScript

**ID:** Microsoft. VisualStudio. úlohy. WebCrossPlat

**Popis:** Vytvářejte aplikace pro Android, iOS a UWP pomocí Nástroje pro Apache Cordova.

### <a name="components-included-by-this-workload"></a>Součásti zahrnuté v tomto zatížení

ID součásti | Name | Verze | Typ závislosti
--- | --- | --- | ---
Component.CordovaToolset.6.3.1 | Sada nástrojů Cordova 6.3.1 | 15.7.27625.0 | Vyžadováno
Component.WebSocket | WebSocket4Net | 15.0.26606.0 | Vyžadováno
Microsoft.VisualStudio.Component.Cordova | Vývoj mobilních aplikací pomocí základních funkcí JavaScriptu | 15.0.26606.0 | Vyžadováno
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostika JavaScriptu | 15.8.27729.1 | Vyžadováno
Microsoft.VisualStudio.Component.JavaScript.ProjectSystem | JavaScript ProjectSystem a sdílené nástroje | 15.0.26606.0 | Vyžadováno
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Podpora jazyků JavaScript a TypeScript | 15.9.28125.51 | Vyžadováno
Microsoft.VisualStudio.Component.TypeScript.2.3 | TypeScript 2.3 SDK | 15.8.27729.1 | Vyžadováno
Microsoft.VisualStudio.Component.TypeScript.3.1 | TypeScript 3.1 SDK | 15.0.28218.60 | Vyžadováno
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Vývoj pro ASP.NET a web | 15.8.27825.0 | Vyžadováno
Component.Android.SDK23.Private | Instalace Android SDK (úroveň rozhraní API 23) (místní instalace pro vývoj pro mobilní zařízení pomocí JavaScriptu nebo C++) | 15.9.28016.0 | Volitelné
Component. Google. Android. emulátor. API23. Private | Google Android Emulator (úroveň rozhraní API 23) (místní instalace) | 15.6.27413.0 | Volitelné
Component. modul HAXM. Private | Intel Hardware Accelerated Execution Manager (modul HAXM) (místní instalace) | 15.9.28307.421 | Volitelné
Component. OpenJDK | Distribuční OpenJDK Microsoftu | 15.9.28125.51 | Volitelné
Microsoft. Component. ClickOnce | Publikování ClickOnce | 15.8.27825.0 | Volitelné
Microsoft. Component. NetFX. Native | .NET Native | 15.0.26208.0 | Volitelné
Microsoft. VisualStudio. Component. AppInsights. Tools | Vývojářské analytické nástroje | 15.8.27825.0 | Volitelné
Microsoft. VisualStudio. Component. DiagnosticTools | Nástroje pro profilaci .NET | 15.8.27729.1 | Volitelné
Microsoft. VisualStudio. Component. Git | Git pro Windows | 15.0.26208.0 | Volitelné
Microsoft.VisualStudio.Component.Graphics | Editory obrázků a 3D model souborů | 15.6.27406.0 | Volitelné
Microsoft.VisualStudio.Component.Phone.Emulator.15254 | Windows 10 Mobile emulátoru (Fall Creators Update) | 15.0.27406.0 | Volitelné
Microsoft.VisualStudio.Component.SQL.CLR | Datové typy CLR pro SQL Server | 15.0.26208.0 | Volitelné
Microsoft.VisualStudio.Component.VisualStudioData | Zdroje dat a odkazy na služby | 15.6.27406.0 | Volitelné
Microsoft.VisualStudio.Component.Windows10SDK.17763 | Windows 10 SDK (10.0.17763.0) | 15.9.28307.102 | Volitelné
Microsoft.VisualStudio.ComponentGroup.UWP.Cordova | Univerzální platforma Windows nástroje pro Cordovu | 15.9.28307.102 | Volitelné

## <a name="unaffiliated-components"></a>Nepřiřazené komponenty

Jedná se o komponenty, které nejsou součástí žádné úlohy, ale mohou být vybrány jako jednotlivé komponenty.

ID komponenty | Name | Verze
--- | --- | ---
Component.Android.Emulator | Emulátor sady Visual Studio pro Android | 15.6.27413.0
Komponenta. Android. NDK. R11C | Android NDK (R11C) | 11.3.14
Component.Android.NDK.R11C_3264 | Android NDK (R11C) (32 bitů) | 11.3.16
Komponenta. Android. SDK23 | Instalace Android SDK (úroveň rozhraní API 23) (globální instalace) | 15.9.28107.0
Komponenta. Android. SDK25 | Instalace Android SDK (úroveň rozhraní API 25) | 15.9.28107.0
Komponenta. GitHub. VisualStudio | Rozšíření GitHub pro Visual Studio | 2.5.2.2500
Součást. Google. Android. emulátor. API23. v2 | Google Android Emulator (úroveň rozhraní API 23) (globální instalace) | 15.6.27413.0
Komponenta. Google. Android. emulátor. API25 | Google Android Emulator (rozhraní API úrovně 25) | 15.7.27604.0
Microsoft. Component. Blend. SDK. WPF | Blend pro Visual Studio SDK pro .NET | 15.6.27406.0
Microsoft.Component.HelpViewer | Help Viewer | 15.9.28307.421
Microsoft.VisualStudio.Component.LinqToSql | Nástroje LINQ to SQL | 15.6.27406.0
Microsoft.VisualStudio.Component.Phone.Emulator | Windows 10 Mobile emulátoru (Anniversary Edition) | 15.6.27406.0
Microsoft.VisualStudio.Component.Phone.Emulator.15063 | Windows 10 Mobile emulátoru (Creators Update) | 15.6.27406.0
Microsoft.VisualStudio.Component.Runtime.Node.x86.6.4.0 | Modul runtime pro komponenty založené na Node.js verze 6.4.0 (x86) | 15.7.27617.1
Microsoft.VisualStudio.Component.Runtime.Node.x86.7.4.0 | Modul runtime pro komponenty založené na Node.js verze 7.4.0 (x86) | 15.7.27617.1
Microsoft.VisualStudio.Component.TestTools.CodedUITest | Programový test UI | 15.0.26606.0
Microsoft.VisualStudio.Component.TestTools.FeedbackClient | Microsoft Feedback Client | 15.6.27406.0
Microsoft.VisualStudio.Component.TestTools.MicrosoftTestManager | Microsoft Test Manager | 15.6.27406.0
Microsoft.VisualStudio.Component.TypeScript.2.0 | TypeScript 2.0 SDK | 15.8.27729.1
Microsoft.VisualStudio.Component.TypeScript.2.1 | TypeScript 2.1 SDK | 15.8.27729.1
Microsoft. VisualStudio. Component. TypeScript. 2.2 | Sada TypeScript 2,2 SDK | 15.8.27729.1
Microsoft. VisualStudio. Component. TypeScript. 2.5 | Sada TypeScript 2,5 SDK | 15.6.27406.0
Microsoft. VisualStudio. Component. TypeScript. 2.6 | Sada TypeScript 2,6 SDK | 15.0.27729.1
Microsoft. VisualStudio. Component. TypeScript. 2.7 | Sada TypeScript 2,7 SDK | 15.0.27729.1
Microsoft. VisualStudio. Component. TypeScript. 2.8 | Sada TypeScript 2,8 SDK | 15.0.27729.1
Microsoft. VisualStudio. Component. TypeScript. 2.9 | Sada TypeScript 2,9 SDK | 15.0.27924.0
Microsoft. VisualStudio. Component. TypeScript. 3.0 | Sada TypeScript 3,0 SDK | 15.0.27924.0
Microsoft. VisualStudio. Component. VC. ATL. ARM | Visual C++ ATL pro ARM | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.ATL.ARM.Spectre | Visual C++ ATL pro ARM se zmírněními rizik spectre | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.ATL.ARM64 | Visual C++ ATL pro ARM64 | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.ATL.ARM64.Spectre | Visual C++ ATL pro ARM64 s omezením rizik spectre | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.ATL.Spectre | Visual C++ ATL (x86/x64) se zmírněním rizik spectre | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.ATLMFC.Spectre | Visual C++ MFC pro x86/x64 s omezením rizik spectre | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.ClangC2 | Clang/C2 (experimentální) | 15.7.27520.0
Microsoft.VisualStudio.Component.VC.MFC.ARM | Visual C++ MFC pro ARM | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.MFC.ARM.Spectre | Visual C++ MFC pro ARM s omezením rizik spectre | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.MFC.ARM64 | Visual C++ MFC pro ARM64 | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.MFC.ARM64.Spectre | Podpora Visual C++ podporou MFC pro ARM64 se Zmírněními hrozeb Spectre | 15.7.27625.0
Microsoft. VisualStudio. Component. VC. runtimes. ARM. Spectre | VC + + 2017 verze 15,9 v 14.16 knihovny pro Spectre (ARM) | 15.9.28230.55
Microsoft. VisualStudio. Component. VC. runtimes. ARM64. Spectre | VC + + 2017 verze 15,9 v 14.16 knihovny pro Spectre (ARM64) | 15.9.28230.55
Microsoft. VisualStudio. Component. VC. runtimes. x86. x64. Spectre | VC + + 2017 verze 15,9 v 14.16 knihovny pro Spectre (x86 a x64) | 15.9.28230.55
Microsoft. VisualStudio. Component. VC. Tools. 14.11 | VC + + 2017 verze 15,4 v 14.11 sady nástrojů | 15.0.27924.0
Microsoft. VisualStudio. Component. VC. Tools. 14.12 | VC + + 2017 verze 15,5 v 14.12 sady nástrojů | 15.0.27924.0
Microsoft. VisualStudio. Component. VC. Tools. 14.13 – | VC + + 2017 verze 15,6 v 14.13 – sady nástrojů | 15.0.27924.0
Microsoft. VisualStudio. Component. VC. Tools. 14.14 – | Sada nástrojů VC++ 2017 verze 15.7 v14.14 | 15.0.27924.0
Microsoft.VisualStudio.Component.VC.Tools.14.15 | Sada nástrojů VC++ 2017 verze 15.8 v14.15 | 15.0.28230.55
