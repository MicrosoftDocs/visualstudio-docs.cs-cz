---
title: Visual Studio Enterprise ID komponent a úloh 2019
titleSuffix: ''
description: Použití ID úloh a komponent k instalaci Visual Studio pomocí příkazového řádku nebo k určení závislosti v manifestu VSIX
keywords: ''
author: j-martens
ms.author: jmartens
manager: jmartens
ms.date: 05/24/2021
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.topic: include
ms.openlocfilehash: c0676e2d79e665f4c42cbc569aa178e2231e9231
ms.sourcegitcommit: 18e7300d4878f2fcd0263a4aff31a755ae8fc289
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/25/2021
ms.locfileid: "110449830"
---
## <a name="visual-studio-core-editor-included-with-visual-studio-enterprise-2019"></a>Visual Studio Core Editor (součástí Visual Studio Enterprise 2019)

**ID:** Microsoft.VisualStudio.Workload.CoreEditor

**Popis:** Základní Visual Studio prostředí, včetně úprav kódu se syntaxí, správy zdrojového kódu a správy pracovních položek.

### <a name="components-included-by-this-workload"></a>Komponenty zahrnuté v této úlohu

ID komponenty | Name | Verze | Typ závislosti
--- | --- | --- | ---
Microsoft.VisualStudio.Component.CoreEditor | Visual Studio základního editoru | 16.1.28811.260 | Vyžadováno
Microsoft.VisualStudio.Component.StartPageExperiment.Cpp | Visual Studio úvodní stránka pro uživatele jazyka C++ | 16.0.28315.86 | Volitelné

## <a name="azure-development"></a>Vývoj pro Azure

**ID:** Microsoft.VisualStudio.Workload.Azure

**Popis:** Sady Azure SDK, nástroje a projekty pro vývoj cloudových aplikací a vytváření prostředků pomocí .NET a .NET Framework. Obsahuje také nástroje pro kontejnerizaci vaší aplikace, včetně podpory Dockeru.

### <a name="components-included-by-this-workload"></a>Komponenty zahrnuté v této úlohu

ID komponenty | Name | Verze | Typ závislosti
--- | --- | --- | ---
Součást. Microsoft. VisualStudio. RazorExtension | Jazykové služby Razor | 16.10.31205.252 | Vyžadováno
Součást. Microsoft. VisualStudio. Web. AzureFunctions | Nástroje Azure WebJobs | 16.10.31205.252 | Vyžadováno
Součást. Microsoft. Web. LibraryManager | Správce knihovny | 16.10.31205.180 | Vyžadováno
Komponenta. Microsoft. WebTools. BrowserLink. WebLivePreview | Web Live Preview | 0.7.22.39845 | Vyžadováno
Microsoft. Component. MSBuild | MSBuild | 16.5.29515.121 | Vyžadováno
Microsoft. Component. ClickOnce. Publish | Publikování ClickOnce pro .NET  | 16.10.31303.231 | Vyžadováno
Microsoft.Net. Component. 4.5.2. TargetingPack | Sada .NET Framework 4.5.2 targeting pack | 16.0.28517.75 | Vyžadováno
Microsoft.Net. Component. 4.5. TargetingPack | .NET Framework 4.5 | 16.0.28517.75 | Vyžadováno
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 | 16.0.28517.75 | Vyžadováno
Microsoft.Net.Component.4.7.2.TargetingPack | .NET Framework 4.7.2 | 16.10.31205.252 | Vyžadováno
Microsoft.Net.Component.4.8.SDK | .NET Framework 4.8 SDK | 16.4.29313.120 | Vyžadováno
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | .NET Framework 4.7.2 – vývojové nástroje | 16.3.29207.166 | Vyžadováno
Microsoft.NetCore.Component.DevelopmentTools | Vývojové nástroje pro .NET | 16.10.31303.231 | Vyžadováno
Microsoft.NetCore.Component.Runtime.3.1 | .NET Core 3.1 Runtime (LTS) | 16.10.31320.204 | Vyžadováno
Microsoft. NetCore. Component. Runtime. 5.0 | .NET 5,0 – modul runtime | 16.10.31320.204 | Vyžadováno
Microsoft. NetCore. Component. SDK | .NET SDK | 16.10.31320.204 | Vyžadováno
Microsoft. NetCore. Component. Web | Vývojové nástroje .NET | 16.10.31303.231 | Vyžadováno
Microsoft. VisualStudio. Component. Azure. AuthoringTools | Nástroje pro tvorbu Azure | 16.0.28625.61 | Vyžadováno
Microsoft. VisualStudio. Component. Azure. ClientLibs | Knihovny Azure pro .NET | 16.0.28315.86 | Vyžadováno
Microsoft. VisualStudio. Component. Azure. Compute. emulátor | Emulátor služby COMPUTE Azure | 16.10.31205.252 | Vyžadováno
Microsoft. VisualStudio. Component. Azure. Storage. emulátor | Emulátor úložiště Azure | 16.4.29313.120 | Vyžadováno
Microsoft. VisualStudio. Component. Průzkumník cloudu | Průzkumník cloudu | 16.0.28625.61 | Vyžadováno
Microsoft.VisualStudio.Component.Common.Azure.Tools | Nástroje pro připojení a publikování | 16.4.29409.204 | Vyžadováno
Microsoft.VisualStudio.Component.DockerTools | Kontejnerové vývojové nástroje | 16.4.29409.204 | Vyžadováno
Microsoft.VisualStudio.Component.FSharp | Podpora jazyka F# | 16.0.28315.86 | Vyžadováno
Microsoft.VisualStudio.Component.FSharp.WebTemplates | Podpora jazyka F# pro webové projekty | 16.3.29207.166 | Vyžadováno
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 16.0.28315.86 | Vyžadováno
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostika JavaScriptu | 16.0.28517.75 | Vyžadováno
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Podpora jazyků JavaScript a TypeScript | 16.10.31303.231 | Vyžadováno
Microsoft. VisualStudio. Component. ManagedDesktop. Core | Jádro úlohy spravované plochy | 16.4.29318.151 | Vyžadováno
Microsoft. VisualStudio. Component. MSODBC. SQL | SQL Server ovladač ODBC | 16.0.28625.61 | Vyžadováno
Microsoft. VisualStudio. Component. MSSQL. CMDLnUtils | SQL Server nástroje příkazového řádku | 16.0.28707.177 | Vyžadováno
Microsoft. VisualStudio. Component. NuGet | Správce balíčků NuGet | 16.1.28829.92 | Vyžadováno
Microsoft. VisualStudio. Component. Roslyn. Compiler | Kompilátory C# a Visual Basic Roslyn | 16.0.28714.129 | Vyžadováno
Microsoft. VisualStudio. Component. Roslyn. LanguageServices | C# a Visual Basic | 16.10.31205.252 | Vyžadováno
Microsoft. VisualStudio. Component. SQL. ADAL | Modul runtime SQL ADAL | 16.0.28517.75 | Vyžadováno
Microsoft.VisualStudio.Component.SQL.CLR | Datové typy CLR pro SQL Server | 16.0.28315.86 | Vyžadováno
Microsoft.VisualStudio.Component.SQL.DataSources | Zdroje dat pro podporu SQL Server dat | 16.0.28315.86 | Vyžadováno
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 16.0.28625.61 | Vyžadováno
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 16.3.29207.166 | Vyžadováno
Microsoft.VisualStudio.Component.TextTemplating | Transformace textových šablon | 16.0.28625.61 | Vyžadováno
Microsoft.VisualStudio.Component.TypeScript.4.2 | TypeScript 4.2 SDK | 16.0.31303.231 | Vyžadováno
Microsoft.VisualStudio.Component.Web | ASP.NET a webové vývojové nástroje | 16.10.31205.252 | Vyžadováno
Microsoft. VisualStudio. Component. Azure. požadavky | Požadavky na vývoj pro Azure | 16.10.31303.231 | Vyžadováno
Microsoft. VisualStudio. Component. AzureFunctions | Nástroje Azure WebJobs | 16.10.31205.180 | Vyžadováno
Microsoft. VisualStudio. Component. Web | Požadavky na ASP.NET a vývojové nástroje pro web | 16.10.31205.180 | Vyžadováno
Microsoft. VisualStudio. Component. WebToolsExtensions | Vývoj pro ASP.NET a web | 16.10.31205.180 | Vyžadováno
Microsoft. Component. Azure. datalake. Tools | Nástroje Azure Data Lake a Stream Analytics | 16.10.31205.252 | Doporučeno
Microsoft.Net. Component. 4.5.1. TargetingPack | Sada .NET Framework 4.5.1 targeting pack | 16.0.28517.75 | Doporučeno
Microsoft.Net. Component. 4.6. TargetingPack | Sada targeting pack .NET Framework 4,6 | 16.0.28517.75 | Doporučeno
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 cílení pack | 16.0.28517.75 | Doporučeno
Microsoft.Net.ComponentGroup.TargetingPacks.Common | .NET Framework 4–4.6 – vývojové nástroje | 16.0.28516.191 | Doporučeno
Microsoft.VisualStudio.Component.AspNet45 | Pokročilé ASP.NET funkcí | 16.10.31205.252 | Doporučeno
Microsoft.VisualStudio.Component.Azure.Kubernetes.Tools | Visual Studio Tools for Kubernetes | 16.10.31205.252 | Doporučeno
Microsoft.VisualStudio.Component.Azure.Powershell | Azure Powershell | 16.5.29515.121 | Doporučeno
Microsoft.VisualStudio.Component.Azure.ResourceManager.Tools | Azure Resource Manager nástroje | 16.4.29409.204 | Doporučeno
Microsoft.VisualStudio.Component.Azure.ServiceFabric.Tools | Nástroje Service Fabricu | 16.4.29313.120 | Doporučeno
Microsoft.VisualStudio.Component.Azure.Waverton | Základní nástroje pro Azure Cloud Services | 16.10.31205.252 | Doporučeno
Microsoft. VisualStudio. Component. Azure. Waverton. BuildTools | Nástroje pro vytváření Cloud Services pro Azure | 16.10.31205.252 | Doporučeno
Microsoft. VisualStudio. Component. Debugger. Snapshot | Ladicí program snímků | 16.5.29813.82 | Doporučeno
Microsoft. VisualStudio. Component. Debugger. TimeTravel | Čas cestovního ladicího programu | 16.10.31205.252 | Doporučeno
Microsoft. VisualStudio. Component. DiagnosticTools | Nástroje pro profilaci .NET | 16.10.31205.252 | Doporučeno
Microsoft. VisualStudio. Component. IntelliCode | IntelliCode | 16.10.31305.154 | Doporučeno
Microsoft. VisualStudio. Component. IntelliTrace. front-end | IntelliTrace | 16.5.29515.121 | Doporučeno
Microsoft. VisualStudio. Component. WebDeploy | Web Deploy | 16.0.28517.75 | Doporučeno
Microsoft. VisualStudio. Component. Azure. CloudServices | Azure Cloud Services nástroje | 16.10.31205.180 | Doporučeno
Microsoft.VisualStudio.ComponentGroup.Azure.ResourceManager.Tools | Azure Resource Manager nástroje | 16.0.28528.71 | Doporučeno
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
Microsoft. VisualStudio. Component. Azure. Storage. AzCopy | Azure Storage AzCopy | 16.0.28517.75 | Volitelné
Microsoft. VisualStudio. Component. WCF. Tools | Windows Communication Foundation | 16.0.28625.61 | Volitelné

## <a name="data-storage-and-processing"></a>Ukládání a zpracování dat

**ID:** Microsoft.VisualStudio.Workload.Data

**Popis:** Připojení, vývoj a testování datových řešení pomocí SQL Server, Azure Data Lake nebo Hadoop.

### <a name="components-included-by-this-workload"></a>Komponenty zahrnuté v této úlohu

ID komponenty | Name | Verze | Typ závislosti
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Služby jazyka Razor | 16.10.31205.252 | Doporučeno
Component.Microsoft.Web.LibraryManager | Správce knihovny | 16.10.31205.180 | Doporučeno
Component.Microsoft.WebTools.BrowserLink.WebLivePreview | Web Live Preview | 0.7.22.39845 | Doporučeno
Microsoft.Component.Azure.DataLake.Tools | Azure Data Lake a Stream Analytics Tools | 16.10.31205.252 | Doporučeno
Microsoft.Component.MSBuild | MSBuild | 16.5.29515.121 | Doporučeno
Microsoft.Net.Component.4.5.1.TargetingPack | .NET Framework 4.5.1 | 16.0.28517.75 | Doporučeno
Microsoft.Net. Component. 4.5.2. TargetingPack | Sada .NET Framework 4.5.2 targeting pack | 16.0.28517.75 | Doporučeno
Microsoft.Net. Component. 4.5. TargetingPack | Sada targeting pack .NET Framework 4,5 | 16.0.28517.75 | Doporučeno
Microsoft.Net. Component. 4.6. TargetingPack | Sada targeting pack .NET Framework 4,6 | 16.0.28517.75 | Doporučeno
Microsoft.Net. Component. 4.7.2. TargetingPack | Sada targeting pack .NET Framework 4.7.2 | 16.10.31205.252 | Doporučeno
Microsoft. NET. Component. 4.8. SDK | .NET Framework 4,8 SDK | 16.4.29313.120 | Doporučeno
Microsoft.Net. Component. 4. TargetingPack | Sada targeting pack .NET Framework 4 | 16.0.28517.75 | Doporučeno
Microsoft.Net. Component. DevelopmentPrerequisites | .NET Framework 4.7.2 – vývojové nástroje | 16.3.29207.166 | Doporučeno
Microsoft.Net.ComponentGroup.TargetingPacks.Common | .NET Framework 4–4.6 – vývojové nástroje | 16.0.28516.191 | Doporučeno
Microsoft.NetCore.Component.Runtime.3.1 | .NET Core 3.1 Runtime (LTS) | 16.10.31320.204 | Doporučeno
Microsoft.NetCore.Component.Runtime.5.0 | .NET 5.0 Runtime | 16.10.31320.204 | Doporučeno
Microsoft.NetCore.Component.SDK | .NET SDK | 16.10.31320.204 | Doporučeno
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Nástroje pro vytváření v Azure | 16.0.28625.61 | Doporučeno
Microsoft.VisualStudio.Component.Azure.ClientLibs | Knihovny Azure pro .NET | 16.0.28315.86 | Doporučeno
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Emulátor služby COMPUTE Azure | 16.10.31205.252 | Doporučeno
Microsoft. VisualStudio. Component. Azure. Storage. emulátor | Emulátor úložiště Azure | 16.4.29313.120 | Doporučeno
Microsoft. VisualStudio. Component. Azure. Waverton | Základní nástroje pro Azure Cloud Services | 16.10.31205.252 | Doporučeno
Microsoft. VisualStudio. Component. Azure. Waverton. BuildTools | Nástroje pro vytváření Cloud Services pro Azure | 16.10.31205.252 | Doporučeno
Microsoft. VisualStudio. Component. Průzkumník cloudu | Průzkumník cloudu | 16.0.28625.61 | Doporučeno
Microsoft. VisualStudio. Component. Common. Azure. Tools | Nástroje pro připojení a publikování | 16.4.29409.204 | Doporučeno
Microsoft.VisualStudio.Component.DockerTools | Kontejnerové vývojové nástroje | 16.4.29409.204 | Doporučeno
Microsoft. VisualStudio. Component. IISExpress | IIS Express  | 16.0.28315.86 | Doporučeno
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostika JavaScriptu | 16.0.28517.75 | Doporučeno
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Podpora jazyků JavaScript a TypeScript | 16.10.31303.231 | Doporučeno
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Jádro úloh spravovaného desktopového prostředí | 16.4.29318.151 | Doporučeno
Microsoft.VisualStudio.Component.MSODBC.SQL | SQL Server ovladače ODBC | 16.0.28625.61 | Doporučeno
Microsoft.VisualStudio.Component.MSSQL.CMDLnUtils | SQL Server nástroje příkazového řádku | 16.0.28707.177 | Doporučeno
Microsoft.VisualStudio.Component.NuGet | Správce balíčků NuGet | 16.1.28829.92 | Doporučeno
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilátory C# a Visual Basic Roslyn | 16.0.28714.129 | Doporučeno
Microsoft. VisualStudio. Component. Roslyn. LanguageServices | C# a Visual Basic | 16.10.31205.252 | Doporučeno
Microsoft. VisualStudio. Component. SQL. ADAL | Modul runtime SQL ADAL | 16.0.28517.75 | Doporučeno
Microsoft. VisualStudio. Component. SQL. CLR | Datové typy CLR pro SQL Server | 16.0.28315.86 | Doporučeno
Microsoft. VisualStudio. Component. SQL. DataSources | Zdroje dat pro podporu SQL Server | 16.0.28315.86 | Doporučeno
Microsoft. VisualStudio. Component. SQL. LocalDB. Runtime | SQL Server Express 2016 LocalDB | 16.0.28625.61 | Doporučeno
Microsoft. VisualStudio. Component. SQL. SSDT | SQL Server Data Tools | 16.3.29207.166 | Doporučeno
Microsoft. VisualStudio. Component. TextTemplating | Transformace textové šablony | 16.0.28625.61 | Doporučeno
Microsoft.VisualStudio.Component.TypeScript.4.2 | TypeScript 4.2 SDK | 16.0.31303.231 | Doporučeno
Microsoft.VisualStudio.Component.Web | ASP.NET a webové vývojové nástroje | 16.10.31205.252 | Doporučeno
Microsoft.VisualStudio.ComponentGroup.Web | Požadavky ASP.NET a webových vývojových nástrojů | 16.10.31205.180 | Doporučeno
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Vývoj pro ASP.NET a web | 16.10.31205.180 | Doporučeno
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 | 16.0.28517.75 | Volitelné
Microsoft.VisualStudio.Component.FSharp.Desktop | Podpora desktopových jazyků F# | 16.0.28315.86 | Volitelné

