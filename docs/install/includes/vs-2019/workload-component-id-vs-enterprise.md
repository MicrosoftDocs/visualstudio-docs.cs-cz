---
title: ID úlohy a ID součástí Visual Studio Enterprise 2019
titleSuffix: ''
description: Použití pracovního vytížení a komponenta ID pro instalaci sady Visual Studio pomocí příkazového řádku nebo v závislosti na VSIX manifest
keywords: ''
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.date: 09/23/2019
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.topic: include
ms.openlocfilehash: dd8b952b1bb783a163c9e5ba3a4e338458b1f663
ms.sourcegitcommit: 88f576ac32af31613c1a10c1548275e1ce029f4f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/23/2019
ms.locfileid: "71210177"
---
## <a name="visual-studio-core-editor-included-with-visual-studio-enterprise-2019"></a>Základní editor sady Visual Studio (zahrnutý v Visual Studio Enterprise 2019)

**ÚČET** Microsoft.VisualStudio.Workload.CoreEditor

**Popis:** Základní prostředí sady Visual Studio, včetně úprav kódu s podporou syntaxe, správy zdrojového kódu a správy pracovních položek.

### <a name="components-included-by-this-workload"></a>Pomocí této úlohy zahrnuté komponenty

ID součásti | Název | Version | Typ závislosti
--- | --- | --- | ---
Microsoft.VisualStudio.Component.CoreEditor | Základním editoru sady Visual Studio | 16.1.28811.260 | Požadováno
Microsoft.VisualStudio.Component.StartPageExperiment.Cpp | Visual Studio úvodní stránka pro uživatele jazyka C++ | 16.0.28315.86 | volitelná,

## <a name="azure-development"></a>Vývoj pro Azure

**ÚČET** Microsoft.VisualStudio.Workload.Azure

**Popis:** Sady SDK, nástroje a projekty Azure pro vývoj cloudových aplikací a vytváření prostředků pomocí .NET Core a .NET Framework. Zahrnuje také nástroje pro uzavřeníí aplikace, včetně podpory Docker.

### <a name="components-included-by-this-workload"></a>Pomocí této úlohy zahrnuté komponenty

ID součásti | Název | Version | Typ závislosti
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Jazykové služby Razor | 16.0.28714.129 | Požadováno
Component.Microsoft.VisualStudio.Web.AzureFunctions | Nástroje Azure WebJobs | 16.0.28714.129 | Požadováno
Component.Microsoft.Web.LibraryManager | Správce knihovny | 16.0.28315.86 | Požadováno
Microsoft.Component.MSBuild | MSBuild | 16.0.28517.75 | Požadováno
Microsoft.Net.Component.4.5.2.TargetingPack | Rozhraní .NET framework 4.5.2 targeting pack | 16.0.28517.75 | Požadováno
Microsoft.Net.Component.4.5.TargetingPack | .NET framework 4.5 targeting pack | 16.0.28517.75 | Požadováno
Microsoft.Net.Component.4.6.1.TargetingPack | Rozhraní .NET framework 4.6.1 targeting pack | 16.0.28517.75 | Požadováno
Microsoft.Net.Component.4.7.2.TargetingPack | Rozhraní .NET framework 4.7.2 targeting pack | 16.0.28517.75 | Požadováno
Microsoft. NET. Component. 4.8. SDK | .NET Framework 4,8 SDK | 16.3.29230.54 | Požadováno
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Vývojové nástroje .NET framework 4.7.2 | 16.3.29207.166 | Požadováno
Microsoft. NetCore. Component. DevelopmentTools | Vývojové nástroje .NET Core | 16.3.29207.166 | Požadováno
Microsoft. NetCore. Component. SDK | Sada .NET Core 3,0 SDK | 16.3.29318.74 | Požadováno
Microsoft. NetCore. Component. Web | Vývojové nástroje .NET Core | 16.3.29207.166 | Požadováno
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Azure – nástroje pro tvorbu | 16.0.28625.61 | Požadováno
Microsoft.VisualStudio.Component.Azure.ClientLibs | Knihovny Azure pro .NET | 16.0.28315.86 | Požadováno
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Emulátor výpočtů v Azure | 16.1.28810.153 | Požadováno
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Emulátor úložiště Azure | 16.3.29230.54 | Požadováno
Microsoft.VisualStudio.Component.CloudExplorer | Průzkumník cloudu | 16.0.28625.61 | Požadováno
Microsoft.VisualStudio.Component.Common.Azure.Tools | Nástroje pro připojení a publikování | 16.3.29311.71 | Požadováno
Microsoft.VisualStudio.Component.DockerTools | Kontejnerové vývojové nástroje | 16.3.29103.31 | Požadováno
Microsoft.VisualStudio.Component.FSharp | F#podpora jazyků | 16.0.28315.86 | Požadováno
Microsoft.VisualStudio.Component.FSharp.WebTemplates | F#podpora jazyků pro webové projekty | 16.3.29207.166 | Požadováno
Microsoft.VisualStudio.Component.IISExpress | Služba IIS Express  | 16.0.28315.86 | Požadováno
Microsoft. VisualStudio. Component. IntelliCode | IntelliCode | 0.1 | Požadováno
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostika jazyka JavaScript | 16.0.28517.75 | Požadováno
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Podpora jazyků JavaScript a TypeScript | 16.3.29207.166 | Požadováno
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Základní spravovaný úloze vývoje desktopových aplikací | 16.3.29230.54 | Požadováno
Microsoft.VisualStudio.Component.MSODBC.SQL | SQL Server ovladač ODBC | 16.0.28625.61 | Požadováno
Microsoft.VisualStudio.Component.MSSQL.CMDLnUtils | Nástroje příkazového řádku SQL serveru | 16.0.28707.177 | Požadováno
Microsoft.VisualStudio.Component.NuGet | Správce balíčků NuGet | 16.1.28829.92 | Požadováno
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilátory C# a Visual Basic Roslyn | 16.0.28714.129 | Požadováno
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# a Visual Basic | 16.1.28829.92 | Požadováno
Microsoft.VisualStudio.Component.SQL.ADAL | SQL ADAL runtime | 16.0.28517.75 | Požadováno
Microsoft.VisualStudio.Component.SQL.CLR | Datové typy CLR pro SQL Server | 16.0.28315.86 | Požadováno
Microsoft.VisualStudio.Component.SQL.DataSources | Zdroje dat pro podporu SQL serveru | 16.0.28315.86 | Požadováno
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 16.0.28625.61 | Požadováno
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 16.3.29207.166 | Požadováno
Microsoft.VisualStudio.Component.TextTemplating | Transformace textové šablony | 16.0.28625.61 | Požadováno
Microsoft. VisualStudio. Component. TypeScript. 3.6 | Sada TypeScript 3,6 SDK | 16.0.29207.166 | Požadováno
Microsoft.VisualStudio.Component.Web | Nástroje pro vývoj pro ASP.NET a web | 16.0.28517.75 | Požadováno
Microsoft.VisualStudio.ComponentGroup.Azure.Prerequisites | Požadavky na vývoj pro Azure | 16.3.29311.71 | Požadováno
Microsoft.VisualStudio.ComponentGroup.AzureFunctions | Nástroje Azure WebJobs | 16.0.28621.142 | Požadováno
Microsoft.VisualStudio.ComponentGroup.Web | Vývoj pro ASP.NET a webové nástroje – požadavky | 16.3.29230.54 | Požadováno
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Vývoj pro ASP.NET a web | 16.0.28621.142 | Požadováno
Microsoft.Component.Azure.DataLake.Tools | Azure Data Lake a Stream Analytics Tools | 16.3.29207.166 | Doporučené
Microsoft.Net.Component.4.5.1.TargetingPack | Rozhraní .NET framework 4.5.1 targeting pack | 16.0.28517.75 | Doporučené
Microsoft.Net.Component.4.6.TargetingPack | .NET framework 4.6 targeting pack | 16.0.28517.75 | Doporučené
Microsoft.Net.Component.4.TargetingPack | .NET framework 4 targeting pack | 16.0.28517.75 | Doporučené
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Vývojové nástroje .NET framework 4 – 4.6 | 16.0.28516.191 | Doporučené
Microsoft.Net.Core.Component.SDK.2.1 | Modul runtime .NET Core 2,1 LTS | 16.3.29318.74 | Doporučené
Microsoft.VisualStudio.Component.AspNet45 | Rozšířené funkce ASP.NET | 16.0.28315.86 | Doporučené
Microsoft.VisualStudio.Component.Azure.Kubernetes.Tools | Visual Studio Tools for Kubernetes | 16.0.28625.61 | Doporučené
Microsoft.VisualStudio.Component.Azure.ResourceManager.Tools | Základní nástroje Azure Resource Manageru | 16.0.28517.75 | Doporučené
Microsoft.VisualStudio.Component.Azure.ServiceFabric.Tools | Nástroje Service Fabricu | 16.3.29230.54 | Doporučené
Microsoft.VisualStudio.Component.Azure.Waverton | Základní nástroje pro Azure Cloud Services | 16.3.29311.71 | Doporučené
Microsoft.VisualStudio.Component.Azure.Waverton.BuildTools | Nástroje pro vytváření Azure Cloud Services | 16.3.29207.166 | Doporučené
Microsoft.VisualStudio.Component.Debugger.Snapshot | Snapshot Debugger | 16.2.29003.222 | Doporučené
Microsoft.VisualStudio.Component.Debugger.TimeTravel | Čas cestovního ladicího programu | 16.0.28714.129 | Doporučené
Microsoft.VisualStudio.Component.DiagnosticTools | Nástroje pro profilaci .NET | 16.3.29207.166 | Doporučené
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | 16.1.28829.92 | Doporučené
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 16.0.28517.75 | Doporučené
Microsoft.VisualStudio.ComponentGroup.Azure.CloudServices | Nástroje pro Azure Cloud Services | 16.3.29311.71 | Doporučené
Microsoft.VisualStudio.ComponentGroup.Azure.ResourceManager.Tools | Nástroje Azure Resource Manageru | 16.0.28528.71 | Doporučené
Microsoft.Net.Component.4.6.2.TargetingPack | Rozhraní .NET framework 4.6.2 targeting pack | 16.0.28517.75 | volitelná,
Microsoft.Net.Component.4.7.1.TargetingPack | Rozhraní .NET framework 4.7.1 targeting pack | 16.0.28517.75 | volitelná,
Microsoft.Net.Component.4.7.TargetingPack | .NET framework 4.7 targeting pack | 16.0.28517.75 | volitelná,
Microsoft.Net. Component. 4.8. TargetingPack | Sada targeting pack .NET Framework 4,8 | 16.3.29230.54 | volitelná,
Microsoft.Net.ComponentGroup.4.6.1.DeveloperTools | Vývojové nástroje .NET framework 4.6.1 | 16.3.29207.166 | volitelná,
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | Vývojové nástroje .NET framework 4.6.2 | 16.3.29207.166 | volitelná,
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | Vývojové nástroje .NET framework 4.7.1 | 16.3.29207.166 | volitelná,
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | Vývojové nástroje .NET framework 4.7 | 16.3.29207.166 | volitelná,
Microsoft.Net. Component. 4,8. DeveloperTools | Vývojové nástroje .NET Framework 4,8 | 16.3.29230.54 | volitelná,
Microsoft.VisualStudio.Component.Azure.Storage.AzCopy | Azure Storage AzCopy | 16.0.28517.75 | volitelná,
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | 16.0.28625.61 | volitelná,

## <a name="data-storage-and-processing"></a>Ukládání a zpracování dat

**ÚČET** Microsoft.VisualStudio.Workload.Data

**Popis:** Připojení, vývoj a testování datových řešení pomocí SQL Server, Azure Data Lake nebo Hadoop.

### <a name="components-included-by-this-workload"></a>Pomocí této úlohy zahrnuté komponenty

