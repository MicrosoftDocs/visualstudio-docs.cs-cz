---
title: ID pracovního vytížení a komponenta Visual Studio Enterprise 2017
titleSuffix: ''
description: Použití pracovního vytížení a komponenta ID pro instalaci sady Visual Studio pomocí příkazového řádku nebo v závislosti na VSIX manifest
keywords: ''
author: TerryGLee
ms.author: tglee
manager: douge
ms.date: 11/13/2018
ms.topic: reference
helpviewer_keywords:
- workload ID, Visual Studio
- component ID, Visual Studio
- install Visual Studio, administrator guide
ms.service: ''
ms.technology: vs-acquisition
ms.prod: visual-studio-dev15
ms.assetid: be73e3af-d87b-4d14-bd08-2e4bda074fb3
ms.workload:
- multiple
ms.openlocfilehash: 7d0496b9559e5e3fbd8984de97d98ea2e075db1a
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53063163"
---
# <a name="visual-studio-enterprise-2017-component-directory"></a>Složka komponenty Visual Studio Enterprise 2017

Tabulky v tomto seznamu stránce ID, můžete použít k instalaci sady Visual Studio pomocí příkazového řádku nebo je můžete zadat jako závislost v manifestu VSIX. Všimněte si, že přidáme další součásti vydaných aktualizací sady Visual Studio.

Všimněte si také následující stránka:

* Každá úloha má vlastní oddíl, za nímž následuje Identifikátor pracovního vytížení a tabulku komponent, které jsou k dispozici pro pracovní vytížení.
* Ve výchozím nastavení **vyžaduje** součásti nainstaluje, když jste si nainstalovali úlohu.
* Pokud budete chtít, můžete nainstalovat také **doporučená** a **volitelné** komponenty.
* Přidali jsme také oddíl, který obsahuje další součásti, které nejsou pod něj nespadá u jakékoli úlohy.

Když nastavíte závislosti v manifestu VSIX, je nutné zadat ID součástí pouze. Určení závislostí naše minimální součástí pomocí tabulek na této stránce. V některých případech to může znamenat, že zadáváte pouze jednu komponentu z pracovního vytížení. V jiných scénářích může znamenat, že zadáte více komponent z jedné úlohy nebo více komponent z více úloh. Další informace najdete v tématu [postupy: migrace projektů rozšíření do sady Visual Studio 2017](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2017.md) stránky.

Další informace o tom, jak pomocí těchto identifikátorů najdete v části [pomocí parametrů příkazového řádku instalace sady Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md) stránky. A seznam pracovního vytížení a komponenta ID pro ostatní produkty, naleznete v tématu [funkcí sady Visual Studio 2017 a ID součástí](workload-and-component-ids.md) stránky.

## <a name="visual-studio-core-editor-included-with-visual-studio-enterprise-2017"></a>Základní editor Visual Studio (je součástí sady Visual Studio Enterprise 2017)

**ID:** Microsoft.VisualStudio.Workload.CoreEditor

**Popis:** příkazové prostředí sady Visual Studio core, včetně úprav kódu podle syntaxe, zdrojového kódu a správy pracovních položek.

### <a name="components-included-by-this-workload"></a>Pomocí této úlohy zahrnuté komponenty

ID součásti | Název | Version | Typ závislosti
--- | --- | --- | ---
Microsoft.VisualStudio.Component.CoreEditor | Základním editoru sady Visual Studio | 15.8.27729.1 | Požadováno
Microsoft.VisualStudio.Component.StartPageExperiment.Cpp | Visual Studio úvodní stránka pro uživatele jazyka C++ | 15.0.27128.1 | volitelná,

## <a name="azure-development"></a>Vývoj pro Azure

**ID:** Microsoft.VisualStudio.Workload.Azure

**Popis:** sady Azure SDK, nástroje a projekty pro vývoj cloudových aplikací, vytváření prostředků a sestavování kontejnerů včetně podpory Dockeru.

### <a name="components-included-by-this-workload"></a>Pomocí této úlohy zahrnuté komponenty

ID součásti | Název | Version | Typ závislosti
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Jazykové služby Razor | 15.0.26720.2 | Požadováno
Component.Microsoft.VisualStudio.Web.AzureFunctions | Nástroje Microsoft Azure WebJobs | 15.7.27617.1 | Požadováno
Component.Microsoft.Web.LibraryManager | Správce knihovny | 15.8.27705.0 | Požadováno
Component.WebSocket | WebSocket4Net | 15.0.26606.0 | Požadováno
Microsoft.Component.ClickOnce | Publikování ClickOnce | 15.8.27825.0 | Požadováno
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | Požadováno
Microsoft.Component.NetFX.Core.Runtime | Modul runtime .NET core | 15.0.26208.0 | Požadováno
Microsoft.Net.Component.4.5.2.TargetingPack | Rozhraní .NET framework 4.5.2 targeting pack | 15.6.27406.0 | Požadováno
Microsoft.Net.Component.4.5.TargetingPack | .NET framework 4.5 targeting pack | 15.6.27406.0 | Požadováno
Microsoft.Net.Component.4.6.1.SDK | Rozhraní .NET framework 4.6.1 SDK | 15.6.27406.0 | Požadováno
Microsoft.Net.Component.4.6.1.TargetingPack | Rozhraní .NET framework 4.6.1 targeting pack | 15.6.27406.0 | Požadováno
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Vývojové nástroje .NET framework 4.6.1 | 15.8.27825.0 | Požadováno
Microsoft.Net.Core.Component.SDK.2.1 | Vývojové nástroje .NET core 2.1 | 15.8.27924.0 | Požadováno
Microsoft.NetCore.ComponentGroup.DevelopmentTools.2.1 | Vývojové nástroje .NET core 2.1 | 15.8.27924.0 | Požadováno
Microsoft.NetCore.ComponentGroup.Web.2.1 | Vývojové nástroje .NET core 2.1 | 15.8.27924.0 | Požadováno
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Azure – nástroje pro tvorbu | 15.8.27825.0 | Požadováno
Microsoft.VisualStudio.Component.Azure.ClientLibs | Knihovny Azure pro .NET | 15.0.26208.0 | Požadováno
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Emulátor výpočtů v Azure | 15.0.26621.2 | Požadováno
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Emulátor úložiště Azure | 15.9.28125.51 | Požadováno
Microsoft.VisualStudio.Component.CloudExplorer | Průzkumník cloudu | 15.9.28230.55 | Požadováno
Microsoft.VisualStudio.Component.Common.Azure.Tools | Nástroje pro připojení a publikování | 15.9.28107.0 | Požadováno
Microsoft.VisualStudio.Component.DockerTools | Kontejnerové vývojové nástroje | 15.8.27906.1 | Požadováno
Microsoft.VisualStudio.Component.DockerTools.BuildTools | Kontejnerové vývojové nástroje – Build Tools | 15.7.27617.1 | Požadováno
Microsoft.VisualStudio.Component.FSharp | F#podpora jazyků | 15.8.27825.0 | Požadováno
Microsoft.VisualStudio.Component.FSharp.WebTemplates | F#podpora jazyků pro webové projekty | 15.8.27705.0 | Požadováno
Microsoft.VisualStudio.Component.IISExpress | Služba IIS Express  | 15.0.26208.0 | Požadováno
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostika jazyka JavaScript | 15.8.27729.1 | Požadováno
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Podpora jazyků JavaScript a TypeScript | 15.9.28125.51 | Požadováno
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Základní spravovaný úloze vývoje desktopových aplikací | 15.8.27729.1 | Požadováno
Microsoft.VisualStudio.Component.NuGet | Správce balíčků NuGet | 15.9.28016.0 | Požadováno
Microsoft.VisualStudio.Component.PortableLibrary | .NET portable Library targeting pack | 15.6.27309.0 | Požadováno
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilátory C# a Visual Basic Roslyn | 15.6.27309.0 | Požadováno
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# a Visual Basic | 15.8.27729.1 | Požadováno
Microsoft.VisualStudio.Component.SQL.ADAL | SQL ADAL runtime | 15.6.27406.0 | Požadováno
Microsoft.VisualStudio.Component.SQL.CLR | Datové typy CLR pro SQL Server | 15.0.26208.0 | Požadováno
Microsoft.VisualStudio.Component.SQL.CMDUtils | Nástroje příkazového řádku SQL serveru | 15.0.26208.0 | Požadováno
Microsoft.VisualStudio.Component.SQL.DataSources | Zdroje dat pro podporu SQL serveru | 15.0.26621.2 | Požadováno
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 15.7.27617.1 | Požadováno
Microsoft.VisualStudio.Component.SQL.NCLI | Nativní klient systému SQL Server | 15.0.26208.0 | Požadováno
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 15.9.28107.0 | Požadováno
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Nástroje statické analýzy | 15.0.26208.0 | Požadováno
Microsoft.VisualStudio.Component.TextTemplating | Transformace textové šablony | 15.0.26208.0 | Požadováno
Microsoft.VisualStudio.Component.TypeScript.3.1 | TypeScript 3.1 SDK | 15.0.28218.60 | Požadováno
Microsoft.VisualStudio.Component.VisualStudioData | Zdroje dat a odkazy na služby | 15.6.27406.0 | Požadováno
Microsoft.VisualStudio.Component.Web | Nástroje pro vývoj pro ASP.NET a web | 15.8.27825.0 | Požadováno
Microsoft.VisualStudio.ComponentGroup.Azure.Prerequisites | Požadavky na vývoj pro Azure | 15.9.28107.0 | Požadováno
Microsoft.VisualStudio.ComponentGroup.AzureFunctions | Nástroje Microsoft Azure WebJobs | 15.7.27617.1 | Požadováno
Microsoft.VisualStudio.ComponentGroup.Web | Vývoj pro ASP.NET a webové nástroje – požadavky | 15.9.28219.51 | Požadováno
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Vývoj pro ASP.NET a web | 15.8.27825.0 | Požadováno
Microsoft.Component.Azure.DataLake.Tools | Azure Data Lake a Stream Analytics Tools | 15.9.28107.0 | Doporučeno
Microsoft.Net.Component.4.5.1.TargetingPack | Rozhraní .NET framework 4.5.1 targeting pack | 15.6.27406.0 | Doporučeno
Microsoft.Net.Component.4.6.TargetingPack | .NET framework 4.6 targeting pack | 15.6.27406.0 | Doporučeno
Microsoft.Net.Component.4.TargetingPack | .NET framework 4 targeting pack | 15.6.27406.0 | Doporučeno
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Vývojové nástroje .NET framework 4 – 4.6 | 15.6.27406.0 | Doporučeno
Microsoft.VisualStudio.Component.AspNet45 | Rozšířené funkce ASP.NET | 15.7.27625.0 | Doporučeno
Microsoft.VisualStudio.Component.Azure.MobileAppsSdk | Azure Mobile Apps SDK | 15.7.27625.0 | Doporučeno
Microsoft.VisualStudio.Component.Azure.ResourceManager.Tools | Základní nástroje Azure Resource Manageru | 15.9.28107.0 | Doporučeno
Microsoft.VisualStudio.Component.Azure.ServiceFabric.Tools | Nástroje Service Fabricu | 15.8.27825.0 | Doporučeno
Microsoft.VisualStudio.Component.Azure.Waverton | Základní nástroje pro Azure Cloud Services | 15.9.28107.0 | Doporučeno
Microsoft.VisualStudio.Component.Azure.Waverton.BuildTools | Nástroje pro vytváření Azure Cloud Services | 15.7.27617.1 | Doporučeno
Microsoft.VisualStudio.Component.Debugger.Snapshot | Snapshot Debugger | 15.8.28010.0 | Doporučeno
Microsoft.VisualStudio.Component.DiagnosticTools | Nástroje pro profilaci .NET | 15.8.27729.1 | Doporučeno
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | 15.8.27729.1 | Doporučeno
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 15.8.27729.1 | Doporučeno
Microsoft.VisualStudio.ComponentGroup.Azure.CloudServices | Nástroje pro Azure Cloud Services | 15.0.26504.0 | Doporučeno
Microsoft.VisualStudio.ComponentGroup.Azure.ResourceManager.Tools | Nástroje Azure Resource Manageru | 15.0.27005.2 | Doporučeno
Microsoft.Net.Component.4.6.2.SDK | Rozhraní .NET framework 4.6.2 SDK | 15.6.27406.0 | volitelná,
Microsoft.Net.Component.4.6.2.TargetingPack | Rozhraní .NET framework 4.6.2 targeting pack | 15.6.27406.0 | volitelná,
Microsoft.Net.Component.4.7.1.SDK | Rozhraní .NET framework 4.7.1 SDK | 15.6.27406.0 | volitelná,
Microsoft.Net.Component.4.7.1.TargetingPack | Rozhraní .NET framework 4.7.1 targeting pack | 15.6.27406.0 | volitelná,
Microsoft.Net.Component.4.7.2.SDK | Rozhraní .NET framework 4.7.2 SDK | 15.8.27825.0 | volitelná,
Microsoft.Net.Component.4.7.2.TargetingPack | Rozhraní .NET framework 4.7.2 targeting pack | 15.8.27825.0 | volitelná,
Microsoft.Net.Component.4.7.SDK | Rozhraní .NET framework 4.7 SDK | 15.6.27406.0 | volitelná,
Microsoft.Net.Component.4.7.TargetingPack | .NET framework 4.7 targeting pack | 15.6.27406.0 | volitelná,
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | Vývojové nástroje .NET framework 4.6.2 | 15.6.27406.0 | volitelná,
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | Vývojové nástroje .NET framework 4.7.1 | 15.6.27406.0 | volitelná,
Microsoft.Net.ComponentGroup.4.7.2.DeveloperTools | Vývojové nástroje .NET framework 4.7.2 | 15.8.27825.0 | volitelná,
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | Vývojové nástroje .NET framework 4.7 | 15.6.27406.0 | volitelná,
Microsoft.Net.Core.Component.SDK | Vývojové nástroje .NET core 2.0 | 15.6.27406.0 | volitelná,
Microsoft.Net.Core.Component.SDK.1x | .NET core 1.0 až 1.1. vývojové nástroje | 15.6.27406.0 | volitelná,
Microsoft.NetCore.1x.ComponentGroup.Web | .NET core 1.0 až 1.1 vývojářské nástroje pro Web | 15.6.27406.0 | volitelná,
Microsoft.NetCore.ComponentGroup.DevelopmentTools | Vývojové nástroje .NET core 2.0 | 15.8.27729.1 | volitelná,
Microsoft.NetCore.ComponentGroup.Web | Vývojové nástroje .NET core 2.0 | 15.7.27625.0 | volitelná,
Microsoft.VisualStudio.Component.Azure.Storage.AzCopy | Azure Storage AzCopy | 15.0.26906.1 | volitelná,
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | 15.8.27924.0 | volitelná,

## <a name="data-storage-and-processing"></a>Ukládání a zpracování dat

**ID:** Microsoft.VisualStudio.Workload.Data

**Popis:** připojit, vyvíjet a testovat datová řešení pomocí SQL Server, Azure Data Lake nebo Hadoop.

### <a name="components-included-by-this-workload"></a>Pomocí této úlohy zahrnuté komponenty