## <a name="data-science-and-analytical-applications"></a>Aplikace pro datovou vědu a analýzu

**ID:** Microsoft.VisualStudio.Workload.DataScience

**Popis:** Jazyky a nástroje pro vytváření aplikací pro datové vědy, včetně Pythonu a F#.

### <a name="components-included-by-this-workload"></a>Komponenty zahrnuté v této úlohu

ID součásti | Name | Verze | Typ závislosti
--- | --- | --- | ---
Microsoft. Component. PythonTools | Podpora jazyka Python | 16.10.31313.127 | Doporučeno
Microsoft. Component. PythonTools. Minicondax64 | Python miniconda (mimo podporu) | 16.10.31313.127 | Doporučeno
Microsoft. Component. PythonTools. Web | Podpora webu Pythonu | 16.10.31205.252 | Doporučeno
Microsoft.Net. Component. 4.6.1. TargetingPack | .NET Framework 4.6.1 targeting pack | 16.0.28517.75 | Doporučeno
Microsoft. VisualStudio. Component. Common. Azure. Tools | Nástroje pro připojení a publikování | 16.4.29409.204 | Doporučeno
Microsoft. VisualStudio. Component. FSharp. Desktop | Podpora jazyka F # pro Desktop | 16.0.28315.86 | Doporučeno
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Podpora jazyků JavaScript a TypeScript | 16.10.31303.231 | Doporučeno
Microsoft.VisualStudio.Component.NuGet | Správce balíčků NuGet | 16.1.28829.92 | Doporučeno
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilátory C# a Visual Basic Roslyn | 16.0.28714.129 | Doporučeno
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# a Visual Basic | 16.10.31205.252 | Doporučeno
Microsoft.VisualStudio.Component.TypeScript.4.2 | TypeScript 4.2 SDK | 16.0.31303.231 | Doporučeno
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 16.0.28517.75 | Doporučeno
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Vývoj pro ASP.NET a web | 16.10.31205.180 | Doporučeno
Microsoft.ComponentGroup.PythonTools.NativeDevelopment | Nativní vývojové nástroje pythonu | 16.10.31205.180 | Volitelné
Microsoft. VisualStudio. Component. Graphics. Tools | Ladicí program grafiky a Profiler GPU pro DirectX | 16.0.28625.61 | Volitelné
Microsoft. VisualStudio. Component. VC. CoreIde | Základní funkce C++ | 16.10.31205.252 | Volitelné
Microsoft. VisualStudio. Component. VC. DiagnosticTools | Nástroje pro profilaci C++ | 16.5.29515.121 | Volitelné
Microsoft. VisualStudio. Component. VC. Tools. x86. x64 | MSVC V142-VS 2019 C++ x64/x86 Build Tools (nejnovější) | 16.10.31205.252 | Volitelné
Microsoft. VisualStudio. Component. Windows10SDK | Windows Universal C Runtime | 16.4.29409.204 | Volitelné
Microsoft. VisualStudio. Component. Windows10SDK. 19041 | Windows 10 SDK (10.0.19041.0) | 16.10.31205.252 | Volitelné

## <a name="net-desktop-development"></a>Vývoj pro desktopy .NET

**ID:** Microsoft.VisualStudio.Workload.ManagedDesktop

**Popis:** Vytvářete aplikace WPF, model Windows Forms a konzolové aplikace pomocí C#, Visual Basic a F# s .NET a .NET Framework.

### <a name="components-included-by-this-workload"></a>Komponenty zahrnuté v této úlohu

ID komponenty | Name | Verze | Typ závislosti
--- | --- | --- | ---
Microsoft.Component.MSBuild | MSBuild | 16.5.29515.121 | Vyžadováno
Microsoft.Net.Component.4.7.2.TargetingPack | .NET Framework 4.7.2 | 16.10.31205.252 | Vyžadováno
Microsoft.Net.Component.4.8.SDK | .NET Framework 4.8 SDK | 16.4.29313.120 | Vyžadováno
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | .NET Framework 4.7.2 – vývojové nástroje | 16.3.29207.166 | Vyžadováno
Microsoft.NetCore.Component.Runtime.3.1 | .NET Core 3.1 Runtime (LTS) | 16.10.31320.204 | Vyžadováno
Microsoft.NetCore.Component.Runtime.5.0 | .NET 5,0 – modul runtime | 16.10.31320.204 | Vyžadováno
Microsoft. NetCore. Component. SDK | .NET SDK | 16.10.31320.204 | Vyžadováno
Microsoft. VisualStudio. Component. ManagedDesktop. Core | Jádro úlohy spravované plochy | 16.4.29318.151 | Vyžadováno
Microsoft. VisualStudio. Component. ManagedDesktop. požadavky | Nástroje pro vývoj desktopových aplikací .NET | 16.10.31205.180 | Vyžadováno
Microsoft. VisualStudio. Component. Roslyn. Compiler | Kompilátory C# a Visual Basic Roslyn | 16.0.28714.129 | Vyžadováno
Microsoft. VisualStudio. Component. Roslyn. LanguageServices | C# a Visual Basic | 16.10.31205.252 | Vyžadováno
Microsoft. VisualStudio. Component. SQL. CLR | Datové typy CLR pro SQL Server | 16.0.28315.86 | Vyžadováno
Microsoft. VisualStudio. Component. TextTemplating | Transformace textové šablony | 16.0.28625.61 | Vyžadováno
Component.Microsoft.VisualStudio.LiveShare | Live Share | 1.0.4062 | Doporučeno
Microsoft.ComponentGroup.Blend | Blend for Visual Studio | 16.0.28315.86 | Doporučeno
Microsoft.ComponentGroup.ClickOnce.Publish | Publikování ClickOnce pro .NET  | 16.10.31303.231 | Doporučeno
Microsoft.Net.Component.4.5.1.TargetingPack | .NET Framework 4.5.1 | 16.0.28517.75 | Doporučeno
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 | 16.0.28517.75 | Doporučeno
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 | 16.0.28517.75 | Doporučeno
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 | 16.0.28517.75 | Doporučeno
Microsoft.Net. Component. 4.6. TargetingPack | Sada targeting pack .NET Framework 4,6 | 16.0.28517.75 | Doporučeno
Microsoft.Net. Component. 4. TargetingPack | Sada targeting pack .NET Framework 4 | 16.0.28517.75 | Doporučeno
Microsoft.Net. Component. TargetingPacks. Common | .NET Framework nástroje pro vývoj 4 – 4,6 | 16.0.28516.191 | Doporučeno
Microsoft. NetCore. Component. DevelopmentTools | Vývojové nástroje .NET | 16.10.31303.231 | Doporučeno
Microsoft. VisualStudio. Component. Common. Azure. Tools | Nástroje pro připojení a publikování | 16.4.29409.204 | Doporučeno
Microsoft. VisualStudio. Component. Debugger. JustInTime | Ladicí program za běhu | 16.0.28517.75 | Doporučeno
Microsoft. VisualStudio. Component. DiagnosticTools | Nástroje pro profilaci .NET | 16.10.31205.252 | Doporučeno
Microsoft.VisualStudio.Component.DotNetModelBuilder | ML.NET Model Builder (Preview) | 16.10.31205.252 | Doporučeno
Microsoft.VisualStudio.Component.EntityFramework | Entity Framework 6 nástrojů | 16.0.28315.86 | Doporučeno
Microsoft.VisualStudio.Component.FSharp | Podpora jazyka F# | 16.0.28315.86 | Doporučeno
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 16.10.31305.154 | Doporučeno
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | 16.5.29515.121 | Doporučeno
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Podpora jazyků JavaScript a TypeScript | 16.10.31303.231 | Doporučeno
Microsoft.VisualStudio.Component.LiveUnitTesting | Live Unit Testing | 16.10.31205.252 | Doporučeno
Microsoft.VisualStudio.Component.NuGet | Správce balíčků NuGet | 16.1.28829.92 | Doporučeno
Microsoft. VisualStudio. Component. TypeScript. 4.2 | Sada TypeScript 4,2 SDK | 16.0.31303.231 | Doporučeno
Microsoft. VisualStudio. Component. WebToolsExtensions | Vývoj pro ASP.NET a web | 16.10.31205.180 | Doporučeno
Component. Dotfuscator | PreEmptive Protection – Dotfuscator | 16.10.31205.252 | Volitelné
Součást. Microsoft. VisualStudio. RazorExtension | Jazykové služby Razor | 16.10.31205.252 | Volitelné
Součást. Microsoft. Web. LibraryManager | Správce knihovny | 16.10.31205.180 | Volitelné
Komponenta. Microsoft. WebTools. BrowserLink. WebLivePreview | Web Live Preview | 0.7.22.39845 | Volitelné
Microsoft.Net. Component. 4.6.2. TargetingPack | Sada targeting pack .NET Framework 4.6.2 | 16.0.28517.75 | Volitelné
Microsoft.Net.Component.4.7.1.TargetingPack | .NET Framework 4.7.1 | 16.10.31205.252 | Volitelné
Microsoft.Net.Component.4.7.TargetingPack | .NET Framework 4.7 | 16.10.31205.252 | Volitelné
Microsoft.Net.Component.4.8.TargetingPack | .NET Framework 4.8 | 16.4.29313.120 | Volitelné
Microsoft.Net.ComponentGroup.4.6.1.DeveloperTools | .NET Framework 4.6.1 | 16.3.29207.166 | Volitelné
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | .NET Framework 4.6.2 – vývojové nástroje | 16.3.29207.166 | Volitelné
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | .NET Framework 4.7.1 | 16.3.29207.166 | Volitelné
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | .NET Framework 4.7 – vývojové nástroje | 16.3.29207.166 | Volitelné
Microsoft.Net. Component.. 4,8. DeveloperTools | Vývojové nástroje .NET Framework 4,8 | 16.4.29318.151 | Volitelné
Microsoft. NET. Core. Component. SDK. 2.1 | Runtime .NET Core 2,1 (LTS) | 16.10.31320.204 | Volitelné
Microsoft. VisualStudio. Component. ClassDesigner | Návrhář tříd | 16.0.28528.71 | Volitelné
Microsoft. VisualStudio. Component. CodeClone | Klon kódu | 16.4.29409.204 | Volitelné
Microsoft. VisualStudio. Component. CodeMap | Mapa kódu | 16.0.28625.61 | Volitelné
Microsoft. VisualStudio. Component. DependencyValidation. Enterprise | Ověřování závislostí v reálném čase | 16.0.28625.61 | Volitelné
Microsoft.VisualStudio.Component.DockerTools | Kontejnerové vývojové nástroje | 16.4.29409.204 | Volitelné
Microsoft. VisualStudio. Component. FSharp. Desktop | Podpora desktopových jazyků F# | 16.0.28315.86 | Volitelné
Microsoft.VisualStudio.Component.GraphDocument | Editor DGML | 16.0.28625.61 | Volitelné
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 16.0.28315.86 | Volitelné
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostika JavaScriptu | 16.0.28517.75 | Volitelné
Microsoft.VisualStudio.Component.MSODBC.SQL | SQL Server ovladače ODBC | 16.0.28625.61 | Volitelné
Microsoft.VisualStudio.Component.MSSQL.CMDLnUtils | SQL Server nástroje příkazového řádku | 16.0.28707.177 | Volitelné
Microsoft.VisualStudio.Component.PortableLibrary | Balíček cílení na přenosnou knihovnu .NET | 16.10.31205.252 | Volitelné
Microsoft. VisualStudio. Component. SQL. ADAL | Modul runtime SQL ADAL | 16.0.28517.75 | Volitelné
Microsoft. VisualStudio. Component. SQL. DataSources | Zdroje dat pro podporu SQL Server | 16.0.28315.86 | Volitelné
Microsoft. VisualStudio. Component. SQL. LocalDB. Runtime | SQL Server Express 2016 LocalDB | 16.0.28625.61 | Volitelné
Microsoft. VisualStudio. Component. SQL. SSDT | SQL Server Data Tools | 16.3.29207.166 | Volitelné
Microsoft. VisualStudio. Component. WCF. Tools | Windows Communication Foundation | 16.0.28625.61 | Volitelné
Microsoft. VisualStudio. Component. Web | ASP.NET a vývojové nástroje pro web | 16.10.31205.252 | Volitelné
Microsoft. VisualStudio. Component. ArchitectureTools. Managed | Nástroje pro architekturu a analýzy | 16.5.29514.35 | Volitelné
Microsoft.VisualStudio.ComponentGroup.MSIX. balení | Nástroje MSIX Packaging | 16.10.31205.180 | Volitelné
Microsoft.VisualStudio.ComponentGroup.Web | Požadavky ASP.NET a webových vývojových nástrojů | 16.10.31205.180 | Volitelné

## <a name="game-development-with-unity"></a>Vývoj her pomocí Unity

**ID:** Microsoft.VisualStudio.Workload.ManagedGame

**Popis:** Vytváření 2D a 3D her pomocí Unity, výkonného vývojového prostředí pro více platforem

### <a name="components-included-by-this-workload"></a>Komponenty zahrnuté v této úlohu

ID komponenty | Name | Verze | Typ závislosti
--- | --- | --- | ---
Microsoft.Net.Component.3.5.DeveloperTools | .NET Framework 3.5 – vývojové nástroje | 16.0.28517.75 | Vyžadováno
Microsoft.Net.Component.4.7.1.TargetingPack | .NET Framework 4.7.1 | 16.10.31205.252 | Vyžadováno
Microsoft.VisualStudio.Component.NuGet | Správce balíčků NuGet | 16.1.28829.92 | Vyžadováno
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilátory C# a Visual Basic Roslyn | 16.0.28714.129 | Vyžadováno
Microsoft. VisualStudio. Component. Roslyn. LanguageServices | C# a Visual Basic | 16.10.31205.252 | Vyžadováno
Microsoft. VisualStudio. Component. Unity | Visual Studio Tools for Unity | 16.0.28315.86 | Vyžadováno
Component. UnityEngine. x64 | Centrum Unity | 16.10.31205.252 | Doporučeno
Component. UnityEngine. x86 | Editor bitových procesorů Unity 5,6 32 | 16.1.28811.260 | Doporučeno

## <a name="linux-development-with-c"></a>Vývoj linuxových aplikací v jazyce C++

**ID:** Microsoft. VisualStudio. úlohy. NativeCrossPlat

**Popis:** Vytváření a ladění aplikací spuštěných v prostředí Linux.

### <a name="components-included-by-this-workload"></a>Součásti zahrnuté v tomto zatížení

ID součásti | Name | Verze | Typ závislosti
--- | --- | --- | ---
Component. MDD. Linux | C++ pro vývoj pro Linux | 16.5.29515.121 | Vyžadováno
Microsoft.VisualStudio.Component.VC.CoreIde | Základní funkce jazyka C++ | 16.10.31205.252 | Vyžadováno
Component.Linux.CMake | Nástroje C++ CMake pro Linux | 16.2.29003.222 | Doporučeno
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 16.10.31305.154 | Doporučeno
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Vývoj pro ASP.NET a web | 16.10.31205.180 | Doporučeno
Component.MDD.Linux.GCC.arm | Integrované vývojové nástroje a nástroje IoT | 16.5.29515.121 | Volitelné

## <a name="desktop-development-with-c"></a>Vývoj desktopových aplikací pomocí C++

**ID:** Microsoft.VisualStudio.Workload.NativeDesktop

**Popis:** Vytvářete moderní aplikace C++ pro Windows pomocí nástrojů podle vašeho výběru, včetně MSVC, Clang, CMake nebo MSBuild.

### <a name="components-included-by-this-workload"></a>Komponenty zahrnuté v této úlohu