ID součásti | Název | Version | Typ závislosti
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Jazykové služby Razor | 16.0.28714.129 | Doporučené
Component.Microsoft.Web.LibraryManager | Správce knihovny | 16.0.28315.86 | Doporučené
Microsoft.Component.Azure.DataLake.Tools | Azure Data Lake a Stream Analytics Tools | 16.3.29207.166 | Doporučené
Microsoft.Component.MSBuild | MSBuild | 16.0.28517.75 | Doporučené
Microsoft.Net.Component.4.5.1.TargetingPack | Rozhraní .NET framework 4.5.1 targeting pack | 16.0.28517.75 | Doporučené
Microsoft.Net.Component.4.5.2.TargetingPack | Rozhraní .NET framework 4.5.2 targeting pack | 16.0.28517.75 | Doporučené
Microsoft.Net.Component.4.5.TargetingPack | .NET framework 4.5 targeting pack | 16.0.28517.75 | Doporučené
Microsoft.Net.Component.4.6.TargetingPack | .NET framework 4.6 targeting pack | 16.0.28517.75 | Doporučené
Microsoft.Net.Component.4.7.2.TargetingPack | Rozhraní .NET framework 4.7.2 targeting pack | 16.0.28517.75 | Doporučené
Microsoft. NET. Component. 4.8. SDK | .NET Framework 4,8 SDK | 16.3.29230.54 | Doporučené
Microsoft.Net.Component.4.TargetingPack | .NET framework 4 targeting pack | 16.0.28517.75 | Doporučené
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Vývojové nástroje .NET framework 4.7.2 | 16.3.29207.166 | Doporučené
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Vývojové nástroje .NET framework 4 – 4.6 | 16.0.28516.191 | Doporučené
Microsoft. NetCore. Component. SDK | Sada .NET Core 3,0 SDK | 16.3.29318.74 | Doporučené
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Azure – nástroje pro tvorbu | 16.0.28625.61 | Doporučené
Microsoft.VisualStudio.Component.Azure.ClientLibs | Knihovny Azure pro .NET | 16.0.28315.86 | Doporučené
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Emulátor výpočtů v Azure | 16.1.28810.153 | Doporučené
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Emulátor úložiště Azure | 16.3.29230.54 | Doporučené
Microsoft.VisualStudio.Component.Azure.Waverton | Základní nástroje pro Azure Cloud Services | 16.3.29311.71 | Doporučené
Microsoft.VisualStudio.Component.Azure.Waverton.BuildTools | Nástroje pro vytváření Azure Cloud Services | 16.3.29207.166 | Doporučené
Microsoft.VisualStudio.Component.CloudExplorer | Průzkumník cloudu | 16.0.28625.61 | Doporučené
Microsoft.VisualStudio.Component.Common.Azure.Tools | Nástroje pro připojení a publikování | 16.3.29311.71 | Doporučené
Microsoft.VisualStudio.Component.DockerTools | Kontejnerové vývojové nástroje | 16.3.29103.31 | Doporučené
Microsoft.VisualStudio.Component.IISExpress | Služba IIS Express  | 16.0.28315.86 | Doporučené
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostika jazyka JavaScript | 16.0.28517.75 | Doporučené
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Podpora jazyků JavaScript a TypeScript | 16.3.29207.166 | Doporučené
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Základní spravovaný úloze vývoje desktopových aplikací | 16.3.29230.54 | Doporučené
Microsoft.VisualStudio.Component.MSODBC.SQL | SQL Server ovladač ODBC | 16.0.28625.61 | Doporučené
Microsoft.VisualStudio.Component.MSSQL.CMDLnUtils | Nástroje příkazového řádku SQL serveru | 16.0.28707.177 | Doporučené
Microsoft.VisualStudio.Component.NuGet | Správce balíčků NuGet | 16.1.28829.92 | Doporučené
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilátory C# a Visual Basic Roslyn | 16.0.28714.129 | Doporučené
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# a Visual Basic | 16.1.28829.92 | Doporučené
Microsoft.VisualStudio.Component.SQL.ADAL | SQL ADAL runtime | 16.0.28517.75 | Doporučené
Microsoft.VisualStudio.Component.SQL.CLR | Datové typy CLR pro SQL Server | 16.0.28315.86 | Doporučené
Microsoft.VisualStudio.Component.SQL.DataSources | Zdroje dat pro podporu SQL serveru | 16.0.28315.86 | Doporučené
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 16.0.28625.61 | Doporučené
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 16.3.29207.166 | Doporučené
Microsoft.VisualStudio.Component.TextTemplating | Transformace textové šablony | 16.0.28625.61 | Doporučené
Microsoft. VisualStudio. Component. TypeScript. 3.6 | Sada TypeScript 3,6 SDK | 16.0.29207.166 | Doporučené
Microsoft.VisualStudio.Component.Web | Nástroje pro vývoj pro ASP.NET a web | 16.0.28517.75 | Doporučené
Microsoft.VisualStudio.ComponentGroup.Web | Vývoj pro ASP.NET a webové nástroje – požadavky | 16.3.29230.54 | Doporučené
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Vývoj pro ASP.NET a web | 16.0.28621.142 | Doporučené
Microsoft.Net.Component.4.6.1.TargetingPack | Rozhraní .NET framework 4.6.1 targeting pack | 16.0.28517.75 | volitelná,
Microsoft.VisualStudio.Component.FSharp.Desktop | F#Podpora klasické pracovní plochy jazyka | 16.0.28315.86 | volitelná,

## <a name="data-science-and-analytical-applications"></a>Aplikace pro datové vědy a analýzy

**ÚČET** Microsoft.VisualStudio.Workload.DataScience

**Popis:** Jazyky a nástroje pro vytváření aplikací pro datové vědy, včetně Pythonu F#a.

### <a name="components-included-by-this-workload"></a>Pomocí této úlohy zahrnuté komponenty

ID součásti | Název | Version | Typ závislosti
--- | --- | --- | ---
Microsoft.Component.PythonTools | Podpora jazyka Python | 16.0.28625.61 | Doporučené
Microsoft.Component.PythonTools.Minicondax64 | Python miniconda | 16.2.29003.222 | Doporučené
Microsoft.Component.PythonTools.Web | Podpora webů v Pythonu | 16.0.28517.75 | Doporučené
Microsoft.Net.Component.4.6.1.TargetingPack | Rozhraní .NET framework 4.6.1 targeting pack | 16.0.28517.75 | Doporučené
Microsoft.VisualStudio.Component.Common.Azure.Tools | Nástroje pro připojení a publikování | 16.3.29311.71 | Doporučené
Microsoft.VisualStudio.Component.FSharp.Desktop | F#Podpora klasické pracovní plochy jazyka | 16.0.28315.86 | Doporučené
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Podpora jazyků JavaScript a TypeScript | 16.3.29207.166 | Doporučené
Microsoft.VisualStudio.Component.NuGet | Správce balíčků NuGet | 16.1.28829.92 | Doporučené
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilátory C# a Visual Basic Roslyn | 16.0.28714.129 | Doporučené
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# a Visual Basic | 16.1.28829.92 | Doporučené
Microsoft. VisualStudio. Component. TypeScript. 3.6 | Sada TypeScript 3,6 SDK | 16.0.29207.166 | Doporučené
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 16.0.28517.75 | Doporučené
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Vývoj pro ASP.NET a web | 16.0.28621.142 | Doporučené
Microsoft.ComponentGroup.PythonTools.NativeDevelopment | Nástroje Pythonu pro nativní vývoj | 16.2.29020.229 | volitelná,
Microsoft.VisualStudio.Component.Graphics.Tools | Ladicí program grafiky a profiler GPU pro DirectX | 16.0.28625.61 | volitelná,
Microsoft.VisualStudio.Component.VC.CoreIde | C++základní funkce | 16.0.28625.61 | volitelná,
Microsoft.VisualStudio.Component.VC.DiagnosticTools | Nástroje pro profilaci v C++ | 16.0.28625.61 | volitelná,
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | Nástroje MSVC V142-VS C++ 2019 x64/x86 Build Tools (v 14.23) | 16.3.29230.54 | volitelná,
Microsoft.VisualStudio.Component.Windows10SDK | Windows Universal C Runtime | 16.3.29311.71 | volitelná,
Microsoft. VisualStudio. Component. Windows10SDK. 18362 | Windows 10 SDK (10.0.18362.0) | 16.1.28829.92 | volitelná,

## <a name="net-desktop-development"></a>Vývoj desktopových aplikací .NET

**ÚČET** Microsoft.VisualStudio.Workload.ManagedDesktop

**Popis:** Sestavujte aplikace WPF, model Windows Forms a konzolových aplikací pomocí C#, F# Visual Basic a pomocí .NET Core a .NET Framework.

### <a name="components-included-by-this-workload"></a>Pomocí této úlohy zahrnuté komponenty

ID součásti | Název | Version | Typ závislosti
--- | --- | --- | ---
Microsoft.Component.MSBuild | MSBuild | 16.0.28517.75 | Požadováno
Microsoft.Net.Component.4.7.2.TargetingPack | Rozhraní .NET framework 4.7.2 targeting pack | 16.0.28517.75 | Požadováno
Microsoft. NET. Component. 4.8. SDK | .NET Framework 4,8 SDK | 16.3.29230.54 | Požadováno
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Vývojové nástroje .NET framework 4.7.2 | 16.3.29207.166 | Požadováno
Microsoft. NetCore. Component. SDK | Sada .NET Core 3,0 SDK | 16.3.29318.74 | Požadováno
Microsoft. VisualStudio. Component. IntelliCode | IntelliCode | 0.1 | Požadováno
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Základní spravovaný úloze vývoje desktopových aplikací | 16.3.29230.54 | Požadováno
Microsoft.VisualStudio.Component.ManagedDesktop.Prerequisites | Nástroje pro vývoj desktopových aplikací .NET | 16.3.29230.54 | Požadováno
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilátory C# a Visual Basic Roslyn | 16.0.28714.129 | Požadováno
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# a Visual Basic | 16.1.28829.92 | Požadováno
Microsoft.VisualStudio.Component.SQL.CLR | Datové typy CLR pro SQL Server | 16.0.28315.86 | Požadováno
Microsoft.VisualStudio.Component.TextTemplating | Transformace textové šablony | 16.0.28625.61 | Požadováno
Component.Microsoft.VisualStudio.LiveShare | Live Share | 1.0.826 | Doporučené
Microsoft.ComponentGroup.Blend | Blend for Visual Studio | 16.0.28315.86 | Doporučené
Microsoft.Net.Component.4.5.1.TargetingPack | Rozhraní .NET framework 4.5.1 targeting pack | 16.0.28517.75 | Doporučené
Microsoft.Net.Component.4.5.2.TargetingPack | Rozhraní .NET framework 4.5.2 targeting pack | 16.0.28517.75 | Doporučené
Microsoft.Net.Component.4.5.TargetingPack | .NET framework 4.5 targeting pack | 16.0.28517.75 | Doporučené
Microsoft.Net.Component.4.6.1.TargetingPack | Rozhraní .NET framework 4.6.1 targeting pack | 16.0.28517.75 | Doporučené
Microsoft.Net.Component.4.6.TargetingPack | .NET framework 4.6 targeting pack | 16.0.28517.75 | Doporučené
Microsoft.Net.Component.4.TargetingPack | .NET framework 4 targeting pack | 16.0.28517.75 | Doporučené
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Vývojové nástroje .NET framework 4 – 4.6 | 16.0.28516.191 | Doporučené
Microsoft.Net.Core.Component.SDK.2.1 | Modul runtime .NET Core 2,1 LTS | 16.3.29318.74 | Doporučené
Microsoft. NetCore. Component. DevelopmentTools | Vývojové nástroje .NET Core | 16.3.29207.166 | Doporučené
Microsoft.VisualStudio.Component.Debugger.JustInTime | Just-In-Time debugger | 16.0.28517.75 | Doporučené
Microsoft.VisualStudio.Component.DiagnosticTools | Nástroje pro profilaci .NET | 16.3.29207.166 | Doporučené
Microsoft.VisualStudio.Component.EntityFramework | Entity Framework 6 tools | 16.0.28315.86 | Doporučené
Microsoft.VisualStudio.Component.FSharp | F#podpora jazyků | 16.0.28315.86 | Doporučené
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | 16.1.28829.92 | Doporučené
Microsoft.VisualStudio.Component.LiveUnitTesting | Live Unit Testing | 16.1.28811.260 | Doporučené
Microsoft.VisualStudio.Component.NuGet | Správce balíčků NuGet | 16.1.28829.92 | Doporučené
Component.Dotfuscator | PreEmptive ochranu – řešení Dotfuscator | 16.0.28528.71 | volitelná,
Component.Microsoft.VisualStudio.RazorExtension | Jazykové služby Razor | 16.0.28714.129 | volitelná,
Component.Microsoft.Web.LibraryManager | Správce knihovny | 16.0.28315.86 | volitelná,
Microsoft.Net.Component.4.6.2.TargetingPack | Rozhraní .NET framework 4.6.2 targeting pack | 16.0.28517.75 | volitelná,
Microsoft.Net.Component.4.7.1.TargetingPack | Rozhraní .NET framework 4.7.1 targeting pack | 16.0.28517.75 | volitelná,
Microsoft.Net.Component.4.7.TargetingPack | .NET framework 4.7 targeting pack | 16.0.28517.75 | volitelná,
Microsoft.Net. Component. 4.8. TargetingPack | Sada targeting pack .NET Framework 4,8 | 16.3.29230.54 | volitelná,
Microsoft.Net.ComponentGroup.4.6.1.DeveloperTools | Vývojové nástroje .NET framework 4.6.1 | 16.3.29207.166 | volitelná,
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | Vývojové nástroje .NET framework 4.6.2 | 16.3.29207.166 | volitelná,
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | Vývojové nástroje .NET framework 4.7.1 | 16.3.29207.166 | volitelná,
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | Vývojové nástroje .NET framework 4.7 | 16.3.29207.166 | volitelná,
Microsoft.Net. Component. 4,8. DeveloperTools | Vývojové nástroje .NET Framework 4,8 | 16.3.29230.54 | volitelná,
Microsoft.VisualStudio.Component.ClassDesigner | Návrhář tříd | 16.0.28528.71 | volitelná,
Microsoft.VisualStudio.Component.CodeClone | Klonování kódu | 16.3.29311.71 | volitelná,
Microsoft.VisualStudio.Component.CodeMap | Mapa kódu | 16.0.28625.61 | volitelná,
Microsoft.VisualStudio.Component.Common.Azure.Tools | Nástroje pro připojení a publikování | 16.3.29311.71 | volitelná,
Microsoft.VisualStudio.Component.DependencyValidation.Enterprise | Živé ověření závislosti | 16.0.28625.61 | volitelná,
Microsoft.VisualStudio.Component.DockerTools | Kontejnerové vývojové nástroje | 16.3.29103.31 | volitelná,
Microsoft.VisualStudio.Component.FSharp.Desktop | F#Podpora klasické pracovní plochy jazyka | 16.0.28315.86 | volitelná,
Microsoft.VisualStudio.Component.GraphDocument | DGML editor | 16.0.28625.61 | volitelná,
Microsoft.VisualStudio.Component.IISExpress | Služba IIS Express  | 16.0.28315.86 | volitelná,
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostika jazyka JavaScript | 16.0.28517.75 | volitelná,
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Podpora jazyků JavaScript a TypeScript | 16.3.29207.166 | volitelná,
Microsoft.VisualStudio.Component.MSODBC.SQL | SQL Server ovladač ODBC | 16.0.28625.61 | volitelná,
Microsoft.VisualStudio.Component.MSSQL.CMDLnUtils | Nástroje příkazového řádku SQL serveru | 16.0.28707.177 | volitelná,
Microsoft.VisualStudio.Component.PortableLibrary | .NET portable Library targeting pack | 16.0.28517.75 | volitelná,
Microsoft.VisualStudio.Component.SQL.ADAL | SQL ADAL runtime | 16.0.28517.75 | volitelná,
Microsoft.VisualStudio.Component.SQL.DataSources | Zdroje dat pro podporu SQL serveru | 16.0.28315.86 | volitelná,
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 16.0.28625.61 | volitelná,
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 16.3.29207.166 | volitelná,
Microsoft. VisualStudio. Component. TypeScript. 3.6 | Sada TypeScript 3,6 SDK | 16.0.29207.166 | volitelná,
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | 16.0.28625.61 | volitelná,
Microsoft.VisualStudio.Component.Web | Nástroje pro vývoj pro ASP.NET a web | 16.0.28517.75 | volitelná,
Microsoft. VisualStudio. Component. Windows10SDK. 18362 | Windows 10 SDK (10.0.18362.0) | 16.1.28829.92 | volitelná,
Microsoft.VisualStudio.ComponentGroup.ArchitectureTools.Managed | Architektury a analytické nástroje | 16.3.29318.136 | volitelná,
Microsoft. VisualStudio. Component. MSIX. balení | Nástroje pro vytváření balíčků MSIX | 16.3.29230.54 | volitelná,
Microsoft.VisualStudio.ComponentGroup.Web | Vývoj pro ASP.NET a webové nástroje – požadavky | 16.3.29230.54 | volitelná,
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Vývoj pro ASP.NET a web | 16.0.28621.142 | volitelná,

