---
title: Úlohy sady Visual Studio Community 2019 a ID komponent
titleSuffix: ''
description: Použití zatížení a ID komponent k instalaci sady Visual Studio pomocí příkazového řádku nebo pro určení jako závislosti v manifestu VSIX
keywords: ''
author: j-martens
ms.author: jmartens
manager: jmartens
ms.date: 05/24/2021
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.topic: include
ms.openlocfilehash: 539b6a1d614bc0e3e7d61a14debcf14a495013a9
ms.sourcegitcommit: 18e7300d4878f2fcd0263a4aff31a755ae8fc289
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/25/2021
ms.locfileid: "110449739"
---
## <a name="visual-studio-core-editor-included-with-visual-studio-community-2019"></a>Základní editor Visual Studio (zahrnutý v rámci sady Visual Studio Community 2019)

**ID:** Microsoft. VisualStudio. úlohy. CoreEditor

**Popis:** Základní prostředí sady Visual Studio, včetně úprav kódu s podporou syntaxe, správy zdrojového kódu a správy pracovních položek.

### <a name="components-included-by-this-workload"></a>Součásti zahrnuté v tomto zatížení

ID součásti | Name | Verze | Typ závislosti
--- | --- | --- | ---
Microsoft. VisualStudio. Component. CoreEditor | Základní editor sady Visual Studio | 16.1.28811.260 | Vyžadováno
Microsoft. VisualStudio. Component. StartPageExperiment. cpp | Úvodní stránka sady Visual Studio pro uživatele C++ | 16.0.28315.86 | Volitelné

## <a name="azure-development"></a>Vývoj pro Azure

**ID:** Microsoft. VisualStudio. úlohy. Azure

**Popis:** Sady SDK, nástroje a projekty Azure pro vývoj cloudových aplikací a vytváření prostředků pomocí .NET a .NET Framework. Zahrnuje také nástroje pro uzavřeníí aplikace, včetně podpory Docker.

### <a name="components-included-by-this-workload"></a>Součásti zahrnuté v tomto zatížení

ID součásti | Name | Verze | Typ závislosti
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Služby jazyka Razor | 16.10.31205.252 | Vyžadováno
Component.Microsoft.VisualStudio.Web.AzureFunctions | Azure WebJobs nástroje | 16.10.31205.252 | Vyžadováno
Component.Microsoft.Web.LibraryManager | Správce knihovny | 16.10.31205.180 | Vyžadováno
Component.Microsoft.WebTools.BrowserLink.WebLivePreview | Web Live Preview | 0.7.22.39845 | Vyžadováno
Microsoft.Component.MSBuild | MSBuild | 16.5.29515.121 | Vyžadováno
Microsoft.ComponentGroup.ClickOnce.Publish | Publikování ClickOnce pro .NET  | 16.10.31303.231 | Vyžadováno
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 | 16.0.28517.75 | Vyžadováno
Microsoft.Net.Component.4.5.TargetingPack | Sada targeting pack .NET Framework 4,5 | 16.0.28517.75 | Vyžadováno
Microsoft.Net. Component. 4.6.1. TargetingPack | .NET Framework 4.6.1 targeting pack | 16.0.28517.75 | Vyžadováno
Microsoft.Net. Component. 4.7.2. TargetingPack | Sada targeting pack .NET Framework 4.7.2 | 16.10.31205.252 | Vyžadováno
Microsoft. NET. Component. 4.8. SDK | .NET Framework 4,8 SDK | 16.4.29313.120 | Vyžadováno
Microsoft.Net. Component. DevelopmentPrerequisites | Vývojové nástroje .NET Framework 4.7.2 | 16.3.29207.166 | Vyžadováno
Microsoft. NetCore. Component. DevelopmentTools | Vývojové nástroje .NET | 16.10.31303.231 | Vyžadováno
Microsoft. NetCore. Component. Runtime. 3.1 | Runtime .NET Core 3,1 (LTS) | 16.10.31320.204 | Vyžadováno
Microsoft.NetCore.Component.Runtime.5.0 | .NET 5.0 Runtime | 16.10.31320.204 | Vyžadováno
Microsoft.NetCore.Component.SDK | .NET SDK | 16.10.31320.204 | Vyžadováno
Microsoft.NetCore.Component.Web | Vývojové nástroje pro .NET | 16.10.31303.231 | Vyžadováno
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Nástroje pro vytváření v Azure | 16.0.28625.61 | Vyžadováno
Microsoft.VisualStudio.Component.Azure.ClientLibs | Knihovny Azure pro .NET | 16.0.28315.86 | Vyžadováno
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Azure Compute emulátoru | 16.10.31205.252 | Vyžadováno
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Emulátor úložiště Azure | 16.4.29313.120 | Vyžadováno
Microsoft.VisualStudio.Component.CloudExplorer | Průzkumník cloudu | 16.0.28625.61 | Vyžadováno
Microsoft. VisualStudio. Component. Common. Azure. Tools | Nástroje pro připojení a publikování | 16.4.29409.204 | Vyžadováno
Microsoft.VisualStudio.Component.DockerTools | Kontejnerové vývojové nástroje | 16.4.29409.204 | Vyžadováno
Microsoft. VisualStudio. Component. FSharp | Podpora jazyka F # | 16.0.28315.86 | Vyžadováno
Microsoft. VisualStudio. Component. FSharp. Webtemplates | Podpora jazyka F # pro webové projekty | 16.3.29207.166 | Vyžadováno
Microsoft. VisualStudio. Component. IISExpress | IIS Express  | 16.0.28315.86 | Vyžadováno
Microsoft. VisualStudio. Component. JavaScript. Diagnostics | Diagnostika JavaScriptu | 16.0.28517.75 | Vyžadováno
Microsoft. VisualStudio. Component. JavaScript. TypeScript | Podpora jazyků JavaScript a TypeScript | 16.10.31303.231 | Vyžadováno
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Jádro úloh spravovaného desktopového prostředí | 16.4.29318.151 | Vyžadováno
Microsoft.VisualStudio.Component.MSODBC.SQL | SQL Server ovladače ODBC | 16.0.28625.61 | Vyžadováno
Microsoft.VisualStudio.Component.MSSQL.CMDLnUtils | SQL Server nástroje příkazového řádku | 16.0.28707.177 | Vyžadováno
Microsoft.VisualStudio.Component.NuGet | Správce balíčků NuGet | 16.1.28829.92 | Vyžadováno
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilátory C# a Visual Basic Roslyn | 16.0.28714.129 | Vyžadováno
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# a Visual Basic | 16.10.31205.252 | Vyžadováno
Microsoft.VisualStudio.Component.SQL.ADAL | Modul runtime SQL ADAL | 16.0.28517.75 | Vyžadováno
Microsoft. VisualStudio. Component. SQL. CLR | Datové typy CLR pro SQL Server | 16.0.28315.86 | Vyžadováno
Microsoft. VisualStudio. Component. SQL. DataSources | Zdroje dat pro podporu SQL Server | 16.0.28315.86 | Vyžadováno
Microsoft. VisualStudio. Component. SQL. LocalDB. Runtime | SQL Server Express 2016 LocalDB | 16.0.28625.61 | Vyžadováno
Microsoft. VisualStudio. Component. SQL. SSDT | SQL Server Data Tools | 16.3.29207.166 | Vyžadováno
Microsoft. VisualStudio. Component. TextTemplating | Transformace textové šablony | 16.0.28625.61 | Vyžadováno
Microsoft. VisualStudio. Component. TypeScript. 4.2 | Sada TypeScript 4,2 SDK | 16.0.31303.231 | Vyžadováno
Microsoft. VisualStudio. Component. Web | ASP.NET a vývojové nástroje pro web | 16.10.31205.252 | Vyžadováno
Microsoft.VisualStudio.ComponentGroup.Azure.Prerequisites | Požadavky na vývoj pro Azure | 16.10.31303.231 | Vyžadováno
Microsoft.VisualStudio.ComponentGroup.AzureFunctions | Azure WebJobs nástroje | 16.10.31205.180 | Vyžadováno
Microsoft.VisualStudio.ComponentGroup.Web | Požadavky ASP.NET a webových vývojových nástrojů | 16.10.31205.180 | Vyžadováno
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Vývoj pro ASP.NET a web | 16.10.31205.180 | Vyžadováno
Microsoft.Component.Azure.DataLake.Tools | Azure Data Lake a Stream Analytics Tools | 16.10.31205.252 | Doporučeno
Microsoft.Net.Component.4.5.1.TargetingPack | .NET Framework 4.5.1 | 16.0.28517.75 | Doporučeno
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework 4.6 | 16.0.28517.75 | Doporučeno
Microsoft.Net. Component. 4. TargetingPack | Sada targeting pack .NET Framework 4 | 16.0.28517.75 | Doporučeno
Microsoft.Net. Component. TargetingPacks. Common | .NET Framework nástroje pro vývoj 4 – 4,6 | 16.0.28516.191 | Doporučeno
Microsoft. VisualStudio. Component. AspNet45 | Pokročilé funkce ASP.NET | 16.10.31205.252 | Doporučeno
Microsoft. VisualStudio. Component. Azure. Kubernetes. Tools | Visual Studio Tools for Kubernetes | 16.10.31205.252 | Doporučeno
Microsoft. VisualStudio. Component. Azure. PowerShell | Azure Powershell | 16.5.29515.121 | Doporučeno
Microsoft. VisualStudio. Component. Azure. ResourceManager. Tools | Základní nástroje Azure Resource Manager | 16.4.29409.204 | Doporučeno
Microsoft. VisualStudio. Component. Azure. ServiceFabric. Tools | Nástroje Service Fabricu | 16.4.29313.120 | Doporučeno
Microsoft. VisualStudio. Component. Azure. Waverton | Azure Cloud Services core tools | 16.10.31205.252 | Doporučeno
Microsoft.VisualStudio.Component.Azure.Waverton.BuildTools | Azure Cloud Services sestavovací nástroje | 16.10.31205.252 | Doporučeno
Microsoft.VisualStudio.Component.DiagnosticTools | Nástroje pro profilaci .NET | 16.10.31205.252 | Doporučeno
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 16.10.31305.154 | Doporučeno
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 16.0.28517.75 | Doporučeno
Microsoft.VisualStudio.ComponentGroup.Azure.CloudServices | Azure Cloud Services nástroje | 16.10.31205.180 | Doporučeno
Microsoft.VisualStudio.ComponentGroup.Azure.ResourceManager.Tools | Azure Resource Manager nástroje | 16.0.28528.71 | Doporučeno
Microsoft.Net.Component.4.6.2.TargetingPack | .NET Framework 4.6.2 | 16.0.28517.75 | Volitelné
Microsoft.Net. Component. 4.7.1. TargetingPack | Sada targeting pack .NET Framework 4.7.1 | 16.10.31205.252 | Volitelné
Microsoft.Net. Component. 4.7. TargetingPack | Sada targeting pack .NET Framework 4,7 | 16.10.31205.252 | Volitelné
Microsoft.Net. Component. 4.8. TargetingPack | Sada targeting pack .NET Framework 4,8 | 16.4.29313.120 | Volitelné
Microsoft.Net. Component.. 4.6.1. DeveloperTools | Vývojové nástroje .NET Framework 4.6.1 | 16.3.29207.166 | Volitelné
Microsoft.Net. Component. 4.6.2. DeveloperTools | Vývojové nástroje .NET Framework 4.6.2 | 16.3.29207.166 | Volitelné
Microsoft.Net. Component. 4.7.1. DeveloperTools | Vývojové nástroje .NET Framework 4.7.1 | 16.3.29207.166 | Volitelné
Microsoft.Net. Component.. 4.7. DeveloperTools | .NET Framework 4.7 – vývojové nástroje | 16.3.29207.166 | Volitelné
Microsoft.Net.ComponentGroup.4.8.DeveloperTools | .NET Framework 4.8 – vývojové nástroje | 16.4.29318.151 | Volitelné
Microsoft.Net.Core.Component.SDK.2.1 | .NET Core 2.1 Runtime (LTS) | 16.10.31320.204 | Volitelné
Microsoft.VisualStudio.Component.Azure.Storage.AzCopy | Azure Storage AzCopy | 16.0.28517.75 | Volitelné
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | 16.0.28625.61 | Volitelné

## <a name="data-storage-and-processing"></a>Ukládání a zpracování dat

**ID:** Microsoft.VisualStudio.Workload.Data

**Popis:** Připojení, vývoj a testování datových řešení pomocí SQL Server, Azure Data Lake nebo Hadoop.

### <a name="components-included-by-this-workload"></a>Komponenty zahrnuté v této úlohu

ID komponenty | Name | Verze | Typ závislosti
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Služby jazyka Razor | 16.10.31205.252 | Doporučeno
Součást. Microsoft. Web. LibraryManager | Správce knihovny | 16.10.31205.180 | Doporučeno
Komponenta. Microsoft. WebTools. BrowserLink. WebLivePreview | Web Live Preview | 0.7.22.39845 | Doporučeno
Microsoft. Component. Azure. datalake. Tools | Nástroje Azure Data Lake a Stream Analytics | 16.10.31205.252 | Doporučeno
Microsoft. Component. MSBuild | MSBuild | 16.5.29515.121 | Doporučeno
Microsoft.Net. Component. 4.5.1. TargetingPack | Sada .NET Framework 4.5.1 targeting pack | 16.0.28517.75 | Doporučeno
Microsoft.Net. Component. 4.5.2. TargetingPack | Sada .NET Framework 4.5.2 targeting pack | 16.0.28517.75 | Doporučeno
Microsoft.Net. Component. 4.5. TargetingPack | Sada targeting pack .NET Framework 4,5 | 16.0.28517.75 | Doporučeno
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework 4.6 | 16.0.28517.75 | Doporučeno
Microsoft.Net.Component.4.7.2.TargetingPack | .NET Framework 4.7.2 | 16.10.31205.252 | Doporučeno
Microsoft.Net.Component.4.8.SDK | .NET Framework 4.8 SDK | 16.4.29313.120 | Doporučeno
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 cílení pack | 16.0.28517.75 | Doporučeno
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | .NET Framework 4.7.2 – vývojové nástroje | 16.3.29207.166 | Doporučeno
Microsoft.Net.ComponentGroup.TargetingPacks.Common | .NET Framework 4–4.6 – vývojové nástroje | 16.0.28516.191 | Doporučeno
Microsoft.NetCore.Component.Runtime.3.1 | .NET Core 3.1 Runtime (LTS) | 16.10.31320.204 | Doporučeno
Microsoft. NetCore. Component. Runtime. 5.0 | .NET 5,0 – modul runtime | 16.10.31320.204 | Doporučeno
Microsoft. NetCore. Component. SDK | .NET SDK | 16.10.31320.204 | Doporučeno
Microsoft. VisualStudio. Component. Azure. AuthoringTools | Nástroje pro tvorbu Azure | 16.0.28625.61 | Doporučeno
Microsoft. VisualStudio. Component. Azure. ClientLibs | Knihovny Azure pro .NET | 16.0.28315.86 | Doporučeno
Microsoft. VisualStudio. Component. Azure. Compute. emulátor | Emulátor služby COMPUTE Azure | 16.10.31205.252 | Doporučeno
Microsoft. VisualStudio. Component. Azure. Storage. emulátor | Emulátor úložiště Azure | 16.4.29313.120 | Doporučeno
Microsoft. VisualStudio. Component. Azure. Waverton | Základní nástroje pro Azure Cloud Services | 16.10.31205.252 | Doporučeno
Microsoft.VisualStudio.Component.Azure.Waverton.BuildTools | Azure Cloud Services sestavovací nástroje | 16.10.31205.252 | Doporučeno
Microsoft.VisualStudio.Component.CloudExplorer | Průzkumník cloudu | 16.0.28625.61 | Doporučeno
Microsoft.VisualStudio.Component.Common.Azure.Tools | Nástroje pro připojení a publikování | 16.4.29409.204 | Doporučeno
Microsoft.VisualStudio.Component.DockerTools | Kontejnerové vývojové nástroje | 16.4.29409.204 | Doporučeno
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 16.0.28315.86 | Doporučeno
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostika JavaScriptu | 16.0.28517.75 | Doporučeno
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Podpora jazyků JavaScript a TypeScript | 16.10.31303.231 | Doporučeno
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Jádro úlohy spravované plochy | 16.4.29318.151 | Doporučeno
Microsoft. VisualStudio. Component. MSODBC. SQL | SQL Server ovladač ODBC | 16.0.28625.61 | Doporučeno
Microsoft. VisualStudio. Component. MSSQL. CMDLnUtils | SQL Server nástroje příkazového řádku | 16.0.28707.177 | Doporučeno
Microsoft. VisualStudio. Component. NuGet | Správce balíčků NuGet | 16.1.28829.92 | Doporučeno
Microsoft. VisualStudio. Component. Roslyn. Compiler | Kompilátory C# a Visual Basic Roslyn | 16.0.28714.129 | Doporučeno
Microsoft. VisualStudio. Component. Roslyn. LanguageServices | C# a Visual Basic | 16.10.31205.252 | Doporučeno
Microsoft. VisualStudio. Component. SQL. ADAL | Modul runtime SQL ADAL | 16.0.28517.75 | Doporučeno
Microsoft. VisualStudio. Component. SQL. CLR | Datové typy CLR pro SQL Server | 16.0.28315.86 | Doporučeno
Microsoft.VisualStudio.Component.SQL.DataSources | Zdroje dat pro podporu SQL Server dat | 16.0.28315.86 | Doporučeno
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 16.0.28625.61 | Doporučeno
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 16.3.29207.166 | Doporučeno
Microsoft.VisualStudio.Component.TextTemplating | Transformace textových šablon | 16.0.28625.61 | Doporučeno
Microsoft.VisualStudio.Component.TypeScript.4.2 | TypeScript 4.2 SDK | 16.0.31303.231 | Doporučeno
Microsoft.VisualStudio.Component.Web | ASP.NET a webové vývojové nástroje | 16.10.31205.252 | Doporučeno
Microsoft.VisualStudio.ComponentGroup.Web | Požadavky na ASP.NET a vývojové nástroje pro web | 16.10.31205.180 | Doporučeno
Microsoft. VisualStudio. Component. WebToolsExtensions | Vývoj pro ASP.NET a web | 16.10.31205.180 | Doporučeno
Microsoft.Net. Component. 4.6.1. TargetingPack | .NET Framework 4.6.1 targeting pack | 16.0.28517.75 | Volitelné
Microsoft. VisualStudio. Component. FSharp. Desktop | Podpora jazyka F # pro Desktop | 16.0.28315.86 | Volitelné