ID součásti | Název | Version | Typ závislosti
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Jazykové služby Razor | 15.0.26720.2 | Doporučeno
Component.Microsoft.Web.LibraryManager | Správce knihovny | 15.8.27705.0 | Doporučeno
Component.Redgate.ReadyRoll | Redgate ReadyRoll Core | 1.17.18155.10346 | Doporučeno
Component.Redgate.SQLPrompt.VsPackage | Redgate SQL Prompt Core | 9.2.0.5601 | Doporučeno
Component.Redgate.SQLSearch.VSExtension | Hledání v Redgate SQL | 3.1.7.2062 | Doporučeno
Component.WebSocket | WebSocket4Net | 15.0.26606.0 | Doporučeno
Microsoft.Component.Azure.DataLake.Tools | Azure Data Lake a Stream Analytics Tools | 15.9.28107.0 | Doporučeno
Microsoft.Component.ClickOnce | Publikování ClickOnce | 15.8.27825.0 | Doporučeno
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | Doporučeno
Microsoft.Net.Component.4.5.1.TargetingPack | Rozhraní .NET framework 4.5.1 targeting pack | 15.6.27406.0 | Doporučeno
Microsoft.Net.Component.4.5.2.TargetingPack | Rozhraní .NET framework 4.5.2 targeting pack | 15.6.27406.0 | Doporučeno
Microsoft.Net.Component.4.5.TargetingPack | .NET framework 4.5 targeting pack | 15.6.27406.0 | Doporučeno
Microsoft.Net.Component.4.6.1.SDK | Rozhraní .NET framework 4.6.1 SDK | 15.6.27406.0 | Doporučeno
Microsoft.Net.Component.4.6.1.TargetingPack | Rozhraní .NET framework 4.6.1 targeting pack | 15.6.27406.0 | Doporučeno
Microsoft.Net.Component.4.6.TargetingPack | .NET framework 4.6 targeting pack | 15.6.27406.0 | Doporučeno
Microsoft.Net.Component.4.TargetingPack | .NET framework 4 targeting pack | 15.6.27406.0 | Doporučeno
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Vývojové nástroje .NET framework 4.6.1 | 15.8.27825.0 | Doporučeno
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Vývojové nástroje .NET framework 4 – 4.6 | 15.6.27406.0 | Doporučeno
Microsoft.Net.Core.Component.SDK.2.1 | Vývojové nástroje .NET core 2.1 | 15.8.27924.0 | Doporučeno
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Azure – nástroje pro tvorbu | 15.8.27825.0 | Doporučeno
Microsoft.VisualStudio.Component.Azure.ClientLibs | Knihovny Azure pro .NET | 15.0.26208.0 | Doporučeno
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Emulátor výpočtů v Azure | 15.0.26621.2 | Doporučeno
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Emulátor úložiště Azure | 15.9.28125.51 | Doporučeno
Microsoft.VisualStudio.Component.Azure.Waverton | Základní nástroje pro Azure Cloud Services | 15.9.28107.0 | Doporučeno
Microsoft.VisualStudio.Component.Azure.Waverton.BuildTools | Nástroje pro vytváření Azure Cloud Services | 15.7.27617.1 | Doporučeno
Microsoft.VisualStudio.Component.CloudExplorer | Průzkumník cloudu | 15.9.28230.55 | Doporučeno
Microsoft.VisualStudio.Component.Common.Azure.Tools | Nástroje pro připojení a publikování | 15.9.28107.0 | Doporučeno
Microsoft.VisualStudio.Component.DockerTools | Kontejnerové vývojové nástroje | 15.8.27906.1 | Doporučeno
Microsoft.VisualStudio.Component.DockerTools.BuildTools | Kontejnerové vývojové nástroje – Build Tools | 15.7.27617.1 | Doporučeno
Microsoft.VisualStudio.Component.IISExpress | Služba IIS Express  | 15.0.26208.0 | Doporučeno
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostika jazyka JavaScript | 15.8.27729.1 | Doporučeno
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Podpora jazyků JavaScript a TypeScript | 15.9.28125.51 | Doporučeno
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Základní spravovaný úloze vývoje desktopových aplikací | 15.8.27729.1 | Doporučeno
Microsoft.VisualStudio.Component.NuGet | Správce balíčků NuGet | 15.9.28016.0 | Doporučeno
Microsoft.VisualStudio.Component.PortableLibrary | .NET portable Library targeting pack | 15.6.27309.0 | Doporučeno
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilátory C# a Visual Basic Roslyn | 15.6.27309.0 | Doporučeno
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# a Visual Basic | 15.8.27729.1 | Doporučeno
Microsoft.VisualStudio.Component.SQL.ADAL | SQL ADAL runtime | 15.6.27406.0 | Doporučeno
Microsoft.VisualStudio.Component.SQL.CLR | Datové typy CLR pro SQL Server | 15.0.26208.0 | Doporučeno
Microsoft.VisualStudio.Component.SQL.CMDUtils | Nástroje příkazového řádku SQL serveru | 15.0.26208.0 | Doporučeno
Microsoft.VisualStudio.Component.SQL.DataSources | Zdroje dat pro podporu SQL serveru | 15.0.26621.2 | Doporučeno
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 15.7.27617.1 | Doporučeno
Microsoft.VisualStudio.Component.SQL.NCLI | Nativní klient systému SQL Server | 15.0.26208.0 | Doporučeno
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 15.9.28107.0 | Doporučeno
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Nástroje statické analýzy | 15.0.26208.0 | Doporučeno
Microsoft.VisualStudio.Component.TextTemplating | Transformace textové šablony | 15.0.26208.0 | Doporučeno
Microsoft.VisualStudio.Component.TypeScript.3.1 | TypeScript 3.1 SDK | 15.0.28218.60 | Doporučeno
Microsoft.VisualStudio.Component.VisualStudioData | Zdroje dat a odkazy na služby | 15.6.27406.0 | Doporučeno
Microsoft.VisualStudio.Component.Web | Nástroje pro vývoj pro ASP.NET a web | 15.8.27825.0 | Doporučeno
Microsoft.VisualStudio.ComponentGroup.Web | Vývoj pro ASP.NET a webové nástroje – požadavky | 15.9.28219.51 | Doporučeno
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Vývoj pro ASP.NET a web | 15.8.27825.0 | Doporučeno
Microsoft.VisualStudio.Component.FSharp.Desktop | F#Podpora klasické pracovní plochy jazyka | 15.8.27825.0 | volitelná,

## <a name="data-science-and-analytical-applications"></a>Aplikace pro datové vědy a analýzy

**ID:** Microsoft.VisualStudio.Workload.DataScience

**Popis:** jazyky a nástroje pro vytváření datových věd aplikací, včetně Python, R a F#.

### <a name="components-included-by-this-workload"></a>Pomocí této úlohy zahrnuté komponenty

ID součásti | Název | Version | Typ závislosti
--- | --- | --- | ---
Component.Anaconda3.x64 | Anaconda3 64-bit (5.2.0) | 5.2.0 | Doporučeno
Microsoft.Component.CookiecutterTools | Podpora šablon Cookiecutter | 15.0.26621.2 | Doporučeno
Microsoft.Component.PythonTools | Podpora jazyka Python | 15.0.26823.1 | Doporučeno
Microsoft.Component.PythonTools.Web | Podpora webů v Pythonu | 15.9.28107.0 | Doporučeno
Microsoft.Net.Component.4.6.1.TargetingPack | Rozhraní .NET framework 4.6.1 targeting pack | 15.6.27406.0 | Doporučeno
Microsoft.VisualStudio.Component.Common.Azure.Tools | Nástroje pro připojení a publikování | 15.9.28107.0 | Doporučeno
Microsoft.VisualStudio.Component.FSharp.Desktop | F#Podpora klasické pracovní plochy jazyka | 15.8.27825.0 | Doporučeno
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Podpora jazyků JavaScript a TypeScript | 15.9.28125.51 | Doporučeno
Microsoft.VisualStudio.Component.NuGet | Správce balíčků NuGet | 15.9.28016.0 | Doporučeno
Microsoft.VisualStudio.Component.R.Open | Microsoft R Client (3.3.2) | 15.6.27406.0 | Doporučeno
Microsoft.VisualStudio.Component.RHost | Podpora modulu runtime pro vývojové nástroje R | 15.6.27406.0 | Doporučeno
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilátory C# a Visual Basic Roslyn | 15.6.27309.0 | Doporučeno
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# a Visual Basic | 15.8.27729.1 | Doporučeno
Microsoft.VisualStudio.Component.RTools | Podpora jazyka r. | 15.0.26919.1 | Doporučeno
Microsoft.VisualStudio.Component.SQL.CLR | Datové typy CLR pro SQL Server | 15.0.26208.0 | Doporučeno
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Nástroje statické analýzy | 15.0.26208.0 | Doporučeno
Microsoft.VisualStudio.Component.TypeScript.3.1 | TypeScript 3.1 SDK | 15.0.28218.60 | Doporučeno
Microsoft.VisualStudio.Component.VisualStudioData | Zdroje dat a odkazy na služby | 15.6.27406.0 | Doporučeno
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 15.8.27729.1 | Doporučeno
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Vývoj pro ASP.NET a web | 15.8.27825.0 | Doporučeno
Component.Anaconda2.x64 | Anaconda2 64-bit (5.2.0) | 5.2.0 | volitelná,
Component.Anaconda2.x86 | Anaconda2 32 bitů (5.2.0) | 5.2.0 | volitelná,
Component.Anaconda3.x86 | Anaconda3 32 bitů (5.2.0) | 5.2.0 | volitelná,
Microsoft.Component.VC.Runtime.UCRTSDK | Windows Universal CRT SDK | 15.6.27309.0 | volitelná,
Microsoft.ComponentGroup.PythonTools.NativeDevelopment | Nástroje Pythonu pro nativní vývoj | 15.8.27729.1 | volitelná,
Microsoft.VisualStudio.Component.Graphics.Tools | Ladicí program grafiky a profiler GPU pro DirectX | 15.6.27406.0 | volitelná,
Microsoft.VisualStudio.Component.Graphics.Win81 | Grafické nástroje systému Windows 8.1 SDK | 15.6.27406.0 | volitelná,
Microsoft.VisualStudio.Component.VC.140 | Nástrojů VC ++ 2015.3 v14.00 (v140) pro desktop | 15.7.27617.1 | volitelná,
Microsoft.VisualStudio.Component.VC.CoreIde | Visual Studio C++ – základní funkce | 15.6.27406.0 | volitelná,
Microsoft.VisualStudio.Component.VC.DiagnosticTools | Nástroje pro profilaci v C++ | 15.0.26823.1 | volitelná,
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | VC ++ 2017 verze 15.9 v14.16 nejnovější nástroje v141 pro | 15.9.28230.55 | volitelná,
Microsoft.VisualStudio.Component.Windows10SDK | Windows Universal C Runtime | 15.6.27406.0 | volitelná,
Microsoft.VisualStudio.Component.Windows10SDK.17134 | Windows 10 SDK (10.0.17134.0) | 15.8.27924.0 | volitelná,
Microsoft.VisualStudio.Component.Windows81SDK | Windows 8.1 SDK | 15.6.27406.0 | volitelná,

## <a name="net-desktop-development"></a>Vývoj desktopových aplikací .NET

**ID:** Microsoft.VisualStudio.Workload.ManagedDesktop

**Popis:** sestavení WPF, Windows Forms a konzolové aplikace pomocí C#, Visual Basic a F#.

### <a name="components-included-by-this-workload"></a>Pomocí této úlohy zahrnuté komponenty