## <a name="game-development-with-unity"></a>Vývoj her pomocí Unity

**ÚČET** Microsoft.VisualStudio.Workload.ManagedGame

**Popis:** Vytvářejte 2D a 3D hry pomocí Unity, výkonného vývojového prostředí pro různé platformy.

### <a name="components-included-by-this-workload"></a>Pomocí této úlohy zahrnuté komponenty

ID součásti | Název | Version | Typ závislosti
--- | --- | --- | ---
Microsoft.Net.Component.3.5.DeveloperTools | Vývojové nástroje .NET framework 3.5 | 16.0.28517.75 | Požadováno
Microsoft.Net.Component.4.7.1.TargetingPack | Rozhraní .NET framework 4.7.1 targeting pack | 16.0.28517.75 | Požadováno
Microsoft.VisualStudio.Component.NuGet | Správce balíčků NuGet | 16.1.28829.92 | Požadováno
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilátory C# a Visual Basic Roslyn | 16.0.28714.129 | Požadováno
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# a Visual Basic | 16.1.28829.92 | Požadováno
Microsoft.VisualStudio.Component.Unity | Visual Studio Tools for Unity | 16.0.28315.86 | Požadováno
Component.UnityEngine.x64 | Editor bitových procesorů Unity 2018,3 64 | 16.1.28810.153 | Doporučené
Component.UnityEngine.x86 | 32bitový Editor Unity 5.6 | 16.1.28811.260 | Doporučené

## <a name="linux-development-with-c"></a>Vývoj pro Linux v C++

**ÚČET** Microsoft.VisualStudio.Workload.NativeCrossPlat

**Popis:** Vytváření a ladění aplikace běžící v prostředí Linux.

### <a name="components-included-by-this-workload"></a>Pomocí této úlohy zahrnuté komponenty

ID součásti | Název | Version | Typ závislosti
--- | --- | --- | ---
Component.MDD.Linux | C++pro vývoj pro Linux | 16.0.28625.61 | Požadováno
Microsoft.VisualStudio.Component.VC.CoreIde | C++základní funkce | 16.0.28625.61 | Požadováno
Component.Linux.CMake | C++Nástroje CMake pro Linux | 16.2.29003.222 | Doporučené
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Vývoj pro ASP.NET a web | 16.0.28621.142 | Doporučené
Component.MDD.Linux.GCC.arm | Nástroje pro vývoj integrovaných a IoT | 16.2.28915.88 | volitelná,

## <a name="desktop-development-with-c"></a>Vývoj desktopových aplikací pomocí C++

**ÚČET** Microsoft.VisualStudio.Workload.NativeDesktop

**Popis:** Vytvářejte moderní C++ aplikace pro Windows pomocí nástrojů podle vašeho výběru, včetně MSVC, Clang, cmake nebo msbuildu.

### <a name="components-included-by-this-workload"></a>Pomocí této úlohy zahrnuté komponenty

ID součásti | Název | Version | Typ závislosti
--- | --- | --- | ---
Microsoft.Component.MSBuild | MSBuild | 16.0.28517.75 | Požadováno
Microsoft.VisualStudio.Component.ClassDesigner | Návrhář tříd | 16.0.28528.71 | Požadováno
Microsoft.VisualStudio.Component.CodeMap | Mapa kódu | 16.0.28625.61 | Požadováno
Microsoft.VisualStudio.Component.GraphDocument | DGML editor | 16.0.28625.61 | Požadováno
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilátory C# a Visual Basic Roslyn | 16.0.28714.129 | Požadováno
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 16.0.28625.61 | Požadováno
Microsoft.VisualStudio.Component.TextTemplating | Transformace textové šablony | 16.0.28625.61 | Požadováno
Microsoft.VisualStudio.Component.VC.CoreIde | C++základní funkce | 16.0.28625.61 | Požadováno
Microsoft.VisualStudio.Component.VC.Redist.14.Latest | C++2019 Distribuovatelný aktualizace | 16.0.28625.61 | Požadováno
Microsoft.VisualStudio.ComponentGroup.ArchitectureTools.Native | Nástroje pro architekturu pro C++ | 16.0.28621.142 | Požadováno
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Core | C++základní desktopové funkce | 16.2.29012.281 | Požadováno
Component.Microsoft.VisualStudio.LiveShare | Live Share | 1.0.826 | Doporučené
Microsoft.VisualStudio.Component.Debugger.JustInTime | Just-In-Time debugger | 16.0.28517.75 | Doporučené
Microsoft.VisualStudio.Component.Graphics.Tools | Ladicí program grafiky a profiler GPU pro DirectX | 16.0.28625.61 | Doporučené
Microsoft. VisualStudio. Component. IntelliCode | IntelliCode | 0.1 | Doporučené
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | 16.1.28829.92 | Doporučené
Microsoft.VisualStudio.Component.NuGet | Správce balíčků NuGet | 16.1.28829.92 | Doporučené
Microsoft.VisualStudio.Component.VC.ATL | C++ATL pro nejnovější nástroje V142 Build (x86 & x64) | 16.3.29230.54 | Doporučené
Microsoft.VisualStudio.Component.VC.CMake.Project | C++Nástroje CMake pro Windows | 16.3.29103.31 | Doporučené
Microsoft.VisualStudio.Component.VC.DiagnosticTools | Nástroje pro profilaci v C++ | 16.0.28625.61 | Doporučené
Microsoft.VisualStudio.Component.VC.TestAdapterForBoostTest | Testovací adaptér pro Boost.Test | 16.0.28517.75 | Doporučené
Microsoft.VisualStudio.Component.VC.TestAdapterForGoogleTest | Testovací adaptér pro Google Test | 16.0.28517.75 | Doporučené
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | Nástroje MSVC V142-VS C++ 2019 x64/x86 Build Tools (v 14.23) | 16.3.29230.54 | Doporučené
Microsoft. VisualStudio. Component. Windows10SDK. 18362 | Windows 10 SDK (10.0.18362.0) | 16.1.28829.92 | Doporučené
Microsoft. VisualStudio. Component. WebToolsExtensions. CMake | Editor JSON | 16.3.29207.166 | Doporučené
Component.Incredibuild | IncrediBuild – urychlení sestavení | 16.0.28528.71 | volitelná,
Component.IncredibuildMenu | IncrediBuildMenu | 1.5.0.10 | volitelná,
Microsoft.Component.VC.Runtime.UCRTSDK | Windows Universal CRT SDK | 16.0.28625.61 | volitelná,
Microsoft.Net.Component.4.6.1.TargetingPack | Rozhraní .NET framework 4.6.1 targeting pack | 16.0.28517.75 | volitelná,
Microsoft. NET. Component. 4.8. SDK | .NET Framework 4,8 SDK | 16.3.29230.54 | volitelná,
Microsoft.VisualStudio.Component.VC.140 | MSVC v140-VS 2015 C++ Build Tools (v 14.00) | 16.0.28625.61 | volitelná,
Microsoft.VisualStudio.Component.VC.ATLMFC | C++MFC pro nejnovější nástroje V142 Build (x86 & x64) | 16.3.29230.54 | volitelná,
Microsoft.VisualStudio.Component.VC.CLI.Support | C++Podpora/CLI pro nástroje V142 Build (14,23) | 16.3.29230.54 | volitelná,
Microsoft. VisualStudio. Component. VC. LLVM. Clang | C++Kompilátor Clang pro Windows (8.0.1) | 16.3.29230.54 | volitelná,
Microsoft. VisualStudio. Component. VC. LLVM. ClangToolset | C++Clang – CL pro nástroje sestavení V142 (x64/x86) | 16.3.29207.166 | volitelná,
Microsoft.VisualStudio.Component.VC.Modules.x86.x64 | C++Moduly pro V142 Build Tools (x64/x86 – experimentální) | 16.0.28625.61 | volitelná,
Microsoft.VisualStudio.Component.VC.v141.x86.x64 | Nástroje MSVC v141-VS C++ 2017 x64/x86 Build Tools (v 14.16) | 16.1.28829.92 | volitelná,
Microsoft.VisualStudio.Component.Windows10SDK.16299 | Windows 10 SDK (10.0.16299.0) | 16.0.28517.75 | volitelná,
Microsoft.VisualStudio.Component.Windows10SDK.17134 | Windows 10 SDK (10.0.17134.0) | 16.0.28517.75 | volitelná,
Microsoft.VisualStudio.Component.Windows10SDK.17763 | Windows 10 SDK (10.0.17763.0) | 16.0.28517.75 | volitelná,
Microsoft. VisualStudio. Component. NativeDesktop. LLVM. Clang | C++Nástroje Clang pro Windows (8.0.1-x64/x86) | 16.3.29230.54 | volitelná,

## <a name="game-development-with-c"></a>Vývoj her v C++

**ÚČET** Microsoft.VisualStudio.Workload.NativeGame

**Popis:** Využijte kompletní sílu C++ pro sestavování profesionálních her využívajících rozhraní DirectX, Unreal nebo Cocos2d.

### <a name="components-included-by-this-workload"></a>Pomocí této úlohy zahrnuté komponenty