ID komponenty | Name | Verze | Typ závislosti
--- | --- | --- | ---
Microsoft.Component.MSBuild | MSBuild | 16.5.29515.121 | Vyžadováno
Microsoft. VisualStudio. Component. ClassDesigner | Návrhář tříd | 16.0.28528.71 | Vyžadováno
Microsoft. VisualStudio. Component. CodeMap | Mapa kódu | 16.0.28625.61 | Vyžadováno
Microsoft. VisualStudio. Component. GraphDocument | Editor DGML | 16.0.28625.61 | Vyžadováno
Microsoft. VisualStudio. Component. Roslyn. Compiler | Kompilátory C# a Visual Basic Roslyn | 16.0.28714.129 | Vyžadováno
Microsoft. VisualStudio. Component. SQL. LocalDB. Runtime | SQL Server Express 2016 LocalDB | 16.0.28625.61 | Vyžadováno
Microsoft. VisualStudio. Component. TextTemplating | Transformace textové šablony | 16.0.28625.61 | Vyžadováno
Microsoft. VisualStudio. Component. VC. CoreIde | Základní funkce C++ | 16.10.31205.252 | Vyžadováno
Microsoft. VisualStudio. Component. VC. Redist. 14. nejnovější | Distribuovatelná aktualizace C++ 2019 | 16.5.29515.121 | Vyžadováno
Microsoft.VisualStudio.ComponentGroup.ArchitectureTools.Native | Nástroje architektury pro C++ | 16.0.28621.142 | Vyžadováno
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Core | Základní desktopové funkce jazyka C++ | 16.2.29012.281 | Vyžadováno
Component.Microsoft.VisualStudio.LiveShare | Live Share | 1.0.4062 | Doporučeno
Microsoft.VisualStudio.Component.Debugger.JustInTime | Ladicí program za běhu | 16.0.28517.75 | Doporučeno
Microsoft.VisualStudio.Component.Graphics.Tools | Ladicí program grafiky a profiler GPU pro DirectX | 16.0.28625.61 | Doporučeno
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 16.10.31305.154 | Doporučeno
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | 16.5.29515.121 | Doporučeno
Microsoft. VisualStudio. Component. JavaScript. TypeScript | Podpora jazyků JavaScript a TypeScript | 16.10.31303.231 | Doporučeno
Microsoft. VisualStudio. Component. NuGet | Správce balíčků NuGet | 16.1.28829.92 | Doporučeno
Microsoft. VisualStudio. Component. Roslyn. LanguageServices | C# a Visual Basic | 16.10.31205.252 | Doporučeno
Microsoft. VisualStudio. Component. TypeScript. 4.2 | Sada TypeScript 4,2 SDK | 16.0.31303.231 | Doporučeno
Microsoft. VisualStudio. Component. VC. ASAN | AddressSanitizer C++ | 16.10.31205.252 | Doporučeno
Microsoft. VisualStudio. Component. VC. ATL | C++ ATL pro nejnovější nástroje V142 Build (x86 & x64) | 16.4.29313.120 | Doporučeno
Microsoft. VisualStudio. Component. VC. CMake. Project | Nástroje C++ CMake pro Windows | 16.3.29103.31 | Doporučeno
Microsoft.VisualStudio.Component.VC.DiagnosticTools | Nástroje pro profilaci jazyka C++ | 16.5.29515.121 | Doporučeno
Microsoft.VisualStudio.Component.VC.TestAdapterForBoostTest | Testovací adaptér pro Boost.Test | 16.0.28517.75 | Doporučeno
Microsoft.VisualStudio.Component.VC.TestAdapterForGoogleTest | Testovací adaptér pro Google Test | 16.0.28517.75 | Doporučeno
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | MSVC v142 – buildovací nástroje VS 2019 C++ x64/x86 (nejnovější) | 16.10.31205.252 | Doporučeno
Microsoft.VisualStudio.Component.Windows10SDK.19041 | Windows 10 SDK (10.0.19041.0) | 16.10.31205.252 | Doporučeno
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Vývoj pro ASP.NET a web | 16.10.31205.180 | Doporučeno
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions.CMake | Editor JSON | 16.10.31205.180 | Doporučeno
Component.Incredibuild | IncrediBuild – zrychlení sestavení | 16.10.31205.252 | Volitelné
Component. IncredibuildMenu | IncrediBuildMenu | 1.5.0.13 | Volitelné
Microsoft. Component. VC. Runtime. UCRTSDK | Sada Windows Universal CRT SDK | 16.0.28625.61 | Volitelné
Microsoft.Net. Component. 4.6.1. TargetingPack | .NET Framework 4.6.1 targeting pack | 16.0.28517.75 | Volitelné
Microsoft. NET. Component. 4.8. SDK | .NET Framework 4,8 SDK | 16.4.29313.120 | Volitelné
Microsoft. VisualStudio. Component. JavaScript. Diagnostics | Diagnostika JavaScriptu | 16.0.28517.75 | Volitelné
Microsoft. VisualStudio. Component. VC. 140 | Nástroje pro sestavení MSVC v140-VS 2015 C++ (v 14.00) | 16.10.31205.252 | Volitelné
Microsoft.VisualStudio.Component.VC.ATLMFC | Knihovna MFC jazyka C++ pro nejnovější nástroje sestavení v142 (x86 & x64) | 16.4.29313.120 | Volitelné
Microsoft.VisualStudio.Component.VC.CLI.Support | Podpora C++/CLI pro nástroje sestavení v142 (nejnovější) | 16.10.31205.252 | Volitelné
Microsoft.VisualStudio.Component.VC.Llvm.Clang | C++ Clang Compiler for Windows (11.0.0) | 16.10.31205.252 | Volitelné
Microsoft.VisualStudio.Component.VC.Llvm.ClangToolset | C++ Clang-cl pro nástroje sestavení v142 (x64/x86) | 16.3.29207.166 | Volitelné
Microsoft.VisualStudio.Component.VC.Modules.x86.x64 | Moduly C++ pro buildovací nástroje v142 (x64/x86 – experimentální) | 16.0.28625.61 | Volitelné
Microsoft.VisualStudio.Component.VC.Tools.ARM64 | MSVC v142 – buildovací nástroje C++ ARM64 sady VS 2019 (nejnovější) | 16.10.31205.252 | Volitelné
Microsoft.VisualStudio.Component.VC.v141.x86.x64 | MSVC v141 – buildovací nástroje VS 2017 C++ x64/x86 (verze 14.16) | 16.10.31205.252 | Volitelné
Microsoft. VisualStudio. Component. Windows10SDK. 16299 | Windows 10 SDK (10.0.16299.0) | 16.10.31205.252 | Volitelné
Microsoft. VisualStudio. Component. Windows10SDK. 17134 | Windows 10 SDK (10.0.17134.0) | 16.10.31205.252 | Volitelné
Microsoft. VisualStudio. Component. Windows10SDK. 17763 | Windows 10 SDK (10.0.17763.0) | 16.0.28517.75 | Volitelné
Microsoft. VisualStudio. Component. Windows10SDK. 18362 | Windows 10 SDK (10.0.18362.0) | 16.1.28829.92 | Volitelné
Microsoft. VisualStudio. Component. NativeDesktop. LLVM. Clang | C++ Clang Tools pro Windows (11.0.0-x64/x86) | 16.10.31205.180 | Volitelné

## <a name="game-development-with-c"></a>Vývoj her v jazyce C++

**ID:** Microsoft. VisualStudio. úlohy. NativeGame

**Popis:** Využijte výhod C++ k sestavování profesionálních her využívajících rozhraní DirectX, Unreal nebo Cocos2d.

### <a name="components-included-by-this-workload"></a>Součásti zahrnuté v tomto zatížení

ID součásti | Name | Verze | Typ závislosti
--- | --- | --- | ---
Microsoft.VisualStudio.Component.VC.CoreIde | Základní funkce jazyka C++ | 16.10.31205.252 | Vyžadováno
Microsoft.VisualStudio.Component.VC.Redist.14.Latest | Distribuovatelná aktualizace C++ 2019 | 16.5.29515.121 | Vyžadováno
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | MSVC v142 – buildovací nástroje VS 2019 C++ x64/x86 (nejnovější) | 16.10.31205.252 | Vyžadováno
Microsoft.VisualStudio.Component.Windows10SDK | Windows Universal C Runtime | 16.4.29409.204 | Vyžadováno
Microsoft.VisualStudio.Component.Graphics.Tools | Ladicí program grafiky a profiler GPU pro DirectX | 16.0.28625.61 | Doporučeno
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 16.10.31305.154 | Doporučeno
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | 16.5.29515.121 | Doporučeno
Microsoft. VisualStudio. Component. VC. ASAN | AddressSanitizer C++ | 16.10.31205.252 | Doporučeno
Microsoft. VisualStudio. Component. VC. DiagnosticTools | Nástroje pro profilaci C++ | 16.5.29515.121 | Doporučeno
Microsoft. VisualStudio. Component. Windows10SDK. 19041 | Windows 10 SDK (10.0.19041.0) | 16.10.31205.252 | Doporučeno
Komponenta. Android. NDK. R16B | Android NDK (R16B) | 16.10.31320.204 | Volitelné
Component. Android. SDK25. Private | Instalace Android SDK (úroveň rozhraní API 25) (místní instalace pro vývoj pro mobilní zařízení pomocí C++) | 16.0.28625.61 | Volitelné
Component. ANT | Apache Ant (1.9.3) | 1.9.3.8 | Volitelné
Component. Cocos | Cocos | 16.0.28315.86 | Volitelné
Component.Incredibuild | Incredibuild – Zrychlení sestavení | 16.10.31205.252 | Volitelné
Component.IncredibuildMenu | IncrediBuildMenu | 1.5.0.13 | Volitelné
Component.MDD.Android | Vývojové nástroje pro C++ pro Android | 16.0.28517.75 | Volitelné
Component.OpenJDK | OpenJDK (distribuce Microsoftu) | 16.10.31303.311 | Volitelné
Component.Unreal | Instalační program Unreal Engine | 16.1.28810.153 | Volitelné
Component.Unreal.Android | Podpora integrovaného vývojového prostředí Androidu pro unreal engine | 16.1.28810.153 | Volitelné
Microsoft.Net.Component.4.5.1.TargetingPack | .NET Framework 4.5.1 | 16.0.28517.75 | Volitelné
Microsoft.Net. Component. 4.5.2. TargetingPack | Sada .NET Framework 4.5.2 targeting pack | 16.0.28517.75 | Volitelné
Microsoft.Net. Component. 4.5. TargetingPack | Sada targeting pack .NET Framework 4,5 | 16.0.28517.75 | Volitelné
Microsoft.Net. Component. 4.6.2. TargetingPack | Sada targeting pack .NET Framework 4.6.2 | 16.0.28517.75 | Volitelné
Microsoft.Net. Component. 4.6. TargetingPack | Sada targeting pack .NET Framework 4,6 | 16.0.28517.75 | Volitelné
Microsoft.Net. Component. 4.7.2. TargetingPack | Sada targeting pack .NET Framework 4.7.2 | 16.10.31205.252 | Volitelné
Microsoft. NET. Component. 4.8. SDK | .NET Framework 4,8 SDK | 16.4.29313.120 | Volitelné
Microsoft.Net. Component. 4. TargetingPack | .NET Framework 4 cílení pack | 16.0.28517.75 | Volitelné
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | .NET Framework 4.7.2 – vývojové nástroje | 16.3.29207.166 | Volitelné
Microsoft.Net.ComponentGroup.TargetingPacks.Common | .NET Framework 4–4.6 – vývojové nástroje | 16.0.28516.191 | Volitelné
Microsoft.VisualStudio.Component.NuGet.BuildTools | Cíle a úlohy sestavení NuGet | 16.1.28829.92 | Volitelné
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilátory C# a Visual Basic Roslyn | 16.0.28714.129 | Volitelné
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# a Visual Basic | 16.10.31205.252 | Volitelné
Microsoft.VisualStudio.Component.Windows10SDK.16299 | Windows 10 SDK (10.0.16299.0) | 16.10.31205.252 | Volitelné
Microsoft.VisualStudio.Component.Windows10SDK.17134 | Windows 10 SDK (10.0.17134.0) | 16.10.31205.252 | Volitelné
Microsoft. VisualStudio. Component. Windows10SDK. 17763 | Windows 10 SDK (10.0.17763.0) | 16.0.28517.75 | Volitelné
Microsoft. VisualStudio. Component. Windows10SDK. 18362 | Windows 10 SDK (10.0.18362.0) | 16.1.28829.92 | Volitelné

## <a name="mobile-development-with-c"></a>Vývoj mobilních aplikací v jazyce C++

**ID:** Microsoft. VisualStudio. úlohy. NativeMobile

**Popis:** Vytvářejte aplikace pro různé platformy pro iOS, Android nebo Windows pomocí C++.

### <a name="components-included-by-this-workload"></a>Součásti zahrnuté v tomto zatížení

ID součásti | Name | Verze | Typ závislosti
--- | --- | --- | ---
Component. Android. SDK25. Private | Instalace Android SDK (úroveň rozhraní API 25) (místní instalace pro vývoj pro mobilní zařízení pomocí C++) | 16.0.28625.61 | Vyžadováno
Component. OpenJDK | OpenJDK (distribuce Microsoft) | 16.10.31303.311 | Vyžadováno
Microsoft. VisualStudio. Component. VC. CoreIde | Základní funkce jazyka C++ | 16.10.31205.252 | Vyžadováno
Component.Android.NDK.R16B | Android NDK (R16B) | 16.10.31320.204 | Doporučeno
Component.Ant | Apache Ant (1.9.3) | 1.9.3.8 | Doporučeno
Component.MDD.Android | Vývojové nástroje pro C++ pro Android | 16.0.28517.75 | Doporučeno
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 16.10.31305.154 | Doporučeno
Component.Android.NDK.R16B_3264 | Android NDK (R16B) (32bitová verze) | 16.10.31320.204 | Volitelné
Component.Google.Android.Emulator.API25.Private | Google Android Emulator (rozhraní API úrovně 25) (místní instalace) | 16.1.28810.153 | Volitelné
Component.HAXM.Private | Intel Hardware Accelerated Execution Manager (modul HAXM) (místní instalace) | 16.0.28528.71 | Volitelné
Component. IncrediBuild | IncrediBuild – zrychlení sestavení | 16.10.31205.252 | Volitelné
Component. IncredibuildMenu | IncrediBuildMenu | 1.5.0.13 | Volitelné
Component. MDD. IOS | Vývojové nástroje C++ pro iOS | 16.0.28517.75 | Volitelné

## <a name="net-cross-platform-development"></a>Vývoj pro různé platformy .NET

**ID:** Microsoft. VisualStudio. úlohy. NetCoreTools

**Popis:** Vytvářejte aplikace pro různé platformy pomocí .NET, ASP.NET Core, HTML/JavaScript a kontejnerů včetně podpory Docker.

### <a name="components-included-by-this-workload"></a>Součásti zahrnuté v tomto zatížení