## <a name="data-science-and-analytical-applications"></a>Aplikace pro datovou vědu a analýzu

**ID:** Microsoft. VisualStudio. úlohy. datavěda

**Popis:** Jazyky a nástroje pro vytváření aplikací pro datové vědy, včetně Pythonu a F #

### <a name="components-included-by-this-workload"></a>Součásti zahrnuté v tomto zatížení

ID součásti | Name | Verze | Typ závislosti
--- | --- | --- | ---
Microsoft. Component. PythonTools | Podpora jazyka Python | 16.10.31313.127 | Doporučeno
Microsoft. Component. PythonTools. Minicondax64 | Python miniconda (mimo podporu) | 16.10.31313.127 | Doporučeno
Microsoft.Component.PythonTools.Web | Webová podpora Pythonu | 16.10.31205.252 | Doporučeno
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 | 16.0.28517.75 | Doporučeno
Microsoft.VisualStudio.Component.Common.Azure.Tools | Nástroje pro připojení a publikování | 16.4.29409.204 | Doporučeno
Microsoft.VisualStudio.Component.FSharp.Desktop | Podpora desktopových jazyků F# | 16.0.28315.86 | Doporučeno
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Podpora jazyků JavaScript a TypeScript | 16.10.31303.231 | Doporučeno
Microsoft.VisualStudio.Component.NuGet | Správce balíčků NuGet | 16.1.28829.92 | Doporučeno
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilátory C# a Visual Basic Roslyn | 16.0.28714.129 | Doporučeno
Microsoft. VisualStudio. Component. Roslyn. LanguageServices | C# a Visual Basic | 16.10.31205.252 | Doporučeno
Microsoft. VisualStudio. Component. TypeScript. 4.2 | Sada TypeScript 4,2 SDK | 16.0.31303.231 | Doporučeno
Microsoft. VisualStudio. Component. WebDeploy | Web Deploy | 16.0.28517.75 | Doporučeno
Microsoft. VisualStudio. Component. WebToolsExtensions | Vývoj pro ASP.NET a web | 16.10.31205.180 | Doporučeno
Microsoft. Component. PythonTools. NativeDevelopment | Nástroje pro nativní vývoj v Pythonu | 16.10.31205.180 | Volitelné
Microsoft. VisualStudio. Component. Graphics. Tools | Ladicí program grafiky a Profiler GPU pro DirectX | 16.0.28625.61 | Volitelné
Microsoft. VisualStudio. Component. VC. CoreIde | Základní funkce C++ | 16.10.31205.252 | Volitelné
Microsoft.VisualStudio.Component.VC.DiagnosticTools | Nástroje pro profilaci jazyka C++ | 16.5.29515.121 | Volitelné
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | MSVC v142 – buildovací nástroje VS 2019 C++ x64/x86 (nejnovější) | 16.10.31205.252 | Volitelné
Microsoft.VisualStudio.Component.Windows10SDK | Windows Universal C Runtime | 16.4.29409.204 | Volitelné
Microsoft.VisualStudio.Component.Windows10SDK.19041 | Windows 10 SDK (10.0.19041.0) | 16.10.31205.252 | Volitelné

## <a name="net-desktop-development"></a>Vývoj desktopových aplikací pro .NET

**ID:** Microsoft.VisualStudio.Workload.ManagedDesktop

**Popis:** Vytvářete aplikace WPF, model Windows Forms a konzolové aplikace pomocí C#, Visual Basic a F# s .NET a .NET Framework.

### <a name="components-included-by-this-workload"></a>Komponenty zahrnuté v této úlohu

ID komponenty | Name | Verze | Typ závislosti
--- | --- | --- | ---
Microsoft.Component.MSBuild | MSBuild | 16.5.29515.121 | Vyžadováno
Microsoft.Net. Component. 4.7.2. TargetingPack | Sada targeting pack .NET Framework 4.7.2 | 16.10.31205.252 | Vyžadováno
Microsoft. NET. Component. 4.8. SDK | .NET Framework 4,8 SDK | 16.4.29313.120 | Vyžadováno
Microsoft.Net. Component. DevelopmentPrerequisites | Vývojové nástroje .NET Framework 4.7.2 | 16.3.29207.166 | Vyžadováno
Microsoft. NetCore. Component. Runtime. 3.1 | Runtime .NET Core 3,1 (LTS) | 16.10.31320.204 | Vyžadováno
Microsoft. NetCore. Component. Runtime. 5.0 | .NET 5,0 – modul runtime | 16.10.31320.204 | Vyžadováno
Microsoft. NetCore. Component. SDK | .NET SDK | 16.10.31320.204 | Vyžadováno
Microsoft. VisualStudio. Component. ManagedDesktop. Core | Jádro úlohy spravované plochy | 16.4.29318.151 | Vyžadováno
Microsoft.VisualStudio.Component.ManagedDesktop.Prerequisites | Nástroje pro vývoj desktopových aplikací .NET | 16.10.31205.180 | Vyžadováno
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilátory C# a Visual Basic Roslyn | 16.0.28714.129 | Vyžadováno
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# a Visual Basic | 16.10.31205.252 | Vyžadováno
Microsoft.VisualStudio.Component.SQL.CLR | Datové typy CLR pro SQL Server | 16.0.28315.86 | Vyžadováno
Microsoft.VisualStudio.Component.TextTemplating | Transformace textových šablon | 16.0.28625.61 | Vyžadováno
Component.Microsoft.VisualStudio.LiveShare | Live Share | 1.0.4062 | Doporučeno
Microsoft.ComponentGroup.Blend | Blend for Visual Studio | 16.0.28315.86 | Doporučeno
Microsoft.ComponentGroup.ClickOnce.Publish | Publikování ClickOnce pro .NET  | 16.10.31303.231 | Doporučeno
Microsoft.Net. Component. 4.5.1. TargetingPack | Sada .NET Framework 4.5.1 targeting pack | 16.0.28517.75 | Doporučeno
Microsoft.Net. Component. 4.5.2. TargetingPack | Sada .NET Framework 4.5.2 targeting pack | 16.0.28517.75 | Doporučeno
Microsoft.Net. Component. 4.5. TargetingPack | Sada targeting pack .NET Framework 4,5 | 16.0.28517.75 | Doporučeno
Microsoft.Net. Component. 4.6.1. TargetingPack | .NET Framework 4.6.1 targeting pack | 16.0.28517.75 | Doporučeno
Microsoft.Net. Component. 4.6. TargetingPack | Sada targeting pack .NET Framework 4,6 | 16.0.28517.75 | Doporučeno
Microsoft.Net. Component. 4. TargetingPack | Sada targeting pack .NET Framework 4 | 16.0.28517.75 | Doporučeno
Microsoft.Net. Component. TargetingPacks. Common | .NET Framework 4–4.6 – vývojové nástroje | 16.0.28516.191 | Doporučeno
Microsoft.NetCore.Component.DevelopmentTools | Vývojové nástroje pro .NET | 16.10.31303.231 | Doporučeno
Microsoft.VisualStudio.Component.Common.Azure.Tools | Nástroje pro připojení a publikování | 16.4.29409.204 | Doporučeno
Microsoft.VisualStudio.Component.Debugger.JustInTime | Ladicí program za běhu | 16.0.28517.75 | Doporučeno
Microsoft.VisualStudio.Component.DiagnosticTools | Nástroje pro profilaci .NET | 16.10.31205.252 | Doporučeno
Microsoft.VisualStudio.Component.DotNetModelBuilder | ML.NET Model Builder (Preview) | 16.10.31205.252 | Doporučeno
Microsoft.VisualStudio.Component.EntityFramework | Entity Framework 6 nástrojů | 16.0.28315.86 | Doporučeno
Microsoft. VisualStudio. Component. FSharp | Podpora jazyka F # | 16.0.28315.86 | Doporučeno
Microsoft. VisualStudio. Component. IntelliCode | IntelliCode | 16.10.31305.154 | Doporučeno
Microsoft. VisualStudio. Component. JavaScript. TypeScript | Podpora jazyků JavaScript a TypeScript | 16.10.31303.231 | Doporučeno
Microsoft. VisualStudio. Component. NuGet | Správce balíčků NuGet | 16.1.28829.92 | Doporučeno
Microsoft. VisualStudio. Component. TypeScript. 4.2 | Sada TypeScript 4,2 SDK | 16.0.31303.231 | Doporučeno
Microsoft. VisualStudio. Component. WebToolsExtensions | Vývoj pro ASP.NET a web | 16.10.31205.180 | Doporučeno
Component. Dotfuscator | PreEmptive Protection – Dotfuscator | 16.10.31205.252 | Volitelné
Součást. Microsoft. VisualStudio. RazorExtension | Jazykové služby Razor | 16.10.31205.252 | Volitelné
Component.Microsoft.Web.LibraryManager | Správce knihovny | 16.10.31205.180 | Volitelné
Component.Microsoft.WebTools.BrowserLink.WebLivePreview | Web Live Preview | 0.7.22.39845 | Volitelné
Microsoft.Net.Component.4.6.2.TargetingPack | .NET Framework 4.6.2 | 16.0.28517.75 | Volitelné
Microsoft.Net.Component.4.7.1.TargetingPack | .NET Framework 4.7.1 | 16.10.31205.252 | Volitelné
Microsoft.Net.Component.4.7.TargetingPack | .NET Framework 4.7 | 16.10.31205.252 | Volitelné
Microsoft.Net.Component.4.8.TargetingPack | .NET Framework 4.8 | 16.4.29313.120 | Volitelné
Microsoft.Net.ComponentGroup.4.6.1.DeveloperTools | .NET Framework 4.6.1 | 16.3.29207.166 | Volitelné
Microsoft.Net. Component. 4.6.2. DeveloperTools | Vývojové nástroje .NET Framework 4.6.2 | 16.3.29207.166 | Volitelné
Microsoft.Net. Component. 4.7.1. DeveloperTools | Vývojové nástroje .NET Framework 4.7.1 | 16.3.29207.166 | Volitelné
Microsoft.Net. Component.. 4.7. DeveloperTools | Vývojové nástroje .NET Framework 4,7 | 16.3.29207.166 | Volitelné
Microsoft.Net. Component.. 4,8. DeveloperTools | Vývojové nástroje .NET Framework 4,8 | 16.4.29318.151 | Volitelné
Microsoft. NET. Core. Component. SDK. 2.1 | Runtime .NET Core 2,1 (LTS) | 16.10.31320.204 | Volitelné
Microsoft.VisualStudio.Component.DockerTools | Kontejnerové vývojové nástroje | 16.4.29409.204 | Volitelné
Microsoft. VisualStudio. Component. FSharp. Desktop | Podpora jazyka F # pro Desktop | 16.0.28315.86 | Volitelné
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 16.0.28315.86 | Volitelné
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostika JavaScriptu | 16.0.28517.75 | Volitelné
Microsoft.VisualStudio.Component.MSODBC.SQL | SQL Server ovladače ODBC | 16.0.28625.61 | Volitelné
Microsoft.VisualStudio.Component.MSSQL.CMDLnUtils | SQL Server nástroje příkazového řádku | 16.0.28707.177 | Volitelné
Microsoft.VisualStudio.Component.PortableLibrary | Balíček cílení na přenosnou knihovnu .NET | 16.10.31205.252 | Volitelné
Microsoft.VisualStudio.Component.SQL.ADAL | Modul runtime SQL ADAL | 16.0.28517.75 | Volitelné
Microsoft.VisualStudio.Component.SQL.DataSources | Zdroje dat pro podporu SQL Server | 16.0.28315.86 | Volitelné
Microsoft. VisualStudio. Component. SQL. LocalDB. Runtime | SQL Server Express 2016 LocalDB | 16.0.28625.61 | Volitelné
Microsoft. VisualStudio. Component. SQL. SSDT | SQL Server Data Tools | 16.3.29207.166 | Volitelné
Microsoft. VisualStudio. Component. WCF. Tools | Windows Communication Foundation | 16.0.28625.61 | Volitelné
Microsoft. VisualStudio. Component. Web | ASP.NET a vývojové nástroje pro web | 16.10.31205.252 | Volitelné
Microsoft.VisualStudio.ComponentGroup.MSIX. balení | Nástroje pro vytváření balíčků MSIX | 16.10.31205.180 | Volitelné
Microsoft. VisualStudio. Component. Web | Požadavky na ASP.NET a vývojové nástroje pro web | 16.10.31205.180 | Volitelné

## <a name="game-development-with-unity"></a>Vývoj her pomocí Unity

**ID:** Microsoft. VisualStudio. úlohy. ManagedGame

**Popis:** Vytvářejte 2D a 3D hry pomocí Unity, výkonného vývojového prostředí pro různé platformy.

### <a name="components-included-by-this-workload"></a>Komponenty zahrnuté v této úlohu

ID komponenty | Name | Verze | Typ závislosti
--- | --- | --- | ---
Microsoft.Net.Component.3.5.DeveloperTools | .NET Framework 3.5 – vývojové nástroje | 16.0.28517.75 | Vyžadováno
Microsoft.Net.Component.4.7.1.TargetingPack | .NET Framework 4.7.1 | 16.10.31205.252 | Vyžadováno
Microsoft.VisualStudio.Component.NuGet | Správce balíčků NuGet | 16.1.28829.92 | Vyžadováno
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilátory C# a Visual Basic Roslyn | 16.0.28714.129 | Vyžadováno
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# a Visual Basic | 16.10.31205.252 | Vyžadováno
Microsoft.VisualStudio.Component.Unity | Visual Studio Tools for Unity | 16.0.28315.86 | Vyžadováno
Component.UnityEngine.x64 | Centrum Unity | 16.10.31205.252 | Doporučeno
Component. UnityEngine. x86 | Editor bitových procesorů Unity 5,6 32 | 16.1.28811.260 | Doporučeno

## <a name="linux-development-with-c"></a>Vývoj linuxových aplikací v jazyce C++

**ID:** Microsoft. VisualStudio. úlohy. NativeCrossPlat

**Popis:** Vytváření a ladění aplikací spuštěných v prostředí Linux.

### <a name="components-included-by-this-workload"></a>Součásti zahrnuté v tomto zatížení

ID součásti | Name | Verze | Typ závislosti
--- | --- | --- | ---
Component. MDD. Linux | C++ pro vývoj pro Linux | 16.5.29515.121 | Vyžadováno
Microsoft. VisualStudio. Component. VC. CoreIde | Základní funkce C++ | 16.10.31205.252 | Vyžadováno
Komponenta. Linux. CMake | Nástroje C++ CMake pro Linux | 16.2.29003.222 | Doporučeno
Microsoft. VisualStudio. Component. IntelliCode | IntelliCode | 16.10.31305.154 | Doporučeno
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Vývoj pro ASP.NET a web | 16.10.31205.180 | Doporučeno
Component.MDD.Linux.GCC.arm | Integrované vývojové nástroje a nástroje IoT | 16.5.29515.121 | Volitelné

## <a name="desktop-development-with-c"></a>Vývoj desktopových aplikací pomocí C++

**ID:** Microsoft.VisualStudio.Workload.NativeDesktop

**Popis:** Vytvářete moderní aplikace C++ pro Windows pomocí nástrojů podle vašeho výběru, včetně MSVC, Clang, CMake nebo MSBuild.

### <a name="components-included-by-this-workload"></a>Komponenty zahrnuté v této úlohu