ID součásti | Název | Version | Typ závislosti
--- | --- | --- | ---
Microsoft.VisualStudio.Component.VC.CoreIde | C++základní funkce | 16.0.28625.61 | Požadováno
Microsoft.VisualStudio.Component.VC.Redist.14.Latest | C++2019 Distribuovatelný aktualizace | 16.0.28625.61 | Požadováno
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | Nástroje MSVC V142-VS C++ 2019 x64/x86 Build Tools (v 14.23) | 16.3.29230.54 | Požadováno
Microsoft.VisualStudio.Component.Windows10SDK | Windows Universal C Runtime | 16.3.29311.71 | Požadováno
Microsoft.VisualStudio.Component.Graphics.Tools | Ladicí program grafiky a profiler GPU pro DirectX | 16.0.28625.61 | Doporučené
Microsoft. VisualStudio. Component. IntelliCode | IntelliCode | 0.1 | Doporučené
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | 16.1.28829.92 | Doporučené
Microsoft.VisualStudio.Component.VC.DiagnosticTools | Nástroje pro profilaci v C++ | 16.0.28625.61 | Doporučené
Microsoft. VisualStudio. Component. Windows10SDK. 18362 | Windows 10 SDK (10.0.18362.0) | 16.1.28829.92 | Doporučené
Component.Android.NDK.R16B | Android NDK (R16B) | 16.3.29318.136 | volitelná,
Component.Android.SDK25.Private | Instalace Android SDK (úroveň rozhraní API 25) (místní instalace pro vývoj pro C++mobilní zařízení pomocí) | 16.0.28625.61 | volitelná,
Component.Ant | Apache Ant (1.9.3) | 1.9.3.8 | volitelná,
Component.Cocos | Cocos | 16.0.28315.86 | volitelná,
Component.Incredibuild | IncrediBuild – urychlení sestavení | 16.0.28528.71 | volitelná,
Component.IncredibuildMenu | IncrediBuildMenu | 1.5.0.10 | volitelná,
Component.MDD.Android | Vývojové nástroje C++ pro Android | 16.0.28517.75 | volitelná,
Component.OpenJDK | OpenJDK (distribuce Microsoft) | 16.1.28811.260 | volitelná,
Component.Unreal | Instalační program Unreal Engine | 16.1.28810.153 | volitelná,
Component.Unreal.Android | Podpora prostředí Android IDE pro modul Unreal | 16.1.28810.153 | volitelná,
Microsoft.Net.Component.4.5.1.TargetingPack | Rozhraní .NET framework 4.5.1 targeting pack | 16.0.28517.75 | volitelná,
Microsoft.Net.Component.4.5.2.TargetingPack | Rozhraní .NET framework 4.5.2 targeting pack | 16.0.28517.75 | volitelná,
Microsoft.Net.Component.4.5.TargetingPack | .NET framework 4.5 targeting pack | 16.0.28517.75 | volitelná,
Microsoft.Net.Component.4.6.2.TargetingPack | Rozhraní .NET framework 4.6.2 targeting pack | 16.0.28517.75 | volitelná,
Microsoft.Net.Component.4.6.TargetingPack | .NET framework 4.6 targeting pack | 16.0.28517.75 | volitelná,
Microsoft.Net.Component.4.7.2.TargetingPack | Rozhraní .NET framework 4.7.2 targeting pack | 16.0.28517.75 | volitelná,
Microsoft. NET. Component. 4.8. SDK | .NET Framework 4,8 SDK | 16.3.29230.54 | volitelná,
Microsoft.Net.Component.4.TargetingPack | .NET framework 4 targeting pack | 16.0.28517.75 | volitelná,
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Vývojové nástroje .NET framework 4.7.2 | 16.3.29207.166 | volitelná,
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Vývojové nástroje .NET framework 4 – 4.6 | 16.0.28516.191 | volitelná,
Microsoft.VisualStudio.Component.NuGet.BuildTools | NuGet cíle a úlohy sestavení | 16.1.28829.92 | volitelná,
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilátory C# a Visual Basic Roslyn | 16.0.28714.129 | volitelná,
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# a Visual Basic | 16.1.28829.92 | volitelná,
Microsoft.VisualStudio.Component.Windows10SDK.16299 | Windows 10 SDK (10.0.16299.0) | 16.0.28517.75 | volitelná,
Microsoft.VisualStudio.Component.Windows10SDK.17134 | Windows 10 SDK (10.0.17134.0) | 16.0.28517.75 | volitelná,
Microsoft.VisualStudio.Component.Windows10SDK.17763 | Windows 10 SDK (10.0.17763.0) | 16.0.28517.75 | volitelná,

## <a name="mobile-development-with-c"></a>Vývoj mobilních aplikací pomocí C++

**ÚČET** Microsoft.VisualStudio.Workload.NativeMobile

**Popis:** Sestavujte aplikace pro různé platformy pro iOS, Android nebo C++Windows pomocí.

### <a name="components-included-by-this-workload"></a>Pomocí této úlohy zahrnuté komponenty

ID součásti | Název | Version | Typ závislosti
--- | --- | --- | ---
Component.Android.SDK25.Private | Instalace Android SDK (úroveň rozhraní API 25) (místní instalace pro vývoj pro C++mobilní zařízení pomocí) | 16.0.28625.61 | Požadováno
Component.OpenJDK | OpenJDK (distribuce Microsoft) | 16.1.28811.260 | Požadováno
Microsoft.VisualStudio.Component.VC.CoreIde | C++základní funkce | 16.0.28625.61 | Požadováno
Component.Android.NDK.R16B | Android NDK (R16B) | 16.3.29318.136 | Doporučené
Component.Ant | Apache Ant (1.9.3) | 1.9.3.8 | Doporučeno
Component.MDD.Android | Vývojové nástroje C++ pro Android | 16.0.28517.75 | Doporučené
Microsoft. VisualStudio. Component. IntelliCode | IntelliCode | 0.1 | Doporučené
Component.Android.NDK.R16B_3264 | Android NDK (R16B) (32 bitů) | 16.3.29318.136 | volitelná,
Component.Google.Android.Emulator.API25.Private | Google Android Emulator (rozhraní API úrovně 25) (místní instalace) | 16.1.28810.153 | volitelná,
Component.HAXM.Private | Intel Hardware Accelerated provádění Manager (HAXM) (místní instalace) | 16.0.28528.71 | volitelná,
Component.Incredibuild | IncrediBuild – urychlení sestavení | 16.0.28528.71 | volitelná,
Component.IncredibuildMenu | IncrediBuildMenu | 1.5.0.10 | volitelná,
Component.MDD.IOS | Nástroje pro vývoj iOS C++ | 16.0.28517.75 | volitelná,

## <a name="net-core-cross-platform-development"></a>Vývoj pro různé platformy .NET core

**ÚČET** Microsoft.VisualStudio.Workload.NetCoreTools

**Popis:** Vytvářejte aplikace pro různé platformy pomocí .NET Core, ASP.NET Core, HTML/JavaScript a kontejnerů včetně podpory Docker.

### <a name="components-included-by-this-workload"></a>Pomocí této úlohy zahrnuté komponenty

ID součásti | Název | Version | Typ závislosti
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Jazykové služby Razor | 16.0.28714.129 | Požadováno
Component.Microsoft.Web.LibraryManager | Správce knihovny | 16.0.28315.86 | Požadováno
Microsoft.Component.MSBuild | MSBuild | 16.0.28517.75 | Požadováno
Microsoft.Net.Component.4.5.2.TargetingPack | Rozhraní .NET framework 4.5.2 targeting pack | 16.0.28517.75 | Požadováno
Microsoft.Net.Component.4.5.TargetingPack | .NET framework 4.5 targeting pack | 16.0.28517.75 | Požadováno
Microsoft.Net.Component.4.6.1.TargetingPack | Rozhraní .NET framework 4.6.1 targeting pack | 16.0.28517.75 | Požadováno
Microsoft.Net.Component.4.7.2.TargetingPack | Rozhraní .NET framework 4.7.2 targeting pack | 16.0.28517.75 | Požadováno
Microsoft. NET. Component. 4.8. SDK | .NET Framework 4,8 SDK | 16.3.29230.54 | Požadováno
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Vývojové nástroje .NET framework 4.7.2 | 16.3.29207.166 | Požadováno
Microsoft. NetCore. Component. DevelopmentTools | Vývojové nástroje .NET Core | 16.3.29207.166 | Požadováno
Microsoft. NetCore. Component. SDK | Sada .NET Core 3,0 SDK | 16.3.29318.74 | Požadováno
Microsoft. NetCore. Component. Web | Vývojové nástroje .NET Core | 16.3.29207.166 | Požadováno
Microsoft.VisualStudio.Component.Common.Azure.Tools | Nástroje pro připojení a publikování | 16.3.29311.71 | Požadováno
Microsoft.VisualStudio.Component.DockerTools | Kontejnerové vývojové nástroje | 16.3.29103.31 | Požadováno
Microsoft.VisualStudio.Component.FSharp | F#podpora jazyků | 16.0.28315.86 | Požadováno
Microsoft.VisualStudio.Component.FSharp.WebTemplates | F#podpora jazyků pro webové projekty | 16.3.29207.166 | Požadováno
Microsoft.VisualStudio.Component.IISExpress | Služba IIS Express  | 16.0.28315.86 | Požadováno
Microsoft. VisualStudio. Component. IntelliCode | IntelliCode | 0.1 | Požadováno
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostika jazyka JavaScript | 16.0.28517.75 | Požadováno
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Podpora jazyků JavaScript a TypeScript | 16.3.29207.166 | Požadováno
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Základní spravovaný úloze vývoje desktopových aplikací | 16.3.29230.54 | Požadováno
Microsoft.VisualStudio.Component.MSODBC.SQL | SQL Server ovladač ODBC | 16.0.28625.61 | Požadováno
Microsoft.VisualStudio.Component.MSSQL.CMDLnUtils | Nástroje příkazového řádku SQL serveru | 16.0.28707.177 | Požadováno
Microsoft.VisualStudio.Component.NuGet | Správce balíčků NuGet | 16.1.28829.92 | Požadováno
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilátory C# a Visual Basic Roslyn | 16.0.28714.129 | Požadováno
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# a Visual Basic | 16.1.28829.92 | Požadováno
Microsoft.VisualStudio.Component.SQL.ADAL | SQL ADAL runtime | 16.0.28517.75 | Požadováno
Microsoft.VisualStudio.Component.SQL.CLR | Datové typy CLR pro SQL Server | 16.0.28315.86 | Požadováno
Microsoft.VisualStudio.Component.SQL.DataSources | Zdroje dat pro podporu SQL serveru | 16.0.28315.86 | Požadováno
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 16.0.28625.61 | Požadováno
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 16.3.29207.166 | Požadováno
Microsoft.VisualStudio.Component.TextTemplating | Transformace textové šablony | 16.0.28625.61 | Požadováno
Microsoft. VisualStudio. Component. TypeScript. 3.6 | Sada TypeScript 3,6 SDK | 16.0.29207.166 | Požadováno
Microsoft.VisualStudio.ComponentGroup.Web | Vývoj pro ASP.NET a webové nástroje – požadavky | 16.3.29230.54 | Požadováno
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Vývoj pro ASP.NET a web | 16.0.28621.142 | Požadováno
Component.Microsoft.VisualStudio.LiveShare | Live Share | 1.0.826 | Doporučené
Component.Microsoft.VisualStudio.Web.AzureFunctions | Nástroje Azure WebJobs | 16.0.28714.129 | Doporučené
Microsoft.Net.Core.Component.SDK.2.1 | Modul runtime .NET Core 2,1 LTS | 16.3.29318.74 | Doporučené
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics tools | 16.2.28917.182 | Doporučené
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Azure – nástroje pro tvorbu | 16.0.28625.61 | Doporučené
Microsoft.VisualStudio.Component.Azure.ClientLibs | Knihovny Azure pro .NET | 16.0.28315.86 | Doporučené
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Emulátor výpočtů v Azure | 16.1.28810.153 | Doporučené
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Emulátor úložiště Azure | 16.3.29230.54 | Doporučené
Microsoft.VisualStudio.Component.CloudExplorer | Průzkumník cloudu | 16.0.28625.61 | Doporučené
Microsoft.VisualStudio.Component.Debugger.Snapshot | Snapshot Debugger | 16.2.29003.222 | Doporučené
Microsoft.VisualStudio.Component.Debugger.TimeTravel | Čas cestovního ladicího programu | 16.0.28714.129 | Doporučené
Microsoft.VisualStudio.Component.DiagnosticTools | Nástroje pro profilaci .NET | 16.3.29207.166 | Doporučené
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | 16.1.28829.92 | Doporučené
Microsoft.VisualStudio.Component.LiveUnitTesting | Live Unit Testing | 16.1.28811.260 | Doporučené
Microsoft.VisualStudio.Component.Web | Nástroje pro vývoj pro ASP.NET a web | 16.0.28517.75 | Doporučené
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 16.0.28517.75 | Doporučené
Microsoft.VisualStudio.ComponentGroup.AzureFunctions | Nástroje Azure WebJobs | 16.0.28621.142 | Doporučené
Microsoft.VisualStudio.ComponentGroup.Web.CloudTools | Cloudové nástroje pro vývoj pro web | 16.2.29003.222 | Doporučené
Microsoft. VisualStudio. Component. Windows10SDK. 18362 | Windows 10 SDK (10.0.18362.0) | 16.1.28829.92 | volitelná,
Microsoft.VisualStudio.ComponentGroup.IISDevelopment | Podpora služby IIS při vývoji | 16.0.28315.86 | volitelná,
Microsoft. VisualStudio. Component. MSIX. balení | Nástroje pro vytváření balíčků MSIX | 16.3.29230.54 | volitelná,

## <a name="mobile-development-with-net"></a>Vývoj mobilních aplikací pomocí .NET

**ÚČET** Microsoft.VisualStudio.Workload.NetCrossPlat

**Popis:** Vytvářejte aplikace pro různé platformy pro iOS, Android nebo Windows pomocí Xamarin.

### <a name="components-included-by-this-workload"></a>Pomocí této úlohy zahrnuté komponenty

ID součásti | Název | Version | Typ závislosti
--- | --- | --- | ---
Component.OpenJDK | OpenJDK (distribuce Microsoft) | 16.1.28811.260 | Požadováno
Component.Xamarin | Xamarin | 16.3.29207.166 | Požadováno
Component.Xamarin.RemotedSimulator | Vzdálený simulátor Xamarin | 16.0.28315.86 | Požadováno
Microsoft.Component.MSBuild | MSBuild | 16.0.28517.75 | Požadováno
Microsoft.Net.Component.4.6.1.TargetingPack | Rozhraní .NET framework 4.6.1 targeting pack | 16.0.28517.75 | Požadováno
Microsoft.Net.Component.4.7.2.TargetingPack | Rozhraní .NET framework 4.7.2 targeting pack | 16.0.28517.75 | Požadováno
Microsoft. NET. Component. 4.8. SDK | .NET Framework 4,8 SDK | 16.3.29230.54 | Požadováno
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Vývojové nástroje .NET framework 4.7.2 | 16.3.29207.166 | Požadováno
Microsoft. NetCore. Component. DevelopmentTools | Vývojové nástroje .NET Core | 16.3.29207.166 | Požadováno
Microsoft. NetCore. Component. SDK | Sada .NET Core 3,0 SDK | 16.3.29318.74 | Požadováno
Microsoft.VisualStudio.Component.FSharp | F#podpora jazyků | 16.0.28315.86 | Požadováno
Microsoft. VisualStudio. Component. IntelliCode | IntelliCode | 0.1 | Požadováno
Microsoft.VisualStudio.Component.Merq | Společné interní nástroje Xamarin | 16.2.29012.281 | Požadováno
Microsoft.VisualStudio.Component.MonoDebugger | Ladicí program mono | 16.0.28517.75 | Požadováno
Microsoft.VisualStudio.Component.NuGet | Správce balíčků NuGet | 16.1.28829.92 | Požadováno
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilátory C# a Visual Basic Roslyn | 16.0.28714.129 | Požadováno
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# a Visual Basic | 16.1.28829.92 | Požadováno
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions.TemplateEngine | Modul šablon ASP.NET | 16.0.28315.86 | Požadováno
Komponenta. Android. SDK28 | Instalace Android SDK (úroveň rozhraní API 28) | 16.2.29003.222 | Doporučené