ID součásti | Name | Verze | Typ závislosti
--- | --- | --- | ---
Součást. Microsoft. VisualStudio. RazorExtension | Jazykové služby Razor | 16.10.31205.252 | Vyžadováno
Component.Microsoft.Web.LibraryManager | Správce knihovny | 16.10.31205.180 | Vyžadováno
Component.Microsoft.WebTools.BrowserLink.WebLivePreview | Web Live Preview | 0.7.22.39845 | Vyžadováno
Microsoft.Component.MSBuild | MSBuild | 16.5.29515.121 | Vyžadováno
Microsoft.ComponentGroup.ClickOnce.Publish | Publikování ClickOnce pro .NET  | 16.10.31303.231 | Vyžadováno
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 | 16.0.28517.75 | Vyžadováno
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 | 16.0.28517.75 | Vyžadováno
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 | 16.0.28517.75 | Vyžadováno
Microsoft.Net.Component.4.7.2.TargetingPack | Sada targeting pack .NET Framework 4.7.2 | 16.10.31205.252 | Vyžadováno
Microsoft. NET. Component. 4.8. SDK | .NET Framework 4,8 SDK | 16.4.29313.120 | Vyžadováno
Microsoft.Net. Component. DevelopmentPrerequisites | Vývojové nástroje .NET Framework 4.7.2 | 16.3.29207.166 | Vyžadováno
Microsoft. NetCore. Component. DevelopmentTools | Vývojové nástroje .NET | 16.10.31303.231 | Vyžadováno
Microsoft. NetCore. Component. Runtime. 3.1 | Runtime .NET Core 3,1 (LTS) | 16.10.31320.204 | Vyžadováno
Microsoft. NetCore. Component. Runtime. 5.0 | .NET 5,0 – modul runtime | 16.10.31320.204 | Vyžadováno
Microsoft. NetCore. Component. SDK | .NET SDK | 16.10.31320.204 | Vyžadováno
Microsoft. NetCore. Component. Web | Vývojové nástroje pro .NET | 16.10.31303.231 | Vyžadováno
Microsoft.VisualStudio.Component.Common.Azure.Tools | Nástroje pro připojení a publikování | 16.4.29409.204 | Vyžadováno
Microsoft.VisualStudio.Component.DockerTools | Kontejnerové vývojové nástroje | 16.4.29409.204 | Vyžadováno
Microsoft.VisualStudio.Component.FSharp | Podpora jazyka F# | 16.0.28315.86 | Vyžadováno
Microsoft.VisualStudio.Component.FSharp.WebTemplates | Podpora jazyka F# pro webové projekty | 16.3.29207.166 | Vyžadováno
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 16.0.28315.86 | Vyžadováno
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostika JavaScriptu | 16.0.28517.75 | Vyžadováno
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Podpora jazyků JavaScript a TypeScript | 16.10.31303.231 | Vyžadováno
Microsoft. VisualStudio. Component. ManagedDesktop. Core | Jádro úlohy spravované plochy | 16.4.29318.151 | Vyžadováno
Microsoft. VisualStudio. Component. MSODBC. SQL | SQL Server ovladač ODBC | 16.0.28625.61 | Vyžadováno
Microsoft. VisualStudio. Component. MSSQL. CMDLnUtils | SQL Server nástroje příkazového řádku | 16.0.28707.177 | Vyžadováno
Microsoft. VisualStudio. Component. NuGet | Správce balíčků NuGet | 16.1.28829.92 | Vyžadováno
Microsoft. VisualStudio. Component. Roslyn. Compiler | Kompilátory C# a Visual Basic Roslyn | 16.0.28714.129 | Vyžadováno
Microsoft. VisualStudio. Component. Roslyn. LanguageServices | C# a Visual Basic | 16.10.31205.252 | Vyžadováno
Microsoft. VisualStudio. Component. SQL. ADAL | Modul runtime SQL ADAL | 16.0.28517.75 | Vyžadováno
Microsoft.VisualStudio.Component.SQL.CLR | Datové typy CLR pro SQL Server | 16.0.28315.86 | Vyžadováno
Microsoft.VisualStudio.Component.SQL.DataSources | Zdroje dat pro podporu SQL Server dat | 16.0.28315.86 | Vyžadováno
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 16.0.28625.61 | Vyžadováno
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 16.3.29207.166 | Vyžadováno
Microsoft.VisualStudio.Component.TextTemplating | Transformace textových šablon | 16.0.28625.61 | Vyžadováno
Microsoft.VisualStudio.Component.TypeScript.4.2 | TypeScript 4.2 SDK | 16.0.31303.231 | Vyžadováno
Microsoft.VisualStudio.ComponentGroup.Web | Požadavky na ASP.NET a vývojové nástroje pro web | 16.10.31205.180 | Vyžadováno
Microsoft. VisualStudio. Component. WebToolsExtensions | Vývoj pro ASP.NET a web | 16.10.31205.180 | Vyžadováno
Součást. Microsoft. VisualStudio. LiveShare | Live Share | 1.0.4062 | Doporučeno
Součást. Microsoft. VisualStudio. Web. AzureFunctions | Nástroje Azure WebJobs | 16.10.31205.252 | Doporučeno
Microsoft. VisualStudio. Component. AppInsights. Tools | Vývojářské analytické nástroje | 16.5.29515.121 | Doporučeno
Microsoft. VisualStudio. Component. Azure. AuthoringTools | Nástroje pro tvorbu Azure | 16.0.28625.61 | Doporučeno
Microsoft. VisualStudio. Component. Azure. ClientLibs | Knihovny Azure pro .NET | 16.0.28315.86 | Doporučeno
Microsoft. VisualStudio. Component. Azure. Compute. emulátor | Emulátor služby COMPUTE Azure | 16.10.31205.252 | Doporučeno
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Emulátor úložiště Azure | 16.4.29313.120 | Doporučeno
Microsoft.VisualStudio.Component.CloudExplorer | Průzkumník cloudu | 16.0.28625.61 | Doporučeno
Microsoft.VisualStudio.Component.Debugger.JustInTime | Ladicí program za běhu | 16.0.28517.75 | Doporučeno
Microsoft.VisualStudio.Component.Debugger.Snapshot | Ladicí program snímků | 16.5.29813.82 | Doporučeno
Microsoft.VisualStudio.Component.Debugger.TimeTravel | Ladicí program pro cestu v čase | 16.10.31205.252 | Doporučeno
Microsoft.VisualStudio.Component.DiagnosticTools | Nástroje pro profilaci .NET | 16.10.31205.252 | Doporučeno
Microsoft.VisualStudio.Component.DotNetModelBuilder | ML.NET Model Builder (Preview) | 16.10.31205.252 | Doporučeno
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 16.10.31305.154 | Doporučeno
Microsoft. VisualStudio. Component. IntelliTrace. front-end | IntelliTrace | 16.5.29515.121 | Doporučeno
Microsoft. VisualStudio. Component. LiveUnitTesting | Live Unit Testing | 16.10.31205.252 | Doporučeno
Microsoft. VisualStudio. Component. Web | ASP.NET a vývojové nástroje pro web | 16.10.31205.252 | Doporučeno
Microsoft. VisualStudio. Component. WebDeploy | Web Deploy | 16.0.28517.75 | Doporučeno
Microsoft. VisualStudio. Component. WslDebugging | Ladění .NET pomocí WSL 2 | 16.10.31303.231 | Doporučeno
Microsoft. VisualStudio. Component. AzureFunctions | Nástroje Azure WebJobs | 16.10.31205.180 | Doporučeno
Microsoft. VisualStudio. Component. Web. CloudTools | Cloudové nástroje pro vývoj pro web | 16.10.31205.180 | Doporučeno
Microsoft. NET. Core. Component. SDK. 2.1 | .NET Core 2.1 Runtime (LTS) | 16.10.31320.204 | Volitelné
Microsoft.VisualStudio.ComponentGroup.IISDevelopment | Podpora služby IIS pro dobu vývoje | 16.10.31205.180 | Volitelné
Microsoft.VisualStudio.ComponentGroup.MSIX.Packaging | Nástroje MSIX Packaging | 16.10.31205.180 | Volitelné

## <a name="mobile-development-with-net"></a>Vývoj mobilních aplikací pomocí .NET

**ID:** Microsoft.VisualStudio.Workload.NetCrossPlat

**Popis:** Vytváření aplikací pro více platforem pro iOS, Android nebo Windows pomocí Xamarinu

### <a name="components-included-by-this-workload"></a>Komponenty zahrnuté v této úlohu

ID komponenty | Name | Verze | Typ závislosti
--- | --- | --- | ---
Component.OpenJDK | OpenJDK (distribuce Microsoftu) | 16.10.31303.311 | Vyžadováno
Component.Xamarin | Xamarin | 16.10.31205.252 | Vyžadováno
Component.Xamarin.RemotedSimulator | Vzdálený simulátor Xamarin | 16.10.31205.252 | Vyžadováno
Microsoft. Component. MSBuild | MSBuild | 16.5.29515.121 | Vyžadováno
Microsoft. Component. ClickOnce. Publish | Publikování ClickOnce pro .NET  | 16.10.31303.231 | Vyžadováno
Microsoft.Net. Component. 4.6.1. TargetingPack | .NET Framework 4.6.1 targeting pack | 16.0.28517.75 | Vyžadováno
Microsoft.Net. Component. 4.7.2. TargetingPack | Sada targeting pack .NET Framework 4.7.2 | 16.10.31205.252 | Vyžadováno
Microsoft. NET. Component. 4.8. SDK | .NET Framework 4,8 SDK | 16.4.29313.120 | Vyžadováno
Microsoft.Net. Component. DevelopmentPrerequisites | Vývojové nástroje .NET Framework 4.7.2 | 16.3.29207.166 | Vyžadováno
Microsoft. NetCore. Component. DevelopmentTools | Vývojové nástroje pro .NET | 16.10.31303.231 | Vyžadováno
Microsoft.NetCore.Component.Runtime.3.1 | .NET Core 3.1 Runtime (LTS) | 16.10.31320.204 | Vyžadováno
Microsoft.NetCore.Component.Runtime.5.0 | .NET 5.0 Runtime | 16.10.31320.204 | Vyžadováno
Microsoft.NetCore.Component.SDK | .NET SDK | 16.10.31320.204 | Vyžadováno
Microsoft.VisualStudio.Component.FSharp | Podpora jazyka F# | 16.0.28315.86 | Vyžadováno
Microsoft.VisualStudio.Component.Merq | Běžné interní nástroje Xamarinu | 16.2.29012.281 | Vyžadováno
Microsoft.VisualStudio.Component.MonoDebugger | Ladicí program Mono | 16.0.28517.75 | Vyžadováno
Microsoft.VisualStudio.Component.NuGet | Správce balíčků NuGet | 16.1.28829.92 | Vyžadováno
Microsoft. VisualStudio. Component. Roslyn. Compiler | Kompilátory C# a Visual Basic Roslyn | 16.0.28714.129 | Vyžadováno
Microsoft. VisualStudio. Component. Roslyn. LanguageServices | C# a Visual Basic | 16.10.31205.252 | Vyžadováno
Microsoft. VisualStudio. Component. WebToolsExtensions. TemplateEngine | ASP.NET šablonování Engine | 16.10.31205.180 | Vyžadováno
Komponenta. Android. SDK30 | Instalace Android SDK (úroveň rozhraní API 30) | 16.10.31205.252 | Doporučeno
Microsoft. VisualStudio. Component. IntelliCode | IntelliCode | 16.10.31305.154 | Doporučeno

## <a name="aspnet-and-web-development"></a>Vývoj pro ASP.NET a web

**ID:** Microsoft. VisualStudio. úlohy. NetWeb

**Popis:** Vytvářejte webové aplikace pomocí ASP.NET Core, ASP.NET, HTML/JavaScript a kontejnerů včetně podpory Docker.

### <a name="components-included-by-this-workload"></a>Součásti zahrnuté v tomto zatížení

ID součásti | Name | Verze | Typ závislosti
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Služby jazyka Razor | 16.10.31205.252 | Vyžadováno
Component.Microsoft.Web.LibraryManager | Správce knihovny | 16.10.31205.180 | Vyžadováno
Component.Microsoft.WebTools.BrowserLink.WebLivePreview | Web Live Preview | 0.7.22.39845 | Vyžadováno
Microsoft.Component.MSBuild | MSBuild | 16.5.29515.121 | Vyžadováno
Microsoft.ComponentGroup.ClickOnce.Publish | Publikování ClickOnce pro .NET  | 16.10.31303.231 | Vyžadováno
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 | 16.0.28517.75 | Vyžadováno
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 | 16.0.28517.75 | Vyžadováno
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 targeting pack | 16.0.28517.75 | Vyžadováno
Microsoft.Net. Component. 4.7.2. TargetingPack | Sada targeting pack .NET Framework 4.7.2 | 16.10.31205.252 | Vyžadováno
Microsoft. NET. Component. 4.8. SDK | .NET Framework 4,8 SDK | 16.4.29313.120 | Vyžadováno
Microsoft.Net. Component. DevelopmentPrerequisites | Vývojové nástroje .NET Framework 4.7.2 | 16.3.29207.166 | Vyžadováno
Microsoft. NetCore. Component. DevelopmentTools | Vývojové nástroje .NET | 16.10.31303.231 | Vyžadováno
Microsoft. NetCore. Component. Runtime. 3.1 | Runtime .NET Core 3,1 (LTS) | 16.10.31320.204 | Vyžadováno
Microsoft. NetCore. Component. Runtime. 5.0 | .NET 5,0 – modul runtime | 16.10.31320.204 | Vyžadováno
Microsoft.NetCore.Component.SDK | .NET SDK | 16.10.31320.204 | Vyžadováno
Microsoft.NetCore.Component.Web | Vývojové nástroje pro .NET | 16.10.31303.231 | Vyžadováno
Microsoft.VisualStudio.Component.Common.Azure.Tools | Nástroje pro připojení a publikování | 16.4.29409.204 | Vyžadováno
Microsoft.VisualStudio.Component.DockerTools | Kontejnerové vývojové nástroje | 16.4.29409.204 | Vyžadováno
Microsoft.VisualStudio.Component.FSharp | Podpora jazyka F# | 16.0.28315.86 | Vyžadováno
Microsoft.VisualStudio.Component.FSharp.WebTemplates | Podpora jazyka F# pro webové projekty | 16.3.29207.166 | Vyžadováno
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 16.0.28315.86 | Vyžadováno
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostika JavaScriptu | 16.0.28517.75 | Vyžadováno
Microsoft. VisualStudio. Component. JavaScript. TypeScript | Podpora jazyků JavaScript a TypeScript | 16.10.31303.231 | Vyžadováno
Microsoft. VisualStudio. Component. ManagedDesktop. Core | Jádro úlohy spravované plochy | 16.4.29318.151 | Vyžadováno
Microsoft. VisualStudio. Component. MSODBC. SQL | SQL Server ovladač ODBC | 16.0.28625.61 | Vyžadováno
Microsoft. VisualStudio. Component. MSSQL. CMDLnUtils | SQL Server nástroje příkazového řádku | 16.0.28707.177 | Vyžadováno
Microsoft. VisualStudio. Component. NuGet | Správce balíčků NuGet | 16.1.28829.92 | Vyžadováno
Microsoft. VisualStudio. Component. Roslyn. Compiler | Kompilátory C# a Visual Basic Roslyn | 16.0.28714.129 | Vyžadováno
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# a Visual Basic | 16.10.31205.252 | Vyžadováno
Microsoft.VisualStudio.Component.SQL.ADAL | Modul runtime SQL ADAL | 16.0.28517.75 | Vyžadováno
Microsoft.VisualStudio.Component.SQL.CLR | Datové typy CLR pro SQL Server | 16.0.28315.86 | Vyžadováno
Microsoft.VisualStudio.Component.SQL.DataSources | Zdroje dat pro podporu SQL Server dat | 16.0.28315.86 | Vyžadováno
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 16.0.28625.61 | Vyžadováno
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 16.3.29207.166 | Vyžadováno
Microsoft.VisualStudio.Component.TextTemplating | Transformace textových šablon | 16.0.28625.61 | Vyžadováno
Microsoft.VisualStudio.Component.TypeScript.4.2 | Sada TypeScript 4,2 SDK | 16.0.31303.231 | Vyžadováno
Microsoft. VisualStudio. Component. Web | ASP.NET a vývojové nástroje pro web | 16.10.31205.252 | Vyžadováno
Microsoft. VisualStudio. Component. Web | Požadavky na ASP.NET a vývojové nástroje pro web | 16.10.31205.180 | Vyžadováno
Microsoft. VisualStudio. Component. Web. Client | ASP.NET a vývojové nástroje pro web | 16.10.31205.180 | Vyžadováno
Microsoft. VisualStudio. Component. WebToolsExtensions | Vývoj pro ASP.NET a web | 16.10.31205.180 | Vyžadováno
Součást. Microsoft. VisualStudio. LiveShare | Live Share | 1.0.4062 | Doporučeno
Součást. Microsoft. VisualStudio. Web. AzureFunctions | Nástroje Azure WebJobs | 16.10.31205.252 | Doporučeno
Microsoft.Net. Component. 4.5.1. TargetingPack | Sada .NET Framework 4.5.1 targeting pack | 16.0.28517.75 | Doporučeno
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework 4.6 | 16.0.28517.75 | Doporučeno
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 cílení pack | 16.0.28517.75 | Doporučeno
Microsoft.Net.ComponentGroup.TargetingPacks.Common | .NET Framework 4–4.6 – vývojové nástroje | 16.0.28516.191 | Doporučeno
Microsoft.VisualStudio.Component.AppInsights.Tools | Vývojářské analytické nástroje | 16.5.29515.121 | Doporučeno
Microsoft.VisualStudio.Component.AspNet45 | Pokročilé ASP.NET funkcí | 16.10.31205.252 | Doporučeno
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Nástroje pro vytváření v Azure | 16.0.28625.61 | Doporučeno
Microsoft.VisualStudio.Component.Azure.ClientLibs | Knihovny Azure pro .NET | 16.0.28315.86 | Doporučeno
Microsoft. VisualStudio. Component. Azure. Compute. emulátor | Emulátor služby COMPUTE Azure | 16.10.31205.252 | Doporučeno
Microsoft. VisualStudio. Component. Azure. Storage. emulátor | Emulátor úložiště Azure | 16.4.29313.120 | Doporučeno
Microsoft. VisualStudio. Component. Průzkumník cloudu | Průzkumník cloudu | 16.0.28625.61 | Doporučeno
Microsoft. VisualStudio. Component. Debugger. JustInTime | Ladicí program za běhu | 16.0.28517.75 | Doporučeno
Microsoft. VisualStudio. Component. Debugger. Snapshot | Ladicí program snímků | 16.5.29813.82 | Doporučeno
Microsoft. VisualStudio. Component. Debugger. TimeTravel | Čas cestovního ladicího programu | 16.10.31205.252 | Doporučeno
Microsoft. VisualStudio. Component. DiagnosticTools | Nástroje pro profilaci .NET | 16.10.31205.252 | Doporučeno
Microsoft.VisualStudio.Component.EntityFramework | Entity Framework 6 nástrojů | 16.0.28315.86 | Doporučeno
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 16.10.31305.154 | Doporučeno
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | 16.5.29515.121 | Doporučeno
Microsoft.VisualStudio.Component.LiveUnitTesting | Live Unit Testing | 16.10.31205.252 | Doporučeno
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 16.0.28517.75 | Doporučeno
Microsoft.VisualStudio.Component.WslDebugging | Ladění .NET s WSL 2 | 16.10.31303.231 | Doporučeno
Microsoft.VisualStudio.ComponentGroup.AzureFunctions | Azure WebJobs nástroje | 16.10.31205.180 | Doporučeno
Microsoft.VisualStudio.ComponentGroup.Web.CloudTools | Cloudové nástroje pro vývoj pro web | 16.10.31205.180 | Doporučeno
Microsoft.Net. Component. 4.6.2. TargetingPack | Sada targeting pack .NET Framework 4.6.2 | 16.0.28517.75 | Volitelné
Microsoft.Net. Component. 4.7.1. TargetingPack | Sada targeting pack .NET Framework 4.7.1 | 16.10.31205.252 | Volitelné
Microsoft.Net. Component. 4.7. TargetingPack | Sada targeting pack .NET Framework 4,7 | 16.10.31205.252 | Volitelné
Microsoft.Net. Component. 4.8. TargetingPack | Sada targeting pack .NET Framework 4,8 | 16.4.29313.120 | Volitelné
Microsoft.Net. Component.. 4.6.1. DeveloperTools | Vývojové nástroje .NET Framework 4.6.1 | 16.3.29207.166 | Volitelné
Microsoft.Net. Component. 4.6.2. DeveloperTools | Vývojové nástroje .NET Framework 4.6.2 | 16.3.29207.166 | Volitelné
Microsoft.Net. Component. 4.7.1. DeveloperTools | Vývojové nástroje .NET Framework 4.7.1 | 16.3.29207.166 | Volitelné
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | .NET Framework 4.7 – vývojové nástroje | 16.3.29207.166 | Volitelné
Microsoft.Net.ComponentGroup.4.8.DeveloperTools | .NET Framework 4.8 – vývojové nástroje | 16.4.29318.151 | Volitelné
Microsoft.Net.Core.Component.SDK.2.1 | .NET Core 2.1 Runtime (LTS) | 16.10.31320.204 | Volitelné
Microsoft.VisualStudio.Component.ClassDesigner | Návrhář tříd | 16.0.28528.71 | Volitelné
Microsoft.VisualStudio.Component.CodeClone | Klonování kódu | 16.4.29409.204 | Volitelné
Microsoft.VisualStudio.Component.CodeMap | Mapa kódu | 16.0.28625.61 | Volitelné
Microsoft.VisualStudio.Component.DependencyValidation.Enterprise | Živé ověřování závislostí | 16.0.28625.61 | Volitelné
Microsoft. VisualStudio. Component. GraphDocument | Editor DGML | 16.0.28625.61 | Volitelné
Microsoft. VisualStudio. Component. TestTools. WebLoadTest | Nástroje pro testování výkonu webu a zátěžové testování | 16.0.28625.61 | Volitelné
Microsoft. VisualStudio. Component. WCF. Tools | Windows Communication Foundation | 16.0.28625.61 | Volitelné
Microsoft. VisualStudio. Component. AdditionalWebProjectTemplates | Další šablony projektů (předchozí verze) | 16.10.31205.180 | Volitelné
Microsoft. VisualStudio. Component. ArchitectureTools. Managed | Nástroje pro architekturu a analýzy | 16.5.29514.35 | Volitelné
Microsoft. VisualStudio. Component. IISDevelopment | Podpora služby IIS při vývoji | 16.10.31205.180 | Volitelné