ID komponenty | Name | Verze | Typ závislosti
--- | --- | --- | ---
Microsoft.Component.MSBuild | MSBuild | 16.5.29515.121 | Vyžadováno
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilátory C# a Visual Basic Roslyn | 16.0.28714.129 | Vyžadováno
Microsoft.VisualStudio.Component.TextTemplating | Transformace textových šablon | 16.0.28625.61 | Vyžadováno
Microsoft.VisualStudio.Component.VC.CoreIde | Základní funkce C++ | 16.10.31205.252 | Vyžadováno
Microsoft. VisualStudio. Component. VC. Redist. 14. nejnovější | Aktualizace C++ 2019 Redistributable | 16.5.29515.121 | Vyžadováno
Microsoft. VisualStudio. Component. NativeDesktop. Core | Základní funkce pro stolní počítače C++ | 16.2.29012.281 | Vyžadováno
Součást. Microsoft. VisualStudio. LiveShare | Live Share | 1.0.4062 | Doporučeno
Microsoft. VisualStudio. Component. Debugger. JustInTime | Ladicí program za běhu | 16.0.28517.75 | Doporučeno
Microsoft. VisualStudio. Component. Graphics. Tools | Ladicí program grafiky a Profiler GPU pro DirectX | 16.0.28625.61 | Doporučeno
Microsoft. VisualStudio. Component. IntelliCode | IntelliCode | 16.10.31305.154 | Doporučeno
Microsoft. VisualStudio. Component. JavaScript. TypeScript | Podpora jazyků JavaScript a TypeScript | 16.10.31303.231 | Doporučeno
Microsoft.VisualStudio.Component.NuGet | Správce balíčků NuGet | 16.1.28829.92 | Doporučeno
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# a Visual Basic | 16.10.31205.252 | Doporučeno
Microsoft.VisualStudio.Component.TypeScript.4.2 | TypeScript 4.2 SDK | 16.0.31303.231 | Doporučeno
Microsoft.VisualStudio.Component.VC.ASAN | C++ AddressSanitizer | 16.10.31205.252 | Doporučeno
Microsoft.VisualStudio.Component.VC.ATL | C++ ATL pro nejnovější nástroje sestavení v142 (x86 & x64) | 16.4.29313.120 | Doporučeno
Microsoft.VisualStudio.Component.VC.CMake.Project | Nástroje C++ CMake pro Windows | 16.3.29103.31 | Doporučeno
Microsoft.VisualStudio.Component.VC.DiagnosticTools | Nástroje pro profilaci jazyka C++ | 16.5.29515.121 | Doporučeno
Microsoft. VisualStudio. Component. VC. TestAdapterForBoostTest | Testovací adaptér pro zvýšení. test | 16.0.28517.75 | Doporučeno
Microsoft. VisualStudio. Component. VC. TestAdapterForGoogleTest | Testovací adaptér pro Google Test | 16.0.28517.75 | Doporučeno
Microsoft. VisualStudio. Component. VC. Tools. x86. x64 | MSVC V142-VS 2019 C++ x64/x86 Build Tools (nejnovější) | 16.10.31205.252 | Doporučeno
Microsoft. VisualStudio. Component. Windows10SDK. 19041 | Windows 10 SDK (10.0.19041.0) | 16.10.31205.252 | Doporučeno
Microsoft. VisualStudio. Component. WebToolsExtensions | Vývoj pro ASP.NET a web | 16.10.31205.180 | Doporučeno
Microsoft. VisualStudio. Component. WebToolsExtensions. CMake | Editor JSON | 16.10.31205.180 | Doporučeno
Component. IncrediBuild | IncrediBuild – zrychlení sestavení | 16.10.31205.252 | Volitelné
Component.IncredibuildMenu | IncrediBuildMenu | 1.5.0.13 | Volitelné
Microsoft.Component.VC.Runtime.UCRTSDK | Univerzální sada CRT SDK pro Windows | 16.0.28625.61 | Volitelné
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 | 16.0.28517.75 | Volitelné
Microsoft.Net.Component.4.8.SDK | .NET Framework 4.8 SDK | 16.4.29313.120 | Volitelné
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostika JavaScriptu | 16.0.28517.75 | Volitelné
Microsoft.VisualStudio.Component.VC.140 | MSVC v140 – nástroje sestavení C++ sady VS 2015 (v14.00) | 16.10.31205.252 | Volitelné
Microsoft.VisualStudio.Component.VC.ATLMFC | Knihovna MFC jazyka C++ pro nejnovější nástroje sestavení v142 (x86 & x64) | 16.4.29313.120 | Volitelné
Microsoft. VisualStudio. Component. VC. CLI. support | Podpora C++/CLI pro nástroje V142 Build (nejnovější) | 16.10.31205.252 | Volitelné
Microsoft. VisualStudio. Component. VC. LLVM. Clang | Kompilátor C++ Clang pro Windows (11.0.0) | 16.10.31205.252 | Volitelné
Microsoft. VisualStudio. Component. VC. LLVM. ClangToolset | C++ Clang – CL pro nástroje sestavení V142 (x64/x86) | 16.3.29207.166 | Volitelné
Microsoft. VisualStudio. Component. VC. Modules. x86. x64 | Moduly C++ pro nástroje V142 Build (x64/x86 – experimentální) | 16.0.28625.61 | Volitelné
Microsoft. VisualStudio. Component. VC. Tools. ARM64 | MSVC V142-VS 2019 C++ ARM64 Build Tools (nejnovější) | 16.10.31205.252 | Volitelné
Microsoft. VisualStudio. Component. VC. v141. x86. x64 | MSVC v141-VS 2017 C++ x64/x86 Build Tools (v 14.16) | 16.10.31205.252 | Volitelné
Microsoft. VisualStudio. Component. Windows10SDK. 16299 | Windows 10 SDK (10.0.16299.0) | 16.10.31205.252 | Volitelné
Microsoft.VisualStudio.Component.Windows10SDK.17134 | Windows 10 SDK (10.0.17134.0) | 16.10.31205.252 | Volitelné
Microsoft.VisualStudio.Component.Windows10SDK.17763 | Windows 10 SDK (10.0.17763.0) | 16.0.28517.75 | Volitelné
Microsoft.VisualStudio.Component.Windows10SDK.18362 | Windows 10 SDK (10.0.18362.0) | 16.1.28829.92 | Volitelné
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Llvm.Clang | Nástroje C++ Clang pro Windows (11.0.0 - x64/x86) | 16.10.31205.180 | Volitelné

## <a name="game-development-with-c"></a>Vývoj her v jazyce C++

**ID:** Microsoft.VisualStudio.Workload.NativeGame

**Popis:** Využijte plný výkon C++ k vytváření profesionálních her využívajících DirectX, Unreal nebo Cocos2d.

### <a name="components-included-by-this-workload"></a>Komponenty zahrnuté v této úlohu

ID komponenty | Name | Verze | Typ závislosti
--- | --- | --- | ---
Microsoft.VisualStudio.Component.VC.CoreIde | Základní funkce C++ | 16.10.31205.252 | Vyžadováno
Microsoft. VisualStudio. Component. VC. Redist. 14. nejnovější | Aktualizace C++ 2019 Redistributable | 16.5.29515.121 | Vyžadováno
Microsoft. VisualStudio. Component. VC. Tools. x86. x64 | MSVC V142-VS 2019 C++ x64/x86 Build Tools (nejnovější) | 16.10.31205.252 | Vyžadováno
Microsoft. VisualStudio. Component. Windows10SDK | Windows Universal C Runtime | 16.4.29409.204 | Vyžadováno
Microsoft. VisualStudio. Component. Graphics. Tools | Ladicí program grafiky a Profiler GPU pro DirectX | 16.0.28625.61 | Doporučeno
Microsoft. VisualStudio. Component. IntelliCode | IntelliCode | 16.10.31305.154 | Doporučeno
Microsoft. VisualStudio. Component. VC. ASAN | AddressSanitizer C++ | 16.10.31205.252 | Doporučeno
Microsoft. VisualStudio. Component. VC. DiagnosticTools | Nástroje pro profilaci jazyka C++ | 16.5.29515.121 | Doporučeno
Microsoft.VisualStudio.Component.Windows10SDK.19041 | Windows 10 SDK (10.0.19041.0) | 16.10.31205.252 | Doporučeno
Component.Android.NDK.R16B | Android NDK (R16B) | 16.10.31320.204 | Volitelné
Component.Android.SDK25.Private | Android SDK nastavení (úroveň 25 rozhraní API) (místní instalace pro vývoj mobilních aplikací pomocí jazyka C++) | 16.0.28625.61 | Volitelné
Component.Ant | Apache Ant (1.9.3) | 1.9.3.8 | Volitelné
Component.Cocos | Cocos | 16.0.28315.86 | Volitelné
Component.Incredibuild | Incredibuild – Zrychlení sestavení | 16.10.31205.252 | Volitelné
Component.IncredibuildMenu | IncrediBuildMenu | 1.5.0.13 | Volitelné
Component. MDD. Android | Vývojové nástroje C++ pro Android | 16.0.28517.75 | Volitelné
Component. OpenJDK | OpenJDK (distribuce Microsoft) | 16.10.31303.311 | Volitelné
Component. Unreal | Instalační program Unreal Engine | 16.1.28810.153 | Volitelné
Component. Unreal. Android | Podpora prostředí Android IDE pro modul Unreal | 16.1.28810.153 | Volitelné
Microsoft.Net. Component. 4.5.1. TargetingPack | Sada .NET Framework 4.5.1 targeting pack | 16.0.28517.75 | Volitelné
Microsoft.Net. Component. 4.5.2. TargetingPack | Sada .NET Framework 4.5.2 targeting pack | 16.0.28517.75 | Volitelné
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 | 16.0.28517.75 | Volitelné
Microsoft.Net.Component.4.6.2.TargetingPack | .NET Framework 4.6.2 | 16.0.28517.75 | Volitelné
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework 4.6 | 16.0.28517.75 | Volitelné
Microsoft.Net.Component.4.7.2.TargetingPack | .NET Framework 4.7.2 | 16.10.31205.252 | Volitelné
Microsoft.Net.Component.4.8.SDK | .NET Framework 4.8 SDK | 16.4.29313.120 | Volitelné
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 cílení pack | 16.0.28517.75 | Volitelné
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | .NET Framework 4.7.2 – vývojové nástroje | 16.3.29207.166 | Volitelné
Microsoft.Net. Component. TargetingPacks. Common | .NET Framework nástroje pro vývoj 4 – 4,6 | 16.0.28516.191 | Volitelné
Microsoft. VisualStudio. Component. NuGet. BuildTools | Cíle a úlohy sestavení NuGet | 16.1.28829.92 | Volitelné
Microsoft. VisualStudio. Component. Roslyn. Compiler | Kompilátory C# a Visual Basic Roslyn | 16.0.28714.129 | Volitelné
Microsoft. VisualStudio. Component. Roslyn. LanguageServices | C# a Visual Basic | 16.10.31205.252 | Volitelné
Microsoft. VisualStudio. Component. Windows10SDK. 16299 | Windows 10 SDK (10.0.16299.0) | 16.10.31205.252 | Volitelné
Microsoft. VisualStudio. Component. Windows10SDK. 17134 | Windows 10 SDK (10.0.17134.0) | 16.10.31205.252 | Volitelné
Microsoft. VisualStudio. Component. Windows10SDK. 17763 | Windows 10 SDK (10.0.17763.0) | 16.0.28517.75 | Volitelné
Microsoft.VisualStudio.Component.Windows10SDK.18362 | Windows 10 SDK (10.0.18362.0) | 16.1.28829.92 | Volitelné

## <a name="mobile-development-with-c"></a>Vývoj mobilních aplikací v jazyce C++

**ID:** Microsoft.VisualStudio.Workload.NativeMobile

**Popis:** Vytváření aplikací pro více platforem pro iOS, Android nebo Windows pomocí C++.

### <a name="components-included-by-this-workload"></a>Komponenty zahrnuté v této úlohu

ID komponenty | Name | Verze | Typ závislosti
--- | --- | --- | ---
Component.Android.SDK25.Private | Android SDK nastavení (úroveň 25 rozhraní API) (místní instalace pro vývoj mobilních aplikací pomocí jazyka C++) | 16.0.28625.61 | Vyžadováno
Component.OpenJDK | OpenJDK (distribuce Microsoftu) | 16.10.31303.311 | Vyžadováno
Microsoft.VisualStudio.Component.VC.CoreIde | Základní funkce jazyka C++ | 16.10.31205.252 | Vyžadováno
Component.Android.NDK.R16B | Android NDK (R16B) | 16.10.31320.204 | Doporučeno
Component. ANT | Apache Ant (1.9.3) | 1.9.3.8 | Doporučeno
Component. MDD. Android | Vývojové nástroje C++ pro Android | 16.0.28517.75 | Doporučeno
Microsoft. VisualStudio. Component. IntelliCode | IntelliCode | 16.10.31305.154 | Doporučeno
Component.Android.NDK.R16B_3264 | Android NDK (R16B) (32 bitů) | 16.10.31320.204 | Volitelné
Component. Google. Android. emulátor. API25. Private | Google Android Emulator (rozhraní API úrovně 25) (místní instalace) | 16.1.28810.153 | Volitelné
Component. modul HAXM. Private | Intel Hardware Accelerated Execution Manager (modul HAXM) (místní instalace) | 16.0.28528.71 | Volitelné
Component. IncrediBuild | IncrediBuild – zrychlení sestavení | 16.10.31205.252 | Volitelné
Component.IncredibuildMenu | IncrediBuildMenu | 1.5.0.13 | Volitelné
Component.MDD.IOS | Vývojové nástroje C++ pro iOS | 16.0.28517.75 | Volitelné

## <a name="net-cross-platform-development"></a>Vývoj pro .NET pro více platforem

**ID:** Microsoft.VisualStudio.Workload.NetCoreTools

**Popis:** Vytváření aplikací pro více platforem pomocí .NET, ASP.NET Core, HTML/JavaScript a kontejnerů, včetně podpory Dockeru

### <a name="components-included-by-this-workload"></a>Komponenty zahrnuté v této úlohu

ID komponenty | Name | Verze | Typ závislosti
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Služby jazyka Razor | 16.10.31205.252 | Vyžadováno
Component.Microsoft.Web.LibraryManager | Správce knihovny | 16.10.31205.180 | Vyžadováno
Component.Microsoft.WebTools.BrowserLink.WebLivePreview | Web Live Preview | 0.7.22.39845 | Vyžadováno
Microsoft. Component. MSBuild | MSBuild | 16.5.29515.121 | Vyžadováno
Microsoft. Component. ClickOnce. Publish | Publikování ClickOnce pro .NET  | 16.10.31303.231 | Vyžadováno
Microsoft.Net. Component. 4.5.2. TargetingPack | Sada .NET Framework 4.5.2 targeting pack | 16.0.28517.75 | Vyžadováno
Microsoft.Net. Component. 4.5. TargetingPack | Sada targeting pack .NET Framework 4,5 | 16.0.28517.75 | Vyžadováno
Microsoft.Net. Component. 4.6.1. TargetingPack | .NET Framework 4.6.1 targeting pack | 16.0.28517.75 | Vyžadováno
Microsoft.Net. Component. 4.7.2. TargetingPack | Sada targeting pack .NET Framework 4.7.2 | 16.10.31205.252 | Vyžadováno
Microsoft. NET. Component. 4.8. SDK | .NET Framework 4,8 SDK | 16.4.29313.120 | Vyžadováno
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | .NET Framework 4.7.2 – vývojové nástroje | 16.3.29207.166 | Vyžadováno
Microsoft.NetCore.Component.DevelopmentTools | Vývojové nástroje pro .NET | 16.10.31303.231 | Vyžadováno
Microsoft.NetCore.Component.Runtime.3.1 | .NET Core 3.1 Runtime (LTS) | 16.10.31320.204 | Vyžadováno
Microsoft.NetCore.Component.Runtime.5.0 | .NET 5.0 Runtime | 16.10.31320.204 | Vyžadováno
Microsoft.NetCore.Component.SDK | .NET SDK | 16.10.31320.204 | Vyžadováno
Microsoft.NetCore.Component.Web | Vývojové nástroje pro .NET | 16.10.31303.231 | Vyžadováno
Microsoft.VisualStudio.Component.Common.Azure.Tools | Nástroje pro připojení a publikování | 16.4.29409.204 | Vyžadováno
Microsoft.VisualStudio.Component.DockerTools | Kontejnerové vývojové nástroje | 16.4.29409.204 | Vyžadováno
Microsoft. VisualStudio. Component. FSharp | Podpora jazyka F # | 16.0.28315.86 | Vyžadováno
Microsoft. VisualStudio. Component. FSharp. Webtemplates | Podpora jazyka F # pro webové projekty | 16.3.29207.166 | Vyžadováno
Microsoft. VisualStudio. Component. IISExpress | IIS Express  | 16.0.28315.86 | Vyžadováno
Microsoft. VisualStudio. Component. JavaScript. Diagnostics | Diagnostika JavaScriptu | 16.0.28517.75 | Vyžadováno
Microsoft. VisualStudio. Component. JavaScript. TypeScript | Podpora jazyků JavaScript a TypeScript | 16.10.31303.231 | Vyžadováno
Microsoft. VisualStudio. Component. ManagedDesktop. Core | Jádro úlohy spravované plochy | 16.4.29318.151 | Vyžadováno
Microsoft.VisualStudio.Component.MSODBC.SQL | SQL Server ovladače ODBC | 16.0.28625.61 | Vyžadováno
Microsoft.VisualStudio.Component.MSSQL.CMDLnUtils | SQL Server nástroje příkazového řádku | 16.0.28707.177 | Vyžadováno
Microsoft.VisualStudio.Component.NuGet | Správce balíčků NuGet | 16.1.28829.92 | Vyžadováno
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilátory C# a Visual Basic Roslyn | 16.0.28714.129 | Vyžadováno
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# a Visual Basic | 16.10.31205.252 | Vyžadováno
Microsoft.VisualStudio.Component.SQL.ADAL | Modul runtime SQL ADAL | 16.0.28517.75 | Vyžadováno
Microsoft.VisualStudio.Component.SQL.CLR | Datové typy CLR pro SQL Server | 16.0.28315.86 | Vyžadováno
Microsoft. VisualStudio. Component. SQL. DataSources | Zdroje dat pro podporu SQL Server | 16.0.28315.86 | Vyžadováno
Microsoft. VisualStudio. Component. SQL. LocalDB. Runtime | SQL Server Express 2016 LocalDB | 16.0.28625.61 | Vyžadováno
Microsoft. VisualStudio. Component. SQL. SSDT | SQL Server Data Tools | 16.3.29207.166 | Vyžadováno
Microsoft. VisualStudio. Component. TextTemplating | Transformace textové šablony | 16.0.28625.61 | Vyžadováno
Microsoft. VisualStudio. Component. TypeScript. 4.2 | Sada TypeScript 4,2 SDK | 16.0.31303.231 | Vyžadováno
Microsoft. VisualStudio. Component. Web | Požadavky na ASP.NET a vývojové nástroje pro web | 16.10.31205.180 | Vyžadováno
Microsoft. VisualStudio. Component. WebToolsExtensions | Vývoj pro ASP.NET a web | 16.10.31205.180 | Vyžadováno
Component.Microsoft.VisualStudio.LiveShare | Live Share | 1.0.4062 | Doporučeno
Component.Microsoft.VisualStudio.Web.AzureFunctions | Azure WebJobs nástroje | 16.10.31205.252 | Doporučeno
Microsoft.VisualStudio.Component.AppInsights.Tools | Vývojářské analytické nástroje | 16.5.29515.121 | Doporučeno
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Nástroje pro vytváření v Azure | 16.0.28625.61 | Doporučeno
Microsoft.VisualStudio.Component.Azure.ClientLibs | Knihovny Azure pro .NET | 16.0.28315.86 | Doporučeno
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Azure Compute emulátoru | 16.10.31205.252 | Doporučeno
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Emulátor úložiště Azure | 16.4.29313.120 | Doporučeno
Microsoft.VisualStudio.Component.CloudExplorer | Průzkumník cloudu | 16.0.28625.61 | Doporučeno
Microsoft. VisualStudio. Component. Debugger. JustInTime | Ladicí program za běhu | 16.0.28517.75 | Doporučeno
Microsoft. VisualStudio. Component. DiagnosticTools | Nástroje pro profilaci .NET | 16.10.31205.252 | Doporučeno
Microsoft. VisualStudio. Component. DotNetModelBuilder | Tvůrce modelů ML.NET (Preview) | 16.10.31205.252 | Doporučeno
Microsoft. VisualStudio. Component. IntelliCode | IntelliCode | 16.10.31305.154 | Doporučeno
Microsoft. VisualStudio. Component. Web | ASP.NET a vývojové nástroje pro web | 16.10.31205.252 | Doporučeno
Microsoft. VisualStudio. Component. WebDeploy | Web Deploy | 16.0.28517.75 | Doporučeno
Microsoft. VisualStudio. Component. WslDebugging | Ladění .NET pomocí WSL 2 | 16.10.31303.231 | Doporučeno
Microsoft.VisualStudio.ComponentGroup.AzureFunctions | Azure WebJobs nástroje | 16.10.31205.180 | Doporučeno
Microsoft.VisualStudio.ComponentGroup.Web.CloudTools | Cloudové nástroje pro vývoj pro web | 16.10.31205.180 | Doporučeno
Microsoft.Net.Core.Component.SDK.2.1 | .NET Core 2.1 Runtime (LTS) | 16.10.31320.204 | Volitelné
Microsoft.VisualStudio.ComponentGroup.IISDevelopment | Podpora služby IIS pro dobu vývoje | 16.10.31205.180 | Volitelné
Microsoft.VisualStudio.ComponentGroup.MSIX.Packaging | Nástroje MSIX Packaging | 16.10.31205.180 | Volitelné