## <a name="aspnet-and-web-development"></a>Vývoj pro ASP.NET a web

**ÚČET** Microsoft.VisualStudio.Workload.NetWeb

**Popis:** Vytvářejte webové aplikace pomocí ASP.NET Core, ASP.NET, HTML/JavaScript a kontejnerů včetně podpory Docker.

### <a name="components-included-by-this-workload"></a>Pomocí této úlohy zahrnuté komponenty

ID součásti | Název | Version | Typ závislosti
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Jazykové služby Razor | 16.0.28714.129 | Požadováno
Component.Microsoft.Web.LibraryManager | Správce knihovny | 16.0.28315.86 | Požadováno
Microsoft.Component.MSBuild | MSBuild | 16.0.28517.75 | Požadováno
Microsoft.Net.Component.4.5.2.TargetingPack | Rozhraní .NET framework 4.5.2 targeting pack | 16.0.28517.75 | Požadováno
Microsoft.Net.Component.4.5.TargetingPack | .NET framework 4.5 targeting pack | 16.0.28517.75 | Požadováno
Microsoft.Net.Component.4.6.1.TargetingPack | Rozhraní .NET framework 4.6.1 targeting pack | 16.0.28517.75 | Požadováno
Microsoft.Net.Component.4.7.2.TargetingPack | Rozhraní .NET framework 4.7.2 targeting pack | 16.0.28517.75 | Požadováno
Microsoft. NET. Component. 4.8. SDK | .NET Framework 4,8 SDK | 16.3.29230.54 | Požadováno
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Vývojové nástroje .NET framework 4.7.2 | 16.3.29207.166 | Požadováno
Microsoft. NetCore. Component. DevelopmentTools | Vývojové nástroje .NET Core | 16.3.29207.166 | Požadováno
Microsoft. NetCore. Component. SDK | Sada .NET Core 3,0 SDK | 16.3.29318.74 | Požadováno
Microsoft. NetCore. Component. Web | Vývojové nástroje .NET Core | 16.3.29207.166 | Požadováno
Microsoft.VisualStudio.Component.Common.Azure.Tools | Nástroje pro připojení a publikování | 16.3.29311.71 | Požadováno
Microsoft.VisualStudio.Component.DockerTools | Kontejnerové vývojové nástroje | 16.3.29103.31 | Požadováno
Microsoft.VisualStudio.Component.FSharp | F#podpora jazyků | 16.0.28315.86 | Požadováno
Microsoft.VisualStudio.Component.FSharp.WebTemplates | F#podpora jazyků pro webové projekty | 16.3.29207.166 | Požadováno
Microsoft.VisualStudio.Component.IISExpress | Služba IIS Express  | 16.0.28315.86 | Požadováno
Microsoft. VisualStudio. Component. IntelliCode | IntelliCode | 0.1 | Požadováno
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostika jazyka JavaScript | 16.0.28517.75 | Požadováno
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Podpora jazyků JavaScript a TypeScript | 16.3.29207.166 | Požadováno
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Základní spravovaný úloze vývoje desktopových aplikací | 16.3.29230.54 | Požadováno
Microsoft.VisualStudio.Component.MSODBC.SQL | SQL Server ovladač ODBC | 16.0.28625.61 | Požadováno
Microsoft.VisualStudio.Component.MSSQL.CMDLnUtils | Nástroje příkazového řádku SQL serveru | 16.0.28707.177 | Požadováno
Microsoft.VisualStudio.Component.NuGet | Správce balíčků NuGet | 16.1.28829.92 | Požadováno
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilátory C# a Visual Basic Roslyn | 16.0.28714.129 | Požadováno
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# a Visual Basic | 16.1.28829.92 | Požadováno
Microsoft.VisualStudio.Component.SQL.ADAL | SQL ADAL runtime | 16.0.28517.75 | Požadováno
Microsoft.VisualStudio.Component.SQL.CLR | Datové typy CLR pro SQL Server | 16.0.28315.86 | Požadováno
Microsoft.VisualStudio.Component.SQL.DataSources | Zdroje dat pro podporu SQL serveru | 16.0.28315.86 | Požadováno
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 16.0.28625.61 | Požadováno
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 16.3.29207.166 | Požadováno
Microsoft.VisualStudio.Component.TextTemplating | Transformace textové šablony | 16.0.28625.61 | Požadováno
Microsoft. VisualStudio. Component. TypeScript. 3.6 | Sada TypeScript 3,6 SDK | 16.0.29207.166 | Požadováno
Microsoft.VisualStudio.Component.Web | Nástroje pro vývoj pro ASP.NET a web | 16.0.28517.75 | Požadováno
Microsoft.VisualStudio.ComponentGroup.Web | Vývoj pro ASP.NET a webové nástroje – požadavky | 16.3.29230.54 | Požadováno
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Vývoj pro ASP.NET a web | 16.0.28621.142 | Požadováno
Component.Microsoft.VisualStudio.LiveShare | Live Share | 1.0.826 | Doporučené
Component.Microsoft.VisualStudio.Web.AzureFunctions | Nástroje Azure WebJobs | 16.0.28714.129 | Doporučené
Microsoft.Net.Component.4.5.1.TargetingPack | Rozhraní .NET framework 4.5.1 targeting pack | 16.0.28517.75 | Doporučené
Microsoft.Net.Component.4.6.TargetingPack | .NET framework 4.6 targeting pack | 16.0.28517.75 | Doporučené
Microsoft.Net.Component.4.TargetingPack | .NET framework 4 targeting pack | 16.0.28517.75 | Doporučené
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Vývojové nástroje .NET framework 4 – 4.6 | 16.0.28516.191 | Doporučené
Microsoft.Net.Core.Component.SDK.2.1 | Modul runtime .NET Core 2,1 LTS | 16.3.29318.74 | Doporučené
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics tools | 16.2.28917.182 | Doporučené
Microsoft.VisualStudio.Component.AspNet45 | Rozšířené funkce ASP.NET | 16.0.28315.86 | Doporučené
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Azure – nástroje pro tvorbu | 16.0.28625.61 | Doporučené
Microsoft.VisualStudio.Component.Azure.ClientLibs | Knihovny Azure pro .NET | 16.0.28315.86 | Doporučené
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Emulátor výpočtů v Azure | 16.1.28810.153 | Doporučené
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Emulátor úložiště Azure | 16.3.29230.54 | Doporučené
Microsoft.VisualStudio.Component.CloudExplorer | Průzkumník cloudu | 16.0.28625.61 | Doporučené
Microsoft.VisualStudio.Component.Debugger.Snapshot | Snapshot Debugger | 16.2.29003.222 | Doporučené
Microsoft.VisualStudio.Component.Debugger.TimeTravel | Čas cestovního ladicího programu | 16.0.28714.129 | Doporučené
Microsoft.VisualStudio.Component.DiagnosticTools | Nástroje pro profilaci .NET | 16.3.29207.166 | Doporučené
Microsoft.VisualStudio.Component.EntityFramework | Entity Framework 6 tools | 16.0.28315.86 | Doporučené
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | 16.1.28829.92 | Doporučené
Microsoft.VisualStudio.Component.LiveUnitTesting | Live Unit Testing | 16.1.28811.260 | Doporučené
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 16.0.28517.75 | Doporučené
Microsoft.VisualStudio.ComponentGroup.AzureFunctions | Nástroje Azure WebJobs | 16.0.28621.142 | Doporučené
Microsoft.VisualStudio.ComponentGroup.Web.CloudTools | Cloudové nástroje pro vývoj pro web | 16.2.29003.222 | Doporučené
Microsoft.Net.Component.4.6.2.TargetingPack | Rozhraní .NET framework 4.6.2 targeting pack | 16.0.28517.75 | volitelná,
Microsoft.Net.Component.4.7.1.TargetingPack | Rozhraní .NET framework 4.7.1 targeting pack | 16.0.28517.75 | volitelná,
Microsoft.Net.Component.4.7.TargetingPack | .NET framework 4.7 targeting pack | 16.0.28517.75 | volitelná,
Microsoft.Net. Component. 4.8. TargetingPack | Sada targeting pack .NET Framework 4,8 | 16.3.29230.54 | volitelná,
Microsoft.Net.ComponentGroup.4.6.1.DeveloperTools | Vývojové nástroje .NET framework 4.6.1 | 16.3.29207.166 | volitelná,
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | Vývojové nástroje .NET framework 4.6.2 | 16.3.29207.166 | volitelná,
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | Vývojové nástroje .NET framework 4.7.1 | 16.3.29207.166 | volitelná,
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | Vývojové nástroje .NET framework 4.7 | 16.3.29207.166 | volitelná,
Microsoft.Net. Component. 4,8. DeveloperTools | Vývojové nástroje .NET Framework 4,8 | 16.3.29230.54 | volitelná,
Microsoft.VisualStudio.Component.ClassDesigner | Návrhář tříd | 16.0.28528.71 | volitelná,
Microsoft.VisualStudio.Component.CodeClone | Klonování kódu | 16.3.29311.71 | volitelná,
Microsoft.VisualStudio.Component.CodeMap | Mapa kódu | 16.0.28625.61 | volitelná,
Microsoft.VisualStudio.Component.DependencyValidation.Enterprise | Živé ověření závislosti | 16.0.28625.61 | volitelná,
Microsoft.VisualStudio.Component.GraphDocument | DGML editor | 16.0.28625.61 | volitelná,
Microsoft.VisualStudio.Component.TestTools.WebLoadTest | Výkonnosti webů a zátěžové testování nástroje | 16.0.28625.61 | volitelná,
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | 16.0.28625.61 | volitelná,
Microsoft.VisualStudio.ComponentGroup.AdditionalWebProjectTemplates | Další šablony projektů (předchozí verze) | 16.0.28621.142 | volitelná,
Microsoft.VisualStudio.ComponentGroup.ArchitectureTools.Managed | Architektury a analytické nástroje | 16.3.29318.136 | volitelná,
Microsoft.VisualStudio.ComponentGroup.IISDevelopment | Podpora služby IIS při vývoji | 16.0.28315.86 | volitelná,

## <a name="nodejs-development"></a>Vývoj v Node.js

**ÚČET** Microsoft.VisualStudio.Workload.Node

**Popis:** Sestavujte škálovatelné síťové aplikace pomocí Node. js, což je asynchronní běhové prostředí JavaScriptu řízené událostmi. 

### <a name="components-included-by-this-workload"></a>Pomocí této úlohy zahrnuté komponenty

ID součásti | Název | Version | Typ závislosti
--- | --- | --- | ---
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostika jazyka JavaScript | 16.0.28517.75 | Požadováno
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Podpora jazyků JavaScript a TypeScript | 16.3.29207.166 | Požadováno
Microsoft.VisualStudio.Component.Node.Tools | Vývojové nástroje Node. js | 16.0.28625.61 | Požadováno
Microsoft. VisualStudio. Component. TypeScript. 3.6 | Sada TypeScript 3,6 SDK | 16.0.29207.166 | Požadováno
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Vývoj pro ASP.NET a web | 16.0.28621.142 | Požadováno
Component.Microsoft.VisualStudio.LiveShare | Live Share | 1.0.826 | Doporučené
Microsoft. VisualStudio. Component. IntelliCode | IntelliCode | 0.1 | Doporučené
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 16.0.28517.75 | Doporučené
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics tools | 16.2.28917.182 | volitelná,
Microsoft.VisualStudio.Component.Common.Azure.Tools | Nástroje pro připojení a publikování | 16.3.29311.71 | volitelná,
Microsoft.VisualStudio.Component.VC.CoreIde | C++základní funkce | 16.0.28625.61 | volitelná,
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | Nástroje MSVC V142-VS C++ 2019 x64/x86 Build Tools (v 14.23) | 16.3.29230.54 | volitelná,

## <a name="officesharepoint-development"></a>Vývoj pro Office/SharePoint

**ÚČET** Microsoft.VisualStudio.Workload.Office

**Popis:** Vytvářejte doplňky pro Office a SharePoint, řešení pro SharePoint a doplňky VSTO pomocí C#, VB a JavaScriptu.

### <a name="components-included-by-this-workload"></a>Pomocí této úlohy zahrnuté komponenty