## <a name="nodejs-development"></a>Vývoj Node.js

**ID:** Microsoft. VisualStudio. úlohy. Node

**Popis:** Sestavujte škálovatelné síťové aplikace pomocí Node.js, asynchronního běhového prostředí JavaScript řízeného událostmi. 

### <a name="components-included-by-this-workload"></a>Komponenty zahrnuté v této úlohu

ID komponenty | Name | Verze | Typ závislosti
--- | --- | --- | ---
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostika JavaScriptu | 16.0.28517.75 | Vyžadováno
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Podpora jazyků JavaScript a TypeScript | 16.10.31303.231 | Vyžadováno
Microsoft.VisualStudio.Component.Node.Tools | Node.js vývojové nástroje | 16.5.29515.121 | Vyžadováno
Microsoft.VisualStudio.Component.TypeScript.4.2 | TypeScript 4.2 SDK | 16.0.31303.231 | Vyžadováno
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Vývoj pro ASP.NET a web | 16.10.31205.180 | Vyžadováno
Component.Microsoft.VisualStudio.LiveShare | Live Share | 1.0.4062 | Doporučeno
Microsoft.VisualStudio.Component.Debugger.JustInTime | Ladicí program za běhu | 16.0.28517.75 | Doporučeno
Microsoft. VisualStudio. Component. IntelliCode | IntelliCode | 16.10.31305.154 | Doporučeno
Microsoft. VisualStudio. Component. Roslyn. Compiler | Kompilátory C# a Visual Basic Roslyn | 16.0.28714.129 | Doporučeno
Microsoft. VisualStudio. Component. Roslyn. LanguageServices | C# a Visual Basic | 16.10.31205.252 | Doporučeno
Microsoft. VisualStudio. Component. WebDeploy | Web Deploy | 16.0.28517.75 | Doporučeno
Microsoft. VisualStudio. Component. AppInsights. Tools | Vývojářské analytické nástroje | 16.5.29515.121 | Volitelné
Microsoft. VisualStudio. Component. Common. Azure. Tools | Nástroje pro připojení a publikování | 16.4.29409.204 | Volitelné
Microsoft. VisualStudio. Component. VC. CoreIde | Základní funkce C++ | 16.10.31205.252 | Volitelné
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | MSVC v142 – buildovací nástroje VS 2019 C++ x64/x86 (nejnovější) | 16.10.31205.252 | Volitelné

## <a name="officesharepoint-development"></a>Vývoj pro Office/SharePoint

**ID:** Microsoft.VisualStudio.Workload.Office

**Popis:** Vytvářejte doplňky pro Office a SharePoint, řešení pro SharePoint a doplňky VSTO pomocí jazyků C#, VB a JavaScript.

### <a name="components-included-by-this-workload"></a>Komponenty zahrnuté v této úlohu

ID komponenty | Name | Verze | Typ závislosti
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Služby jazyka Razor | 16.10.31205.252 | Vyžadováno
Component.Microsoft.Web.LibraryManager | Správce knihovny | 16.10.31205.180 | Vyžadováno
Component.Microsoft.WebTools.BrowserLink.WebLivePreview | Web Live Preview | 0.7.22.39845 | Vyžadováno
Microsoft.Component.MSBuild | MSBuild | 16.5.29515.121 | Vyžadováno
Microsoft.Net.Component.4.5.2.TargetingPack | Sada .NET Framework 4.5.2 targeting pack | 16.0.28517.75 | Vyžadováno
Microsoft.Net. Component. 4.5. TargetingPack | Sada targeting pack .NET Framework 4,5 | 16.0.28517.75 | Vyžadováno
Microsoft.Net. Component. 4.6.1. TargetingPack | .NET Framework 4.6.1 targeting pack | 16.0.28517.75 | Vyžadováno
Microsoft.Net. Component. 4.7.2. TargetingPack | Sada targeting pack .NET Framework 4.7.2 | 16.10.31205.252 | Vyžadováno
Microsoft. NET. Component. 4.8. SDK | .NET Framework 4,8 SDK | 16.4.29313.120 | Vyžadováno
Microsoft.Net. Component. 4. TargetingPack | Sada targeting pack .NET Framework 4 | 16.0.28517.75 | Vyžadováno
Microsoft.Net. Component. DevelopmentPrerequisites | Vývojové nástroje .NET Framework 4.7.2 | 16.3.29207.166 | Vyžadováno
Microsoft.NetCore.Component.Runtime.3.1 | .NET Core 3.1 Runtime (LTS) | 16.10.31320.204 | Vyžadováno
Microsoft.NetCore.Component.Runtime.5.0 | .NET 5.0 Runtime | 16.10.31320.204 | Vyžadováno
Microsoft.NetCore.Component.SDK | .NET SDK | 16.10.31320.204 | Vyžadováno
Microsoft.VisualStudio.Component.AppInsights.Tools | Vývojářské analytické nástroje | 16.5.29515.121 | Vyžadováno
Microsoft.VisualStudio.Component.Common.Azure.Tools | Nástroje pro připojení a publikování | 16.4.29409.204 | Vyžadováno
Microsoft.VisualStudio.Component.DockerTools | Kontejnerové vývojové nástroje | 16.4.29409.204 | Vyžadováno
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 16.0.28315.86 | Vyžadováno
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostika JavaScriptu | 16.0.28517.75 | Vyžadováno
Microsoft. VisualStudio. Component. JavaScript. TypeScript | Podpora jazyků JavaScript a TypeScript | 16.10.31303.231 | Vyžadováno
Microsoft. VisualStudio. Component. ManagedDesktop. Core | Jádro úlohy spravované plochy | 16.4.29318.151 | Vyžadováno
Microsoft. VisualStudio. Component. ManagedDesktop. požadavky | Nástroje pro vývoj desktopových aplikací .NET | 16.10.31205.180 | Vyžadováno
Microsoft. VisualStudio. Component. MSODBC. SQL | SQL Server ovladač ODBC | 16.0.28625.61 | Vyžadováno
Microsoft. VisualStudio. Component. MSSQL. CMDLnUtils | SQL Server nástroje příkazového řádku | 16.0.28707.177 | Vyžadováno
Microsoft. VisualStudio. Component. NuGet | Správce balíčků NuGet | 16.1.28829.92 | Vyžadováno
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilátory C# a Visual Basic Roslyn | 16.0.28714.129 | Vyžadováno
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# a Visual Basic | 16.10.31205.252 | Vyžadováno
Microsoft.VisualStudio.Component.Sharepoint.Tools | Office Developer Tools for Visual Studio | 16.4.29409.204 | Vyžadováno
Microsoft.VisualStudio.Component.SQL.ADAL | Modul runtime SQL ADAL | 16.0.28517.75 | Vyžadováno
Microsoft.VisualStudio.Component.SQL.CLR | Datové typy CLR pro SQL Server | 16.0.28315.86 | Vyžadováno
Microsoft.VisualStudio.Component.SQL.DataSources | Zdroje dat pro podporu SQL Server dat | 16.0.28315.86 | Vyžadováno
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 16.0.28625.61 | Vyžadováno
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 16.3.29207.166 | Vyžadováno
Microsoft. VisualStudio. Component. TextTemplating | Transformace textové šablony | 16.0.28625.61 | Vyžadováno
Microsoft. VisualStudio. Component. TypeScript. 4.2 | Sada TypeScript 4,2 SDK | 16.0.31303.231 | Vyžadováno
Microsoft. VisualStudio. Component. WCF. Tools | Windows Communication Foundation | 16.0.28625.61 | Vyžadováno
Microsoft. VisualStudio. Component. Web | ASP.NET a vývojové nástroje pro web | 16.10.31205.252 | Vyžadováno
Microsoft. VisualStudio. Component. Workflow | Windows Workflow Foundation | 16.0.28315.86 | Vyžadováno
Microsoft. VisualStudio. Component. Web | Požadavky na ASP.NET a vývojové nástroje pro web | 16.10.31205.180 | Vyžadováno
Microsoft. VisualStudio. Component. WebToolsExtensions | Vývoj pro ASP.NET a web | 16.10.31205.180 | Vyžadováno
Microsoft. VisualStudio. Component. IntelliCode | IntelliCode | 16.10.31305.154 | Doporučeno
Microsoft.VisualStudio.Component.TeamOffice | Visual Studio Tools for Office (VSTO) | 16.4.29409.204 | Doporučeno
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 16.0.28517.75 | Doporučeno
Microsoft.Net.Component.4.6.2.TargetingPack | .NET Framework 4.6.2 | 16.0.28517.75 | Volitelné
Microsoft.Net.Component.4.7.1.TargetingPack | .NET Framework 4.7.1 | 16.10.31205.252 | Volitelné
Microsoft.Net.Component.4.7.TargetingPack | .NET Framework 4.7 | 16.10.31205.252 | Volitelné
Microsoft.Net.Component.4.8.TargetingPack | .NET Framework 4.8 | 16.4.29313.120 | Volitelné
Microsoft.Net.ComponentGroup.4.6.1.DeveloperTools | .NET Framework 4.6.1 | 16.3.29207.166 | Volitelné
Microsoft.Net. Component. 4.6.2. DeveloperTools | Vývojové nástroje .NET Framework 4.6.2 | 16.3.29207.166 | Volitelné
Microsoft.Net. Component. 4.7.1. DeveloperTools | Vývojové nástroje .NET Framework 4.7.1 | 16.3.29207.166 | Volitelné
Microsoft.Net. Component.. 4.7. DeveloperTools | Vývojové nástroje .NET Framework 4,7 | 16.3.29207.166 | Volitelné
Microsoft.Net. Component.. 4,8. DeveloperTools | Vývojové nástroje .NET Framework 4,8 | 16.4.29318.151 | Volitelné
Microsoft. VisualStudio. Component. IntelliTrace. front-end | IntelliTrace | 16.5.29515.121 | Volitelné
Microsoft. VisualStudio. Component. SharePoint. WIF | Windows Identity Foundation 3.5 | 16.0.28621.142 | Volitelné

## <a name="python-development"></a>Vývoj v Pythonu

**ID:** Microsoft. VisualStudio. úlohy. Python

**Popis:** Úpravy, ladění, interaktivní vývoj a Správa zdrojového kódu pro Python.

### <a name="components-included-by-this-workload"></a>Komponenty zahrnuté v této úlohu

ID komponenty | Name | Verze | Typ závislosti
--- | --- | --- | ---
Microsoft.Component.PythonTools | Podpora jazyka Python | 16.10.31313.127 | Vyžadováno
Component.CPython3.x64 | Python 3 (64bitová verze) (3.7.8) | 3.7.8 | Doporučeno
Component.CPython2.x64 | Python 2 – 64 bitů (2.7.18) (nepodporuje se) | 2.7.18.2 | Volitelné
Component.CPython2.x86 | Python 2 – 32bitová verze (2.7.18) (nepodporuje se) | 2.7.18.2 | Volitelné
Component.CPython3.x86 | Python 3 (32bitová verze) (3.7.8) | 3.7.8 | Volitelné
Component.Microsoft.VisualStudio.LiveShare | Live Share | 1.0.4062 | Volitelné
Součást. Microsoft. VisualStudio. RazorExtension | Jazykové služby Razor | 16.10.31205.252 | Volitelné
Součást. Microsoft. Web. LibraryManager | Správce knihovny | 16.10.31205.180 | Volitelné
Komponenta. Microsoft. WebTools. BrowserLink. WebLivePreview | Web Live Preview | 0.7.22.39845 | Volitelné
Microsoft. Component. Ironpythonu | Ironpythonu (mimo podporu) | 16.10.31303.231 | Volitelné
Microsoft. Component. MSBuild | MSBuild | 16.5.29515.121 | Volitelné
Microsoft. Component. PythonTools. Minicondax64 | Python miniconda (mimo podporu) | 16.10.31313.127 | Volitelné
Microsoft. Component. PythonTools. Web | Podpora webu Pythonu | 16.10.31205.252 | Volitelné
Microsoft. Component. PythonTools. NativeDevelopment | Nativní vývojové nástroje pythonu | 16.10.31205.180 | Volitelné
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 | 16.0.28517.75 | Volitelné
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 | 16.0.28517.75 | Volitelné
Microsoft.Net.Component.4.7.2.TargetingPack | .NET Framework 4.7.2 | 16.10.31205.252 | Volitelné
Microsoft.Net.Component.4.8.SDK | .NET Framework 4.8 SDK | 16.4.29313.120 | Volitelné
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | .NET Framework 4.7.2 – vývojové nástroje | 16.3.29207.166 | Volitelné
Microsoft.NetCore.Component.Runtime.3.1 | .NET Core 3.1 Runtime (LTS) | 16.10.31320.204 | Volitelné
Microsoft. NetCore. Component. Runtime. 5.0 | .NET 5,0 – modul runtime | 16.10.31320.204 | Volitelné
Microsoft. NetCore. Component. SDK | .NET SDK | 16.10.31320.204 | Volitelné
Microsoft. VisualStudio. Component. Azure. AuthoringTools | Nástroje pro tvorbu Azure | 16.0.28625.61 | Volitelné
Microsoft. VisualStudio. Component. Azure. ClientLibs | Knihovny Azure pro .NET | 16.0.28315.86 | Volitelné
Microsoft. VisualStudio. Component. Azure. Compute. emulátor | Emulátor služby COMPUTE Azure | 16.10.31205.252 | Volitelné
Microsoft. VisualStudio. Component. Azure. Storage. emulátor | Emulátor úložiště Azure | 16.4.29313.120 | Volitelné
Microsoft. VisualStudio. Component. Azure. Waverton | Základní nástroje pro Azure Cloud Services | 16.10.31205.252 | Volitelné
Microsoft. VisualStudio. Component. Azure. Waverton. BuildTools | Azure Cloud Services sestavovací nástroje | 16.10.31205.252 | Volitelné
Microsoft.VisualStudio.Component.Common.Azure.Tools | Nástroje pro připojení a publikování | 16.4.29409.204 | Volitelné
Microsoft.VisualStudio.Component.Debugger.JustInTime | Ladicí program za běhu | 16.0.28517.75 | Volitelné
Microsoft.VisualStudio.Component.DockerTools | Kontejnerové vývojové nástroje | 16.4.29409.204 | Volitelné
Microsoft.VisualStudio.Component.Graphics.Tools | Ladicí program grafiky a profiler GPU pro DirectX | 16.0.28625.61 | Volitelné
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 16.0.28315.86 | Volitelné
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostika JavaScriptu | 16.0.28517.75 | Volitelné
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Podpora jazyků JavaScript a TypeScript | 16.10.31303.231 | Volitelné
Microsoft. VisualStudio. Component. ManagedDesktop. Core | Jádro úlohy spravované plochy | 16.4.29318.151 | Volitelné
Microsoft. VisualStudio. Component. MSODBC. SQL | SQL Server ovladač ODBC | 16.0.28625.61 | Volitelné
Microsoft. VisualStudio. Component. MSSQL. CMDLnUtils | SQL Server nástroje příkazového řádku | 16.0.28707.177 | Volitelné
Microsoft. VisualStudio. Component. NuGet | Správce balíčků NuGet | 16.1.28829.92 | Volitelné
Microsoft. VisualStudio. Component. Roslyn. Compiler | Kompilátory C# a Visual Basic Roslyn | 16.0.28714.129 | Volitelné
Microsoft. VisualStudio. Component. Roslyn. LanguageServices | C# a Visual Basic | 16.10.31205.252 | Volitelné
Microsoft. VisualStudio. Component. SQL. ADAL | Modul runtime SQL ADAL | 16.0.28517.75 | Volitelné
Microsoft.VisualStudio.Component.SQL.CLR | Datové typy CLR pro SQL Server | 16.0.28315.86 | Volitelné
Microsoft.VisualStudio.Component.SQL.DataSources | Zdroje dat pro podporu SQL Server dat | 16.0.28315.86 | Volitelné
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 16.0.28625.61 | Volitelné
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 16.3.29207.166 | Volitelné
Microsoft.VisualStudio.Component.TextTemplating | Transformace textových šablon | 16.0.28625.61 | Volitelné
Microsoft.VisualStudio.Component.TypeScript.4.2 | TypeScript 4.2 SDK | 16.0.31303.231 | Volitelné
Microsoft.VisualStudio.Component.VC.CoreIde | Základní funkce C++ | 16.10.31205.252 | Volitelné
Microsoft. VisualStudio. Component. VC. DiagnosticTools | Nástroje pro profilaci C++ | 16.5.29515.121 | Volitelné
Microsoft. VisualStudio. Component. VC. Tools. x86. x64 | MSVC V142-VS 2019 C++ x64/x86 Build Tools (nejnovější) | 16.10.31205.252 | Volitelné
Microsoft. VisualStudio. Component. Web | ASP.NET a vývojové nástroje pro web | 16.10.31205.252 | Volitelné
Microsoft. VisualStudio. Component. WebDeploy | Web Deploy | 16.0.28517.75 | Volitelné
Microsoft. VisualStudio. Component. Windows10SDK | Windows Universal C Runtime | 16.4.29409.204 | Volitelné
Microsoft. VisualStudio. Component. Windows10SDK. 19041 | Windows 10 SDK (10.0.19041.0) | 16.10.31205.252 | Volitelné
Microsoft. VisualStudio. Component. Web | Požadavky ASP.NET a webových vývojových nástrojů | 16.10.31205.180 | Volitelné
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Vývoj pro ASP.NET a web | 16.10.31205.180 | Volitelné