## <a name="mobile-development-with-net"></a>Vývoj mobilních aplikací pomocí .NET

**ID:** Microsoft.VisualStudio.Workload.NetCrossPlat

**Popis:** Vytváření aplikací pro více platforem pro iOS, Android nebo Windows pomocí Xamarinu

### <a name="components-included-by-this-workload"></a>Komponenty zahrnuté v této úlohu

ID komponenty | Name | Verze | Typ závislosti
--- | --- | --- | ---
Component. OpenJDK | OpenJDK (distribuce Microsoft) | 16.10.31303.311 | Vyžadováno
Komponenta. Xamarin | Xamarin | 16.10.31205.252 | Vyžadováno
Komponenta. Xamarin. RemotedSimulator | Vzdálený simulátor Xamarin | 16.10.31205.252 | Vyžadováno
Microsoft. Component. MSBuild | MSBuild | 16.5.29515.121 | Vyžadováno
Microsoft. Component. ClickOnce. Publish | Publikování ClickOnce pro .NET  | 16.10.31303.231 | Vyžadováno
Microsoft.Net. Component. 4.6.1. TargetingPack | .NET Framework 4.6.1 targeting pack | 16.0.28517.75 | Vyžadováno
Microsoft.Net. Component. 4.7.2. TargetingPack | Sada targeting pack .NET Framework 4.7.2 | 16.10.31205.252 | Vyžadováno
Microsoft.Net.Component.4.8.SDK | .NET Framework 4.8 SDK | 16.4.29313.120 | Vyžadováno
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | .NET Framework 4.7.2 – vývojové nástroje | 16.3.29207.166 | Vyžadováno
Microsoft.NetCore.Component.DevelopmentTools | Vývojové nástroje pro .NET | 16.10.31303.231 | Vyžadováno
Microsoft.NetCore.Component.Runtime.3.1 | .NET Core 3.1 Runtime (LTS) | 16.10.31320.204 | Vyžadováno
Microsoft.NetCore.Component.Runtime.5.0 | .NET 5.0 Runtime | 16.10.31320.204 | Vyžadováno
Microsoft.NetCore.Component.SDK | .NET SDK | 16.10.31320.204 | Vyžadováno
Microsoft.VisualStudio.Component.FSharp | Podpora jazyka F# | 16.0.28315.86 | Vyžadováno
Microsoft. VisualStudio. Component. Merq | Běžné interní nástroje Xamarin | 16.2.29012.281 | Vyžadováno
Microsoft. VisualStudio. Component. MonoDebugger | Ladicí program mono | 16.0.28517.75 | Vyžadováno
Microsoft. VisualStudio. Component. NuGet | Správce balíčků NuGet | 16.1.28829.92 | Vyžadováno
Microsoft. VisualStudio. Component. Roslyn. Compiler | Kompilátory C# a Visual Basic Roslyn | 16.0.28714.129 | Vyžadováno
Microsoft. VisualStudio. Component. Roslyn. LanguageServices | C# a Visual Basic | 16.10.31205.252 | Vyžadováno
Microsoft. VisualStudio. Component. WebToolsExtensions. TemplateEngine | ASP.NET šablonování Engine | 16.10.31205.180 | Vyžadováno
Komponenta. Android. SDK30 | Instalace Android SDK (úroveň rozhraní API 30) | 16.10.31205.252 | Doporučeno
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 16.10.31305.154 | Doporučeno

## <a name="aspnet-and-web-development"></a>Vývoj pro ASP.NET a web

**ID:** Microsoft.VisualStudio.Workload.NetWeb

**Popis:** Vytvářete webové aplikace pomocí ASP.NET Core, ASP.NET, HTML/JavaScript a Containers, včetně podpory Dockeru.

### <a name="components-included-by-this-workload"></a>Komponenty zahrnuté v této úlohu

ID komponenty | Name | Verze | Typ závislosti
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Služby jazyka Razor | 16.10.31205.252 | Vyžadováno
Component.Microsoft.Web.LibraryManager | Správce knihovny | 16.10.31205.180 | Vyžadováno
Component.Microsoft.WebTools.BrowserLink.WebLivePreview | Web Live Preview | 0.7.22.39845 | Vyžadováno
Microsoft.Component.MSBuild | MSBuild | 16.5.29515.121 | Vyžadováno
Microsoft.ComponentGroup.ClickOnce.Publish | Publikování ClickOnce pro .NET  | 16.10.31303.231 | Vyžadováno
Microsoft.Net. Component. 4.5.2. TargetingPack | Sada .NET Framework 4.5.2 targeting pack | 16.0.28517.75 | Vyžadováno
Microsoft.Net. Component. 4.5. TargetingPack | Sada targeting pack .NET Framework 4,5 | 16.0.28517.75 | Vyžadováno
Microsoft.Net. Component. 4.6.1. TargetingPack | .NET Framework 4.6.1 targeting pack | 16.0.28517.75 | Vyžadováno
Microsoft.Net. Component. 4.7.2. TargetingPack | Sada targeting pack .NET Framework 4.7.2 | 16.10.31205.252 | Vyžadováno
Microsoft. NET. Component. 4.8. SDK | .NET Framework 4,8 SDK | 16.4.29313.120 | Vyžadováno
Microsoft.Net. Component. DevelopmentPrerequisites | Vývojové nástroje .NET Framework 4.7.2 | 16.3.29207.166 | Vyžadováno
Microsoft. NetCore. Component. DevelopmentTools | Vývojové nástroje .NET | 16.10.31303.231 | Vyžadováno
Microsoft.NetCore.Component.Runtime.3.1 | .NET Core 3.1 Runtime (LTS) | 16.10.31320.204 | Vyžadováno
Microsoft.NetCore.Component.Runtime.5.0 | .NET 5.0 Runtime | 16.10.31320.204 | Vyžadováno
Microsoft.NetCore.Component.SDK | .NET SDK | 16.10.31320.204 | Vyžadováno
Microsoft.NetCore.Component.Web | Vývojové nástroje pro .NET | 16.10.31303.231 | Vyžadováno
Microsoft.VisualStudio.Component.Common.Azure.Tools | Nástroje pro připojení a publikování | 16.4.29409.204 | Vyžadováno
Microsoft.VisualStudio.Component.DockerTools | Kontejnerové vývojové nástroje | 16.4.29409.204 | Vyžadováno
Microsoft.VisualStudio.Component.FSharp | Podpora jazyka F# | 16.0.28315.86 | Vyžadováno
Microsoft. VisualStudio. Component. FSharp. Webtemplates | Podpora jazyka F # pro webové projekty | 16.3.29207.166 | Vyžadováno
Microsoft. VisualStudio. Component. IISExpress | IIS Express  | 16.0.28315.86 | Vyžadováno
Microsoft. VisualStudio. Component. JavaScript. Diagnostics | Diagnostika JavaScriptu | 16.0.28517.75 | Vyžadováno
Microsoft. VisualStudio. Component. JavaScript. TypeScript | Podpora jazyků JavaScript a TypeScript | 16.10.31303.231 | Vyžadováno
Microsoft. VisualStudio. Component. ManagedDesktop. Core | Jádro úlohy spravované plochy | 16.4.29318.151 | Vyžadováno
Microsoft. VisualStudio. Component. MSODBC. SQL | SQL Server ovladač ODBC | 16.0.28625.61 | Vyžadováno
Microsoft. VisualStudio. Component. MSSQL. CMDLnUtils | SQL Server nástroje příkazového řádku | 16.0.28707.177 | Vyžadováno
Microsoft.VisualStudio.Component.NuGet | Správce balíčků NuGet | 16.1.28829.92 | Vyžadováno
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilátory C# a Visual Basic Roslyn | 16.0.28714.129 | Vyžadováno
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# a Visual Basic | 16.10.31205.252 | Vyžadováno
Microsoft.VisualStudio.Component.SQL.ADAL | Modul runtime SQL ADAL | 16.0.28517.75 | Vyžadováno
Microsoft.VisualStudio.Component.SQL.CLR | Datové typy CLR pro SQL Server | 16.0.28315.86 | Vyžadováno
Microsoft.VisualStudio.Component.SQL.DataSources | Zdroje dat pro podporu SQL Server dat | 16.0.28315.86 | Vyžadováno
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 16.0.28625.61 | Vyžadováno
Microsoft. VisualStudio. Component. SQL. SSDT | SQL Server Data Tools | 16.3.29207.166 | Vyžadováno
Microsoft. VisualStudio. Component. TextTemplating | Transformace textové šablony | 16.0.28625.61 | Vyžadováno
Microsoft. VisualStudio. Component. TypeScript. 4.2 | Sada TypeScript 4,2 SDK | 16.0.31303.231 | Vyžadováno
Microsoft. VisualStudio. Component. Web | ASP.NET a vývojové nástroje pro web | 16.10.31205.252 | Vyžadováno
Microsoft. VisualStudio. Component. Web | Požadavky na ASP.NET a vývojové nástroje pro web | 16.10.31205.180 | Vyžadováno
Microsoft. VisualStudio. Component. Web. Client | ASP.NET a vývojové nástroje pro web | 16.10.31205.180 | Vyžadováno
Microsoft. VisualStudio. Component. WebToolsExtensions | Vývoj pro ASP.NET a web | 16.10.31205.180 | Vyžadováno
Component.Microsoft.VisualStudio.LiveShare | Live Share | 1.0.4062 | Doporučeno
Component.Microsoft.VisualStudio.Web.AzureFunctions | Azure WebJobs nástroje | 16.10.31205.252 | Doporučeno
Microsoft.Net.Component.4.5.1.TargetingPack | .NET Framework 4.5.1 | 16.0.28517.75 | Doporučeno
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework 4.6 | 16.0.28517.75 | Doporučeno
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 cílení pack | 16.0.28517.75 | Doporučeno
Microsoft.Net.ComponentGroup.TargetingPacks.Common | .NET Framework 4–4.6 – vývojové nástroje | 16.0.28516.191 | Doporučeno
Microsoft.VisualStudio.Component.AppInsights.Tools | Vývojářské analytické nástroje | 16.5.29515.121 | Doporučeno
Microsoft. VisualStudio. Component. AspNet45 | Pokročilé funkce ASP.NET | 16.10.31205.252 | Doporučeno
Microsoft. VisualStudio. Component. Azure. AuthoringTools | Nástroje pro tvorbu Azure | 16.0.28625.61 | Doporučeno
Microsoft. VisualStudio. Component. Azure. ClientLibs | Knihovny Azure pro .NET | 16.0.28315.86 | Doporučeno
Microsoft. VisualStudio. Component. Azure. Compute. emulátor | Emulátor služby COMPUTE Azure | 16.10.31205.252 | Doporučeno
Microsoft. VisualStudio. Component. Azure. Storage. emulátor | Emulátor úložiště Azure | 16.4.29313.120 | Doporučeno
Microsoft. VisualStudio. Component. Průzkumník cloudu | Průzkumník cloudu | 16.0.28625.61 | Doporučeno
Microsoft. VisualStudio. Component. Debugger. JustInTime | Ladicí program za běhu | 16.0.28517.75 | Doporučeno
Microsoft. VisualStudio. Component. DiagnosticTools | Nástroje pro profilaci .NET | 16.10.31205.252 | Doporučeno
Microsoft.VisualStudio.Component.EntityFramework | Entity Framework 6 nástrojů | 16.0.28315.86 | Doporučeno
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 16.10.31305.154 | Doporučeno
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 16.0.28517.75 | Doporučeno
Microsoft.VisualStudio.Component.WslDebugging | Ladění .NET s WSL 2 | 16.10.31303.231 | Doporučeno
Microsoft.VisualStudio.ComponentGroup.AzureFunctions | Azure WebJobs nástroje | 16.10.31205.180 | Doporučeno
Microsoft.VisualStudio.ComponentGroup.Web.CloudTools | Cloudové nástroje pro vývoj pro web | 16.10.31205.180 | Doporučeno
Microsoft.Net.Component.4.6.2.TargetingPack | .NET Framework 4.6.2 | 16.0.28517.75 | Volitelné
Microsoft.Net. Component. 4.7.1. TargetingPack | Sada targeting pack .NET Framework 4.7.1 | 16.10.31205.252 | Volitelné
Microsoft.Net. Component. 4.7. TargetingPack | Sada targeting pack .NET Framework 4,7 | 16.10.31205.252 | Volitelné
Microsoft.Net. Component. 4.8. TargetingPack | Sada targeting pack .NET Framework 4,8 | 16.4.29313.120 | Volitelné
Microsoft.Net. Component.. 4.6.1. DeveloperTools | Vývojové nástroje .NET Framework 4.6.1 | 16.3.29207.166 | Volitelné
Microsoft.Net. Component. 4.6.2. DeveloperTools | Vývojové nástroje .NET Framework 4.6.2 | 16.3.29207.166 | Volitelné
Microsoft.Net. Component. 4.7.1. DeveloperTools | Vývojové nástroje .NET Framework 4.7.1 | 16.3.29207.166 | Volitelné
Microsoft.Net. Component.. 4.7. DeveloperTools | .NET Framework 4.7 – vývojové nástroje | 16.3.29207.166 | Volitelné
Microsoft.Net.ComponentGroup.4.8.DeveloperTools | .NET Framework 4.8 – vývojové nástroje | 16.4.29318.151 | Volitelné
Microsoft.Net.Core.Component.SDK.2.1 | .NET Core 2.1 Runtime (LTS) | 16.10.31320.204 | Volitelné
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | 16.0.28625.61 | Volitelné
Microsoft.VisualStudio.ComponentGroup.AdditionalWebProjectTemplates | Další šablony projektů (předchozí verze) | 16.10.31205.180 | Volitelné
Microsoft.VisualStudio.ComponentGroup.IISDevelopment | Podpora služby IIS pro dobu vývoje | 16.10.31205.180 | Volitelné

## <a name="nodejs-development"></a>Node.js vývoje

**ID:** Microsoft.VisualStudio.Workload.Node

**Popis:** Sestavovat škálovatelné síťové aplikace pomocí Node.js, asynchronního modulu runtime JavaScriptu řízeného událostmi. 