ID součásti | Název | Version | Typ závislosti
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Jazykové služby Razor | 16.0.28714.129 | Požadováno
Component.Microsoft.Web.LibraryManager | Správce knihovny | 16.0.28315.86 | Požadováno
Microsoft.Component.MSBuild | MSBuild | 16.0.28517.75 | Požadováno
Microsoft.Net.Component.4.5.2.TargetingPack | Rozhraní .NET framework 4.5.2 targeting pack | 16.0.28517.75 | Požadováno
Microsoft.Net.Component.4.5.TargetingPack | .NET framework 4.5 targeting pack | 16.0.28517.75 | Požadováno
Microsoft.Net.Component.4.6.1.TargetingPack | Rozhraní .NET framework 4.6.1 targeting pack | 16.0.28517.75 | Požadováno
Microsoft.Net.Component.4.7.2.TargetingPack | Rozhraní .NET framework 4.7.2 targeting pack | 16.0.28517.75 | Požadováno
Microsoft. NET. Component. 4.8. SDK | .NET Framework 4,8 SDK | 16.3.29230.54 | Požadováno
Microsoft.Net.Component.4.TargetingPack | .NET framework 4 targeting pack | 16.0.28517.75 | Požadováno
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Vývojové nástroje .NET framework 4.7.2 | 16.3.29207.166 | Požadováno
Microsoft. NetCore. Component. SDK | Sada .NET Core 3,0 SDK | 16.3.29318.74 | Požadováno
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics tools | 16.2.28917.182 | Požadováno
Microsoft.VisualStudio.Component.Common.Azure.Tools | Nástroje pro připojení a publikování | 16.3.29311.71 | Požadováno
Microsoft.VisualStudio.Component.DockerTools | Kontejnerové vývojové nástroje | 16.3.29103.31 | Požadováno
Microsoft.VisualStudio.Component.IISExpress | Služba IIS Express  | 16.0.28315.86 | Požadováno
Microsoft. VisualStudio. Component. IntelliCode | IntelliCode | 0.1 | Požadováno
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostika jazyka JavaScript | 16.0.28517.75 | Požadováno
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Podpora jazyků JavaScript a TypeScript | 16.3.29207.166 | Požadováno
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Základní spravovaný úloze vývoje desktopových aplikací | 16.3.29230.54 | Požadováno
Microsoft.VisualStudio.Component.ManagedDesktop.Prerequisites | Nástroje pro vývoj desktopových aplikací .NET | 16.3.29230.54 | Požadováno
Microsoft.VisualStudio.Component.MSODBC.SQL | SQL Server ovladač ODBC | 16.0.28625.61 | Požadováno
Microsoft.VisualStudio.Component.MSSQL.CMDLnUtils | Nástroje příkazového řádku SQL serveru | 16.0.28707.177 | Požadováno
Microsoft.VisualStudio.Component.NuGet | Správce balíčků NuGet | 16.1.28829.92 | Požadováno
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilátory C# a Visual Basic Roslyn | 16.0.28714.129 | Požadováno
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# a Visual Basic | 16.1.28829.92 | Požadováno
Microsoft.VisualStudio.Component.Sharepoint.Tools | Office Developer Tools for Visual Studio | 16.3.29311.71 | Požadováno
Microsoft.VisualStudio.Component.SQL.ADAL | SQL ADAL runtime | 16.0.28517.75 | Požadováno
Microsoft.VisualStudio.Component.SQL.CLR | Datové typy CLR pro SQL Server | 16.0.28315.86 | Požadováno
Microsoft.VisualStudio.Component.SQL.DataSources | Zdroje dat pro podporu SQL serveru | 16.0.28315.86 | Požadováno
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 16.0.28625.61 | Požadováno
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 16.3.29207.166 | Požadováno
Microsoft.VisualStudio.Component.TextTemplating | Transformace textové šablony | 16.0.28625.61 | Požadováno
Microsoft. VisualStudio. Component. TypeScript. 3.6 | Sada TypeScript 3,6 SDK | 16.0.29207.166 | Požadováno
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | 16.0.28625.61 | Požadováno
Microsoft.VisualStudio.Component.Web | Nástroje pro vývoj pro ASP.NET a web | 16.0.28517.75 | Požadováno
Microsoft.VisualStudio.Component.Workflow | Windows Workflow Foundation | 16.0.28315.86 | Požadováno
Microsoft.VisualStudio.ComponentGroup.Web | Vývoj pro ASP.NET a webové nástroje – požadavky | 16.3.29230.54 | Požadováno
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Vývoj pro ASP.NET a web | 16.0.28621.142 | Požadováno
Microsoft.VisualStudio.Component.TeamOffice | Visual Studio Tools for Office (VSTO) | 16.3.29311.71 | Doporučené
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 16.0.28517.75 | Doporučené
Microsoft.Net.Component.4.6.2.TargetingPack | Rozhraní .NET framework 4.6.2 targeting pack | 16.0.28517.75 | volitelná,
Microsoft.Net.Component.4.7.1.TargetingPack | Rozhraní .NET framework 4.7.1 targeting pack | 16.0.28517.75 | volitelná,
Microsoft.Net.Component.4.7.TargetingPack | .NET framework 4.7 targeting pack | 16.0.28517.75 | volitelná,
Microsoft.Net. Component. 4.8. TargetingPack | Sada targeting pack .NET Framework 4,8 | 16.3.29230.54 | volitelná,
Microsoft.Net.ComponentGroup.4.6.1.DeveloperTools | Vývojové nástroje .NET framework 4.6.1 | 16.3.29207.166 | volitelná,
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | Vývojové nástroje .NET framework 4.6.2 | 16.3.29207.166 | volitelná,
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | Vývojové nástroje .NET framework 4.7.1 | 16.3.29207.166 | volitelná,
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | Vývojové nástroje .NET framework 4.7 | 16.3.29207.166 | volitelná,
Microsoft.Net. Component. 4,8. DeveloperTools | Vývojové nástroje .NET Framework 4,8 | 16.3.29230.54 | volitelná,
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | 16.1.28829.92 | volitelná,
Microsoft.VisualStudio.ComponentGroup.Sharepoint.WIF | Windows Identity Foundation 3,5 | 16.0.28621.142 | volitelná,

## <a name="python-development"></a>Vývoj v jazyce Python

**ÚČET** Microsoft.VisualStudio.Workload.Python

**Popis:** Úpravy, ladění, interaktivní vývoj a Správa zdrojového kódu pro Python.

### <a name="components-included-by-this-workload"></a>Pomocí této úlohy zahrnuté komponenty

ID součásti | Název | Version | Typ závislosti
--- | --- | --- | ---
Microsoft.Component.PythonTools | Podpora jazyka Python | 16.0.28625.61 | Požadováno
Component.CPython3.x64 | Python 3 64 – bit (3.7.4) | 3.7.4 | Doporučené
Component.Microsoft.VisualStudio.LiveShare | Live Share | 1.0.826 | Doporučené
Microsoft.Component.PythonTools.Minicondax64 | Python miniconda | 16.2.29003.222 | Doporučené
Microsoft.Component.PythonTools.Web | Podpora webů v Pythonu | 16.0.28517.75 | Doporučené
Microsoft.VisualStudio.Component.Common.Azure.Tools | Nástroje pro připojení a publikování | 16.3.29311.71 | Doporučené
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Podpora jazyků JavaScript a TypeScript | 16.3.29207.166 | Doporučené
Microsoft. VisualStudio. Component. TypeScript. 3.6 | Sada TypeScript 3,6 SDK | 16.0.29207.166 | Doporučené
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 16.0.28517.75 | Doporučené
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Vývoj pro ASP.NET a web | 16.0.28621.142 | Doporučené
Component.CPython2.x64 | Python 2 64 – bit (2.7.16) | 2.7.16 | volitelná,
Component.CPython2.x86 | Python 2 32 – bit (2.7.16) | 2.7.16 | volitelná,
Component.CPython3.x86 | Python 3 32 – bit (3.7.4) | 3.7.4 | volitelná,
Component.Microsoft.VisualStudio.RazorExtension | Jazykové služby Razor | 16.0.28714.129 | volitelná,
Component.Microsoft.Web.LibraryManager | Správce knihovny | 16.0.28315.86 | volitelná,
Microsoft.Component.MSBuild | MSBuild | 16.0.28517.75 | volitelná,
Microsoft.ComponentGroup.PythonTools.NativeDevelopment | Nástroje Pythonu pro nativní vývoj | 16.2.29020.229 | volitelná,
Microsoft.Net.Component.4.5.2.TargetingPack | Rozhraní .NET framework 4.5.2 targeting pack | 16.0.28517.75 | volitelná,
Microsoft.Net.Component.4.5.TargetingPack | .NET framework 4.5 targeting pack | 16.0.28517.75 | volitelná,
Microsoft.Net.Component.4.7.2.TargetingPack | Rozhraní .NET framework 4.7.2 targeting pack | 16.0.28517.75 | volitelná,
Microsoft. NET. Component. 4.8. SDK | .NET Framework 4,8 SDK | 16.3.29230.54 | volitelná,
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Vývojové nástroje .NET framework 4.7.2 | 16.3.29207.166 | volitelná,
Microsoft. NetCore. Component. SDK | Sada .NET Core 3,0 SDK | 16.3.29318.74 | volitelná,
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Azure – nástroje pro tvorbu | 16.0.28625.61 | volitelná,
Microsoft.VisualStudio.Component.Azure.ClientLibs | Knihovny Azure pro .NET | 16.0.28315.86 | volitelná,
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Emulátor výpočtů v Azure | 16.1.28810.153 | volitelná,
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Emulátor úložiště Azure | 16.3.29230.54 | volitelná,
Microsoft.VisualStudio.Component.Azure.Waverton | Základní nástroje pro Azure Cloud Services | 16.3.29311.71 | volitelná,
Microsoft.VisualStudio.Component.Azure.Waverton.BuildTools | Nástroje pro vytváření Azure Cloud Services | 16.3.29207.166 | volitelná,
Microsoft.VisualStudio.Component.DockerTools | Kontejnerové vývojové nástroje | 16.3.29103.31 | volitelná,
Microsoft.VisualStudio.Component.Graphics.Tools | Ladicí program grafiky a profiler GPU pro DirectX | 16.0.28625.61 | volitelná,
Microsoft.VisualStudio.Component.IISExpress | Služba IIS Express  | 16.0.28315.86 | volitelná,
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostika jazyka JavaScript | 16.0.28517.75 | volitelná,
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Základní spravovaný úloze vývoje desktopových aplikací | 16.3.29230.54 | volitelná,
Microsoft.VisualStudio.Component.MSODBC.SQL | SQL Server ovladač ODBC | 16.0.28625.61 | volitelná,
Microsoft.VisualStudio.Component.MSSQL.CMDLnUtils | Nástroje příkazového řádku SQL serveru | 16.0.28707.177 | volitelná,
Microsoft.VisualStudio.Component.NuGet | Správce balíčků NuGet | 16.1.28829.92 | volitelná,
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilátory C# a Visual Basic Roslyn | 16.0.28714.129 | volitelná,
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# a Visual Basic | 16.1.28829.92 | volitelná,
Microsoft.VisualStudio.Component.SQL.ADAL | SQL ADAL runtime | 16.0.28517.75 | volitelná,
Microsoft.VisualStudio.Component.SQL.CLR | Datové typy CLR pro SQL Server | 16.0.28315.86 | volitelná,
Microsoft.VisualStudio.Component.SQL.DataSources | Zdroje dat pro podporu SQL serveru | 16.0.28315.86 | volitelná,
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 16.0.28625.61 | volitelná,
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 16.3.29207.166 | volitelná,
Microsoft.VisualStudio.Component.TextTemplating | Transformace textové šablony | 16.0.28625.61 | volitelná,
Microsoft.VisualStudio.Component.VC.CoreIde | C++základní funkce | 16.0.28625.61 | volitelná,
Microsoft.VisualStudio.Component.VC.DiagnosticTools | Nástroje pro profilaci v C++ | 16.0.28625.61 | volitelná,
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | Nástroje MSVC V142-VS C++ 2019 x64/x86 Build Tools (v 14.23) | 16.3.29230.54 | volitelná,
Microsoft.VisualStudio.Component.Web | Nástroje pro vývoj pro ASP.NET a web | 16.0.28517.75 | volitelná,
Microsoft.VisualStudio.Component.Windows10SDK | Windows Universal C Runtime | 16.3.29311.71 | volitelná,
Microsoft. VisualStudio. Component. Windows10SDK. 18362 | Windows 10 SDK (10.0.18362.0) | 16.1.28829.92 | volitelná,
Microsoft.VisualStudio.ComponentGroup.Web | Vývoj pro ASP.NET a webové nástroje – požadavky | 16.3.29230.54 | volitelná,

## <a name="universal-windows-platform-development"></a>Vývoj pro univerzální platformu Windows

**ÚČET** Microsoft. VisualStudio. úlohu. Universal

**Popis:** Vytvářejte aplikace pro Univerzální platforma Windows pomocí C#, vb nebo volitelně. C++

### <a name="components-included-by-this-workload"></a>Pomocí této úlohy zahrnuté komponenty