ID součásti | Název | Version | Typ závislosti
--- | --- | --- | ---
Microsoft.Component.ClickOnce | Publikování ClickOnce | 15.8.27825.0 | Požadováno
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | Požadováno
Microsoft.Net.Component.4.6.1.SDK | Rozhraní .NET framework 4.6.1 SDK | 15.6.27406.0 | Požadováno
Microsoft.Net.Component.4.6.1.TargetingPack | Rozhraní .NET framework 4.6.1 targeting pack | 15.6.27406.0 | Požadováno
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Vývojové nástroje .NET framework 4.6.1 | 15.8.27825.0 | Požadováno
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Základní spravovaný úloze vývoje desktopových aplikací | 15.8.27729.1 | Požadováno
Microsoft.VisualStudio.Component.ManagedDesktop.Prerequisites | Nástroje pro vývoj desktopových aplikací .NET | 15.7.27625.0 | Požadováno
Microsoft.VisualStudio.Component.PortableLibrary | .NET portable Library targeting pack | 15.6.27309.0 | Požadováno
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilátory C# a Visual Basic Roslyn | 15.6.27309.0 | Požadováno
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# a Visual Basic | 15.8.27729.1 | Požadováno
Microsoft.VisualStudio.Component.SQL.CLR | Datové typy CLR pro SQL Server | 15.0.26208.0 | Požadováno
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Nástroje statické analýzy | 15.0.26208.0 | Požadováno
Microsoft.VisualStudio.Component.TextTemplating | Transformace textové šablony | 15.0.26208.0 | Požadováno
Microsoft.VisualStudio.Component.VisualStudioData | Zdroje dat a odkazy na služby | 15.6.27406.0 | Požadováno
Microsoft.ComponentGroup.Blend | Blend for Visual Studio | 15.6.27406.0 | Doporučeno
Microsoft.Net.Component.4.5.1.TargetingPack | Rozhraní .NET framework 4.5.1 targeting pack | 15.6.27406.0 | Doporučeno
Microsoft.Net.Component.4.5.2.TargetingPack | Rozhraní .NET framework 4.5.2 targeting pack | 15.6.27406.0 | Doporučeno
Microsoft.Net.Component.4.5.TargetingPack | .NET framework 4.5 targeting pack | 15.6.27406.0 | Doporučeno
Microsoft.Net.Component.4.6.TargetingPack | .NET framework 4.6 targeting pack | 15.6.27406.0 | Doporučeno
Microsoft.Net.Component.4.TargetingPack | .NET framework 4 targeting pack | 15.6.27406.0 | Doporučeno
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Vývojové nástroje .NET framework 4 – 4.6 | 15.6.27406.0 | Doporučeno
Microsoft.VisualStudio.Component.Debugger.JustInTime | Just-In-Time debugger | 15.0.27005.2 | Doporučeno
Microsoft.VisualStudio.Component.DiagnosticTools | Nástroje pro profilaci .NET | 15.8.27729.1 | Doporučeno
Microsoft.VisualStudio.Component.EntityFramework | Entity Framework 6 tools | 15.6.27406.0 | Doporučeno
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | 15.8.27729.1 | Doporučeno
Microsoft.VisualStudio.Component.LiveUnitTesting | Live Unit Testing | 15.0.26720.2 | Doporučeno
Component.Dotfuscator | PreEmptive ochranu – řešení Dotfuscator | 15.0.26208.0 | volitelná,
Component.Microsoft.VisualStudio.RazorExtension | Jazykové služby Razor | 15.0.26720.2 | volitelná,
Component.Microsoft.Web.LibraryManager | Správce knihovny | 15.8.27705.0 | volitelná,
Component.WebSocket | WebSocket4Net | 15.0.26606.0 | volitelná,
Microsoft.Net.Component.4.6.2.SDK | Rozhraní .NET framework 4.6.2 SDK | 15.6.27406.0 | volitelná,
Microsoft.Net.Component.4.6.2.TargetingPack | Rozhraní .NET framework 4.6.2 targeting pack | 15.6.27406.0 | volitelná,
Microsoft.Net.Component.4.7.1.SDK | Rozhraní .NET framework 4.7.1 SDK | 15.6.27406.0 | volitelná,
Microsoft.Net.Component.4.7.1.TargetingPack | Rozhraní .NET framework 4.7.1 targeting pack | 15.6.27406.0 | volitelná,
Microsoft.Net.Component.4.7.2.SDK | Rozhraní .NET framework 4.7.2 SDK | 15.8.27825.0 | volitelná,
Microsoft.Net.Component.4.7.2.TargetingPack | Rozhraní .NET framework 4.7.2 targeting pack | 15.8.27825.0 | volitelná,
Microsoft.Net.Component.4.7.SDK | Rozhraní .NET framework 4.7 SDK | 15.6.27406.0 | volitelná,
Microsoft.Net.Component.4.7.TargetingPack | .NET framework 4.7 targeting pack | 15.6.27406.0 | volitelná,
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | Vývojové nástroje .NET framework 4.6.2 | 15.6.27406.0 | volitelná,
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | Vývojové nástroje .NET framework 4.7.1 | 15.6.27406.0 | volitelná,
Microsoft.Net.ComponentGroup.4.7.2.DeveloperTools | Vývojové nástroje .NET framework 4.7.2 | 15.8.27825.0 | volitelná,
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | Vývojové nástroje .NET framework 4.7 | 15.6.27406.0 | volitelná,
Microsoft.Net.Core.Component.SDK | Vývojové nástroje .NET core 2.0 | 15.6.27406.0 | volitelná,
Microsoft.Net.Core.Component.SDK.1x | .NET core 1.0 až 1.1. vývojové nástroje | 15.6.27406.0 | volitelná,
Microsoft.Net.Core.Component.SDK.2.1 | Vývojové nástroje .NET core 2.1 | 15.8.27924.0 | volitelná,
Microsoft.NetCore.ComponentGroup.DevelopmentTools | Vývojové nástroje .NET core 2.0 | 15.8.27729.1 | volitelná,
Microsoft.NetCore.ComponentGroup.DevelopmentTools.2.1 | Vývojové nástroje .NET core 2.1 | 15.8.27924.0 | volitelná,
Microsoft.VisualStudio.Component.CodeClone | Klonování kódu | 15.0.26208.0 | volitelná,
Microsoft.VisualStudio.Component.CodeMap | Mapa kódu | 15.0.26208.0 | volitelná,
Microsoft.VisualStudio.Component.Common.Azure.Tools | Nástroje pro připojení a publikování | 15.9.28107.0 | volitelná,
Microsoft.VisualStudio.Component.DependencyValidation.Enterprise | Živé ověření závislosti | 15.0.26208.0 | volitelná,
Microsoft.VisualStudio.Component.DockerTools | Kontejnerové vývojové nástroje | 15.8.27906.1 | volitelná,
Microsoft.VisualStudio.Component.DockerTools.BuildTools | Kontejnerové vývojové nástroje – Build Tools | 15.7.27617.1 | volitelná,
Microsoft.VisualStudio.Component.FSharp | F#podpora jazyků | 15.8.27825.0 | volitelná,
Microsoft.VisualStudio.Component.FSharp.Desktop | F#Podpora klasické pracovní plochy jazyka | 15.8.27825.0 | volitelná,
Microsoft.VisualStudio.Component.GraphDocument | DGML editor | 15.0.27005.2 | volitelná,
Microsoft.VisualStudio.Component.IISExpress | Služba IIS Express  | 15.0.26208.0 | volitelná,
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostika jazyka JavaScript | 15.8.27729.1 | volitelná,
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Podpora jazyků JavaScript a TypeScript | 15.9.28125.51 | volitelná,
Microsoft.VisualStudio.Component.NuGet | Správce balíčků NuGet | 15.9.28016.0 | volitelná,
Microsoft.VisualStudio.Component.SQL.ADAL | SQL ADAL runtime | 15.6.27406.0 | volitelná,
Microsoft.VisualStudio.Component.SQL.CMDUtils | Nástroje příkazového řádku SQL serveru | 15.0.26208.0 | volitelná,
Microsoft.VisualStudio.Component.SQL.DataSources | Zdroje dat pro podporu SQL serveru | 15.0.26621.2 | volitelná,
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 15.7.27617.1 | volitelná,
Microsoft.VisualStudio.Component.SQL.NCLI | Nativní klient systému SQL Server | 15.0.26208.0 | volitelná,
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 15.9.28107.0 | volitelná,
Microsoft.VisualStudio.Component.TypeScript.3.1 | TypeScript 3.1 SDK | 15.0.28218.60 | volitelná,
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | 15.8.27924.0 | volitelná,
Microsoft.VisualStudio.Component.Web | Nástroje pro vývoj pro ASP.NET a web | 15.8.27825.0 | volitelná,
Microsoft.VisualStudio.ComponentGroup.ArchitectureTools.Managed | Architektury a analytické nástroje | 15.0.26208.0 | volitelná,
Microsoft.VisualStudio.ComponentGroup.Web | Vývoj pro ASP.NET a webové nástroje – požadavky | 15.9.28219.51 | volitelná,
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Vývoj pro ASP.NET a web | 15.8.27825.0 | volitelná,

## <a name="game-development-with-unity"></a>Vývoj her pomocí Unity

**ID:** Microsoft.VisualStudio.Workload.ManagedGame

**Popis:** vytvářejte 2D a 3D hry s Unity, výkonné multiplatformní vývojové prostředí.

### <a name="components-included-by-this-workload"></a>Pomocí této úlohy zahrnuté komponenty

ID součásti | Název | Version | Typ závislosti
--- | --- | --- | ---
Microsoft.Net.Component.3.5.DeveloperTools | Vývojové nástroje .NET framework 3.5 | 15.6.27406.0 | Požadováno
Microsoft.Net.Component.4.7.1.TargetingPack | Rozhraní .NET framework 4.7.1 targeting pack | 15.6.27406.0 | Požadováno
Microsoft.VisualStudio.Component.NuGet | Správce balíčků NuGet | 15.9.28016.0 | Požadováno
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilátory C# a Visual Basic Roslyn | 15.6.27309.0 | Požadováno
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# a Visual Basic | 15.8.27729.1 | Požadováno
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Nástroje statické analýzy | 15.0.26208.0 | Požadováno
Microsoft.VisualStudio.Component.Unity | Visual Studio Tools for Unity | 15.7.27617.1 | Požadováno
Component.UnityEngine.x64 | 64bitový Editor Unity 2018.1 | 15.8.27924.0 | Doporučeno
Component.UnityEngine.x86 | 32bitový Editor Unity 5.6 | 15.6.27406.0 | Doporučeno

## <a name="linux-development-with-c"></a>Vývoj pro Linux v C++

**ID:** Microsoft.VisualStudio.Workload.NativeCrossPlat

**Popis:** vytváření a ladění aplikace běžící v prostředí Linux.

### <a name="components-included-by-this-workload"></a>Pomocí této úlohy zahrnuté komponenty

ID součásti | Název | Version | Typ závislosti
--- | --- | --- | ---
Component.MDD.Linux | Visual C++ for Linux Development | 15.6.27406.0 | Požadováno
Microsoft.VisualStudio.Component.VC.CoreIde | Visual Studio C++ – základní funkce | 15.6.27406.0 | Požadováno
Microsoft.VisualStudio.Component.Windows10SDK | Windows Universal C Runtime | 15.6.27406.0 | Požadováno
Component.Linux.CMake | Nástroje Visual C++ pro CMake a Linux | 15.8.27906.1 | Doporučeno
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Nástroje statické analýzy | 15.0.26208.0 | Doporučeno
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | VC ++ 2017 verze 15.9 v14.16 nejnovější nástroje v141 pro | 15.9.28230.55 | Doporučeno
Microsoft.VisualStudio.Component.Windows10SDK.17134 | Windows 10 SDK (10.0.17134.0) | 15.8.27924.0 | Doporučeno
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Vývoj pro ASP.NET a web | 15.8.27825.0 | Doporučeno
Component.MDD.Linux.GCC.arm | Vložené a IoT vývoj | 15.6.27309.0 | volitelná,

## <a name="desktop-development-with-c"></a>Vývoj desktopových aplikací pomocí C++

**ID:** Microsoft.VisualStudio.Workload.NativeDesktop

**Popis:** vytváření aplikací klasické pracovní plochy Windows pomocí sady nástrojů Microsoft C++, ATL nebo MFC.

### <a name="components-included-by-this-workload"></a>Pomocí této úlohy zahrnuté komponenty

ID součásti | Název | Version | Typ závislosti
--- | --- | --- | ---
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | Požadováno
Microsoft.VisualStudio.Component.ClassDesigner | Návrhář tříd | 15.0.26208.0 | Požadováno
Microsoft.VisualStudio.Component.CodeMap | Mapa kódu | 15.0.26208.0 | Požadováno
Microsoft.VisualStudio.Component.GraphDocument | DGML editor | 15.0.27005.2 | Požadováno
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilátory C# a Visual Basic Roslyn | 15.6.27309.0 | Požadováno
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 15.7.27617.1 | Požadováno
Microsoft.VisualStudio.Component.SQL.NCLI | Nativní klient systému SQL Server | 15.0.26208.0 | Požadováno
Microsoft.VisualStudio.Component.TextTemplating | Transformace textové šablony | 15.0.26208.0 | Požadováno
Microsoft.VisualStudio.Component.VC.CoreIde | Visual Studio C++ – základní funkce | 15.6.27406.0 | Požadováno
Microsoft.VisualStudio.Component.VC.Redist.14.Latest | Distribuovatelné součásti Visual C++ 2017 Update | 15.6.27406.0 | Požadováno
Microsoft.VisualStudio.ComponentGroup.ArchitectureTools.Native | Nástroje pro architekturu pro C++ | 15.0.26208.0 | Požadováno
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Core | Visual C++ – základní desktopové funkce | 15.8.27729.1 | Požadováno
Microsoft.VisualStudio.Component.Debugger.JustInTime | Just-In-Time debugger | 15.0.27005.2 | Doporučeno
Microsoft.VisualStudio.Component.Graphics.Tools | Ladicí program grafiky a profiler GPU pro DirectX | 15.6.27406.0 | Doporučeno
Microsoft.VisualStudio.Component.Graphics.Win81 | Grafické nástroje systému Windows 8.1 SDK | 15.6.27406.0 | Doporučeno
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | 15.8.27729.1 | Doporučeno
Microsoft.VisualStudio.Component.NuGet | Správce balíčků NuGet | 15.9.28016.0 | Doporučeno
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Nástroje statické analýzy | 15.0.26208.0 | Doporučeno
Microsoft.VisualStudio.Component.VC.ATL | Visual C++ ATL pro x86 a x64 | 15.7.27625.0 | Doporučeno
Microsoft.VisualStudio.Component.VC.CMake.Project | Nástroje Visual C++ pro CMake | 15.8.27906.1 | Doporučeno
Microsoft.VisualStudio.Component.VC.DiagnosticTools | Nástroje pro profilaci v C++ | 15.0.26823.1 | Doporučeno
Microsoft.VisualStudio.Component.VC.TestAdapterForBoostTest | Testovací adaptér pro Boost.Test | 15.8.27906.1 | Doporučeno
Microsoft.VisualStudio.Component.VC.TestAdapterForGoogleTest | Testovací adaptér pro Google Test | 15.8.27906.1 | Doporučeno
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | VC ++ 2017 verze 15.9 v14.16 nejnovější nástroje v141 pro | 15.9.28230.55 | Doporučeno
Microsoft.VisualStudio.Component.Windows10SDK.17134 | Windows 10 SDK (10.0.17134.0) | 15.8.27924.0 | Doporučeno
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Vývoj pro ASP.NET a web | 15.8.27825.0 | Doporučeno
Component.Incredibuild | IncrediBuild – urychlení sestavení | 15.7.27617.1 | volitelná,
Component.IncredibuildMenu | IncrediBuildMenu | 1.5.0.2 | volitelná,
Microsoft.Component.VC.Runtime.UCRTSDK | Windows Universal CRT SDK | 15.6.27309.0 | volitelná,
Microsoft.Net.Component.4.6.1.SDK | Rozhraní .NET framework 4.6.1 SDK | 15.6.27406.0 | volitelná,
Microsoft.Net.Component.4.6.1.TargetingPack | Rozhraní .NET framework 4.6.1 targeting pack | 15.6.27406.0 | volitelná,
Microsoft.VisualStudio.Component.VC.140 | Nástrojů VC ++ 2015.3 v14.00 (v140) pro desktop | 15.7.27617.1 | volitelná,
Microsoft.VisualStudio.Component.VC.ATLMFC | Visual C++ MFC pro x86 a x64 | 15.7.27625.0 | volitelná,
Microsoft.VisualStudio.Component.VC.CLI.Support | C + +/ CLI podpory | 15.6.27309.0 | volitelná,
Microsoft.VisualStudio.Component.VC.Modules.x86.x64 | Moduly pro standardní knihovnu (experimentální) | 15.6.27309.0 | volitelná,
Microsoft.VisualStudio.Component.Windows10SDK.10240 | Windows 10 SDK (10.0.10240.0) | 15.6.27406.0 | volitelná,
Microsoft.VisualStudio.Component.Windows10SDK.10586 | Windows 10 SDK (10.0.10586.0) | 15.6.27406.0 | volitelná,
Microsoft.VisualStudio.Component.Windows10SDK.14393 | Windows 10 SDK (10.0.14393.0) | 15.6.27406.0 | volitelná,
Microsoft.VisualStudio.Component.Windows10SDK.15063.Desktop | Windows 10 SDK (10.0.15063.0) pro Desktop C++ [x86 a x64] | 15.6.27406.0 | volitelná,
Microsoft.VisualStudio.Component.Windows10SDK.15063.UWP | Windows 10 SDK (10.0.15063.0) pro UPW: C#, VB, JS | 15.6.27406.0 | volitelná,
Microsoft.VisualStudio.Component.Windows10SDK.15063.UWP.Native | Windows 10 SDK (10.0.15063.0) pro UPW: C++ | 15.6.27406.0 | volitelná,
Microsoft.VisualStudio.Component.Windows10SDK.16299.Desktop | Windows 10 SDK (10.0.16299.0) pro Desktop C++ [x86 a x64] | 15.6.27406.0 | volitelná,
Microsoft.VisualStudio.Component.Windows10SDK.16299.Desktop.arm | Windows 10 SDK (10.0.16299.0) pro Desktop C++ [ARM a ARM64] | 15.6.27406.0 | volitelná,
Microsoft.VisualStudio.Component.Windows10SDK.16299.UWP | Windows 10 SDK (10.0.16299.0) pro UPW: C#, VB, JS | 15.6.27406.0 | volitelná,
Microsoft.VisualStudio.Component.Windows10SDK.16299.UWP.Native | Windows 10 SDK (10.0.16299.0) pro UPW: C++ | 15.6.27406.0 | volitelná,
Microsoft.VisualStudio.Component.Windows81SDK | Windows 8.1 SDK | 15.6.27406.0 | volitelná,
Microsoft.VisualStudio.Component.WinXP | Podpora Windows XP pro C++ | 15.8.27924.0 | volitelná,
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Win81 | Windows 8.1 SDK a UCRT SDK | 15.6.27406.0 | volitelná,
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.WinXP | Podpora Windows XP pro C++ | 15.8.27705.0 | volitelná,
Microsoft.VisualStudio.ComponentGroup.Windows10SDK.15063 | Windows 10 SDK (10.0.15063.0) | 15.8.27825.0 | volitelná,
Microsoft.VisualStudio.ComponentGroup.Windows10SDK.16299 | Windows 10 SDK (10.0.16299.0) | 15.8.27825.0 | volitelná,