### <a name="components-included-by-this-workload"></a>Komponenty zahrnuté v této úlohu

ID součásti | Name | Verze | Typ závislosti
--- | --- | --- | ---
Microsoft. VisualStudio. Component. JavaScript. Diagnostics | Diagnostika JavaScriptu | 16.0.28517.75 | Vyžadováno
Microsoft. VisualStudio. Component. JavaScript. TypeScript | Podpora jazyků JavaScript a TypeScript | 16.10.31303.231 | Vyžadováno
Microsoft. VisualStudio. Component. Node. Tools | Vývojové nástroje Node.js | 16.5.29515.121 | Vyžadováno
Microsoft. VisualStudio. Component. TypeScript. 4.2 | Sada TypeScript 4,2 SDK | 16.0.31303.231 | Vyžadováno
Microsoft. VisualStudio. Component. WebToolsExtensions | Vývoj pro ASP.NET a web | 16.10.31205.180 | Vyžadováno
Součást. Microsoft. VisualStudio. LiveShare | Live Share | 1.0.4062 | Doporučeno
Microsoft. VisualStudio. Component. Debugger. JustInTime | Ladicí program za běhu | 16.0.28517.75 | Doporučeno
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 16.10.31305.154 | Doporučeno
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilátory C# a Visual Basic Roslyn | 16.0.28714.129 | Doporučeno
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# a Visual Basic | 16.10.31205.252 | Doporučeno
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 16.0.28517.75 | Doporučeno
Microsoft.VisualStudio.Component.AppInsights.Tools | Vývojářské analytické nástroje | 16.5.29515.121 | Volitelné
Microsoft.VisualStudio.Component.Common.Azure.Tools | Nástroje pro připojení a publikování | 16.4.29409.204 | Volitelné
Microsoft.VisualStudio.Component.VC.CoreIde | Základní funkce jazyka C++ | 16.10.31205.252 | Volitelné
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | MSVC V142-VS 2019 C++ x64/x86 Build Tools (nejnovější) | 16.10.31205.252 | Volitelné

## <a name="officesharepoint-development"></a>Vývoj pro Office/SharePoint

**ID:** Microsoft. VisualStudio. úlohy. Office

**Popis:** Vytvářejte doplňky pro Office a SharePoint, řešení pro SharePoint a doplňky VSTO pomocí C#, VB a JavaScriptu.

### <a name="components-included-by-this-workload"></a>Součásti zahrnuté v tomto zatížení

ID součásti | Name | Verze | Typ závislosti
--- | --- | --- | ---
Součást. Microsoft. VisualStudio. RazorExtension | Jazykové služby Razor | 16.10.31205.252 | Vyžadováno
Součást. Microsoft. Web. LibraryManager | Správce knihovny | 16.10.31205.180 | Vyžadováno
Komponenta. Microsoft. WebTools. BrowserLink. WebLivePreview | Web Live Preview | 0.7.22.39845 | Vyžadováno
Microsoft. Component. MSBuild | MSBuild | 16.5.29515.121 | Vyžadováno
Microsoft.Net. Component. 4.5.2. TargetingPack | Sada .NET Framework 4.5.2 targeting pack | 16.0.28517.75 | Vyžadováno
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 | 16.0.28517.75 | Vyžadováno
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 | 16.0.28517.75 | Vyžadováno
Microsoft.Net.Component.4.7.2.TargetingPack | .NET Framework 4.7.2 | 16.10.31205.252 | Vyžadováno
Microsoft.Net.Component.4.8.SDK | .NET Framework 4.8 SDK | 16.4.29313.120 | Vyžadováno
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 cílení pack | 16.0.28517.75 | Vyžadováno
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | .NET Framework 4.7.2 – vývojové nástroje | 16.3.29207.166 | Vyžadováno
Microsoft.NetCore.Component.Runtime.3.1 | Runtime .NET Core 3,1 (LTS) | 16.10.31320.204 | Vyžadováno
Microsoft. NetCore. Component. Runtime. 5.0 | .NET 5,0 – modul runtime | 16.10.31320.204 | Vyžadováno
Microsoft. NetCore. Component. SDK | .NET SDK | 16.10.31320.204 | Vyžadováno
Microsoft. VisualStudio. Component. AppInsights. Tools | Vývojářské analytické nástroje | 16.5.29515.121 | Vyžadováno
Microsoft. VisualStudio. Component. Common. Azure. Tools | Nástroje pro připojení a publikování | 16.4.29409.204 | Vyžadováno
Microsoft.VisualStudio.Component.DockerTools | Kontejnerové vývojové nástroje | 16.4.29409.204 | Vyžadováno
Microsoft. VisualStudio. Component. IISExpress | IIS Express  | 16.0.28315.86 | Vyžadováno
Microsoft. VisualStudio. Component. JavaScript. Diagnostics | Diagnostika JavaScriptu | 16.0.28517.75 | Vyžadováno
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Podpora jazyků JavaScript a TypeScript | 16.10.31303.231 | Vyžadováno
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Jádro úloh spravovaného desktopového prostředí | 16.4.29318.151 | Vyžadováno
Microsoft.VisualStudio.Component.ManagedDesktop.Prerequisites | Nástroje pro vývoj desktopových aplikací .NET | 16.10.31205.180 | Vyžadováno
Microsoft.VisualStudio.Component.MSODBC.SQL | SQL Server ovladače ODBC | 16.0.28625.61 | Vyžadováno
Microsoft.VisualStudio.Component.MSSQL.CMDLnUtils | SQL Server nástroje příkazového řádku | 16.0.28707.177 | Vyžadováno
Microsoft.VisualStudio.Component.NuGet | Správce balíčků NuGet | 16.1.28829.92 | Vyžadováno
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilátory C# a Visual Basic Roslyn | 16.0.28714.129 | Vyžadováno
Microsoft. VisualStudio. Component. Roslyn. LanguageServices | C# a Visual Basic | 16.10.31205.252 | Vyžadováno
Microsoft. VisualStudio. Component. SharePoint. Tools | Office Developer Tools for Visual Studio | 16.4.29409.204 | Vyžadováno
Microsoft. VisualStudio. Component. SQL. ADAL | Modul runtime SQL ADAL | 16.0.28517.75 | Vyžadováno
Microsoft. VisualStudio. Component. SQL. CLR | Datové typy CLR pro SQL Server | 16.0.28315.86 | Vyžadováno
Microsoft. VisualStudio. Component. SQL. DataSources | Zdroje dat pro podporu SQL Server | 16.0.28315.86 | Vyžadováno
Microsoft. VisualStudio. Component. SQL. LocalDB. Runtime | SQL Server Express 2016 LocalDB | 16.0.28625.61 | Vyžadováno
Microsoft. VisualStudio. Component. SQL. SSDT | SQL Server Data Tools | 16.3.29207.166 | Vyžadováno
Microsoft.VisualStudio.Component.TextTemplating | Transformace textových šablon | 16.0.28625.61 | Vyžadováno
Microsoft.VisualStudio.Component.TypeScript.4.2 | TypeScript 4.2 SDK | 16.0.31303.231 | Vyžadováno
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | 16.0.28625.61 | Vyžadováno
Microsoft.VisualStudio.Component.Web | ASP.NET a webové vývojové nástroje | 16.10.31205.252 | Vyžadováno
Microsoft.VisualStudio.Component.Workflow | Windows Workflow Foundation | 16.0.28315.86 | Vyžadováno
Microsoft.VisualStudio.ComponentGroup.Web | Požadavky ASP.NET a webových vývojových nástrojů | 16.10.31205.180 | Vyžadováno
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Vývoj pro ASP.NET a web | 16.10.31205.180 | Vyžadováno
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 16.10.31305.154 | Doporučeno
Microsoft. VisualStudio. Component. TeamOffice | Visual Studio Tools for Office (VSTO) | 16.4.29409.204 | Doporučeno
Microsoft. VisualStudio. Component. WebDeploy | Web Deploy | 16.0.28517.75 | Doporučeno
Microsoft.Net. Component. 4.6.2. TargetingPack | Sada targeting pack .NET Framework 4.6.2 | 16.0.28517.75 | Volitelné
Microsoft.Net. Component. 4.7.1. TargetingPack | Sada targeting pack .NET Framework 4.7.1 | 16.10.31205.252 | Volitelné
Microsoft.Net. Component. 4.7. TargetingPack | Sada targeting pack .NET Framework 4,7 | 16.10.31205.252 | Volitelné
Microsoft.Net. Component. 4.8. TargetingPack | Sada targeting pack .NET Framework 4,8 | 16.4.29313.120 | Volitelné
Microsoft.Net. Component.. 4.6.1. DeveloperTools | Vývojové nástroje .NET Framework 4.6.1 | 16.3.29207.166 | Volitelné
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | .NET Framework 4.6.2 | 16.3.29207.166 | Volitelné
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | .NET Framework 4.7.1 | 16.3.29207.166 | Volitelné
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | .NET Framework 4.7 – vývojové nástroje | 16.3.29207.166 | Volitelné
Microsoft.Net.ComponentGroup.4.8.DeveloperTools | .NET Framework 4.8 – vývojové nástroje | 16.4.29318.151 | Volitelné
Microsoft.VisualStudio.ComponentGroup.Sharepoint.WIF | Windows Identity Foundation 3.5 | 16.0.28621.142 | Volitelné

## <a name="python-development"></a>Vývoj v Pythonu

**ID:** Microsoft.VisualStudio.Workload.Python

**Popis:** Úpravy, ladění, interaktivní vývoj a řízení zdrojového kódu pro Python.

### <a name="components-included-by-this-workload"></a>Komponenty zahrnuté v této úlohu

ID komponenty | Name | Verze | Typ závislosti
--- | --- | --- | ---
Microsoft. Component. PythonTools | Podpora jazyka Python | 16.10.31313.127 | Vyžadováno
Component. CPython3. x64 | Python 3 64 – bit (3.7.8) | 3.7.8 | Doporučeno
Component. CPython2. x64 | Python 2 64 – bit (2.7.18) (mimo podporu) | 2.7.18.2 | Volitelné
Component. CPython2. x86 | Python 2 32 – bit (2.7.18) (mimo podporu) | 2.7.18.2 | Volitelné
Component. CPython3. x86 | Python 3 32 – bit (3.7.8) | 3.7.8 | Volitelné
Součást. Microsoft. VisualStudio. LiveShare | Live Share | 1.0.4062 | Volitelné
Součást. Microsoft. VisualStudio. RazorExtension | Jazykové služby Razor | 16.10.31205.252 | Volitelné
Component.Microsoft.Web.LibraryManager | Správce knihovny | 16.10.31205.180 | Volitelné
Component.Microsoft.WebTools.BrowserLink.WebLivePreview | Web Live Preview | 0.7.22.39845 | Volitelné
Microsoft.Component.IronPython | IronPython (bez podpory) | 16.10.31303.231 | Volitelné
Microsoft.Component.MSBuild | MSBuild | 16.5.29515.121 | Volitelné
Microsoft.Component.PythonTools.Minicondax64 | Miniconda Pythonu (bez podpory) | 16.10.31313.127 | Volitelné
Microsoft.Component.PythonTools.Web | Webová podpora Pythonu | 16.10.31205.252 | Volitelné
Microsoft.ComponentGroup.PythonTools.NativeDevelopment | Nativní vývojové nástroje pythonu | 16.10.31205.180 | Volitelné
Microsoft.Net.Component.4.5.2.TargetingPack | Sada .NET Framework 4.5.2 targeting pack | 16.0.28517.75 | Volitelné
Microsoft.Net. Component. 4.5. TargetingPack | Sada targeting pack .NET Framework 4,5 | 16.0.28517.75 | Volitelné
Microsoft.Net. Component. 4.7.2. TargetingPack | Sada targeting pack .NET Framework 4.7.2 | 16.10.31205.252 | Volitelné
Microsoft. NET. Component. 4.8. SDK | .NET Framework 4,8 SDK | 16.4.29313.120 | Volitelné
Microsoft.Net. Component. DevelopmentPrerequisites | Vývojové nástroje .NET Framework 4.7.2 | 16.3.29207.166 | Volitelné
Microsoft. NetCore. Component. Runtime. 3.1 | Runtime .NET Core 3,1 (LTS) | 16.10.31320.204 | Volitelné
Microsoft. NetCore. Component. Runtime. 5.0 | .NET 5,0 – modul runtime | 16.10.31320.204 | Volitelné
Microsoft.NetCore.Component.SDK | .NET SDK | 16.10.31320.204 | Volitelné
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Nástroje pro vytváření v Azure | 16.0.28625.61 | Volitelné
Microsoft.VisualStudio.Component.Azure.ClientLibs | Knihovny Azure pro .NET | 16.0.28315.86 | Volitelné
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Azure Compute emulátoru | 16.10.31205.252 | Volitelné
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Emulátor úložiště Azure | 16.4.29313.120 | Volitelné
Microsoft.VisualStudio.Component.Azure.Waverton | Azure Cloud Services core tools | 16.10.31205.252 | Volitelné
Microsoft.VisualStudio.Component.Azure.Waverton.BuildTools | Azure Cloud Services sestavovací nástroje | 16.10.31205.252 | Volitelné
Microsoft.VisualStudio.Component.Common.Azure.Tools | Nástroje pro připojení a publikování | 16.4.29409.204 | Volitelné
Microsoft. VisualStudio. Component. Debugger. JustInTime | Ladicí program za běhu | 16.0.28517.75 | Volitelné
Microsoft.VisualStudio.Component.DockerTools | Kontejnerové vývojové nástroje | 16.4.29409.204 | Volitelné
Microsoft. VisualStudio. Component. Graphics. Tools | Ladicí program grafiky a Profiler GPU pro DirectX | 16.0.28625.61 | Volitelné
Microsoft. VisualStudio. Component. IISExpress | IIS Express  | 16.0.28315.86 | Volitelné
Microsoft. VisualStudio. Component. JavaScript. Diagnostics | Diagnostika JavaScriptu | 16.0.28517.75 | Volitelné
Microsoft. VisualStudio. Component. JavaScript. TypeScript | Podpora jazyků JavaScript a TypeScript | 16.10.31303.231 | Volitelné
Microsoft. VisualStudio. Component. ManagedDesktop. Core | Jádro úloh spravovaného desktopového prostředí | 16.4.29318.151 | Volitelné
Microsoft.VisualStudio.Component.MSODBC.SQL | SQL Server ovladače ODBC | 16.0.28625.61 | Volitelné
Microsoft.VisualStudio.Component.MSSQL.CMDLnUtils | SQL Server nástroje příkazového řádku | 16.0.28707.177 | Volitelné
Microsoft.VisualStudio.Component.NuGet | Správce balíčků NuGet | 16.1.28829.92 | Volitelné
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilátory C# a Visual Basic Roslyn | 16.0.28714.129 | Volitelné
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# a Visual Basic | 16.10.31205.252 | Volitelné
Microsoft.VisualStudio.Component.SQL.ADAL | Modul runtime SQL ADAL | 16.0.28517.75 | Volitelné
Microsoft.VisualStudio.Component.SQL.CLR | Datové typy CLR pro SQL Server | 16.0.28315.86 | Volitelné
Microsoft. VisualStudio. Component. SQL. DataSources | Zdroje dat pro podporu SQL Server | 16.0.28315.86 | Volitelné
Microsoft. VisualStudio. Component. SQL. LocalDB. Runtime | SQL Server Express 2016 LocalDB | 16.0.28625.61 | Volitelné
Microsoft. VisualStudio. Component. SQL. SSDT | SQL Server Data Tools | 16.3.29207.166 | Volitelné
Microsoft. VisualStudio. Component. TextTemplating | Transformace textové šablony | 16.0.28625.61 | Volitelné
Microsoft. VisualStudio. Component. TypeScript. 4.2 | Sada TypeScript 4,2 SDK | 16.0.31303.231 | Volitelné
Microsoft. VisualStudio. Component. VC. CoreIde | Základní funkce C++ | 16.10.31205.252 | Volitelné
Microsoft. VisualStudio. Component. VC. DiagnosticTools | Nástroje pro profilaci jazyka C++ | 16.5.29515.121 | Volitelné
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | MSVC v142 – buildovací nástroje VS 2019 C++ x64/x86 (nejnovější) | 16.10.31205.252 | Volitelné
Microsoft.VisualStudio.Component.Web | ASP.NET a webové vývojové nástroje | 16.10.31205.252 | Volitelné
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 16.0.28517.75 | Volitelné
Microsoft.VisualStudio.Component.Windows10SDK | Windows Universal C Runtime | 16.4.29409.204 | Volitelné
Microsoft.VisualStudio.Component.Windows10SDK.19041 | Windows 10 SDK (10.0.19041.0) | 16.10.31205.252 | Volitelné
Microsoft.VisualStudio.ComponentGroup.Web | Požadavky ASP.NET a webových vývojových nástrojů | 16.10.31205.180 | Volitelné
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Vývoj pro ASP.NET a web | 16.10.31205.180 | Volitelné

## <a name="universal-windows-platform-development"></a>Vývoj Univerzální platforma Windows

**ID:** Microsoft. VisualStudio. úlohu. Universal

**Popis:** Vytvářejte aplikace pro Univerzální platforma Windows pomocí jazyka C#, VB nebo volitelně C++.

### <a name="components-included-by-this-workload"></a>Součásti zahrnuté v tomto zatížení