ID součásti | Název | Version | Typ závislosti
--- | --- | --- | ---
Microsoft.Component.NetFX.Native | .NET Native | 16.0.28315.86 | Požadováno
Microsoft.ComponentGroup.Blend | Blend for Visual Studio | 16.0.28315.86 | Požadováno
Microsoft.Net.Component.4.5.TargetingPack | .NET framework 4.5 targeting pack | 16.0.28517.75 | Požadováno
Microsoft. NetCore. Component. SDK | Sada .NET Core 3,0 SDK | 16.3.29318.74 | Požadováno
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics tools | 16.2.28917.182 | Požadováno
Microsoft.VisualStudio.Component.DiagnosticTools | Nástroje pro profilaci .NET | 16.3.29207.166 | Požadováno
Microsoft.VisualStudio.Component.Graphics | Editory obrázků a 3D modelu | 16.0.28517.75 | Požadováno
Microsoft. VisualStudio. Component. IntelliCode | IntelliCode | 0.1 | Požadováno
Microsoft.VisualStudio.Component.NuGet | Správce balíčků NuGet | 16.1.28829.92 | Požadováno
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilátory C# a Visual Basic Roslyn | 16.0.28714.129 | Požadováno
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# a Visual Basic | 16.1.28829.92 | Požadováno
Microsoft.VisualStudio.Component.SQL.CLR | Datové typy CLR pro SQL Server | 16.0.28315.86 | Požadováno
Microsoft. VisualStudio. Component. Windows10SDK. 18362 | Windows 10 SDK (10.0.18362.0) | 16.1.28829.92 | Požadováno
Microsoft. VisualStudio. Component. MSIX. balení | Nástroje pro vytváření balíčků MSIX | 16.3.29230.54 | Požadováno
Microsoft.VisualStudio.ComponentGroup.UWP.NetCoreAndStandard | .NET native a .NET Standard | 16.3.29102.218 | Požadováno
Microsoft.VisualStudio.ComponentGroup.UWP.Support | Nástroje pro univerzální platformu Windows | 16.3.29311.71 | Požadováno
Microsoft.VisualStudio.ComponentGroup.UWP.Xamarin | Nástroje pro univerzální platformu Windows pro Xamarin | 16.2.29020.229 | Požadováno
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | 16.1.28829.92 | Doporučené
Microsoft.Component.MSBuild | MSBuild | 16.0.28517.75 | volitelná,
Microsoft. NET. Component. 4.8. SDK | .NET Framework 4,8 SDK | 16.3.29230.54 | volitelná,
Microsoft.VisualStudio.Component.ClassDesigner | Návrhář tříd | 16.0.28528.71 | volitelná,
Microsoft.VisualStudio.Component.CodeClone | Klonování kódu | 16.3.29311.71 | volitelná,
Microsoft.VisualStudio.Component.CodeMap | Mapa kódu | 16.0.28625.61 | volitelná,
Microsoft.VisualStudio.Component.DependencyValidation.Enterprise | Živé ověření závislosti | 16.0.28625.61 | volitelná,
Microsoft.VisualStudio.Component.GraphDocument | DGML editor | 16.0.28625.61 | volitelná,
Microsoft.VisualStudio.Component.Graphics.Tools | Ladicí program grafiky a profiler GPU pro DirectX | 16.0.28625.61 | volitelná,
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 16.0.28625.61 | volitelná,
Microsoft.VisualStudio.Component.TextTemplating | Transformace textové šablony | 16.0.28625.61 | volitelná,
Microsoft.VisualStudio.Component.UWP.VC.ARM64 | C++Podpora Univerzální platforma Windows pro V142 Build Tools (ARM64) | 16.3.29207.166 | volitelná,
Microsoft.VisualStudio.Component.VC.CoreIde | C++základní funkce | 16.0.28625.61 | volitelná,
Microsoft.VisualStudio.Component.VC.Redist.14.Latest | C++2019 Distribuovatelný aktualizace | 16.0.28625.61 | volitelná,
Microsoft.VisualStudio.Component.VC.Tools.ARM | MSVC V142-VS 2019 C++ nástroje pro sestavení ARM (v 14.23) | 16.3.29230.54 | volitelná,
Microsoft.VisualStudio.Component.VC.Tools.ARM64 | MSVC V142-VS 2019 C++ ARM64 Build Tools (v 14.23) | 16.3.29230.54 | volitelná,
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | Nástroje MSVC V142-VS C++ 2019 x64/x86 Build Tools (v 14.23) | 16.3.29230.54 | volitelná,
Microsoft.VisualStudio.Component.VC.v141.ARM | MSVC v141-VS 2017 C++ nástroje pro sestavení ARM (v 14.16) | 16.2.29003.222 | volitelná,
Microsoft.VisualStudio.Component.VC.v141.ARM64 | MSVC v141-VS 2017 C++ ARM64 Build Tools (v 14.16) | 16.1.28829.92 | volitelná,
Microsoft.VisualStudio.Component.VC.v141.x86.x64 | Nástroje MSVC v141-VS C++ 2017 x64/x86 Build Tools (v 14.16) | 16.1.28829.92 | volitelná,
Microsoft.VisualStudio.Component.Windows10SDK.16299 | Windows 10 SDK (10.0.16299.0) | 16.0.28517.75 | volitelná,
Microsoft.VisualStudio.Component.Windows10SDK.17134 | Windows 10 SDK (10.0.17134.0) | 16.0.28517.75 | volitelná,
Microsoft.VisualStudio.Component.Windows10SDK.17763 | Windows 10 SDK (10.0.17763.0) | 16.0.28517.75 | volitelná,
Microsoft.VisualStudio.Component.Windows10SDK.IpOverUsb | Připojení zařízení USB | 16.2.29020.229 | volitelná,
Microsoft.VisualStudio.ComponentGroup.ArchitectureTools.Managed | Architektury a analytické nástroje | 16.3.29318.136 | volitelná,
Microsoft.VisualStudio.ComponentGroup.ArchitectureTools.Native | Nástroje pro architekturu pro C++ | 16.0.28621.142 | volitelná,
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Core | C++základní desktopové funkce | 16.2.29012.281 | volitelná,
Microsoft.VisualStudio.ComponentGroup.UWP.VC | C++(v142) Nástroje Univerzální platforma Windows | 16.3.29207.166 | volitelná,
Microsoft.VisualStudio.ComponentGroup.UWP.VC.v141 | C++v141 Nástroje Univerzální platforma Windows | 16.1.28810.153 | volitelná,

## <a name="visual-studio-extension-development"></a>Vývoj rozšíření sady Visual Studio

**ÚČET** Microsoft.VisualStudio.Workload.VisualStudioExtension

**Popis:** Vytvořte doplňky a rozšíření pro Visual Studio, včetně nových příkazů, analyzátorů kódu a oken nástrojů.

### <a name="components-included-by-this-workload"></a>Pomocí této úlohy zahrnuté komponenty

ID součásti | Název | Version | Typ závislosti
--- | --- | --- | ---
Microsoft.Component.MSBuild | MSBuild | 16.0.28517.75 | Požadováno
Microsoft.Net.Component.4.6.TargetingPack | .NET framework 4.6 targeting pack | 16.0.28517.75 | Požadováno
Microsoft.Net.Component.4.7.2.TargetingPack | Rozhraní .NET framework 4.7.2 targeting pack | 16.0.28517.75 | Požadováno
Microsoft. NET. Component. 4.8. SDK | .NET Framework 4,8 SDK | 16.3.29230.54 | Požadováno
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Vývojové nástroje .NET framework 4.7.2 | 16.3.29207.166 | Požadováno
Microsoft. VisualStudio. Component. IntelliCode | IntelliCode | 0.1 | Požadováno
Microsoft.VisualStudio.Component.NuGet | Správce balíčků NuGet | 16.1.28829.92 | Požadováno
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilátory C# a Visual Basic Roslyn | 16.0.28714.129 | Požadováno
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# a Visual Basic | 16.1.28829.92 | Požadováno
Microsoft.VisualStudio.Component.VSSDK | Visual Studio SDK | 16.0.28315.86 | Požadováno
Microsoft.VisualStudio.ComponentGroup.VisualStudioExtension.Prerequisites | Visual Studio předpoklady pro vývoj rozšíření | 16.3.29230.54 | Požadováno
Microsoft.VisualStudio.Component.DiagnosticTools | Nástroje pro profilaci .NET | 16.3.29207.166 | Doporučené
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | 16.1.28829.92 | Doporučené
Microsoft.VisualStudio.Component.TextTemplating | Transformace textové šablony | 16.0.28625.61 | Doporučené
Microsoft.Component.CodeAnalysis.SDK | Sada .NET Compiler Platform SDK | 16.2.29003.222 | volitelná,
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics tools | 16.2.28917.182 | volitelná,
Microsoft.VisualStudio.Component.DslTools | Sada Modeling SDK | 16.0.28315.86 | volitelná,

## <a name="unaffiliated-components"></a>Nespojená komponenty

Toto jsou komponenty, které nejsou zahrnuty u jakékoli úlohy, ale může vybrat jako jednotlivých komponent.