## <a name="game-development-with-c"></a>Vývoj her v C++

**ID:** Microsoft.VisualStudio.Workload.NativeGame

**Popis:** využijte naplno potenciál C++ k vytváření profesionálních her využívajících technologii DirectX, Unreal nebo Cocos2d.

### <a name="components-included-by-this-workload"></a>Pomocí této úlohy zahrnuté komponenty

ID součásti | Název | Version | Typ závislosti
--- | --- | --- | ---
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Nástroje statické analýzy | 15.0.26208.0 | Požadováno
Microsoft.VisualStudio.Component.VC.CoreIde | Visual Studio C++ – základní funkce | 15.6.27406.0 | Požadováno
Microsoft.VisualStudio.Component.VC.Redist.14.Latest | Distribuovatelné součásti Visual C++ 2017 Update | 15.6.27406.0 | Požadováno
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | VC ++ 2017 verze 15.9 v14.16 nejnovější nástroje v141 pro | 15.9.28230.55 | Požadováno
Microsoft.VisualStudio.Component.Windows10SDK | Windows Universal C Runtime | 15.6.27406.0 | Požadováno
Microsoft.VisualStudio.Component.Graphics.Tools | Ladicí program grafiky a profiler GPU pro DirectX | 15.6.27406.0 | Doporučeno
Microsoft.VisualStudio.Component.Graphics.Win81 | Grafické nástroje systému Windows 8.1 SDK | 15.6.27406.0 | Doporučeno
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | 15.8.27729.1 | Doporučeno
Microsoft.VisualStudio.Component.VC.DiagnosticTools | Nástroje pro profilaci v C++ | 15.0.26823.1 | Doporučeno
Microsoft.VisualStudio.Component.Windows10SDK.17134 | Windows 10 SDK (10.0.17134.0) | 15.8.27924.0 | Doporučeno
Component.Android.NDK.R12B | Sada Android NDK (R12B) | 12.1.10 | volitelná,
Component.Android.SDK23.Private | Instalace sady Android SDK (úroveň rozhraní API 23) (místní instalace pro vývoj pro mobilní zařízení pomocí JavaScriptu nebo C++) | 15.9.28016.0 | volitelná,
Component.Ant | Apache Ant (1.9.3) | 1.9.3.8 | volitelná,
Component.Cocos | Cocos | 15.0.26906.1 | volitelná,
Component.Incredibuild | IncrediBuild – urychlení sestavení | 15.7.27617.1 | volitelná,
Component.IncredibuildMenu | IncrediBuildMenu | 1.5.0.2 | volitelná,
Component.JavaJDK | Java SE Development Kit (8.0.1120.15) | 15.6.27406.0 | volitelná,
Component.MDD.Android | Vývojové nástroje C++ pro Android | 15.0.26606.0 | volitelná,
Component.OpenJDK | OpenJDK je distribuce Microsoftu | 15.9.28125.51 | volitelná,
Component.Unreal | Instalační program Unreal Engine | 15.8.27729.1 | volitelná,
Component.Unreal.Android | Podpora pro Unreal Engine Visual Studio pro Android | 15.0.27005.2 | volitelná,
Microsoft.Component.VC.Runtime.UCRTSDK | Windows Universal CRT SDK | 15.6.27309.0 | volitelná,
Microsoft.Net.Component.4.5.1.TargetingPack | Rozhraní .NET framework 4.5.1 targeting pack | 15.6.27406.0 | volitelná,
Microsoft.Net.Component.4.5.2.TargetingPack | Rozhraní .NET framework 4.5.2 targeting pack | 15.6.27406.0 | volitelná,
Microsoft.Net.Component.4.5.TargetingPack | .NET framework 4.5 targeting pack | 15.6.27406.0 | volitelná,
Microsoft.Net.Component.4.6.1.SDK | Rozhraní .NET framework 4.6.1 SDK | 15.6.27406.0 | volitelná,
Microsoft.Net.Component.4.6.1.TargetingPack | Rozhraní .NET framework 4.6.1 targeting pack | 15.6.27406.0 | volitelná,
Microsoft.Net.Component.4.6.TargetingPack | .NET framework 4.6 targeting pack | 15.6.27406.0 | volitelná,
Microsoft.Net.Component.4.TargetingPack | .NET framework 4 targeting pack | 15.6.27406.0 | volitelná,
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Vývojové nástroje .NET framework 4.6.1 | 15.8.27825.0 | volitelná,
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Vývojové nástroje .NET framework 4 – 4.6 | 15.6.27406.0 | volitelná,
Microsoft.VisualStudio.Component.NuGet.BuildTools | NuGet cíle a úlohy sestavení | 15.9.28016.0 | volitelná,
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilátory C# a Visual Basic Roslyn | 15.6.27309.0 | volitelná,
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# a Visual Basic | 15.8.27729.1 | volitelná,
Microsoft.VisualStudio.Component.Windows10SDK.10240 | Windows 10 SDK (10.0.10240.0) | 15.6.27406.0 | volitelná,
Microsoft.VisualStudio.Component.Windows10SDK.10586 | Windows 10 SDK (10.0.10586.0) | 15.6.27406.0 | volitelná,
Microsoft.VisualStudio.Component.Windows10SDK.14393 | Windows 10 SDK (10.0.14393.0) | 15.6.27406.0 | volitelná,
Microsoft.VisualStudio.Component.Windows10SDK.15063.Desktop | Windows 10 SDK (10.0.15063.0) pro Desktop C++ [x86 a x64] | 15.6.27406.0 | volitelná,
Microsoft.VisualStudio.Component.Windows10SDK.15063.UWP | Windows 10 SDK (10.0.15063.0) pro UPW: C#, VB, JS | 15.6.27406.0 | volitelná,
Microsoft.VisualStudio.Component.Windows10SDK.15063.UWP.Native | Windows 10 SDK (10.0.15063.0) pro UPW: C++ | 15.6.27406.0 | volitelná,
Microsoft.VisualStudio.Component.Windows10SDK.16299.Desktop | Windows 10 SDK (10.0.16299.0) pro Desktop C++ [x86 a x64] | 15.6.27406.0 | volitelná,
Microsoft.VisualStudio.Component.Windows10SDK.16299.Desktop.arm | Windows 10 SDK (10.0.16299.0) pro Desktop C++ [ARM a ARM64] | 15.6.27406.0 | volitelná,
Microsoft.VisualStudio.Component.Windows10SDK.16299.UWP | Windows 10 SDK (10.0.16299.0) pro UPW: C#, VB, JS | 15.6.27406.0 | volitelná,
Microsoft.VisualStudio.Component.Windows10SDK.16299.UWP.Native | Windows 10 SDK (10.0.16299.0) pro UPW: C++ | 15.6.27406.0 | volitelná,
Microsoft.VisualStudio.Component.Windows81SDK | Windows 8.1 SDK | 15.6.27406.0 | volitelná,
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Win81 | Windows 8.1 SDK a UCRT SDK | 15.6.27406.0 | volitelná,
Microsoft.VisualStudio.ComponentGroup.Windows10SDK.15063 | Windows 10 SDK (10.0.15063.0) | 15.8.27825.0 | volitelná,
Microsoft.VisualStudio.ComponentGroup.Windows10SDK.16299 | Windows 10 SDK (10.0.16299.0) | 15.8.27825.0 | volitelná,

## <a name="mobile-development-with-c"></a>Vývoj mobilních aplikací pomocí C++

**ID:** Microsoft.VisualStudio.Workload.NativeMobile

**Popis:** vytvářet multiplatformní aplikace pro iOS, Android nebo Windows pomocí C++.

### <a name="components-included-by-this-workload"></a>Pomocí této úlohy zahrnuté komponenty

ID součásti | Název | Version | Typ závislosti
--- | --- | --- | ---
Component.Android.SDK19.Private | Instalace sady Android SDK (úroveň rozhraní API 19) (místní instalace pro vývoj pro mobilní zařízení pomocí JavaScriptu nebo C++) | 15.9.28107.0 | Požadováno
Component.Android.SDK21.Private | Instalace sady Android SDK (úroveň rozhraní API 21) (místní instalace pro vývoj pro mobilní zařízení pomocí JavaScriptu nebo C++) | 15.9.28016.0 | Požadováno
Component.Android.SDK22.Private | Instalace sady Android SDK (úroveň rozhraní API 22) (místní instalace pro vývoj pro mobilní zařízení pomocí JavaScriptu nebo C++) | 15.9.28016.0 | Požadováno
Component.Android.SDK23.Private | Instalace sady Android SDK (úroveň rozhraní API 23) (místní instalace pro vývoj pro mobilní zařízení pomocí JavaScriptu nebo C++) | 15.9.28016.0 | Požadováno
Component.Android.SDK25.Private | Instalace sady Android SDK (úroveň rozhraní API 25) (místní instalace pro vývoj pro mobilní zařízení pomocí JavaScriptu nebo C++) | 15.9.28016.0 | Požadováno
Component.OpenJDK | OpenJDK je distribuce Microsoftu | 15.9.28125.51 | Požadováno
Microsoft.VisualStudio.Component.VC.CoreIde | Visual Studio C++ – základní funkce | 15.6.27406.0 | Požadováno
Component.Android.NDK.R15C | Sada Android NDK (R15C) | 15.2.1 | Doporučeno
Component.Ant | Apache Ant (1.9.3) | 1.9.3.8 | Doporučeno
Component.MDD.Android | Vývojové nástroje C++ pro Android | 15.0.26606.0 | Doporučeno
Component.Android.NDK.R12B | Sada Android NDK (R12B) | 12.1.10 | volitelná,
Component.Android.NDK.R12B_3264 | Sada Android NDK (R12B) (32 bitů) | 12.1.11 | volitelná,
Component.Android.NDK.R13B | Sada Android NDK (R13B) | 13.1.7 | volitelná,
Component.Android.NDK.R13B_3264 | Sada Android NDK (R13B) (32 bitů) | 13.1.8 | volitelná,
Component.Android.NDK.R15C_3264 | Sada Android NDK (R15C) (32 bitů) | 15.2.1 | volitelná,
Component.Google.Android.Emulator.API23.Private | Emulátor Google Android (úroveň rozhraní API 23) (místní instalace) | 15.6.27413.0 | volitelná,
Component.HAXM.Private | Intel Hardware Accelerated provádění Manager (HAXM) (místní instalace) | 15.6.27413.0 | volitelná,
Component.Incredibuild | IncrediBuild – urychlení sestavení | 15.7.27617.1 | volitelná,
Component.IncredibuildMenu | IncrediBuildMenu | 1.5.0.2 | volitelná,
Component.MDD.IOS | Nástroje pro vývoj iOS C++ | 15.0.26621.2 | volitelná,

## <a name="net-core-cross-platform-development"></a>Vývoj pro různé platformy .NET core

**ID:** Microsoft.VisualStudio.Workload.NetCoreTools

**Popis:** umožňuje sestavovat multiplatformní aplikace pomocí .NET Core, ASP.NET Core, HTML/JavaScript a kontejnerů včetně podpory Dockeru.

### <a name="components-included-by-this-workload"></a>Pomocí této úlohy zahrnuté komponenty

ID součásti | Název | Version | Typ závislosti
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Jazykové služby Razor | 15.0.26720.2 | Požadováno
Component.Microsoft.Web.LibraryManager | Správce knihovny | 15.8.27705.0 | Požadováno
Component.WebSocket | WebSocket4Net | 15.0.26606.0 | Požadováno
Microsoft.Component.ClickOnce | Publikování ClickOnce | 15.8.27825.0 | Požadováno
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | Požadováno
Microsoft.Net.Component.4.5.2.TargetingPack | Rozhraní .NET framework 4.5.2 targeting pack | 15.6.27406.0 | Požadováno
Microsoft.Net.Component.4.5.TargetingPack | .NET framework 4.5 targeting pack | 15.6.27406.0 | Požadováno
Microsoft.Net.Component.4.6.1.SDK | Rozhraní .NET framework 4.6.1 SDK | 15.6.27406.0 | Požadováno
Microsoft.Net.Component.4.6.1.TargetingPack | Rozhraní .NET framework 4.6.1 targeting pack | 15.6.27406.0 | Požadováno
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Vývojové nástroje .NET framework 4.6.1 | 15.8.27825.0 | Požadováno
Microsoft.Net.Core.Component.SDK.2.1 | Vývojové nástroje .NET core 2.1 | 15.8.27924.0 | Požadováno
Microsoft.NetCore.ComponentGroup.DevelopmentTools.2.1 | Vývojové nástroje .NET core 2.1 | 15.8.27924.0 | Požadováno
Microsoft.NetCore.ComponentGroup.Web.2.1 | Vývojové nástroje .NET core 2.1 | 15.8.27924.0 | Požadováno
Microsoft.VisualStudio.Component.Common.Azure.Tools | Nástroje pro připojení a publikování | 15.9.28107.0 | Požadováno
Microsoft.VisualStudio.Component.DockerTools | Kontejnerové vývojové nástroje | 15.8.27906.1 | Požadováno
Microsoft.VisualStudio.Component.DockerTools.BuildTools | Kontejnerové vývojové nástroje – Build Tools | 15.7.27617.1 | Požadováno
Microsoft.VisualStudio.Component.FSharp | F#podpora jazyků | 15.8.27825.0 | Požadováno
Microsoft.VisualStudio.Component.FSharp.WebTemplates | F#podpora jazyků pro webové projekty | 15.8.27705.0 | Požadováno
Microsoft.VisualStudio.Component.IISExpress | Služba IIS Express  | 15.0.26208.0 | Požadováno
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostika jazyka JavaScript | 15.8.27729.1 | Požadováno
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Podpora jazyků JavaScript a TypeScript | 15.9.28125.51 | Požadováno
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Základní spravovaný úloze vývoje desktopových aplikací | 15.8.27729.1 | Požadováno
Microsoft.VisualStudio.Component.NuGet | Správce balíčků NuGet | 15.9.28016.0 | Požadováno
Microsoft.VisualStudio.Component.PortableLibrary | .NET portable Library targeting pack | 15.6.27309.0 | Požadováno
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilátory C# a Visual Basic Roslyn | 15.6.27309.0 | Požadováno
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# a Visual Basic | 15.8.27729.1 | Požadováno
Microsoft.VisualStudio.Component.SQL.ADAL | SQL ADAL runtime | 15.6.27406.0 | Požadováno
Microsoft.VisualStudio.Component.SQL.CLR | Datové typy CLR pro SQL Server | 15.0.26208.0 | Požadováno
Microsoft.VisualStudio.Component.SQL.CMDUtils | Nástroje příkazového řádku SQL serveru | 15.0.26208.0 | Požadováno
Microsoft.VisualStudio.Component.SQL.DataSources | Zdroje dat pro podporu SQL serveru | 15.0.26621.2 | Požadováno
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 15.7.27617.1 | Požadováno
Microsoft.VisualStudio.Component.SQL.NCLI | Nativní klient systému SQL Server | 15.0.26208.0 | Požadováno
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 15.9.28107.0 | Požadováno
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Nástroje statické analýzy | 15.0.26208.0 | Požadováno
Microsoft.VisualStudio.Component.TextTemplating | Transformace textové šablony | 15.0.26208.0 | Požadováno
Microsoft.VisualStudio.Component.TypeScript.3.1 | TypeScript 3.1 SDK | 15.0.28218.60 | Požadováno
Microsoft.VisualStudio.Component.VisualStudioData | Zdroje dat a odkazy na služby | 15.6.27406.0 | Požadováno
Microsoft.VisualStudio.ComponentGroup.Web | Vývoj pro ASP.NET a webové nástroje – požadavky | 15.9.28219.51 | Požadováno
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Vývoj pro ASP.NET a web | 15.8.27825.0 | Požadováno
Component.Microsoft.VisualStudio.Web.AzureFunctions | Nástroje Microsoft Azure WebJobs | 15.7.27617.1 | Doporučeno
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics tools | 15.8.27825.0 | Doporučeno
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Azure – nástroje pro tvorbu | 15.8.27825.0 | Doporučeno
Microsoft.VisualStudio.Component.Azure.ClientLibs | Knihovny Azure pro .NET | 15.0.26208.0 | Doporučeno
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Emulátor výpočtů v Azure | 15.0.26621.2 | Doporučeno
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Emulátor úložiště Azure | 15.9.28125.51 | Doporučeno
Microsoft.VisualStudio.Component.CloudExplorer | Průzkumník cloudu | 15.9.28230.55 | Doporučeno
Microsoft.VisualStudio.Component.Debugger.Snapshot | Snapshot Debugger | 15.8.28010.0 | Doporučeno
Microsoft.VisualStudio.Component.DiagnosticTools | Nástroje pro profilaci .NET | 15.8.27729.1 | Doporučeno
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | 15.8.27729.1 | Doporučeno
Microsoft.VisualStudio.Component.LiveUnitTesting | Live Unit Testing | 15.0.26720.2 | Doporučeno
Microsoft.VisualStudio.Component.Web | Nástroje pro vývoj pro ASP.NET a web | 15.8.27825.0 | Doporučeno
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 15.8.27729.1 | Doporučeno
Microsoft.VisualStudio.ComponentGroup.AzureFunctions | Nástroje Microsoft Azure WebJobs | 15.7.27617.1 | Doporučeno
Microsoft.VisualStudio.ComponentGroup.Web.CloudTools | Cloudové nástroje pro vývoj pro web | 15.8.27729.1 | Doporučeno
Microsoft.Net.Core.Component.SDK | Vývojové nástroje .NET core 2.0 | 15.6.27406.0 | volitelná,
Microsoft.Net.Core.Component.SDK.1x | .NET core 1.0 až 1.1. vývojové nástroje | 15.6.27406.0 | volitelná,
Microsoft.NetCore.1x.ComponentGroup.Web | .NET core 1.0 až 1.1 vývojářské nástroje pro Web | 15.6.27406.0 | volitelná,
Microsoft.NetCore.ComponentGroup.DevelopmentTools | Vývojové nástroje .NET core 2.0 | 15.8.27729.1 | volitelná,
Microsoft.NetCore.ComponentGroup.Web | Vývojové nástroje .NET core 2.0 | 15.7.27625.0 | volitelná,
Microsoft.VisualStudio.ComponentGroup.IISDevelopment | Podpora služby IIS při vývoji | 15.9.28219.51 | volitelná,