ID součásti | Name | Verze | Typ závislosti
--- | --- | --- | ---
Microsoft. Component. NetFX. Native | .NET Native | 16.5.29515.121 | Vyžadováno
Microsoft. Components. Blend | Blend for Visual Studio | 16.0.28315.86 | Vyžadováno
Microsoft.Net. Component. 4.5. TargetingPack | Sada targeting pack .NET Framework 4,5 | 16.0.28517.75 | Vyžadováno
Microsoft. NetCore. Component. Runtime. 3.1 | Runtime .NET Core 3,1 (LTS) | 16.10.31320.204 | Vyžadováno
Microsoft. NetCore. Component. Runtime. 5.0 | .NET 5,0 – modul runtime | 16.10.31320.204 | Vyžadováno
Microsoft.NetCore.Component.SDK | .NET SDK | 16.10.31320.204 | Vyžadováno
Microsoft.VisualStudio.Component.AppInsights.Tools | Vývojářské analytické nástroje | 16.5.29515.121 | Vyžadováno
Microsoft.VisualStudio.Component.DiagnosticTools | Nástroje pro profilaci .NET | 16.10.31205.252 | Vyžadováno
Microsoft.VisualStudio.Component.Graphics | Editory obrázků a 3D model souborů | 16.10.31205.252 | Vyžadováno
Microsoft.VisualStudio.Component.NuGet | Správce balíčků NuGet | 16.1.28829.92 | Vyžadováno
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilátory C# a Visual Basic Roslyn | 16.0.28714.129 | Vyžadováno
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# a Visual Basic | 16.10.31205.252 | Vyžadováno
Microsoft.VisualStudio.Component.SQL.CLR | Datové typy CLR pro SQL Server | 16.0.28315.86 | Vyžadováno
Microsoft. VisualStudio. Component. Windows10SDK. 19041 | Windows 10 SDK (10.0.19041.0) | 16.10.31205.252 | Vyžadováno
Microsoft.VisualStudio.ComponentGroup.MSIX. balení | Nástroje pro vytváření balíčků MSIX | 16.10.31205.180 | Vyžadováno
Microsoft. VisualStudio. Component. UWP. NetCoreAndStandard | .NET Native a .NET Standard | 16.3.29102.218 | Vyžadováno
Microsoft. VisualStudio. Component. UWP. support | Nástroje Univerzální platforma Windows | 16.10.31205.180 | Vyžadováno
Microsoft. VisualStudio. Component. UWP. Xamarin | Univerzální platforma Windows Tools for Xamarin | 16.10.31205.180 | Vyžadováno
Microsoft. VisualStudio. Component. IntelliCode | IntelliCode | 16.10.31305.154 | Doporučeno
Microsoft. NET. Component. 4.8. SDK | .NET Framework 4.8 SDK | 16.4.29313.120 | Volitelné
Microsoft.VisualStudio.Component.Graphics.Tools | Ladicí program grafiky a profiler GPU pro DirectX | 16.0.28625.61 | Volitelné
Microsoft.VisualStudio.Component.UWP.VC.ARM64 | Podpora Univerzální platforma Windows C++ pro nástroje sestavení v142 (ARM64) | 16.3.29207.166 | Volitelné
Microsoft.VisualStudio.Component.UWP.VC.ARM64EC | Podpora Univerzální platforma Windows c++ pro buildovací nástroje v142 (ARM64EC – experimentální) | 16.10.31303.231 | Volitelné
Microsoft.VisualStudio.Component.VC.CoreIde | Základní funkce jazyka C++ | 16.10.31205.252 | Volitelné
Microsoft.VisualStudio.Component.VC.Tools.ARM | MSVC v142 – nástroje sestavení ARM VS 2019 C++ (nejnovější) | 16.10.31205.252 | Volitelné
Microsoft.VisualStudio.Component.VC.Tools.ARM64 | MSVC v142 – buildovací nástroje C++ ARM64 sady VS 2019 (nejnovější) | 16.10.31205.252 | Volitelné
Microsoft. VisualStudio. Component. VC. Tools. ARM64EC | MSVC V142-VS 2019 C++ ARM64EC Build Tools (nejnovější – experimentální) | 16.10.31205.252 | Volitelné
Microsoft. VisualStudio. Component. VC. Tools. x86. x64 | MSVC V142-VS 2019 C++ x64/x86 Build Tools (nejnovější) | 16.10.31205.252 | Volitelné
Microsoft. VisualStudio. Component. VC. v141. ARM | MSVC v141-VS 2017 C++ ARM Build Tools (v 14.16) | 16.10.31205.252 | Volitelné
Microsoft. VisualStudio. Component. VC. v141. ARM64 | MSVC v141-VS 2017 C++ ARM64 Build Tools (v 14.16) | 16.10.31205.252 | Volitelné
Microsoft. VisualStudio. Component. VC. v141. x86. x64 | MSVC v141-VS 2017 C++ x64/x86 Build Tools (v 14.16) | 16.10.31205.252 | Volitelné
Microsoft. VisualStudio. Component. Windows10SDK. 16299 | Windows 10 SDK (10.0.16299.0) | 16.10.31205.252 | Volitelné
Microsoft. VisualStudio. Component. Windows10SDK. 17134 | Windows 10 SDK (10.0.17134.0) | 16.10.31205.252 | Volitelné
Microsoft.VisualStudio.Component.Windows10SDK.17763 | Windows 10 SDK (10.0.17763.0) | 16.0.28517.75 | Volitelné
Microsoft.VisualStudio.Component.Windows10SDK.18362 | Windows 10 SDK (10.0.18362.0) | 16.1.28829.92 | Volitelné
Microsoft.VisualStudio.Component.Windows10SDK.IpOverUsb | Připojení zařízení USB | 16.10.31205.252 | Volitelné
Microsoft.VisualStudio.ComponentGroup.UWP.VC | C++ (v142) – Univerzální platforma Windows nástroje | 16.10.31205.180 | Volitelné
Microsoft.VisualStudio.ComponentGroup.UWP.VC.v141 | C++ (v141) – Univerzální platforma Windows nástroje | 16.1.28810.153 | Volitelné

## <a name="visual-studio-extension-development"></a>Vývoj rozšíření sady Visual Studio

**ID:** Microsoft.VisualStudio.Workload.VisualStudioExtension

**Popis:** Vytvářejte doplňky a rozšíření pro Visual Studio, včetně nových příkazů, analyzátorů kódu a oken nástrojů.

### <a name="components-included-by-this-workload"></a>Komponenty zahrnuté v této úlohu

ID komponenty | Name | Verze | Typ závislosti
--- | --- | --- | ---
Microsoft. Component. MSBuild | MSBuild | 16.5.29515.121 | Vyžadováno
Microsoft.Net. Component. 4.6. TargetingPack | Sada targeting pack .NET Framework 4,6 | 16.0.28517.75 | Vyžadováno
Microsoft.Net. Component. 4.7.2. TargetingPack | Sada targeting pack .NET Framework 4.7.2 | 16.10.31205.252 | Vyžadováno
Microsoft. NET. Component. 4.8. SDK | .NET Framework 4,8 SDK | 16.4.29313.120 | Vyžadováno
Microsoft.Net. Component. DevelopmentPrerequisites | Vývojové nástroje .NET Framework 4.7.2 | 16.3.29207.166 | Vyžadováno
Microsoft. VisualStudio. Component. NuGet | Správce balíčků NuGet | 16.1.28829.92 | Vyžadováno
Microsoft. VisualStudio. Component. Roslyn. Compiler | Kompilátory C# a Visual Basic Roslyn | 16.0.28714.129 | Vyžadováno
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# a Visual Basic | 16.10.31205.252 | Vyžadováno
Microsoft.VisualStudio.Component.VSSDK | Visual Studio SDK | 16.0.28315.86 | Vyžadováno
Microsoft.VisualStudio.ComponentGroup.VisualStudioExtension.Prerequisites | Visual Studio pro vývoj rozšíření | 16.10.31205.180 | Vyžadováno
Microsoft.VisualStudio.Component.DiagnosticTools | Nástroje pro profilaci .NET | 16.10.31205.252 | Doporučeno
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 16.10.31305.154 | Doporučeno
Microsoft.VisualStudio.Component.TextTemplating | Transformace textových šablon | 16.0.28625.61 | Doporučeno
Microsoft.Component.CodeAnalysis.SDK | Sada .NET Compiler Platform SDK | 16.2.29003.222 | Volitelné
Microsoft.VisualStudio.Component.AppInsights.Tools | Vývojářské analytické nástroje | 16.5.29515.121 | Volitelné
Microsoft. VisualStudio. Component. DslTools | Sada SDK pro modelování | 16.0.28315.86 | Volitelné

## <a name="unaffiliated-components"></a>Nepřidružené součásti

Jedná se o součásti, které nejsou součástí žádné úlohy, ale mohou být vybrány jako jednotlivé komponenty.