ID součásti | Název | Version
--- | --- | ---
Component.GitHub.VisualStudio | Rozšíření GitHub pro Visual Studio | 2.5.9.5485
Component.Xamarin.Inspector | Xamarin Inspector | 16.0.28315.86
Component.Xamarin.Profiler | Xamarin Profiler | 16.0.28315.86
Komponenta. Xamarin. sešity | Sešity ke Xamarinu | 16.0.28315.86
Microsoft.Component.ClickOnce | Publikování ClickOnce | 16.3.29311.71
Microsoft.Component.HelpViewer | Aplikaci Help Viewer | 16.0.28625.61
Microsoft.Net.Component.4.6.1.SDK | Rozhraní .NET framework 4.6.1 SDK | 16.3.29230.54
Microsoft.Net.Component.4.6.2.SDK | Rozhraní .NET framework 4.6.2 SDK | 16.3.29230.54
Microsoft.Net.Component.4.7.1.SDK | Rozhraní .NET framework 4.7.1 SDK | 16.3.29230.54
Microsoft.Net.Component.4.7.2.SDK | Rozhraní .NET framework 4.7.2 SDK | 16.3.29230.54
Microsoft.Net.Component.4.7.SDK | Rozhraní .NET framework 4.7 SDK | 16.3.29230.54
Microsoft.Net.Core.Component.SDK.2.2 | Modul runtime .NET Core 2,2 | 16.3.29318.74
Microsoft.NetCore.ComponentGroup.DevelopmentTools.2.1 | Vývojové nástroje Plus .NET Core 2,1 | 16.3.29207.166
Microsoft.NetCore.ComponentGroup.Web.2.1 | Vývojové nástroje pro web Plus .NET Core 2,1 | 16.3.29207.166
Microsoft.VisualStudio.Component.AzureDevOps.OfficeIntegration | Integrace Azure DevOps Office | 16.0.28625.61
Microsoft.VisualStudio.Component.Git | Git for Windows | 16.0.28625.61
Microsoft.VisualStudio.Component.LinqToSql | Nástroje LINQ to SQL | 16.0.28625.61
Microsoft.VisualStudio.Component.TestTools.CodedUITest | Programový test UI | 16.0.28327.66
Microsoft. VisualStudio. Component. VC. 14.20. ARM | MSVC V142-VS 2019 C++ nástroje pro sestavení ARM (v 14.20) | 16.1.28829.92
Microsoft. VisualStudio. Component. VC. 14.20. ARM. Spectre | MSVC V142-VS 2019 C++ ARM Spectre – zmírňovaná knihovny (v 14.20) | 16.1.28829.92
Microsoft. VisualStudio. Component. VC. 14.20. ARM64 | MSVC V142-VS 2019 C++ ARM64 Build Tools (v 14.20) | 16.1.28829.92
Microsoft. VisualStudio. Component. VC. 14.20. ARM64. Spectre | MSVC V142-VS 2019 C++ ARM64 Spectre-zmírňované knihovny (v 14.20) | 16.1.28829.92
Microsoft. VisualStudio. Component. VC. 14.20. ATL | C++v 14.20 ATL pro nástroje sestavení V142 (x86 & x64) | 16.1.28829.92
Microsoft. VisualStudio. Component. VC. 14.20. ATL. ARM | C++v 14.20 ATL pro nástroje V142 Build (ARM) | 16.1.28829.92
Microsoft. VisualStudio. Component. VC. 14.20. ATL. ARM. Spectre | C++v 14.20 ATL pro nástroje sestavení V142 s omezeními Spectre (ARM) | 16.1.28829.92
Microsoft. VisualStudio. Component. VC. 14.20. ATL. ARM64 | C++v 14.20 ATL pro nástroje V142 Build (ARM64) | 16.1.28829.92
Microsoft. VisualStudio. Component. VC. 14.20. ATL. ARM64. Spectre | C++v 14.20 ATL pro nástroje pro vytváření V142 s Spectre Zmírněními (ARM64) | 16.1.28829.92
Microsoft. VisualStudio. Component. VC. 14.20. ATL. Spectre | C++v 14.20 ATL pro nástroje sestavení V142 s riziky Spectre (x86 & x64) | 16.1.28829.92
Microsoft. VisualStudio. Component. VC. 14.20. CLI. support | C++Podpora/CLI pro nástroje V142 Build (14,20) | 16.3.29207.166
Microsoft. VisualStudio. Component. VC. 14.20. MFC | C++v 14.20 MFC pro nástroje sestavení V142 (x86 & x64) | 16.2.29003.222
Microsoft. VisualStudio. Component. VC. 14.20. MFC. ARM | C++v 14.20 MFC pro nástroje sestavení V142 (ARM) | 16.1.28829.92
Microsoft. VisualStudio. Component. VC. 14.20. MFC. ARM. Spectre | C++v 14.20 MFC pro nástroje sestavení V142 s omezeními Spectre (ARM) | 16.1.28829.92
Microsoft. VisualStudio. Component. VC. 14.20. MFC. ARM64 | C++v 14.20 MFC pro nástroje sestavení V142 (ARM64) | 16.1.28829.92
Microsoft. VisualStudio. Component. VC. 14.20. MFC. ARM64. Spectre | C++v 14.20 MFC pro nástroje sestavení V142 s riziky Spectre (ARM64) | 16.1.28829.92
Microsoft. VisualStudio. Component. VC. 14.20. MFC. Spectre | C++v 14.20 MFC pro nástroje sestavení V142 s riziky Spectre (x86 & x64) | 16.1.28829.92
Microsoft. VisualStudio. Component. VC. 14.20. x86. x64 | Nástroje MSVC V142-VS C++ 2019 x64/x86 Build Tools (v 14.20) | 16.1.28829.92
Microsoft. VisualStudio. Component. VC. 14.20. x86. x64. Spectre | MSVC V142-VS 2019 C++ x64/x86 Spectre-zmírňované knihovny (v 14.20) | 16.1.28829.92
Microsoft. VisualStudio. Component. VC. 14.21. ARM | MSVC V142-VS 2019 C++ nástroje pro sestavení ARM (v 14.21) | 16.3.29207.166
Microsoft. VisualStudio. Component. VC. 14.21. ARM. Spectre | MSVC V142-VS 2019 C++ ARM Spectre – zmírňovaná knihovny (v 14.21) | 16.3.29207.166
Microsoft. VisualStudio. Component. VC. 14.21. ARM64 | MSVC V142-VS 2019 C++ ARM64 Build Tools (v 14.21) | 16.3.29207.166
Microsoft. VisualStudio. Component. VC. 14.21. ARM64. Spectre | MSVC V142-VS 2019 C++ ARM64 Spectre-zmírňované knihovny (v 14.21) | 16.3.29207.166
Microsoft. VisualStudio. Component. VC. 14.21. ATL | C++v 14.21 ATL pro nástroje sestavení V142 (x86 & x64) | 16.2.29019.55
Microsoft. VisualStudio. Component. VC. 14.21. ATL. ARM | C++v 14.21 ATL pro nástroje V142 Build (ARM) | 16.2.29019.55
Microsoft. VisualStudio. Component. VC. 14.21. ATL. ARM. Spectre | C++v 14.21 ATL pro nástroje sestavení V142 s omezeními Spectre (ARM) | 16.2.29019.55
Microsoft. VisualStudio. Component. VC. 14.21. ATL. ARM64 | C++v 14.21 ATL pro nástroje V142 Build (ARM64) | 16.2.29019.55
Microsoft. VisualStudio. Component. VC. 14.21. ATL. ARM64. Spectre | C++v 14.21 ATL pro nástroje pro vytváření V142 s Spectre Zmírněními (ARM64) | 16.2.29019.55
Microsoft. VisualStudio. Component. VC. 14.21. ATL. Spectre | C++v 14.21 ATL pro nástroje sestavení V142 s riziky Spectre (x86 & x64) | 16.2.29019.55
Microsoft. VisualStudio. Component. VC. 14.21. CLI. support | C++Podpora/CLI pro nástroje V142 Build (14,21) | 16.3.29207.166
Microsoft. VisualStudio. Component. VC. 14.21. MFC | C++v 14.21 MFC pro nástroje sestavení V142 (x86 & x64) | 16.2.29019.55
Microsoft. VisualStudio. Component. VC. 14.21. MFC. ARM | C++v 14.21 MFC pro nástroje sestavení V142 (ARM) | 16.2.29019.55
Microsoft. VisualStudio. Component. VC. 14.21. MFC. ARM. Spectre | C++v 14.21 MFC pro nástroje sestavení V142 s omezeními Spectre (ARM) | 16.2.29019.55
Microsoft. VisualStudio. Component. VC. 14.21. MFC. ARM64 | C++v 14.21 MFC pro nástroje sestavení V142 (ARM64) | 16.2.29019.55
Microsoft. VisualStudio. Component. VC. 14.21. MFC. ARM64. Spectre | C++v 14.21 MFC pro nástroje sestavení V142 s riziky Spectre (ARM64) | 16.2.29019.55
Microsoft. VisualStudio. Component. VC. 14.21. MFC. Spectre | C++v 14.21 MFC pro nástroje sestavení V142 s riziky Spectre (x86 & x64) | 16.2.29019.55
Microsoft. VisualStudio. Component. VC. 14.21. x86. x64 | Nástroje MSVC V142-VS C++ 2019 x64/x86 Build Tools (v 14.21) | 16.3.29207.166
Microsoft. VisualStudio. Component. VC. 14.21. x86. x64. Spectre | MSVC V142-VS 2019 C++ x64/x86 Spectre-zmírňované knihovny (v 14.21) | 16.3.29207.166
Microsoft. VisualStudio. Component. VC. 14.22. ARM | MSVC V142-VS 2019 C++ nástroje pro sestavení ARM (v 14.22) | 16.3.29230.54
Microsoft. VisualStudio. Component. VC. 14.22. ARM. Spectre | MSVC V142-VS 2019 C++ ARM Spectre – zmírňovaná knihovny (v 14.22) | 16.3.29230.54
Microsoft. VisualStudio. Component. VC. 14.22. ARM64 | MSVC V142-VS 2019 C++ ARM64 Build Tools (v 14.22) | 16.3.29230.54
Microsoft. VisualStudio. Component. VC. 14.22. ARM64. Spectre | MSVC V142-VS 2019 C++ ARM64 Spectre-zmírňované knihovny (v 14.22) | 16.3.29230.54
Microsoft. VisualStudio. Component. VC. 14.22. ATL | C++v 14.22 ATL pro nástroje sestavení V142 (x86 & x64) | 16.3.29230.54
Microsoft. VisualStudio. Component. VC. 14.22. ATL. ARM | C++v 14.22 ATL pro nástroje V142 Build (ARM) | 16.3.29230.54
Microsoft. VisualStudio. Component. VC. 14.22. ATL. ARM. Spectre | C++v 14.22 ATL pro nástroje sestavení V142 s omezeními Spectre (ARM) | 16.3.29230.54
Microsoft. VisualStudio. Component. VC. 14.22. ATL. ARM64 | C++v 14.22 ATL pro nástroje V142 Build (ARM64) | 16.3.29230.54
Microsoft. VisualStudio. Component. VC. 14.22. ATL. ARM64. Spectre | C++v 14.22 ATL pro nástroje pro vytváření V142 s Spectre Zmírněními (ARM64) | 16.3.29230.54
Microsoft. VisualStudio. Component. VC. 14.22. ATL. Spectre | C++v 14.22 ATL pro nástroje sestavení V142 s riziky Spectre (x86 & x64) | 16.3.29230.54
Microsoft. VisualStudio. Component. VC. 14.22. CLI. support | C++Podpora/CLI pro nástroje V142 Build (14,22) | 16.3.29230.54
Microsoft. VisualStudio. Component. VC. 14.22. MFC | C++v 14.22 MFC pro nástroje sestavení V142 (x86 & x64) | 16.3.29230.54
Microsoft. VisualStudio. Component. VC. 14.22. MFC. ARM | C++v 14.22 MFC pro nástroje sestavení V142 (ARM) | 16.3.29230.54
Microsoft. VisualStudio. Component. VC. 14.22. MFC. ARM. Spectre | C++v 14.22 MFC pro nástroje sestavení V142 s omezeními Spectre (ARM) | 16.3.29230.54
Microsoft. VisualStudio. Component. VC. 14.22. MFC. ARM64 | C++v 14.22 MFC pro nástroje sestavení V142 (ARM64) | 16.3.29230.54
Microsoft. VisualStudio. Component. VC. 14.22. MFC. ARM64. Spectre | C++v 14.22 MFC pro nástroje sestavení V142 s riziky Spectre (ARM64) | 16.3.29230.54
Microsoft. VisualStudio. Component. VC. 14.22. MFC. Spectre | C++v 14.22 MFC pro nástroje sestavení V142 s riziky Spectre (x86 & x64) | 16.3.29230.54
Microsoft. VisualStudio. Component. VC. 14.22. x86. x64 | Nástroje MSVC V142-VS C++ 2019 x64/x86 Build Tools (v 14.22) | 16.3.29230.54
Microsoft. VisualStudio. Component. VC. 14.22. x86. x64. Spectre | MSVC V142-VS 2019 C++ x64/x86 Spectre-zmírňované knihovny (v 14.22) | 16.3.29230.54
Microsoft.VisualStudio.Component.VC.ATL.ARM | C++ATL pro nejnovější nástroje V142 Build (ARM) | 16.3.29230.54
Microsoft.VisualStudio.Component.VC.ATL.ARM.Spectre | C++ATL pro nejnovější nástroje V142 buildu s omezeními Spectre (ARM) | 16.3.29230.54
Microsoft.VisualStudio.Component.VC.ATL.ARM64 | C++ATL pro nejnovější nástroje V142 Build (ARM64) | 16.3.29230.54
Microsoft.VisualStudio.Component.VC.ATL.ARM64.Spectre | C++ATL pro nejnovější nástroje V142 buildu s omezeními Spectre (ARM64) | 16.3.29230.54
Microsoft.VisualStudio.Component.VC.ATL.Spectre | C++ATL pro nejnovější nástroje V142 buildu s omezeními Spectre (x86 & x64) | 16.3.29230.54
Microsoft.VisualStudio.Component.VC.ATLMFC.Spectre | C++MFC pro nejnovější nástroje pro sestavení V142 se Zmírněními hrozeb Spectre (x86 & x64) | 16.3.29230.54
Microsoft.VisualStudio.Component.VC.MFC.ARM | C++MFC pro nejnovější nástroje V142 Build (ARM) | 16.3.29230.54
Microsoft.VisualStudio.Component.VC.MFC.ARM.Spectre | C++MFC pro nejnovější nástroje V142 buildu s omezeními Spectre (ARM) | 16.3.29230.54
Microsoft.VisualStudio.Component.VC.MFC.ARM64 | C++MFC pro nejnovější nástroje V142 Build (ARM64) | 16.3.29230.54
Microsoft.VisualStudio.Component.VC.MFC.ARM64.Spectre | C++MFC pro nejnovější nástroje V142 buildu s omezeními Spectre (ARM64) | 16.3.29230.54
Microsoft.VisualStudio.Component.VC.Redist.MSM | C++2019 Distribuovatelný MSMs | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.Runtimes.ARM.Spectre | MSVC V142-VS 2019 C++ ARM Spectre – zmírňovaná knihovny (v 14.23) | 16.3.29230.54
Microsoft.VisualStudio.Component.VC.Runtimes.ARM64.Spectre | MSVC V142-VS 2019 C++ ARM64 Spectre-zmírňované knihovny (v 14.23) | 16.3.29230.54
Microsoft.VisualStudio.Component.VC.Runtimes.x86.x64.Spectre | MSVC V142-VS 2019 C++ x64/x86 Spectre-zmírňované knihovny (v 14.23)  | 16.3.29230.54
Microsoft.VisualStudio.Component.VC.v141.ARM.Spectre | MSVC v141-VS 2017 C++ ARM Spectre – zmírňovaná knihovny (v 14.16) | 16.1.28829.92
Microsoft.VisualStudio.Component.VC.v141.ARM64.Spectre | MSVC v141-VS 2017 C++ ARM64 Spectre-zmírňované knihovny (v 14.16) | 16.1.28829.92
Microsoft.VisualStudio.Component.VC.v141.ATL | C++ATL pro nástroje v141 Build (x86 & x64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.ATL.ARM | C++ATL pro nástroje v141 Build (ARM) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.ATL.ARM.Spectre | C++ATL pro nástroje buildu v141 s omezeními Spectre (ARM) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.ATL.ARM64 | C++ATL pro nástroje v141 Build (ARM64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.ATL.ARM64.Spectre | C++ATL pro nástroje v141 Build s omezeními Spectre (ARM64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.ATL.Spectre | C++ATL pro nástroje v141 Build s omezeními Spectre (x86 & x64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.CLI.Support | C++Podpora/CLI pro nástroje v141 Build (14,16) | 16.3.29207.166
Microsoft.VisualStudio.Component.VC.v141.MFC | C++MFC pro nástroje v141 Build (x86 & x64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.MFC.ARM | C++MFC pro nástroje v141 Build (ARM) | 16.2.28915.88
Microsoft.VisualStudio.Component.VC.v141.MFC.ARM.Spectre | C++MFC pro nástroje v141 Build s omezeními Spectre (ARM) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.MFC.ARM64 | C++MFC pro nástroje v141 Build (ARM64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.MFC.ARM64.Spectre | C++MFC pro nástroje v141 Build s omezeními Spectre (ARM64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.MFC.Spectre | C++MFC pro nástroje v141 Build s omezeními Spectre (x86 & x64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.x86.x64.Spectre | MSVC v141-VS 2017 C++ x64/x86 Spectre-zmírňované knihovny (v 14.16) | 16.1.28829.92
Microsoft.VisualStudio.Component.VisualStudioData | Zdroje dat a odkazy na služby | 16.0.28707.177
Microsoft.VisualStudio.Component.WinXP | C++Podpora Windows XP pro VS 2017 (v141) Tools [zastaralé] | 16.1.28811.260
Microsoft.VisualStudio.Web.Mvc4.ComponentGroup | ASP.NET MVC 4 | 16.1.28810.153