## <a name="mobile-development-with-net"></a>Vývoj mobilních aplikací pomocí .NET

**ID:** Microsoft.VisualStudio.Workload.NetCrossPlat

**Popis:** vytvářet multiplatformní aplikace pro iOS, Android nebo Windows pomocí Xamarinu.

### <a name="components-included-by-this-workload"></a>Pomocí této úlohy zahrnuté komponenty

ID součásti | Název | Version | Typ závislosti
--- | --- | --- | ---
Component.Xamarin | Xamarin | 15.8.27906.1 | Požadováno
Component.Xamarin.RemotedSimulator | Vzdálený simulátor Xamarin | 15.6.27323.2 | Požadováno
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | Požadováno
Microsoft.Net.Component.4.6.1.SDK | Rozhraní .NET framework 4.6.1 SDK | 15.6.27406.0 | Požadováno
Microsoft.Net.Component.4.6.1.TargetingPack | Rozhraní .NET framework 4.6.1 targeting pack | 15.6.27406.0 | Požadováno
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Vývojové nástroje .NET framework 4.6.1 | 15.8.27825.0 | Požadováno
Microsoft.Net.Core.Component.SDK | Vývojové nástroje .NET core 2.0 | 15.6.27406.0 | Požadováno
Microsoft.NetCore.ComponentGroup.DevelopmentTools | Vývojové nástroje .NET core 2.0 | 15.8.27729.1 | Požadováno
Microsoft.VisualStudio.Component.FSharp | F#podpora jazyků | 15.8.27825.0 | Požadováno
Microsoft.VisualStudio.Component.Merq | Společné interní nástroje Xamarin | 15.8.27924.0 | Požadováno
Microsoft.VisualStudio.Component.MonoDebugger | Ladicí program mono | 15.0.26720.2 | Požadováno
Microsoft.VisualStudio.Component.NuGet | Správce balíčků NuGet | 15.9.28016.0 | Požadováno
Microsoft.VisualStudio.Component.PortableLibrary | .NET portable Library targeting pack | 15.6.27309.0 | Požadováno
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilátory C# a Visual Basic Roslyn | 15.6.27309.0 | Požadováno
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# a Visual Basic | 15.8.27729.1 | Požadováno
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Nástroje statické analýzy | 15.0.26208.0 | Požadováno
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions.TemplateEngine | Modul šablon ASP.NET | 15.8.27729.1 | Požadováno
Component.Android.SDK27 | Instalace sady Android SDK (úroveň rozhraní API 27) | 15.9.28016.0 | Doporučeno
Component.Google.Android.Emulator.API27 | Emulátor Google Android (úroveň rozhraní API 27) | 15.9.28016.0 | Doporučeno
Component.HAXM | Intel Hardware Accelerated provádění Manager (HAXM) (globální instalace) | 15.6.27413.0 | Doporučeno
Component.OpenJDK | OpenJDK je distribuce Microsoftu | 15.9.28125.51 | Doporučeno
Component.Xamarin.Profiler | Xamarin Profiler | 15.0.27005.2 | Doporučeno
Component.Xamarin.Inspector | Sešity ke Xamarinu | 15.0.26606.0 | volitelná,
Microsoft.Component.ClickOnce | Publikování ClickOnce | 15.8.27825.0 | volitelná,
Microsoft.Component.NetFX.Native | .NET Native | 15.0.26208.0 | volitelná,
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics tools | 15.8.27825.0 | volitelná,
Microsoft.VisualStudio.Component.CodeClone | Klonování kódu | 15.0.26208.0 | volitelná,
Microsoft.VisualStudio.Component.CodeMap | Mapa kódu | 15.0.26208.0 | volitelná,
Microsoft.VisualStudio.Component.DependencyValidation.Enterprise | Živé ověření závislosti | 15.0.26208.0 | volitelná,
Microsoft.VisualStudio.Component.DiagnosticTools | Nástroje pro profilaci .NET | 15.8.27729.1 | volitelná,
Microsoft.VisualStudio.Component.GraphDocument | DGML editor | 15.0.27005.2 | volitelná,
Microsoft.VisualStudio.Component.Graphics | Editory obrázků a 3D modelu | 15.6.27406.0 | volitelná,
Microsoft.VisualStudio.Component.SQL.CLR | Datové typy CLR pro SQL Server | 15.0.26208.0 | volitelná,
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 15.7.27617.1 | volitelná,
Microsoft.VisualStudio.Component.SQL.NCLI | Nativní klient systému SQL Server | 15.0.26208.0 | volitelná,
Microsoft.VisualStudio.Component.VisualStudioData | Zdroje dat a odkazy na služby | 15.6.27406.0 | volitelná,
Microsoft.VisualStudio.Component.Windows10SDK.17134 | Windows 10 SDK (10.0.17134.0) | 15.8.27924.0 | volitelná,
Microsoft.VisualStudio.ComponentGroup.ArchitectureTools.Managed | Architektury a analytické nástroje | 15.0.26208.0 | volitelná,
Microsoft.VisualStudio.ComponentGroup.UWP.Xamarin | Nástroje pro univerzální platformu Windows pro Xamarin | 15.7.27617.1 | volitelná,

## <a name="aspnet-and-web-development"></a>Vývoj pro ASP.NET a web

**ID:** Microsoft.VisualStudio.Workload.NetWeb

**Popis:** sestavovat webové aplikace pomocí ASP.NET, ASP.NET Core, HTML/JavaScript a kontejnerů včetně podpory Dockeru.

### <a name="components-included-by-this-workload"></a>Pomocí této úlohy zahrnuté komponenty

ID součásti | Název | Version | Typ závislosti
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Jazykové služby Razor | 15.0.26720.2 | Požadováno
Component.Microsoft.Web.LibraryManager | Správce knihovny | 15.8.27705.0 | Požadováno
Component.WebSocket | WebSocket4Net | 15.0.26606.0 | Požadováno
Microsoft.Component.ClickOnce | Publikování ClickOnce | 15.8.27825.0 | Požadováno
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | Požadováno
Microsoft.Net.Component.4.5.2.TargetingPack | Rozhraní .NET framework 4.5.2 targeting pack | 15.6.27406.0 | Požadováno
Microsoft.Net.Component.4.5.TargetingPack | .NET framework 4.5 targeting pack | 15.6.27406.0 | Požadováno
Microsoft.Net.Component.4.6.1.SDK | Rozhraní .NET framework 4.6.1 SDK | 15.6.27406.0 | Požadováno
Microsoft.Net.Component.4.6.1.TargetingPack | Rozhraní .NET framework 4.6.1 targeting pack | 15.6.27406.0 | Požadováno
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Vývojové nástroje .NET framework 4.6.1 | 15.8.27825.0 | Požadováno
Microsoft.Net.Core.Component.SDK.2.1 | Vývojové nástroje .NET core 2.1 | 15.8.27924.0 | Požadováno
Microsoft.NetCore.ComponentGroup.DevelopmentTools.2.1 | Vývojové nástroje .NET core 2.1 | 15.8.27924.0 | Požadováno
Microsoft.NetCore.ComponentGroup.Web.2.1 | Vývojové nástroje .NET core 2.1 | 15.8.27924.0 | Požadováno
Microsoft.VisualStudio.Component.Common.Azure.Tools | Nástroje pro připojení a publikování | 15.9.28107.0 | Požadováno
Microsoft.VisualStudio.Component.DockerTools | Kontejnerové vývojové nástroje | 15.8.27906.1 | Požadováno
Microsoft.VisualStudio.Component.DockerTools.BuildTools | Kontejnerové vývojové nástroje – Build Tools | 15.7.27617.1 | Požadováno
Microsoft.VisualStudio.Component.FSharp | F#podpora jazyků | 15.8.27825.0 | Požadováno
Microsoft.VisualStudio.Component.FSharp.WebTemplates | F#podpora jazyků pro webové projekty | 15.8.27705.0 | Požadováno
Microsoft.VisualStudio.Component.IISExpress | Služba IIS Express  | 15.0.26208.0 | Požadováno
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostika jazyka JavaScript | 15.8.27729.1 | Požadováno
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Podpora jazyků JavaScript a TypeScript | 15.9.28125.51 | Požadováno
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Základní spravovaný úloze vývoje desktopových aplikací | 15.8.27729.1 | Požadováno
Microsoft.VisualStudio.Component.NuGet | Správce balíčků NuGet | 15.9.28016.0 | Požadováno
Microsoft.VisualStudio.Component.PortableLibrary | .NET portable Library targeting pack | 15.6.27309.0 | Požadováno
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilátory C# a Visual Basic Roslyn | 15.6.27309.0 | Požadováno
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# a Visual Basic | 15.8.27729.1 | Požadováno
Microsoft.VisualStudio.Component.SQL.ADAL | SQL ADAL runtime | 15.6.27406.0 | Požadováno
Microsoft.VisualStudio.Component.SQL.CLR | Datové typy CLR pro SQL Server | 15.0.26208.0 | Požadováno
Microsoft.VisualStudio.Component.SQL.CMDUtils | Nástroje příkazového řádku SQL serveru | 15.0.26208.0 | Požadováno
Microsoft.VisualStudio.Component.SQL.DataSources | Zdroje dat pro podporu SQL serveru | 15.0.26621.2 | Požadováno
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 15.7.27617.1 | Požadováno
Microsoft.VisualStudio.Component.SQL.NCLI | Nativní klient systému SQL Server | 15.0.26208.0 | Požadováno
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 15.9.28107.0 | Požadováno
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Nástroje statické analýzy | 15.0.26208.0 | Požadováno
Microsoft.VisualStudio.Component.TextTemplating | Transformace textové šablony | 15.0.26208.0 | Požadováno
Microsoft.VisualStudio.Component.TypeScript.3.1 | TypeScript 3.1 SDK | 15.0.28218.60 | Požadováno
Microsoft.VisualStudio.Component.VisualStudioData | Zdroje dat a odkazy na služby | 15.6.27406.0 | Požadováno
Microsoft.VisualStudio.Component.Web | Nástroje pro vývoj pro ASP.NET a web | 15.8.27825.0 | Požadováno
Microsoft.VisualStudio.ComponentGroup.Web | Vývoj pro ASP.NET a webové nástroje – požadavky | 15.9.28219.51 | Požadováno
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Vývoj pro ASP.NET a web | 15.8.27825.0 | Požadováno
Component.Microsoft.VisualStudio.Web.AzureFunctions | Nástroje Microsoft Azure WebJobs | 15.7.27617.1 | Doporučeno
Microsoft.Net.Component.4.5.1.TargetingPack | Rozhraní .NET framework 4.5.1 targeting pack | 15.6.27406.0 | Doporučeno
Microsoft.Net.Component.4.6.TargetingPack | .NET framework 4.6 targeting pack | 15.6.27406.0 | Doporučeno
Microsoft.Net.Component.4.TargetingPack | .NET framework 4 targeting pack | 15.6.27406.0 | Doporučeno
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Vývojové nástroje .NET framework 4 – 4.6 | 15.6.27406.0 | Doporučeno
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics tools | 15.8.27825.0 | Doporučeno
Microsoft.VisualStudio.Component.AspNet45 | Rozšířené funkce ASP.NET | 15.7.27625.0 | Doporučeno
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Azure – nástroje pro tvorbu | 15.8.27825.0 | Doporučeno
Microsoft.VisualStudio.Component.Azure.ClientLibs | Knihovny Azure pro .NET | 15.0.26208.0 | Doporučeno
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Emulátor výpočtů v Azure | 15.0.26621.2 | Doporučeno
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Emulátor úložiště Azure | 15.9.28125.51 | Doporučeno
Microsoft.VisualStudio.Component.CloudExplorer | Průzkumník cloudu | 15.9.28230.55 | Doporučeno
Microsoft.VisualStudio.Component.Debugger.Snapshot | Snapshot Debugger | 15.8.28010.0 | Doporučeno
Microsoft.VisualStudio.Component.DiagnosticTools | Nástroje pro profilaci .NET | 15.8.27729.1 | Doporučeno
Microsoft.VisualStudio.Component.EntityFramework | Entity Framework 6 tools | 15.6.27406.0 | Doporučeno
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | 15.8.27729.1 | Doporučeno
Microsoft.VisualStudio.Component.LiveUnitTesting | Live Unit Testing | 15.0.26720.2 | Doporučeno
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | 15.8.27924.0 | Doporučeno
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 15.8.27729.1 | Doporučeno
Microsoft.VisualStudio.ComponentGroup.AzureFunctions | Nástroje Microsoft Azure WebJobs | 15.7.27617.1 | Doporučeno
Microsoft.VisualStudio.ComponentGroup.Web.CloudTools | Cloudové nástroje pro vývoj pro web | 15.8.27729.1 | Doporučeno
Microsoft.Net.Component.4.6.2.SDK | Rozhraní .NET framework 4.6.2 SDK | 15.6.27406.0 | volitelná,
Microsoft.Net.Component.4.6.2.TargetingPack | Rozhraní .NET framework 4.6.2 targeting pack | 15.6.27406.0 | volitelná,
Microsoft.Net.Component.4.7.1.SDK | Rozhraní .NET framework 4.7.1 SDK | 15.6.27406.0 | volitelná,
Microsoft.Net.Component.4.7.1.TargetingPack | Rozhraní .NET framework 4.7.1 targeting pack | 15.6.27406.0 | volitelná,
Microsoft.Net.Component.4.7.2.SDK | Rozhraní .NET framework 4.7.2 SDK | 15.8.27825.0 | volitelná,
Microsoft.Net.Component.4.7.2.TargetingPack | Rozhraní .NET framework 4.7.2 targeting pack | 15.8.27825.0 | volitelná,
Microsoft.Net.Component.4.7.SDK | Rozhraní .NET framework 4.7 SDK | 15.6.27406.0 | volitelná,
Microsoft.Net.Component.4.7.TargetingPack | .NET framework 4.7 targeting pack | 15.6.27406.0 | volitelná,
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | Vývojové nástroje .NET framework 4.6.2 | 15.6.27406.0 | volitelná,
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | Vývojové nástroje .NET framework 4.7.1 | 15.6.27406.0 | volitelná,
Microsoft.Net.ComponentGroup.4.7.2.DeveloperTools | Vývojové nástroje .NET framework 4.7.2 | 15.8.27825.0 | volitelná,
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | Vývojové nástroje .NET framework 4.7 | 15.6.27406.0 | volitelná,
Microsoft.Net.Core.Component.SDK | Vývojové nástroje .NET core 2.0 | 15.6.27406.0 | volitelná,
Microsoft.Net.Core.Component.SDK.1x | .NET core 1.0 až 1.1. vývojové nástroje | 15.6.27406.0 | volitelná,
Microsoft.NetCore.1x.ComponentGroup.Web | .NET core 1.0 až 1.1 vývojářské nástroje pro Web | 15.6.27406.0 | volitelná,
Microsoft.NetCore.ComponentGroup.DevelopmentTools | Vývojové nástroje .NET core 2.0 | 15.8.27729.1 | volitelná,
Microsoft.NetCore.ComponentGroup.Web | Vývojové nástroje .NET core 2.0 | 15.7.27625.0 | volitelná,
Microsoft.VisualStudio.Component.CodeClone | Klonování kódu | 15.0.26208.0 | volitelná,
Microsoft.VisualStudio.Component.CodeMap | Mapa kódu | 15.0.26208.0 | volitelná,
Microsoft.VisualStudio.Component.DependencyValidation.Enterprise | Živé ověření závislosti | 15.0.26208.0 | volitelná,
Microsoft.VisualStudio.Component.GraphDocument | DGML editor | 15.0.27005.2 | volitelná,
Microsoft.VisualStudio.Component.TestTools.WebLoadTest | Výkonnosti webů a zátěžové testování nástroje | 15.8.27729.1 | volitelná,
Microsoft.VisualStudio.ComponentGroup.ArchitectureTools.Managed | Architektury a analytické nástroje | 15.0.26208.0 | volitelná,
Microsoft.VisualStudio.ComponentGroup.IISDevelopment | Podpora služby IIS při vývoji | 15.9.28219.51 | volitelná,
Microsoft.VisualStudio.Web.Mvc4.ComponentGroup | ASP.NET MVC 4 | 15.6.27406.0 | volitelná,