ID součásti | Name | Verze
--- | --- | ---
Komponenta. GitHub. VisualStudio | Rozšíření GitHub pro Visual Studio | 2.5.9.5485
Komponenta. Xamarin. Profiler | Xamarin Profiler | 16.0.28315.86
Microsoft. Component. ClickOnce | Publikování ClickOnce | 16.4.29409.204
Microsoft. Component. HelpViewer | Prohlížeč nápovědy | 16.0.28625.61
Microsoft. NET. Component. 4.6.1. SDK | .NET Framework 4.6.1 SDK | 16.4.29409.204
Microsoft.Net.Component.4.6.2.SDK | .NET Framework 4.6.2 SDK | 16.4.29409.204
Microsoft.Net.Component.4.7.1.SDK | .NET Framework 4.7.1 SDK | 16.4.29409.204
Microsoft.Net.Component.4.7.2.SDK | .NET Framework 4.7.2 SDK | 16.4.29409.204
Microsoft.Net.Component.4.7.SDK | .NET Framework 4.7 SDK | 16.4.29409.204
Microsoft.Net.Core.Component.SDK.2.2 | Modul runtime .NET Core 2.2 (nepodporuje se) | 16.10.31205.252
Microsoft.Net.Core.Component.SDK.3.0 | Modul runtime .NET Core 3.0 (nepodporuje se) | 16.10.31320.204
Microsoft.NetCore.ComponentGroup.DevelopmentTools.2.1 | Vývojové nástroje Plus .NET Core 2,1 | 16.10.31205.252
Microsoft. NetCore. Component. Web. 2.1 | Vývojové nástroje pro web Plus .NET Core 2,1 | 16.10.31205.252
Microsoft. VisualStudio. Component. AzureDevOps. OfficeIntegration | Integrace Azure DevOps Office | 16.0.28625.61
Microsoft. VisualStudio. Component. ClassDesigner | Návrhář tříd | 16.0.28528.71
Microsoft. VisualStudio. Component. DependencyValidation. Community | Ověřování závislostí | 16.0.28517.75
Microsoft. VisualStudio. Component. Git | Git pro Windows | 16.0.28625.61
Microsoft. VisualStudio. Component. GraphDocument | Editor DGML | 16.0.28625.61
Microsoft. VisualStudio. Component. LinqToSql | Nástroje LINQ to SQL | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.14.20.ARM | MSVC v142 – VS 2019 C++ – nástroje pro sestavení ARM (v14.20) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.20.ARM.Spectre | MSVC v142 – VS 2019 C++ ARM Spectre-mitigated libs (verze 14.20) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.ARM64 | MSVC v142 – VS 2019 C++ ARM64 – buildovací nástroje (v14.20) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.20.ARM64.Spectre | MSVC v142 – VS 2019 C++ ARM64 Spectre-mitigated libs (v14.20) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.ATL | C++ v14.20 ATL pro nástroje sestavení v142 (x86 & x64) | 16.1.28829.92
Microsoft.VisualStudio.Component.VC.14.20.ATL.ARM | C++ v14.20 ATL pro nástroje sestavení v142 (ARM) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.ATL.ARM.Spectre | C++ v14.20 ATL pro buildovací nástroje v142 s omezením rizik spectre (ARM) | 16.5.29721.120
Microsoft. VisualStudio. Component. VC. 14.20. ATL. ARM64 | C++ v 14.20 ATL pro nástroje pro vytváření V142 (ARM64) | 16.5.29515.121
Microsoft. VisualStudio. Component. VC. 14.20. ATL. ARM64. Spectre | C++ v 14.20 ATL pro nástroje pro sestavení V142 s omezeními Spectre (ARM64) | 16.5.29515.121
Microsoft. VisualStudio. Component. VC. 14.20. ATL. Spectre | C++ v 14.20 ATL pro nástroje sestavení V142 s riziky Spectre (x86 & x64) | 16.5.29515.121
Microsoft. VisualStudio. Component. VC. 14.20. CLI. support | Podpora C++/CLI pro V142 Build Tools (14,20) | 16.10.31205.252
Microsoft. VisualStudio. Component. VC. 14.20. MFC | C++ v 14.20 MFC pro nástroje sestavení V142 (x86 & x64) | 16.2.29003.222
Microsoft. VisualStudio. Component. VC. 14.20. MFC. ARM | C++ v 14.20 MFC pro nástroje sestavení V142 (ARM) | 16.5.29515.121
Microsoft. VisualStudio. Component. VC. 14.20. MFC. ARM. Spectre | Nástroje sestavení C++ v14.20 MFC pro v142 s omezením rizik spectre (ARM) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.MFC.ARM64 | C++ v14.20 MFC pro nástroje sestavení v142 (ARM64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.MFC.ARM64.Spectre | Nástroje sestavení C++ v14.20 MFC pro v142 s omezením rizik spectre (ARM64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.MFC.Spectre | Nástroje sestavení C++ v14.20 MFC pro v142 s omezením rizik spectre (x86 & x64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.x86.x64 | MSVC v142 – buildovací nástroje VS 2019 C++ x64/x86 (verze 14.20) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.20.x86.x64.Spectre | MSVC v142 – VS 2019 C++ x64/x86 Spectre-mitigated libs (verze 14.20) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.21.ARM | MSVC v142 – VS 2019 C++ – nástroje pro sestavení ARM (verze 14.21) | 16.10.31205.252
Microsoft. VisualStudio. Component. VC. 14.21. ARM. Spectre | MSVC V142-VS 2019 C++ ARM Spectre-zmírnit knihovny (v 14.21) | 16.5.29515.121
Microsoft. VisualStudio. Component. VC. 14.21. ARM64 | MSVC V142-VS 2019 C++ ARM64 Build Tools (v 14.21) | 16.10.31205.252
Microsoft. VisualStudio. Component. VC. 14.21. ARM64. Spectre | MSVC V142-VS 2019 C++ ARM64 Spectre-zmírňované knihovny (v 14.21) | 16.5.29515.121
Microsoft. VisualStudio. Component. VC. 14.21. ATL | C++ v 14.21 ATL pro nástroje sestavení V142 (x86 & x64) | 16.2.29019.55
Microsoft. VisualStudio. Component. VC. 14.21. ATL. ARM | C++ v 14.21 ATL pro nástroje pro sestavení V142 (ARM) | 16.2.29019.55
Microsoft. VisualStudio. Component. VC. 14.21. ATL. ARM. Spectre | C++ v 14.21 ATL pro nástroje pro sestavení V142 s omezeními Spectre (ARM) | 16.5.29721.120
Microsoft. VisualStudio. Component. VC. 14.21. ATL. ARM64 | C++ v 14.21 ATL pro nástroje pro vytváření V142 (ARM64) | 16.2.29019.55
Microsoft.VisualStudio.Component.VC.14.21.ATL.ARM64.Spectre | C++ v14.21 ATL pro buildovací nástroje verze 142 s omezením rizik spectre (ARM64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.21.ATL.Spectre | C++ v14.21 ATL pro buildovací nástroje v142 s omezením rizik spectre (x86 & x64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.21.CLI.Support | Podpora C++/CLI pro nástroje sestavení v142 (14.21) | 16.3.29207.166
Microsoft.VisualStudio.Component.VC.14.21.MFC | C++ v14.21 MFC pro nástroje sestavení v142 (x86 & x64) | 16.2.29019.55
Microsoft.VisualStudio.Component.VC.14.21.MFC.ARM | C++ v14.21 MFC pro nástroje sestavení v142 (ARM) | 16.2.29019.55
Microsoft.VisualStudio.Component.VC.14.21.MFC.ARM.Spectre | Nástroje sestavení C++ v14.21 MFC pro v142 s omezením rizik spectre (ARM) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.21.MFC.ARM64 | C++ v 14.21 MFC pro nástroje sestavení V142 (ARM64) | 16.2.29019.55
Microsoft. VisualStudio. Component. VC. 14.21. MFC. ARM64. Spectre | C++ v 14.21 MFC pro nástroje pro sestavení V142 s omezeními Spectre (ARM64) | 16.5.29515.121
Microsoft. VisualStudio. Component. VC. 14.21. MFC. Spectre | C++ v 14.21 MFC pro nástroje sestavení V142 s riziky Spectre (x86 & x64) | 16.5.29515.121
Microsoft. VisualStudio. Component. VC. 14.21. x86. x64 | MSVC V142-VS 2019 C++ x64/x86 Build Tools (v 14.21) | 16.10.31205.252
Microsoft. VisualStudio. Component. VC. 14.21. x86. x64. Spectre | MSVC V142-VS 2019 C++ x64/x86 Spectre-zmírnit knihovny (v 14.21) | 16.5.29515.121
Microsoft. VisualStudio. Component. VC. 14.22. ARM | MSVC V142-VS 2019 C++ ARM Build Tools (v 14.22) | 16.10.31205.252
Microsoft. VisualStudio. Component. VC. 14.22. ARM. Spectre | MSVC V142-VS 2019 C++ ARM Spectre-zmírnit knihovny (v 14.22) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.22.ARM64 | MSVC v142 – buildovací nástroje C++ ARM64 sady VS 2019 (v14.22) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.22.ARM64.Spectre | MSVC v142 – VS 2019 C++ ARM64 Spectre-mitigated libs (v14.22) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.22.ATL | C++ v14.22 ATL pro nástroje sestavení v142 (x86 & x64) | 16.4.29313.120
Microsoft.VisualStudio.Component.VC.14.22.ATL.ARM | C++ v14.22 ATL pro nástroje sestavení v142 (ARM) | 16.4.29313.120
Microsoft.VisualStudio.Component.VC.14.22.ATL.ARM.Spectre | C++ v14.22 ATL pro buildovací nástroje v142 s omezením rizik spectre (ARM) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.22.ATL.ARM64 | C++ v14.22 ATL pro nástroje sestavení v142 (ARM64) | 16.4.29313.120
Microsoft.VisualStudio.Component.VC.14.22.ATL.ARM64.Spectre | C++ v14.22 ATL pro buildovací nástroje v142 s omezením rizik spectre (ARM64) | 16.5.29515.121
Microsoft. VisualStudio. Component. VC. 14.22. ATL. Spectre | C++ v 14.22 ATL pro nástroje sestavení V142 s riziky Spectre (x86 & x64) | 16.5.29515.121
Microsoft. VisualStudio. Component. VC. 14.22. CLI. support | Podpora C++/CLI pro V142 Build Tools (14,22) | 16.10.31205.252
Microsoft. VisualStudio. Component. VC. 14.22. MFC | C++ v 14.22 MFC pro nástroje sestavení V142 (x86 & x64) | 16.4.29313.120
Microsoft. VisualStudio. Component. VC. 14.22. MFC. ARM | C++ v 14.22 MFC pro nástroje sestavení V142 (ARM) | 16.4.29313.120
Microsoft. VisualStudio. Component. VC. 14.22. MFC. ARM. Spectre | C++ v 14.22 MFC pro nástroje pro sestavení V142 s omezeními Spectre (ARM) | 16.5.29515.121
Microsoft. VisualStudio. Component. VC. 14.22. MFC. ARM64 | C++ v 14.22 MFC pro nástroje sestavení V142 (ARM64) | 16.4.29313.120
Microsoft. VisualStudio. Component. VC. 14.22. MFC. ARM64. Spectre | C++ v14.22 MFC pro nástroje sestavení v142 s omezením rizik spectre (ARM64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.22.MFC.Spectre | C++ v14.22 MFC pro nástroje sestavení v142 s omezením rizik spectre (x86 & x64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.22.x86.x64 | MSVC v142 – buildovací nástroje VS 2019 C++ x64/x86 (verze 14.22) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.22.x86.x64.Spectre | MSVC v142 – VS 2019 C++ x64/x86 Spectre-mitigated libs (v14.22) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.ARM | MSVC v142 – nástroje sestavení ARM VS 2019 C++ (verze 14.23) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.23.ARM.Spectre | MSVC v142 – VS 2019 C++ ARM Spectre-mitigated libs (verze 14.23) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.ARM64 | MSVC v142 – buildovací nástroje C++ ARM64 sady VS 2019 (v14.23) | 16.10.31205.252
Microsoft. VisualStudio. Component. VC. 14.23. ARM64. Spectre | MSVC V142-VS 2019 C++ ARM64 Spectre-zmírňované knihovny (v 14.23) | 16.5.29515.121
Microsoft. VisualStudio. Component. VC. 14.23. ATL | C++ v 14.23 ATL pro nástroje sestavení V142 (x86 & x64) | 16.5.29515.121
Microsoft. VisualStudio. Component. VC. 14.23. ATL. ARM | C++ v 14.23 ATL pro nástroje pro sestavení V142 (ARM) | 16.5.29515.121
Microsoft. VisualStudio. Component. VC. 14.23. ATL. ARM. Spectre | C++ v 14.23 ATL pro nástroje pro sestavení V142 s omezeními Spectre (ARM) | 16.5.29721.120
Microsoft. VisualStudio. Component. VC. 14.23. ATL. ARM64 | C++ v 14.23 ATL pro nástroje pro vytváření V142 (ARM64) | 16.5.29515.121
Microsoft. VisualStudio. Component. VC. 14.23. ATL. ARM64. Spectre | C++ v 14.23 ATL pro nástroje pro sestavení V142 s omezeními Spectre (ARM64) | 16.5.29515.121
Microsoft. VisualStudio. Component. VC. 14.23. ATL. Spectre | C++ v 14.23 ATL pro nástroje sestavení V142 s riziky Spectre (x86 & x64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.CLI.Support | Podpora C++/CLI pro nástroje sestavení v142 (14.23) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.23.MFC | C++ v14.23 MFC pro nástroje sestavení v142 (x86 & x64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.MFC.ARM | C++ v14.23 MFC pro nástroje sestavení v142 (ARM) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.MFC.ARM.Spectre | C++ v14.23 MFC pro nástroje sestavení v142 s omezením rizik spectre (ARM) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.MFC.ARM64 | C++ v14.23 MFC pro nástroje sestavení v142 (ARM64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.MFC.ARM64.Spectre | C++ v14.23 MFC pro nástroje sestavení v142 s omezením rizik spectre (ARM64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.MFC.Spectre | C++ v 14.23 MFC pro nástroje sestavení V142 s riziky Spectre (x86 & x64) | 16.5.29515.121
Microsoft. VisualStudio. Component. VC. 14.23. x86. x64 | MSVC V142-VS 2019 C++ x64/x86 Build Tools (v 14.23) | 16.10.31205.252
Microsoft. VisualStudio. Component. VC. 14.23. x86. x64. Spectre | MSVC V142-VS 2019 C++ x64/x86 Spectre-zmírnit knihovny (v 14.23) | 16.5.29515.121
Microsoft. VisualStudio. Component. VC. 14.24. ARM | MSVC V142-VS 2019 C++ ARM Build Tools (v 14.24) | 16.10.31205.252
Microsoft. VisualStudio. Component. VC. 14.24. ARM. Spectre | MSVC V142-VS 2019 C++ ARM Spectre-zmírnit knihovny (v 14.24) | 16.5.29721.120
Microsoft. VisualStudio. Component. VC. 14.24. ARM64 | MSVC V142-VS 2019 C++ ARM64 Build Tools (v 14.24) | 16.10.31205.252
Microsoft. VisualStudio. Component. VC. 14.24. ARM64. Spectre | MSVC V142-VS 2019 C++ ARM64 Spectre-zmírňované knihovny (v 14.24) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.ATL | C++ v14.24 ATL pro nástroje sestavení v142 (x86 & x64) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.ATL.ARM | C++ v14.24 ATL pro nástroje sestavení v142 (ARM) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.ATL.ARM.Spectre | C++ v14.24 ATL pro buildovací nástroje v142 s omezením rizik spectre (ARM) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.ATL.ARM64 | C++ v14.24 ATL pro nástroje sestavení v142 (ARM64) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.ATL.ARM64.Spectre | C++ v14.24 ATL pro buildovací nástroje v142 s omezením rizik spectre (ARM64) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.ATL.Spectre | C++ v14.24 ATL pro buildovací nástroje v142 s omezením rizik spectre (x86 & x64) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.24.CLI.Support | Podpora C++/CLI pro nástroje sestavení v142 (14.24) | 16.10.31205.252
Microsoft. VisualStudio. Component. VC. 14.24. MFC | C++ v 14.24 MFC pro nástroje sestavení V142 (x86 & x64) | 16.5.29721.120
Microsoft. VisualStudio. Component. VC. 14.24. MFC. ARM | C++ v 14.24 MFC pro nástroje sestavení V142 (ARM) | 16.5.29721.120
Microsoft. VisualStudio. Component. VC. 14.24. MFC. ARM. Spectre | C++ v 14.24 MFC pro nástroje pro sestavení V142 s omezeními Spectre (ARM) | 16.5.29721.120
Microsoft. VisualStudio. Component. VC. 14.24. MFC. ARM64 | C++ v 14.24 MFC pro nástroje sestavení V142 (ARM64) | 16.5.29721.120
Microsoft. VisualStudio. Component. VC. 14.24. MFC. ARM64. Spectre | C++ v 14.24 MFC pro nástroje pro sestavení V142 s omezeními Spectre (ARM64) | 16.10.31205.252
Microsoft. VisualStudio. Component. VC. 14.24. MFC. Spectre | C++ v 14.24 MFC pro nástroje sestavení V142 s riziky Spectre (x86 & x64) | 16.10.31205.252
Microsoft. VisualStudio. Component. VC. 14.24. x86. x64 | MSVC v142 – buildovací nástroje VS 2019 C++ x64/x86 (verze 14.24) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.24.x86.x64.Spectre | MSVC v142 – VS 2019 C++ x64/x86 Spectre-mitigated libs (verze 14.24) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.25.ARM | MSVC v142 – VS 2019 C++ – nástroje pro sestavení ARM (verze 14.25) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.25.ARM.Spectre | MSVC v142 – VS 2019 C++ ARM Spectre-mitigated libs (verze 14.25) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.25.ARM64 | MSVC v142 – VS 2019 C++ ARM64 – buildovací nástroje (v14.25) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.25.ARM64.Spectre | MSVC v142 – VS 2019 C++ ARM64 Spectre-mitigated libs (v14.25) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.25.ATL | C++ v14.25 ATL pro nástroje sestavení v142 (x86 & x64) | 16.10.31205.252
Microsoft. VisualStudio. Component. VC. 14.25. ATL. ARM | C++ v 14.25 ATL pro nástroje pro sestavení V142 (ARM) | 16.10.31205.252
Microsoft. VisualStudio. Component. VC. 14.25. ATL. ARM. Spectre | C++ v 14.25 ATL pro nástroje pro sestavení V142 s omezeními Spectre (ARM) | 16.10.31205.252
Microsoft. VisualStudio. Component. VC. 14.25. ATL. ARM64 | C++ v 14.25 ATL pro nástroje pro vytváření V142 (ARM64) | 16.10.31205.252
Microsoft. VisualStudio. Component. VC. 14.25. ATL. ARM64. Spectre | C++ v 14.25 ATL pro nástroje pro sestavení V142 s omezeními Spectre (ARM64) | 16.10.31205.252
Microsoft. VisualStudio. Component. VC. 14.25. ATL. Spectre | C++ v 14.25 ATL pro nástroje sestavení V142 s riziky Spectre (x86 & x64) | 16.10.31205.252
Microsoft. VisualStudio. Component. VC. 14.25. CLI. support | Podpora C++/CLI pro V142 Build Tools (14,25) | 16.10.31205.252
Microsoft. VisualStudio. Component. VC. 14.25. MFC | C++ v 14.25 MFC pro nástroje sestavení V142 (x86 & x64) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.25.MFC.ARM | C++ v14.25 MFC pro nástroje sestavení v142 (ARM) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.25.MFC.ARM.Spectre | C++ v14.25 MFC pro nástroje sestavení v142 s omezením rizik spectre (ARM) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.25.MFC.ARM64 | C++ v14.25 MFC pro nástroje sestavení v142 (ARM64) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.25.MFC.ARM64.Spectre | C++ v14.25 MFC pro nástroje sestavení v142 s omezením rizik spectre (ARM64) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.25.MFC.Spectre | C++ v14.25 MFC pro nástroje sestavení v142 s omezením rizik spectre (x86 & x64) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.25.x86.x64 | MSVC v142 – buildovací nástroje VS 2019 C++ x64/x86 (verze 14.25) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.25.x86.x64.Spectre | MSVC V142-VS 2019 C++ x64/x86 Spectre-zmírnit knihovny (v 14.25) | 16.10.31205.252
Microsoft. VisualStudio. Component. VC. 14.26. ARM | MSVC V142-VS 2019 C++ ARM Build Tools (v 14.26) | 16.10.31205.252
Microsoft. VisualStudio. Component. VC. 14.26. ARM. Spectre | MSVC V142-VS 2019 C++ ARM Spectre-zmírnit knihovny (v 14.26) | 16.10.31205.252
Microsoft. VisualStudio. Component. VC. 14.26. ARM64 | MSVC V142-VS 2019 C++ ARM64 Build Tools (v 14.26) | 16.10.31205.252
Microsoft. VisualStudio. Component. VC. 14.26. ARM64. Spectre | MSVC V142-VS 2019 C++ ARM64 Spectre-zmírňované knihovny (v 14.26) | 16.10.31205.252
Microsoft. VisualStudio. Component. VC. 14.26. ATL | C++ v 14.26 ATL pro nástroje sestavení V142 (x86 & x64) | 16.10.31205.252
Microsoft. VisualStudio. Component. VC. 14.26. ATL. ARM | C++ v 14.26 ATL pro nástroje pro sestavení V142 (ARM) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.26.ATL.ARM.Spectre | C++ v14.26 ATL pro buildovací nástroje v142 s omezením rizik spectre (ARM) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.26.ATL.ARM64 | C++ v14.26 ATL pro nástroje sestavení v142 (ARM64) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.26.ATL.ARM64.Spectre | C++ v14.26 ATL pro buildovací nástroje v142 s omezením rizik spectre (ARM64) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.26.ATL.Spectre | C++ v14.26 ATL pro buildovací nástroje v142 s omezením rizik spectre (x86 & x64) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.26.CLI.Support | Podpora C++/CLI pro nástroje sestavení v142 (14.26) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.26.MFC | C++ v14.26 MFC pro nástroje sestavení v142 (x86 & x64) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.26.MFC.ARM | C++ v14.26 MFC pro nástroje sestavení v142 (ARM) | 16.10.31205.252
Microsoft. VisualStudio. Component. VC. 14.26. MFC. ARM. Spectre | C++ v 14.26 MFC pro nástroje pro sestavení V142 s omezeními Spectre (ARM) | 16.10.31205.252
Microsoft. VisualStudio. Component. VC. 14.26. MFC. ARM64 | C++ v 14.26 MFC pro nástroje sestavení V142 (ARM64) | 16.10.31205.252
Microsoft. VisualStudio. Component. VC. 14.26. MFC. ARM64. Spectre | C++ v 14.26 MFC pro nástroje pro sestavení V142 s omezeními Spectre (ARM64) | 16.10.31205.252
Microsoft. VisualStudio. Component. VC. 14.26. MFC. Spectre | C++ v 14.26 MFC pro nástroje sestavení V142 s riziky Spectre (x86 & x64) | 16.10.31205.252
Microsoft. VisualStudio. Component. VC. 14.26. x86. x64 | MSVC V142-VS 2019 C++ x64/x86 Build Tools (v 14.26) | 16.10.31205.252
Microsoft. VisualStudio. Component. VC. 14.26. x86. x64. Spectre | MSVC V142-VS 2019 C++ x64/x86 Spectre-zmírnit knihovny (v 14.26) | 16.10.31205.252
Microsoft. VisualStudio. Component. VC. 14.27. ARM | MSVC v142 – VS 2019 C++ – nástroje pro sestavení ARM (verze 14.27) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.27.ARM.Spectre | MSVC v142 – VS 2019 C++ ARM Spectre-mitigated libs (verze 14.27) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.27.ARM64 | MSVC v142 – buildovací nástroje C++ ARM64 sady VS 2019 (v14.27) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.27.ARM64.Spectre | MSVC v142 – VS 2019 C++ ARM64 Spectre-mitigated libs (verze 14.27) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.27.ATL | C++ v14.27 ATL pro nástroje sestavení v142 (x86 & x64) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.27.ATL.ARM | C++ v14.27 ATL pro nástroje sestavení v142 (ARM) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.27.ATL.ARM.Spectre | C++ v14.27 ATL pro buildovací nástroje v142 s omezením rizik spectre (ARM) | 16.10.31205.252
Microsoft. VisualStudio. Component. VC. 14.27. ATL. ARM64 | C++ v 14.27 ATL pro nástroje pro vytváření V142 (ARM64) | 16.10.31205.252
Microsoft. VisualStudio. Component. VC. 14.27. ATL. ARM64. Spectre | C++ v 14.27 ATL pro nástroje pro sestavení V142 s omezeními Spectre (ARM64) | 16.10.31205.252
Microsoft. VisualStudio. Component. VC. 14.27. ATL. Spectre | C++ v 14.27 ATL pro nástroje sestavení V142 s riziky Spectre (x86 & x64) | 16.10.31205.252
Microsoft. VisualStudio. Component. VC. 14.27. CLI. support | Podpora C++/CLI pro V142 Build Tools (14,27) | 16.10.31205.252
Microsoft. VisualStudio. Component. VC. 14.27. MFC | C++ v 14.27 MFC pro nástroje sestavení V142 (x86 & x64) | 16.10.31205.252
Microsoft. VisualStudio. Component. VC. 14.27. MFC. ARM | C++ v 14.27 MFC pro nástroje sestavení V142 (ARM) | 16.10.31205.252
Microsoft. VisualStudio. Component. VC. 14.27. MFC. ARM. Spectre | C++ v 14.27 MFC pro nástroje pro sestavení V142 s omezeními Spectre (ARM) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.27.MFC.ARM64 | C++ v14.27 MFC pro nástroje sestavení v142 (ARM64) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.27.MFC.ARM64.Spectre | Nástroje sestavení C++ v14.27 MFC pro v142 s omezením rizik spectre (ARM64) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.27.MFC.Spectre | Nástroje sestavení C++ v14.27 MFC pro v142 s omezením rizik spectre (x86 & x64) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.27.x86.x64 | MSVC v142 – buildovací nástroje VS 2019 C++ x64/x86 (verze 14.27) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.27.x86.x64.Spectre | MSVC v142 – VS 2019 C++ x64/x86 Spectre-mitigated libs (verze 14.27) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.28.16.9.ARM | MSVC v142 – VS 2019 C++ – nástroje pro sestavení ARM (verze 14.28-16.9) | 16.10.31303.231
Microsoft.VisualStudio.Component.VC.14.28.16.9.ARM.Spectre | MSVC V142-VS 2019 C++ ARM Spectre-zmírnit knihovny (v 14.28-16.9) | 16.10.31303.231
Microsoft. VisualStudio. Component. VC. 14.28.16.9. ARM64 | MSVC V142-VS 2019 C++ ARM64 Build Tools (v 14.28-16.9) | 16.10.31303.231
Microsoft. VisualStudio. Component. VC. 14.28.16.9. ARM64. Spectre | MSVC V142-VS 2019 C++ ARM64 Spectre-zmírňované knihovny (v 14.28-16.9) | 16.10.31303.231
Microsoft. VisualStudio. Component. VC. 14.28.16.9. ATL | C++ v 14.28 (16,9) ATL pro nástroje sestavení V142 (x86 & x64) | 16.10.31303.231
Microsoft. VisualStudio. Component. VC. 14.28.16.9. ATL. ARM | C++ v 14.28 (16,9) ATL pro nástroje sestavení V142 (ARM) | 16.10.31303.231
Microsoft. VisualStudio. Component. VC. 14.28.16.9. ATL. ARM. Spectre | C++ v 14.28 (16,9) ATL pro nástroje sestavení V142 s omezeními Spectre (ARM) | 16.10.31303.231
Microsoft. VisualStudio. Component. VC. 14.28.16.9. ATL. ARM64 | C++ v 14.28 (16,9) ATL pro nástroje sestavení V142 (ARM64) | 16.10.31303.231
Microsoft.VisualStudio.Component.VC.14.28.16.9.ATL.ARM64.Spectre | C++ v14.28 (16.9) ATL pro buildovací nástroje v142 s zmírněními rizik spectre (ARM64) | 16.10.31303.231
Microsoft.VisualStudio.Component.VC.14.28.16.9.ATL.Spectre | C++ v14.28 (16.9) ATL pro buildovací nástroje v142 se zmírněními rizik spectre (x86 & x64) | 16.10.31303.231
Microsoft.VisualStudio.Component.VC.14.28.16.9.CLI.Support | Podpora C++/CLI pro nástroje sestavení v142 (14.28-16.9) | 16.10.31303.231
Microsoft.VisualStudio.Component.VC.14.28.16.9.MFC | C++ v14.28 (16.9) MFC pro nástroje sestavení v142 (x86 & x64) | 16.10.31303.231
Microsoft.VisualStudio.Component.VC.14.28.16.9.MFC.ARM | C++ v14.28 (16.9) MFC pro nástroje sestavení v142 (ARM) | 16.10.31303.231
Microsoft.VisualStudio.Component.VC.14.28.16.9.MFC.ARM.Spectre | C++ v14.28 (16.9) MFC pro nástroje sestavení v142 s omezením rizik spectre (ARM) | 16.10.31303.231
Microsoft.VisualStudio.Component.VC.14.28.16.9.MFC.ARM64 | C++ v14.28 (16.9) MFC pro nástroje sestavení v142 (ARM64) | 16.10.31303.231
Microsoft. VisualStudio. Component. VC. 14.28.16.9. MFC. ARM64. Spectre | C++ v 14.28 (16,9) MFC pro nástroje sestavení V142 s riziky Spectre (ARM64) | 16.10.31303.231
Microsoft. VisualStudio. Component. VC. 14.28.16.9. MFC. Spectre | C++ v 14.28 (16,9) MFC pro nástroje sestavení V142 s riziky Spectre (x86 & x64) | 16.10.31303.231
Microsoft. VisualStudio. Component. VC. 14.28.16.9. x86. x64 | MSVC V142-VS 2019 C++ x64/x86 Build Tools (v 14.28-16.9) | 16.10.31303.231
Microsoft. VisualStudio. Component. VC. 14.28.16.9. x86. x64. Spectre | MSVC V142-VS 2019 C++ x64/x86 Spectre-zmírnit knihovny (v 14.28-16.9) | 16.10.31303.231
Microsoft. VisualStudio. Component. VC. 14.28. ARM | MSVC V142-VS 2019 C++ ARM Build Tools (v 14.28-16.8) | 16.10.31205.252
Microsoft. VisualStudio. Component. VC. 14.28. ARM. Spectre | MSVC V142-VS 2019 C++ ARM Spectre-zmírnit knihovny (v 14.28-16.8) | 16.10.31205.252
Microsoft. VisualStudio. Component. VC. 14.28. ARM64 | MSVC v142 – buildovací nástroje C++ ARM64 sady VS 2019 (v14.28-16.8) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.28.ARM64.Spectre | MSVC v142 – VS 2019 C++ ARM64 Spectre-mitigated libs (v14.28-16.8) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.28.ATL | C++ v14.28 (16.8) ATL pro buildovací nástroje v142 (x86 & x64) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.28.ATL.ARM | C++ v14.28 (16.8) ATL pro nástroje sestavení v142 (ARM) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.28.ATL.ARM.Spectre | C++ v14.28 (16.8) ATL pro buildovací nástroje v142 s spectre mitigations (ARM) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.28.ATL.ARM64 | C++ v14.28 (16.8) ATL pro nástroje sestavení v142 (ARM64) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.28.ATL.ARM64.Spectre | C++ v14.28 (16.8) ATL pro buildovací nástroje v142 s zmírněními rizik spectre (ARM64) | 16.10.31205.252
Microsoft. VisualStudio. Component. VC. 14.28. ATL. Spectre | C++ v 14.28 (16,8) ATL pro nástroje sestavení V142 s riziky Spectre (x86 & x64) | 16.10.31205.252
Microsoft. VisualStudio. Component. VC. 14.28. CLI. support | Podpora C++/CLI pro V142 Build Tools (14.28-16.8) | 16.10.31205.252
Microsoft. VisualStudio. Component. VC. 14.28. MFC | C++ v 14.28 (16,8) MFC pro nástroje sestavení V142 (x86 & x64) | 16.10.31205.252
Microsoft. VisualStudio. Component. VC. 14.28. MFC. ARM | C++ v 14.28 (16,8) MFC pro nástroje sestavení V142 (ARM) | 16.10.31205.252
Microsoft. VisualStudio. Component. VC. 14.28. MFC. ARM. Spectre | C++ v 14.28 (16,8) MFC pro nástroje sestavení V142 s omezeními Spectre (ARM) | 16.10.31205.252
Microsoft. VisualStudio. Component. VC. 14.28. MFC. ARM64 | C++ v 14.28 (16,8) MFC pro nástroje sestavení V142 (ARM64) | 16.10.31205.252
Microsoft. VisualStudio. Component. VC. 14.28. MFC. ARM64. Spectre | C++ v 14.28 (16,8) MFC pro nástroje sestavení V142 s riziky Spectre (ARM64) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.28.MFC.Spectre | C++ v14.28 (16.8) MFC pro buildovací nástroje v142 s omezeními rizik spectre (x86 & x64) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.28.x86.x64 | MSVC v142 – buildovací nástroje VS 2019 C++ x64/x86 (v14.28-16.8) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.28.x86.x64.Spectre | MSVC v142 – VS 2019 C++ x64/x86 Spectre-mitigated libs (v14.28-16.8) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.29.16.10.ARM | MSVC v142 – VS 2019 C++ – nástroje pro sestavení ARM (v14.29-16.10) | 16.10.31313.121
Microsoft.VisualStudio.Component.VC.14.29.16.10.ARM.Spectre | MSVC v142 – VS 2019 C++ ARM Spectre-mitigated libs (v14.29-16.10) | 16.10.31313.121
Microsoft.VisualStudio.Component.VC.14.29.16.10.ARM64 | MSVC v142 – VS 2019 C++ ARM64 – buildovací nástroje (v14.29-16.10) | 16.10.31313.121
Microsoft.VisualStudio.Component.VC.14.29.16.10.ARM64.Spectre | MSVC V142-VS 2019 C++ ARM64 Spectre-zmírňované knihovny (v 14.29-16.10) | 16.10.31313.121
Microsoft. VisualStudio. Component. VC. 14.29.16.10. ATL | C++ v 14.29 (16,10) ATL pro nástroje sestavení V142 (x86 & x64) | 16.10.31313.121
Microsoft. VisualStudio. Component. VC. 14.29.16.10. ATL. ARM | C++ v 14.29 (16,10) ATL pro nástroje sestavení V142 (ARM) | 16.10.31313.121
Microsoft. VisualStudio. Component. VC. 14.29.16.10. ATL. ARM. Spectre | C++ v 14.29 (16,10) ATL pro nástroje sestavení V142 s omezeními Spectre (ARM) | 16.10.31313.121
Microsoft. VisualStudio. Component. VC. 14.29.16.10. ATL. ARM64 | C++ v 14.29 (16,10) ATL pro nástroje sestavení V142 (ARM64) | 16.10.31313.121
Microsoft. VisualStudio. Component. VC. 14.29.16.10. ATL. ARM64. Spectre | C++ v 14.29 (16,10) ATL pro nástroje sestavení V142 s riziky Spectre (ARM64) | 16.10.31313.121
Microsoft. VisualStudio. Component. VC. 14.29.16.10. ATL. Spectre | C++ v 14.29 (16,10) ATL pro nástroje sestavení V142 s riziky Spectre (x86 & x64) | 16.10.31313.121
Microsoft.VisualStudio.Component.VC.14.29.16.10.CLI.Support | Podpora C++/CLI pro nástroje sestavení v142 (14.29-16.10) | 16.10.31313.121
Microsoft.VisualStudio.Component.VC.14.29.16.10.MFC | C++ v14.29 (16.10) MFC pro nástroje sestavení v142 (x86 & x64) | 16.10.31313.121
Microsoft.VisualStudio.Component.VC.14.29.16.10.MFC.ARM | C++ v14.29 (16.10) MFC pro nástroje sestavení v142 (ARM) | 16.10.31313.121
Microsoft.VisualStudio.Component.VC.14.29.16.10.MFC.ARM.Spectre | C++ v14.29 (16.10) MFC pro buildovací nástroje v142 s omezením rizik spectre (ARM) | 16.10.31313.121
Microsoft.VisualStudio.Component.VC.14.29.16.10.MFC.ARM64 | C++ v14.29 (16.10) MFC pro nástroje sestavení v142 (ARM64) | 16.10.31313.121
Microsoft.VisualStudio.Component.VC.14.29.16.10.MFC.ARM64.Spectre | C++ v14.29 (16.10) MFC pro buildovací nástroje v142 s omezením rizik spectre (ARM64) | 16.10.31313.121
Microsoft.VisualStudio.Component.VC.14.29.16.10.MFC.Spectre | C++ v14.29 (16.10) MFC pro nástroje sestavení v142 s omezeními rizik spectre (x86 & x64) | 16.10.31313.121
Microsoft. VisualStudio. Component. VC. 14.29.16.10. x86. x64 | MSVC V142-VS 2019 C++ x64/x86 Build Tools (v 14.29-16.10) | 16.10.31313.121
Microsoft. VisualStudio. Component. VC. 14.29.16.10. x86. x64. Spectre | MSVC V142-VS 2019 C++ x64/x86 Spectre-zmírnit knihovny (v 14.29-16.10) | 16.10.31313.121
Microsoft. VisualStudio. Component. VC. ATL. ARM | C++ ATL pro nejnovější nástroje V142 Build (ARM) | 16.4.29313.120
Microsoft. VisualStudio. Component. VC. ATL. ARM. Spectre | C++ ATL pro nejnovější nástroje V142 buildu s omezeními Spectre (ARM) | 16.5.29721.120
Microsoft. VisualStudio. Component. VC. ATL. ARM64 | C++ ATL pro nejnovější nástroje V142 Build (ARM64) | 16.4.29313.120
Microsoft. VisualStudio. Component. VC. ATL. ARM64. Spectre | C++ ATL pro nejnovější nástroje V142 buildu s omezeními Spectre (ARM64) | 16.5.29515.121
Microsoft. VisualStudio. Component. VC. ATL. ARM64EC | C++ ATL pro nejnovější nástroje sestavení v142 (ARM64EC – experimentální) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.ATL.ARM64EC.Spectre | C++ ATL pro nejnovější nástroje sestavení v142 s omezením rizik spectre (ARM64EC – experimentální) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.ATL.Spectre | C++ ATL pro nejnovější nástroje sestavení v142 s omezením rizik spectre (x86 & x64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.ATLMFC.Spectre | C++ MFC pro nejnovější nástroje sestavení v142 s omezením rizik spectre (x86 & x64) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.MFC.ARM | Knihovna MFC jazyka C++ pro nejnovější nástroje sestavení v142 (ARM) | 16.4.29313.120
Microsoft.VisualStudio.Component.VC.MFC.ARM.Spectre | C++ MFC pro nejnovější nástroje sestavení v142 s omezením rizik spectre (ARM) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.MFC.ARM64 | C++ MFC pro nejnovější nástroje sestavení v142 (ARM64) | 16.4.29313.120
Microsoft. VisualStudio. Component. VC. MFC. ARM64. Spectre | C++ MFC pro nejnovější nástroje V142 buildu s omezeními Spectre (ARM64) | 16.5.29721.120
Microsoft. VisualStudio. Component. VC. MFC. ARM64EC | C++ MFC pro nejnovější nástroje V142 Build (ARM64EC – experimentální) | 16.10.31205.252
Microsoft. VisualStudio. Component. VC. MFC. ARM64EC. Spectre | C++ MFC pro nejnovější nástroje V142 buildu s omezeními Spectre (ARM64EC-experimentální) | 16.10.31205.252
Microsoft. VisualStudio. Component. VC. Redist. MSM | C++ 2019 Distribuovatelný MSMs | 16.5.29515.121
Microsoft. VisualStudio. Component. VC. runtimes. ARM. Spectre | MSVC V142-VS 2019 C++ ARM Spectre – zmírňovaná knihovny (nejnovější) | 16.10.31205.252
Microsoft. VisualStudio. Component. VC. runtimes. ARM64. Spectre | MSVC V142-VS 2019 C++ ARM64 Spectre-zmírňované knihovny (nejnovější) | 16.10.31205.252
Microsoft. VisualStudio. Component. VC. runtimes. ARM64EC. Spectre | MSVC V142-VS 2019 C++ ARM64EC Spectre-zmírňované knihovny (nejnovější – experimentální) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.Runtimes.x86.x64.Spectre | MSVC v142 – VS 2019 C++ x64/x86 Spectre-mitigated libs (nejnovější)  | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.v141.ARM.Spectre | MSVC v141 – Knihovny s mitigated c++ ARM vS 2017 (verze 14.16) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.v141.ARM64.Spectre | MSVC v141 – VS 2017 C++ ARM64 Spectre-mitigated libs (verze 14.16) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.v141.ATL | C++ ATL pro buildovací nástroje v141 (x86 & x64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.ATL.ARM | C++ ATL pro nástroje sestavení v141 (ARM) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.ATL.ARM.Spectre | C++ ATL pro buildovací nástroje v141 s omezením rizik spectre (ARM) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.v141.ATL.ARM64 | C++ ATL pro nástroje v141 Build (ARM64) | 16.0.28625.61
Microsoft. VisualStudio. Component. VC. v141. ATL. ARM64. Spectre | C++ ATL pro nástroje v141 buildu s omezeními Spectre (ARM64) | 16.0.28625.61
Microsoft. VisualStudio. Component. VC. v141. ATL. Spectre | C++ ATL pro nástroje v141 buildu s omezeními Spectre (x86 & x64) | 16.0.28625.61
Microsoft. VisualStudio. Component. VC. v141. CLI. support | Podpora C++/CLI pro v141 Build Tools (14,16) | 16.3.29207.166
Microsoft. VisualStudio. Component. VC. v141. MFC | C++ MFC pro nástroje v141 Build (x86 & x64) | 16.0.28625.61
Microsoft. VisualStudio. Component. VC. v141. MFC. ARM | C++ MFC pro nástroje v141 Build (ARM) | 16.2.28915.88
Microsoft. VisualStudio. Component. VC. v141. MFC. ARM. Spectre | C++ MFC pro nástroje v141 buildu s omezeními Spectre (ARM) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.MFC.ARM64 | C++ MFC pro nástroje sestavení v141 (ARM64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.MFC.ARM64.Spectre | C++ MFC pro buildovací nástroje v141 s omezením rizik spectre (ARM64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.MFC.Spectre | C++ MFC pro buildovací nástroje v141 s omezením rizik spectre (x86 & x64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.x86.x64.Spectre | MSVC v141 – VS 2017 C++ x64/x86 Spectre-mitigated libs (verze 14.16) | 16.5.29515.121
Microsoft.VisualStudio.Component.VisualStudioData | Zdroje dat a odkazy na služby | 16.0.28707.177
Microsoft.VisualStudio.Component.WinXP | Podpora C++ Windows XP pro nástroje VS 2017 (v141) [zastaralé] | 16.10.31205.252
Microsoft.VisualStudio.Web.Mvc4.ComponentGroup | ASP.NET MVC 4 | 16.10.31205.180