## <a name="universal-windows-platform-development"></a>Univerzální platforma Windows vývoje

**ID:** Microsoft.VisualStudio.Workload.Universal

**Popis:** Vytvářejte aplikace pro Univerzální platforma Windows pomocí C#, VB nebo volitelně C++.

### <a name="components-included-by-this-workload"></a>Komponenty zahrnuté v této úlohu

ID komponenty | Name | Verze | Typ závislosti
--- | --- | --- | ---
Microsoft.Component.NetFX.Native | .NET Native | 16.5.29515.121 | Vyžadováno
Microsoft.ComponentGroup.Blend | Blend for Visual Studio | 16.0.28315.86 | Vyžadováno
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 | 16.0.28517.75 | Vyžadováno
Microsoft.NetCore.Component.Runtime.3.1 | .NET Core 3.1 Runtime (LTS) | 16.10.31320.204 | Vyžadováno
Microsoft. NetCore. Component. Runtime. 5.0 | .NET 5,0 – modul runtime | 16.10.31320.204 | Vyžadováno
Microsoft. NetCore. Component. SDK | .NET SDK | 16.10.31320.204 | Vyžadováno
Microsoft. VisualStudio. Component. AppInsights. Tools | Vývojářské analytické nástroje | 16.5.29515.121 | Vyžadováno
Microsoft. VisualStudio. Component. DiagnosticTools | Nástroje pro profilaci .NET | 16.10.31205.252 | Vyžadováno
Microsoft. VisualStudio. Component. Graphics | Editory obrázků a 3D model | 16.10.31205.252 | Vyžadováno
Microsoft. VisualStudio. Component. NuGet | Správce balíčků NuGet | 16.1.28829.92 | Vyžadováno
Microsoft. VisualStudio. Component. Roslyn. Compiler | Kompilátory C# a Visual Basic Roslyn | 16.0.28714.129 | Vyžadováno
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# a Visual Basic | 16.10.31205.252 | Vyžadováno
Microsoft.VisualStudio.Component.SQL.CLR | Datové typy CLR pro SQL Server | 16.0.28315.86 | Vyžadováno
Microsoft.VisualStudio.Component.Windows10SDK.19041 | Windows 10 SDK (10.0.19041.0) | 16.10.31205.252 | Vyžadováno
Microsoft.VisualStudio.ComponentGroup.MSIX.Packaging | Nástroje MSIX Packaging | 16.10.31205.180 | Vyžadováno
Microsoft.VisualStudio.ComponentGroup.UWP.NetCoreAndStandard | .NET Native a .NET Standard | 16.3.29102.218 | Vyžadováno
Microsoft.VisualStudio.ComponentGroup.UWP.Support | Univerzální platforma Windows nástroje | 16.10.31205.180 | Vyžadováno
Microsoft.VisualStudio.ComponentGroup.UWP.Xamarin | Univerzální platforma Windows nástroje pro Xamarin | 16.10.31205.180 | Vyžadováno
Microsoft. VisualStudio. Component. IntelliCode | IntelliCode | 16.10.31305.154 | Doporučeno
Microsoft. VisualStudio. Component. IntelliTrace. front-end | IntelliTrace | 16.5.29515.121 | Doporučeno
Microsoft. NET. Component. 4.8. SDK | .NET Framework 4,8 SDK | 16.4.29313.120 | Volitelné
Microsoft. VisualStudio. Component. ClassDesigner | Návrhář tříd | 16.0.28528.71 | Volitelné
Microsoft. VisualStudio. Component. CodeClone | Klon kódu | 16.4.29409.204 | Volitelné
Microsoft. VisualStudio. Component. CodeMap | Mapa kódu | 16.0.28625.61 | Volitelné
Microsoft. VisualStudio. Component. DependencyValidation. Enterprise | Ověřování závislostí v reálném čase | 16.0.28625.61 | Volitelné
Microsoft. VisualStudio. Component. GraphDocument | Editor DGML | 16.0.28625.61 | Volitelné
Microsoft.VisualStudio.Component.Graphics.Tools | Ladicí program grafiky a profiler GPU pro DirectX | 16.0.28625.61 | Volitelné
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 16.0.28625.61 | Volitelné
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
Microsoft.VisualStudio.ComponentGroup.ArchitectureTools.Managed | Nástroje pro architekturu a analýzu | 16.5.29514.35 | Volitelné
Microsoft.VisualStudio.ComponentGroup.UWP.VC | C++ (v142) – Univerzální platforma Windows nástroje | 16.10.31205.180 | Volitelné
Microsoft.VisualStudio.ComponentGroup.UWP.VC.v141 | C++ (v141) – Univerzální platforma Windows nástroje | 16.1.28810.153 | Volitelné

## <a name="visual-studio-extension-development"></a>Vývoj rozšíření sady Visual Studio

**ID:** Microsoft. VisualStudio. úlohy. VisualStudioExtension

**Popis:** Vytvořte doplňky a rozšíření pro Visual Studio, včetně nových příkazů, analyzátorů kódu a oken nástrojů.

### <a name="components-included-by-this-workload"></a>Součásti zahrnuté v tomto zatížení

ID součásti | Name | Verze | Typ závislosti
--- | --- | --- | ---
Microsoft. Component. MSBuild | MSBuild | 16.5.29515.121 | Vyžadováno
Microsoft.Net. Component. 4.6. TargetingPack | Sada targeting pack .NET Framework 4,6 | 16.0.28517.75 | Vyžadováno
Microsoft.Net. Component. 4.7.2. TargetingPack | Sada targeting pack .NET Framework 4.7.2 | 16.10.31205.252 | Vyžadováno
Microsoft. NET. Component. 4.8. SDK | .NET Framework 4,8 SDK | 16.4.29313.120 | Vyžadováno
Microsoft.Net. Component. DevelopmentPrerequisites | Vývojové nástroje .NET Framework 4.7.2 | 16.3.29207.166 | Vyžadováno
Microsoft. VisualStudio. Component. NuGet | Správce balíčků NuGet | 16.1.28829.92 | Vyžadováno
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilátory C# a Visual Basic Roslyn | 16.0.28714.129 | Vyžadováno
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# a Visual Basic | 16.10.31205.252 | Vyžadováno
Microsoft.VisualStudio.Component.VSSDK | Visual Studio SDK | 16.0.28315.86 | Vyžadováno
Microsoft.VisualStudio.ComponentGroup.VisualStudioExtension.Prerequisites | Visual Studio pro vývoj rozšíření | 16.10.31205.180 | Vyžadováno
Microsoft.VisualStudio.Component.DiagnosticTools | Nástroje pro profilaci .NET | 16.10.31205.252 | Doporučeno
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 16.10.31305.154 | Doporučeno
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | 16.5.29515.121 | Doporučeno
Microsoft.VisualStudio.Component.TextTemplating | Transformace textové šablony | 16.0.28625.61 | Doporučeno
Microsoft. Component. CodeAnalysis. SDK | Sada .NET Compiler Platform SDK | 16.2.29003.222 | Volitelné
Microsoft. VisualStudio. Component. AppInsights. Tools | Vývojářské analytické nástroje | 16.5.29515.121 | Volitelné
Microsoft. VisualStudio. Component. DslTools | Sada SDK pro modelování | 16.0.28315.86 | Volitelné

## <a name="unaffiliated-components"></a>Nepřidružené součásti

Jedná se o součásti, které nejsou součástí žádné úlohy, ale mohou být vybrány jako jednotlivé komponenty.