## <a name="nodejs-development"></a>Vývoj v Node.js

**ID:** Microsoft.VisualStudio.Workload.Node

**Popis:** sestavovat škálovatelné síťové aplikace využívající Node.js, asynchronního runtime JavaScriptu založený na událostech. 

### <a name="components-included-by-this-workload"></a>Pomocí této úlohy zahrnuté komponenty

ID součásti | Název | Version | Typ závislosti
--- | --- | --- | ---
Component.WebSocket | WebSocket4Net | 15.0.26606.0 | Požadováno
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostika jazyka JavaScript | 15.8.27729.1 | Požadováno
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Podpora jazyků JavaScript a TypeScript | 15.9.28125.51 | Požadováno
Microsoft.VisualStudio.Component.Node.Build | Podporu nástroje Node.js MSBuild | 15.8.27825.0 | Požadováno
Microsoft.VisualStudio.Component.Node.Tools | Podpora vývoje v Node.js | 15.8.27825.0 | Požadováno
Microsoft.VisualStudio.Component.NuGet | Správce balíčků NuGet | 15.9.28016.0 | Požadováno
Microsoft.VisualStudio.Component.TestTools.Core | Základní funkce testovacích nástrojů | 15.7.27520.0 | Požadováno
Microsoft.VisualStudio.Component.TypeScript.3.1 | TypeScript 3.1 SDK | 15.0.28218.60 | Požadováno
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Vývoj pro ASP.NET a web | 15.8.27825.0 | Požadováno
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 15.8.27729.1 | Doporučeno
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics tools | 15.8.27825.0 | volitelná,
Microsoft.VisualStudio.Component.Common.Azure.Tools | Nástroje pro připojení a publikování | 15.9.28107.0 | volitelná,
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Nástroje statické analýzy | 15.0.26208.0 | volitelná,
Microsoft.VisualStudio.Component.VC.CoreIde | Visual Studio C++ – základní funkce | 15.6.27406.0 | volitelná,
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | VC ++ 2017 verze 15.9 v14.16 nejnovější nástroje v141 pro | 15.9.28230.55 | volitelná,

## <a name="officesharepoint-development"></a>Vývoj pro Office/SharePoint

**ID:** Microsoft.VisualStudio.Workload.Office

**Popis:** doplňky vytvořit Office a SharePoint, řešení služby SharePoint a doplňky pro VSTO pomocí C#, VB a JavaScript.

### <a name="components-included-by-this-workload"></a>Pomocí této úlohy zahrnuté komponenty

ID součásti | Název | Version | Typ závislosti
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Jazykové služby Razor | 15.0.26720.2 | Požadováno
Component.Microsoft.Web.LibraryManager | Správce knihovny | 15.8.27705.0 | Požadováno
Component.WebSocket | WebSocket4Net | 15.0.26606.0 | Požadováno
Microsoft.Component.ClickOnce | Publikování ClickOnce | 15.8.27825.0 | Požadováno
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | Požadováno
Microsoft.Net.Component.4.5.2.TargetingPack | Rozhraní .NET framework 4.5.2 targeting pack | 15.6.27406.0 | Požadováno
Microsoft.Net.Component.4.5.TargetingPack | .NET framework 4.5 targeting pack | 15.6.27406.0 | Požadováno
Microsoft.Net.Component.4.6.1.SDK | Rozhraní .NET framework 4.6.1 SDK | 15.6.27406.0 | Požadováno
Microsoft.Net.Component.4.6.1.TargetingPack | Rozhraní .NET framework 4.6.1 targeting pack | 15.6.27406.0 | Požadováno
Microsoft.Net.Component.4.TargetingPack | .NET framework 4 targeting pack | 15.6.27406.0 | Požadováno
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Vývojové nástroje .NET framework 4.6.1 | 15.8.27825.0 | Požadováno
Microsoft.Net.Core.Component.SDK.2.1 | Vývojové nástroje .NET core 2.1 | 15.8.27924.0 | Požadováno
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics tools | 15.8.27825.0 | Požadováno
Microsoft.VisualStudio.Component.Common.Azure.Tools | Nástroje pro připojení a publikování | 15.9.28107.0 | Požadováno
Microsoft.VisualStudio.Component.DockerTools | Kontejnerové vývojové nástroje | 15.8.27906.1 | Požadováno
Microsoft.VisualStudio.Component.DockerTools.BuildTools | Kontejnerové vývojové nástroje – Build Tools | 15.7.27617.1 | Požadováno
Microsoft.VisualStudio.Component.IISExpress | Služba IIS Express  | 15.0.26208.0 | Požadováno
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostika jazyka JavaScript | 15.8.27729.1 | Požadováno
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Podpora jazyků JavaScript a TypeScript | 15.9.28125.51 | Požadováno
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Základní spravovaný úloze vývoje desktopových aplikací | 15.8.27729.1 | Požadováno
Microsoft.VisualStudio.Component.ManagedDesktop.Prerequisites | Nástroje pro vývoj desktopových aplikací .NET | 15.7.27625.0 | Požadováno
Microsoft.VisualStudio.Component.NuGet | Správce balíčků NuGet | 15.9.28016.0 | Požadováno
Microsoft.VisualStudio.Component.PortableLibrary | .NET portable Library targeting pack | 15.6.27309.0 | Požadováno
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilátory C# a Visual Basic Roslyn | 15.6.27309.0 | Požadováno
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# a Visual Basic | 15.8.27729.1 | Požadováno
Microsoft.VisualStudio.Component.Sharepoint.Tools | Office Developer Tools for Visual Studio | 15.8.27924.0 | Požadováno
Microsoft.VisualStudio.Component.SQL.ADAL | SQL ADAL runtime | 15.6.27406.0 | Požadováno
Microsoft.VisualStudio.Component.SQL.CLR | Datové typy CLR pro SQL Server | 15.0.26208.0 | Požadováno
Microsoft.VisualStudio.Component.SQL.CMDUtils | Nástroje příkazového řádku SQL serveru | 15.0.26208.0 | Požadováno
Microsoft.VisualStudio.Component.SQL.DataSources | Zdroje dat pro podporu SQL serveru | 15.0.26621.2 | Požadováno
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 15.7.27617.1 | Požadováno
Microsoft.VisualStudio.Component.SQL.NCLI | Nativní klient systému SQL Server | 15.0.26208.0 | Požadováno
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 15.9.28107.0 | Požadováno
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Nástroje statické analýzy | 15.0.26208.0 | Požadováno
Microsoft.VisualStudio.Component.TextTemplating | Transformace textové šablony | 15.0.26208.0 | Požadováno
Microsoft.VisualStudio.Component.TypeScript.3.1 | TypeScript 3.1 SDK | 15.0.28218.60 | Požadováno
Microsoft.VisualStudio.Component.VisualStudioData | Zdroje dat a odkazy na služby | 15.6.27406.0 | Požadováno
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | 15.8.27924.0 | Požadováno
Microsoft.VisualStudio.Component.Web | Nástroje pro vývoj pro ASP.NET a web | 15.8.27825.0 | Požadováno
Microsoft.VisualStudio.Component.Workflow | Windows Workflow Foundation | 15.8.27825.0 | Požadováno
Microsoft.VisualStudio.ComponentGroup.Web | Vývoj pro ASP.NET a webové nástroje – požadavky | 15.9.28219.51 | Požadováno
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Vývoj pro ASP.NET a web | 15.8.27825.0 | Požadováno
Microsoft.VisualStudio.Component.TeamOffice | Visual Studio Tools for Office (VSTO) | 15.7.27625.0 | Doporučeno
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 15.8.27729.1 | Doporučeno
Microsoft.Net.Component.4.6.2.SDK | Rozhraní .NET framework 4.6.2 SDK | 15.6.27406.0 | volitelná,
Microsoft.Net.Component.4.6.2.TargetingPack | Rozhraní .NET framework 4.6.2 targeting pack | 15.6.27406.0 | volitelná,
Microsoft.Net.Component.4.7.1.SDK | Rozhraní .NET framework 4.7.1 SDK | 15.6.27406.0 | volitelná,
Microsoft.Net.Component.4.7.1.TargetingPack | Rozhraní .NET framework 4.7.1 targeting pack | 15.6.27406.0 | volitelná,
Microsoft.Net.Component.4.7.2.SDK | Rozhraní .NET framework 4.7.2 SDK | 15.8.27825.0 | volitelná,
Microsoft.Net.Component.4.7.2.TargetingPack | Rozhraní .NET framework 4.7.2 targeting pack | 15.8.27825.0 | volitelná,
Microsoft.Net.Component.4.7.SDK | Rozhraní .NET framework 4.7 SDK | 15.6.27406.0 | volitelná,
Microsoft.Net.Component.4.7.TargetingPack | .NET framework 4.7 targeting pack | 15.6.27406.0 | volitelná,
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | Vývojové nástroje .NET framework 4.6.2 | 15.6.27406.0 | volitelná,
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | Vývojové nástroje .NET framework 4.7.1 | 15.6.27406.0 | volitelná,
Microsoft.Net.ComponentGroup.4.7.2.DeveloperTools | Vývojové nástroje .NET framework 4.7.2 | 15.8.27825.0 | volitelná,
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | Vývojové nástroje .NET framework 4.7 | 15.6.27406.0 | volitelná,
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | 15.8.27729.1 | volitelná,

## <a name="python-development"></a>Vývoj v jazyce Python

**ID:** Microsoft.VisualStudio.Workload.Python

**Popis:** úpravy, ladění, interaktivní vývoj a zdrojový ovládací prvek pro Python.

### <a name="components-included-by-this-workload"></a>Pomocí této úlohy zahrnuté komponenty

ID součásti | Název | Version | Typ závislosti
--- | --- | --- | ---
Microsoft.Component.PythonTools | Podpora jazyka Python | 15.0.26823.1 | Požadováno
Component.CPython3.x64 | Python 3, 64 bitů (3.6.6) | 3.6.6 | Doporučeno
Microsoft.Component.CookiecutterTools | Podpora šablon Cookiecutter | 15.0.26621.2 | Doporučeno
Microsoft.Component.PythonTools.Web | Podpora webů v Pythonu | 15.9.28107.0 | Doporučeno
Microsoft.VisualStudio.Component.Common.Azure.Tools | Nástroje pro připojení a publikování | 15.9.28107.0 | Doporučeno
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Podpora jazyků JavaScript a TypeScript | 15.9.28125.51 | Doporučeno
Microsoft.VisualStudio.Component.SQL.CLR | Datové typy CLR pro SQL Server | 15.0.26208.0 | Doporučeno
Microsoft.VisualStudio.Component.TypeScript.3.1 | TypeScript 3.1 SDK | 15.0.28218.60 | Doporučeno
Microsoft.VisualStudio.Component.VisualStudioData | Zdroje dat a odkazy na služby | 15.6.27406.0 | Doporučeno
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 15.8.27729.1 | Doporučeno
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Vývoj pro ASP.NET a web | 15.8.27825.0 | Doporučeno
Component.Anaconda2.x64 | Anaconda2 64-bit (5.2.0) | 5.2.0 | volitelná,
Component.Anaconda2.x86 | Anaconda2 32 bitů (5.2.0) | 5.2.0 | volitelná,
Component.Anaconda3.x64 | Anaconda3 64-bit (5.2.0) | 5.2.0 | volitelná,
Component.Anaconda3.x86 | Anaconda3 32 bitů (5.2.0) | 5.2.0 | volitelná,
Component.CPython2.x64 | Python 2, 64 bitů (2.7.14) | 2.7.14 | volitelná,
Component.CPython2.x86 | Python 2, 32 bitů (2.7.14) | 2.7.14 | volitelná,
Component.CPython3.x86 | Python 3, 32 bitů (3.6.6) | 3.6.6 | volitelná,
Component.Microsoft.VisualStudio.RazorExtension | Jazykové služby Razor | 15.0.26720.2 | volitelná,
Component.Microsoft.Web.LibraryManager | Správce knihovny | 15.8.27705.0 | volitelná,
Component.WebSocket | WebSocket4Net | 15.0.26606.0 | volitelná,
Microsoft.Component.ClickOnce | Publikování ClickOnce | 15.8.27825.0 | volitelná,
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | volitelná,
Microsoft.Component.NetFX.Native | .NET Native | 15.0.26208.0 | volitelná,
Microsoft.Component.PythonTools.UWP | Podpory pro Python IoT | 15.0.26606.0 | volitelná,
Microsoft.Component.VC.Runtime.UCRTSDK | Windows Universal CRT SDK | 15.6.27309.0 | volitelná,
Microsoft.ComponentGroup.PythonTools.NativeDevelopment | Nástroje Pythonu pro nativní vývoj | 15.8.27729.1 | volitelná,
Microsoft.Net.Component.4.5.2.TargetingPack | Rozhraní .NET framework 4.5.2 targeting pack | 15.6.27406.0 | volitelná,
Microsoft.Net.Component.4.5.TargetingPack | .NET framework 4.5 targeting pack | 15.6.27406.0 | volitelná,
Microsoft.Net.Component.4.6.1.SDK | Rozhraní .NET framework 4.6.1 SDK | 15.6.27406.0 | volitelná,
Microsoft.Net.Component.4.6.1.TargetingPack | Rozhraní .NET framework 4.6.1 targeting pack | 15.6.27406.0 | volitelná,
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Vývojové nástroje .NET framework 4.6.1 | 15.8.27825.0 | volitelná,
Microsoft.Net.Core.Component.SDK.2.1 | Vývojové nástroje .NET core 2.1 | 15.8.27924.0 | volitelná,
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics tools | 15.8.27825.0 | volitelná,
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Azure – nástroje pro tvorbu | 15.8.27825.0 | volitelná,
Microsoft.VisualStudio.Component.Azure.ClientLibs | Knihovny Azure pro .NET | 15.0.26208.0 | volitelná,
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Emulátor výpočtů v Azure | 15.0.26621.2 | volitelná,
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Emulátor úložiště Azure | 15.9.28125.51 | volitelná,
Microsoft.VisualStudio.Component.Azure.Waverton | Základní nástroje pro Azure Cloud Services | 15.9.28107.0 | volitelná,
Microsoft.VisualStudio.Component.Azure.Waverton.BuildTools | Nástroje pro vytváření Azure Cloud Services | 15.7.27617.1 | volitelná,
Microsoft.VisualStudio.Component.ClassDesigner | Návrhář tříd | 15.0.26208.0 | volitelná,
Microsoft.VisualStudio.Component.CodeClone | Klonování kódu | 15.0.26208.0 | volitelná,
Microsoft.VisualStudio.Component.CodeMap | Mapa kódu | 15.0.26208.0 | volitelná,
Microsoft.VisualStudio.Component.DiagnosticTools | Nástroje pro profilaci .NET | 15.8.27729.1 | volitelná,
Microsoft.VisualStudio.Component.DockerTools | Kontejnerové vývojové nástroje | 15.8.27906.1 | volitelná,
Microsoft.VisualStudio.Component.DockerTools.BuildTools | Kontejnerové vývojové nástroje – Build Tools | 15.7.27617.1 | volitelná,
Microsoft.VisualStudio.Component.GraphDocument | DGML editor | 15.0.27005.2 | volitelná,
Microsoft.VisualStudio.Component.Graphics | Editory obrázků a 3D modelu | 15.6.27406.0 | volitelná,
Microsoft.VisualStudio.Component.Graphics.Tools | Ladicí program grafiky a profiler GPU pro DirectX | 15.6.27406.0 | volitelná,
Microsoft.VisualStudio.Component.Graphics.Win81 | Grafické nástroje systému Windows 8.1 SDK | 15.6.27406.0 | volitelná,
Microsoft.VisualStudio.Component.IISExpress | Služba IIS Express  | 15.0.26208.0 | volitelná,
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | 15.8.27729.1 | volitelná,
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostika jazyka JavaScript | 15.8.27729.1 | volitelná,
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Základní spravovaný úloze vývoje desktopových aplikací | 15.8.27729.1 | volitelná,
Microsoft.VisualStudio.Component.NuGet | Správce balíčků NuGet | 15.9.28016.0 | volitelná,
Microsoft.VisualStudio.Component.PortableLibrary | .NET portable Library targeting pack | 15.6.27309.0 | volitelná,
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilátory C# a Visual Basic Roslyn | 15.6.27309.0 | volitelná,
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# a Visual Basic | 15.8.27729.1 | volitelná,
Microsoft.VisualStudio.Component.SQL.ADAL | SQL ADAL runtime | 15.6.27406.0 | volitelná,
Microsoft.VisualStudio.Component.SQL.CMDUtils | Nástroje příkazového řádku SQL serveru | 15.0.26208.0 | volitelná,
Microsoft.VisualStudio.Component.SQL.DataSources | Zdroje dat pro podporu SQL serveru | 15.0.26621.2 | volitelná,
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 15.7.27617.1 | volitelná,
Microsoft.VisualStudio.Component.SQL.NCLI | Nativní klient systému SQL Server | 15.0.26208.0 | volitelná,
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 15.9.28107.0 | volitelná,
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Nástroje statické analýzy | 15.0.26208.0 | volitelná,
Microsoft.VisualStudio.Component.TextTemplating | Transformace textové šablony | 15.0.26208.0 | volitelná,
Microsoft.VisualStudio.Component.VC.140 | Nástrojů VC ++ 2015.3 v14.00 (v140) pro desktop | 15.7.27617.1 | volitelná,
Microsoft.VisualStudio.Component.VC.CoreIde | Visual Studio C++ – základní funkce | 15.6.27406.0 | volitelná,
Microsoft.VisualStudio.Component.VC.DiagnosticTools | Nástroje pro profilaci v C++ | 15.0.26823.1 | volitelná,
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | VC ++ 2017 verze 15.9 v14.16 nejnovější nástroje v141 pro | 15.9.28230.55 | volitelná,
Microsoft.VisualStudio.Component.Web | Nástroje pro vývoj pro ASP.NET a web | 15.8.27825.0 | volitelná,
Microsoft.VisualStudio.Component.Windows10SDK | Windows Universal C Runtime | 15.6.27406.0 | volitelná,
Microsoft.VisualStudio.Component.Windows10SDK.10586 | Windows 10 SDK (10.0.10586.0) | 15.6.27406.0 | volitelná,
Microsoft.VisualStudio.Component.Windows10SDK.17134 | Windows 10 SDK (10.0.17134.0) | 15.8.27924.0 | volitelná,
Microsoft.VisualStudio.Component.Windows81SDK | Windows 8.1 SDK | 15.6.27406.0 | volitelná,
Microsoft.VisualStudio.ComponentGroup.Web | Vývoj pro ASP.NET a webové nástroje – požadavky | 15.9.28219.51 | volitelná,

## <a name="universal-windows-platform-development"></a>Vývoj pro univerzální platformu Windows

**ID:** Microsoft.VisualStudio.Workload.Universal

**Popis:** vytváření aplikací pro univerzální platformu Windows pomocí C#, VB, JavaScriptu nebo volitelně C++.

### <a name="components-included-by-this-workload"></a>Pomocí této úlohy zahrnuté komponenty

ID součásti | Název | Version | Typ závislosti
--- | --- | --- | ---
Component.WebSocket | WebSocket4Net | 15.0.26606.0 | Požadováno
Microsoft.Component.ClickOnce | Publikování ClickOnce | 15.8.27825.0 | Požadováno
Microsoft.Component.NetFX.Native | .NET Native | 15.0.26208.0 | Požadováno
Microsoft.ComponentGroup.Blend | Blend for Visual Studio | 15.6.27406.0 | Požadováno
Microsoft.Net.Component.4.5.TargetingPack | .NET framework 4.5 targeting pack | 15.6.27406.0 | Požadováno
Microsoft.Net.Component.4.6.1.SDK | Rozhraní .NET framework 4.6.1 SDK | 15.6.27406.0 | Požadováno
Microsoft.Net.Core.Component.SDK.2.1 | Vývojové nástroje .NET core 2.1 | 15.8.27924.0 | Požadováno
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics tools | 15.8.27825.0 | Požadováno
Microsoft.VisualStudio.Component.DiagnosticTools | Nástroje pro profilaci .NET | 15.8.27729.1 | Požadováno
Microsoft.VisualStudio.Component.Graphics | Editory obrázků a 3D modelu | 15.6.27406.0 | Požadováno
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostika jazyka JavaScript | 15.8.27729.1 | Požadováno
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Podpora jazyků JavaScript a TypeScript | 15.9.28125.51 | Požadováno
Microsoft.VisualStudio.Component.NuGet | Správce balíčků NuGet | 15.9.28016.0 | Požadováno
Microsoft.VisualStudio.Component.PortableLibrary | .NET portable Library targeting pack | 15.6.27309.0 | Požadováno
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilátory C# a Visual Basic Roslyn | 15.6.27309.0 | Požadováno
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# a Visual Basic | 15.8.27729.1 | Požadováno
Microsoft.VisualStudio.Component.SQL.CLR | Datové typy CLR pro SQL Server | 15.0.26208.0 | Požadováno
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Nástroje statické analýzy | 15.0.26208.0 | Požadováno
Microsoft.VisualStudio.Component.TypeScript.3.1 | TypeScript 3.1 SDK | 15.0.28218.60 | Požadováno
Microsoft.VisualStudio.Component.UWP.Support | Nástroje pro univerzální platformu Windows | 15.9.28119.51 | Požadováno
Microsoft.VisualStudio.Component.VisualStudioData | Zdroje dat a odkazy na služby | 15.6.27406.0 | Požadováno
Microsoft.VisualStudio.Component.Windows10SDK.17134 | Windows 10 SDK (10.0.17134.0) | 15.8.27924.0 | Požadováno
Microsoft.VisualStudio.ComponentGroup.UWP.Cordova | Nástroje pro univerzální platformu Windows pro Cordova | 15.7.27617.1 | Požadováno
Microsoft.VisualStudio.ComponentGroup.UWP.NetCoreAndStandard | .NET native a .NET Standard | 15.8.27906.1 | Požadováno
Microsoft.VisualStudio.ComponentGroup.UWP.Xamarin | Nástroje pro univerzální platformu Windows pro Xamarin | 15.7.27617.1 | Požadováno
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Vývoj pro ASP.NET a web | 15.8.27825.0 | Požadováno
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | 15.8.27729.1 | Doporučeno
Microsoft.Component.VC.Runtime.OSSupport | Visual C++ runtime pro UPW | 15.6.27406.0 | volitelná,
Microsoft.Net.Component.4.7.1.SDK | Rozhraní .NET framework 4.7.1 SDK | 15.6.27406.0 | volitelná,
Microsoft.VisualStudio.Component.CodeClone | Klonování kódu | 15.0.26208.0 | volitelná,
Microsoft.VisualStudio.Component.CodeMap | Mapa kódu | 15.0.26208.0 | volitelná,
Microsoft.VisualStudio.Component.DependencyValidation.Enterprise | Živé ověření závislosti | 15.0.26208.0 | volitelná,
Microsoft.VisualStudio.Component.GraphDocument | DGML editor | 15.0.27005.2 | volitelná,
Microsoft.VisualStudio.Component.Graphics.Tools | Ladicí program grafiky a profiler GPU pro DirectX | 15.6.27406.0 | volitelná,
Microsoft.VisualStudio.Component.Graphics.Win81 | Grafické nástroje systému Windows 8.1 SDK | 15.6.27406.0 | volitelná,
Microsoft.VisualStudio.Component.Phone.Emulator.15254 | Emulátor Windows 10 Mobile (Fall Creators Update) | 15.0.27406.0 | volitelná,
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 15.7.27617.1 | volitelná,
Microsoft.VisualStudio.Component.SQL.NCLI | Nativní klient systému SQL Server | 15.0.26208.0 | volitelná,
Microsoft.VisualStudio.Component.UWP.VC.ARM64 | Nástroje pro univerzální platformu Windows C++ pro ARM64 | 15.0.28125.51 | volitelná,
Microsoft.VisualStudio.Component.VC.CoreIde | Visual Studio C++ – základní funkce | 15.6.27406.0 | volitelná,
Microsoft.VisualStudio.Component.VC.Tools.ARM | Kompilátory jazyka Visual C++ a knihovny pro ARM | 15.8.27825.0 | volitelná,
Microsoft.VisualStudio.Component.VC.Tools.ARM64 | Kompilátory jazyka Visual C++ a knihovny pro ARM64 | 15.9.28230.55 | volitelná,
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | VC ++ 2017 verze 15.9 v14.16 nejnovější nástroje v141 pro | 15.9.28230.55 | volitelná,
Microsoft.VisualStudio.Component.Windows10SDK.10240 | Windows 10 SDK (10.0.10240.0) | 15.6.27406.0 | volitelná,
Microsoft.VisualStudio.Component.Windows10SDK.10586 | Windows 10 SDK (10.0.10586.0) | 15.6.27406.0 | volitelná,
Microsoft.VisualStudio.Component.Windows10SDK.14393 | Windows 10 SDK (10.0.14393.0) | 15.6.27406.0 | volitelná,
Microsoft.VisualStudio.Component.Windows10SDK.15063.Desktop | Windows 10 SDK (10.0.15063.0) pro Desktop C++ [x86 a x64] | 15.6.27406.0 | volitelná,
Microsoft.VisualStudio.Component.Windows10SDK.15063.UWP | Windows 10 SDK (10.0.15063.0) pro UPW: C#, VB, JS | 15.6.27406.0 | volitelná,
Microsoft.VisualStudio.Component.Windows10SDK.15063.UWP.Native | Windows 10 SDK (10.0.15063.0) pro UPW: C++ | 15.6.27406.0 | volitelná,
Microsoft.VisualStudio.Component.Windows10SDK.16299.Desktop | Windows 10 SDK (10.0.16299.0) pro Desktop C++ [x86 a x64] | 15.6.27406.0 | volitelná,
Microsoft.VisualStudio.Component.Windows10SDK.16299.Desktop.arm | Windows 10 SDK (10.0.16299.0) pro Desktop C++ [ARM a ARM64] | 15.6.27406.0 | volitelná,
Microsoft.VisualStudio.Component.Windows10SDK.16299.UWP | Windows 10 SDK (10.0.16299.0) pro UPW: C#, VB, JS | 15.6.27406.0 | volitelná,
Microsoft.VisualStudio.Component.Windows10SDK.16299.UWP.Native | Windows 10 SDK (10.0.16299.0) pro UPW: C++ | 15.6.27406.0 | volitelná,
Microsoft.VisualStudio.Component.Windows10SDK.17763 | Windows 10 SDK (10.0.17763.0) | 15.9.28218.60 | volitelná,
Microsoft.VisualStudio.Component.Windows10SDK.IpOverUsb | Připojení zařízení USB | 15.7.27625.0 | volitelná,
Microsoft.VisualStudio.ComponentGroup.ArchitectureTools.Managed | Architektury a analytické nástroje | 15.0.26208.0 | volitelná,
Microsoft.VisualStudio.ComponentGroup.UWP.VC | Nástroje pro univerzální platformu Windows C++ | 15.9.28107.0 | volitelná,
Microsoft.VisualStudio.ComponentGroup.Windows10SDK.15063 | Windows 10 SDK (10.0.15063.0) | 15.8.27825.0 | volitelná,
Microsoft.VisualStudio.ComponentGroup.Windows10SDK.16299 | Windows 10 SDK (10.0.16299.0) | 15.8.27825.0 | volitelná,