ID součásti | Name | Verze
--- | --- | ---
Komponenta. GitHub. VisualStudio | Rozšíření GitHub pro Visual Studio | 2.5.9.5485
Komponenta. Xamarin. Profiler | Xamarin Profiler | 16.0.28315.86
Microsoft. Component. ClickOnce | Publikování ClickOnce | 16.4.29409.204
Microsoft.Component.HelpViewer | Help Viewer | 16.0.28625.61
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 16.4.29409.204
Microsoft.Net.Component.4.6.2.SDK | .NET Framework 4.6.2 SDK | 16.4.29409.204
Microsoft.Net.Component.4.7.1.SDK | .NET Framework 4.7.1 SDK | 16.4.29409.204
Microsoft.Net.Component.4.7.2.SDK | .NET Framework 4.7.2 SDK | 16.4.29409.204
Microsoft.Net.Component.4.7.SDK | .NET Framework 4.7 SDK | 16.4.29409.204
Microsoft.Net.Core.Component.SDK.2.2 | .NET Core 2,2 runtime (mimo podporu) | 16.10.31205.252
Microsoft. NET. Core. Component. SDK. 3.0 | .NET Core 3,0 Runtime (mimo podporu) | 16.10.31320.204
Microsoft. NetCore. Component. DevelopmentTools. 2.1 | Vývojové nástroje Plus .NET Core 2,1 | 16.10.31205.252
Microsoft. NetCore. Component. Web. 2.1 | Vývojové nástroje pro web Plus .NET Core 2,1 | 16.10.31205.252
Microsoft. VisualStudio. Component. AzureDevOps. OfficeIntegration | Integrace Azure DevOps Office | 16.0.28625.61
Microsoft. VisualStudio. Component. Debugger. VSOnline | Ladicí program pro GitHub Codespaces | 16.10.31205.252
Microsoft. VisualStudio. Component. Git | Git pro Windows | 16.0.28625.61
Microsoft. VisualStudio. Component. LinqToSql | Nástroje LINQ to SQL | 16.0.28625.61
Microsoft.VisualStudio.Component.TestTools.CodedUITest | Programový test UI | 16.0.28327.66
Microsoft.VisualStudio.Component.VC.14.20.ARM | MSVC v142 – VS 2019 C++ – nástroje pro sestavení ARM (v14.20) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.20.ARM.Spectre | MSVC v142 – VS 2019 C++ ARM Spectre-mitigated libs (verze 14.20) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.ARM64 | MSVC v142 – VS 2019 C++ ARM64 – buildovací nástroje (v14.20) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.20.ARM64.Spectre | MSVC v142 – VS 2019 C++ ARM64 Spectre-mitigated libs (v14.20) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.ATL | C++ v14.20 ATL pro nástroje sestavení v142 (x86 & x64) | 16.1.28829.92
Microsoft.VisualStudio.Component.VC.14.20.ATL.ARM | C++ v14.20 ATL pro nástroje sestavení v142 (ARM) | 16.5.29515.121
Microsoft. VisualStudio. Component. VC. 14.20. ATL. ARM. Spectre | C++ v 14.20 ATL pro nástroje pro sestavení V142 s omezeními Spectre (ARM) | 16.5.29721.120
Microsoft. VisualStudio. Component. VC. 14.20. ATL. ARM64 | C++ v 14.20 ATL pro nástroje pro vytváření V142 (ARM64) | 16.5.29515.121
Microsoft. VisualStudio. Component. VC. 14.20. ATL. ARM64. Spectre | C++ v 14.20 ATL pro nástroje pro sestavení V142 s omezeními Spectre (ARM64) | 16.5.29515.121
Microsoft. VisualStudio. Component. VC. 14.20. ATL. Spectre | C++ v 14.20 ATL pro nástroje sestavení V142 s riziky Spectre (x86 & x64) | 16.5.29515.121
Microsoft. VisualStudio. Component. VC. 14.20. CLI. support | Podpora C++/CLI pro V142 Build Tools (14,20) | 16.10.31205.252
Microsoft. VisualStudio. Component. VC. 14.20. MFC | C++ v 14.20 MFC pro nástroje sestavení V142 (x86 & x64) | 16.2.29003.222
Microsoft. VisualStudio. Component. VC. 14.20. MFC. ARM | C++ v14.20 MFC pro nástroje sestavení v142 (ARM) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.MFC.ARM.Spectre | Nástroje sestavení C++ v14.20 MFC pro v142 s omezením rizik spectre (ARM) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.MFC.ARM64 | C++ v14.20 MFC pro nástroje sestavení v142 (ARM64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.MFC.ARM64.Spectre | Nástroje sestavení C++ v14.20 MFC pro v142 s omezením rizik spectre (ARM64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.MFC.Spectre | Nástroje sestavení C++ v14.20 MFC pro v142 s omezením rizik spectre (x86 & x64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.x86.x64 | MSVC v142 – buildovací nástroje VS 2019 C++ x64/x86 (verze 14.20) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.20.x86.x64.Spectre | MSVC v142 – VS 2019 C++ x64/x86 Spectre-mitigated libs (verze 14.20) | 16.5.29515.121
Microsoft. VisualStudio. Component. VC. 14.21. ARM | MSVC V142-VS 2019 C++ ARM Build Tools (v 14.21) | 16.10.31205.252
Microsoft. VisualStudio. Component. VC. 14.21. ARM. Spectre | MSVC V142-VS 2019 C++ ARM Spectre-zmírnit knihovny (v 14.21) | 16.5.29515.121
Microsoft. VisualStudio. Component. VC. 14.21. ARM64 | MSVC V142-VS 2019 C++ ARM64 Build Tools (v 14.21) | 16.10.31205.252
Microsoft. VisualStudio. Component. VC. 14.21. ARM64. Spectre | MSVC V142-VS 2019 C++ ARM64 Spectre-zmírňované knihovny (v 14.21) | 16.5.29515.121
Microsoft. VisualStudio. Component. VC. 14.21. ATL | C++ v 14.21 ATL pro nástroje sestavení V142 (x86 & x64) | 16.2.29019.55
Microsoft. VisualStudio. Component. VC. 14.21. ATL. ARM | C++ v 14.21 ATL pro nástroje pro sestavení V142 (ARM) | 16.2.29019.55
Microsoft. VisualStudio. Component. VC. 14.21. ATL. ARM. Spectre | C++ v 14.21 ATL pro nástroje pro sestavení V142 s omezeními Spectre (ARM) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.21.ATL.ARM64 | C++ v14.21 ATL pro nástroje sestavení v142 (ARM64) | 16.2.29019.55
Microsoft.VisualStudio.Component.VC.14.21.ATL.ARM64.Spectre | C++ v14.21 ATL pro buildovací nástroje verze 142 s omezením rizik spectre (ARM64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.21.ATL.Spectre | C++ v14.21 ATL pro buildovací nástroje v142 s omezením rizik spectre (x86 & x64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.21.CLI.Support | Podpora C++/CLI pro nástroje sestavení v142 (14.21) | 16.3.29207.166
Microsoft.VisualStudio.Component.VC.14.21.MFC | C++ v14.21 MFC pro nástroje sestavení v142 (x86 & x64) | 16.2.29019.55
Microsoft.VisualStudio.Component.VC.14.21.MFC.ARM | C++ v14.21 MFC pro nástroje sestavení v142 (ARM) | 16.2.29019.55
Microsoft.VisualStudio.Component.VC.14.21.MFC.ARM.Spectre | C++ v 14.21 MFC pro nástroje pro sestavení V142 s omezeními Spectre (ARM) | 16.5.29515.121
Microsoft. VisualStudio. Component. VC. 14.21. MFC. ARM64 | C++ v 14.21 MFC pro nástroje sestavení V142 (ARM64) | 16.2.29019.55
Microsoft. VisualStudio. Component. VC. 14.21. MFC. ARM64. Spectre | C++ v 14.21 MFC pro nástroje pro sestavení V142 s omezeními Spectre (ARM64) | 16.5.29515.121
Microsoft. VisualStudio. Component. VC. 14.21. MFC. Spectre | C++ v 14.21 MFC pro nástroje sestavení V142 s riziky Spectre (x86 & x64) | 16.5.29515.121
Microsoft. VisualStudio. Component. VC. 14.21. x86. x64 | MSVC V142-VS 2019 C++ x64/x86 Build Tools (v 14.21) | 16.10.31205.252
Microsoft. VisualStudio. Component. VC. 14.21. x86. x64. Spectre | MSVC V142-VS 2019 C++ x64/x86 Spectre-zmírnit knihovny (v 14.21) | 16.5.29515.121
Microsoft. VisualStudio. Component. VC. 14.22. ARM | MSVC V142-VS 2019 C++ ARM Build Tools (v 14.22) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.22.ARM.Spectre | MSVC v142 – VS 2019 C++ ARM Spectre-mitigated libs (verze 14.22) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.22.ARM64 | MSVC v142 – buildovací nástroje C++ ARM64 sady VS 2019 (v14.22) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.22.ARM64.Spectre | MSVC v142 – VS 2019 C++ ARM64 Spectre-mitigated libs (v14.22) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.22.ATL | C++ v14.22 ATL pro nástroje sestavení v142 (x86 & x64) | 16.4.29313.120
Microsoft.VisualStudio.Component.VC.14.22.ATL.ARM | C++ v14.22 ATL pro nástroje sestavení v142 (ARM) | 16.4.29313.120
Microsoft.VisualStudio.Component.VC.14.22.ATL.ARM.Spectre | C++ v14.22 ATL pro buildovací nástroje v142 s omezením rizik spectre (ARM) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.22.ATL.ARM64 | C++ v14.22 ATL pro nástroje sestavení v142 (ARM64) | 16.4.29313.120
Microsoft. VisualStudio. Component. VC. 14.22. ATL. ARM64. Spectre | C++ v 14.22 ATL pro nástroje pro sestavení V142 s omezeními Spectre (ARM64) | 16.5.29515.121
Microsoft. VisualStudio. Component. VC. 14.22. ATL. Spectre | C++ v 14.22 ATL pro nástroje sestavení V142 s riziky Spectre (x86 & x64) | 16.5.29515.121
Microsoft. VisualStudio. Component. VC. 14.22. CLI. support | Podpora C++/CLI pro V142 Build Tools (14,22) | 16.10.31205.252
Microsoft. VisualStudio. Component. VC. 14.22. MFC | C++ v 14.22 MFC pro nástroje sestavení V142 (x86 & x64) | 16.4.29313.120
Microsoft. VisualStudio. Component. VC. 14.22. MFC. ARM | C++ v 14.22 MFC pro nástroje sestavení V142 (ARM) | 16.4.29313.120
Microsoft. VisualStudio. Component. VC. 14.22. MFC. ARM. Spectre | C++ v 14.22 MFC pro nástroje pro sestavení V142 s omezeními Spectre (ARM) | 16.5.29515.121
Microsoft. VisualStudio. Component. VC. 14.22. MFC. ARM64 | C++ v14.22 MFC pro nástroje sestavení v142 (ARM64) | 16.4.29313.120
Microsoft.VisualStudio.Component.VC.14.22.MFC.ARM64.Spectre | C++ v14.22 MFC pro nástroje sestavení v142 s omezením rizik spectre (ARM64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.22.MFC.Spectre | C++ v14.22 MFC pro nástroje sestavení v142 s omezením rizik spectre (x86 & x64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.22.x86.x64 | MSVC v142 – buildovací nástroje VS 2019 C++ x64/x86 (verze 14.22) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.22.x86.x64.Spectre | MSVC v142 – VS 2019 C++ x64/x86 Spectre-mitigated libs (v14.22) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.ARM | MSVC v142 – nástroje sestavení ARM VS 2019 C++ (verze 14.23) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.23.ARM.Spectre | MSVC v142 – VS 2019 C++ ARM Spectre-mitigated libs (verze 14.23) | 16.5.29515.121
Microsoft. VisualStudio. Component. VC. 14.23. ARM64 | MSVC V142-VS 2019 C++ ARM64 Build Tools (v 14.23) | 16.10.31205.252
Microsoft. VisualStudio. Component. VC. 14.23. ARM64. Spectre | MSVC V142-VS 2019 C++ ARM64 Spectre-zmírňované knihovny (v 14.23) | 16.5.29515.121
Microsoft. VisualStudio. Component. VC. 14.23. ATL | C++ v 14.23 ATL pro nástroje sestavení V142 (x86 & x64) | 16.5.29515.121
Microsoft. VisualStudio. Component. VC. 14.23. ATL. ARM | C++ v 14.23 ATL pro nástroje pro sestavení V142 (ARM) | 16.5.29515.121
Microsoft. VisualStudio. Component. VC. 14.23. ATL. ARM. Spectre | C++ v 14.23 ATL pro nástroje pro sestavení V142 s omezeními Spectre (ARM) | 16.5.29721.120
Microsoft. VisualStudio. Component. VC. 14.23. ATL. ARM64 | C++ v 14.23 ATL pro nástroje pro vytváření V142 (ARM64) | 16.5.29515.121
Microsoft. VisualStudio. Component. VC. 14.23. ATL. ARM64. Spectre | C++ v 14.23 ATL pro nástroje pro sestavení V142 s omezeními Spectre (ARM64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.ATL.Spectre | C++ v14.23 ATL pro buildovací nástroje v142 s omezením rizik spectre (x86 & x64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.CLI.Support | Podpora C++/CLI pro nástroje sestavení v142 (14.23) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.23.MFC | C++ v14.23 MFC pro nástroje sestavení v142 (x86 & x64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.MFC.ARM | C++ v14.23 MFC pro nástroje sestavení v142 (ARM) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.MFC.ARM.Spectre | C++ v14.23 MFC pro nástroje sestavení v142 s omezením rizik spectre (ARM) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.MFC.ARM64 | C++ v14.23 MFC pro nástroje sestavení v142 (ARM64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.MFC.ARM64.Spectre | C++ v 14.23 MFC pro nástroje pro sestavení V142 s omezeními Spectre (ARM64) | 16.5.29515.121
Microsoft. VisualStudio. Component. VC. 14.23. MFC. Spectre | C++ v 14.23 MFC pro nástroje sestavení V142 s riziky Spectre (x86 & x64) | 16.5.29515.121
Microsoft. VisualStudio. Component. VC. 14.23. x86. x64 | MSVC V142-VS 2019 C++ x64/x86 Build Tools (v 14.23) | 16.10.31205.252
Microsoft. VisualStudio. Component. VC. 14.23. x86. x64. Spectre | MSVC V142-VS 2019 C++ x64/x86 Spectre-zmírnit knihovny (v 14.23) | 16.5.29515.121
Microsoft. VisualStudio. Component. VC. 14.24. ARM | MSVC V142-VS 2019 C++ ARM Build Tools (v 14.24) | 16.10.31205.252
Microsoft. VisualStudio. Component. VC. 14.24. ARM. Spectre | MSVC V142-VS 2019 C++ ARM Spectre-zmírnit knihovny (v 14.24) | 16.5.29721.120
Microsoft. VisualStudio. Component. VC. 14.24. ARM64 | MSVC V142-VS 2019 C++ ARM64 Build Tools (v 14.24) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.24.ARM64.Spectre | MSVC v142 – VS 2019 C++ ARM64 Spectre-mitigated libs (verze 14.24) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.ATL | C++ v14.24 ATL pro nástroje sestavení v142 (x86 & x64) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.ATL.ARM | C++ v14.24 ATL pro nástroje sestavení v142 (ARM) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.ATL.ARM.Spectre | C++ v14.24 ATL pro buildovací nástroje v142 s omezením rizik spectre (ARM) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.ATL.ARM64 | C++ v14.24 ATL pro nástroje sestavení v142 (ARM64) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.ATL.ARM64.Spectre | C++ v14.24 ATL pro buildovací nástroje v142 s omezením rizik spectre (ARM64) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.ATL.Spectre | C++ v14.24 ATL pro buildovací nástroje v142 s omezením rizik spectre (x86 & x64) | 16.10.31205.252
Microsoft. VisualStudio. Component. VC. 14.24. CLI. support | Podpora C++/CLI pro V142 Build Tools (14,24) | 16.10.31205.252
Microsoft. VisualStudio. Component. VC. 14.24. MFC | C++ v 14.24 MFC pro nástroje sestavení V142 (x86 & x64) | 16.5.29721.120
Microsoft. VisualStudio. Component. VC. 14.24. MFC. ARM | C++ v 14.24 MFC pro nástroje sestavení V142 (ARM) | 16.5.29721.120
Microsoft. VisualStudio. Component. VC. 14.24. MFC. ARM. Spectre | C++ v 14.24 MFC pro nástroje pro sestavení V142 s omezeními Spectre (ARM) | 16.5.29721.120
Microsoft. VisualStudio. Component. VC. 14.24. MFC. ARM64 | C++ v 14.24 MFC pro nástroje sestavení V142 (ARM64) | 16.5.29721.120
Microsoft. VisualStudio. Component. VC. 14.24. MFC. ARM64. Spectre | C++ v 14.24 MFC pro nástroje pro sestavení V142 s omezeními Spectre (ARM64) | 16.10.31205.252
Microsoft. VisualStudio. Component. VC. 14.24. MFC. Spectre | Buildovací nástroje C++ v14.24 MFC pro v142 s omezením rizik spectre (x86 & x64) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.24.x86.x64 | MSVC v142 – buildovací nástroje VS 2019 C++ x64/x86 (verze 14.24) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.24.x86.x64.Spectre | MSVC v142 – VS 2019 C++ x64/x86 Spectre-mitigated libs (verze 14.24) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.25.ARM | MSVC v142 – VS 2019 C++ – nástroje pro sestavení ARM (verze 14.25) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.25.ARM.Spectre | MSVC v142 – VS 2019 C++ ARM Spectre-mitigated libs (verze 14.25) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.25.ARM64 | MSVC v142 – VS 2019 C++ ARM64 – buildovací nástroje (v14.25) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.25.ARM64.Spectre | MSVC v142 – VS 2019 C++ ARM64 Spectre-mitigated libs (v14.25) | 16.10.31205.252
Microsoft. VisualStudio. Component. VC. 14.25. ATL | C++ v 14.25 ATL pro nástroje sestavení V142 (x86 & x64) | 16.10.31205.252
Microsoft. VisualStudio. Component. VC. 14.25. ATL. ARM | C++ v 14.25 ATL pro nástroje pro sestavení V142 (ARM) | 16.10.31205.252
Microsoft. VisualStudio. Component. VC. 14.25. ATL. ARM. Spectre | C++ v 14.25 ATL pro nástroje pro sestavení V142 s omezeními Spectre (ARM) | 16.10.31205.252
Microsoft. VisualStudio. Component. VC. 14.25. ATL. ARM64 | C++ v 14.25 ATL pro nástroje pro vytváření V142 (ARM64) | 16.10.31205.252
Microsoft. VisualStudio. Component. VC. 14.25. ATL. ARM64. Spectre | C++ v 14.25 ATL pro nástroje pro sestavení V142 s omezeními Spectre (ARM64) | 16.10.31205.252
Microsoft. VisualStudio. Component. VC. 14.25. ATL. Spectre | C++ v 14.25 ATL pro nástroje sestavení V142 s riziky Spectre (x86 & x64) | 16.10.31205.252
Microsoft. VisualStudio. Component. VC. 14.25. CLI. support | Podpora C++/CLI pro V142 Build Tools (14,25) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.25.MFC | C++ v14.25 MFC pro nástroje sestavení v142 (x86 & x64) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.25.MFC.ARM | C++ v14.25 MFC pro nástroje sestavení v142 (ARM) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.25.MFC.ARM.Spectre | C++ v14.25 MFC pro nástroje sestavení v142 s omezením rizik spectre (ARM) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.25.MFC.ARM64 | C++ v14.25 MFC pro nástroje sestavení v142 (ARM64) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.25.MFC.ARM64.Spectre | C++ v14.25 MFC pro nástroje sestavení v142 s omezením rizik spectre (ARM64) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.25.MFC.Spectre | C++ v14.25 MFC pro nástroje sestavení v142 s omezením rizik spectre (x86 & x64) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.25.x86.x64 | MSVC V142-VS 2019 C++ x64/x86 Build Tools (v 14.25) | 16.10.31205.252
Microsoft. VisualStudio. Component. VC. 14.25. x86. x64. Spectre | MSVC V142-VS 2019 C++ x64/x86 Spectre-zmírnit knihovny (v 14.25) | 16.10.31205.252
Microsoft. VisualStudio. Component. VC. 14.26. ARM | MSVC V142-VS 2019 C++ ARM Build Tools (v 14.26) | 16.10.31205.252
Microsoft. VisualStudio. Component. VC. 14.26. ARM. Spectre | MSVC V142-VS 2019 C++ ARM Spectre-zmírnit knihovny (v 14.26) | 16.10.31205.252
Microsoft. VisualStudio. Component. VC. 14.26. ARM64 | MSVC V142-VS 2019 C++ ARM64 Build Tools (v 14.26) | 16.10.31205.252
Microsoft. VisualStudio. Component. VC. 14.26. ARM64. Spectre | MSVC V142-VS 2019 C++ ARM64 Spectre-zmírňované knihovny (v 14.26) | 16.10.31205.252
Microsoft. VisualStudio. Component. VC. 14.26. ATL | C++ v 14.26 ATL pro nástroje sestavení V142 (x86 & x64) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.26.ATL.ARM | C++ v14.26 ATL pro nástroje sestavení v142 (ARM) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.26.ATL.ARM.Spectre | C++ v14.26 ATL pro buildovací nástroje v142 s omezením rizik spectre (ARM) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.26.ATL.ARM64 | C++ v14.26 ATL pro nástroje sestavení v142 (ARM64) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.26.ATL.ARM64.Spectre | C++ v14.26 ATL pro buildovací nástroje v142 s omezením rizik spectre (ARM64) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.26.ATL.Spectre | C++ v14.26 ATL pro buildovací nástroje v142 s omezením rizik spectre (x86 & x64) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.26.CLI.Support | Podpora C++/CLI pro nástroje sestavení v142 (14.26) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.26.MFC | C++ v14.26 MFC pro nástroje sestavení v142 (x86 & x64) | 16.10.31205.252
Microsoft. VisualStudio. Component. VC. 14.26. MFC. ARM | C++ v 14.26 MFC pro nástroje sestavení V142 (ARM) | 16.10.31205.252
Microsoft. VisualStudio. Component. VC. 14.26. MFC. ARM. Spectre | C++ v 14.26 MFC pro nástroje pro sestavení V142 s omezeními Spectre (ARM) | 16.10.31205.252
Microsoft. VisualStudio. Component. VC. 14.26. MFC. ARM64 | C++ v 14.26 MFC pro nástroje sestavení V142 (ARM64) | 16.10.31205.252
Microsoft. VisualStudio. Component. VC. 14.26. MFC. ARM64. Spectre | C++ v 14.26 MFC pro nástroje pro sestavení V142 s omezeními Spectre (ARM64) | 16.10.31205.252
Microsoft. VisualStudio. Component. VC. 14.26. MFC. Spectre | C++ v 14.26 MFC pro nástroje sestavení V142 s riziky Spectre (x86 & x64) | 16.10.31205.252
Microsoft. VisualStudio. Component. VC. 14.26. x86. x64 | MSVC V142-VS 2019 C++ x64/x86 Build Tools (v 14.26) | 16.10.31205.252
Microsoft. VisualStudio. Component. VC. 14.26. x86. x64. Spectre | MSVC v142 – VS 2019 C++ x64/x86 Spectre-mitigated libs (verze 14.26) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.27.ARM | MSVC v142 – VS 2019 C++ – nástroje pro sestavení ARM (verze 14.27) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.27.ARM.Spectre | MSVC v142 – VS 2019 C++ ARM Spectre-mitigated libs (verze 14.27) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.27.ARM64 | MSVC v142 – buildovací nástroje C++ ARM64 sady VS 2019 (v14.27) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.27.ARM64.Spectre | MSVC v142 – VS 2019 C++ ARM64 Spectre-mitigated libs (verze 14.27) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.27.ATL | C++ v14.27 ATL pro nástroje sestavení v142 (x86 & x64) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.27.ATL.ARM | C++ v14.27 ATL pro nástroje sestavení v142 (ARM) | 16.10.31205.252
Microsoft. VisualStudio. Component. VC. 14.27. ATL. ARM. Spectre | C++ v 14.27 ATL pro nástroje pro sestavení V142 s omezeními Spectre (ARM) | 16.10.31205.252
Microsoft. VisualStudio. Component. VC. 14.27. ATL. ARM64 | C++ v 14.27 ATL pro nástroje pro vytváření V142 (ARM64) | 16.10.31205.252
Microsoft. VisualStudio. Component. VC. 14.27. ATL. ARM64. Spectre | C++ v 14.27 ATL pro nástroje pro sestavení V142 s omezeními Spectre (ARM64) | 16.10.31205.252
Microsoft. VisualStudio. Component. VC. 14.27. ATL. Spectre | C++ v 14.27 ATL pro nástroje sestavení V142 s riziky Spectre (x86 & x64) | 16.10.31205.252
Microsoft. VisualStudio. Component. VC. 14.27. CLI. support | Podpora C++/CLI pro V142 Build Tools (14,27) | 16.10.31205.252
Microsoft. VisualStudio. Component. VC. 14.27. MFC | C++ v 14.27 MFC pro nástroje sestavení V142 (x86 & x64) | 16.10.31205.252
Microsoft. VisualStudio. Component. VC. 14.27. MFC. ARM | C++ v 14.27 MFC pro nástroje sestavení V142 (ARM) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.27.MFC.ARM.Spectre | C++ v14.27 MFC pro nástroje sestavení v142 s omezením rizik spectre (ARM) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.27.MFC.ARM64 | C++ v14.27 MFC pro nástroje sestavení v142 (ARM64) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.27.MFC.ARM64.Spectre | C++ v14.27 MFC pro nástroje sestavení v142 s omezením rizik spectre (ARM64) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.27.MFC.Spectre | Nástroje sestavení C++ v14.27 MFC pro v142 s omezením rizik spectre (x86 & x64) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.27.x86.x64 | MSVC v142 – buildovací nástroje VS 2019 C++ x64/x86 (verze 14.27) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.27.x86.x64.Spectre | MSVC v142 – VS 2019 C++ x64/x86 Spectre-mitigated libs (verze 14.27) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.28.16.9.ARM | MSVC V142-VS 2019 C++ ARM Build Tools (v 14.28-16.9) | 16.10.31303.231
Microsoft. VisualStudio. Component. VC. 14.28.16.9. ARM. Spectre | MSVC V142-VS 2019 C++ ARM Spectre-zmírnit knihovny (v 14.28-16.9) | 16.10.31303.231
Microsoft. VisualStudio. Component. VC. 14.28.16.9. ARM64 | MSVC V142-VS 2019 C++ ARM64 Build Tools (v 14.28-16.9) | 16.10.31303.231
Microsoft. VisualStudio. Component. VC. 14.28.16.9. ARM64. Spectre | MSVC V142-VS 2019 C++ ARM64 Spectre-zmírňované knihovny (v 14.28-16.9) | 16.10.31303.231
Microsoft. VisualStudio. Component. VC. 14.28.16.9. ATL | C++ v 14.28 (16,9) ATL pro nástroje sestavení V142 (x86 & x64) | 16.10.31303.231
Microsoft. VisualStudio. Component. VC. 14.28.16.9. ATL. ARM | C++ v 14.28 (16,9) ATL pro nástroje sestavení V142 (ARM) | 16.10.31303.231
Microsoft. VisualStudio. Component. VC. 14.28.16.9. ATL. ARM. Spectre | C++ v 14.28 (16,9) ATL pro nástroje sestavení V142 s omezeními Spectre (ARM) | 16.10.31303.231
Microsoft.VisualStudio.Component.VC.14.28.16.9.ATL.ARM64 | C++ v14.28 (16.9) ATL pro nástroje sestavení v142 (ARM64) | 16.10.31303.231
Microsoft.VisualStudio.Component.VC.14.28.16.9.ATL.ARM64.Spectre | C++ v14.28 (16.9) ATL pro buildovací nástroje v142 se zmírněními rizik Spectre (ARM64) | 16.10.31303.231
Microsoft.VisualStudio.Component.VC.14.28.16.9.ATL.Spectre | C++ v14.28 (16.9) ATL pro buildovací nástroje v142 se zmírněními rizik spectre (x86 & x64) | 16.10.31303.231
Microsoft.VisualStudio.Component.VC.14.28.16.9.CLI.Support | Podpora C++/CLI pro nástroje sestavení v142 (14.28-16.9) | 16.10.31303.231
Microsoft.VisualStudio.Component.VC.14.28.16.9.MFC | C++ v14.28 (16.9) MFC pro nástroje sestavení v142 (x86 & x64) | 16.10.31303.231
Microsoft.VisualStudio.Component.VC.14.28.16.9.MFC.ARM | C++ v14.28 (16.9) MFC pro nástroje sestavení v142 (ARM) | 16.10.31303.231
Microsoft.VisualStudio.Component.VC.14.28.16.9.MFC.ARM.Spectre | C++ v14.28 (16.9) MFC pro nástroje sestavení v142 s omezením rizik spectre (ARM) | 16.10.31303.231
Microsoft. VisualStudio. Component. VC. 14.28.16.9. MFC. ARM64 | C++ v 14.28 (16,9) MFC pro nástroje sestavení V142 (ARM64) | 16.10.31303.231
Microsoft. VisualStudio. Component. VC. 14.28.16.9. MFC. ARM64. Spectre | C++ v 14.28 (16,9) MFC pro nástroje sestavení V142 s riziky Spectre (ARM64) | 16.10.31303.231
Microsoft. VisualStudio. Component. VC. 14.28.16.9. MFC. Spectre | C++ v 14.28 (16,9) MFC pro nástroje sestavení V142 s riziky Spectre (x86 & x64) | 16.10.31303.231
Microsoft. VisualStudio. Component. VC. 14.28.16.9. x86. x64 | MSVC V142-VS 2019 C++ x64/x86 Build Tools (v 14.28-16.9) | 16.10.31303.231
Microsoft. VisualStudio. Component. VC. 14.28.16.9. x86. x64. Spectre | MSVC V142-VS 2019 C++ x64/x86 Spectre-zmírnit knihovny (v 14.28-16.9) | 16.10.31303.231
Microsoft. VisualStudio. Component. VC. 14.28. ARM | MSVC V142-VS 2019 C++ ARM Build Tools (v 14.28-16.8) | 16.10.31205.252
Microsoft. VisualStudio. Component. VC. 14.28. ARM. Spectre | MSVC v142 – VS 2019 C++ ARM Spectre-mitigated libs (v14.28-16.8) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.28.ARM64 | MSVC v142 – buildovací nástroje C++ ARM64 sady VS 2019 (v14.28-16.8) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.28.ARM64.Spectre | MSVC v142 – VS 2019 C++ ARM64 Spectre-mitigated libs (v14.28-16.8) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.28.ATL | C++ v14.28 (16.8) ATL pro buildovací nástroje v142 (x86 & x64) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.28.ATL.ARM | C++ v14.28 (16.8) ATL pro nástroje sestavení v142 (ARM) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.28.ATL.ARM.Spectre | C++ v14.28 (16.8) ATL pro buildovací nástroje v142 s spectre mitigations (ARM) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.28.ATL.ARM64 | C++ v14.28 (16.8) ATL pro nástroje sestavení v142 (ARM64) | 16.10.31205.252
Microsoft. VisualStudio. Component. VC. 14.28. ATL. ARM64. Spectre | C++ v 14.28 (16,8) ATL pro nástroje sestavení V142 s riziky Spectre (ARM64) | 16.10.31205.252
Microsoft. VisualStudio. Component. VC. 14.28. ATL. Spectre | C++ v 14.28 (16,8) ATL pro nástroje sestavení V142 s riziky Spectre (x86 & x64) | 16.10.31205.252
Microsoft. VisualStudio. Component. VC. 14.28. CLI. support | Podpora C++/CLI pro V142 Build Tools (14.28-16.8) | 16.10.31205.252
Microsoft. VisualStudio. Component. VC. 14.28. MFC | C++ v 14.28 (16,8) MFC pro nástroje sestavení V142 (x86 & x64) | 16.10.31205.252
Microsoft. VisualStudio. Component. VC. 14.28. MFC. ARM | C++ v 14.28 (16,8) MFC pro nástroje sestavení V142 (ARM) | 16.10.31205.252
Microsoft. VisualStudio. Component. VC. 14.28. MFC. ARM. Spectre | C++ v 14.28 (16,8) MFC pro nástroje sestavení V142 s omezeními Spectre (ARM) | 16.10.31205.252
Microsoft. VisualStudio. Component. VC. 14.28. MFC. ARM64 | C++ v 14.28 (16,8) MFC pro nástroje sestavení V142 (ARM64) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.28.MFC.ARM64.Spectre | C++ v14.28 (16.8) MFC pro buildovací nástroje v142 s omezeními rizik spectre (ARM64) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.28.MFC.Spectre | C++ v14.28 (16.8) MFC pro buildovací nástroje v142 s omezeními rizik spectre (x86 & x64) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.28.x86.x64 | MSVC v142 – buildovací nástroje VS 2019 C++ x64/x86 (v14.28-16.8) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.28.x86.x64.Spectre | MSVC v142 – VS 2019 C++ x64/x86 Spectre-mitigated libs (v14.28-16.8) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.29.16.10.ARM | MSVC v142 – VS 2019 C++ – nástroje pro sestavení ARM (v14.29-16.10) | 16.10.31313.121
Microsoft.VisualStudio.Component.VC.14.29.16.10.ARM.Spectre | MSVC v142 – VS 2019 C++ ARM Spectre-mitigated libs (v14.29-16.10) | 16.10.31313.121
Microsoft.VisualStudio.Component.VC.14.29.16.10.ARM64 | MSVC V142-VS 2019 C++ ARM64 Build Tools (v 14.29-16.10) | 16.10.31313.121
Microsoft. VisualStudio. Component. VC. 14.29.16.10. ARM64. Spectre | MSVC V142-VS 2019 C++ ARM64 Spectre-zmírňované knihovny (v 14.29-16.10) | 16.10.31313.121
Microsoft. VisualStudio. Component. VC. 14.29.16.10. ATL | C++ v 14.29 (16,10) ATL pro nástroje sestavení V142 (x86 & x64) | 16.10.31313.121
Microsoft. VisualStudio. Component. VC. 14.29.16.10. ATL. ARM | C++ v 14.29 (16,10) ATL pro nástroje sestavení V142 (ARM) | 16.10.31313.121
Microsoft. VisualStudio. Component. VC. 14.29.16.10. ATL. ARM. Spectre | C++ v 14.29 (16,10) ATL pro nástroje sestavení V142 s omezeními Spectre (ARM) | 16.10.31313.121
Microsoft. VisualStudio. Component. VC. 14.29.16.10. ATL. ARM64 | C++ v 14.29 (16,10) ATL pro nástroje sestavení V142 (ARM64) | 16.10.31313.121
Microsoft. VisualStudio. Component. VC. 14.29.16.10. ATL. ARM64. Spectre | C++ v 14.29 (16,10) ATL pro nástroje sestavení V142 s riziky Spectre (ARM64) | 16.10.31313.121
Microsoft.VisualStudio.Component.VC.14.29.16.10.ATL.Spectre | C++ v14.29 (16.10) ATL pro buildovací nástroje v142 se zmírněními rizik spectre (x86 & x64) | 16.10.31313.121
Microsoft.VisualStudio.Component.VC.14.29.16.10.CLI.Support | Podpora C++/CLI pro nástroje sestavení v142 (14.29-16.10) | 16.10.31313.121
Microsoft.VisualStudio.Component.VC.14.29.16.10.MFC | C++ v14.29 (16.10) MFC pro nástroje sestavení v142 (x86 & x64) | 16.10.31313.121
Microsoft.VisualStudio.Component.VC.14.29.16.10.MFC.ARM | C++ v14.29 (16.10) MFC pro nástroje sestavení v142 (ARM) | 16.10.31313.121
Microsoft.VisualStudio.Component.VC.14.29.16.10.MFC.ARM.Spectre | C++ v14.29 (16.10) MFC pro nástroje sestavení v142 s omezením rizik spectre (ARM) | 16.10.31313.121
Microsoft.VisualStudio.Component.VC.14.29.16.10.MFC.ARM64 | C++ v14.29 (16.10) MFC pro nástroje sestavení v142 (ARM64) | 16.10.31313.121
Microsoft.VisualStudio.Component.VC.14.29.16.10.MFC.ARM64.Spectre | C++ v14.29 (16.10) MFC pro buildovací nástroje v142 s omezením rizik spectre (ARM64) | 16.10.31313.121
Microsoft. VisualStudio. Component. VC. 14.29.16.10. MFC. Spectre | C++ v 14.29 (16,10) MFC pro nástroje sestavení V142 s riziky Spectre (x86 & x64) | 16.10.31313.121
Microsoft. VisualStudio. Component. VC. 14.29.16.10. x86. x64 | MSVC V142-VS 2019 C++ x64/x86 Build Tools (v 14.29-16.10) | 16.10.31313.121
Microsoft. VisualStudio. Component. VC. 14.29.16.10. x86. x64. Spectre | MSVC V142-VS 2019 C++ x64/x86 Spectre-zmírnit knihovny (v 14.29-16.10) | 16.10.31313.121
Microsoft. VisualStudio. Component. VC. ATL. ARM | C++ ATL pro nejnovější nástroje V142 Build (ARM) | 16.4.29313.120
Microsoft. VisualStudio. Component. VC. ATL. ARM. Spectre | C++ ATL pro nejnovější nástroje V142 buildu s omezeními Spectre (ARM) | 16.5.29721.120
Microsoft. VisualStudio. Component. VC. ATL. ARM64 | C++ ATL pro nejnovější nástroje V142 Build (ARM64) | 16.4.29313.120
Microsoft. VisualStudio. Component. VC. ATL. ARM64. Spectre | C++ ATL pro nejnovější nástroje sestavení v142 s omezením rizik spectre (ARM64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.ATL.ARM64EC | C++ ATL pro nejnovější nástroje sestavení v142 (ARM64EC – experimentální) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.ATL.ARM64EC.Spectre | C++ ATL pro nejnovější nástroje sestavení v142 s omezením rizik spectre (ARM64EC – experimentální) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.ATL.Spectre | C++ ATL pro nejnovější nástroje sestavení v142 s omezením rizik spectre (x86 & x64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.ATLMFC.Spectre | C++ MFC pro nejnovější nástroje sestavení v142 s omezením rizik spectre (x86 & x64) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.MFC.ARM | Knihovna MFC jazyka C++ pro nejnovější nástroje sestavení v142 (ARM) | 16.4.29313.120
Microsoft.VisualStudio.Component.VC.MFC.ARM.Spectre | C++ MFC pro nejnovější nástroje sestavení v142 s omezením rizik spectre (ARM) | 16.5.29721.120
Microsoft. VisualStudio. Component. VC. MFC. ARM64 | C++ MFC pro nejnovější nástroje V142 Build (ARM64) | 16.4.29313.120
Microsoft. VisualStudio. Component. VC. MFC. ARM64. Spectre | C++ MFC pro nejnovější nástroje V142 buildu s omezeními Spectre (ARM64) | 16.5.29721.120
Microsoft. VisualStudio. Component. VC. MFC. ARM64EC | C++ MFC pro nejnovější nástroje V142 Build (ARM64EC – experimentální) | 16.10.31205.252
Microsoft. VisualStudio. Component. VC. MFC. ARM64EC. Spectre | C++ MFC pro nejnovější nástroje V142 buildu s omezeními Spectre (ARM64EC-experimentální) | 16.10.31205.252
Microsoft. VisualStudio. Component. VC. Redist. MSM | C++ 2019 Distribuovatelný MSMs | 16.5.29515.121
Microsoft. VisualStudio. Component. VC. runtimes. ARM. Spectre | MSVC V142-VS 2019 C++ ARM Spectre – zmírňovaná knihovny (nejnovější) | 16.10.31205.252
Microsoft. VisualStudio. Component. VC. runtimes. ARM64. Spectre | MSVC V142-VS 2019 C++ ARM64 Spectre-zmírňované knihovny (nejnovější) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.Runtimes.ARM64EC.Spectre | MSVC v142 – VS 2019 C++ ARM64EC Spectre-mitigated libs (nejnovější – experimentální) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.Runtimes.x86.x64.Spectre | MSVC v142 – VS 2019 C++ x64/x86 Spectre-mitigated libs (nejnovější)  | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.v141.ARM.Spectre | MSVC v141 – VS 2017 C++ ARM Spectre-mitigated libs (verze 14.16) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.v141.ARM64.Spectre | MSVC v141 – VS 2017 C++ ARM64 Spectre-mitigated libs (verze 14.16) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.v141.ATL | C++ ATL pro nástroje sestavení v141 (x86 & x64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.ATL.ARM | C++ ATL pro buildovací nástroje v141 (ARM) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.ATL.ARM.Spectre | C++ ATL pro nástroje v141 buildu s omezeními Spectre (ARM) | 16.5.29721.120
Microsoft. VisualStudio. Component. VC. v141. ATL. ARM64 | C++ ATL pro nástroje v141 Build (ARM64) | 16.0.28625.61
Microsoft. VisualStudio. Component. VC. v141. ATL. ARM64. Spectre | C++ ATL pro nástroje v141 buildu s omezeními Spectre (ARM64) | 16.0.28625.61
Microsoft. VisualStudio. Component. VC. v141. ATL. Spectre | C++ ATL pro nástroje v141 buildu s omezeními Spectre (x86 & x64) | 16.0.28625.61
Microsoft. VisualStudio. Component. VC. v141. CLI. support | Podpora C++/CLI pro v141 Build Tools (14,16) | 16.3.29207.166
Microsoft. VisualStudio. Component. VC. v141. MFC | C++ MFC pro nástroje v141 Build (x86 & x64) | 16.0.28625.61
Microsoft. VisualStudio. Component. VC. v141. MFC. ARM | C++ MFC pro nástroje v141 Build (ARM) | 16.2.28915.88
Microsoft.VisualStudio.Component.VC.v141.MFC.ARM.Spectre | C++ MFC pro buildovací nástroje v141 s omezením rizik spectre (ARM) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.MFC.ARM64 | C++ MFC pro nástroje sestavení v141 (ARM64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.MFC.ARM64.Spectre | C++ MFC pro buildovací nástroje v141 s omezením rizik spectre (ARM64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.MFC.Spectre | C++ MFC pro buildovací nástroje v141 s omezením rizik spectre (x86 & x64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.x86.x64.Spectre | MSVC v141 – VS 2017 C++ x64/x86 Spectre-mitigated libs (verze 14.16) | 16.5.29515.121
Microsoft.VisualStudio.Component.VisualStudioData | Zdroje dat a odkazy na služby | 16.0.28707.177
Microsoft.VisualStudio.Component.WinXP | Podpora C++ Windows XP pro nástroje VS 2017 (v141) [zastaralé] | 16.10.31205.252
Microsoft. VisualStudio. Web. Mvc4. Components | ASP.NET MVC 4 | 16.10.31205.180