## <a name="visual-studio-extension-development"></a>Vývoj rozšíření sady Visual Studio

**ID:** Microsoft.VisualStudio.Workload.VisualStudioExtension

**Popis:** vytvořit doplňky a rozšíření pro Visual Studio, včetně nových příkazů, analyzátorů kódu a nástrojů systému windows.

### <a name="components-included-by-this-workload"></a>Pomocí této úlohy zahrnuté komponenty

ID součásti | Název | Version | Typ závislosti
--- | --- | --- | ---
Microsoft.Component.ClickOnce | Publikování ClickOnce | 15.8.27825.0 | Požadováno
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | Požadováno
Microsoft.Net.Component.4.6.1.SDK | Rozhraní .NET framework 4.6.1 SDK | 15.6.27406.0 | Požadováno
Microsoft.Net.Component.4.6.1.TargetingPack | Rozhraní .NET framework 4.6.1 targeting pack | 15.6.27406.0 | Požadováno
Microsoft.Net.Component.4.6.TargetingPack | .NET framework 4.6 targeting pack | 15.6.27406.0 | Požadováno
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Vývojové nástroje .NET framework 4.6.1 | 15.8.27825.0 | Požadováno
Microsoft.VisualStudio.Component.NuGet | Správce balíčků NuGet | 15.9.28016.0 | Požadováno
Microsoft.VisualStudio.Component.PortableLibrary | .NET portable Library targeting pack | 15.6.27309.0 | Požadováno
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilátory C# a Visual Basic Roslyn | 15.6.27309.0 | Požadováno
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# a Visual Basic | 15.8.27729.1 | Požadováno
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Nástroje statické analýzy | 15.0.26208.0 | Požadováno
Microsoft.VisualStudio.Component.VSSDK | Visual Studio SDK | 15.8.27729.1 | Požadováno
Microsoft.VisualStudio.ComponentGroup.VisualStudioExtension.Prerequisites | Visual Studio předpoklady pro vývoj rozšíření | 15.7.27625.0 | Požadováno
Microsoft.VisualStudio.Component.DiagnosticTools | Nástroje pro profilaci .NET | 15.8.27729.1 | Doporučeno
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | 15.8.27729.1 | Doporučeno
Microsoft.VisualStudio.Component.TextTemplating | Transformace textové šablony | 15.0.26208.0 | Doporučeno
Component.Dotfuscator | PreEmptive ochranu – řešení Dotfuscator | 15.0.26208.0 | volitelná,
Microsoft.Component.CodeAnalysis.SDK | Sada .NET Compiler Platform SDK | 15.0.27729.1 | volitelná,
Microsoft.Component.VC.Runtime.OSSupport | Visual C++ runtime pro UPW | 15.6.27406.0 | volitelná,
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics tools | 15.8.27825.0 | volitelná,
Microsoft.VisualStudio.Component.ClassDesigner | Návrhář tříd | 15.0.26208.0 | volitelná,
Microsoft.VisualStudio.Component.CodeClone | Klonování kódu | 15.0.26208.0 | volitelná,
Microsoft.VisualStudio.Component.CodeMap | Mapa kódu | 15.0.26208.0 | volitelná,
Microsoft.VisualStudio.Component.DependencyValidation.Enterprise | Živé ověření závislosti | 15.0.26208.0 | volitelná,
Microsoft.VisualStudio.Component.DslTools | Sada Modeling SDK | 15.0.27005.2 | volitelná,
Microsoft.VisualStudio.Component.GraphDocument | DGML editor | 15.0.27005.2 | volitelná,
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 15.7.27617.1 | volitelná,
Microsoft.VisualStudio.Component.SQL.NCLI | Nativní klient systému SQL Server | 15.0.26208.0 | volitelná,
Microsoft.VisualStudio.Component.VC.ATL | Visual C++ ATL pro x86 a x64 | 15.7.27625.0 | volitelná,
Microsoft.VisualStudio.Component.VC.ATLMFC | Visual C++ MFC pro x86 a x64 | 15.7.27625.0 | volitelná,
Microsoft.VisualStudio.Component.VC.CoreIde | Visual Studio C++ – základní funkce | 15.6.27406.0 | volitelná,
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | VC ++ 2017 verze 15.9 v14.16 nejnovější nástroje v141 pro | 15.9.28230.55 | volitelná,
Microsoft.VisualStudio.ComponentGroup.ArchitectureTools.Managed | Architektury a analytické nástroje | 15.0.26208.0 | volitelná,

## <a name="mobile-development-with-javascript"></a>Vývoj pro mobilní zařízení pomocí JavaScriptu

**ID:** Microsoft.VisualStudio.Workload.WebCrossPlat

**Popis:** vytvářet aplikace pro Android, iOS a UPW pomocí nástrojů pro Apache Cordova.

### <a name="components-included-by-this-workload"></a>Pomocí této úlohy zahrnuté komponenty

ID součásti | Název | Version | Typ závislosti
--- | --- | --- | ---
Component.CordovaToolset.6.3.1 | Sada nástrojů Cordova 6.3.1 | 15.7.27625.0 | Požadováno
Component.WebSocket | WebSocket4Net | 15.0.26606.0 | Požadováno
Microsoft.VisualStudio.Component.Cordova | Vývoj pro mobilní zařízení pomocí základních funkcí JavaScriptu | 15.0.26606.0 | Požadováno
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostika jazyka JavaScript | 15.8.27729.1 | Požadováno
Microsoft.VisualStudio.Component.JavaScript.ProjectSystem | JavaScript ProjectSystem a sdílené nástroje | 15.0.26606.0 | Požadováno
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Podpora jazyků JavaScript a TypeScript | 15.9.28125.51 | Požadováno
Microsoft.VisualStudio.Component.TypeScript.2.3 | TypeScript 2.3 SDK | 15.8.27729.1 | Požadováno
Microsoft.VisualStudio.Component.TypeScript.3.1 | TypeScript 3.1 SDK | 15.0.28218.60 | Požadováno
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Vývoj pro ASP.NET a web | 15.8.27825.0 | Požadováno
Component.Android.SDK23.Private | Instalace sady Android SDK (úroveň rozhraní API 23) (místní instalace pro vývoj pro mobilní zařízení pomocí JavaScriptu nebo C++) | 15.9.28016.0 | volitelná,
Component.Google.Android.Emulator.API23.Private | Emulátor Google Android (úroveň rozhraní API 23) (místní instalace) | 15.6.27413.0 | volitelná,
Component.HAXM.Private | Intel Hardware Accelerated provádění Manager (HAXM) (místní instalace) | 15.6.27413.0 | volitelná,
Component.JavaJDK | Java SE Development Kit (8.0.1120.15) | 15.6.27406.0 | volitelná,
Component.OpenJDK | OpenJDK je distribuce Microsoftu | 15.9.28125.51 | volitelná,
Microsoft.Component.ClickOnce | Publikování ClickOnce | 15.8.27825.0 | volitelná,
Microsoft.Component.NetFX.Native | .NET Native | 15.0.26208.0 | volitelná,
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics tools | 15.8.27825.0 | volitelná,
Microsoft.VisualStudio.Component.DiagnosticTools | Nástroje pro profilaci .NET | 15.8.27729.1 | volitelná,
Microsoft.VisualStudio.Component.Git | Git for Windows | 15.0.26208.0 | volitelná,
Microsoft.VisualStudio.Component.Graphics | Editory obrázků a 3D modelu | 15.6.27406.0 | volitelná,
Microsoft.VisualStudio.Component.Phone.Emulator.15254 | Emulátor Windows 10 Mobile (Fall Creators Update) | 15.0.27406.0 | volitelná,
Microsoft.VisualStudio.Component.SQL.CLR | Datové typy CLR pro SQL Server | 15.0.26208.0 | volitelná,
Microsoft.VisualStudio.Component.VisualStudioData | Zdroje dat a odkazy na služby | 15.6.27406.0 | volitelná,
Microsoft.VisualStudio.Component.Windows10SDK.17134 | Windows 10 SDK (10.0.17134.0) | 15.8.27924.0 | volitelná,
Microsoft.VisualStudio.ComponentGroup.UWP.Cordova | Nástroje pro univerzální platformu Windows pro Cordova | 15.7.27617.1 | volitelná,

## <a name="unaffiliated-components"></a>Nespojená komponenty

Toto jsou komponenty, které nejsou zahrnuty u jakékoli úlohy, ale může vybrat jako jednotlivých komponent.

ID součásti | Název | Version
--- | --- | ---
Component.Android.Emulator | Emulátor sady Visual Studio pro Android | 15.6.27413.0
Component.Android.NDK.R11C | Sada Android NDK (R11C) | 11.3.14
Component.Android.NDK.R11C_3264 | Sada Android NDK (R11C) (32 bitů) | 11.3.16
Component.Android.SDK23 | Instalace sady Android SDK (úroveň rozhraní API 23) (globální instalace) | 15.9.28107.0
Component.Android.SDK25 | Instalace sady Android SDK (úroveň rozhraní API 25) | 15.9.28107.0
Component.GitHub.VisualStudio | Rozšíření GitHub pro Visual Studio | 2.5.2.2500
Component.Google.Android.Emulator.API23.V2 | Emulátor Google Android (úroveň rozhraní API 23) (globální instalace) | 15.6.27413.0
Component.Google.Android.Emulator.API25 | Emulátor Google Android (úroveň rozhraní API 25) | 15.7.27604.0
Microsoft.Component.Blend.SDK.WPF | Blend for Visual Studio SDK pro .NET | 15.6.27406.0
Microsoft.Component.HelpViewer | Aplikaci Help Viewer | 15.6.27323.2
Microsoft.VisualStudio.Component.LinqToSql | Nástroje LINQ to SQL | 15.6.27406.0
Microsoft.VisualStudio.Component.Phone.Emulator | Emulátor Windows 10 Mobile (Anniversary Edition) | 15.6.27406.0
Microsoft.VisualStudio.Component.Phone.Emulator.15063 | Windows 10 Mobile Emulator (Creators Update) | 15.6.27406.0
Microsoft.VisualStudio.Component.Runtime.Node.x86.6.4.0 | Modul runtime pro komponenty založené na Node.js v6.4.0 (x86) | 15.7.27617.1
Microsoft.VisualStudio.Component.Runtime.Node.x86.7.4.0 | Modul runtime pro komponenty založené na Node.js v7.4.0 (x86) | 15.7.27617.1
Microsoft.VisualStudio.Component.TestTools.CodedUITest | Programový test UI | 15.0.26606.0
Microsoft.VisualStudio.Component.TestTools.FeedbackClient | Microsoft Feedback Client | 15.6.27406.0
Microsoft.VisualStudio.Component.TestTools.MicrosoftTestManager | Microsoft Test Manager | 15.6.27406.0
Microsoft.VisualStudio.Component.TypeScript.2.0 | TypeScript 2.0 SDK | 15.8.27729.1
Microsoft.VisualStudio.Component.TypeScript.2.1 | TypeScript 2.1 sady SDK | 15.8.27729.1
Microsoft.VisualStudio.Component.TypeScript.2.2 | TypeScript 2.2 SDK | 15.8.27729.1
Microsoft.VisualStudio.Component.TypeScript.2.5 | TypeScript 2.5 SDK | 15.6.27406.0
Microsoft.VisualStudio.Component.TypeScript.2.6 | TypeScript 2.6 SDK | 15.0.27729.1
Microsoft.VisualStudio.Component.TypeScript.2.7 | TypeScript 2.7 sady SDK | 15.0.27729.1
Microsoft.VisualStudio.Component.TypeScript.2.8 | TypeScript 2.8 SDK | 15.0.27729.1
Microsoft.VisualStudio.Component.TypeScript.2.9 | TypeScript 2.9 SDK | 15.0.27924.0
Microsoft.VisualStudio.Component.TypeScript.3.0 | TypeScript 3.0 SDK | 15.0.27924.0
Microsoft.VisualStudio.Component.VC.ATL.ARM | Visual C++ ATL pro ARM | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.ATL.ARM.Spectre | Visual C++ ATL pro ARM se zmírněními hrozeb Spectre | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.ATL.ARM64 | Visual C++ ATL pro ARM64 | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.ATL.ARM64.Spectre | Visual C++ ATL pro ARM64 se zmírněními hrozeb Spectre | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.ATL.Spectre | Visual C++ ATL (x86/x64) se zmírněními hrozeb Spectre | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.ATLMFC.Spectre | Visual C++ MFC pro x86/x64 se zmírněními hrozeb Spectre | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.ClangC2 | Clang/C2 (experimentální) | 15.7.27520.0
Microsoft.VisualStudio.Component.VC.MFC.ARM | Visual C++ MFC pro ARM | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.MFC.ARM.Spectre | Visual C++ MFC pro ARM se zmírněními hrozeb Spectre | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.MFC.ARM64 | Visual C++ MFC pro ARM64 | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.MFC.ARM64.Spectre | Podpora Visual C++ MFC pro ARM64 se zmírněními hrozeb Spectre | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.Runtimes.ARM.Spectre | VC ++ 2017 verze 15.9 v14.16 knihovny pro Spectre (ARM) | 15.9.28230.55
Microsoft.VisualStudio.Component.VC.Runtimes.ARM64.Spectre | VC ++ 2017 verze 15.9 v14.16 knihovny pro Spectre (ARM64) | 15.9.28230.55
Microsoft.VisualStudio.Component.VC.Runtimes.x86.x64.Spectre | VC ++ 2017 verze 15.9 v14.16 knihovny pro Spectre (x86 a x64) | 15.9.28230.55
Microsoft.VisualStudio.Component.VC.Tools.14.11 | Sada nástrojů 14.11 pro VC ++ 2017 verze 15.4 | 15.0.27924.0
Microsoft.VisualStudio.Component.VC.Tools.14.12 | Sada nástrojů VC ++ 2017 verze 15.5 14.12 | 15.0.27924.0
Microsoft.VisualStudio.Component.VC.Tools.14.13 | VC ++ 2017 verze 15.6 v14.13 – sada nástrojů | 15.0.27924.0
Microsoft.VisualStudio.Component.VC.Tools.14.14 | Sada nástrojů VC ++ 2017 verze 15.7 v14.14 – | 15.0.27924.0
Microsoft.VisualStudio.Component.VC.Tools.14.15 | Sada nástrojů VC ++ 2017 verze 15.8 v14.15 | 15.0.28230.55

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Viz také:

* [ID úloh a komponent sady Visual Studio](workload-and-component-ids.md)
* [Příručka pro správce aplikace Visual Studio](visual-studio-administrator-guide.md)
* [Instalace sady Visual Studio s použitím parametrů příkazového řádku](use-command-line-parameters-to-install-visual-studio.md)
  * [Příklady parametrů příkazového řádku](command-line-parameter-examples.md)
* [Vytvoření offline instalace sady Visual Studio](create-an-offline-installation-of-visual-studio.md)
